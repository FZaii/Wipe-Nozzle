# Klipper macros
将“fz-wipe-nozzle.cfg”上传至klipper配置文件目录中，并在printer.cfg中引用，调用时宏命令为“WIPE_NOZZLE”

```ini
[include fz-wipe-nozzle.cfg]
```
*printer.cfg引用参考：*

```ini
[gcode_macro PRINT_START]
gcode:
    {% set BED_TEMP = params.BED_TEMP|default(60)|float %}
    {% set EXTRUDER_TEMP = params.EXTRUDER_TEMP|default(210)|float %}
    {% set BED_TEMP_PRE = 50|float %}
    {% set EXTRUDER_TEMP_PRE = 140|float %}

    M104 S{EXTRUDER_TEMP_PRE}       #设置挤出机预热温度
    M140 S{BED_TEMP_PRE}            #设置热床预热温度
    BED_MESH_CLEAR                  #卸载网床
    G28                             #归零3轴
    M109 S{EXTRUDER_TEMP}           #等待挤出机至打印温度
    M190 S{BED_TEMP}                #等待热床至打印温度
    Z_TILT_ADJUST                   #2Z轴调平
    WIPE_NOZZLE                     #擦拭喷嘴
    G28 Z                           #归零Z轴
    G90                             #所有轴使用绝对定位
    M83                             #挤出机使用相对定位
    M109 S{EXTRUDER_TEMP}           #等待挤出机至打印温度
#   G92 E0                          #重置挤出机
    G1 Y10 F3000
    BED_MESH_PROFILE LOAD=FZ_CC     #加载网床
```
