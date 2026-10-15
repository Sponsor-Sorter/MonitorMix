# SoundSpan 0.6.11 release notes

- Improved Windows volume-session recovery when source or speaker sessions appear late, expire or disconnect. One unavailable output no longer prevents other outputs receiving volume and mute changes.
- Moved volume reconciliation out of Windows notification callbacks to avoid a potential lock/cleanup stall. Delayed notifications use current volume values instead of replaying stale ones.
- Fixed updater checks getting stuck after settings-save failures, and preserved retry scheduling when a completed check cannot be saved.
- Improved updater cancellation and shutdown handling, including pending HTTP requests.
- Prevented concurrent speaker timing updates from losing a larger buffer requirement. Automatic gap recovery now respects its 120 ms cap while preserving larger device requirements.
- Diagnostic reports now identify the actual running version. Shared-playback volume tooltips clarify that directly routed apps use their Windows app volume controls.

Verification: 17 offline volume/updater/timing checks pass in the portable build; Store policy and build checks also pass. The final ZIP is checked through the real updater extraction and manifest verifier without installing it. These checks do not open audio devices or validate audible sound.

Live audio, acoustic synchronization, physical Bluetooth/Wi-Fi hardware, other-PC compatibility and actual Store entitlement/certification were not retested for this release. No zero-latency or bug-free guarantee. Direct per-app routes retain Windows app volume controls. The Store edition remains a separate private candidate.


Offline endurance result: the production mixer-recovery code completed 68.1 minutes against simulated endpoints with 13039 recovery checkpoints, 2620839 notifications and 13039 simulated disconnects, with no test failure. Zero audio devices were opened; this does not validate native/audio hardware behavior. The attached offline-endurance JSON contains the final result.

## Previous release
# SoundSpan 0.6.8 release notes

- Connected Bluetooth devices now appear beneath the monitors in Studio and App routing, using matching blue icons for device-reported speakers, headsets, phones, tablets and computers.
- Click an audio-capable Bluetooth device to open its speaker settings. Devices without an available Windows audio output show an explanation.
- Unknown device types use a Bluetooth icon rather than guessing. Ready Bluetooth LE audio outputs can appear through their Windows device identity.
- Disconnected devices are removed automatically. Background connection checks do not start discovery inquiries and pause while hidden or minimized.
- Small Studio windows scroll to keep settings accessible; additional device tiles scroll horizontally. Monitor proportions, saved speaker choices, volume and calibration remain intact.

Physical Bluetooth pairing and device-type reporting remain unverified on this PC because no Bluetooth adapter is detected. Connected-only non-audio LE devices are not guaranteed to appear. A connected phone or tablet is not automatically an audio output.


Offline endurance result: the production mixer-recovery code completed 68.1 minutes against simulated endpoints with 13039 recovery checkpoints, 2620839 notifications and 13039 simulated disconnects, with no test failure. Zero audio devices were opened; this does not validate native/audio hardware behavior. The attached offline-endurance JSON contains the final result.

## Previous release
# SoundSpan 0.6.7 release notes

- Windows/keyboard master volume targets the shared source in All apps mode. SoundSpan repairs changed Windows default output roles without changing source volume.
- Fixed the source speaker-card slider: it now controls actual Windows source volume rather than an unused copy gain. Inapp copy delay/channel controls are disabled for the source.
- SoundSpan’s source-side Windows mixer volume and mute now control the audible copied output sessions, fixing a mixer slider that previously affected only a silent session.
- Old SoundSpan-specific Windows output preferences are cleared before reading system defaults, fixing masked default-output recovery and restoration.
- Add Bluetooth device opens a branded speaker/headset picker, requests Windows pairing, enables its audio service and adds the selected ready output to playback. Already paired devices can be selected. Windows Bluetooth settings is available for LE-only devices or Windows-managed setup.
- Stereo profiles are preferred; physical device identity is matched using container IDs, with a friendly-name fallback. Ambiguous outputs are not chosen automatically.
- Outputs can join, disconnect and rejoin the live timeline without restarting other speakers. Source-device disconnection still pauses copying until the source returns.
- Bluetooth pairing and profile switching were not physically tested: this test PC exposes no Bluetooth adapter. No instant pairing, universal device support, acoustic synchronization or zero latency guarantee. Bluetooth transport and decoder delays vary by device.

