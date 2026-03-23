### Sea Turtle Nest Monitoring Data Dictionary
This catalog describes the structure, meaning, and rules of data in a the BH turtle database. It's relevance is in ensuring that data is comprehended, managed, and used consistently across the organization. It improves data clarity, quality, consistency, collaboration, and analysis, thus remaining essential for managing datasets and information systems within Bahari Hai.


#### turtle_nest

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|-------------------------|-------------|
| nest_id | varchar | 20 | No | NEST_2026_001 | Unique string ID | Unique identifier for the turtle nest nest (nest-laid year-nest sequence/number)|
| turtle_id | int | 10 | No | 1452 | Integer (FK) | Reference to turtle (lookup table) |
| laid_date_time | datetime | — | No | 2026-03-15 02:30:00 | YYYY-MM-DD HH:MM:SS | Date and time when the nest was laid |
| reporter_party_id | varchar | 8 | No | rpt001 | Alphanumeric code (FK) | ID of the person or organization reporting the nest. Reference to party (lookup table) |
| temperature_logger_id_1 | int | 10 | Yes | 122434 | Integer (FK) | ID of the first temperature logger placed inside the nest. Reference to temp_logger (lookup table) |
| temperature_logger_id_2 | int | 10 | Yes | 122435 | Integer (FK) | ID of the second temperature logger placed in control site outside the nest. Reference to temp_logger (lookup table)|
| nest_location_original_id | int | 10 | No | 87 | Integer (Location reference ID) (FK) | Original nest location reference |
| distance_from_hwm_m | numeric | 8,2 | Yes | 12.50 | Decimal (meters) | Distance from High Water Mark |
| turtle_track_width_cm | numeric | 8,2 | Yes | 95.30 | Decimal (centimeters) | Width of turtle track measured |
| reason_for_no_track_width | int | 10 | Yes | 2 | Reference code (lookup table) | Reason track width was not recorded |
| is_relocated | bit | 1 | Yes | 1 | 0 = No, 1 = Yes | Indicates if the nest was relocated |
| expected_hatch_datetime | datetime | — | Yes | 2026-05-12 18:00:00 | YYYY-MM-DD HH:MM:SS | Estimated hatching date and time |
| nest_notes | varchar | 300 | Yes | Nest near beach access road | Free text (max 300 chars) | Additional notes about the nest |

---

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

---
#### nest_relocation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| nest_relocation_id | int | 10 | No | 501 | Integer (Primary Key) | Unique ID for each nest relocation |
| nest_id | varchar | 20 | No | NEST-2026-015 | Alphanumeric | Reference to the original nest (`nest_id`) |
| reason_for_relocation | int | 10 | Yes | 1 | Integer (FK) | Reference to reason_for_relocation (lookup table) |
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
#### interaction_type

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| interaction_type_id | int | — | No | 1 | Integer, unique | Unique identifier for interaction type |
| interaction_type_name | varchar | 30 | No | nesting | Predefined categories (e.g., nesting,bycatch) | Type of interaction with the turtle |

---
#### capture_method

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| capture_method_id | int | — | No | 1 | Integer, unique | Unique identifier for capture method |
| capture_method_name | varchar | 30 | No | Net| Predefined categories (e.g., Net, line, collected floater) | Method used to capture the turtle |
| capture_method_explanation | varchar | 200 | Yes | Captured as bycatch | Free text | Additional explanation or details about the capture method |

---
#### interaction_outcome

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| outcome_id | int | — | No | 1 | Integer, unique | Unique identifier for outcome |
| outcome_name | varchar | 30 | No | admitted | Predefined categories (e.g., Released, admitted in rehabilitation center) | Outcome of the interaction|
| outcome_explanation | varchar | 500 | Yes | Turtle was treated and safely released back into the ocean | Free text | Additional details describing the outcome |

