## `schema`

| name           | type    | description                                                                                                                                                                                 | constraints                                                                                                                                                                                               | warnings                       |
|:---------------|:--------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------|
| segment_tod_id | any     | Primary key.                                                                                                                                                                                | {'required': True}                                                                                                                                                                                        |                                |
| segment_id     | any     | Foreign key to segment table.                                                                                                                                                               | {'required': True}                                                                                                                                                                                        |                                |
| timeday_id     | any     | Conditionally required (either timeday_id or time_day). Foreign key to time_set_definitions.                                                                                                |                                                                                                                                                                                                           |                                |
| time_day       | string  | Conditionally required (either timeday_id or time_day). XXXXXXXX_HHMM_HHMM, where XXXXXXXX is a bitmap of days of the week, Sunday-Saturday, Holiday. The HHMM are the start and end times. |                                                                                                                                                                                                           |                                |
| capacity       | number  | Optional. Capacity (veh/hr/ln)                                                                                                                                                              | {'minimum': 0}                                                                                                                                                                                            |                                |
| free_speed     | number  | Optional. Free flow speed in short_length units per hour                                                                                                                                    | {'minimum': 0, 'maximum': 200}                                                                                                                                                                            | {'minimum': 1, 'maximum': 120} |
| lanes          | integer | Optional. Number of lanes in the direction of travel (must be consistent with link lanes + lanes added).                                                                                    |                                                                                                                                                                                                           |                                |
| l_lanes_added  | integer | Optional. # of lanes added on the left of the road link (negative indicates a lane drop).                                                                                                   |                                                                                                                                                                                                           |                                |
| r_lanes_added  | integer | Optional. # of lanes added on the right of the road link (negative indicates a lane drop).                                                                                                  |                                                                                                                                                                                                           |                                |
| bike_facility  | string  | Optional. Types of bicycle accommodation based on the National Bikeway Network Data Template (Table 1-A at https://nmtdev.ornl.gov/assets/templates/NBN_DataTemplates_final.pdf)            | {'enum': ['unseparated bike lane', 'buffered bike lane', 'separated bike lane', 'counter-flow bike lane', 'paved shoulder', 'shared lane', 'shared use path', 'off-road unpaved trail', 'other', 'none']} |                                |
| ped_facility   | string  | Optional. Type of pedestrian accommodation: unknown,none,shoulder,sidewalk,offstreet_path.                                                                                                  | {'enum': ['unknown', 'none', 'shoulder', 'sidewalk', 'offstreet_path']}                                                                                                                                   |                                |
| parking        | string  | Optional. Type of parking: unknown,none,shoulder,sidewalk,offstreet_path.                                                                                                                   | {'enum': ['unknown', 'none', 'shoulder', 'sidewalk', 'offstreet_path']}                                                                                                                                   |                                |
| toll           | number  | Optional. Toll in currency units                                                                                                                                                            |                                                                                                                                                                                                           |                                |
| allowed_uses   | string  | Optional. Set of allowed uses that should appear in either the use_definition or use_group tables; comma-separated.                                                                         |                                                                                                                                                                                                           |                                |