# start_g_code_WT150: Start and end g-code for Weistek WT150
## start gcode
M104 S220 T0
G21 (Metric FTW)
G90 (Absolute Positioning)
M18 (This disables the stepper motors.)
M103 ;Madanh: no extrusion


G161 Y X F2500
G92 X0 Y0 Z0 A0 B0
G1 X5.0 Y5.0 Z-5.0 F450
G162 Z F450 
G161 Y X F2500 (Home X axis maximum; go until reaching the end stop.)
G92 Z141.51
G92 X0 Y0 (set zero for X and Y)



M108 R8.0 (Extruder speed = max)
G1 Z10.0 F500
M6 T0 (wait for toolhead parts, nozzle, HBP, etc., to reach temperature)

G04 P1000
M01



G1 Z25 F5000 (lift nozzle)
G1 X75 Y75 F5000 (go to center)
M01

## End gcode

M103
G1 Z140.0 F450.0
(**** end move to cooling position ****)
M73 P95 (display progress)
M18 (Turn off steppers)

M73 P96 (display progress)
M6 T0 (wait for toolhead parts (nozzle, HBP, etc) to reach temperature)
M104 S0 T0 (set extruder temperature)
M01 (Remove the object then click okay.)

(**** end eject ****)
(**** begin cool for safety ****)
M104 S0 T0 (set extruder temperature)

M109 S0 T0 (set heated-build-platform temperature)
(**** end cool for safety ****)

(**** end of end.txt ****)
