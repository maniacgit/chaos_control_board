#Chaos Control Board

This will be a control board for 3D printers using 32 bit and the TMC2130 stpper driver.

## features
* 32 bit
* TMC2130 stepper driver
* Marlin firmware
* Teensy 3.6 based
* 12V - at least 24V (the limiting factors are stepper driver, hotend, heatbed)
* SPI for the stepper driver is routed directly on the board
* enable and direction over SPI (needs Marlin patch)
* steps over SPI?
* sensorless homing, no x/y endstops needed. diag1 of the TMC2130 will be directly routed to the endstop pins of the controller
* Raspberry Pi Zero W connected to a pin header on the board with power and rx/tx
* step down for 5V and 12V
* 3 pwm controlled fans, each fan can be jumpered to use vcc, 12V or 5V
* if possible THT design to make it easier to build one
* JST connectors
* 2 connectors for Z to drive two motors with the same driver
* onboard optocoupler for Z probe
* BL Touch support
* 5 stepper driver onboard, expansion header to support more


## open points
* heatbed mosfet onboard or only control connector to an external mosfet?

## possible future features
* ws2812 controlled LEDs (does Marlin supports this?)
* flash firmware using the Raspberry and Octoprint (needs modified bootloader on the Teensy to use rx1/tx1 instead of rx0/tx0 from the default usb connector)
* filament sensor using the sensor from an old optical mouse (does Marlin already supports this?)

## Teensy pinout planning
* 42 GPIO on the default pin headers (we should use them for all default features if possible)
* 20 more GPIO are accessible with smd pin header

### needed pins

#### SPI
* SDO
* SCK
* SDI

#### stepper driver
* X CS
* X Step
* Y CS
* Y Step
* Z CS
* Z Step
* E0 CS
* E0 Step
* E1 CS
* E1 Step

#### thermistor
* bed
* hotend 0
* hotend 1

#### fans
* part cooler
* fan 2
* fan 3

#### display
* 9?
* sd?

#### misc
* heatbed
* rpi tx
* rpi rx

