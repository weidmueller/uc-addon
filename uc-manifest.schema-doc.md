# Manifest file structure

- [1. [Required] Property `root > manifestVersion`](#manifestVersion)
- [2. [Required] Property `root > version`](#version)
- [3. [Required] Property `root > title`](#title)
- [4. [Required] Property `root > description`](#description)
- [5. [Required] Property `root > logo`](#logo)
- [6. [Optional] Property `root > vendor`](#vendor)
  - [6.1. [Optional] Property `root > vendor > name`](#vendor_name)
  - [6.2. [Optional] Property `root > vendor > url`](#vendor_url)
  - [6.3. [Optional] Property `root > vendor > email`](#vendor_email)
  - [6.4. [Optional] Property `root > vendor > street`](#vendor_street)
  - [6.5. [Optional] Property `root > vendor > zip`](#vendor_zip)
  - [6.6. [Optional] Property `root > vendor > city`](#vendor_city)
  - [6.7. [Optional] Property `root > vendor > country`](#vendor_country)
- [7. [Required] Property `root > services`](#services)
  - [7.1. [Optional]Pattern Property `root > services > ^[a-zA-Z0-9]+$`](#services_pattern1)
    - [7.1.1. [Required] Property `root > services > ^[a-zA-Z0-9]+$ > type`](#services_pattern1_type)
    - [7.1.2. [Required] Property `root > services > ^[a-zA-Z0-9]+$ > config`](#services_pattern1_config)
- [8. [Optional] Property `root > environments`](#environments)
  - [8.1. [Optional]Pattern Property `root > environments > ^[a-zA-Z0-9]+$`](#environments_pattern1)
    - [8.1.1. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > type`](#environments_pattern1_type)
    - [8.1.2. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > config`](#environments_pattern1_config)
      - [8.1.2.1. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > config > volumes`](#environments_pattern1_config_volumes)
      - [8.1.2.2. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > config > networks`](#environments_pattern1_config_networks)
- [9. [Optional] Property `root > settings`](#settings)
  - [9.1. [Optional] Property `root > settings > environmentVariables`](#settings_environmentVariables)
    - [9.1.1. root > settings > environmentVariables > environmentVariables items](#autogenerated_heading_2)
      - [9.1.1.1. Property `root > settings > environmentVariables > environmentVariables items > name`](#settings_environmentVariables_items_name)
      - [9.1.1.2. Property `root > settings > environmentVariables > environmentVariables items > label`](#settings_environmentVariables_items_label)
      - [9.1.1.3. Property `root > settings > environmentVariables > environmentVariables items > default`](#settings_environmentVariables_items_default)
      - [9.1.1.4. Property `root > settings > environmentVariables > environmentVariables items > description`](#settings_environmentVariables_items_description)
      - [9.1.1.5. Property `root > settings > environmentVariables > environmentVariables items > required`](#settings_environmentVariables_items_required)
      - [9.1.1.6. Property `root > settings > environmentVariables > environmentVariables items > pattern`](#settings_environmentVariables_items_pattern)
      - [9.1.1.7. Property `root > settings > environmentVariables > environmentVariables items > readonly`](#settings_environmentVariables_items_readonly)
      - [9.1.1.8. Property `root > settings > environmentVariables > environmentVariables items > select`](#settings_environmentVariables_items_select)
        - [9.1.1.8.1. root > settings > environmentVariables > environmentVariables items > select > select items](#autogenerated_heading_3)
          - [9.1.1.8.1.1. Property `root > settings > environmentVariables > environmentVariables items > select > select items > label`](#settings_environmentVariables_items_select_items_label)
          - [9.1.1.8.1.2. Property `root > settings > environmentVariables > environmentVariables items > select > select items > value`](#settings_environmentVariables_items_select_items_value)
          - [9.1.1.8.1.3. Property `root > settings > environmentVariables > environmentVariables items > select > select items > default`](#settings_environmentVariables_items_select_items_default)
- [10. [Optional] Property `root > publish`](#publish)
  - [10.1. [Optional]Pattern Property `root > publish > ^[a-zA-Z0-9]+$`](#publish_pattern1)
    - [10.1.1. [Required] Property `root > publish > ^[a-zA-Z0-9]+$ > from`](#publish_pattern1_from)
    - [10.1.2. [Required] Property `root > publish > ^[a-zA-Z0-9]+$ > to`](#publish_pattern1_to)
  - [10.2. [Optional]Pattern Property `root > publish > additionalProperties`](#publish_pattern2)
- [11. [Required] Property `root > platform`](#platform)
  - [11.1. root > platform > platform items](#autogenerated_heading_4)

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** Schema for the u-create manifest

| Property                               | Pattern | Type            | Deprecated | Definition | Title/Description                                                                    |
| -------------------------------------- | ------- | --------------- | ---------- | ---------- | ------------------------------------------------------------------------------------ |
| + [manifestVersion](#manifestVersion ) | No      | string          | No         | -          | The version of the manifest                                                          |
| + [version](#version )                 | No      | string          | No         | -          | The version of the add-on, i.e. 1.0.0-1                                              |
| + [title](#title )                     | No      | string          | No         | -          | The title of the add-on will preferably be short                                     |
| + [description](#description )         | No      | string          | No         | -          | description will provide a more lengthy explanation about the purpose of the add ... |
| + [logo](#logo )                       | No      | string          | No         | -          | Path to the logo based on the root path. The logo should be at least 128 x 128 p ... |
| - [vendor](#vendor )                   | No      | object          | No         | -          | Add-ons vendor information                                                           |
| + [services](#services )               | No      | object          | No         | -          | services definition contains configuration that is applied to each add-on servic ... |
| - [environments](#environments )       | No      | object          | No         | -          | The environments object includes the different environment settings for the defi ... |
| - [settings](#settings )               | No      | object          | No         | -          | The settings section defines the editable values of an add-on                        |
| - [publish](#publish )                 | No      | object          | No         | -          | Publish one or more proxy routes where the add-on will be accessible                 |
| + [platform](#platform )               | No      | array of string | No         | -          | -                                                                                    |
|                                        |         |                 |            |            |                                                                                      |

## <a name="manifestVersion"></a>1. [Required] Property `root > manifestVersion`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** The version of the manifest

| Restrictions                      |                                                                                                       |
| --------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Must match regular expression** | ```^[0-9]+\.?[0-9]+?$``` [Test](https://regex101.com/?regex=%5E%5B0-9%5D%2B%5C.%3F%5B0-9%5D%2B%3F%24) |
|                                   |                                                                                                       |

## <a name="version"></a>2. [Required] Property `root > version`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** The version of the add-on, i.e. 1.0.0-1

| Restrictions                      |                                                                                                                                                                                                                                                                                                           |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Must match regular expression** | ```^([0-9]+\.)+([0-9]+)(-(alpha\|beta\|rc)\.[0-9]+)?(-[0-9]+(-(alpha\|beta\|rc)\.[0-9]+)?)$``` [Test](https://regex101.com/?regex=%5E%28%5B0-9%5D%2B%5C.%29%2B%28%5B0-9%5D%2B%29%28-%28alpha%7Cbeta%7Crc%29%5C.%5B0-9%5D%2B%29%3F%28-%5B0-9%5D%2B%28-%28alpha%7Cbeta%7Crc%29%5C.%5B0-9%5D%2B%29%3F%29%24) |
|                                   |                                                                                                                                                                                                                                                                                                           |

## <a name="title"></a>3. [Required] Property `root > title`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** The title of the add-on will preferably be short

## <a name="description"></a>4. [Required] Property `root > description`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** description will provide a more lengthy explanation about the purpose of the add-on

## <a name="logo"></a>5. [Required] Property `root > logo`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Path to the logo based on the root path. The logo should be at least 128 x 128 pixels.

## <a name="vendor"></a>6. [Optional] Property `root > vendor`

| Type                      | `object`                                                |
| ------------------------- | ------------------------------------------------------- |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |
|                           |                                                         |

**Description:** Add-ons vendor information

| Property                      | Pattern | Type   | Deprecated | Definition | Title/Description                              |
| ----------------------------- | ------- | ------ | ---------- | ---------- | ---------------------------------------------- |
| - [name](#vendor_name )       | No      | string | No         | -          | Name of the vendor                             |
| - [url](#vendor_url )         | No      | string | No         | -          | Website url of the vendor                      |
| - [email](#vendor_email )     | No      | string | No         | -          | Email address of the vendor                    |
| - [street](#vendor_street )   | No      | string | No         | -          | Street address with house number of the vendor |
| - [zip](#vendor_zip )         | No      | string | No         | -          | The zip of the vendor                          |
| - [city](#vendor_city )       | No      | string | No         | -          | City of the vendor                             |
| - [country](#vendor_country ) | No      | string | No         | -          | Country of the vendor                          |
|                               |         |        |            |            |                                                |

### <a name="vendor_name"></a>6.1. [Optional] Property `root > vendor > name`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Name of the vendor

### <a name="vendor_url"></a>6.2. [Optional] Property `root > vendor > url`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Website url of the vendor

### <a name="vendor_email"></a>6.3. [Optional] Property `root > vendor > email`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Email address of the vendor

### <a name="vendor_street"></a>6.4. [Optional] Property `root > vendor > street`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Street address with house number of the vendor

### <a name="vendor_zip"></a>6.5. [Optional] Property `root > vendor > zip`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** The zip of the vendor

### <a name="vendor_city"></a>6.6. [Optional] Property `root > vendor > city`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** City of the vendor

### <a name="vendor_country"></a>6.7. [Optional] Property `root > vendor > country`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Country of the vendor

## <a name="services"></a>7. [Required] Property `root > services`

| Type                      | `object`                                                |
| ------------------------- | ------------------------------------------------------- |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |
|                           |                                                         |

**Description:** services definition contains configuration that is applied to each add-on service

| Property                                | Pattern | Type   | Deprecated | Definition | Title/Description                              |
| --------------------------------------- | ------- | ------ | ---------- | ---------- | ---------------------------------------------- |
| - [^[a-zA-Z0-9]+$](#services_pattern1 ) | Yes     | object | No         | -          | A definition of a service that will be started |
|                                         |         |        |            |            |                                                |

### <a name="services_pattern1"></a>7.1. [Optional]Pattern Property `root > services > ^[a-zA-Z0-9]+$`
> All property whose name matches the regular expression 
```^[a-zA-Z0-9]+$``` ([Test](https://regex101.com/?regex=%5E%5Ba-zA-Z0-9%5D%2B%24))
must respect the following conditions

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** A definition of a service that will be started

| Property                               | Pattern | Type             | Deprecated | Definition | Title/Description                                                                    |
| -------------------------------------- | ------- | ---------------- | ---------- | ---------- | ------------------------------------------------------------------------------------ |
| + [type](#services_pattern1_type )     | No      | enum (of string) | No         | -          | Define the type of the service. Only the value 'docker-compose' is supported at  ... |
| + [config](#services_pattern1_config ) | No      | object           | No         | -          | Defines the docker settings for this service based on the docker compose structu ... |
|                                        |         |                  |            |            |                                                                                      |

#### <a name="services_pattern1_type"></a>7.1.1. [Required] Property `root > services > ^[a-zA-Z0-9]+$ > type`

| Type | `enum (of string)` |
| ---- | ------------------ |
|      |                    |

**Description:** Define the type of the service. Only the value 'docker-compose' is supported at the moment

Must be one of:
* "docker-compose"

#### <a name="services_pattern1_config"></a>7.1.2. [Required] Property `root > services > ^[a-zA-Z0-9]+$ > config`

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** Defines the docker settings for this service based on the docker compose structure. Any setting names that contain an underscore '_' should be converted to camelCase, e.g. replace `network_mode` with `networkMode`.

## <a name="environments"></a>8. [Optional] Property `root > environments`

| Type                      | `object`                                                |
| ------------------------- | ------------------------------------------------------- |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |
|                           |                                                         |

**Description:** The environments object includes the different environment settings for the defined services.

| Property                                    | Pattern | Type   | Deprecated | Definition | Title/Description              |
| ------------------------------------------- | ------- | ------ | ---------- | ---------- | ------------------------------ |
| - [^[a-zA-Z0-9]+$](#environments_pattern1 ) | Yes     | object | No         | -          | A definition of an environment |
|                                             |         |        |            |            |                                |

### <a name="environments_pattern1"></a>8.1. [Optional]Pattern Property `root > environments > ^[a-zA-Z0-9]+$`
> All property whose name matches the regular expression 
```^[a-zA-Z0-9]+$``` ([Test](https://regex101.com/?regex=%5E%5Ba-zA-Z0-9%5D%2B%24))
must respect the following conditions

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** A definition of an environment

| Property                                   | Pattern | Type             | Deprecated | Definition | Title/Description                                                                    |
| ------------------------------------------ | ------- | ---------------- | ---------- | ---------- | ------------------------------------------------------------------------------------ |
| - [type](#environments_pattern1_type )     | No      | enum (of string) | No         | -          | Define the type of the volume. Type 'docker-compose' will create and associate w ... |
| - [config](#environments_pattern1_config ) | No      | object           | No         | -          | Defines the docker environment settings based on the docker compose structure        |
|                                            |         |                  |            |            |                                                                                      |

#### <a name="environments_pattern1_type"></a>8.1.1. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > type`

| Type | `enum (of string)` |
| ---- | ------------------ |
|      |                    |

**Description:** Define the type of the volume. Type 'docker-compose' will create and associate when starting the container. Only the value 'docker-compose' is supported at the moment

Must be one of:
* "docker-compose"

#### <a name="environments_pattern1_config"></a>8.1.2. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > config`

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** Defines the docker environment settings based on the docker compose structure

| Property                                              | Pattern | Type   | Deprecated | Definition | Title/Description                                              |
| ----------------------------------------------------- | ------- | ------ | ---------- | ---------- | -------------------------------------------------------------- |
| - [volumes](#environments_pattern1_config_volumes )   | No      | object | No         | -          | Docker Volumes settings based on the docker compose structure  |
| - [networks](#environments_pattern1_config_networks ) | No      | object | No         | -          | Docker networks settings based on the docker compose structure |
|                                                       |         |        |            |            |                                                                |

##### <a name="environments_pattern1_config_volumes"></a>8.1.2.1. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > config > volumes`

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** Docker Volumes settings based on the docker compose structure

##### <a name="environments_pattern1_config_networks"></a>8.1.2.2. [Optional] Property `root > environments > ^[a-zA-Z0-9]+$ > config > networks`

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** Docker networks settings based on the docker compose structure

## <a name="settings"></a>9. [Optional] Property `root > settings`

| Type                      | `object`                                                |
| ------------------------- | ------------------------------------------------------- |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |
|                           |                                                         |

**Description:** The settings section defines the editable values of an add-on

| Property                                                  | Pattern | Type            | Deprecated | Definition | Title/Description                      |
| --------------------------------------------------------- | ------- | --------------- | ---------- | ---------- | -------------------------------------- |
| - [environmentVariables](#settings_environmentVariables ) | No      | array of object | No         | -          | Defines editable environment variables |
|                                                           |         |                 |            |            |                                        |

### <a name="settings_environmentVariables"></a>9.1. [Optional] Property `root > settings > environmentVariables`

| Type | `array of object` |
| ---- | ----------------- |
|      |                   |

**Description:** Defines editable environment variables

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |
|                      |                    |

| Each item of this array must be                                    | Description |
| ------------------------------------------------------------------ | ----------- |
| [environmentVariables items](#settings_environmentVariables_items) | -           |
|                                                                    |             |

#### <a name="autogenerated_heading_2"></a>9.1.1. root > settings > environmentVariables > environmentVariables items

| Type                      | `object`                                                |
| ------------------------- | ------------------------------------------------------- |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |
|                           |                                                         |

| Property                                                           | Pattern | Type            | Deprecated | Definition | Title/Description                                                            |
| ------------------------------------------------------------------ | ------- | --------------- | ---------- | ---------- | ---------------------------------------------------------------------------- |
| - [name](#settings_environmentVariables_items_name )               | No      | string          | No         | -          | Name of the environment variable                                             |
| - [label](#settings_environmentVariables_items_label )             | No      | string          | No         | -          | Label of the environment variable edit field                                 |
| - [default](#settings_environmentVariables_items_default )         | No      | string          | No         | -          | Default value of the environment variable                                    |
| - [description](#settings_environmentVariables_items_description ) | No      | string          | No         | -          | Description of the environment variable                                      |
| - [required](#settings_environmentVariables_items_required )       | No      | boolean         | No         | -          | Optional boolean flag that will apply the required validator                 |
| - [pattern](#settings_environmentVariables_items_pattern )         | No      | string          | No         | -          | Optional regex pattern that will apply the pattern validator                 |
| - [readonly](#settings_environmentVariables_items_readonly )       | No      | boolean         | No         | -          | Optional boolean if the environment variable should be displayed as readonly |
| - [select](#settings_environmentVariables_items_select )           | No      | array of object | No         | -          | Optional select options that will display a select input                     |
|                                                                    |         |                 |            |            |                                                                              |

##### <a name="settings_environmentVariables_items_name"></a>9.1.1.1. Property `root > settings > environmentVariables > environmentVariables items > name`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Name of the environment variable

##### <a name="settings_environmentVariables_items_label"></a>9.1.1.2. Property `root > settings > environmentVariables > environmentVariables items > label`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Label of the environment variable edit field

##### <a name="settings_environmentVariables_items_default"></a>9.1.1.3. Property `root > settings > environmentVariables > environmentVariables items > default`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Default value of the environment variable

##### <a name="settings_environmentVariables_items_description"></a>9.1.1.4. Property `root > settings > environmentVariables > environmentVariables items > description`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Description of the environment variable

##### <a name="settings_environmentVariables_items_required"></a>9.1.1.5. Property `root > settings > environmentVariables > environmentVariables items > required`

| Type | `boolean` |
| ---- | --------- |
|      |           |

**Description:** Optional boolean flag that will apply the required validator

##### <a name="settings_environmentVariables_items_pattern"></a>9.1.1.6. Property `root > settings > environmentVariables > environmentVariables items > pattern`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** Optional regex pattern that will apply the pattern validator

##### <a name="settings_environmentVariables_items_readonly"></a>9.1.1.7. Property `root > settings > environmentVariables > environmentVariables items > readonly`

| Type | `boolean` |
| ---- | --------- |
|      |           |

**Description:** Optional boolean if the environment variable should be displayed as readonly

##### <a name="settings_environmentVariables_items_select"></a>9.1.1.8. Property `root > settings > environmentVariables > environmentVariables items > select`

| Type | `array of object` |
| ---- | ----------------- |
|      |                   |

**Description:** Optional select options that will display a select input

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |
|                      |                    |

| Each item of this array must be                                   | Description |
| ----------------------------------------------------------------- | ----------- |
| [select items](#settings_environmentVariables_items_select_items) | -           |
|                                                                   |             |

##### <a name="autogenerated_heading_3"></a>9.1.1.8.1. root > settings > environmentVariables > environmentVariables items > select > select items

| Type                      | `object`                                                |
| ------------------------- | ------------------------------------------------------- |
| **Additional properties** | [[Not allowed]](# "Additional Properties not allowed.") |
|                           |                                                         |

| Property                                                                | Pattern | Type    | Deprecated | Definition | Title/Description |
| ----------------------------------------------------------------------- | ------- | ------- | ---------- | ---------- | ----------------- |
| + [label](#settings_environmentVariables_items_select_items_label )     | No      | string  | No         | -          | -                 |
| + [value](#settings_environmentVariables_items_select_items_value )     | No      | string  | No         | -          | -                 |
| - [default](#settings_environmentVariables_items_select_items_default ) | No      | boolean | No         | -          | -                 |
|                                                                         |         |         |            |            |                   |

##### <a name="settings_environmentVariables_items_select_items_label"></a>9.1.1.8.1.1. Property `root > settings > environmentVariables > environmentVariables items > select > select items > label`

| Type | `string` |
| ---- | -------- |
|      |          |

##### <a name="settings_environmentVariables_items_select_items_value"></a>9.1.1.8.1.2. Property `root > settings > environmentVariables > environmentVariables items > select > select items > value`

| Type | `string` |
| ---- | -------- |
|      |          |

##### <a name="settings_environmentVariables_items_select_items_default"></a>9.1.1.8.1.3. Property `root > settings > environmentVariables > environmentVariables items > select > select items > default`

| Type | `boolean` |
| ---- | --------- |
|      |           |

## <a name="publish"></a>10. [Optional] Property `root > publish`

| Type                      | `object`                                                                                              |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Additional properties** | [[Should-conform]](#publish_pattern2 "Each additional property must conform to the following schema") |
|                           |                                                                                                       |

**Description:** Publish one or more proxy routes where the add-on will be accessible

| Property                                     | Pattern | Type   | Deprecated | Definition | Title/Description                                                            |
| -------------------------------------------- | ------- | ------ | ---------- | ---------- | ---------------------------------------------------------------------------- |
| - [^[a-zA-Z0-9]+$](#publish_pattern1 )       | Yes     | object | No         | -          | A specific proxy route from an internal origin to a publicly accessible path |
| - [additionalProperties](#publish_pattern2 ) | Yes     | object | No         | -          | -                                                                            |
|                                              |         |        |            |            |                                                                              |

### <a name="publish_pattern1"></a>10.1. [Optional]Pattern Property `root > publish > ^[a-zA-Z0-9]+$`
> All property whose name matches the regular expression 
```^[a-zA-Z0-9]+$``` ([Test](https://regex101.com/?regex=%5E%5Ba-zA-Z0-9%5D%2B%24))
must respect the following conditions

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

**Description:** A specific proxy route from an internal origin to a publicly accessible path

| Property                          | Pattern | Type   | Deprecated | Definition | Title/Description                                                                    |
| --------------------------------- | ------- | ------ | ---------- | ---------- | ------------------------------------------------------------------------------------ |
| + [from](#publish_pattern1_from ) | No      | string | No         | -          | An absolute URL consisting of protocol, origin host and port e.g. http://localho ... |
| + [to](#publish_pattern1_to )     | No      | string | No         | -          | A relative URL path e.g. /home, which will be prefixed with the add-on name, i.e ... |
|                                   |         |        |            |            |                                                                                      |

#### <a name="publish_pattern1_from"></a>10.1.1. [Required] Property `root > publish > ^[a-zA-Z0-9]+$ > from`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** An absolute URL consisting of protocol, origin host and port e.g. http://localhost:8456

#### <a name="publish_pattern1_to"></a>10.1.2. [Required] Property `root > publish > ^[a-zA-Z0-9]+$ > to`

| Type | `string` |
| ---- | -------- |
|      |          |

**Description:** A relative URL path e.g. /home, which will be prefixed with the add-on name, i.e. add-on-name/home

### <a name="publish_pattern2"></a>10.2. [Optional]Pattern Property `root > publish > additionalProperties`
> All property whose name matches the regular expression 
```additionalProperties``` ([Test](https://regex101.com/?regex=additionalProperties))
must respect the following conditions

| Type                      | `object`                                                                  |
| ------------------------- | ------------------------------------------------------------------------- |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
|                           |                                                                           |

## <a name="platform"></a>11. [Required] Property `root > platform`

| Type | `array of string` |
| ---- | ----------------- |
|      |                   |

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |
|                      |                    |

| Each item of this array must be   | Description |
| --------------------------------- | ----------- |
| [platform items](#platform_items) | -           |
|                                   |             |

### <a name="autogenerated_heading_4"></a>11.1. root > platform > platform items

| Type | `string` |
| ---- | -------- |
|      |          |

| Restrictions                      |                                                             |
| --------------------------------- | ----------------------------------------------------------- |
| **Must match regular expression** | ```uc[mg]``` [Test](https://regex101.com/?regex=uc%5Bmg%5D) |
|                                   |                                                             |

----------------------------------------------------------------------------------------------------------------------------
Generated using [json-schema-for-humans](https://github.com/coveooss/json-schema-for-humans) on 2022-05-23 at 07:46:06 +0000