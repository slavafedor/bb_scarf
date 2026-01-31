# Open Questions / Decisions

## Decisions (v0.1)

- Bands: 300-900 MHz, 900 MHz-1.8 GHz, 2.8-4.08 GHz, 4.8-6.06 GHz.
- Sweep target: under 1 second per band; combined 300-900 MHz + 900 MHz-1.8 GHz within 2 seconds.
- FFT size baseline: 128 per band.
- Bucket averaging: N=32 tuned frequencies per bucket; 8 DMA captures per tuned frequency.
- Display: 3-4 inches, 480x320 (or similar), SPI or parallel; start with a dev kit that includes the display.
- UI: three spectrum views + three waterfalls; list of top 3 frequency bands/buckets per range.
- Battery: 8 hours target; LiPo with USB/external power support; size up to 75x100 mm, weight up to 400 g.
- System scope: v0.1 is single-MCU standalone firmware; host app planned later for visualization/config via device API.
- DSP library: CMSIS-DSP (best performance on STM32).
- Data products: store both raw captures and aggregated bucket power (for future API use).
- UI tech: TouchGFX if it supports fast updates from a designated buffer; otherwise custom framebuffer.
- Logging: microSD if present; fallback to internal flash with Fail/Error only. Log format (binary/CSV/JSON) configurable via JSON app.config.
- app.config location: stored on microSD and internal flash; if microSD missing or app.config absent on microSD, use internal flash default.

## Product

- What sweep resolution and refresh rate are required?
- What antenna types and connectors should we support?

## Hardware

- Which RF front-end module(s) are viable and available?
- ADC strategy: direct sampling vs IF chain?
- MCU selection and memory requirements?
- Display type and size?
- Battery capacity and charging method?

## Firmware

- DSP pipeline selection: FFT size/windowing?
- Data logging format and transfer method?
- Update mechanism (bootloader/DFU)?
- Validate timing math: confirm ADC sample rate and DMA capture size vs 1 s per band target.

## Operational

- Calibration approach and accuracy requirements?
- Safety/regulatory considerations for a handheld device?
