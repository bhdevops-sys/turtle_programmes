### Turtle interaction verification points 
This guide provides SQL scripts and verification points to ensure turtle interaction and nesting data are accurate, consistent, and free from duplicates or invalid entries.

---
### Overall Data Integrity Rules

- **Sites & Parties:** No duplicates, misspellings, or wrong entries  
- **Turtles:** Tags and names correctly assigned, no duplicates, no invalid IDs  
- **Interactions:** Outcomes, GPS, release times always captured  
- **Nests:** Sequential IDs, valid hatch dates, track widths, relocation completeness, incubation data present  
- **Excavations:** Recorded on time with full details  
- **Nest failure:** Correct failure cause assigned  

All verification queries should ideally return **zero results** unless otherwise noted.

Prior undertaking any of the cleansing steps, create a duplicate of the database.
---

### How to Use this guide

1. Open **SSMS** or **Azure Data Studio**.  
2. Connect to the database storing turtle interaction and nest data.  
3. Copy and run the SQL scripts provided in each section.  
4. Investigate any records returned — they may indicate data quality issues.  
5. Spatially map coordinates for correct nest location positioning verification.  
6. Repeat these checks periodically to ensure **high-quality turtle monitoring data**.

---

## 1. Party and Site Checks

### Party Names
Ensure no wrong name/spelling is selected:
```sql
SELECT party_name, COUNT(*) AS counts 
FROM party 
GROUP BY party_name  
HAVING COUNT(*) > 1;
```

Check with concatenated fields:
```sql
SELECT CONCAT(party_type_id, ':', party_name, ':', site_id) AS mergedColumns 
INTO #temp_v1 
FROM party;

SELECT COUNT(*) AS occurrence, mergedColumns 
FROM #temp_v1 
GROUP BY mergedColumns HAVING COUNT(*) > 1;
```

### Duplicate Areas
```sql
SELECT area_name, COUNT(*) AS occurrence 
FROM area 
GROUP BY area_name HAVING COUNT(*) > 1;
```

### Duplicate Sites
```sql
SELECT CONCAT(site_name, ':', area_id) AS mergedColumns 
INTO #temp_v2  
FROM site;

SELECT COUNT(*) AS occurrence, mergedColumns 
FROM #temp_v2  
GROUP BY mergedColumns HAVING COUNT(*) > 1;
```

### Fisher Names
Prevent duplicates and spelling errors (similar logic as above).  
> Note: All parties are linked to a site to help identify them correctly.

---

## 2. Turtle Interaction Checks

### Landing and Capture Sites
Confirm they are written correctly for new sites and no duplicates are created (manual check).

### Turtle Tags and Names
```sql
-- Check same tag not used twice
SELECT * FROM dbo.turtle 
WHERE current_tag_1 = current_tag_2  
AND current_tag_1 != 'none';

-- Check tag ID not used as turtle name
SELECT * FROM dbo.turtle 
WHERE (current_tag_1 = turtle_name OR current_tag_2 = turtle_name)
AND current_tag_1 != 'none';
```

### Turtle Measurements
Ensure correct CCL, CCW & weight captured for nesting interactions:
```sql
SELECT * FROM dbo.turtle_interaction 
WHERE (turtle_ccl_cm IS NULL OR turtle_ccw_cm IS NULL OR turtle_weight_kg IS NULL)
AND interaction_date_time > '2021-11-01' 
AND interaction_type_id IN (2,3);
```

### Interaction Outcome
```sql
SELECT * FROM dbo.turtle_interaction 
WHERE interaction_outcome IS NULL;
```

### Release Datetime
```sql
SELECT * FROM dbo.turtle_release 
WHERE release_datetime IS NULL;
```

### GPS Capture
(Not expected to return zero – depends on chosen date.)
```sql
SELECT * FROM dbo.turtle_interaction   
WHERE interaction_date_time > '2021-11-01'  
AND interaction_gps = '0.000000, 0.000000'  
ORDER BY caught_date_time DESC;
```

### Protect 'None' Tags from updates
```sql
SELECT * FROM turtle 
WHERE turtle_id IN (162,163,164,165,166,168) 
AND current_tag_1 <> 'None' 
AND current_tag_2 <> 'None';
```

---

## 3. Nesting Data Verification

