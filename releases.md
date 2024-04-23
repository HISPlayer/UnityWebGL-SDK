# HISPlayer Unity WebGL SDK Release Notes

### Version 3.4.1
##### April 23, 2024
- [**Improvement**] Improvement of software robustness

### Version 3.4.0
##### April 10, 2024
- [**Added**] Multi stream support on Windows Editor
- [**Added**] HISPLAYER_ERROR_PLATFORM_NOT_REGISTERED error event
- [**Improvement**] Optimized initialization of the player
- [**Improvement**] Optimized HISPlayer Settings
    - A warning message will be displayed in case a field required by HISPlayer SDK is missing

### Version 3.3.0
##### January 25, 2024
- [**Added**] API to change video content using the URL string as a parameter is added to multiplatform SDK:
    - **ChangeVideoContent(int playerIndex, string url, int resumePosition = 0, AdsProperties ads = null)**
- [**Improvement**] Optimized Unity logs improvement
- [**Added**] WebGL Ads Insertion to multiplatform SDK

### Version 3.2.0
##### December 7, 2023
- [**Added**] AutoTransition and LoopPlayback APIs to multiplatform SDK
- [**Added**] Unity 2023 support
- [**Added**] Error system
- [**Added**] Seek event

### Version 3.1.1
##### November 23, 2023
- [**Improvement**] Improvement of software robustness

### Version 3.1.0
##### October 11, 2023
- [**Improvement**] Improvement of software robustness

### Version 3.0.0 (Multiplatform SDK)
##### September 5, 2023
The WebGL SDK is moved to multiplatform HISPlayerSDK (Android, iOS, macOS, WebGL, Windows)

Starting from version 3.0.0, the WebGL SDK is part of multiplatform SDK

### Version 1.14.0
##### October 25, 2023
- [Added] Yospace server-side ad insertion.

### Version 1.13.0
##### October 17, 2023
- [Improvement] Increased default connection timeout.
- [Added] Connection manifest and segments timeout control API.

### Version 1.12.0
##### October 13, 2023
- [Added] Client-side ads insertion.

### Version 1.11.0
##### September 22, 2023
- [Added] Server-side ads insertion.
- [Added] Custom Shaders for Linear Color Space.

### Version 1.10.0
##### September 6, 2023
- [Improvement] Optimized LogLevel API.

### Version 1.9.0
##### September 1, 2023
- [Improvement] Optimized video playback on Safari browser.
- [Improvement] Optimized project build process using Unity 2020.

### Version 1.8.0
##### July 18, 2023
- [Added] SetLogLevel API to filter the logs by the types : Error, Warning, Info, Debug, None.
- [Improvement] Optimized seek functionality on Windows Editor.

### Version 1.7.0
##### June 29, 2023
- [Improvement] Optimized Release API when changing Unity scene.
- [Improvement] Optimized SetupPlayer API during runtime for Windows Editor.

### Version 1.6.0
##### June 12, 2023
- [Added] ChangeVideoContent API for MacOS Editor.
- [Added] GetTracks API for MacOS Editor.
- [Improvement] Optimized Release API.
- [Improvement] Removed GLManager.js and Queue.js files.
- [Improvement] Optimized Low Latency playback.

### Version 1.5.0
##### May 17, 2023
- [Added] MacOS Editor support.

### Version 1.4.0
##### April 4, 2023
- [Added] VideoTrackChange event.
- [Improvement] Optimized SetTrack error.

### Version 1.3.0
##### March 27, 2023
- [Added] Loop play API.
- [Added] Windows Editor support.

### Version 1.2.0
##### March 23, 2023
- [Added] Playback current time API.
- [Added] Playback duration API.
- [Added] Change video content at runtime API.
- [Added] Raw Image and Material override support.

### Version 1.1.0
##### March 7, 2023
- [Added] ABR support.
- [Improvement] Optimized playing MP4 content issue.

### Version 1.0.0
##### March 2, 2023
- [Added] Initial release of HisPlayer WebGL SDK for Unity.
