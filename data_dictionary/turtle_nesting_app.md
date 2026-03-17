### Sea Turtle Nest Monitoring Data Dictionary
This catalog describes the structure, meaning, and rules of data in a the BH turtle database. It's relevance is in ensuring that data is comprehended, managed, and used consistently across the organization. It improves data clarity, quality, consistency, collaboration, and analysis, thus remaining essential for managing datasets and information systems within Bahari Hai.


#### turtle_nest

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|-------------------------|-------------|
| nest_id | varchar | 20 | No | NEST_2026_001 | Unique string ID | Unique identifier for the turtle nest nest (nest-laid year-nest sequence/number)|
| turtle_id | int | 10 | No | 1452 | Integer (FK) | Reference to turtle (lookup table) |
| laid_date_time | datetime | — | No | 2026-03-15 02:30:00 | YYYY-MM-DD HH:MM:SS | Date and time when the nest was laid |
| reporter_party_id | varchar | 8 | No | rpt001 | Alphanumeric code (FK) | ID of the person or organization reporting the nest (references party table) |
| temperature_logger_id_1 | int | 10 | Yes | 122434 | Integer (FK) | ID of the first temperature logger placed inside the nest. Reference to temp_logger (lookup table) |
| temperature_logger_id_2 | int | 10 | Yes | 122435 | Integer (FK) | ID of the second temperature logger placed in control site outside the nest. Reference to temp_logger (lookup table)|
| nest_location_original_id | int | 10 | No | 87 | Integer (Location reference ID) (FK) | Original nest location reference |
| distance_from_hwm_m | numeric | 8,2 | Yes | 12.50 | Decimal (meters) | Distance from High Water Mark |
| turtle_track_width_cm | numeric | 8,2 | Yes | 95.30 | Decimal (centimeters) | Width of turtle track measured |
| reason_for_no_track_width | int | 10 | Yes | 2 | Reference code (lookup table) | Reason track width was not recorded |
| is_relocated | bit | 1 | Yes | 1 | 0 = No, 1 = Yes | Indicates if the nest was relocated |
| expected_hatch_datetime | smalldatetime | — | Yes | 2026-05-12 18:00 | YYYY-MM-DD HH:MM | Estimated hatching date and time |
| nest_notes | varchar | 300 | Yes | Nest near beach access road | Free text (max 300 chars) | Additional notes about the nest |

