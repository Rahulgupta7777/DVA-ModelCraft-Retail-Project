## Dataset Summary

| Item | Details |
|---|---|
| Dataset name | Road Traffic Accident Dataset |
| Source | https://www.kaggle.com/datasets/saurabhshahane/road-traffic-accidents |
| Raw file name | RTA_Dataset.csv |
| Last updated | Historical (Kaggle Archive) |
| Granularity | One row per reported traffic accident |

## Column Definitions

| Column Name | Data Type | Description | Example Value | Used In | Cleaning Notes |
|---|---|---|---|---|---|
| Time | string / time | The time of day the accident occurred | 17:02:00 | EDA / Tableau | Cast to datetime to extract hour, kept as string for Tableau export |
| Day_of_week | string | The day of the week the accident occurred | Monday | EDA / Tableau | Capitalized; used to derive `Is_weekend` |
| Age_band_of_driver | string | Demographic age range of the driver | 18-30 | EDA / Tableau | Nulls filled with 'Unknown' |
| Sex_of_driver | string | Gender of the driver involved | Male | EDA / Tableau | Capitalized; nulls filled with 'Unknown' |
| Driving_experience | string | Driver's level of experience | 1-2yr | EDA | Nulls filled with 'Unknown' |
| Type_of_vehicle | string | The classification of the vehicle | Automobile | EDA | Nulls filled with 'Unknown' |
| Service_year_of_vehicle | string | The age/service time of the vehicle | 2-5yrs | EDA | High missing rate (~32%); defensively imputed with 'Unknown' |
| Defect_of_vehicle | string | Pre-existing mechanical issues | No defect | EDA | High missing rate (~36%); defensively imputed with 'Unknown' |
| Area_accident_occured | string | The zone or location type of the crash | Residential areas | EDA / Tableau | Stripped leading/trailing whitespace; filled nulls |
| Lanes_or_Medians | string | Road divider and lane structure | Two-way (divided) | EDA | Nulls filled with 'Unknown' |
| Road_allignment | string | Curvature and terrain of the road | Tangent road with flat terrain | EDA | Nulls filled with 'Unknown' |
| Types_of_Junction | string | Type of intersection where crash happened | Y Shape | EDA / Tableau | Nulls filled with 'Unknown' |
| Road_surface_type | string | Physical material of the road | Asphalt roads | EDA | Nulls filled with 'Unknown' |
| Road_surface_conditions | string | State of the road surface at time of crash | Dry | EDA / Tableau | Nulls filled with 'Unknown'; used to derive `Is_Adverse_Condition` |
| Light_conditions | string | Visibility and lighting environment | Daylight | EDA / Tableau | Nulls filled with 'Unknown' |
| Weather_conditions | string | Weather state at time of crash | Normal | EDA / Tableau | Nulls filled with 'Unknown'; used to derive `Is_Adverse_Condition` |
| Type_of_collision | string | How the vehicles collided | Collision with vehicles | EDA | Nulls filled with 'Unknown' |
| Number_of_vehicles_involved | int | Total count of vehicles in the accident | 2 | KPI / Tableau | Cast to integer; missing filled with median |
| Number_of_casualties | int | Total count of people injured/killed | 1 | KPI / Tableau | Cast to integer; missing filled with median |
| Vehicle_movement | string | Action the vehicle was taking before crash | Going straight | EDA | Nulls filled with 'Unknown' |
| Casualty_class | string | Role of the injured person | Driver or rider | EDA | Nulls filled with 'Unknown' |
| Sex_of_casualty | string | Gender of the injured person | Male | EDA | Capitalized; nulls filled with 'Unknown' |
| Age_band_of_casualty | string | Demographic age range of the casualty | 18-30 | EDA | Nulls filled with 'Unknown' |
| Casualty_severity | string | Specific severity level of the casualty | 3 | EDA | Nulls filled with 'Unknown' |
| Pedestrian_movement | string | Action the pedestrian was taking (if any) | Not a Pedestrian | EDA | Nulls filled with 'Unknown' |
| Cause_of_accident | string | Primary attributed cause of the crash | Moving Backward | EDA / Tableau | Nulls filled with 'Unknown' |
| Accident_severity | string | Overall severity outcome of the crash | Slight Injury | EDA / KPI / Tableau | **Target Variable.** No nulls present. |

## Derived Columns

| Derived Column | Logic | Business Meaning |
|---|---|---|
| Hour_of_day | Extracted `.dt.hour` from the `Time` column | Allows for chronological grouping and time-series analysis without minute-level noise. |
| Patrol_Shift | 06:00-14:00 (Morning), 14:00-22:00 (Evening), 22:00-06:00 (Night) | Groups hours into actionable operational blocks for traffic authorities to schedule highway patrol deployments. |
| Is_Adverse_Condition | `Yes` if Weather is NOT 'Normal' OR Road is NOT 'Dry' | Consolidates complex environmental variables into a single binary flag to quickly assess if bad weather/roads caused severe crashes. |
| Is_weekend | `Weekend` if Saturday/Sunday, else `Weekday` | Differentiates traffic patterns, as weekend drivers and volumes behave differently than weekday commuter traffic. |
| Severity_score | Maps 'Slight' = 1, 'Serious' = 2, 'Fatal' = 3 | Converts categorical severity into a numeric weight, allowing Tableau to calculate average severity metrics across dimensions. |

## Data Quality Notes

- **Missing Calendar Dates:** The dataset includes `Time` and `Day_of_week` but lacks standard calendar dates (Month/Year). This prevents longitudinal forecasting, seasonality analysis, or year-over-year trend comparisons.
- **Defensive Imputation:** Columns like `Service_year_of_vehicle` and `Defect_of_vehicle` contained >30% missing values. To preserve the row count for the Capstone requirement, these were assigned an explicit 'Unknown' category rather than using mode imputation, which would have artificially skewed the data.
- **Scoping Reductions:** Five columns (`Educational_level`, `Work_of_casuality`, `Fitness_of_casuality`, `Vehicle_driver_relation`, `Owner_of_vehicle`) were intentionally dropped during ETL phase as they fell outside the actionable scope of the "City Planning & Public Safety" problem statement.
- **Duplicate Records:** Exact duplicate rows were identified and removed during the cleaning phase to prevent double-counting in KPI aggregations.
- **Tableau Type Flattening:** All `category` data types were cast back to standard `string` formats in the final `05_final_load_prep.ipynb` step to ensure seamless import into Tableau Public without hierarchy errors.