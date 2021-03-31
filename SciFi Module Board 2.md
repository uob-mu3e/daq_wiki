# SciFi Module Board 2

Also known as DPNC414_03A. For reference, see also the [Mu3e Wiki Page](https://www.physi.uni-heidelberg.de/Forschung/he/mu3e/wiki/index.php/MuTRiG_and_STiC_Documents#SciFi_Module_Board_2_.28DPNC414_03A.29).

## Description
The board contains four MuTRiG v2 chips, a 128-channel SiPM array, two [Si53306](https://www.silabs.com/timing/buffers/any-format-clock-buffers/device.si53306-b-gm) clock chips, and voltage regulators for 3.3 V and 1.8 V.

## Inputs
* HV connection (TPHV), typically 58 V
* +5 V, typically works with 3.5 V (input for the 3.3 V LDO),  5.5 V maximum
* +2.5V, typically works with 2.0 V (for 1.8 V LDOs), 6 V maximum

## Outputs
* One QSH-030 connector with all relevant signals

## Cooling
The board must be actively cooled if one wants to avoid the risk of overheating. 

## Todo
* typical currents
* Configuration