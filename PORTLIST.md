# App port list
This list documents the used dockerports within the 65280-65535 port range. 

| Port number | application name           | reverse proxy name |
|-------------|----------------------------|--------------------|
|  1740 - 1743| Codesys UDP                |                    |
|  4840       | Codesys OPC UA Server      |                    |
|  11740 - 11743| Codesys TCP              |                    |
|  8888       | anyviz                     | /anyviz		    |
| 50051       | ngnix                      |			        |
| 50052       | uc-service-manager         |			        |
| 50062       | uc-modbus-slave            |			        |
| 50072       | uc-opc-ua                  |			        |
| 50082       | uc-information-service     |			        |
| 50092       | uc-iam                     |			        |
| 50100       | uc-addon                   |			        |
| 65280       | uc-addon-crosser           | -                  |
| 65283       | uc-addon-crosser           | -                  |
| 65291       | uc-addon-crosser           | /                  |
| 65300       | uc-addon-procon-web-es     | -			            |
| 65301       | uc-addon-procon-web-es     | /sysm		          |
| 16620       | uc-addon-procon-web-es     | -		              |
| 16800       | uc-addon-procon-web-es     | -		              |
| 16810       | uc-addon-procon-web-es     | -		              |
| 65302       | uc-addon-web-ssh           |                    |
| 65310       | uc-addon-telemetry         | /tele		          |
| 65320       | uc-addon-easyconnect-iiot  | /eacc		          |
| 65321       | uc-addon-easyconnect-iiot  | -		              |
| 65325       | u-os-app-u-link	  	   | /		              |
| 65330       | uc-addon-portainer         | -                  |
| 65333       | uc-addon-portainer         | /portainer         |
| 65340       | uc-addon-filebrowser       | /                  |
| 65350       | uc-addon-flecs             | /		              |
| 65360       | uc-addon-nodered           | /red               |
| 65530       | uc-addon-codesys (Codesys WebServer HTTP)| /          |
| 65531       | Codesys WebServer HTTPS     | -                 |
| 65532       | uc-addon-codesys (reserved) | -                 |
