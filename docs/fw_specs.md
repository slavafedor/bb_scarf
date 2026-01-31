# Firmware Specs

## Firmware architecture

- RF control layer: configure RF modules, gain, sweep params.
- Data acquisition: sampling, buffering, DMA management.
- Signal processing: FFT, smoothing, peak detect (TBD).
- UI layer: render spectrum, markers, menus.
- Storage: logging and playback (TBD format).
- Comms: USB serial or CDC (TBD).

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

- Format: CSV or binary (TBD)
- Metadata: sweep params, timestamp, device config

## Update mechanism

- USB DFU or bootloader (TBD)

## Future (v0.2+)

- RF signature recognition (inference only)
- Cross-band correlation
- On-device signal classifiers
