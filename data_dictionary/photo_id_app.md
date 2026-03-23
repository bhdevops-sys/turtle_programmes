Turtle photo-id Data Dictionary
This catalog describes the structure, meaning, and rules of data in a the BH photo-id database. It's relevance is in ensuring that data is comprehended, managed, and used consistently across the organization. It improves data clarity, quality, consistency, collaboration, and analysis, thus remaining essential for managing datasets and information systems within Bahari Hai.

#### turtle_sighting
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| turtle_sighting_id | varchar | 8 | No | TS00001 | Alphanumeric, unique | Unique ID for each sighting |
| survey_datetime | datetime | — | No | 2025-06-01 10:30:00 | YYYY-MM-DD HH:MM:SS | Date and time of observation |
| obsever_id | varchar | 8 | No | rty001 | Alphanumeric (FK) | Observer id. Reference to party (lookup table)|
| tide_cycle_id | varchar | 8 | No | 01 | Alphanumeric (FK) | Tide cycle. Reference to tide_cycle (lookup table) |
| tide_level_id | varchar | 8 | No | 01 | Alphanumeric (FK) | Tide level. Reference to tide_level (lookup table) |
| visibility_id | varchar | 8 | Yes | VIS01 | Alphanumeric (FK) | Visibility condition. Reference to visibility (lookup table) |
| turtle_sighting_depth_m | int | — | Yes | 5 | Integer ≥ 0 | Depth in meters |
| site_id | varchar | 8 | No | SITE01 | Alphanumeric (FK) | Observation site. Reference to site (lookup table) |
| lat_long | nvarchar | 100 | Yes | -3.123,40.123 | "lat,lon" decimal format | Geographic coordinates (decimal degree)|
| individual_id | varchar | 8 | No | tdr0001 | Alphanumeric (FK)| Reference to individual (lookup table) |
| age | varchar | 20 | No | Adult | Juvenile, Subadult, Adult | Age class |
| estimate_length_cm | int | — | No | 75 | Integer ≥ 0 | Estimated turtle length (cm) |
| turtle_behaviour_id | varchar | 8 | No | BHV01 | Alphanumeric (FK) | Reference to behaviour (lookup table)|
| image_right | varchar | 100 | No | right_001.jpg | File path / URL | Right-side image |
| image_left | varchar | 100 | No | left_001.jpg | File path / URL | Left-side image |
| image_top | varchar | 100 | No | top_001.jpg | File path / URL | Top-view image |
| is_fibro | bit | — | Yes | 1 | 0 = No, 1 = Yes | Fibropapillomatosis indicator |
| comment | varchar | 250 | Yes | Healthy individual | Free text | Additional notes |

---

#### individual
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| individual_id | varchar | 8 | No | IND0001 | Alphanumeric, unique | Unique identifier for each turtle individual |
| name | varchar | 20 | Yes | Amina | Free text | Name or label assigned to the turtle |
| sex | varchar | 8 | Yes | Female | Male, Female, Unknown | Reference to sex (lookup table) |
| iot_id | varchar | 20 | Yes | iot4325 | Alphanumeric(FK) | internet of turtles issued number. Reference to iot_number (lookup table) |
| bh_id | varchar | 20 | No | BH001 | Alphanumeric | bahari hai issued turtle identifier |
| turtle_id | varchar | 8 | Yes | 001 | Alphanumeric(FK) | Reference to turtle (lookup table) |

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
| name | varchar | 20 | No | High | High, Low | Tide level |

---

####  behaviour
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| behaviour_id | varchar | 8 | No | 01 | Alphanumeric | Unique behaviour ID |
| name | varchar | 20 | No | Feeding | Feeding, Resting, Swimming | Turtle behaviour |

---

####  foraging_ground
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| foraging_ground_id | int | — | No | 1 | Integer | Unique foraging ground ID |
| foraging_ground_name | varchar | 10 | No | Reef | Predefined names | Name of foraging ground |

---

####  iot_number
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| iot_number_id | varchar | 8 | No | IOT001 | Alphanumeric | Unique iot record ID |
| iot_id | varchar | 20 | No | IOT123456 | Alphanumeric | internet of turtles issued identifier |

---

####  tag_status
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| tag_status_id | int | — | No | 1 | Integer, unique | Unique tag status ID |
| tag_status_name | varchar | 20 | No | Active | Active, Lost | Status of tag |

---
#### site

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| site_id | varchar | 8 | No | S001 | Alphanumeric | Unique ID for the site |
| site_name | varchar | 50 | No | Diani Beach | Text | Name of the site |
| area_id | int | 10 | No | 1 | Integer (FK) | Reference to area (lookup table) |
| foraging_ground_id | int | 10 | Yes | 5 | Integer (FK) | Reference to foraging_ground (lookup table)|
| is_capture_site | bit | 1 | Yes | 1 | 0 / 1 | Flag if site is used for turtle capture |
| is_landing_site | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is used for turtle/fish landing |
| is_nesting_site | bit | 1 | Yes | 1 | 0 / 1 | Flag if site is used for turtle nesting |
| is_release_site | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is used for turtle release |
| is_plot | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is a beach plot |
| is_hotel | bit | 1 | Yes | 1 | 0 / 1 | Flag if site is part of a hotel property |
| is_private | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is privately owned |

