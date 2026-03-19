Turtle photo-id Data Dictionary
This catalog describes the structure, meaning, and rules of data in a the BH photo-id database. It's relevance is in ensuring that data is comprehended, managed, and used consistently across the organization. It improves data clarity, quality, consistency, collaboration, and analysis, thus remaining essential for managing datasets and information systems within Bahari Hai.

#### turtle_sighting
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| turtle_sighting_id | varchar | 8 | No | TS00001 | Alphanumeric, unique | Unique ID for each sighting |
| survey_datetime | datetime | — | No | 2025-06-01 10:30:00 | YYYY-MM-DD HH:MM:SS | Date and time of observation |
| obsever_id | varchar | 8 | No | OBS001 | Alphanumeric | Observer/data collector ID |
| tide_cycle_id | varchar | 8 | No | TC01 | FK reference | Tide cycle reference |
| tide_level_id | varchar | 8 | No | TL01 | FK reference | Tide level reference |
| visibility_id | varchar | 8 | Yes | VIS01 | FK reference | Visibility condition |
| turtle_sighting_depth_m | int | — | Yes | 5 | Integer ≥ 0 | Depth in meters |
| site_id | varchar | 8 | No | SITE01 | Alphanumeric | Observation site ID |
| lat_long | nvarchar | 100 | Yes | -3.123,40.123 | "lat,lon" decimal format | Geographic coordinates |
| individual_id | varchar | 8 | No | IND0001 | FK reference | Linked turtle individual |
| age | varchar | 20 | No | Adult | Juvenile, Subadult, Adult | Age class |
| estimate_length_cm | int | — | No | 75 | Integer ≥ 0 | Estimated turtle length (cm) |
| turtle_behaviour_id | varchar | 8 | No | BHV01 | FK reference | Behaviour reference |
| image_right | varchar | 100 | No | right_001.jpg | File path / URL | Right-side image |
| image_left | varchar | 100 | No | left_001.jpg | File path / URL | Left-side image |
| image_top | varchar | 100 | No | top_001.jpg | File path / URL | Top-view image |
| is_fibro | bit | — | Yes | 1 | 0 = No, 1 = Yes | Fibropapillomatosis indicator |
| comment | varchar | 250 | Yes | Healthy individual | Free text | Additional notes |

---

#### foraging_ground
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| individual_id | varchar | 8 | No | IND0001 | Alphanumeric, unique | Unique identifier for each turtle individual |
| name | varchar | 20 | Yes | Amina | Free text | Name or label assigned to the turtle |
| sex | varchar | 8 | Yes | Female | Male, Female, Unknown | Sex of the turtle |
| iot_id | varchar | 20 | Yes | IOT123456 | Alphanumeric | IoT tracking device identifier |
| bh_id | varchar | 20 | No | BH001 | Alphanumeric | Beach or habitat identifier |
| turtle_id | varchar | 8 | Yes | T001 | Alphanumeric | External or legacy turtle ID |

---

####  tide_cycle

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| tide_cycle_id | varchar | 8 | No | TC01 | Alphanumeric | Unique tide cycle ID |
| name | varchar | 20 | No | Spring | Spring, Neap | Tide cycle type |

---

####  tide_level
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| tide_level_id | varchar | 8 | No | TL01 | Alphanumeric | Unique tide level ID |
| name | varchar | 20 | No | High | High, Low, Mid | Tide level |

---

####  behaviour
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| behaviour_id | varchar | 8 | No | BHV01 | Alphanumeric | Unique behaviour ID |
| name | varchar | 20 | No | Feeding | Feeding, Resting, Swimming | Turtle behaviour |

---

####  individual
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| individual_id | varchar | 8 | No | IND0001 | Alphanumeric, unique | Unique identifier for each turtle individual |
| name | varchar | 20 | Yes | Amina | Free text | Name or label assigned to the turtle |
| sex | varchar | 8 | Yes | Female | Male, Female, Unknown | Sex of the turtle |
| iot_id | varchar | 20 | Yes | IOT123456 | Alphanumeric | IoT tracking device identifier |
| bh_id | varchar | 20 | No | BH001 | Alphanumeric | Beach or habitat identifier |
| turtle_id | varchar | 8 | Yes | T001 | Alphanumeric | External or legacy turtle ID |

---

####  iot_number
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| iot_number_id | varchar | 8 | No | IOT001 | Alphanumeric | Unique IoT record ID |
| iot_id | varchar | 20 | No | IOT123456 | Alphanumeric | IoT device identifier |

---

####  tag_status
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| tag_status_id | int | — | No | 1 | Integer, unique | Unique tag status ID |
| tag_status_name | varchar | 20 | No | Active | Active, Lost, Replaced | Status of tag |

---
