# Sensorless Homing on SW

Sensorless homing for XZ Kinematics:
[homing_sw.cfg](https://github.com/thomasfjen/SW_MISC/blob/main/homing_sw.cfg)  
Based on: [Voron Sensorless Macros](https://docs.vorondesign.com/community/howto/clee/sensorless_xy_homing.html#homing-macros) but adapted for corexz kinematics  

Why?  
[Klipper Docs](https://www.klipper3d.org/TMC_Drivers.html#using-macros-when-homing): 
"It is a good idea for the macro to pause at least 2 seconds prior to starting sensorless homing (or otherwise ensure that there has been no movement on the stepper for 2 seconds). Without a delay it is possible for the driver's internal stall flag to still be set from a previous move.
It can also be useful to have that macro set the driver current before homing and set a new current after the carriage has moved away."

After the initial Z hop to not scrape the bed while homing the stepper drivers need a little pause, without that x homing may get a false home. 


# Eddy Coil with EBB36

[Example Config](https://github.com/thomasfjen/Klipper_MISC/blob/main/eddy_coil.cfg) when using the BTT Eddy Coil connected to the EBB36 as Probe.  
Don't use it as virtual Z Endstop, Eddy Coil does not have an thermistor at the coil so you can't calibrate thermal compensation.
