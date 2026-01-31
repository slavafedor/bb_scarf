# Project Structure

## Current

- `README.md` - project overview and pointers
- `docs/` - requirements, specs, plans, and decisions
- `config/` - default configuration files
  - `config/app.config` - default device configuration (mirrors `/config/app.config` on device)
- `firmware/` - MCU firmware source (RTOS-based)
  - `firmware/app/` - application logic and system state
  - `firmware/bsp/` - board support package (STM32F746G-DISCO)
  - `firmware/drivers/` - peripheral drivers and HAL wrappers
  - `firmware/rtos/` - RTOS integration and tasks
  - `firmware/middleware/` - third-party middleware (USB, FS, etc.)
  - `firmware/services/` - logging, config, scheduling helpers
  - `firmware/ui/` - UI rendering and screens
  - `firmware/dsp/` - signal processing and FFT pipeline
  - `firmware/comms/` - device communications and APIs
  - `firmware/storage/` - file system and data logging
  - `firmware/config/` - config loading and defaults
  - `firmware/tests/` - unit tests and stubs
  - `firmware/cubemx/` - single STM32CubeMX project; hardware changes tracked via CubeMX config updates
- `hardware/` - electrical/mechanical design
  - `hardware/schematics/`
  - `hardware/pcb/`
  - `hardware/bom/`
  - `hardware/mechanical/`
- `tools/` - scripts and utilities
- `assets/` - images, UI assets, and misc files

## Planned (TBD)

None (moved to Current).
