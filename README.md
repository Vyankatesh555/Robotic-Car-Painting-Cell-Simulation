# Robotic-Car-Painting-Cell-Simulation

**Name:** Vyankatesh Pandharpurkar

**College:** AISSMS College of Engineering, Pune

**Software used:** RoboDK version:6.1, Blender version:5.1

**Robot selected:** ABB IRB 1300-10/1.15, mounted inverted on a custom 3-axis overhead gantry (9 axes in total)

Practical assessment for the Robotics Simulation Intern position at Yuktii AI Labs.

## Overview
One industrial robot paints the exterior panels of a car body inside a glass-walled painting cell. The ABB IRB 1300 hangs from a custom X-Y-Z gantry. The arm and the gantry move together as one 9-axis system, so one robot reaches every side of the car without a second robot or a turntable.

## Links
| Item | Link |
|---|---|
| Technical report | [Technical_Report.pdf] |
| Demo video | [https://drive.google.com/file/d/1VxoycxTVcjbKSUFnx-HmSLqNhDA8X-yx/view?usp=drive_link] |
| Google Drive folder | [https://drive.google.com/drive/folders/1f1qFb8xROggR6NAO5vW30rXwBKvUpfL-?usp=drive_link] |
| Weblink to Simulation | [https://web.robodk.com/lnk/3132323431233138] |

## Setup
| Item | Value |
|---|---|
| Robot | ABB IRB 1300-10/1.15 (reach 1.15 m, payload 10 kg), inverted |
| Gantry | Custom 3-axis, travel X 5800 / Y 4210 / Z 1100 mm |
| Car | Volkswagen Golf GTI 2024, 4300 x 1800 x 1270 mm |
| Cell | 7000 x 5300 mm, with glass safety walls |
| Tool | Generic Paint Sprayer (RoboDK library), TCP at the spray impact point |
| Spray speed | 200 mm/s |
| Approach / retract | 100 mm along the surface normal |
| Tool Z rotation | +/- 180 deg, step 20 deg |

## Approach
1. **Models:** car, gantry and glass cell prepared in Blender, exported as STL, one file per part.
2. **Cell:** gantry built as a 3-axis mechanism in RoboDK. The robot is mounted on its Z flange and synchronized with it.
3. **Paths:** the Surface Pattern Generator makes a target pattern for each panel. A curve follow project solves each pattern with smart axis optimization, so the arm and the gantry move in sync.
4. **Main program:** `Main_Prog` calls the panel programs in order, with safe transfer moves between them.
5. **Collision checking:** collision map active for robot, tool, car, gantry and cell.

## Painted surfaces
[Hood, roof, tailgate, front doors, rear doors, parts of frame, bumpers]

## Results
| Metric | Result |
|---|---|
| Surfaces painted | [10] of [10] |
| Path points reached | [100] % |
| Collisions in final program | [ 0 ] |
| Simulated cycle time | [11m 9.7s] |

## How to run
1. Install RoboDK [version:6.1].
2. Open `Vyankatesh_Robotic_Car_Painting_cell.rdk`.
3. Double-click `Main_Prog` to run the full painting program.
4. If the yellow path is not visible, right-click `Main_Prog` and choose Recalculate.

## Limitations
The car is a compact hatchback, smaller than the reference car in the brief.
Some Parts(Frame and Both Bumpers and some of the tailgate) do not have a pattern/path that evenly/efficiently covers the surface.

