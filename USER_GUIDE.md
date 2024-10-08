# Command line tool to create, publish and pull apps

An app package contains your manifest and logo along with any docker images referenced in the manifest. We provide a tool, `uc-aom-packager` to create these self-contained bundles as a docker image.
You can pull the `u-control/uc-aom-packager` image from `wmucdev.azurecr.io` registry and integrate it into your build pipeline.

Usage:

```sh
docker run -it --rm --pull=always \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 \
    uc-aom-packager <command> [flags]
```

The commands are:
| Command | Description                                           |
| :------ | :---------------------------------------------------- |
| export  | export an app as SWU for offline installation         |
| push    | push an app to the Weidmüller development registry    |
| pull    | pull a previously pushed app to the local file system |

## Prerequisites

First login to the Weidmüller development registry `wmucdev.azurecr.io` with your provided credentials:

```sh
docker login --username <username> --password <password> wmucdev.azurecr.io
```

Then pull the `uc-aom-packager` image:

```sh
docker pull wmucdev.azurecr.io/u-control/uc-aom-packager:0
```

## Integration with a build pipeline

The `uc-aom-packager` requires access to the docker images that are referenced in your manifest.
It is anticipated that these will be hosted by a container registry.

The credentials for this registry must be present in a file and given as a command line argument to the `uc-aom-packager`.

The default command of the container is to display the help message, which you should refer to for more detailed usage information.

### Note about semantic versioning tagging scheme

The `uc-aom-packager` docker image follows a semantic versioning tagging scheme that ensures that users of a docker image can guarantee compatibility and stay updated without having to be aware of every new build that is created.

By subscribing to the `major` label only, you are guaranteed backward compatibility and get new features and fixes each time you pull.

By subscribing to the `major.minor` label, you are guaranteed backward compatibility and bug fixes, but will have to decide when to implement new features.

Finally, by subscribing to the `major.minor.patch` label, you are guaranteed to always get the _exact_ same image layer, excluding every update.

A `latest` tag isn't offered. Therefore, you need to choose at least the `major` tag to pull the `uc-aom-packager` docker image, as demonstrated in the examples that follow.

## Push of an app to the Weidmüller development registry

Usage:

```sh
docker run -it --rm --pull=always \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 \
    uc-aom-packager push [flags]
```

Flags:
| Flags                           | Description                                                                                                                           |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------ |
| -m, --manifest string           | a directory path which contains logo and manifest.json files                                                                          |
| -s, --source-credentials string | path to a file providing credentials, for the registry hosting docker images, referenced in the app's manifest.json file              |
| -t, --target-credentials string | path to a file providing credentials for the app's host repository. The target registry is always the Weidmüller development registry |
| -v, --verbose count             | explain what is being done, pass multiple times to increase verbosity                                                                 |

Example:

We will publish a fictitious app called `app-example`.
For the purpose of this example, we will assume that the docker image
that app uses is hosted at `private.registry.io` as `docker-image:v0.0.1`.

A minimal `manifest.json` file references this docker image and has the following contents:

```json
{
  "manifestVersion": "0.2",
  "version": "0.1.0-1",
  "title": "app-example",
  "description": "Example to demonstrate uc-aom-packager tool",
  "logo": "logo.png",
  "services": {
    "example-service": {
      "type": "docker-compose",
      "config": {
        "image": "docker-image:v0.0.1",
        "stdinOpen": true,
        "tty": true,
        "containerName": "app-example-container"
      }
    }
  },
  "vendor": {
    "name": "Test Name",
    "url": "https://www.example.com",
    "email": "test@mail.test",
    "street": "Test Street",
    "zip": "12345",
    "city": "Test City",
    "country": "Test Country"
  }
}
```

This file along with the `logo.png` exist in the directory `/home/apps/example`

The uc-aom-packager needs to be able to access the host registry `private.registry.io`.
Provide the credentials in the following `source-credentials.json` file:

```json
{
  "username": "<username>",
  "password": "<password>",
  "serveraddress": "private.registry.io",
  "plain-http": false,
  "insecure": false
}
```

For the uc-aom-packager to publish `app-example` to our dedicated app registry,
we require a further credentials file `target-credentials.json`, which has the following contents:

```json
{
  "username": "<username>",
  "password": "<password>",
  "repositoryname": "app-example",
  "serveraddress": "<custom registry address>",
  "plain-http": false,
  "insecure": false
}
```

