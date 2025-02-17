# App port list

This list documents the used dockerports within the 65280-65535 port range.

| Port number   | application name                                                             | reverse proxy name         |
| ------------- | ---------------------------------------------------------------------------- | -------------------------- |
| 123           | u-os-app-chrony and uc-addon-chrony (public NTP Server port)                 |                            |
| 1740 - 1743   | Codesys UDP                                                                  |                            |
| 4840          | Codesys OPC UA Server                                                        |                            |
| 11740 - 11743 | Codesys TCP                                                                  |                            |
| 8888          | anyviz                                                                       | /anyviz                    |
| 43981         | u-os-app-rexygen (Connection to Rexygen Studio via a custom binary protocol) | -                          |
| 50051         | ngnix                                                                        |                            |
| 50052         | uc-service-manager                                                           |                            |
| 50062         | uc-modbus-slave                                                              |                            |
| 50072         | uc-opc-ua                                                                    |                            |
| 50082         | uc-information-service                                                       |                            |
| 50092         | uc-iam                                                                       |                            |
| 50100         | uc-addon                                                                     |                            |
| 65280         | u-os-app-crosser                                                             | -                          |
| 65283         | u-os-app-crosser                                                             | -                          |
| 65290         | u-os-app-chrony and uc-addon-chrony (webserver port)                         | /                          |
| 65300         | uc-addon-procon-web-es                                                       | -                          |
| 65301         | uc-addon-procon-web-es                                                       | /sysm                      |
| 16620         | uc-addon-procon-web-es                                                       | -                          |
| 16800         | uc-addon-procon-web-es                                                       | -                          |
| 16810         | uc-addon-procon-web-es                                                       | -                          |
| 65302         | uc-addon-web-ssh                                                             |                            |
| 65305         | u-os-app-procon-connect                                                      | /                          |
| 65310         | uc-addon-telemetry                                                           | /tele                      |
| 65320         | uc-addon-easyconnect-iiot                                                    | /eacc                      |
| 65321         | uc-addon-easyconnect-iiot                                                    | -                          |
| 65330         | uc-addon-portainer                                                           | -                          |
| 65333         | uc-addon-portainer                                                           | /portainer                 |
| 65340         | uc-addon-filebrowser                                                         | /                          |
| 65350         | uc-addon-flecs                                                               | /                          |
| 65360         | uc-addon-nodered                                                             | /red                       |
| 65362         | u-os-app-node-red-u-sense                                                    | /red                       |
| 65370         | u-os-app-siemens-ied (Public port of the Siemens Service)                    | -                          |
| 65371         | u-os-app-siemens-ied (Redirect service)                                      | /                          |
| 65380         | u-os-app-rexygen                                                             | /                          |
| 65390         | u-os-app-usense (NATS-Server)                                                | /                          |
| 65391         | u-os-app-usense (gRPC)                                                       | /                          |
| 65392         | u-os-app-usense (gRPC web proxy)                                             | /                          |
| 65393         | u-os-app-usense (Caddy)                                                      | /                          |
| 65400         | u-os-app-nupano                                                              | /                          |
| 65410         | u-os-app-u-sense-platform (Webserver)                                        | /                          |
| 65411         | u-os-app-u-sense-platform (MQTT Broker, local)                               | /                          |
| 65420         | u-os-app-swarmguard-agent                                                    | /home                      |
| 65530         | u-os-app-codesys (Codesys WebServer HTTP)                                    | /                          |
| 65531         | u-os-app-codesys (Codesys WebServer HTTPS)                                   | -                          |
| 65532         | u-os-app-codesys (CODESYS Visualization Proxy)                               | /application/visualization |
| 65533         | u-os-app-registry registry                                                   | -                          |
| 65534         | u-os-app-registry-browser                                                    | /app-hub                   |