## Earlier changes
## SoundSpan 0.6.5

- New All apps → all selected speakers checkbox on Studio and App routing. While audio runs, existing and newly detected Windows audio apps are routed through the shared source, overriding per-screen assignments without deleting them. Turning it off restores per-screen routing.
- App preferences are checked again after player resets and mixer changes; helper processes without a routable audio identity no longer block other processes.
- Connecting or disconnecting unrelated audio devices no longer stops playback.
- Saved speakers and the source stay selected through disconnection. Playback waits for selected devices to reconnect and resumes; sleep/wake retains playback intent.
- Volumes, delays and the once-per-launch branded low-volume reminder are preserved.
- Some players with fixed output devices, exclusive audio or cached streams still need their playback restarted. Browser tabs usually share a browser output. Physical device reconnection and sleep/wake need user testing.

## Earlier changes
## SoundSpan 0.6.4

- Branded low-source-volume reminder with the SoundSpan logo, blue styling and a clear Got it button.

- Remove app works while automatic routing is enabled. Removed apps stay excluded until Add app is used again.
- Route removal handles apps with multiple helper processes and waits safely for closed apps to play again before releasing Windows preferences.

- Reverted forced capture-source volume: source volume and mute remain under your control.
- Check sound restores the source volume slider and mute control. Below 50%, a warning appears once per app launch and stays dismissed until restart.

- Default-on automatic updates every three days, with an Updates checkbox and manual check.
- Verified downloads, preserved settings and rollback on installation failure.
- Smaller proportional Studio monitor previews.
- Screen dropdowns show resolution instead of desktop coordinates; saved assignments retain their screen identity.



- New App routing tab: click a screen, match its speaker and save app assignments for the next time they open.
- Automatic routing discovers open applications without separate assignments and follows their windows between mapped screens. Unchecked uses saved manual assignments.
- Compact Studio monitor preview preserves each display’s proportions and arrangement.
- Double-click the visualizer to fill the app window; double-click again or press Escape to restore the layout.
- App routing integration checks cover automatic discovery, moving a window, manual mode, settings reload, application restart and preference restoration.
- Direct app routes use Windows preferences without adding SoundSpan’s copy buffer. Browser tabs share a browser destination; some players require a playback restart after switching.
- Fast setup & play configures this PC for the selected speakers and starts audio in one click.
- Studio opens the simple listening dashboard; Speakers opens detailed routing and speaker settings. The current tab is highlighted at every window size.
- Mirror stereo now sends both source channels to every selected speaker, even when saved per-speaker assignments were left/right or surround. Saved positions, levels and measured delays are preserved.
- Check sound shows Windows endpoint volumes, device mutes and SoundSpan's Windows mixer levels. The app's 100% speaker gain no longer hides a low Windows volume without guidance.
- Stereo repair & restart picks an unused source, enables Windows routing and restarts the selected speakers in stereo. It preserves speaker volume, screen assignment and delay.
- Live status distinguishes receiving audio from waiting for a song/video. An active audio stream alone is no longer presented as proof that sound is arriving.
- Mouse Back follows the window receiving the mouse message instead of relying on foreground activation timing.
- Release verification now includes a quiet non-silent signal check through source capture, app render sessions and Windows output loopback, in addition to timing tests.

Extract the entire ZIP and run SoundSpan.exe. Existing settings are retained. Click Start audio; if sound is missing or quiet, click Check sound. Use Open Windows mixer to inspect the source and speaker levels, or Stereo repair & restart to repair routing. Adjust speaker Windows volume and mute controls in Check sound. Source volume and mute controls are also adjustable; SoundSpan does not automatically raise volume or unmute devices.

Windows has separate capture-source, playback-device and per-app mixer volumes. Low source volume reduces every copied output; a warning below 50% is shown once per app launch. Players pinned to a specific output may need their output changed to Default and playback restarted.

Known limits: the tested Acer pair uses a 95 ms software buffer plus device processing and saved delays. Windows stream/loopback measurements do not prove physical audibility, acoustic synchronization or performance on every device. The executable is unsigned. Bluetooth/Wi-Fi Windows endpoints may add transport delay; direct DLNA/AirPlay/Chromecast/Sonos casting is not implemented. See COMPATIBILITY.md.
