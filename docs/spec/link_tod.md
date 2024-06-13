## `schema`

| name          | type    | description                                                                                                                                                                                 | constraints                                                                                                                                                                                               | warnings                         |
|:--------------|:--------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------|
| link_tod_id   | any     | Primary key                                                                                                                                                                                 | {'required': True}                                                                                                                                                                                        |                                  |
| link_id       | any     | Required. Foreign key, link table                                                                                                                                                           | {'required': True}                                                                                                                                                                                        |                                  |
| timeday_id    | any     | Conditionally required (either timeday_id or time_day). Foreign key to time_set_definitions.                                                                                                |                                                                                                                                                                                                           |                                  |
| time_day      | string  | Conditionally required (either timeday_id or time_day). XXXXXXXX_HHMM_HHMM, where XXXXXXXX is a bitmap of days of the week, Sunday-Saturday, Holiday. The HHMM are the start and end times. |                                                                                                                                                                                                           |                                  |
| capacity      | number  | Optional. Capacity (veh / hr / lane)                                                                                                                                                        | {'minimum': 0}                                                                                                                                                                                            |                                  |
| free_speed    | number  | Optional. Free flow speed in long_distance units per hour                                                                                                                                   | {'minimum': 0, 'maximum': 200}                                                                                                                                                                            | {'minimum': 1, 'maximum': 120}   |
| lanes         | integer | Optional. Number of permanent lanes (not including turn pockets) in the direction of travel open to motor vehicles. It does not include bike lanes, shoulders or parking lanes.             | {'minimum': 0}                                                                                                                                                                                            |                                  |
| bike_facility | string  | Optional. Types of bicycle accommodation based on the National Bikeway Network Data Template (Table 1-A at https://nmtdev.ornl.gov/assets/templates/NBN_DataTemplates_final.pdf)            | {'enum': ['unseparated bike lane', 'buffered bike lane', 'separated bike lane', 'counter-flow bike lane', 'paved shoulder', 'shared lane', 'shared use path', 'off-road unpaved trail', 'other', 'none']} |                                  |
| ped_facility  | string  | Optional. Type of pedestrian accommodation: unknown, none, shoulder, sidewalk, offstreet path                                                                                               | {'enum': ['unknown', 'none', 'shoulder', 'sidewalk', 'offstreet_path']}                                                                                                                                   |                                  |
| parking       | string  | Optional. Type of parking: unknown, none, parallel, angle, other                                                                                                                            | {'enum': ['unknown', 'none', 'parallel', 'angle', 'other']}                                                                                                                                               |                                  |
| allowed_uses  | string  | Optional. Set of allowed uses that should appear in either the use_definition or use_group tables; comma-separated.                                                                         |                                                                                                                                                                                                           |                                  |
| toll          | number  | toll in currency units.                                                                                                                                                                     |                                                                                                                                                                                                           | {'minimum': 0, 'maximum': 10000} |