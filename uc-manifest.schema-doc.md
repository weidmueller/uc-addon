# Manifest file structure

- [Manifest file structure](#manifest-file-structure)
  - [1. Property `Manifest file structure > manifestVersion`](#1-property-manifest-file-structure--manifestversion)
  - [2. Property `Manifest file structure > version`](#2-property-manifest-file-structure--version)
  - [3. Property `Manifest file structure > title`](#3-property-manifest-file-structure--title)
  - [4. Property `Manifest file structure > description`](#4-property-manifest-file-structure--description)
  - [5. Property `Manifest file structure > logo`](#5-property-manifest-file-structure--logo)
  - [6. Property `Manifest file structure > vendor`](#6-property-manifest-file-structure--vendor)
    - [6.1. Property `Manifest file structure > vendor > name`](#61-property-manifest-file-structure--vendor--name)
    - [6.2. Property `Manifest file structure > vendor > url`](#62-property-manifest-file-structure--vendor--url)
    - [6.3. Property `Manifest file structure > vendor > email`](#63-property-manifest-file-structure--vendor--email)
    - [6.4. Property `Manifest file structure > vendor > street`](#64-property-manifest-file-structure--vendor--street)
    - [6.5. Property `Manifest file structure > vendor > zip`](#65-property-manifest-file-structure--vendor--zip)
    - [6.6. Property `Manifest file structure > vendor > city`](#66-property-manifest-file-structure--vendor--city)
    - [6.7. Property `Manifest file structure > vendor > country`](#67-property-manifest-file-structure--vendor--country)
  - [7. Property `Manifest file structure > services`](#7-property-manifest-file-structure--services)
    - [7.1. Pattern Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$`](#71-pattern-property-manifest-file-structure--services--a-za-z0-9-)
      - [7.1.1. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > type`](#711-property-manifest-file-structure--services--a-za-z0-9---type)
      - [7.1.2. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > config`](#712-property-manifest-file-structure--services--a-za-z0-9---config)
        - [7.1.2.1. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > config > restart`](#7121-property-manifest-file-structure--services--a-za-z0-9---config--restart)
        - [7.1.2.2. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > config > image`](#7122-property-manifest-file-structure--services--a-za-z0-9---config--image)
  - [8. Property `Manifest file structure > environments`](#8-property-manifest-file-structure--environments)
    - [8.1. Pattern Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$`](#81-pattern-property-manifest-file-structure--environments--a-za-z0-9-)
      - [8.1.1. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > type`](#811-property-manifest-file-structure--environments--a-za-z0-9---type)
      - [8.1.2. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > config`](#812-property-manifest-file-structure--environments--a-za-z0-9---config)
        - [8.1.2.1. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > config > volumes`](#8121-property-manifest-file-structure--environments--a-za-z0-9---config--volumes)
        - [8.1.2.2. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > config > networks`](#8122-property-manifest-file-structure--environments--a-za-z0-9---config--networks)
  - [9. Property `Manifest file structure > settings`](#9-property-manifest-file-structure--settings)
    - [9.1. Property `Manifest file structure > settings > environmentVariables`](#91-property-manifest-file-structure--settings--environmentvariables)
      - [9.1.1. Manifest file structure \> settings \> environmentVariables \> environmentVariables items](#911-manifest-file-structure--settings--environmentvariables--environmentvariables-items)
        - [9.1.1.1. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > name`](#9111-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--name)
        - [9.1.1.2. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > label`](#9112-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--label)
        - [9.1.1.3. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > default`](#9113-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--default)
        - [9.1.1.4. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > description`](#9114-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--description)
        - [9.1.1.5. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > required`](#9115-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--required)
        - [9.1.1.6. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > pattern`](#9116-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--pattern)
        - [9.1.1.7. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > readonly`](#9117-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--readonly)
        - [9.1.1.8. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select`](#9118-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--select)
        - [9.1.1.8.1. Manifest file structure \> settings \> environmentVariables \> environmentVariables items \> select \> select items](#91181-manifest-file-structure--settings--environmentvariables--environmentvariables-items--select--select-items)
        - [9.1.1.8.1.1. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items > label`](#911811-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--select--select-items--label)
        - [9.1.1.8.1.2. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items > value`](#911812-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--select--select-items--value)
        - [9.1.1.8.1.3. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items > default`](#911813-property-manifest-file-structure--settings--environmentvariables--environmentvariables-items--select--select-items--default)
  - [10. Property `Manifest file structure > publish`](#10-property-manifest-file-structure--publish)
    - [10.1. Pattern Property `Manifest file structure > publish > ^[a-zA-Z0-9]+$`](#101-pattern-property-manifest-file-structure--publish--a-za-z0-9)
      - [10.1.1. Property `Manifest file structure > publish > ^[a-zA-Z0-9]+$ > from`](#1011-property-manifest-file-structure--publish--a-za-z0-9--from)
      - [10.1.2. Property `Manifest file structure > publish > ^[a-zA-Z0-9]+$ > to`](#1012-property-manifest-file-structure--publish--a-za-z0-9--to)
    - [10.2. Pattern Property `Manifest file structure > publish > additionalProperties`](#102-pattern-property-manifest-file-structure--publish--additionalproperties)
  - [11. Property `Manifest file structure > features`](#11-property-manifest-file-structure--features)
    - [11.1. Manifest file structure \> features \> features items](#111-manifest-file-structure--features--features-items)
      - [11.1.1. Property `Manifest file structure > features > features items > name`](#1111-property-manifest-file-structure--features--features-items--name)
      - [11.1.2. Property `Manifest file structure > features > features items > required`](#1112-property-manifest-file-structure--features--features-items--required)
  - [12. Property `Manifest file structure > platform`](#12-property-manifest-file-structure--platform)
    - [12.1. Manifest file structure \> platform \> platform items](#121-manifest-file-structure--platform--platform-items)

**Title:** Manifest file structure

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Schema for the u-create manifest

| Property                               | Pattern | Type            | Deprecated | Definition | Title/Description                                                                                                                                                                                                                                                                                                                               |
| -------------------------------------- | ------- | --------------- | ---------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| + [manifestVersion](#manifestVersion ) | No      | string          | No         | -          | The version of the manifest                                                                                                                                                                                                                                                                                                                     |
| + [version](#version )                 | No      | string          | No         | -          | The version of the app, i.e. 1.0.0-1                                                                                                                                                                                                                                                                                                            |
| + [title](#title )                     | No      | string          | No         | -          | The title of the app will preferably be short                                                                                                                                                                                                                                                                                                   |
| + [description](#description )         | No      | string          | No         | -          | description will provide a more lengthy explanation about the purpose of the app                                                                                                                                                                                                                                                                |
| + [logo](#logo )                       | No      | string          | No         | -          | Path to the logo based on the root path. The logo should be at least 128 x 128 pixels.                                                                                                                                                                                                                                                          |
| + [vendor](#vendor )                   | No      | object          | No         | -          | Apps vendor information                                                                                                                                                                                                                                                                                                                         |
| + [services](#services )               | No      | object          | No         | -          | services definition contains configuration that is applied to each app service                                                                                                                                                                                                                                                                  |
| - [environments](#environments )       | No      | object          | No         | -          | The environments object includes the different environment settings for the defined services.                                                                                                                                                                                                                                                   |
| - [settings](#settings )               | No      | object          | No         | -          | The settings section defines the editable values of an app                                                                                                                                                                                                                                                                                      |
| - [publish](#publish )                 | No      | object          | No         | -          | Publish one or more proxy routes where the app will be accessible                                                                                                                                                                                                                                                                               |
| - [features](#features )               | No      | array of object | No         | -          | Declares a single hardware or software feature that is used by the application. The purpose of a \`features\` declaration is to inform about the set of hardware and software features on which your application depends. The definition is based on android manifest: https://developer.android.com/guide/topics/manifest/uses-feature-element |
| + [platform](#platform )               | No      | array of string | No         | -          | -                                                                                                                                                                                                                                                                                                                                               |

## <a name="manifestVersion"></a>1. Property `Manifest file structure > manifestVersion`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** The version of the manifest

| Restrictions                      |                                                                                                       |
| --------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Must match regular expression** | ```^[0-9]+\.?[0-9]+?$``` [Test](https://regex101.com/?regex=%5E%5B0-9%5D%2B%5C.%3F%5B0-9%5D%2B%3F%24) |

## <a name="version"></a>2. Property `Manifest file structure > version`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** The version of the app, i.e. 1.0.0-1

| Restrictions                      |                                                                                                                                                                                                                                                                                                           |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Must match regular expression** | ```^([0-9]+\.)+([0-9]+)(-(alpha\|beta\|rc)\.[0-9]+)?(-[0-9]+(-(alpha\|beta\|rc)\.[0-9]+)?)$``` [Test](https://regex101.com/?regex=%5E%28%5B0-9%5D%2B%5C.%29%2B%28%5B0-9%5D%2B%29%28-%28alpha%7Cbeta%7Crc%29%5C.%5B0-9%5D%2B%29%3F%28-%5B0-9%5D%2B%28-%28alpha%7Cbeta%7Crc%29%5C.%5B0-9%5D%2B%29%3F%29%24) |

## <a name="title"></a>3. Property `Manifest file structure > title`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** The title of the app will preferably be short

## <a name="description"></a>4. Property `Manifest file structure > description`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** description will provide a more lengthy explanation about the purpose of the app

## <a name="logo"></a>5. Property `Manifest file structure > logo`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Path to the logo based on the root path. The logo should be at least 128 x 128 pixels.

| Restrictions                      |                                                                                                                  |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Must match regular expression** | ```^.+\.(jpg\|png\|jpeg\|svg)$``` [Test](https://regex101.com/?regex=%5E.%2B%5C.%28jpg%7Cpng%7Cjpeg%7Csvg%29%24) |

## <a name="vendor"></a>6. Property `Manifest file structure > vendor`

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | Yes                                                     |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

**Description:** Apps vendor information

| Property                      | Pattern | Type   | Deprecated | Definition | Title/Description                              |
| ----------------------------- | ------- | ------ | ---------- | ---------- | ---------------------------------------------- |
| + [name](#vendor_name )       | No      | string | No         | -          | Name of the vendor                             |
| + [url](#vendor_url )         | No      | string | No         | -          | Website url of the vendor                      |
| + [email](#vendor_email )     | No      | string | No         | -          | Email address of the vendor                    |
| + [street](#vendor_street )   | No      | string | No         | -          | Street address with house number of the vendor |
| + [zip](#vendor_zip )         | No      | string | No         | -          | The zip of the vendor                          |
| + [city](#vendor_city )       | No      | string | No         | -          | City of the vendor                             |
| + [country](#vendor_country ) | No      | string | No         | -          | Country of the vendor                          |

### <a name="vendor_name"></a>6.1. Property `Manifest file structure > vendor > name`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Name of the vendor

### <a name="vendor_url"></a>6.2. Property `Manifest file structure > vendor > url`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |
| **Format**   | `uri`    |

**Description:** Website url of the vendor

### <a name="vendor_email"></a>6.3. Property `Manifest file structure > vendor > email`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |
| **Format**   | `email`  |

**Description:** Email address of the vendor

### <a name="vendor_street"></a>6.4. Property `Manifest file structure > vendor > street`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Street address with house number of the vendor

### <a name="vendor_zip"></a>6.5. Property `Manifest file structure > vendor > zip`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** The zip of the vendor

### <a name="vendor_city"></a>6.6. Property `Manifest file structure > vendor > city`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** City of the vendor

### <a name="vendor_country"></a>6.7. Property `Manifest file structure > vendor > country`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Country of the vendor

## <a name="services"></a>7. Property `Manifest file structure > services`

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | Yes                                                     |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

**Description:** services definition contains configuration that is applied to each app service

| Property                                 | Pattern | Type   | Deprecated | Definition | Title/Description                              |
| ---------------------------------------- | ------- | ------ | ---------- | ---------- | ---------------------------------------------- |
| - [^[a-zA-Z0-9-]+$](#services_pattern1 ) | Yes     | object | No         | -          | A definition of a service that will be started |

### <a name="services_pattern1"></a>7.1. Pattern Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$`
> All properties whose name matches the regular expression
```^[a-zA-Z0-9-]+$``` ([Test](https://regex101.com/?regex=%5E%5Ba-zA-Z0-9-%5D%2B%24))
must respect the following conditions

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** A definition of a service that will be started

| Property                               | Pattern | Type             | Deprecated | Definition | Title/Description                                                                                                                                                                                                          |
| -------------------------------------- | ------- | ---------------- | ---------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| + [type](#services_pattern1_type )     | No      | enum (of string) | No         | -          | Define the type of the service. Only the value 'docker-compose' is supported at the moment                                                                                                                                 |
| + [config](#services_pattern1_config ) | No      | object           | No         | -          | Defines the docker settings for this service based on the docker compose structure. Any setting names that contain an underscore '_' should be converted to camelCase, e.g. replace \`network_mode\` with \`networkMode\`. |

#### <a name="services_pattern1_type"></a>7.1.1. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > type`

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | Yes                |

**Description:** Define the type of the service. Only the value 'docker-compose' is supported at the moment

Must be one of:
* "docker-compose"

#### <a name="services_pattern1_config"></a>7.1.2. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > config`

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Defines the docker settings for this service based on the docker compose structure. Any setting names that contain an underscore '_' should be converted to camelCase, e.g. replace `network_mode` with `networkMode`.

| Property                                        | Pattern | Type             | Deprecated | Definition | Title/Description                                                                                               |
| ----------------------------------------------- | ------- | ---------------- | ---------- | ---------- | --------------------------------------------------------------------------------------------------------------- |
| - [restart](#services_pattern1_config_restart ) | No      | enum (of string) | No         | -          | Defines the restart policy for the service. Restart policy 'always' is not allowed to prevent endless restarts. |
| + [image](#services_pattern1_config_image )     | No      | string           | No         | -          | Defines the name of the docker image of the service                                                             |

##### <a name="services_pattern1_config_restart"></a>7.1.2.1. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > config > restart`

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | No                 |

**Description:** Defines the restart policy for the service. Restart policy 'always' is not allowed to prevent endless restarts.

Must be one of:
* "no"
* "on-failure"
* "unless-stopped"

##### <a name="services_pattern1_config_image"></a>7.1.2.2. Property `Manifest file structure > services > ^[a-zA-Z0-9-]+$ > config > image`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Defines the name of the docker image of the service

## <a name="environments"></a>8. Property `Manifest file structure > environments`

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | No                                                      |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

**Description:** The environments object includes the different environment settings for the defined services.

| Property                                     | Pattern | Type   | Deprecated | Definition | Title/Description              |
| -------------------------------------------- | ------- | ------ | ---------- | ---------- | ------------------------------ |
| - [^[a-zA-Z0-9-]+$](#environments_pattern1 ) | Yes     | object | No         | -          | A definition of an environment |

### <a name="environments_pattern1"></a>8.1. Pattern Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$`
> All properties whose name matches the regular expression
```^[a-zA-Z0-9-]+$``` ([Test](https://regex101.com/?regex=%5E%5Ba-zA-Z0-9-%5D%2B%24))
must respect the following conditions

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** A definition of an environment

| Property                                   | Pattern | Type             | Deprecated | Definition | Title/Description                                                                                                                                                      |
| ------------------------------------------ | ------- | ---------------- | ---------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - [type](#environments_pattern1_type )     | No      | enum (of string) | No         | -          | Define the type of the volume. Type 'docker-compose' will create and associate when starting the container. Only the value 'docker-compose' is supported at the moment |
| - [config](#environments_pattern1_config ) | No      | object           | No         | -          | Defines the docker environment settings based on the docker compose structure                                                                                          |

#### <a name="environments_pattern1_type"></a>8.1.1. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > type`

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | No                 |

**Description:** Define the type of the volume. Type 'docker-compose' will create and associate when starting the container. Only the value 'docker-compose' is supported at the moment

Must be one of:
* "docker-compose"

#### <a name="environments_pattern1_config"></a>8.1.2. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > config`

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Defines the docker environment settings based on the docker compose structure

| Property                                              | Pattern | Type   | Deprecated | Definition | Title/Description                                              |
| ----------------------------------------------------- | ------- | ------ | ---------- | ---------- | -------------------------------------------------------------- |
| - [volumes](#environments_pattern1_config_volumes )   | No      | object | No         | -          | Docker Volumes settings based on the docker compose structure  |
| - [networks](#environments_pattern1_config_networks ) | No      | object | No         | -          | Docker networks settings based on the docker compose structure |

##### <a name="environments_pattern1_config_volumes"></a>8.1.2.1. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > config > volumes`

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Docker Volumes settings based on the docker compose structure

##### <a name="environments_pattern1_config_networks"></a>8.1.2.2. Property `Manifest file structure > environments > ^[a-zA-Z0-9-]+$ > config > networks`

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Docker networks settings based on the docker compose structure

## <a name="settings"></a>9. Property `Manifest file structure > settings`

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | No                                                      |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

**Description:** The settings section defines the editable values of an app

| Property                                                  | Pattern | Type            | Deprecated | Definition | Title/Description                      |
| --------------------------------------------------------- | ------- | --------------- | ---------- | ---------- | -------------------------------------- |
| - [environmentVariables](#settings_environmentVariables ) | No      | array of object | No         | -          | Defines editable environment variables |

### <a name="settings_environmentVariables"></a>9.1. Property `Manifest file structure > settings > environmentVariables`

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of object` |
| **Required** | No                |

**Description:** Defines editable environment variables

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                    | Description |
| ------------------------------------------------------------------ | ----------- |
| [environmentVariables items](#settings_environmentVariables_items) | -           |

#### <a name="autogenerated_heading_2"></a>9.1.1. Manifest file structure > settings > environmentVariables > environmentVariables items

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | No                                                      |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

| Property                                                           | Pattern | Type            | Deprecated | Definition | Title/Description                                                            |
| ------------------------------------------------------------------ | ------- | --------------- | ---------- | ---------- | ---------------------------------------------------------------------------- |
| + [name](#settings_environmentVariables_items_name )               | No      | string          | No         | -          | Name of the environment variable                                             |
| + [label](#settings_environmentVariables_items_label )             | No      | string          | No         | -          | Label of the environment variable edit field                                 |
| - [default](#settings_environmentVariables_items_default )         | No      | string          | No         | -          | Default value of the environment variable                                    |
| - [description](#settings_environmentVariables_items_description ) | No      | string          | No         | -          | Description of the environment variable                                      |
| - [required](#settings_environmentVariables_items_required )       | No      | boolean         | No         | -          | Optional boolean flag that will apply the required validator                 |
| - [pattern](#settings_environmentVariables_items_pattern )         | No      | string          | No         | -          | Optional regex pattern that will apply the pattern validator                 |
| - [readonly](#settings_environmentVariables_items_readonly )       | No      | boolean         | No         | -          | Optional boolean if the environment variable should be displayed as readonly |
| - [select](#settings_environmentVariables_items_select )           | No      | array of object | No         | -          | Optional select options that will display a select input                     |

##### <a name="settings_environmentVariables_items_name"></a>9.1.1.1. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > name`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Name of the environment variable

##### <a name="settings_environmentVariables_items_label"></a>9.1.1.2. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > label`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Label of the environment variable edit field

##### <a name="settings_environmentVariables_items_default"></a>9.1.1.3. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > default`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Default value of the environment variable

##### <a name="settings_environmentVariables_items_description"></a>9.1.1.4. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > description`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Description of the environment variable

##### <a name="settings_environmentVariables_items_required"></a>9.1.1.5. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > required`

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Optional boolean flag that will apply the required validator

##### <a name="settings_environmentVariables_items_pattern"></a>9.1.1.6. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > pattern`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Optional regex pattern that will apply the pattern validator

##### <a name="settings_environmentVariables_items_readonly"></a>9.1.1.7. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > readonly`

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Optional boolean if the environment variable should be displayed as readonly

##### <a name="settings_environmentVariables_items_select"></a>9.1.1.8. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select`

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of object` |
| **Required** | No                |

**Description:** Optional select options that will display a select input

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                   | Description |
| ----------------------------------------------------------------- | ----------- |
| [select items](#settings_environmentVariables_items_select_items) | -           |

##### <a name="autogenerated_heading_3"></a>9.1.1.8.1. Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | No                                                      |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

| Property                                                                | Pattern | Type    | Deprecated | Definition | Title/Description |
| ----------------------------------------------------------------------- | ------- | ------- | ---------- | ---------- | ----------------- |
| + [label](#settings_environmentVariables_items_select_items_label )     | No      | string  | No         | -          | -                 |
| + [value](#settings_environmentVariables_items_select_items_value )     | No      | string  | No         | -          | -                 |
| - [default](#settings_environmentVariables_items_select_items_default ) | No      | boolean | No         | -          | -                 |

##### <a name="settings_environmentVariables_items_select_items_label"></a>9.1.1.8.1.1. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items > label`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

##### <a name="settings_environmentVariables_items_select_items_value"></a>9.1.1.8.1.2. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items > value`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

##### <a name="settings_environmentVariables_items_select_items_default"></a>9.1.1.8.1.3. Property `Manifest file structure > settings > environmentVariables > environmentVariables items > select > select items > default`

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

## <a name="publish"></a>10. Property `Manifest file structure > publish`

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Publish one or more proxy routes where the app will be accessible

| Property                                     | Pattern | Type   | Deprecated | Definition | Title/Description                                                            |
| -------------------------------------------- | ------- | ------ | ---------- | ---------- | ---------------------------------------------------------------------------- |
| - [^[a-zA-Z0-9]+$](#publish_pattern1 )       | Yes     | object | No         | -          | A specific proxy route from an internal origin to a publicly accessible path |
| - [additionalProperties](#publish_pattern2 ) | Yes     | object | No         | -          | -                                                                            |

### <a name="publish_pattern1"></a>10.1. Pattern Property `Manifest file structure > publish > ^[a-zA-Z0-9]+$`
> All properties whose name matches the regular expression
```^[a-zA-Z0-9]+$``` ([Test](https://regex101.com/?regex=%5E%5Ba-zA-Z0-9%5D%2B%24))
must respect the following conditions

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** A specific proxy route from an internal origin to a publicly accessible path

| Property                          | Pattern | Type   | Deprecated | Definition | Title/Description                                                                            |
| --------------------------------- | ------- | ------ | ---------- | ---------- | -------------------------------------------------------------------------------------------- |
| + [from](#publish_pattern1_from ) | No      | string | No         | -          | An absolute URL consisting of protocol, origin host and port e.g. http://localhost:8456      |
| + [to](#publish_pattern1_to )     | No      | string | No         | -          | A relative URL path e.g. /home, which will be prefixed with the app name, i.e. app-name/home |

#### <a name="publish_pattern1_from"></a>10.1.1. Property `Manifest file structure > publish > ^[a-zA-Z0-9]+$ > from`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** An absolute URL consisting of protocol, origin host and port e.g. http://localhost:8456

#### <a name="publish_pattern1_to"></a>10.1.2. Property `Manifest file structure > publish > ^[a-zA-Z0-9]+$ > to`

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** A relative URL path e.g. /home, which will be prefixed with the app name, i.e. app-name/home

### <a name="publish_pattern2"></a>10.2. Pattern Property `Manifest file structure > publish > additionalProperties`
> All properties whose name matches the regular expression
```additionalProperties``` ([Test](https://regex101.com/?regex=additionalProperties))
must respect the following conditions

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

## <a name="features"></a>11. Property `Manifest file structure > features`

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of object` |
| **Required** | No                |

**Description:** Declares a single hardware or software feature that is used by the application. The purpose of a `features` declaration is to inform about the set of hardware and software features on which your application depends. The definition is based on android manifest: https://developer.android.com/guide/topics/manifest/uses-feature-element

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be   | Description |
| --------------------------------- | ----------- |
| [features items](#features_items) | -           |

### <a name="autogenerated_heading_4"></a>11.1. Manifest file structure > features > features items

|                           |                                                         |
| ------------------------- | ------------------------------------------------------- |
| **Type**                  | `object`                                                |
| **Required**              | No                                                      |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |

| Property                                | Pattern | Type             | Deprecated | Definition | Title/Description                                                                                                                               |
| --------------------------------------- | ------- | ---------------- | ---------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| + [name](#features_items_name )         | No      | enum (of string) | No         | -          | Specifies a single hardware or software feature used by the application, as a descriptor string.                                                |
| - [required](#features_items_required ) | No      | boolean          | No         | -          | Boolean value that indicates whether the application requires the feature specified in \`name\`. The default value if not declared is \`true\`. |

#### <a name="features_items_name"></a>11.1.1. Property `Manifest file structure > features > features items > name`

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | Yes                |

**Description:** Specifies a single hardware or software feature used by the application, as a descriptor string.

Must be one of:
* "ucontrol.software.root_access"

#### <a name="features_items_required"></a>11.1.2. Property `Manifest file structure > features > features items > required`

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Boolean value that indicates whether the application requires the feature specified in `name`. The default value if not declared is `true`.

## <a name="platform"></a>12. Property `Manifest file structure > platform`

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be   | Description |
| --------------------------------- | ----------- |
| [platform items](#platform_items) | -           |

### <a name="autogenerated_heading_5"></a>12.1. Manifest file structure > platform > platform items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

| Restrictions                      |                                                                 |
| --------------------------------- | --------------------------------------------------------------- |
| **Must match regular expression** | ```uc[amgu]``` [Test](https://regex101.com/?regex=uc%5Bamgu%5D) |

----------------------------------------------------------------------------------------------------------------------------
Generated using [json-schema-for-humans](https://github.com/coveooss/json-schema-for-humans) on 2023-11-15 at 10:03:24 +0000
