# HISPlayer API

## Public API

The following public APIs are provided by **HISPlayerManager**

* **public string licenseKey**: License key for making the SDK works. License key is not required for Unity Editor usage.

* **public List <StreamProperties> multiStreamProperties**: List of properties for multi stream. Please, don't modify this list directly in the code.

* **public class StreamProperties**:
    * **public StreamProperties(bool isLoopPlaybackEnabled = true, bool isAutoTransitionEnabled = false)**: Constructor of the class. The received parameters will set the value of **LoopPlayback** and **AutoTransition** properties respectively. 
    * **public HISPlayerRenderMode renderMode**: Type of texture for rendering. **HISPlayerRenderMode.NONE** by default.
    * **public Material material**: Reference to the Unity Material.
    * **public RawImage rawImage**: Reference to the Unity Raw Image.
    * **public RenderTexture renderTexture**: Reference to the Unity Render Texture.
    * **public List \<string\> url**: List of the URLs for the stream.
    * **public bool autoPlay**: If true, the players will start playing automatically after set-up.
    * **public bool EnableRendering**: Determines if the stream will be rendered or not. The value can change in every moment for toggling between render or non-render mode. If true, the player will be rendered. It only can change in runtime.
    * **public bool LoopPlayback (Read-only)**: Loop the current playback. It's true by default. To modify this value, please, use the Editor or the constructor **StreamProperties(loopPlayback, autoTransition)**.
    * **public bool AutoTransition (Read-only)**: Change the playback to the next video in the playlist. This action won't have effect when loopPlayback is true. It's false by default. To modify this value, please, use the Editor or the constructor **StreamProperties(loopPlayback, autoTransition)**.
    * **public List <AdsProperties> adsProperties**: List of properties to configure advertisement insertions for each player in the scene.
    * **public int startingBitrate**: The bitrate in bps the player will try to start playing. Setting it to 0 will make the player start with the lowest track.
    * **public int manifestTimeout**: The manifest request connection timeout, in milliseconds. Zero means unlimited. Defaults to 10000 milliseconds. Not visible in the Editor.
    * **public int segmentsTimeout**: The segments requests connection timeout, in milliseconds. Zero means unlimited. Defaults to 5000 milliseconds. Not visible in the Editor.

* **public enum HISPlayerRenderMode**: Type of texture for rendering.
    * **RenderTexture**
    * **Material**
    * **RawImage**

* **public class AdsProperties**:
  * **public enum AdsMode**: Types of the advertisement library.
  * **public struct ImaConfig**: Config for IMA ads mode.
  * **public struct DaiConfig**: Config for DAI ads mode.
  * **public struct MediaTailorConfig**: Config for MediaTailor ads mode.

* **public enum AdsMode**: Types of the advertisement library.
    * **DAI**
    * **MEDIA_TAILOR**
    * **YOSPACE**
    * **IMA**
    * **NONE**

 * **public struct ImaConfig**: Config for DAI ads mode.
    * **public string adTagUri**: Advertisement URL that is going to be played. VAST, VPAID, VMAP are supported. If the IMA ad mode is used this parameter is mandatory.
    * **public bool enableVpaid**: Enables the usage of VPAID. The ads mode must be IMA.
    * **public string pageUrl**: Adds a parameter to the ad request to keep track of the domain that sent the request. For targeting purposes. The ad mode must be IMA.

 * **public struct DaiConfig**: Config for DAI ads mode.
    * **public string assetKey**: For live streams. This is used to determine which stream should be played.
    * **public string contentSrcId**: For VoD (on-demand) streams. Unique identifier for the publisher content, from a CMS.
    * **public string videoId**: For VoD (on-demand) streams. Identifier for the video content source.

 * **public struct MediaTailorConfig**: Config for MediaTailor ads mode.
    * **public string baseUrl**: Base URL for video and ads.
    * **public string manifestUrl**: Video URL to be attached to the baseURL.
    * **public string adsParams**: Contains 'Params: string' this is the ad URL to be attached to the baseURL.

