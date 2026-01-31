# Hardware Specs

## Architecture overview

- Antenna bank with switching or parallel RF chains.
- RF front-end modules (TBD) feeding ADCs or module outputs.
- Central MCU for orchestration, UI, and data logging.
- Display subsystem (TBD type/size).
- Power subsystem for battery + USB.

## RF front-end (TBD)

- Frequency range: TBD
- Noise figure: TBD
- Dynamic range: TBD
- IF chain or direct sampling: TBD
- Gain control: TBD

## MCU and compute

- MCU family: STM32F7 (initial platform: STM32F746G-DISCO)
- RAM/Flash requirements: TBD
- Peripheral needs: SPI/I2C/USB/UART/ADC/DMA, etc.

## Display and UI

- Display size: 3-4 inches
- Resolution: 480x320 (or similar)
- Interface: SPI or parallel
- MCU compatibility: STM32F7 or STM32H7
- Initial approach: start with a dev kit that includes the display.
- Input method (priority order, TBD):
  - Touch screen + a couple of physical buttons
  - 4-8 physical buttons
  - Couple of buttons + rotational encoder

## Storage

- Local storage: microSD or internal flash (TBD)
- File system: TBD

## Power

- Battery type/capacity: LiPo (capacity TBD)
- External power: USB power bank or external device supported
- Battery size limit: up to 75x100 mm
- Battery weight limit: up to 400 g
- Charging IC: TBD
- Typical current draw: TBD
- Power modes: active/idle/sleep

## Mechanical

- Enclosure: TBD
- Antenna connectors: TBD
- Thermal considerations: TBD
