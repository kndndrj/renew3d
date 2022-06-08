# Renew3D
A simple, cheap and (hopefully) reliable 3D printer.

![render](images/render_banner.png)

###### What kind of name is this?
I built my first 3D printer a couple of years ago, but there was no assembly,
only parts from thingiverse, etc. Then I had an idea to make a new printer with
extra features, but the project became *waaay* to complicated (check it
[here](https://github.com/kndndrj/complicator-3000)). So this printer here, is
a "renewed" version of those two (quite bad, I know).

## Getting Started
The files for this printer are available in `.f3d`, `.step` and `.stl` formats.
If you want to assemble the printer, I suggest that you check
[`assembly.f3z`](cad/assembly.f3z) (alternatively `assembly.step`) first, and
check what materials to buy and what parts to print. Then look into the
[`printed_parts`](cad/printed_parts) directory and browse files in different
formats. If you have a sensor, board, hotend, etc. check the `extras`
directory.

## Firmware Uploading (Linux)
You can use any firmware you like, here is just my example config using Marlin
2.0.x for Ramps board with mega 2560.

1. Download Marlin Firmware [here](https://github.com/MarlinFirmware/Marlin).
2. Install platformio (example on Arch Linux):
	```sh
	$ paru -S platformio
	```
3. Go to the downloaded firmware directory and replace `Marlin/Configuration.h`
   and `Marlin/Configuration_adv.h` with files from [`firmware`](firmware) in
   this repository.
4. Plug in the printer and run:
	```sh
	$ platformio run --target upload -e mega2560
	```

#### Note on cheap Chinese boards
Try these steps (stop when you get it to work):
- Install `i2c-ch341-dkms` from AUR.
- Disable udev rules:
	```
	/usr/lib/udev/rules.d/90-brltty-device.rules
	/usr/lib/udev/rules.d/90-brltty-uinput.rules
	```
- Specify `upload_port = /dev/ttyUSB0` in `ini/avr.ini`

## Development

#### Specific Components
If you are creating a new specific part (like SKR 1.3), put it in the `extras`
directory. If it's made of multiple bodies, export the whole file as `.f3d` and
`.step`. Then export separate bodies (only printable parts) as `.stl`.

#### Main Assembly
For main assembly, use only the `assembly.f3z` when developing. then export the
modified printable parts in all formats and put them in `main_assembly`
directory.

####

## Credits

#### Standard Parts 3D Models:

**NOTE:** I'm not the owner of any of the following "standard" parts.

- [atx_power_supply](https://grabcad.com/library/atx-power-supply-1)
- [cooling_fan_4010](https://grabcad.com/library/40mm-dc-fan-1)
- [cooling_fan_radial_5015](https://grabcad.com/library/radial-cooling-5015-fan-50mm-dc12v-1/details?folder_id=2074285)
- [e3d_v6_hotend](https://grabcad.com/library/e3d-v6-hotend-1-75mm-bowden-1)
- [endstop_switch](https://grabcad.com/library/mechanical-endstop-module-1)
- [flex_coupler_5x8]()https://grabcad.com/library/flex-coupler-5mm-8mm-1
- [GT2_20T_motor](https://grabcad.com/library/timing-pulley-gt2-20-teeth-5mm-bore-2/details?folder_id=2369004)
- [GT2_20T_idler](https://grabcad.com/library/tension-pulley-gt2-20t-b5-1)
- [induction_sensor_m12](https://grabcad.com/library/lj12a3-4-z_bx-inductive-sensor-m12-1)
- [lead_screw_nut_t8](https://grabcad.com/library/tr8x8-4-8mm-4-start-lead-screw-nut-1)
- [lead_screw_t8_340](https://grabcad.com/library/tr8x8-4-8mm-4-start-lead-screw-1)
- [linear_bearing_LM8UU](https://grabcad.com/library/lm8uu-11)
- [nema_17_motor](https://grabcad.com/library/step-motor-nema-17-1)
- [ramps_14_arduino_mega_2560](https://grabcad.com/library/arduino-mega-ramps-1-4-1)
- [ramps_lcd_adapter](https://grabcad.com/library/smart-adapter-conector-lcd-ramps-1-4-1)
- [SSR_40_DA](https://grabcad.com/library/ssr-40-da-1)

#### Printed Parts:

- [part_cooling_fan_duct](https://www.thingiverse.com/thing:3063554) - changed only text
- [x_idler & x_motor_holder](https://www.thingiverse.com/thing:1103976) - fork
- [x_carriage & hotend_holder](https://www.thingiverse.com/thing:2023947) - fork
- [y_endstop_holder](https://www.thingiverse.com/thing:919432/files) - inspiration