* **public enum HISPlayerEvent**: The list of events provided by HISPlayer SDK. The events can be used with the virtual functions in the next section:
    * **HISPLAYER_EVENT_PLAYBACK_READY**
    * **HISPLAYER_EVENT_VIDEO_SIZE_CHANGE**
    * **HISPLAYER_EVENT_PLAYBACK_PLAY**
    * **HISPLAYER_EVENT_PLAYBACK_PAUSE**
    * **HISPLAYER_EVENT_PLAYBACK_STOP**
    * **HISPLAYER_EVENT_PLAYBACK_SEEK**
    * **HISPLAYER_EVENT_VOLUME_CHANGE**
    * **HISPLAYER_EVENT_END_OF_PLAYLIST**
    * **HISPLAYER_EVENT_AUTO_TRANSITION**
    * **HISPLAYER_EVENT_PLAYBACK_BUFFERING**
    * **HISPLAYER_EVENT_END_OF_CONTENT**
    * **HISPLAYER_EVENT_AD_BLOCK_STARTED**
    * **HISPLAYER_EVENT_AD_BLOCK_ENDY**
    * **HISPLAYER_EVENT_AD_STARTED**
    * **HISPLAYER_EVENT_AD_STOPPED**
    * **HISPLAYER_EVENT_AD_PODS_INFO**
    * **HISPLAYER_EVENT_ID3_METADATA**
 
* **public enum HISPlayerError**: The list of errors provided by HISPlayer SDK. The errors can be used with the virtual functions in the next section:
   * **HISPLAYER_ERROR_LICENSE_EXPIRED** (no function on this)
   * **HISPLAYER_ERROR_NOT_VALID_APPID** (no function on this)
   * **HISPLAYER_ERROR_GENERAL_LICENSE_ERROR** (no function on this)
   * **HISPLAYER_ERROR_LICENSE_DISABLED** (no function on this)
   * **HISPLAYER_ERROR_IMPRESSIONS_LIMIT_REACHED** (no function on this)
   * **HISPLAYER_ERROR_PLAYBACK_DURATION_LIMIT_REACHED** (no function on this)
   * **HISPLAYER_ERROR_PLATFORM_NOT_REGISTERED** (no function on this)

* **public struct HISPlayerEventInfo**: The information of the triggered event.
   * **public HISPlayerEvent eventType**: The type of the event triggered.
   * **public int playerIndex**: The index of the player where the event is triggered.
   * **public float param1**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param2**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param3**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param4**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public string stringInfo**: Log information about the event.

* **public struct HISPlayerErrorInfo**: The information of the triggered error.
   * **public HISPlayerError errorType**: The type of the error triggered.
   * **public int playerIndex**: The index of the player where the error is triggered.
   * **public float param1**: This will have different meanings depending on the error. If there is no information about the parameter, it will have the default value -1.
   * **public string stringInfo**: Log information about the error.

* **public struct HISPlayerTrack**:
   * **public string id**: Id of the track
   * **public int bitrate**: Bitrate of the track in bits per second.
   * **public int width**: Width of the track.
   * **public int height**: Height of the track.
   * **public int framerate**: Framerate of the track in frames per second.
 
* **public struct HISPlayerCaptionTrack**:
   * **public string id**: Id of the caption
   * **public string language**: Language of the caption
 
* **public struct HisPlayerAudioTrack**:
   * **public string id**: Id of the audio
   * **public string caption**: Language of the audio
 
* **public struct HISPlayerCaptionElement**: The information of the triggered event turns into caption’s format.
   * **public int playerIndex**: The index of the player where the event is triggered.
   * **public string language**: The next generated caption text.

* **public enum LogLevel**: The current logging level to filter which log messages are output.
  * **ERROR** : Indicates critical errors that may prevent the application from functioning correctly.
  * **WARNING** : Indicates potential issues or situations that may require attention.
  * **INFO** : Provides general informational messages about the application's execution.
  * **DEBUG** : Logs messages useful for debugging and troubleshooting purposes, typically only visible during development.
  * **NONE** : No log messages will appear.

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

### Virtual functions - These functions can be overridden

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

#### protected void SetUpPlayer()
Initialize the player video stream system internally. It is necessary to use this function before anything else.