---
#### hatching

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| hatching_id | int | 10 | No | 501 | Integer (Primary Key) | Unique ID for each hatching record |
| nest_id | varchar | 20 | No | NEST-2026-015 | Existing nest ID | Reference to the associated nest |
| actual_hatch_datetime | datetime | — | Yes | 2026-05-12 18:15:00 | YYYY-MM-DD HH:MM:SS | Date and time the nest actually hatched |
| num_actual_incubation_days | float | — | Yes | 57.5 | Decimal (days) | Total incubation period in days |
| hatching_outcome_id | int | 10 | No | 1 | integer (FK) | Reference to hatching_outcome (lookup table) |
| hatching_notes | varchar | 50 | Yes | All hatchlings emerged successfully | Text (≤50 chars) | Additional observations about hatching |

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
#### hatching_outcome

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| hatching_outcome_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for hatching outcome |
| hatching_outcome_name | varchar | 30 | No | Successful | Text | Name/description of hatching outcome |

---
####  foraging_ground
| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| foraging_ground_id | int | — | No | 1 | Integer | Unique foraging ground ID |
| foraging_ground_name | varchar | 10 | No | Reef | Predefined names | Name of foraging ground |

---
#### party_at_hatching

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_hatching_id | int | 10 | No | 1001 | Integer (Primary Key) | Unique identifier for the party-hatching relationship |
| hatching_id | int | 10 | No | 501 | Integer (FK) | Reference to the hatching record (`hatching_id`) |
| party_id | varchar | 8 | No | pth001 | Alphanumeric ID (FK) | Reference to party (`party_id`) |

---
#### party_at_nesting

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_nesting_id | int | 10 | No | 2001 | Integer (Primary Key) | Unique identifier for the party-nesting relationship |
| nest_id | varchar | 20 | No | NEST-2026-015 | Alphanumeric ID (FK) | Reference to turtle_nest  (`nest_id`) |
| party_id | varchar | 8 | No | ptn001 | Alphanumeric ID (FK) | Reference to party (`party_id`) |

---
#### party_at_relocation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_relocation_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Unique identifier for the party involved in a relocation event |
| relocation_id | int | 10 | No | 301 | Integer (FK) | Reference to the nest_relocation (`relocation_id`) |
| party_id | varchar | 8 | No | ptr001 | Alphanumeric ID (FK) | Reference to party (`party_id`) |

---
#### turtle_interaction

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| interaction_id | varchar | 8 | No | INT001 | Alphanumeric ID | Unique identifier for each turtle interaction |
| old_rescue_id | varchar | 14 | Yes | rsc-2023-001 | Alphanumeric ID | Legacy rescue ID if applicable |
| turtle_id | int | 10 | No | 101 | Integer (FK) | Reference to turtle (`turtle_id`) |
| interaction_type_id | int | 10 | No | 2 | Integer (FK) | Reference to interaction_type (e.g., nesting,bycatch) |
| interaction_date_time | datetime | — | Yes | 2026-06-15 09:45:00 | YYYY-MM-DD HH:MM:SS | Date and time of the interaction |
| caught_date_time | datetime | — | Yes | 2026-06-15 08:30:00 | YYYY-MM-DD HH:MM:SS | Date and time turtle was caught (if applicable) |
| capture_method | int | 10 | Yes | 1 | Integer (FK) | Method used to capture the turtle. Reference to capture_method (lookup table) |
| fisher | varchar | 8 | Yes | FISH001 | Alphanumeric ID (FK) | Fisher involved in interaction. Reference to party (lookup table) |
| collected_from | varchar | 8 | Yes | SITE001 | Alphanumeric ID (FK) | Source party of turtle. Reference to party (lookup table) |
| site_caught | varchar | 8 | Yes | SITE002 | Alphanumeric ID (FK)| Site where turtle was caught. Reference to site (lookup table)|
| landing_site | varchar | 8 | Yes | LAND001 | Alphanumeric ID (FK)| Landing site for turtle. Reference to site (lookup table) |
| turtle_ccl_cm | numeric | 8,2 | No | 112.5 | Decimal (cm) | Curved Carapace Length |
| turtle_ccw_cm | numeric | 8,2 | No | 87.3 | Decimal (cm) | Curved Carapace Width |
| turtle_weight_kg | numeric | 8,3 | Yes | 95.2 | Decimal (kg) | Turtle weight |
| turtle_characteristics | varchar | 500 | Yes | Small scar on left flipper | Free text | Additional turtle observations |
| interaction_outcome | int | 10 | No | 1 | Integer (FK) | Outcome of interaction (e.g., released, admitted)Reference to interaction_outcome (lookup table) |
| interaction_notes | varchar | 300 | Yes | Released after tagging | Free text | Notes about interaction |
| nest_id | varchar | 20 | Yes | NEST-2026-015 | Alphanumeric ID (FK) | Reference to turtle_nest |
| interaction_gps | varchar | 50 | Yes | -3.25012, 40.89022 | Latitude, Longitude | GPS coordinates of interaction in decimal degree |