#### nest_excavation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|-------------------------|-------------|
| nest_excavation_id | int | 10 | No | 4501 | Integer (Primary Key) | Unique excavation record identifier |
| nest_id | varchar | 20 | No | NEST-2026-015 | Existing nest ID | Reference to nest record |
| excavation_datetime | datetime | — | No | 2026-05-18 09:30:00 | YYYY-MM-DD HH:MM:SS | Date and time when nest was excavated |
| sun_exposure_type_id | int | 10 | No | 2 | Integer (FK) | reference to sun_exposure_type |
| top_shell_depth_cm | float | — | No | 35.5 | Decimal (cm) | Depth of top eggshell layer in the nest |
| bottom_shell_depth_cm | float | — | No | 62.3 | Decimal (cm) | Depth of bottom eggshell layer in the nest |
| num_eggs_empty | smallint | — | No | 10 | Integer ≥ 0 | Number of empty eggshells |
| num_eggs_early_dev | smallint | — | No | 4 | Integer ≥ 0 | Eggs with early embryo development |
| num_eggs_under_dev | smallint | — | No | 2 | Integer ≥ 0 | Eggs with underdeveloped embryos |
| num_eggs_mid_dev | smallint | — | No | 3 | Integer ≥ 0 | Eggs with mid-stage development |
| num_eggs_late_dev | smallint | — | No | 1 | Integer ≥ 0 | Eggs with late-stage development |
| num_eggs_micro | smallint | — | No | 0 | Integer ≥ 0 | small than normal size eggs |
| num_eggs_unknown | smallint | — | No | 2 | Integer ≥ 0 | Eggs with unknown status |
| num_eggs_depredated | smallint | — | No | 5 | Integer ≥ 0 | Eggs predated by animals |
| num_eggs_yolkless | smallint | — | No | 1 | Integer ≥ 0 | Yolkless eggs |
| num_hatchlings_pipped_dead | smallint | — | No | 2 | Integer ≥ 0 | Hatchlings that pipped but died |
| num_hatchlings_pipped_live | smallint | — | No | 3 | Integer ≥ 0 | Hatchlings pipped and alive |
| num_hatchlings_dead | smallint | — | No | 4 | Integer ≥ 0 | Dead hatchlings found |
| num_hatchlings_live | smallint | — | No | 90 | Integer ≥ 0 | Live hatchlings found |
| num_total_eggs_excavated | smallint | — | No | 110 | Integer ≥ 0 | Total eggs excavated |
| num_total_eggs_successful | smallint | — | No | 95 | Integer ≥ 0 | Total successful hatchlings |
| num_relocated_eggs_missing | smallint | — | No | 2 | Integer ≥ 0 | Relocated eggs missing |
| num_relocated_eggs_extra | smallint | — | No | 1 | Integer ≥ 0 | Extra eggs found in relocated nest |
| num_total_eggs | smallint | — | No | 112 | Integer ≥ 0 | Total eggs found in the nest |
| nest_success_rate | float | — | No | 84.8 | Percentage (0–100) | Overall nest success rate |
| rate_eggs_empty | float | — | No | 9.1 | Percentage (0–100) | Rate of empty eggs |
| rate_eggs_early_dev | float | — | No | 3.6 | Percentage (0–100) | Rate of early embryo development eggs |
| rate_eggs_under_dev | float | — | No | 1.8 | Percentage (0–100) | Rate of underdeveloped eggs |
| rate_eggs_mid_dev | float | — | No | 2.7 | Percentage (0–100) | Rate of mid-stage embryo development |
| rate_eggs_late_dev | float | — | No | 0.9 | Percentage (0–100) | Rate of late-stage embryo development |
| rate_eggs_micro | float | — | No | 0.0 | Percentage (0–100) | Rate of small than normal size eggs |
| rate_eggs_unknown | float | — | No | 1.8 | Percentage (0–100) | Rate of unknown egg condition |
| rate_eggs_depredated | float | — | No | 4.5 | Percentage (0–100) | Rate of egg predation |
| rate_eggs_yolkless | float | — | No | 0.9 | Percentage (0–100) | Rate of yolkless eggs |
| rate_hatchlings_pipped_dead | float | — | No | 1.8 | Percentage (0–100) | Rate of dead pipped hatchlings |
| rate_hatchlings_pipped_live | float | — | No | 2.7 | Percentage (0–100) | Rate of live pipped hatchlings |
| rate_hatchlings_dead | float | — | No | 3.6 | Percentage (0–100) | Rate of dead hatchlings |
| rate_hatchlings_live | float | — | No | 80.4 | Percentage (0–100) | Rate of live hatchlings |
| nest_failure_cause | int | 10 | No | 3 | Lookup ID (FK) | Reference to nest_failure_cause (lookup table) |
| excavation_notes | varchar | 300 | Yes | Predation signs by monitor lizard | Free text (≤300 characters) | Additional excavation observations |

