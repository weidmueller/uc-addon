# Command line tool to create and publish AddOns
An AddOn package contains your manifest and logo along with any docker images referenced in the manifest. We provide a tool, `uc-aom-packager` to create these self-contained bundles as a docker image.
You can pull the `u-control/uc-aom-packager` image from `wmucdev.azurecr.io` registry and integrate it into your build pipeline.

## Prerequisites
First login to the `wmucdev.azure.io` registry with your provided credentials:
```sh
docker login --username <username> --password <password> wmucdev.azurecr.io
```

Then pull the `uc-aom-packager` image:
```sh
docker pull wmucdev.azurecr.io/u-control/uc-aom-packager
```

## Integration with a build pipeline
The `uc-aom-packager` requires access to the docker images that are referenced in your manifest.
It is anticipated that these will be hosted by a container registry.

The credentials for this registry must be present in a file and given as a command line argument to the `uc-aom-packager`.

The default entry point of the container is to display the help message, which you should refer to for more detailed usage information.

### Example
We will publish a fictitious Add-On called `add-on-example`.
For the purpose of this example, we will assume that the docker image
that Add-On uses is hosted at `private.registry.io` as `docker-image:v0.0.1`.

A minimal `manifest.json` file references this docker image and has the following contents:
```json
{
  "manifestVersion": "0.1",
  "version": "0.1",
  "title": "add-on-example",
  "description": "Example to demonstrate uc-aom-packager tool",
  "logo": "logo.png",
  "services": {
    "example-service": {
      "type": "docker-compose",
      "config": {
        "image": "docker-image:v0.0.1",
        "stdinOpen": true,
        "tty": true,
        "containerName": "add-on-example-container"
      }
    }
  }
}
```
This file along with the `logo.png` exist in the directory `/home/add-ons/example`

The uc-aom-packager needs to be able to access the host registry `private.registry.io`.
Provide the credentials in the following `source-credentials.json` file:
```json
{
  "username": "<username>",
  "password": "<password>",
  "serveraddress": "docker.registry.io"
}
```

For the uc-aom-packager to publish `add-on-example` to our dedicated Add-On registry,
we require a further credentials file `target-credentials.json`, which has the following contents:
```json
{
  "username": "<username>",
  "password": "<password>",
  "repositoryname": "add-on-example"
}
```

All of the files (`manifest.json`, `logo.png`, `source-credentials.json`, and `target-credentials.json`) exist in
the host directory `/home/add-ons/example`.

To build and publish the example Add-On `add-on-example`, we could using the following docker command:
```sh
docker run -it --rm \
    --mount src=/home/add-ons/example,target=/tmp/add-on-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager uc-aom-packager \
    -m /tmp/add-on-example \
    -s /tmp/add-on-example/source-credentials.json \
    -t /tmp/add-on-example/target-credentials.json \
    -v
```

### Note about publishing
The version property from the manifest is used to tag the Add-On in the registry. Thus, publishing the same Add-On will overwrite the existing one if both of them have identical versions.

## Change Add-On registry
Overwriting the default Add-On registry requires a debug firmware to be installed on the device.

If a debug firmware is installed, access the device and navigate to `/var/lib/uc-aom` and create the file `registrycredentials.json`.

Depending on the type of registry, enter and fill out the following content in the created file:
### Secure registry
To access a secure registry, username, password and server address are required.
```json
{
  "username": "<username>",
  "password": "<password>",
  "serveraddress": "<serveraddress>"
}
```
### Insecure registry
To access an insecure registry only the server address is required.
```json
{
  "serveraddress": "<serveraddress>"
}
```
## Restart device/service
Changes will take effect after you restart the device or service (`uc-aom`) . This can be done by one of the following methods:
* Restart the device by using the `reboot` command
* Power cycling the device
* Using the `Restart system` button in the Web Interface (`Settings -> Restart system`)
* Restart the service by entering '`systemctl restart uc-aom`' in the command line
