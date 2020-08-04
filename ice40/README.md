#### milliLearn iCE40

milliLearn/iCE40 is an FPGA dev board focused at ultra low-power machine learning research. As a platform itself, it's not meant to be deployed, but is instead meant for benchtop power and performance metering.

The files in the pcb-ng directory are a smaller version of the board that might be less convenient to work with - it saves space at the expense of having limited header pins and no swappable memory modules.


Circuit checklist:
 - [x] 3.3v, 1.8v linear regulators
 - [x] USB port
 - [x] Selectable Vddios
 - [x] FT232H for programming configuration flash
 - [x] iCE40 FPGA
 - [x] configuration flash
 - [x] uart connection from iCE40
 - [x] Connector for [Sparkfun-produced hm01b0 image sensor](https://www.sparkfun.com/products/15570)
 - [x] Modular memory footprints
   - [x] 0.1" header modular pins
      - [x] Swap modules easily
      - [x] Program modules easily
   - [x] 4 spaces for memory chips in total (excluding configuration flash)
   - [x] Choose between the follwing parts, which are all footprint compatible
      - [x] SPI FRAM
      - [x] QSPI Flash
      - [ ] SRAM
 - [x] Current sense amps with header pins for monitoring output voltage
 - [x] Seperate power consumption monitoring for
   - [x] Each memory chip
   - [x] Each sensor
   - [x] FPGA
      - [x] Vddcore + Vddpll
      - [x] Vccio{0, 1, 2}
 - [x] i2s microphone(s)   SPH0645LM4H-B
 - [x] Sparkfun qwiic connect compatible connector
 - [x] All i/os broken out for debug
 - [x] oscillator
 - [x] a couple LEDs, a couple buttons (could re-use config flash pins, hm01b0_int, hm01b0_trig, or ice40_gpio)

Future featues:
 - [ ] Onboard mcu for measuring power in firmware and reporting over UART


random notes:

###### Config memory read speed

When using iceprog, the config flash memory is written by the ft232hq at 6MHz.
The iCE40 starts by reading the config flash at about 12MHz. This is the default read frequency. There are options to put a "speed up the read" near the beginning of the bitstream (refer to Lattice Technical Note 1248: "iCE40 Programming and Configuration")
