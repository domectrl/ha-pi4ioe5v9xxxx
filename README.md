# pi4ioe5v9xxxx IO Expander

[![GitHub Release][releases-shield]][releases]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE)

[![hacs][hacsbadge]][hacs]
![Project Maintenance][maintenance-shield]

[![Discord][discord-shield]][discord]
[![Community Forum][forum-shield]][forum]

**Description.**
The `pi4ioe5v9xxxx` integration provides support for the quasi-bidirectional devices PI4IOE5V9570, PI4IOE5V9674, PI4IOE5V9673, PI4IOE5V96224 and PI4IOE5V96248 from digital.com.

For more details about the pi4ioe5v9xxxx I2C I/O port expander you can find the datasheets here:
- [PI4IOE5V9570](https://www.diodes.com/assets/Datasheets/PI4IOE5V9570.pdf)
- [PI4IOE5V9674](https://www.diodes.com/assets/Datasheets/PI4IOE5V9674.pdf)
- [PI4IOE5V9673](https://www.diodes.com/assets/Datasheets/PI4IOE5V9673.pdf)
- [PI4IOE5V96224](https://www.diodes.com/assets/Datasheets/PI4IOE5V96224.pdf)
- [PI4IOE5V96248](https://www.diodes.com/assets/Datasheets/PI4IOE5V96248.pdf)

**This integration can set up the following platforms.**

Platform | Description
-- | --
`binary_sensor` | Reads digital inputs from Digital.com I/O expanders. The pin numbers are from 1 to X where: 1-8 correspond to port 0 (00-07) and 9-16 to port 1, etc.
`switch` | Writes digital outputs from Digital.com IO expanders. The pin numbers are from 1 to X where: 1-8 correspond to port 0 (00-07) and 9-16 to port 1, etc.


## Installation

### HACS (Preferred)
1. [Add](http://homeassistant.local:8123/hacs/integrations) the custom integration repository: https://github.com/domectrl/ha-pi4ioe5v9xxxx
2. Select `PI4IOE5V9xxxx` in the Integration tab and click `download`
3. Restart Home Assistant
4. Done!

### Manual
1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
1. If you do not have a `custom_components` directory (folder) there, you need to create it.
1. In the `custom_components` directory (folder) create a new folder called `pi4ioe5v9xxxx`.
1. Download _all_ the files from the `custom_components//` directory (folder) in this repository.
1. Place the files you downloaded in the new directory (folder) you created.
1. Restart Home Assistant

## Configuration via user interface:
* Confuguration via user interface is not yet supported

## YAML Configuration

This integration can be configured and set up manually via YAML. To enable the integration binary_sensor or switch in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
binary_sensor:
- platform: pi4ioe5v9xxxx
  pins:
    1: Pin_01/PI0_0
    2: Pin_02/PI0_1
    3: Pin_03/PI0_2
    4: Pin_04/PI0_3
    5: Pin_05/PI0_4
    6: Pin_06/PI0_5
    7: Pin_07/PI0_6
    8: Pin_08/PI0_7

switch:
  - platform: pi4ioe5v9xxxx
    pins:
     9: Pin_09/PI1_0
     10: Pin_10/PI1_1
     11: Pin_11/PI1_2
     12: Pin_12/PI1_3
     13: Pin_13/PI1_4
     14: Pin_14/PI1_5
     15: Pin_15/PI1_6
     16: Pin_16/PI1_7
```

### Configuration parameters
- pins: List of used pins.
  > required: true | type: map
  - keys ("pin: name"): The pin numbers (from 1 to X) and corresponding names.
    > required: true | type: [integer, string]
- i2c_bus: i2c bus containing the pi4ioe5v9xxxx chip.
  > required: false | type: integer | default: "`1`"
- i2c_address: i2c address of pi4ioe5v9xxxx chip.
  > required: false | type: integer | default: "`0x20`"
- bits: number of bits of pi4ioe5v9xxxx chip, see particular datasheet for your device for the right number.
  > required: false | type: integer | default: "`24`"
- invert_logic: If `true`, inverts the output logic to ACTIVE LOW.
  > required: false | type: boolean | default: "`false` (ACTIVE HIGH)"


### Full configuration example

```yaml
binary_sensor:
- platform: pi4ioe5v9xxxx
  i2c_bus: 1
  i2c_address: 0x20
  bits: 16
  pins:
    1: Pin_01/PI0_0
    2: Pin_02/PI0_1
    3: Pin_03/PI0_2
    4: Pin_04/PI0_3
    5: Pin_05/PI0_4
    6: Pin_06/PI0_5
    7: Pin_07/PI0_6
    8: Pin_08/PI0_7

switch:
- platform: pi4ioe5v9xxxx
  i2c_bus: 1
  i2c_address: 0x20
  bits: 16
  pins:
    9: Pin_09/PI1_0
    10: Pin_10/PI1_1
    11: Pin_11/PI1_2
    12: Pin_12/PI1_3
    13: Pin_13/PI1_4
    14: Pin_14/PI1_5
    15: Pin_15/PI1_6
    16: Pin_16/PI1_7
```

## Contributions are welcome!

If you want to contribute to this please read the [Contribution guidelines](CONTRIBUTING.md)

***

[commits-shield]: https://img.shields.io/github/commit-activity/y/domectrl/ha-pi4ioe5v9xxxx.svg?style=for-the-badge
[commits]: https://github.com/domectrl/ha-pi4ioe5v9xxxx/commits/main
[hacs]: https://hacs.xyz/
[hacsbadge]: https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge
[discord]: https://discord.gg/Qa5fW2R
[discord-shield]: https://img.shields.io/discord/330944238910963714.svg?style=for-the-badge
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge
[forum]: https://community.home-assistant.io/
[license-shield]: https://img.shields.io/github/license/domectrl/ha-pi4ioe5v9xxxx.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-domectrl-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/domectrl/ha-pi4ioe5v9xxxx.svg?style=for-the-badge
[releases]: https://github.com/domectrl/ha-pi4ioe5v9xxxx/releases

