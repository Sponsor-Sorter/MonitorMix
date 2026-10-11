# SoundSpan 0.6.2 release notes

- Remove app works while automatic routing is enabled. Removed apps stay excluded until Add app is used again.
- Route removal handles apps with multiple helper processes and waits safely for closed apps to play again before releasing Windows preferences.

- Capture source loads at 100%, unmuted and is kept there during copied playback.
- Check sound shows its managed status without a source volume slider or mute control. Speaker settings remain adjustable.

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

Extract the entire ZIP and run SoundSpan.exe. Existing settings are retained. Click Start audio; if sound is missing or quiet, click Check sound. Use Open Windows mixer to inspect the source and speaker levels, or Stereo repair & restart to repair routing. Adjust speaker Windows volume and mute controls in Check sound. The capture source is read-only. The app manages capture-source volume at 100%; speaker volume remains under your control.

Windows has separate capture-source, playback-device and per-app mixer volumes. SoundSpan keeps the capture source at 100% to avoid attenuating every copied output. Players pinned to a specific output may need their output changed to Default and playback restarted.

Known limits: the tested Acer pair uses a 95 ms software buffer plus device processing and saved delays. Windows stream/loopback measurements do not prove physical audibility, acoustic synchronization or performance on every device. The executable is unsigned. Bluetooth/Wi-Fi Windows endpoints may add transport delay; direct DLNA/AirPlay/Chromecast/Sonos casting is not implemented. See COMPATIBILITY.md.