#### nest_relocation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| nest_relocation_id | int | 10 | No | 501 | Integer (Primary Key) | Unique ID for each nest relocation |
| nest_id | varchar | 20 | No | NEST-2026-015 | Alphanumeric | Reference to the original nest (`nest_id`) |
| reason_for_relocation | int | 10 | Yes | 1 | Integer (FK) | Reference to reason for relocation (lookup table) |
| relocation_datetime | datetime | — | Yes | 2026-06-20 07:30:00 | YYYY-MM-DD HH:MM:SS | Date and time of relocation |
| temp_logger_id_1 | int | 10 | Yes | 107751 | Integer (FK) | Reference to first temperature logger used.Reference to temp_logger (lookup table) |
| temp_logger_id_2 | int | 10 | Yes | 107752 | Integer (FK) | Reference to second temperature logger used. Reference to temp_logger (lookup table) |
| original_top_egg_depth_cm | numeric | 8,2 | Yes | 20.5 | Decimal (cm) | Depth of top egg before relocation |
| num_eggs_relocated | int | 10 | Yes | 100 | Integer | Total eggs relocated |
| num_micro_eggs_relocated | int | 10 | Yes | 3 | Integer | Number of micro (undeveloped) eggs relocated |
| original_bottom_egg_depth_cm | numeric | 8,2 | Yes | 35.0 | Decimal (cm) | Depth of bottom egg before relocation |
| original_chamber_width_cm | varchar | 20 | Yes | 25 | Text / Numeric | Width of original egg chamber |
| new_bottom_egg_depth_cm | numeric | 8,2 | Yes | 36.0 | Decimal (cm) | Depth of bottom egg in new location |
| new_chamber_width_cm | varchar | 20 | Yes | 27 | Text / Numeric | Width of new egg chamber |
| new_top_egg_depth_cm | numeric | 8,2 | Yes | 11.0 | Decimal (cm) | Depth of top egg in new location |
| new_location_id | int | 10 | Yes | 102 | Integer (FK) | Reference to location (`location_id`) |
| relocation_notes | varchar | 200 | Yes | Relocated due to being below high water mark| Free text | Notes about the relocation process |
| time_taken_to_relocate | numeric | 4,2 | Yes | 2.5 | Decimal (hours) | Time taken to complete relocation |

#### party

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_id | varchar | 8 | No | RPT001 | Alphanumeric | Unique ID for each party (person or organization) |
| party_type_id | int | 10 | No | 1 | Integer (FK) | Reference to party_type (lookup table) |
| party_name | varchar | 200 | No | Kalume Karisa | Text | Full name of party or organization |
| party_telephone_1 | varchar | 20 | Yes | +254701234567 | Text / Numeric | Primary contact number |
| party_telephone_2 | varchar | 20 | Yes | +254712345678 | Text / Numeric | Secondary contact number |
| party_email | varchar | 50 | Yes | karisa@baharihai.org | Email format | Email address |
| site_id | varchar | 8 | No | S001 | Alphanumeric (FK) | Reference to site |
| sex_id | varchar | 8 | Yes | M | Alphanumeric (FK) | Reference to sex (`sex_id`) |
| organization_id | varchar | 8 | Yes | baharihai | Alphanumeric | Reference to associated organization in party (`party_id`) |

#### party_type

| Field Name          | SQL Type | Length / Precision | Nullable | Example Value        | Allowed Values / Format | Description                                      |
|---------------------|----------|-------------------|----------|---------------------|------------------------|--------------------------------------------------|
| party_type_id       | int      | 10                | No       | 4                   | Integer (0-10)         | Unique identifier for the party type.            |
| party_type_name     | varchar  | 20                | Yes      | "Organization"          | String (max 20 chars)  | Name of the party type in English.                |
| party_type_swahili  | varchar  | 100               | Yes      | "Shirika"  | String (max 100 chars) | Name of the party type in Swahili.                |


#### hatching

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| hatching_id | int | 10 | No | 501 | Integer (Primary Key) | Unique ID for each hatching record |
| nest_id | varchar | 20 | No | NEST-2026-015 | Existing nest ID | Reference to the associated nest |
| actual_hatch_datetime | datetime | — | Yes | 2026-05-12 18:15:00 | YYYY-MM-DD HH:MM:SS | Date and time the nest actually hatched |
| num_actual_incubation_days | float | — | Yes | 57.5 | Decimal (days) | Total incubation period in days |
| hatching_outcome_id | int | 10 | No | 1 | integer (FK) | Reference to hatching_outcome (lookup table) |
| hatching_notes | varchar | 50 | Yes | All hatchlings emerged successfully | Free text (≤50 chars) | Additional observations about hatching |

#### sex

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| sex_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for sex/gender category |
| sex_name | varchar | 20 | No | Male | Text | Name of sex/gender in English |
| sex_name_swahili | varchar | 100 | Yes | Mwanaume | Text | Name of sex/gender in Swahili (optional) |

