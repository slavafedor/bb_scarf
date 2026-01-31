# Requirements

## Functional

- RF scanning across defined bands:
  - 300-900 MHz
  - 900 MHz-1.8 GHz
  - 2.8-4.08 GHz
  - 4.8-6.06 GHz
- Each band represented by 128 buckets; each bucket averages N=32 tuned frequencies.
- Per tuned frequency, average 8 DMA captures.
- Multi-antenna input selection or simultaneous capture (TBD).
- Parallel RF modules (TBD count) coordinated by MCU.
- Real-time visualization of power vs frequency (spectrum view).
- Peak hold and averaging options.
- Signal detection thresholds and markers.
- Data logging to local storage (TBD format).
- USB for power and data transfer.

## Non-functional

- Handheld form factor with battery operation.
- Boot to scan-ready within acceptable time (TBD).
- Sweep latency and refresh rate suitable for field usage.
- Target sweep time: under 1 second per band; combined 300-900 MHz + 900 MHz-1.8 GHz within 2 seconds.
- Battery life target: 8 hours of operation.
- EMI/EMC consideration for internal electronics.
- Modular firmware for future ML/AI pipeline integration.

## Regulatory/Compliance (future)

- RF emission limits for internal oscillators or spurs (TBD).
- Battery safety and charging standards (TBD).

## Assumptions

- v0.1 prioritizes scanning and visualization over classification.
- Calibration will be coarse for v0.1.
