# Zigbee Coordinator Firmware for Ebyte E72-2G4M20S1E module (cc2652p chip)

## Firmware description:

Based on [Koenkk](https://github.com/Koenkk/Z-Stack-firmware/blob/master/coordinator/Z-Stack_3.x.0/firmware.patch) patches for Z-Stack_3.x.0.

SDK 4.40.00.44

Changes according E72-2G4M20S1E datasheet:
- DIO5 and DIO6 controls RF switch
- DC/DC converter enabled
- SET_CCFG_MODE_CONF_XOSC_CAPARRAY_DELTA set to 0xFA (from E79-900DM2005S datasheet, but without it oscilator settings not related to hardware)

Built for CC2652P1F chip variant (not for CC1352P1F).

Default TX power: 20dBm. Power can be adjusted in zigbee2mqtt config:

    experimental:
      transmit_power: 5

Available TX power values: -20, -18, -15, -12, -10, -9, -6, -5, -3, 0, 1..5, 14..20

LEDs description:
- Green (DIO8) turns ON when High-power PA is not used (TX power from -20 to 5 dBm)
- Red (DIO7) turns ON when High-power PA is used (TX power from 15 to 20 dBm)
- LEDs on DIO9 and DIO10 also supported in source code, but currently not used and perhaps never will be.

Leds CAN NOT be turned OFF by zigbee2mqtt config - sorry, I still haven't skills for it.

Buttons description:
- Button 1 (BTN1) on DIO14 supported in source code, but currently not used and perhaps never will be.
- Button 2 (BTN2, Flash) on DIO15 - used for bootloader activation (for firmware update)
- Reset button - you guess what it do.

NOTES:

Coordinator backup from 2538/2652/1352 can be loaded back into another 2538/2652/1352, but into CLEAN (never used with zigbee2mqtt) chip only.
You can clear chip with zigbee2mqtt script scripts\zStackEraseAllNvMem.js

FIRMWARE SOURCES:

As I know, sharing source codes prohibited by TI, so there is no sources here. And I can't made patches because they will include code. But you now what to do ;)