#### species

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| species_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for each turtle species |
| species_name | varchar | 20 | No | Green Turtle | Text | Name of the turtle species |

#### turtle

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| turtle_id | int | 10 | No | 101 | Integer (Primary Key) | Unique identifier for each turtle |
| turtle_name | varchar | 50 | Yes | Kima | Text | Name of the turtle (optional, if tagged individually) |
| species_id | int | 10 | No | 1 | Integer (FK) | Reference to turtle species (`species_id`) |
| current_tag_1 | varchar | 20 | No | T001 | Text | Primary identification tag on turtle |
| current_tag_2 | varchar | 20 | No | T002 | Text | Secondary tag (if applicable) |
| turtle_sex | int | 10 | No | 1 | Integer (FK) | Reference to `sex_id` table |
| turtle_notes | varchar | 200 | Yes | Female observed nesting in June | Free text (≤200 chars) | Additional observations about the turtle |

#### hatching_outcome

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| hatching_outcome_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for hatching outcome |
| hatching_outcome_name | varchar | 30 | No | Successful | Text | Name/description of hatching outcome |

#### party_at_hatching

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_hatching_id | int | 10 | No | 1001 | Integer (Primary Key) | Unique identifier for the party-hatching relationship |
| hatching_id | int | 10 | No | 501 | Integer (FK) | Reference to the hatching record (`hatching_id`) |
| party_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Reference to the reporting party (`party_id`) |

#### party_at_nesting

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_nesting_id | int | 10 | No | 2001 | Integer (Primary Key) | Unique identifier for the party-nesting relationship |
| nest_id | varchar | 20 | No | NEST-2026-015 | Alphanumeric ID | Reference to the nest record (`nest_id`) |
| party_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Reference to the reporting party (`party_id`) |

#### party_at_relocation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_relocation_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Unique identifier for the party involved in a relocation event |
| relocation_id | int | 10 | No | 301 | Integer (FK) | Reference to the relocation record (`relocation_id`) |
| party_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Reference to the reporting party (`party_id`) |

#### turtle_interaction

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| interaction_id | varchar | 8 | No | INT001 | Alphanumeric ID | Unique identifier for each turtle interaction |
| old_rescue_id | varchar | 14 | Yes | RESC-2023-001 | Alphanumeric ID | Legacy rescue ID if applicable |
| turtle_id | int | 10 | No | 101 | Integer (FK) | Reference to turtle record (`turtle_id`) |
| interaction_type_id | int | 10 | No | 2 | Integer (FK) | Reference to type of interaction (e.g., capture, tagging, release) |
| interaction_date_time | datetime | — | Yes | 2026-06-15 09:45:00 | YYYY-MM-DD HH:MM:SS | Date and time of the interaction |
| caught_date_time | datetime | — | Yes | 2026-06-15 08:30:00 | YYYY-MM-DD HH:MM:SS | Date and time turtle was caught (if applicable) |
| capture_method | int | 10 | Yes | 1 | Lookup ID | Method used to capture the turtle |
| fisher | varchar | 8 | Yes | FISH001 | Alphanumeric ID | Fisher involved in interaction |
| collected_from | varchar | 8 | Yes | SITE001 | Alphanumeric ID | Source site of turtle |
| site_caught | varchar | 8 | Yes | SITE002 | Alphanumeric ID | Site where turtle was caught |
| landing_site | varchar | 8 | Yes | LAND001 | Alphanumeric ID | Landing site for turtle release or record |
| turtle_ccl_cm | numeric | 8,2 | No | 112.5 | Decimal (cm) | Curved Carapace Length |
| turtle_ccw_cm | numeric | 8,2 | No | 87.3 | Decimal (cm) | Curved Carapace Width |
| turtle_weight_kg | numeric | 8,3 | Yes | 95.250 | Decimal (kg) | Turtle weight |
| turtle_characteristics | varchar | 500 | Yes | Small scar on left flipper | Free text | Additional turtle observations |
| interaction_outcome | int | 10 | No | 1 | Lookup ID | Outcome of interaction (e.g., released, rescued, dead) |
| interaction_notes | varchar | 300 | Yes | Released after tagging | Free text | Notes about interaction |
| nest_id | varchar | 20 | Yes | NEST-2026-015 | Alphanumeric ID | Reference to associated nest (if applicable) |
| interaction_gps | varchar | 50 | Yes | -3.25012, 40.89022 | Latitude, Longitude | GPS coordinates of interaction |

