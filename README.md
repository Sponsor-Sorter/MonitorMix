# SoundSpan

One PC. Every speaker.

SoundSpan (formerly MonitorMix) routes Windows audio to multiple playback devices, with listening presets, output timing correction, bass boost and a live visualizer.

## Download

[Download the current Windows x64 release](https://github.com/Sponsor-Sorter/MonitorMix/releases/latest)

Extract the whole ZIP, then run MonitorMix.exe. The published build still uses the MonitorMix name; SoundSpan branding is in development.

This repository contains downloads and documentation only. Application source is private.

## Current limits

Windows playback endpoints are supported through shared audio streams. Direct network casting is not yet available. Hardware support and acoustic timing vary by device; Bluetooth and network audio can add substantial delay. The tested Acer setup uses a 95 ms software buffer plus device processing. The executable is unsigned.
