# Zigbee Coordinator Firmware for Ebyte E72-2G4M20S1E module (cc2652p chip)

## Firmware description

Based on [Koenkk](https://github.com/Koenkk/Z-Stack-firmware/blob/master/coordinator/Z-Stack_3.x.0/firmware.patch) and [JetHome](https://github.com/jethome-ru/zigbee-firmware/tree/master/ti/coordinator/cc2652) patches for Z-Stack_3.x.0.

### Changes from original firmware
- Default TX power: 20dBm.
- Extended LEDs support
- DC/DC and VDDR enabled for high power TX
- HF XOSC CAPARRAY disabled (not needed for this module)

### TX power ajust

Power can be adjusted in zigbee2mqtt config:

    experimental:
      transmit_power: 5

Available TX power values: -20, -18, -15, -12, -10, -9, -6, -5, -3, 0, 1..20

### LEDs description
- Green (DIO8) turns OFF when the network is running, blinking when joining enable
- Red (DIO7) flashed when APS frame received
- When stick restarted - both double blinking (depends on zigbee-heardsman status and **disable_led** configuration)

Leds can be turned OFF/ON by zigbee2mqtt config.

### Buttons description
- Flash button on DIO15 used for bootloader activation (for firmware update)
- Reset button - you guess what it do.

### Notes

Strongly recommended to clear the memory after flashing (look about it on [Flashing page](https://github.com/egony/cc2652p_E72-2G4M20S1E/wiki/Flashing)).

---

## Changelog

### 2026-01-03

- SDK 8.32.00.07
- Green LED mode changed to OFF when joining disabled
- DCDC and VDDR enabled
- HF XOSC CAPARRAY disabled
  
### 2022-03-01

- SDK 5.40.00.40

### 2022-02-17

- Built for CC1352P1F chip variant due to compiling for CC2652P1F chip variant produce same code now.
- LEDs on DIO9 and DIO10, Button 1 (BTN1) on DIO14 removed from source code.
- LEDs support code now copy-pasted from [JetHome patches](https://github.com/jethome-ru/zigbee-firmware/tree/master/ti/coordinator/cc2652) for code compatibility and easy maintenance. But...
- Hard reset (or unplug-plug) not required now when changing **disable_led** false -> true in configuration (restart z2m still required).

### 2021-09-01

- SDK 5.20.00.52

### 2021-08-12

- SDK 5.10.00.48

### 2021-03-19

- LEDs now shows some events - reboot, network startup, join, data recieved
- LEDs now can be turned OFF by zigbee2mqtt config (require modifyed file zStackAdapter.js)

### 2021-02-11

- SDK 4.40.04.04

### 2020-09-21

- Initial release.
- SDK 4.20.01.04
- DIO5 and DIO6 controls RF switch
- DC/DC converter enabled
- SET_CCFG_MODE_CONF_XOSC_CAPARRAY_DELTA set to 0xFA
- Built for CC2652P1F chip variant (not for CC1352P1F).
- Default TX power: 20dBm. Power can be adjusted in zigbee2mqtt config (-20...20)
- LEDs are supported: Red (DIO7) - PA used, Green (DIO8) - PA not used
- LEDs can't be turned OFF
