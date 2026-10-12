# SoundSpan 0.6.8

Enable **All apps → all selected speakers** on Studio to share existing and newly opened apps across your selected outputs. While enabled and playing, saved per-screen assignments are paused. Turn it off to restore screen routing. Some players require playback restarted after switching output.

One PC. Every speaker. Portable Windows x64 app.

Extract the entire ZIP and run SoundSpan.exe. Select your speakers, choose a listening preset, then click Fast setup & play. If sound is missing or quiet, click Check sound. It shows Windows levels separately from app gain and offers Stereo repair & restart without changing your measured delays. Source volume and mute remain adjustable. Below 50%, a warning appears once per app launch; dismissing it keeps your chosen volume.

Studio is the simple listening dashboard. Speakers opens the detailed routing and speaker settings; the active tab is highlighted. Fast setup & play chooses an unused source, enables Windows routing, configures the selected speakers and starts audio. It preserves volume, positions and measured delays.

Advanced settings contains source selection, channel placement, timing, microphone calibration and optional paused Windows startup. Click a screen preview to open its assigned speaker settings. Mouse Back returns to simple speaker view. Keep in tray continues audio and pauses visualization; Exit restores Windows output choices and closes the app.

Classic waveform shows the blue full mix, gold bass, purple mids and mint treble. These readings do not change sound. Bass boost uses digital headroom protection; a physical speaker can still distort when driven too loudly.

Settings, logs and recovery information are in %LOCALAPPDATA%\MonitorSound. Updates retain your source, speaker selections, positions, volume and calibration. Music, Gaming and Movies presets preserve those installation settings.

## Bluetooth device preview

Connected Bluetooth devices appear beneath the monitors in Studio and App routing, with matching blue icons. SoundSpan uses the device-reported type for speakers, headsets, phones, tablets and computers. Unknown types use a Bluetooth icon. Click a device with an available audio output to open its speaker settings. Phones and tablets do not automatically become speakers; SoundSpan explains when Windows exposes no audio output.

Disconnected devices leave the preview automatically. Connection checks run in the background without discovery inquiries and pause while the app is hidden or minimized. Extra devices scroll horizontally; small Studio windows scroll vertically to keep the controls accessible. Monitor proportions are preserved.

## App routing

Open App routing and click a screen in the monitor map. Choose its speaker, choose an open app, then Add app. Repeat for each screen. Assignments are saved and reapplied when apps reopen. Remove app restores the previous Windows preference; reopen a closed app before removing its Windows preference.

With Automatically route open apps to the screen they’re on checked, SoundSpan discovers open apps itself and follows their windows between mapped screens. Separate app assignments or approvals are not required. Uncheck it to use saved manual assignments; moving a window then leaves its output unchanged. Leave SoundSpan running in the tray for automatic following. Match each screen to a speaker once, particularly when identical monitor names make automatic matching ambiguous.

Windows routes an application as a whole. Browser tabs and multiple windows of the same browser generally share one audio destination. Following prefers an app’s foreground window and otherwise uses its topmost visible window. Minimized windows retain their last assignment. Protected apps, apps using exclusive/ASIO output, apps that select their own device and some Store applications may not accept a Windows preference. If an app has not opened an audio session yet, its assignment waits until it does.

These are direct Windows output preferences and add no SoundSpan copy buffer. Direct routes bypass SoundSpan bass processing and the shared-source visualizer. Each destination retains its own Windows volume. Windows and the player determine whether a running stream changes immediately or briefly stops; some players require playback or the app to restart. Zero interruption is not guaranteed. The per-app policy adapter was verified on Windows 10 build 19045; other Windows builds and real player switching require further acceptance testing. Store app version/path changes may require reassignment.

Double-click the visualizer to fill the app window. Double-click again or press Escape to restore the frame. Studio’s enlarged screen preview retains the real display proportions and placement.

## Timing limits

Fast selects the smallest buffer supported by the current engine's safety policy. On the tested Acer pair this is 95 ms, plus device processing and any configured speaker delay. The displayed buffer and clock measurements are software values, not acoustic or end-to-end latency measurements. This is not a zero-latency or competitively low-latency gaming release.

The source must be separate from copied outputs to avoid feedback and direct unsynchronized playback. True discrete surround requires a multichannel source; the tested Realtek Digital source is stereo. Identical monitor names require user screen assignment or speaker testing. Optional microphone calibration measures relative delays; it does not remove the hardware latency.

## Reliability and release status

Audio uses shared WASAPI playback timing and automatic clock correction. Device loss or sleep pauses playback safely; reopen and start again after checking outputs. Windows defaults are restored on normal stop/exit and recovered after an abnormal exit on the next launch. This uses a Windows PolicyConfig adapter, which must be validated on each supported Windows version.

This candidate ships its .NET 10 runtime, requires no administrator privileges and installs no driver. Signal/UI, silent hardware routing, restart and Windows-default restoration reports are bundled in Verification. Archive contents are checked against manifest.json. The executable is not Authenticode signed. Physical unplug/sleep, other PCs/DPI configurations, microphone calibration and game/movie acoustic latency still require manual acceptance before a broad production release. Automated tests cannot guarantee there are no bugs.

## Audio outputs
Supports active Windows shared-mode PCM playback devices across manufacturers: monitor/TV speakers, analog speakers/headphones, USB outputs, headsets and virtual devices. Mono outputs are handled explicitly. See [COMPATIBILITY.md](COMPATIBILITY.md) for verified devices, Bluetooth delay, source requirements, multichannel and ASIO limitations.





Updates: automatic GitHub updates are on by default and check every three days. Open Updates from Speakers or the tray menu to turn them off or check now. Downloads are checksum-verified; installation briefly restarts the app, preserves settings and rolls back a failed install. A writable app folder is required.

Screen dropdowns show the current screen resolution, with existing assignments preserved. Studio monitor previews retain their proportions in a smaller frame.



Remove app releases its saved Windows destination and excludes it from automatic following. Add app includes it again. If the app is closed or has no audio session, release completes when it next plays audio.
