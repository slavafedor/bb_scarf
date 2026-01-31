# Firmware Specs

## Firmware architecture

- RF control layer: configure RF modules, gain, sweep params.
- Data acquisition: sampling, buffering, DMA management.
- Signal processing: FFT, smoothing, peak detect (CMSIS-DSP).
- UI layer: render spectrum, markers, menus.
- Storage: logging and playback (TBD format).
- Comms: USB serial or CDC (TBD).
- System scope (v0.1): single-MCU, standalone firmware; host app planned later for data visualization and device configuration via a device API.
- RTOS: use an ST-recommended RTOS to keep hardware flexibility during R&D (e.g., STM32Cube/FreeRTOS).
- UI tech: use TouchGFX if it is fast enough and supports updates from a designated buffer; otherwise fallback to custom framebuffer (TBD).

## RTOS task map (v0.1, initial)

- Task_RFControl (prio: high): tune SDR, set gain, manage sweep parameters; consumes sweep commands.
- Task_Acquire (prio: high): start ADC/DMA capture, manage double buffers, timestamp captures.
- Task_DSP (prio: high): run FFT + bucket aggregation (CMSIS-DSP) and publish spectrum frames.
- Task_UI (prio: medium): render spectrum/waterfall and update display (TouchGFX or framebuffer).
- Task_Storage (prio: low): write raw + bucket data to SD/flash; handle log rotation.
- Task_Comms (prio: low): USB CDC/API handling; disabled if API not enabled.
- Task_Config (prio: low): load/validate app.config, watch for config changes on SD.
- Task_Watchdog (prio: low): system health and watchdog kick.

## RTOS data flow (v0.1, initial)

- RFControl -> Acquire: queue of tune commands and gain settings.
- Acquire -> DSP: ring buffer or queue of capture blocks.
- DSP -> UI: shared frame buffer (double buffered).
- DSP -> Storage: queue of raw blocks + bucket summaries.
- Config -> All: shared config struct with versioning; updates via event flags.

## Core features (v0.1)

- Configurable sweep range and step size.
- Live spectrum display with peak hold.
- Basic detection thresholding.
- Snapshot logging to storage.
- UI views for v0.1:
  - Three spectrum views with corresponding waterfall views.
  - List of top 3 frequency bands/buckets per range.

## Initial performance targets (v0.1)

- Sweep time: under 1 second per band.
- Bands 300-900 MHz and 900 MHz-1.8 GHz may share one RF module; combined sweep within 2 seconds.
- FFT size: 128 per band (initial baseline).
- Bucket averaging: N=32 tuned frequencies per bucket.
- DMA captures: 8 captures per tuned frequency, averaged.
- Timing-derived ADC constraint (based on 1 s per band target):
  - Total tune points per band: 128 * 32 = 4096
  - Time per tune point: ~244.1 us
  - Time per DMA capture (8 per tune): ~30.5 us
  - ADC sample rate required for 1-10 samples per DMA capture: ~33 kS/s to ~330 kS/s (add margin as needed).

## Performance targets (TBD)

- Sweep rate
- UI refresh rate
- Memory headroom

## Data logging

- Data products: store both raw captures and aggregated bucket power (for future API use).
- Storage target:
  - Primary: microSD if present.
  - Fallback: internal flash, log only Fail and Error levels.
- Format: binary, CSV, or JSON, configurable via app.config (JSON-based).
- app.config location: stored on microSD and internal flash; if microSD is missing or app.config not found, use the internal flash default.
- Metadata: sweep params, timestamp, device config

## Configuration (app.config)

- JSON-based file; draft schema and example in `docs/app_config.md`.

## Update mechanism

- USB DFU or bootloader (TBD)

## Future (v0.2+)

- RF signature recognition (inference only)
- Cross-band correlation
- On-device signal classifiers
