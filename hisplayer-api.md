# HISPlayer API

1. [Classes](#classes)  
2. [Structs](#structs)  
3. [Enums](#enums)  
4. [Functions](#functions)  
   - [Overridable Functions](#overridable-functions)  
     - [Events](#events)  
     - [Errors](#errors)  
   - [Non-Overridable Functions](#non-overridable-functions)  
     - [Initialization](#initialization)  
     - [Core Player](#core-player)  
     - [Video Content](#video-content)  
     - [Timeline](#timeline)  
     - [Tracks](#tracks)  
     - [Captions](#captions)  
     - [Audio](#audio)  
     - [ABR (Adaptive Bitrate)](#abr-adaptive-bitrate)  
     - [Live & Ads](#live--ads)


## CLASSES

#### StreamProperties

- `public StreamProperties(bool isLoopPlaybackEnabled = true, bool isAutoTransitionEnabled = false)`
  - Constructor for the class. Parameters define `LoopPlayback` and `AutoTransition`.
- `public HISPlayerRenderMode renderMode`: Type of texture for rendering. Default is `HISPlayerRenderMode.NONE`.
- `public Material material`: Reference to the Unity Material.
- `public RawImage rawImage`: Reference to the Unity Raw Image.
- `public RenderTexture renderTexture`: Reference to the Unity Render Texture.
- `public List<string> url`: List of URLs for the stream.
- `public bool autoPlay`: Whether the stream auto-plays after setup.
- `public bool EnableRendering`: Whether the stream is rendered. Can change at runtime.
- `public bool LoopPlayback (Read-only)`: Loops current playback. Default is true.
- `public bool AutoTransition (Read-only)`: Switches to next video in the playlist. Default is false.
- `public List<AdsProperties> adsProperties`: Advertisement configuration list.
- `public int startingBitrate`: Starting bitrate in bps. `0` starts with lowest track.
- `public int manifestTimeout`: Timeout for manifest request in ms. `0` means unlimited. Default is `10000ms`.
- `public int segmentsTimeout`: Timeout for segment requests in ms. `0` means unlimited. Default is `5000ms`.

#### AdsProperties

- `public enum AdsMode`: Types of the advertisement library.
- `public struct ImaConfig`: Configuration for IMA ad mode.
- `public struct DaiConfig`: Configuration for DAI ad mode.
- `public struct MediaTailorConfig`: Configuration for MediaTailor ad mode.

## STRUCTS

#### HISPlayerEventInfo

- `public HISPlayerEvent eventType`
- `public int playerIndex`
- `public float param1`
- `public float param2`
- `public float param3`
- `public float param4`
- `public string stringInfo`

#### HISPlayerErrorInfo

- `public HISPlayerError errorType`
- `public int playerIndex`
- `public float param1`
- `public string stringInfo`

#### HISPlayerTrack

- `public string id`
- `public int bitrate`
- `public int width`
- `public int height`
- `public int framerate`

#### HISPlayerCaptionTrack

- `public string id`
- `public string language`

#### HisPlayerAudioTrack

- `public string id`
- `public string caption`

#### HISPlayerCaptionElement

- `public int playerIndex`
- `public string language`

#### ImaConfig

- `public string adTagUri`
- `public bool enableVpaid`
- `public string pageUrl`

#### DaiConfig

- `public string assetKey`
- `public string contentSrcId`
- `public string videoId`

#### MediaTailorConfig

- `public string baseUrl`
- `public string manifestUrl`
- `public string adsParams`

## ENUMS

#### HISPlayerRenderMode

- `RenderTexture`
- `Material`
- `RawImage`

#### AdsMode

- `DAI`
- `MEDIA_TAILOR`
- `YOSPACE`
- `IMA`
- `NONE`

#### HISPlayerEvent

- `HISPLAYER_EVENT_PLAYBACK_READY`
- `HISPLAYER_EVENT_VIDEO_SIZE_CHANGE`
- `HISPLAYER_EVENT_PLAYBACK_PLAY`
- `HISPLAYER_EVENT_PLAYBACK_PAUSE`
- `HISPLAYER_EVENT_PLAYBACK_STOP`
- `HISPLAYER_EVENT_PLAYBACK_SEEK`
- `HISPLAYER_EVENT_VOLUME_CHANGE`
- `HISPLAYER_EVENT_END_OF_PLAYLIST`
- `HISPLAYER_EVENT_AUTO_TRANSITION`
- `HISPLAYER_EVENT_PLAYBACK_BUFFERING`
- `HISPLAYER_EVENT_END_OF_CONTENT`
- `HISPLAYER_EVENT_AD_BLOCK_STARTED`
- `HISPLAYER_EVENT_AD_BLOCK_ENDY`
- `HISPLAYER_EVENT_AD_STARTED`
- `HISPLAYER_EVENT_AD_STOPPED`
- `HISPLAYER_EVENT_AD_PODS_INFO`
- `HISPLAYER_EVENT_ID3_METADATA`

#### HISPlayerError

- `HISPLAYER_ERROR_LICENSE_EXPIRED`
- `HISPLAYER_ERROR_NOT_VALID_APPID`
- `HISPLAYER_ERROR_GENERAL_LICENSE_ERROR`
- `HISPLAYER_ERROR_LICENSE_DISABLED`
- `HISPLAYER_ERROR_IMPRESSIONS_LIMIT_REACHED`
- `HISPLAYER_ERROR_PLAYBACK_DURATION_LIMIT_REACHED`
- `HISPLAYER_ERROR_PLATFORM_NOT_REGISTERED`

#### LogLevel

- `ERROR`
- `WARNING`
- `INFO`
- `DEBUG`
- `NONE`


These log levels are represented as an enum of integers, so every type of log whose representative integer is greater or equal to the established log level will be shown. The log levels are represented as follows:

```cs
public enum LogLevel
{
    DEBUG, // = 0
    INFO, // = 1
    WARNING, // = 2
    ERROR, // = 3
    NONE // = 4
}
```

## FUNCTIONS
The following functions are provided by **HISPlayerManager**. They are not public so it’s necessary to create a custom script that inherits from **HISPlayerManager**.

### Overridable Functions

These methods can be overridden to inject custom logic into the player's behavior when certain events are triggered.  
**Important**: Always call `base.MethodName()` in the overridden method to preserve internal behavior.

---

#### 🧠 Unity Lifecycle

- `Awake()`  
  Unity's lifecycle method. Called at the beginning of the scene.  
  You **must** call `base.Awake()` in your override for the system to work correctly.

---

#### 🔁 Playback Lifecycle Events

These methods are triggered during playback transitions.

- `EventPlaybackReady(HISPlayerEventInfo eventInfo)`  
  Triggered when the stream is ready to be used.

- `EventPlaybackPlay(HISPlayerEventInfo eventInfo)`  
  Triggered when playback starts.

- `EventPlaybackPause(HISPlayerEventInfo eventInfo)`  
  Triggered when playback is paused.

- `EventPlaybackStop(HISPlayerEventInfo eventInfo)`  
  Triggered when playback is stopped.

- `EventPlaybackSeek(HISPlayerEventInfo eventInfo)`  
  Triggered when seeking to a new time position.  
  |------|-------------|
  | Name | Description |
  |------|-------------|
  | `param1` | Old track position (ms) |
  | `param2` | New track position (ms) |
  |------|-------------|
  
- `EventPlaybackBuffering(HISPlayerEventInfo eventInfo)`  
  Triggered when buffering occurs.

- `EventEndOfContent(HISPlayerEventInfo eventInfo)`  
  Triggered when the end of the content is reached.

- `EventEndOfPlaylist(HISPlayerEventInfo eventInfo)`  
  Triggered at the end of the playlist.

- `EventAutoTransition(HISPlayerCaptionElement subtitlesInfo)`  
  Triggered when the next video auto-plays in the playlist.

---

#### 🔊 Volume Events

- `EventVolumeChange(HISPlayerEventInfo eventInfo)`  
  Triggered when volume is modified.  
  | Name | Description |
  |------|-------------|
  | `param1` | New volume value |

---

#### 🖼️ Video Track Events

- `EventVideoSizeChange(HISPlayerEventInfo eventInfo)`  
  Triggered when video resolution changes due to ABR.  
  | Name | Description |
  |------|-------------|
  | `param1` | Width |
  | `param2` | Height |

---

#### 📄 Caption Events

- `EventTextRender(HISPlayerCaptionElement subtitlesInfo)`  
  Triggered when caption text is rendered.  
  | Name | Description |
  |------|-------------|
  | `caption` | The generated caption text |

---

#### 🧩 Metadata Events

- `EventOnId3Metadata(HISPlayerEventID3Metadata eventInfo)`  
  Triggered when a Yospace ID3 ad cue is found.

**ID3Metadata**
| Name | Description |
|------|-------------|
| `startTime` | Start of ad break (ms) |
| `endTime` | End of ad break (ms) |
| `payload` | Metadata payload (see below) |

**ID3MetadataPayload**
| Name | Description |
|------|-------------|
| `decodedData` | Decoded metadata |
| `data` | Base64-encoded data |
| `description` | Optional description |
| `key` | Metadata identifier (e.g. "YMID") |

---

#### 📺 Advertisement Events

- `EventAdBlockStarted(HISPlayerEventInfo eventInfo)`  
- `EventAdBlockEnd(HISPlayerEventInfo eventInfo)`  
- `EventAdStarted(HISPlayerEventInfo eventInfo)`  
- `EventAdStopped(HISPlayerEventInfo eventInfo)`

- `EventAdPodsInfo(HISPlayerEventAdPodsInfo eventInfo)`  
  Triggered when ad pod cue point information is available.  
  | Name | Description | Notes |
  |------|-------------|-------|
  | `startTime` | Start of ad break (ms) | |
  | `endTime` | End of ad break (ms) | |
  | `param1` | Deprecated start cue | Deprecated |
  | `param2` | Deprecated end cue | Deprecated |

---

#### ❌ Error Handling

- `ErrorInfo(HISPlayerErrorInfo errorInfo)`  
  Triggered when an error occurs. Refer to `HISPlayerError` for types and descriptions.

### Non-virtual functions

These functions can’t be overridden and they can be used only inside the inherited script. If it’s needed to use some of these functions in the Unity scene, for example with buttons, it is needed to create a public function that connects the button with the API.

---

### 🟢 Initialization

#### protected void SetUpPlayer()
Initialize the player video stream system internally. It is necessary to use this function before anything else.

#### protected void Release()
Free all resources internally. In the SDK v4.3.0 and below, it's necessary to call this function before changing between Unity scenes or before quitting the application. In the SDK v4.4.0 and above, the release is called automatically when changing scenes or quitting the application and it's not required to call this function.

---

### ▶️ Core Player

#### protected void Play(int playerIndex)
Play a certain stream giving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void Pause(int playerIndex)
Pause a certain stream giving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void Stop(int playerIndex)
Stop a certain stream giving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void Seek(int playerIndex, int milliseconds)
Seek a certain stream to a certain time giving a **playerIndex** and the time of the track to be sought in **milliseconds**. The stream is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetVolume(int playerIndex, float volume)
Modify the volume of a certain stream giving a **playerIndex**. The **volume** of the track value ranges between 0.0f and 1.0f. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.  
Call this API after having interaction with the web page/screen, otherwise audio will not play on WebGL due to browser autoplay policy.

#### protected void SetPlaybackSpeedRate(int playerIndex, float speed)
Modify the **speed rate** of a certain stream giving a **playerIndex**. The value of the player's speed must be greater (>) than 0.0f and less than or equal (<=) to 8.0f. The default value of player's speed is 1.0f. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetPlaybackSpeedRate(int playerIndex)
Obtain the **speed rate** of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

---

### 🎞️ Video Content

#### protected void ChangeVideoContent(int playerIndex, int urlIndex, int resumePosition = 0 (optional), AdsProperties ads = null (optional))
Change the video’s URL of a certain player. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The **urlIndex** is associated with the index of the element in the list of URLs. The **resumePosition** parameter is optional and is the time position in second(s) where the new content is starting the playback, default value is 0. The **AdsProperties** is an ads properties to use when loading the new content, default value is null.

#### protected void ChangeVideoContent(int playerIndex, string url, int resumePosition = 0 (optional), AdsProperties ads = null (optional))
Change the video’s URL of a certain player given a new URL. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The parameter **url** is the link to the new video. Please, make sure the new URL is correctly written. The **resumePosition** parameter is optional and is the time position in second(s) where the new content is starting the playback, default value is 0. The **AdsProperties** is an ads properties to use when loading the new content, default value is null.

---

### ⏱️ Timeline

#### protected long GetVideoPosition(int playerIndex)
Provides information about the timeline position in milliseconds, of the current video of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected long GetVideoDuration(int playerIndex)
Provides information about the total duration in milliseconds, of the current video of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

---

### 🧩 Tracks

#### protected HISPlayerTrack[] GetTracks(int playerIndex)
Provides the list of the video tracks of the current video playing on a certain stream.

#### protected int GetTrackBitrate(int playerIndex, int trackIndex)
Get the bitrate of a certain track of a certain stream.

#### protected int GetTrackWidth(int playerIndex, int trackIndex)
Get the width of a certain track of a certain stream.

#### protected int GetTrackHeight(int playerIndex, int trackIndex)
Get the height of a certain track of a certain stream.

#### protected int GetTrackID(int playerIndex, int trackIndex)
Get the ID of a certain track of a certain stream.

#### protected int GetTrackCount(int playerIndex)
Get the number of tracks of a certain stream.

#### protected void SelectTrack(int playerIndex, int trackIndex)
Select a certain track of a certain stream to be used as the main track. This action will disable ABR, to enable it again you can use **EnableABR** API.

---

### 📶 ABR (Adaptive Bitrate)

#### protected void EnableABR(int playerIndex)
Enables the ABR to change automatically between tracks.

#### protected void DisableABR(int playerIndex)
Disables the ABR to prevent the player from changing tracks regardless of bandwidth.

#### protected void SetMaxBitrate(int playerIndex, int bitrate)
Set a new maximum bitrate (in bits per second) of a specific track.

#### protected void SetMinBitrate(int playerIndex, int bitrate)
Set a new minimum bitrate (in bits per second) of a specific track.

---

### 💬 Captions

#### public void EnableCaptions(int playerIndex, bool enabled)
Enables the captions of the stream.

#### public HISPlayerCaptionTrack[] GetCaptionTrackList(int playerIndex)
Provide information about all the captions of a certain stream.

#### public int GetCaptionsCount(int playerIndex)
Obtain the number of captions of a certain stream.

#### public string GetCaptionID(int playerIndex, int ccTrackIndex)
Obtain the ID of a certain caption of a certain player.

#### public string GetCaptionLanguage(int playerIndex, int ccTrackIndex)
Obtain the language of a certain caption of a certain player.

#### public void SelectCaptionTrack(int playerIndex, int ccTrackIndex)
Select a certain caption of a certain stream to be used. Before using this function, it is recommended to use GetCaptionTrackList in order to know all the information about the captions.

---

### 🔊 Audio

#### public HisPlayerAudioTrack[] GetAudioTrackList(int playerIndex)
Provide information about all the audio tracks of a certain stream.

#### public int GetAudioCount(int playerIndex)
Obtain the number of audio of a certain stream.

#### public string GetAudioID(int playerIndex, int audioTrackIndex)
Obtain the ID of a certain audio of a certain player.

#### protected string GetAudioLanguage(int playerIndex, int audioTrackIndex)
Obtain the language of a certain audio of a certain player.

#### protected void SelectAudioTrack(int playerIndex, int audioTrackIndex)
Select a certain audio-track of a certain stream to be used.

---

### 📡 Live & Ads

#### protected bool IsLive(int playerIndex)
Returns true if a certain stream is a live stream.

#### protected float GetAdDuration(int playerIndex)
Get the duration of a certain advertisement in milliseconds (ms).

#### protected float GetAdRemainingTime(int playerIndex)
Get the remaining time of a certain advertisement in milliseconds (ms).

#### protected float GetAdCurrentTime(int playerIndex)
Get the current time of a certain advertisement in milliseconds (ms).