#### protected void Release()
Free all resources internally. In the SDK v4.3.0 and below, it's necessary to call this function before changing between Unity scenes or before quitting the application. In the SDK v4.4.0 and above, the release is called automatically when changing scenes or quitting the application and it's not required to call this function.

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

#### protected void ChangeVideoContent(int playerIndex, int urlIndex, int resumePosition = 0 (optional), AdsProperties ads = null (optional))
Change the video’s URL of a certain player. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The **urlIndex** is associated with the index of the element in the list of URLs. The **resumePosition** parameter is optional and is the time position in second(s) where the new content is starting the playback, default value is 0. The **AdsProperties** is an ads properties to use when loading the new content, default value is null.

#### protected void ChangeVideoContent(int playerIndex, string url, int resumePosition = 0 (optional), AdsProperties ads = null (optional))
Change the video’s URL of a certain player given a new URL. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The parameter **url** is the link to the new video. Please, make sure the new URL is correctly written. The **resumePosition** parameter is optional and is the time position in second(s) where the new content is starting the playback, default value is 0. The **AdsProperties** is an ads properties to use when loading the new content, default value is null.

#### protected long GetVideoPosition(int playerIndex)
Provides information about the timeline position in milliseconds, of the current video of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected long GetVideoDuration(int playerIndex)
Provides information about the total duration in milliseconds, of the current video of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected HISPlayerTrack[] GetTracks(int playerIndex)
Provides the list of the video tracks of the current video playing on a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackBitrate(int playerIndex, int trackIndex)
Get the bitrate of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackWidth(int playerIndex, int trackIndex)
Get the width of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackHeight(int playerIndex, int trackIndex)
Get the height of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 of the list.

#### protected int GetVideoWidth(int playerIndex)
Get the width of the current track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetVideoHeight(int playerIndex)
Get the height of the current track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackID(int playerIndex, int trackIndex)
Get the ID of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackCount(int playerIndex)
Get the number of tracks of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SelectTrack(int playerIndex, int trackIndex)
Select a certain track of a certain stream to be used as the main track. This action will disable ABR, to enable it again you can use **EnableABR** API. The possible tracks can be obtained from the tracks returned from the method GetTracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public void EnableCaptions(int playerIndex, bool enabled)
Enables the captions of the stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public HISPlayerCaptionTrack[] GetCaptionTrackList(int playerIndex)
Provide information about all the captions of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public int GetCaptionsCount(int playerIndex)
Obtain the number of captions of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public string GetCaptionID(int playerIndex, int ccTrackIndex)
Obtain the ID of a certain caption of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public string GetCaptionLanguage(int playerIndex, int ccTrackIndex)
Obtain the language of a certain caption of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

### public void SelectCaptionTrack(int playerIndex, int ccTrackIndex)
Select a certain caption of a certain stream to be used. Before using this functions is recommended to use GetCaptionTrackList in order to know all the information about the captions. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void EnableABR(int playerIndex)
Enables the ABR to change automatically between tracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetMaxBitrate(int playerIndex, int bitrate)
Set a new maximum bitrate (in bits per second) of a specific track. This doesn’t disable ABR. The possible tracks can be obtained from the tracks returned from the method GetTracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetMinBitrate(int playerIndex, int bitrate)
Set a new minimum bitrate (in bits per second) of a specific track. This doesn’t disable ABR. The possible tracks can be obtained from the tracks returned from the method GetTracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void DisableABR(int playerIndex)
Disables the ABR to prevent the player from changing tracks regardless of bandwidth. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected bool IsLive(int playerIndex)
Returns true if a certain stream is a live stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetAdDuration(int playerIndex)
Get the duration of a certain advertisement in milliseconds (ms). The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetAdRemainingTime(int playerIndex)
Get the remaining time of a certain advertisement in milliseconds (ms). The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetAdCurrentTime(int playerIndex)
Get the current time of a certain advertisement in milliseconds (ms). The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetPlaybackSpeedRate(int playerIndex, float speed)
Modify the **speed rate** of a certain stream giving a **playerIndex**. The value of the player's speed must be greater (>) than 0.0f and less than or equal (<=) to 8.0f. The default value of player's speed is 1.0f. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetPlaybackSpeedRate(int playerIndex)
Obtain the **speed rate** of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.
