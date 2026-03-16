### Sea Turtle Nest Monitoring Data Dictionary
#### turtle_nest

| Field Name | SQL Type | Length | Nullable | Example Value | Allowed Values / Format | Description |
|------------|----------|--------|----------|---------------|-------------------------|-------------|
| nest_id | varchar | 20 | No | NEST_2026_001 | Unique string ID | Unique identifier for the turtle nest |
| turtle_id | int | 10 | No | 1452 | Integer | Identifier linking to the turtle record |
| laid_date_time | datetime | — | No | 2026-03-15 02:30:00 | YYYY-MM-DD HH:MM:SS | Date and time when the nest was laid |
| reporter_party_id | varchar | 8 | No | RPT001 | Alphanumeric code | ID of the person or organization reporting the nest |
| temperature_logger_id_1 | int | 10 | Yes | 34 | Integer | ID of the first temperature logger placed in the nest |
| temperature_logger_id_2 | int | 10 | Yes | 35 | Integer | ID of the second temperature logger placed in the nest |
| nest_location_original_id | int | 10 | No | 87 | Integer (Location reference ID) | Original nest location reference |
| distance_from_hwm_m | numeric | 8,2 | Yes | 12.50 | Decimal (meters) | Distance from High Water Mark |
| turtle_track_width_cm | numeric | 8,2 | Yes | 95.30 | Decimal (centimeters) | Width of turtle track measured |
| reason_for_no_track_width | int | 10 | Yes | 2 | Reference code (lookup table) | Reason track width was not recorded |
| is_relocated | bit | 1 | Yes | 1 | 0 = No, 1 = Yes | Indicates if the nest was relocated |
| expected_hatch_datetime | smalldatetime | — | Yes | 2026-05-12 18:00 | YYYY-MM-DD HH:MM | Estimated hatch date and time |
| nest_notes | varchar | 300 | Yes | Nest near vegetation line | Free text (max 300 chars) | Additional notes about the nest |

#### nest_excavation
#### nest_relocation
#### party
#### party_type
#### hatching
#### sex
#### species
#### turtle
#### hatching_outcome
#### party_at_hatching
#### party_at_nesting
#### party_at_relocation
#### turtle_interaction
#### party_at_excavation
#### temp_logger
#### nest_failure_cause
#### sun_exposure_type
#### location
#### site
#### area
