# Blue Pill UAVCAN Node Example

skyyu.zhang's example code from https://github.com/skyyuzhang/UAVCAN_NODE_FreeRTOS
reshaped as a PlatformIO [STM32Cube](https://docs.platformio.org/en/latest/frameworks/stm32cube.html)
project.

keywords: STM32F103C8, CAN bus, [UAVCAN](https://uavcan.org), [libcanard](https://github.com/UAVCAN/libcanard), PlatformIO, STM32Cube, FreeRTOS

## Hardware

- tested on [STM32F103C8 ("Blue Pill")](https://wiki.stm32duino.com/index.php?title=Blue_Pill)
- CAN RX: pin A11
- CAN TX: pin A12
- bus speed: 250kbaud (you can change `CAN_SPEED` in `uavcan.h`)

## Usage

Build and upload using PlatformIO as usual.

After connecting to your PC's CAN bus hardware, you should see new
UAVCAN node named `skyyu.node.demo` with id 50 in 
[UAVCAN GUI Tool](https://uavcan.org/GUI_Tool/Overview/).

## Bugs

The code uses original skyyu.zhang's FreeRTOS version because there's no
FreeRTOS for `stm32cube` platform in PlatformIO. I have placed it in 
`lib/FreeRTOS-stm32cube` directory for better reuse but 
`FreeRTOSConfig.h` is placed here too which is not a good solution.
I could probably use some includedir black magic but it would not be much
better solution IMHO...
