### Sea Turtle Nest Monitoring Data Dictionary


| Field Name        | Data Type        | Description                                  | Example Value | Allowed Values / Format |
|-------------------|------------------|----------------------------------------------|---------------|-------------------------|
| nest_id           | Integer / AutoID | Unique identifier for each turtle nest       | 1023          | Auto generated |
| date_recorded     | Date             | Date the nest was recorded                   | 2026-03-15    | YYYY-MM-DD |
| beach_name        | Text             | Name of beach where nest was found           | Watamu Beach  | Text |
| latitude          | Decimal          | Latitude coordinate of nest location         | -3.3532       | GPS decimal |
| longitude         | Decimal          | Longitude coordinate of nest location        | 40.0196       | GPS decimal |
| species           | Text             | Turtle species observed                      | Green Turtle  | Green, Hawksbill, Olive Ridley, Loggerhead |
| nest_status       | Text             | Current status of the nest                   | Active        | Active, Relocated, Hatched, Predated |
| nest_depth_cm     | Integer          | Depth of nest chamber                        | 65            | Numeric (cm) |
| clutch_size       | Integer          | Number of eggs counted in nest               | 112           | Numeric |
| relocation        | Boolean          | Indicates if nest was relocated              | Yes           | Yes / No |
| relocation_reason | Text             | Reason for relocation                        | Risk of flooding | Flooding, Predation risk, Human disturbance |
| observer_name     | Text             | Name of ranger or data collector             | J. Otieno     | Text |
| organization      | Text             | Monitoring organization                      | Marine Org    | Text |
| hatch_success     | Decimal          | Percentage of eggs hatched                   | 82.5          | 0–100 |
