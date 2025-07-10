# HISPlayer API

1. [Classes](#Classes)
2. [Structs](#Structs)
3. [Enums](#Enums)
4. [Functions](#Functions)
   4.1. [Overridable Functions](#Overridable-functions)
     - [Events](#Events)
     - [Errors](#Errors)
   4.2. [Non-Overridable Functions](#Non-overridable-functions)
     - [Initialization](#Initialization)
     - [Core Player](#Core-Player)
     - [Video Content](#Video-Content)
     - [Timeline](#Timeline)
     - [Tracks](#Tracks)
     - [Captions](#Captions)
     - [Audio](#Audio)
     - [ABR (Adaptive Bitrate)](#ABR-adaptive-bitrate)
     - [Live & Ads](#live--ads)

## Classes

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

## Structs

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

### 3. Enums

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

## Functions
The following functions are provided by **HISPlayerManager**. They are not public so it’s necessary to create a custom script that inherits from **HISPlayerManager**.

### Overridable Functions

#### protected virtual void Awake()
MonoBehaviour function which will be called from the beginning of the scene. It can be overridden but to make the system work it’s necessary to call **base.Awake()** into the overridden function.

#### protected virtual void EventPlaybackReady(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_READY** is triggered.
This event occurs when the current playback of a stream is ready to be used.
Calling functions such as GetTracks before this event is triggered will provide null information.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Number of tracks of the playback.</td>
  </tr>
</table>

#### protected virtual void EventVideoSizeChange(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_VIDEO_SIZE_CHANGE** is triggered.
This event occurs whenever the internal video size of the current track changes.
This event is triggered by the ABR feature.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Width of the video.</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>Heigth of the video.</td>
  </tr>
</table>

#### protected virtual void EventPlaybackPlay(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PLAY** is triggered.
This event occurs whenever an internal playback has been played.

#### protected virtual void EventPlaybackPause(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PAUSE** is triggered.
This event occurs whenever an internal playback has been paused.

#### protected virtual void EventPlaybackStop(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_STOP** is triggered.
This event occurs whenever an internal playback has been stopped.

#### protected virtual void EventPlaybackSeek(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_SEEK** is triggered.
This event occurs whenever an internal playback has been sought to a new time position.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Value of the old track position in milliseconds.</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>Value of the new track position in milliseconds.</td>
  </tr>
</table>

#### protected virtual void EventVolumeChange(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_VOLUME_CHANGE** is triggered.
This event occurs whenever the volume has been modified.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>New value for the volume.</td>
  </tr>
</table>

#### protected virtual void EventEndOfPlaylist(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_END_OF_PLAYLIST** is triggered.
This event occurs whenever an internal playlist reaches the end of the list.

#### protected virtual void EventTextRender(HISPlayerCaptionElement subtitlesInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_TEXT_RENDER** is triggered.
This event occurs whenever a caption’s text has been generated.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>caption</td>
    <td>The next generated caption text.</td>
  </tr>
</table>

#### protected virtual void EventAutoTransition(HISPlayerCaptionElement subtitlesInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPlayerEvent.HISPLAYER_EVENT_AUTO_TRANSITION** is triggered.
This event occurs when the playback has changed to the next video in the playlist automatically.

#### protected virtual void EventPlaybackBuffering(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_BUFFERING** is triggered.
This event occurs whenever an internal playback is buffering.

#### protected virtual void EventEndOfContent(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPlayer_EVENT_END_OF_CONTENT** is triggered.
This event occurs whenever an internal playback reaches the end of the video content.

#### protected virtual void EventOnId3Metadata(HISPlayerEventID3Metadata eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_ID3_METADATA** is triggered. This event is fired when a new Yospace ad cue within the segments is encountered.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ID3Metadata metadata</td>
    <td>Metadata object that contains information about the ad cue</td>
  </tr>
</table>

<table>
<tr>
    <th>ID3Metadata</th>
  </tr>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>int startTime</td>
    <td>Start cue point of ad break in milliseconds</td>
  </tr>
   <tr>
    <td>int endTime</td>
    <td>End cue point of ad break in milliseconds</td>
  </tr>
  <tr>
    <td>ID3MetadataPayload payload</td>
    <td>Contains the Yospace specific ad cue's data. Visit Yospace's Dev Tools for more information: https://developer.yospace.com/login.php</td>
  </tr>
</table>

<table>
  <tr>
    <th>ID3MetadataPayload</th>
  </tr>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>string decodedData</td>
    <td>The decoded data ready to be used</td>
  </tr>
  <tr>
    <td>string data</td>
    <td>Base64 data</td>
  </tr>
  <tr>
    <td>string description</td>
    <td>The data description. It might be empty</td>
  </tr>
  <tr>
    <td>string key</td>
    <td>Cue metadata identifier, e.g. "YMID"</td>
  </tr>
</table>

#### protected virtual void EventAdBlockStarted(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_BLOCK_STARTED** is triggered. This event occurs whenever a group of advertisements starts.

#### protected virtual void EventAdBlockEnd(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_BLOCK_END** is triggered. This event occurs whenever a group of advertisements ends.

#### protected virtual void EventAdStarted(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_STARTED** is triggered. This event occurs whenever a single advertisement starts.

#### protected virtual void EventAdStopped(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_STOPPED** is triggered. This event occurs whenever a single advertisement ends.

#### protected virtual void EventAdPodsInfo(HISPlayerEventAdPodsInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_PODS_INFO** is triggered. This event occurs whenever there is an advertisement pods information indicating cue points of ad breaks.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>int startTime</td>
    <td>Start cue point of ad break in milliseconds</td>
    <td></td>
  </tr>
   <tr>
    <td>int endTime</td>
    <td>End cue point of ad break in milliseconds</td>
    <td></td>
  </tr>
  <tr>
    <td>int param1</td>
    <td>Start cue point of ad break in milliseconds</td>
    <td>Deprecated</td>
  </tr>
   <tr>
    <td>int param2</td>
    <td>End cue point of ad break in milliseconds</td>
    <td>Deprecated</td>
  </tr>
</table>

#### protected virtual void ErrorInfo(HISPlayerErrorInfo errorInfo)
Override this method to add custom logic when an error callback is triggered. Please, refer to the **HISPlayerError** list.

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