---
#### area

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| area_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for each area/region |
| area_name | varchar | 20 | No | Lamu County | Text | Name of the area |
| admin_2 | varchar | 20 | Yes | Malindi | Text | Lower administrative unit (sub-county) |
| admin_1 | varchar | 20 | Yes | Kilifi | Text | Mid-level administrative unit (county) |
| admin_0 | varchar | 20 | Yes | Kenya | Text | top-level administrative unit (Country)|

---
#### sex

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| sex_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for sex |
| sex_name | varchar | 20 | No | Male | Text | Name of sex in English |
| sex_name_swahili | varchar | 100 | Yes | Mwanaume | Text | Name of sex in Swahili (optional) |

---
#### species

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| species_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for each turtle species |
| species_name | varchar | 20 | No | Green Turtle | Text | Name of the turtle species |

---
#### turtle

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| turtle_id | int | 10 | No | 101 | Integer (Primary Key) | Unique identifier for each turtle |
| turtle_name | varchar | 50 | Yes | Kanga | Text | Name of the turtle (optional) |
| species_id | int | 10 | No | 1 | Integer (FK) | Reference to species (`species_id`) |
| current_tag_1 | varchar | 20 | No | KBL001 | Text | Primary tag on turtle |
| current_tag_2 | varchar | 20 | No | KBL002 | Text | Secondary tag (if applicable) |
| turtle_sex | int | 10 | No | 1 | Integer (FK) | Reference to sex table |
| turtle_notes | varchar | 200 | Yes | Female observed nesting in June | Free text (≤200 chars) | Additional observations about the turtle |

---
#### party

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_id | varchar | 8 | No | RPT001 | Alphanumeric | Unique ID for each party (person,group or organization) |
| party_type_id | int | 10 | No | 1 | Integer (FK) | Reference to party_type (lookup table) |
| party_name | varchar | 200 | No | Kalume Karisa | Text | Full name of party, group or organization |
| party_telephone_1 | varchar | 20 | Yes | +254701234567 | Text / Numeric | Primary contact number |
| party_telephone_2 | varchar | 20 | Yes | +254712345678 | Text / Numeric | Secondary contact number |
| party_email | varchar | 50 | Yes | karisa@baharihai.org | Email format | Email address |
| site_id | varchar | 8 | No | S001 | Alphanumeric (FK) | Reference to site |
| sex_id | varchar | 8 | Yes | Male | Alphanumeric (FK) | Reference to sex (`sex_id`) |
| organization_id | varchar | 8 | Yes | baharihai | Alphanumeric (FK)| Reference to party (`party_id`) |

---
#### party_type

| Field Name          | SQL Type | Length / Precision | Nullable | Example Value        | Allowed Values / Format | Description                                      |
|---------------------|----------|-------------------|----------|---------------------|------------------------|--------------------------------------------------|
| party_type_id       | int      | 10                | No       | 4                   | Integer (0-10)         | Unique identifier for the party type.            |
| party_type_name     | varchar  | 20                | Yes      | Organization          | String (max 20 chars)  | Name of the party type in English.                |
| party_type_swahili  | varchar  | 100               | Yes      | Shirika  | String (max 100 chars) | Name of the party type in Swahili.                |

---

#### v_all_photo_id_fields
## 13. turtle_sightings_view (denormalized / reporting view)

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| turtle_sighting_id | varchar | 8 | No | TS00001 | Alphanumeric, unique | Unique sighting identifier |
| survey_datetime | datetime | — | No | 2025-06-01 10:30:00 | YYYY-MM-DD HH:MM:SS | Date and time of observation |
| observer | varchar | 200 | Yes | Kalume Kenga| Free text | Name of observer |
| individual's name | varchar | 20 | Yes | Salimu | Free text | Name/label of turtle |
| bh_id | varchar | 20 | Yes | BH001 | Alphanumeric | bahari hai issued turtle identifier  |
| species_name | varchar | 20 | Yes | Green Turtle | Predefined species | Turtle species |
| sex_name | varchar | 20 | Yes | Female | Male, Female, Unknown | Sex of turtle |
| age | varchar | 20 | No | Adult | Juvenile, Subadult, Adult | Age class |
| estimated_ccl | int | — | No | 75 | Integer ≥ 0 | Estimated curved carapace length (cm) |
| turtle_behaviour | varchar | 20 | Yes | Feeding | Predefined behaviours | Observed behaviour |
| site_name | varchar | 50 | Yes | Watamu Reef | Free text | Site name |
| tide_name | varchar | 20 | Yes | High | High, Low, Mid | Tide level |
| name | varchar | 20 | Yes | Spring | Spring, Neap | Tide cycle |
| visibility_name | varchar | 20 | Yes | Clear | Poor, Moderate, Clear | Visibility condition |
| sighting depth(m) | int | — | Yes | 5 | Integer ≥ 0 | Depth in meters |
| lat_long | nvarchar | 100 | Yes | -3.123,40.123 | "lat,lon" decimal format | Geographic coordinates |

---