The server address within the target credentials is optional. If it is set, the uc-aom-packager will use that value as the registry address instead of the default one.

By default, https is accepted as the server address.
To access an http-only registry (e.g. for a local registry) you must set the `plain-http` field to `true`.

To access an https registry without a TLS certificate check (e.g. for a self signed certificate) you must set the field `insecure` to `true`.

All of the files (`manifest.json`, `logo.png`, `source-credentials.json`, and `target-credentials.json`) exist in
the host directory `/home/apps/example`.

To build and publish the example app `app-example`, we could use the following docker command in combination with the `push` command:

```sh
docker run -it --rm --pull=always \
    --mount src=/home/apps/example,target=/tmp/app-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 \
    uc-aom-packager push \
    -m /tmp/app-example \
    -s /tmp/app-example/source-credentials.json \
    -t /tmp/app-example/target-credentials.json \
    -v
```

### Create app with a docker image from Docker Hub

You can directly create a u-OS app from docker hub.

For those, provide the credentials in the following `source-credentials.json` file:

```json
{
  "serveraddress": "docker.io"
}
```

The docker image reference in the manifest needs to start with `library/`.

A minimal `manifest.json` file references this docker hub docker image and has the following contents:

```json
{
    "manifestVersion": "0.2",
    "version": "0.1.0-1",
    "title": "app-example",
    "description": "Example to demonstrate uc-aom-packager tool",
    "logo": "logo.png",
    "services": {
        "example-service": {
            "type": "docker-compose",
            "config": {
                "image": "library/alpine:latest",
                "stdinOpen": true,
                "tty": true,
                "containerName": "app-example-container"
            }
        }
    },
    "platform": [
        "ucg",
        "ucm",
        "ucu"
    ],
    "vendor": {
        "name": "Test Name",
        "url": "https://www.example.com",
        "email": "test@mail.test",
        "street": "Test Street",
        "zip": "12345",
        "city": "Test City",
        "country": "Test Country"
    }
}
```

### Note about publishing

The version property from the manifest is used to tag the app in the registry. Thus, publishing the same app will overwrite the existing one if both of them have identical versions.

There is a change between the app package format between u-OS version 1.16 and 2.0.
The new format now supports multi architecture apps.
All apps from 1.16 can be installed on 2.0 devices with an ARMv7 architecture and will be migrated automatically on installation.
However, a 1.16 device is limited to a manifest schema version of 0.1.
Thus, if you require a new feature from the manifest, you can only deploy the app for 2.0.
There is no downgrade migration between manifest schema versions.

To publish an app for 1.16 you need to use packager 0.3:

```sh
docker run -it --rm --pull=always \
    --mount src=/home/apps/example,target=/tmp/app-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0.3 \
    uc-aom-packager push \
    -m /tmp/app-example \
    -s /tmp/app-example/source-credentials.json \
    -t /tmp/app-example/target-credentials.json \
    -v
```

The packager creates the 2.0 package format since packager version 0.4.

## Pull of an app from the Weidmüller development registry

Usage:

```sh
docker run -it --rm --pull=always \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 \
    uc-aom-packager pull [flags]
```

Flags:
| Flags                           | Description                                                                                                         |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------------ |
| -o, --output string             | output directory where the pulled app will be stored                                                                |
| -t, --target-credentials string | filepath to the target registry credentials file. The target registry is always the Weidmüller development registry |
| -v, --verbose count             | explain what is being done, pass multiple times to increase verbosity                                               |
| -x, --extract                   | extract the app archive (default true)                                                                              |
| --version string                | version of the app to be pulled from the registry                                                                   |

Example:

```sh
docker run -it --rm --pull=always \
    --mount src=/home/apps/example,target=/tmp/app-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 uc-aom-packager \
    pull
    -t /tmp/app-example/target-credentials.json
    -o /tmp/app-example/output
    -v
    --version 0.1.0-1
```

The target credentials file `target-credentials.json` has the same content as in the `push` command:

```json
{
  "username": "<username>",
  "password": "<password>",
  "repositoryname": "app-example",
  "serveraddress": "<custom registry address>",
  "plain-http": false,
  "insecure": false
}
```

## Export of an app from the Weidmüller development registry for offline installation

Usage:

