# App

With apps you can tailor Weidmueller devices to your needs.

## Manifest

Meta-information about an app are stored in the manifest.
Please have a look into the [manifest documentation](./uc-manifest.schema-doc.md).

## App Packager

To publish an app you need to set up the app packager.
Please see the [USER_GUIDE](./USER_GUIDE.md) for details.

## Reverse Proxy

The apps installed on u-OS devices are protected by an [nginx](https://nginx.org/) reverse proxy.

The reverse proxy handles the identity and access management (IAM). Additionally, it acts as an SSL-Termination for a secure HTTPS-connection.

The uc-aom generates an [nginx](https://nginx.org/) configuration for each app during installation.

Specifically, uc-aom uses the configuration directives from the module [ngx_http_proxy_module](http://nginx.org/en/docs/http/ngx_http_proxy_module.html).

Please review the directive default values if you receive communication errors, e.g. timeouts from nginx.

The following is an example of the currently generated configuration:

```nginx
# {"com.weidmueller.uc.aom.reverse-proxy.version":"0.2.0","com.weidmueller.uc.aom.version":"0.5.3"}
location /app-example/ui {

    return 301 $scheme://$host/app-example/ui/$request_uri;

    location /app-example/ui/ {
        proxy_pass http://127.0.0.1:65000/;

        proxy_http_version 1.1;

        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection $connection_upgrade;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Host $host;
        proxy_set_header X-Forwarded-Port $server_port;

        client_max_body_size 0;
        client_body_timeout 30m;
    }
}
```

Your app service has the possibility to override the nginx default behavior by using special [X-accel](https://www.nginx.com/resources/wiki/start/topics/examples/x-accel/#special-headers) header fields.

If you are using HTTP streaming such as [Server-sent events](https://html.spec.whatwg.org/multipage/server-sent-events.html) (SSE) you probably need to disable the nginx proxy buffering, so that the request is sent immediately to the client.

To achieve this, set the value of the header field *X-Accel-Buffering* to *no*. Otherwise, the individual chunks will be sent in a bulk response from nginx to the client.

Have a look to the [proxy_buffering](http://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_buffering) directive for more information on the topic.
