# Zigbee Coordinator Firmware for Ebyte E72-2G4M20S1E module (cc2652p chip)

## Firmware description:

Based on [Koenkk](https://github.com/Koenkk) patches for Z-Stack_3.x.0.

SDK 4.20.01.04

Built for CC2652P1F chip variant (not for CC1352P1F).

Changes according E72-2G4M20S1E datasheet:
- DIO5 and DIO6 controls RF switch
- DC/DC converter enabled
- SET_CCFG_MODE_CONF_XOSC_CAPARRAY_DELTA set to 0xFA (from E79-900DM2005S datasheet, without it oscilator settings not related to hardware)

Default TX power: 20dBm.

Can be adjusted in config zigbee2mqtt:

    experimental:
      transmit_power: 5

Available values: -20, -18, -15, -12, -10, -9, -6, -5, -3, 0, 1-5, 14-20

LEDs description:
- LED4 (Red) turns ON when High-power PA is not used (from -20 to 5 dBm)
- LED3 (Green) turns ON when High-power PA used (from 15 to 20 dBm)
- LED1,2 supported in source code, but currently not used.
- Leds can't be turned OFF by zigbee2mqtt config - sorry, I haven't skills for it.

Buttons description:
- Button 1 (BTN1) supported in source code, but not currently used
- Button 2 (BTN2, Flash) - used for bootloader activation (for firmware update)
- Reset button - you guess what it do.
