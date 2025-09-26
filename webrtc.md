# HISPlayer WebRTC

## Configuration

To use **WebRTC** in Unity, you must change the Player Mode in the Platform WebGL settings:

<p align="center">
  <img width="466" height="74" alt="image" src="https://github.com/user-attachments/assets/68b6267d-89c0-4ab3-bb42-64f7d530a9f3" />
</p>

---

## WebRTCPlayer API

The following API is provided by the **WebRTCPlayer** class.

### Constants

* **(static, constant) BUFFER_TYPE : string**  
WebRTCPlayer buffer types.
  * **CONNECTION** – Connection
  * **INITIAL** – Initial
  * **SEEK** – Seek
  * **PAUSE** – Pause
  * **BACKGROUND** – Background

* **(static, constant) HisPlayerEvent : string**  
WebRTCPlayer event types.
  * **LICENSE_ERROR** – `licenseError`  
  * **STATE_CHANGE** – `stateChange`  
    - The event contains a `detail` field with the **PLAYER_STATES** value.  
  * **BUFFER_TYPE** – `bufferType`  
    - The event contains a `detail` field with the **BUFFER_TYPE** value.  
  * **ERROR** – `error`  
    - The event contains a `detail` field with the error description.  

* **(static, constant) PLAYER_STATES : string**  
WebRTCPlayer playback states.
  * **NONE** – None  
  * **CONTENT_REQUESTED** – ContentRequested  
  * **READY** – Ready  
  * **BUFFERING** – Buffering  
  * **PLAYING** – Playing  
  * **PAUSED** – Paused  
  * **ENDED** – Ended  

---

### Methods

* **addEventListener(type, listener)**  
Adds an event listener to this object.  
  - **type**: `string` – The event type to listen for.  
  - **listener**: `EventListener | function` – The callback or listener object to invoke.  

* **async destroy()**  
Destroys the WebRTC player instance and releases all resources.  

* **getMediaElement() → {HTMLMediaElement}**  
Returns the underlying media element.  

* **getVolume() → {number}**  
Returns the current volume, between `0.0` (muted) and `1.0` (max).  

* **async init(userConfig)**  
Creates the WebRTC player.  
  - **userConfig**: `WebRTCConfig` – The configuration object.  

* **isMuted() → {boolean}**  
Returns `true` if playback is muted.  

* **listenToAllEvents(listener)**  
Adds an event listener that is invoked for **all event types**.  
  - **listener**: `EventListener | function` – Callback for events.  

* **pause()**  
Pauses playback. Does nothing if already paused.  

* **play()**  
Resumes playback if the stream is loaded and paused.  

* **removeEventListener(type, listener)**  
Removes an event listener.  
  - **type**: `string` – The event type.  
  - **listener**: `EventListener | function` – The listener to remove.  

* **setMute(muted)**  
Mutes or unmutes the playback.  
  - **muted**: `boolean` – `true` to mute, `false` to unmute.  

* **setVolume(volume)**  
Sets the volume.  
  - **volume**: `number` – Value between `0.0` and `1.0`.  
