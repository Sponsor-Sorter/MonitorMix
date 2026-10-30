SoundSpan 0.6.15 adds Windows master-mute propagation, background audio discovery and setup recovery after endpoint IDs change. Normal playback, volume/mute and responsiveness were confirmed on the Windows 11 test PC. Fixture routing and software output reattachment passed; physical device unplug/reconnect, sustained game load and acoustic synchronization remain separate verification. No automatic remapping is inferred from identical monitor names.

# Audio device compatibility

SoundSpan enumerates active Windows playback endpoints through WASAPI. There is no monitor-brand allowlist. An installed driver must expose the output in Windows Sound settings and allow shared-mode PCM playback.

| Output type | Support scope | Verification |
|---|---|---|
| HDMI/DisplayPort monitor or TV speakers | Windows playback endpoint | Two Acer/AMD endpoints physically enumerated and silent routing tested |
| Internal or analog sound-card speakers/headphones | Windows playback endpoint | Driver path supported; physical analog output not tested here |
| USB speakers, DACs, wired USB headsets | Windows playback endpoint | Driver path supported; physical USB hardware not tested here |
| Bluetooth headphones/speakers, wireless headsets | Windows playback endpoint | Driver path supported; transport/profile behavior not tested here |
| Virtual playback devices | Windows playback endpoint | Oculus virtual endpoint and Realtek digital source exercised |
| Mono playback devices | Explicit stereo-to-mono averaging | Signal tests passed; physical mono endpoint not available here |
| Multichannel playback devices | Stereo app stream converted by Windows to the endpoint format | Physical multichannel output not tested here |
| ASIO-only or exclusive-only devices | Not supported by this backend | Requires another backend |

The engine uses 48 kHz float PCM internally. Windows shared-mode conversion handles compatible endpoint sample rates and PCM formats. Stereo copies are stereo; a multichannel output does not automatically become discrete surround. Discrete channel roles require a compatible one-to-eight-channel source; standard 5.1/7.1 channel ordering is assumed. Encoded Dolby/DTS passthrough and nonstandard multichannel layouts are not supported.

Fast setup keeps checked outputs and chooses a separate unselected source: a cable-labelled virtual device, generic digital/S/PDIF output, current source, Windows default or another available endpoint. Prefer a silent/unused digital source or installed virtual cable. A physical source also plays directly and cannot be synchronized with copied outputs by the app. Do not choose a copied output as its own source. If every device is checked, provide a separate source or uncheck one.

Wireless transport and speaker processing add delay that software clocks cannot measure. The 95 ms observed software floor on the tested Acer pair is not a promise for other drivers. Larger native buffers may require more latency. Manual delay or optional microphone calibration can align devices relatively; it cannot eliminate baseline latency. Bluetooth profile changes, device disconnects and sleep require checking the device list and restarting playback.

Devices disabled or disconnected in Windows are not active playback endpoints. Microphones are inputs, not audio outputs. A broken or exclusively occupied driver may reject startup; use Windows shared mode, close the exclusive application and try again.

References: [Microsoft WASAPI](https://learn.microsoft.com/en-us/windows/win32/coreaudio/wasapi), [Windows stream conversion flags](https://learn.microsoft.com/en-us/windows/win32/coreaudio/audclnt-streamflags-xxx-constants), [WASAPI loopback](https://learn.microsoft.com/en-us/windows/win32/coreaudio/loopback-recording).

## Optical, Bluetooth and Wi-Fi

Optical fibre/TOSLINK/S/PDIF outputs are supported when their driver exposes a Windows shared-mode PCM playback endpoint. The tested Realtek Digital source is such an endpoint; an optical receiver or cable was not physically listening-tested. Encoded Dolby/DTS passthrough is outside this PCM engine.

Bluetooth and Wi-Fi/wireless playback endpoints can be selected when they appear in Windows Sound settings. Their own transport/codec buffers may add substantial delay, and cannot be removed by SoundSpan's software clock correction. No Bluetooth or Wi-Fi audio endpoint was available for physical verification in this build.

Direct DLNA, AirPlay, Chromecast and Sonos network casting is not implemented in 0.6.12. Network discovery does not make a device a usable Windows playback endpoint. A separate streaming backend and per-device acceptance are required.

## Application routing

App routing uses Windows per-application output preferences and any active Windows playback endpoint. Native preference changes, monitor following and persistence were tested with a disposable silent app on Windows 10 build 19045. This does not prove live stream migration in every browser/game/player. Exclusive/ASIO or app-selected outputs may ignore Windows preferences; browser tabs generally share one destination. No SoundSpan copy buffer is added to direct app routes. Automatic following needs SoundSpan running and speakers mapped to the relevant screens.


Bluetooth setup: native classic Bluetooth pairing and audio-service enablement are implemented. LE-only devices use Windows Bluetooth settings and are added when an identifiable audio output appears. Actual pairing/profile switching requires hardware testing; no Bluetooth adapter was available on the test PC. Output hot-add/remove was verified using connected monitor endpoints. Some applications with fixed or cached audio devices require playback restarted.

Bluetooth preview icons use reported Class of Device information. Unknown or unavailable type metadata uses a generic Bluetooth icon. Classic connected devices and ready Bluetooth LE Windows audio endpoints can appear; non-audio LE devices are not guaranteed to appear. A connected phone/tablet needs a Windows playback endpoint to receive audio. Preview layout and classification fixtures were checked; physical Bluetooth testing remains unavailable on this PC.


