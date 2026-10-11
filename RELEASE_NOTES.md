# MonitorMix 0.4.4 release notes

- Explicit mono-output support: stereo is averaged into the device's single channel with bounded gain.
- Mono loopback sources retain their channel count, including the silent keep-alive stream.
- Fast setup recognizes digital outputs from any manufacturer and falls back to another available Windows playback device.
- Device guidance covers speakers, headsets and interfaces as well as monitors.
- Sources with more than eight channels are rejected clearly instead of silently truncating their layout.
- All 0.4.3 reliability fixes, protected bass boost, presets, tray mode and screen shortcuts remain.

Extract the whole ZIP and run MonitorMix.exe. Existing speaker calibration and settings are preserved. Read COMPATIBILITY.md for device support and limitations.

Known limits: Windows shared-mode PCM playback is supported; ASIO-only outputs and exclusive-mode-only devices are not. Bluetooth/wireless devices add transport delay and may change playback profiles when a microphone is enabled. This is not a guarantee for every model. The tested Acer pair uses a 95 ms software timing buffer plus device processing and configured delays. The executable is unsigned. Physical testing of USB/Bluetooth/mono hardware and additional PCs remains outstanding.

Optical/TOSLINK/S/PDIF PCM and Bluetooth/Wi-Fi outputs follow the Windows playback-endpoint path. Direct DLNA/AirPlay/Chromecast/Sonos casting is not implemented in this release.
