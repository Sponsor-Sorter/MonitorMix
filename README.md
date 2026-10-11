# SoundSpan 0.5.0

One PC. Every speaker. Portable Windows x64 release candidate.

[Download SoundSpan for Windows x64](https://github.com/Sponsor-Sorter/SoundSpan/releases/latest).

Extract the entire ZIP and run SoundSpan.exe. Select your speakers, choose a listening preset, then click Fast setup or Start audio. Advanced settings contains source selection, channel placement, timing, microphone calibration and optional paused Windows startup. Click a screen preview to open its assigned speaker settings. Mouse Back returns to simple speaker view. Keep in tray continues audio and pauses visualization; Exit restores Windows output choices and closes the app.

Classic waveform shows the blue full mix, gold bass, purple mids and mint treble. These readings do not change sound. Bass boost uses digital headroom protection; a physical speaker can still distort when driven too loudly.

Settings, logs and recovery information are in %LOCALAPPDATA%\MonitorSound. Updates retain your source, speaker selections, positions, volume and calibration. Music, Gaming and Movies presets preserve those installation settings.

## Timing limits

Fast selects the smallest buffer supported by the current engine's safety policy. On the tested Acer pair this is 95 ms, plus device processing and any configured speaker delay. The displayed buffer and clock measurements are software values, not acoustic or end-to-end latency measurements. This is not a zero-latency or competitively low-latency gaming release.

The source must be separate from copied outputs to avoid feedback and direct unsynchronized playback. True discrete surround requires a multichannel source; the tested Realtek Digital source is stereo. Identical monitor names require user screen assignment or speaker testing. Optional microphone calibration measures relative delays; it does not remove the hardware latency.

## Reliability and release status

Audio uses shared WASAPI playback timing and automatic clock correction. Device loss or sleep pauses playback safely; reopen and start again after checking outputs. Windows defaults are restored on normal stop/exit and recovered after an abnormal exit on the next launch. This uses a Windows PolicyConfig adapter, which must be validated on each supported Windows version.

This candidate ships its .NET 10 runtime, requires no administrator privileges and installs no driver. Signal/UI, silent hardware routing, restart and Windows-default restoration reports are bundled in Verification. Archive contents are checked against manifest.json. The executable is not Authenticode signed. Physical unplug/sleep, other PCs/DPI configurations, microphone calibration and game/movie acoustic latency still require manual acceptance before a broad production release. Automated tests cannot guarantee there are no bugs.

## Audio outputs
Supports active Windows shared-mode PCM playback devices across manufacturers: monitor/TV speakers, analog speakers/headphones, USB outputs, headsets and virtual devices. Mono outputs are handled explicitly. See [COMPATIBILITY.md](COMPATIBILITY.md) for verified devices, Bluetooth delay, source requirements, multichannel and ASIO limitations.

## Source and support

This public repository contains downloads and documentation only. Application source is private. Report problems through the repository Issues page.
