# Sensorless Homing on SW

Sensorless homing for XZ Kinematics:
https://github.com/thomasfjen/SW_MISC/blob/main/homing_sw.cfg
Based on: https://docs.vorondesign.com/community/howto/clee/sensorless_xy_homing.html#homing-macros but adapted for corexz kinematics

Why? https://www.klipper3d.org/TMC_Drivers.html#using-macros-when-homing
"It is a good idea for the macro to pause at least 2 seconds prior to starting sensorless homing (or otherwise ensure that there has been no movement on the stepper for 2 seconds). Without a delay it is possible for the driver's internal stall flag to still be set from a previous move.

It can also be useful to have that macro set the driver current before homing and set a new current after the carriage has moved away."

After the initial Z hop to not scrape the bed while homing the stepper drivers need a little pause, without that x homing may get a false home. 
