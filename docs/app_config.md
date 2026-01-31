# app.config (JSON)

Configuration file used by the device at boot and runtime.

## Location and precedence

- Repo default: `config/app.config`.
- Device path: `/config/app.config` (on both microSD and internal flash).
- If microSD is missing or app.config is not found on microSD, use the internal flash default.

## Schema (draft)

```json
{
  "version": 1,
  "device": {
    "name": "BB-ScaRF",
    "hw_rev": "A",
    "serial": "TBD"
  },
  "logging": {
    "level": "INFO",
    "format": "binary",
    "target": "auto",
    "fallback_internal_levels": ["ERROR", "FAIL"],
    "file_prefix": "scan",
    "max_file_mb": 32,
    "flush_interval_s": 2
  },
  "scan": {
    "bucket_count": 128,
    "tuned_freq_per_bucket": 32,
    "dma_captures_per_tune": 8,
    "sweep_target_s_per_band": 1.0,
    "sdr_settle_time_us": 5,
    "bands_mhz": [
      {"name": "A", "start": 300, "end": 900},
      {"name": "B", "start": 900, "end": 1800},
      {"name": "C", "start": 2800, "end": 4080},
      {"name": "D", "start": 4800, "end": 6060}
    ]
  },
  "rf": {
    "gain_mode": "auto",
    "gain_db": 0,
    "lna_enable": true,
    "attenuator_db": 0,
    "antenna_select": "auto"
  },
  "dsp": {
    "fft_size": 128,
    "window": "hann",
    "smoothing_alpha": 0.2,
    "peak_hold": true,
    "detect_threshold_db": -60
  },
  "ui": {
    "enable_waterfall": true,
    "top_bands_per_range": 3,
    "refresh_hz": 20,
    "brightness_pct": 70,
    "show_units": true
  },
  "storage": {
    "prefer_micro_sd": true,
    "log_dir": "/logs",
    "data_dir": "/data",
    "raw_dir": "/raw"
  },
  "comms": {
    "usb_cdc_enable": true,
    "api_enable": false,
    "api_baud": 115200
  },
  "power": {
    "backlight_timeout_s": 120,
    "auto_sleep_s": 0
  },
  "calibration": {
    "enabled": false,
    "offset_db": 0
  }
}
```

## Notes

- `logging.level` values: `DEBUG`, `INFO`, `WARN`, `ERROR`, `FAIL`.
- `logging.format` values: `binary`, `csv`, `json`.
- `logging.target`: `auto` means microSD if present; otherwise internal flash.
- `scan.*` values are aligned with v0.1 defaults; may be tuned during R&D.
- `rf.gain_mode` values: `auto`, `manual`.
- `rf.antenna_select` values: `auto` or a specific antenna ID (TBD).
- `dsp.window` values: `hann`, `hamming`, `rect` (TBD).
- `comms.api_enable`: host API planned for later phase.
