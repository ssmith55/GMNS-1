##	segment	

A road segment is a portion of a link. It is similar to a linear
event in ESRI, and is typically used to indicate where the number of
lanes (or other properties) changes on a link. The following fields are
used to define a segment:

  - link\_id

  - ref\_node_id, the node from which the linear referencing starts (typically the from_node of the link)

  - start\_lr, the start of the segment, measured as distance from
    the ref\_node

  - end\_lr, the end of the segment, measured as distance from the
    ref\_node

For example, a 5000 foot hill climbing lane on link 102 that begins 1000
feet downstream of Node 12, would have the following segment:

  - link\_id = 102

  - ref\_node_id = 12

  - start\_lr = 1000 feet

  - end\_lr = 6000 feet

Most of the fields in the segment table are simply inherited from
the link table. When values are present in these fields, these
values override the values in the link table along the segment.

If segments overlap, but one is contained within the other, the smaller
segment’s characteristics should prevail. Partial overlap of segments is
more complicated; validation tools should throw a warning in this
scenario.

segment data dictionary

| Field                                   | Type                 | Required? | Comment                                                                                                                                                                                                                          |
| --------------------------------------- | -------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| segment\_id                             | Segment\_ID          | Required  | Primary key                                                                                                                                                                                                                      |
| link_id | Link_ID             | Required  | The link that the segment is located on (Foreign key, link table)                                                                                                                                                         |
| ref\_node_id                               | Node\_ID             | Required  | Foreign key – Node table, where the distance is 0                                                                                                                                                                               |
| start\_lr                         | NUMERIC               | Required  | Distance from Ref\_Node in short_length units                                                                                                                                                                                                         |
| end\_lr                           | NUMERIC               | Required  | Distance from Ref\_Node in short_length units                                                                                                                                                                                                         |
| grade | DOUBLE  | Optional  |  Percent grade of the segment (<0 is down) |
| capacity                                | NUMERIC              | Optional  | Capacity (veh / hr / lane)                                                                                                                                                                                                              |
| free_speed                               | NUMERIC              | Optional  | Free flow speed in long_length units per hour                                                                                                                                                                                                                  |
| lanes			                              | INTEGER		            | Optional	| Number of lanes in the direction of travel (must be consistent with link lanes + lanes added) 	                                                                                                                                |
| l_lanes_added                           | INTEGER              | Optional  | # of lanes added on the left of the link (negative indicates a lane drop).                                                                                                                                                                                      |
| r_lanes_added                           | INTEGER              | Optional  | # of lanes added on the right of the link (negative indicates a lane drop).                                                                                                                                                                                      |
| bike_facility                            | TEXT                 | Optional  | Type of bicycle accommodation: unknown, none, wcl, bikelane, cycletrack                                                                                                                                                          |
| ped_facility                             | TEXT                 | Optional  | Type of pedestrian accommodation: unknown, none, shoulder, sidewalk                                                                                                                                                              |
| parking                                 | TEXT                 | Optional  | Type of parking: unknown, none, parallel, angle, other                                                                                                                                                                           |
| allowed\_uses                           | Use\_Set             | Optional  | Set of allowed uses: shoulder, parking, walk, all, bike, auto, hov2, hov3, truck, bus, etc.                                                                                    |
| toll          | NUMERIC       | Optional  | currency units                                     |
| jurisdiction  | TEXT  | Optional  | Owner/operator of the segment  |
| row_width | NUMERIC  | Optional  |  Width (in short_length units) of the entire right-of-way (both directions).  | 

Ad hoc fields may also be added. Examples of other fields might include jam density, wave speed, traffic message channel (TMC) identifier, traffic count sensor identifier and location, average daily traffic, etc.