#### party_at_excavation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_excavation_id | int | 10 | No | 3001 | Integer (Primary Key) | Unique identifier for the party-excavation relationship |
| nest_excavation_id | int | 10 | No | 4501 | Integer (FK) | Reference to the nest excavation record (`nest_excavation_id`) |
| party_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Reference to the reporting party (`party_id`) |

#### temp_logger

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| temp_logger_id | int | 10 | No | 101 | Integer (Primary Key) | Unique identifier for each temperature logger |
| serial_no | varchar | 30 | Yes | TL-2026-001 | Alphanumeric | Serial number of the logger device |

#### nest_failure_cause

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| nest_failure_cause_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for each nest failure cause |
| nest_failure_cause_name | varchar | 50 | Yes | Predation | Text | Description of why the nest failed |

#### sun_exposure_type

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| sun_exposure_type_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for sun exposure category |
| sun_exposure_type_name | varchar | 50 | No | Full Sun | Text | Name of sun exposure type (e.g., Full Sun, Partial Shade, Shade) |

#### location

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| location_id | int | 10 | No | 101 | Integer (Primary Key) | Unique ID for each location |
| site_id | varchar | 8 | No | S001 | Alphanumeric ID | Reference to the monitoring site |
| lat_long | nvarchar | 50 | Yes | -3.25678, 40.89123 | Latitude, Longitude | GPS coordinates as text |
| y_coordinate | decimal | 10,4 | Yes | -3.2567 | Decimal | Latitude (or projected Y coordinate) |
| x_coordinate | decimal | 11,4 | Yes | 40.8912 | Decimal | Longitude (or projected X coordinate) |
| location_name | nvarchar | 50 | Yes | Turtle Nesting Beach A | Text | Descriptive name of the location |
| nearest_landmark | nvarchar | 50 | Yes | Lighthouse | Text | Nearest landmark for reference |
| location_type_id | int | 10 | No | 1 | Integer (FK) | Type of location (e.g., nesting site, hatchery, patrol site) |

#### site

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| site_id | varchar | 8 | No | S001 | Alphanumeric | Unique ID for the site |
| site_name | varchar | 50 | No | Diani Beach | Text | Name of the site |
| area_id | int | 10 | No | 1 | Integer (FK) | Reference to administrative area / region |
| foraging_ground_id | int | 10 | Yes | 5 | Integer (FK) | Reference to associated foraging ground (if applicable) |
| is_capture_site | bit | 1 | Yes | 1 | 0 / 1 | Flag if site is used for turtle capture |
| is_landing_site | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is used for turtle landing |
| is_nesting_site | bit | 1 | Yes | 1 | 0 / 1 | Flag if site is used for turtle nesting |
| is_release_site | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is used for turtle release |
| is_plot | bit | 1 | Yes | 0 | 0 / 1 | Flag if site contains a monitored plot |
| is_hotel | bit | 1 | Yes | 1 | 0 / 1 | Flag if site is part of a hotel property |
| is_private | bit | 1 | Yes | 0 | 0 / 1 | Flag if site is privately owned |

#### area

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| area_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for each area/region |
| area_name | varchar | 20 | No | Lamu County | Text | Name of the area |
| admin_2 | varchar | 20 | Yes | Lamu East | Text | Lower administrative unit (e.g., sub-county, district) |
| admin_1 | varchar | 20 | Yes | Lamu County | Text | Mid-level administrative unit (e.g., county) |
| admin_0 | varchar | 20 | Yes | Kenya | Text | Country / top-level administrative unit |