### Nest ID Sequence
Nest IDs should follow sequentially.

### Expected Hatch Date
Should be ~60 days after laid date:
```sql
SELECT nest_id, laid_date_time, expected_hatch_datetime,
       DATEDIFF(day, CAST(laid_date_time AS date), CAST(expected_hatch_datetime AS date)) AS day_diff
FROM turtle_nest  
WHERE DATEDIFF(day, CAST(laid_date_time AS date), CAST(expected_hatch_datetime AS date)) <> 60;
```

### Reporter Name
```sql
SELECT DISTINCT reporter_name  
FROM v_all_nest_fields  
ORDER BY reporter_name ASC;
```

### Track Width
```sql
SELECT * FROM turtle_nest 
WHERE turtle_track_width_cm IS NULL 
AND reason_for_no_track_width IS NULL;
```

### Nest Location (Manual Mapping Check)
Map coordinates to confirm correct nest location placement.

### Coordinates Check
```sql
-- Original
SELECT * FROM v_all_nest_fields 
WHERE original_x_coord = '0.000000' OR original_y_coord = '0.000000';

-- Relocated
SELECT * FROM v_all_nest_fields 
WHERE relocated_x_coord = '0.000000' OR relocated_y_coord = '0.000000';
```

### Distance from HWM
```sql
SELECT nest_id, reason_for_relocation, reason_for_relocation_id, distance_from_hwm_m 
FROM v_all_nest_fields 
WHERE reason_for_relocation_id = 1 
AND distance_from_hwm_m >= 0 
ORDER BY distance_from_hwm_m ASC;

-- Not relocated but below HWM
SELECT nest_id, reason_for_relocation, reason_for_relocation_id, is_relocated, distance_from_hwm_m 
FROM v_all_nest_fields 
WHERE is_relocated = 'No' 
AND distance_from_hwm_m <= 0 
ORDER BY distance_from_hwm_m ASC;
```

### Nest Relocation
```sql
SELECT * FROM v_all_nest_fields  
WHERE is_relocated = 'Yes'  
AND relocation_datetime IS NULL;

SELECT * FROM v_all_nest_fields  
WHERE is_relocated = 'Yes'  
AND num_eggs_relocated IS NULL;
```

### Hatching Outcome
```sql
SELECT * FROM v_all_nest_fields  
WHERE hatching_outcome_name <> 'success'  
AND num_eggs_empty > 1;
```

### Incubation Days
```sql
SELECT * FROM v_all_nest_fields   
WHERE hatching_outcome_name IS NOT NULL 
AND num_actual_incubation_days IS NULL  
AND laid_date_time > '2023';
```

### Excavation Records
Check if excavation happens 3 days after nest hatching:
```sql
SELECT nest_id, laid_date_time, actual_hatch_datetime, 
       DATEDIFF(DAY, actual_hatch_datetime, GETDATE()) AS diff 
FROM v_all_nest_fields 
WHERE DATEDIFF(DAY, actual_hatch_datetime, GETDATE()) > 3 
AND YEAR(actual_hatch_datetime) = YEAR(GETDATE()) 
AND excavation_datetime IS NULL 
AND hatching_outcome_name <> 'Fail' 
ORDER BY 4 ASC;
```

### Complete  Nest Excavation Records
```sql
SELECT * FROM nest_excavation 
WHERE sun_exposure_type_id IS NULL 
OR top_shell_depth_cm IS NULL 
OR bottom_shell_depth_cm IS NULL;
```

### Nest Failure Cause
```sql
SELECT * FROM v_all_nest_fields 
WHERE num_eggs_empty < 1 
AND nest_failure_cause_name = 'N/A Nest Successful';
```

### Relocation Records
Check relocation record completeness:
```sql
SELECT * FROM nest_relocation  
WHERE (relocation_datetime IS NULL 
    OR reason_for_relocation IS NULL 
    OR original_bottom_egg_depth_cm IS NULL 
    OR num_eggs_relocated IS NULL 
    OR new_bottom_egg_depth_cm IS NULL 
    OR new_chamber_width_cm IS NULL 
    OR new_top_egg_depth_cm IS NULL 
    OR new_location_id IS NULL)
AND YEAR(relocation_datetime) > 2020;
```

---
