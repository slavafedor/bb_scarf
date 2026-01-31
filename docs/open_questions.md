# Open Questions / Decisions

## Decisions (v0.1)

- Bands: 300-900 MHz, 900 MHz-1.8 GHz, 2.8-4.08 GHz, 4.8-6.06 GHz.
- Sweep target: under 1 second per band; combined 300-900 MHz + 900 MHz-1.8 GHz within 2 seconds.
- FFT size baseline: 128 per band.
- Bucket averaging: N=32 tuned frequencies per bucket; 8 DMA captures per tuned frequency.
- Display: 3-4 inches, 480x320 (or similar), SPI or parallel; start with a dev kit that includes the display.
- UI: three spectrum views + three waterfalls; list of top 3 frequency bands/buckets per range.
- Battery: 8 hours target; LiPo with USB/external power support; size up to 75x100 mm, weight up to 400 g.

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
