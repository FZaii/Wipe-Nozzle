# Klipper macros

These macros are  based on the great Annex magprobe dockable probe macros "#Originally developed by Mental, modified for better use on K-series printers by RyanG and Trails", kudos to them.
That macro as since evolved into a klipper plugin that currently is pending inclusion in klipper, more information [here](https://github.com/Annex-Engineering/Quickdraw_Probe/tree/main/Klipper_Macros)

Would alse like to thank the Voron discord community and VoronDesign for all the work, suggestions and support that they have given to improve on the macros.

## Updating from an earlier version

While you should read these instructions to the end, as the necessary helper functions are now split on different files and it's better explained below, as a current user of the klicky macros, it's easier to configure.

The first macro on the old klicky-probe.cfg contained all the necessary variables, you should the values you changed one by one to the new klicky-variables.cfg, the most important are these ones:

```ini
# if you do not have any of these variables, read the explanation on klicky-variables.cfg and the setup of the macros on your respective printer, this is a quick start quide
variable_enable_z_hop           # set this to false for beds that fall significantly under gravity (almost to Z max)
variable_max_bed_y              # bed max y size
variable_max_bed_x              # bed max x size

variable_z_endstop_x            # copy this value over your old file
variable_z_endstop_y            # copy this value over your old file

variable_docklocation_[x,y,z]   # copy this value over your old file
Variable_dockmove_[x,y,z]       # use 40,0,0 it's the old default
Variable_attachmove_[x,y,z]     # use 0,30,0 it's the old default
```