---
#### party_at_excavation

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| party_at_excavation_id | int | 10 | No | 3001 | Integer (Primary Key) | Unique identifier for the party-excavation relationship |
| nest_excavation_id | int | 10 | No | 4501 | Integer (FK) | Reference to the nest excavation record (`nest_excavation_id`) |
| party_id | varchar | 8 | No | RPT001 | Alphanumeric ID | Reference to party (`party_id`) |

---
#### temp_logger

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| temp_logger_id | int | 10 | No | 101 | Integer (Primary Key) | Unique identifier for each temperature logger |
| serial_no | varchar | 30 | Yes | TL-2026-001 | Alphanumeric | Serial number of the logger device |

---
#### nest_failure_cause

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| nest_failure_cause_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for each nest failure cause |
| nest_failure_cause_name | varchar | 50 | Yes | Predation | Text | Description of why the nest failed |

---
#### sun_exposure_type

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| sun_exposure_type_id | int | 10 | No | 1 | Integer (Primary Key) | Unique ID for sun exposure category |
| sun_exposure_type_name | varchar | 50 | No | Full Sun | Text | Name of sun exposure type (e.g.Partial Shade, Shade) |

---
#### location

| Field Name | SQL Type | Length / Precision | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|-------------------|----------|---------------|------------------------|-------------|
| location_id | int | 10 | No | 101 | Integer (Primary Key) | Unique ID for each location |
| site_id | varchar | 8 | No | S001 | Alphanumeric ID | Reference to the monitoring site |
| lat_long | nvarchar | 50 | Yes | -3.25678, 40.89123 | Latitude, Longitude | GPS coordinates as text |
| y_coordinate | decimal | 10,4 | Yes | -3.2567 | Decimal | Latitude (or projected Y coordinate) |
| x_coordinate | decimal | 11,4 | Yes | 40.8912 | Decimal | Longitude (or projected X coordinate) |
| location_name | nvarchar | 50 | Yes | Turtle Nesting Beach A | Text | Descriptive name of the location |
| nearest_landmark | nvarchar | 50 | Yes | Beach access road | Text | Nearest landmark for reference |
| location_type_id | int | 10 | No | 1 | Integer (FK) | Type of location (e.g., nesting site, landing site, hotel). Reference to location_type (lookup table) |

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
#### v_all_nest_fields

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|--------------------------|-------------|
| nest_id | varchar | 20 | No | NEST-2026-015 | Alphanumeric, unique | Unique nest identifier |
| laid_date_time | datetime | — | No | 2025-02-10 22:15:00.000 | YYYY-MM-DD HH:MM:SS | Date and time eggs were laid |
| expected_hatch_datetime | datetime | — | Yes | 2022-06-29 06:09:00.000 | YYYY-MM-DD HH:MM:SS | Estimated hatching datetime |
| reporter_name | varchar | 50 | No | Karisa Kenga | Free text | Person reporting the nest |
| turtle_track_width_cm | numeric | — | Yes | 85.50 | Decimal ≥ 0 | Width of turtle track (cm) |
| species_name | varchar | 20 | No | Green Turtle | Predefined species names | Turtle species |
| original_site_id | varchar | 8 | No | 107 | FK reference | Original nesting site id |
| original_site_name | varchar | 50 | No | Watamu Beach | Free text | Original nesting site name |
| original_location_id | int | — | No | 1445 | Integer | Location reference |
| original_x_coord | decimal | — | Yes | 40.1234 | Decimal (lon) | Original longitude |
| original_y_coord | decimal | — | Yes | -3.1234 | Decimal (lat) | Original latitude |
| original_area | varchar | 20 | Yes | Watamu | Free text | Original nesting area name |
| distance_from_hwm_m | numeric | — | Yes | 2.50 | Decimal ≥ 0 | Distance from high water mark (m) |
| is_relocated | varchar | 3 | No | Yes | Yes/No | Indicates if nest was relocated |
| relocated_site_id | varchar | 8 | Yes | 765 | FK reference | New site ID |
| relocated_site_name | varchar | 50 | Yes | Plot 28 | Free text | New site name |
| relocated_location_id | int | — | Yes | 2 | Integer | New location reference |
| relocated_x_coord | decimal | — | Yes | 40.5678 | Decimal (lon) | Relocated longitude |
| relocated_y_coord | decimal | — | Yes | -3.5678 | Decimal (lat) | Relocated latitude |
| relocated_area | varchar | 20 | Yes | Watamu | Free text | Relocated area name |
| relocation_datetime | datetime | — | Yes | 2025-02-11 08:00:00 | YYYY-MM-DD HH:MM:SS | Date/time of relocation |
| reason_for_relocation_id | int | — | Yes | 1 | FK reference | Reason for relocation ID |
| reason_for_relocation | varchar | 50 | Yes | Nest laid in a beach access road | Predefined / free text | Reason description |
| time_taken_to_relocate | numeric | — | Yes | 1.50 | Hours (decimal) | Time taken to relocate the nest |
| parties_at_relocation | ntext | — | Yes | Shungu, KWS, Jefwa | Free text | People/groups/organizations involved |
| num_eggs_relocated | int | — | Yes | 124 | Integer ≥ 0 | Number of relocated eggs|
| relocation_notes | varchar | 200 | Yes | Nest safely relocated | Free text | Notes on relocation |
| turtle_id | int | — | No | 3401 | FK reference | turtle reference|
| current_tag_1 | varchar | 20 | No | KBL123 | Alphanumeric | Primary tag |
| current_tag_2 | varchar | 20 | No | KBL124 | Alphanumeric | Secondary tag |
| turtle_ccl_cm | numeric | — | Yes | 95.20 | Decimal ≥ 0 | Curved carapace length (cm) |
| turtle_ccw_cm | numeric | — | Yes | 88.40 | Decimal ≥ 0 | Curved carapace width (cm) |
| turtle_characteristics | varchar | 500 | Yes | Notch on left rear flipper | Free text | Physical characteristics |
| hatching_outcome_name | varchar | 30 | Yes | Successful | Predefined categories | Hatching outcome |
| actual_hatch_datetime | datetime | — | Yes | 2025-04-12 02:00:00 | YYYY-MM-DD HH:MM:SS | Actual hatch time |
| num_actual_incubation_days | float | — | Yes | 60.5 | Decimal ≥ 0 | Incubation duration (days) |
| excavation_datetime | datetime | — | Yes | 2025-04-15 09:00:00 | YYYY-MM-DD HH:MM:SS | Excavation date/time |
| sun_exposure_type_name | varchar | 50 | Yes | Partial Shade | Predefined categories | Sun exposure |
| top_shell_depth_cm | float | — | Yes | 30.5 | Decimal ≥ 0 | Top shell depth  (cm)|
| bottom_shell_depth_cm | float | — | Yes | 60.0 | Decimal ≥ 0 | Bottom shell depth  (cm)|
| num_eggs_empty | smallint | — | Yes | 5 | Integer ≥ 0 | Empty eggs |
| num_eggs_early_dev | smallint | — | Yes | 3 | Integer ≥ 0 | Early development eggs |
| num_eggs_under_dev | smallint | — | Yes | 2 | Integer ≥ 0 | Underdeveloped eggs |
| num_eggs_mid_dev | smallint | — | Yes | 4 | Integer ≥ 0 | Mid development eggs |
| num_eggs_late_dev | smallint | — | Yes | 6 | Integer ≥ 0 | Late development eggs |
| num_eggs_micro | smallint | — | Yes | 1 | Integer ≥ 0 | Micro-sized eggs |
| num_eggs_unknown | smallint | — | Yes | 0 | Integer ≥ 0 | Unknown category |
| num_eggs_depredated | smallint | — | Yes | 2 | Integer ≥ 0 | Depredated eggs |
| num_eggs_yolkless | smallint | — | Yes | 1 | Integer ≥ 0 | Yolkless eggs |
| num_hatchlings_pipped_dead | smallint | — | Yes | 1 | Integer ≥ 0 | Dead pipped hatchlings |
| num_hatchlings_pipped_live | smallint | — | Yes | 3 | Integer ≥ 0 | Live pipped hatchlings |
| num_hatchlings_dead | smallint | — | Yes | 2 | Integer ≥ 0 | Dead hatchlings |
| num_hatchlings_live | smallint | — | Yes | 100 | Integer ≥ 0 | Live hatchlings |
| num_total_eggs_excavated | smallint | — | Yes | 120 | Integer ≥ 0 | Total eggs excavated |
| num_total_eggs_successful | smallint | — | Yes | 100 | Integer ≥ 0 | Successfully hatched eggs |
| num_relocated_eggs_missing | smallint | — | Yes | 2 | Integer ≥ 0 |number of missing eggs from total relocated eggs |
| num_relocated_eggs_extra | smallint | — | Yes | 1 | Integer ≥ 0 | Extra eggs found |
| nest_success_rate | float | — | Yes | 0.83 | 0–1 decimal | Success rate |
| rate_eggs_empty | float | — | Yes | 0.04 | 0–1 decimal | Empty egg rate |
| rate_eggs_early_dev | float | — | Yes | 0.02 | 0–1 decimal | Rate of early developed eggs (%) |
| rate_eggs_under_dev | float | — | Yes | 0.01 | 0–1 decimal | Rate of underdeveloped eggs (%) |
| rate_eggs_mid_dev | float | — | Yes | 0.03 | 0–1 decimal | Rate of mid-developed eggs (%) |
| rate_eggs_late_dev | float | — | Yes | 0.05 | 0–1 decimal | Rate of late-developed eggs (%) |
| rate_eggs_micro | float | — | Yes | 0.01 | 0–1 decimal | Rate of micro-eggs (%) |
| rate_eggs_unknown | float | — | Yes | 0.00 | 0–1 decimal | Rate of unknown eggs (%) |
| rate_eggs_depredated | float | — | Yes | 0.02 | 0–1 decimal | Rate of depredated eggs (%) |
| rate_eggs_yolkless | float | — | Yes | 0.01 | 0–1 decimal | Rate of yolkless eggs (%) |
| rate_hatchlings_pipped_dead | float | — | Yes | 0.01 | 0–1 decimal | Rate of dead pipped hatchlings (%) |
| rate_hatchlings_pipped_live | float | — | Yes | 0.02 | 0–1 decimal | Rate of live pipped hatchlings (%) |
| rate_hatchlings_dead | float | — | Yes | 0.02 | 0–1 decimal | Rate of dead hatchlings (%) |
| rate_hatchlings_live | float | — | Yes | 0.83 | 0–1 decimal | Rate of live hatchlings (%) |
| nest_failure_cause_name | varchar | 50 | Yes | Flooding | Predefined categories | Cause of nest failure |
| excavation_notes | varchar | 300 | Yes | Successful excavation | Free text | Notes from excavation |

---