```sh
docker run -it --rm --pull=always \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 \
    uc-aom-packager export [flags]
```

Flags:
| Flags                           | Description                                                                                                         |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------------ |
| -t, --target-credentials string | filepath to the target registry credentials file. The target registry is always the Weidmüller development registry |
| --version string                | version of the app to be exported from the registry                                                                 |
| -o, --output string             | output directory where the exported app will be stored as an swu file                                               |
| -v, --verbose count             | explain what is being done, pass multiple times to increase verbosity                                               |

Example:

```sh
docker run -it --rm --pull=always \
    --mount src=/home/apps/example,target=/tmp/app-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 uc-aom-packager \
    export
    -t /tmp/app-example/target-credentials.json
    --version 0.1.0-1
    -o /tmp/app-example/example-app.swu
    -v
```

The target credentials file `target-credentials.json` has the same content as in the `push` command:

```json
{
  "username": "<username>",
  "password": "<password>",
  "repositoryname": "app-example",
  "serveraddress": "<custom registry address>",
  "plain-http": false,
  "insecure": false
}
```

## Change the default registry address

The uc-aom-packager uses the Weidmüller development registry by default.
To change the default registry server address, override the `DEFAULT_REGISTRY_SERVER_ADDRESS` environment variable or set the `serveraddress` within the `target-credentials.json` file.

Example:

```sh
docker run -it --rm --pull=always \
    --mount src=/home/apps/example,target=/tmp/app-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0.3 \
    uc-aom-packager push \
    -e DEFAULT_REGISTRY_SERVER_ADDRESS=custom.registry.address
    -m /tmp/app-example \
    -s /tmp/app-example/source-credentials.json \
    -t /tmp/app-example/target-credentials.json \
    -v
```

## Change app registry on the device

Overriding the default app registry requires a debug firmware to be installed on the device.

If a debug firmware is installed, access the device and navigate to `/var/lib/uc-aom` and create the file `registrycredentials.json`.

By default, https is accepted as the server address.

```json
{
  "username": "<username>",
  "password": "<password>",
  "serveraddress": "<serveraddress>",
  "plain-http": false,
  "insecure": false,
}
```

A http-only registry (e.g. a local registry) can be accessed by set the `plain-http` field to `true`.

To access an https registry without a TLS certificate check (e.g. for a self signed certificate) you can set the field `insecure` to `true`.

## File based app installation

You can install the app offline via files, in addition to installation of an app via a docker registry.

The offline installation, requires you to use the `uc-aom-packager` in combination with the `pull` command and the `--extract=false` option.
Both are used to store the app on your local filesystem.
Example:

```sh
docker run -it --rm --pull=always \
    --mount src=/home/apps/example,target=/tmp/app-example,type=bind \
    wmucdev.azurecr.io/u-control/uc-aom-packager:0 uc-aom-packager \
    pull
    -t /tmp/app-example/target-credentials.json
    -o /tmp/app-example/output
    -v
    --version 0.1.0-1
    --extract=false
```

The output folder used by the `pull` command can be copied to the specific folder `/var/cache/uc-aom/drop-in/` on the device.

Now, if you [restart the service](#restarting-the-service) the apps represented by the copied files will be installed.

## Filtering apps based on names

To reduce loading times of the dialog when clicking `+ Install App`, you can add a whitelist to filter the apps by their repository-name.

Create a file `/var/lib/uc-aom/config.json` and provide a list of regex expressions, then [restart uc-aom](#restarting-the-service). If the apps repository-name matches *any* of the rules it will be included. The repository-name is not the apps title you see in the dialog!

```json
{
    "appsAllowedList": [
        ".*node-red.*",
        "test.*",
    ]
}
```

The example file would include all apps with a repo-name that starts with `test` *or* that contains `node-red`.
The regex example can be found [here](https://regexr.com/83h2s).


## Restarting the service

Changes will take effect after you restart the service (`uc-aom`) . This can be done by using the following command:

- Restart the service by entering '`systemctl restart uc-aom`' on the command line.

## Compatibility matrix

There are several versions of the manifest file format

This table shows which manifest file versions support specific device releases and packager.

| Manifest file format | Device release | uc-aom-packager release |
| :------------------- | :------------- | :---------------------- |
| 0.1                  | 1.16.0+        | 0.1.0+                  |
| 0.2                  | 2.0.0+         | 0.4.0+                  |
