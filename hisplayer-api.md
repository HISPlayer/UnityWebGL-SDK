# HISPlayer API

## Public API

The following public APIs are provided by **HISPlayerManager**

* **public List <StreamProperties> multiStreamProperties**: List of properties for multi stream. Any change to the property member must be set before calling SetupPlayer(), otherwise it will not have effect.

* **public class StreamProperties**:
  * **public HisPlayerRenderMode renderMode**: Type of texture for rendering.
  * **public List < string > url**: List of the URLs for the stream.
  * **public RenderTexture renderTexture**: Reference to the Unity Render Texture.
  * **public Material material**: Reference to the Unity Material.
  * **public RawImage rawImage**: Reference to the Unity RawImage.
  * **public List <AdsProperties> adsProperties**: List of properties to configure advertisement insertions for each player in the scene.
  * **public int manifestTimeout**: The manifest request connection timeout, in milliseconds. Zero means unlimited. Defaults to 10000 milliseconds.
  * **public int segmentsTimeout**: The segments requests connection timeout, in milliseconds. Zero means unlimited. Defaults to 5000 milliseconds.

* **public bool autoPlay**: If true, the players will start playing automatically after set-up.

* **public string licenseKey**: The license key associated with the SDK.

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


* **public enum HISPlayerEvent**: The list of events provided by HisPlayer SDK. You can use the event using the virtual functions in the next section.
  * **HISPLAYER_EVENT_INIT_COMPLETE**
  * **HISPLAYER_EVENT_PLAYBACK_PLAY**
  * **HISPLAYER_EVENT_END_OF_CONTENT**
  * **HISPLAYER_EVENT_ON_TIME**
  * **HISPLAYER_EVENT_PLAYBACK_PAUSE**
  * **HISPLAYER_EVENT_PLAYBACK_STOP**
  * **HISPLAYER_EVENT_PLAYBACK_SEEK**
  * **HISPLAYER_EVENT_AD_BLOCK_STARTED**
  * **HISPLAYER_EVENT_AD_BLOCK_ENDY**
  * **HISPLAYER_EVENT_AD_STARTED**
  * **HISPLAYER_EVENT_AD_STOPPED**
  * **HISPLAYER_EVENT_AD_PODS_INFO**

* **public struct HISPlayerEventInfo**: The information of the triggered event.
  * **public HisPlayerEvent eventType**: The type of the triggered event.
  * **public int param1**: This will have different meanings depending on the event.
  * **public int param2**: This will have different meanings depending on the event.
  * **public int param3**: This will have different meanings depending on the event.
  * **public int playerIndex**: The index of the player where the event is triggered.

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

#### protected virtual void EventInitComplete(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_INIT_COMPLETE** is triggered.
This event occurs whenever the internal system of the player has been set up.

#### protected virtual void EventPlaybackPlay(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PLAY** is triggered.
This event occurs whenever an internal playback has been played

#### protected virtual void EventEndOfContent(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_END_OF_CONTENT** is triggered.
This event occurs whenever an internal playback reaches the end of the video content.

#### protected virtual void EventOnTime(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_ON_TIME** is triggered.
This event occurs once per second.

#### protected virtual void EventPlaybackPause(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PAUSE** is triggered.
This event occurs whenever an internal playback has been paused.

#### protected virtual void EventPlaybackStop(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_STOP** is triggered.
This event occurs whenever an internal playback has been stopped.

#### protected virtual void EventPlaybackSeek(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_SEEK** is triggered.
This event occurs whenever an internal playback has finished seeking.

#### protected virtual void EventVideoTrackChange (HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_VIDEO_TRACK_CHANGE** is triggered. This event occurs whenever an internal playback has a track change.

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

#### protected virtual void EventAdBlockStarted(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_BLOCK_STARTED** is triggered. This event occurs whenever a group of advertisements starts.

#### protected virtual void EventAdBlockEnd(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_BLOCK_END** is triggered. This event occurs whenever a group of advertisements ends.

#### protected virtual void EventAdStarted(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_STARTED** is triggered. This event occurs whenever a single advertisement starts.

#### protected virtual void EventAdStopped(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_STOPPED** is triggered. This event occurs whenever a single advertisement ends.

#### protected virtual void EventAdPodsInfo(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_AD_PODS_INFO** is triggered. This event occurs whenever there is an advertisement pods information indicating cue points of ad breaks.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Start cue point of ad break in milliseconds</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>End cue point of ad break in milliseconds</td>
  </tr>
</table>

### Non-virtual functions
These functions can’t be overridden and they can be used only inside the inherited script. If it’s needed to use some of these functions in the Unity scene, for example with buttons, it is needed to create a public function that connects the button with the API.

#### protected void SetUpPlayer()
Initialize the player video stream system internally. It is necessary to use this function before anything else.

#### protected void Release()
Free all resources internally.

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

#### protected HisPlayerTrack[] GetTracks(int playerIndex)
Get the track information of a certain stream fiving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackBitrate(int playerIndex, int trackIndex)
Get the bitrate of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackWidth(int playerIndex, int trackIndex)
Get the width of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackHeight(int playerIndex, int trackIndex)
Get the height of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 of the list.

#### protected int GetTrackID(int playerIndex, int trackIndex)
Get the ID of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackCount(int playerIndex)
Get the number of tracks of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetTrack(int playerIndex, int trackIndex)
Set the track to be used.  Using this disables ABR. The possible tracks can be obtained from the tracks returned from the method **GetTracks**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void DisableABR(int playerIndex)
Disables the ABR to prevent the player from changing tracks regardless of bandwidth. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void EnableABR(int playerIndex)
Enables the ABR to change automatically between tracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetCurrentTime(int playerIndex)
Get the playback's current time of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetDuration(int playerIndex)
Get the duration of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected bool IsLive(int playerIndex)
Returns true if a certain stream is a live stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void ChangeVideoContent(int playerIndex, string url)
Change video content at run time of a certain stream. The **url** is the new content that will be running on the stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public void SetLogLevel(LogLevel logLevel)
Establishes the number of logs to be shown. The log levels are represented as an enum of integers, so every type of log whose representative integer is greater or equal to the established log level will be shown. The log levels to be used are (0 : DEBUG, 1 : INFO, 2 : WARNING, 3 : ERROR, 4 : NONE)

#### protected float GetAdDuration(int playerIndex)
Get the duration of a certain advertisement in milliseconds (ms). The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetAdRemainingTime(int playerIndex)
Get the remaining time of a certain advertisement in milliseconds (ms). The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetAdCurrentTime(int playerIndex)
Get the current time of a certain advertisement in milliseconds (ms). The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void ChangeVideoContent(int playerIndex, string url, int resumePosition, AdsProperties ads)
Change video content at run time of a certain stream. The **url** is the new content that will be running on the stream. The **resumePosition** is time position in milliseconds (ms) where the new content is starting the playback, default value is 0. The **AdsProperties** is an ads properties to use when loading the new content, default value is null. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.
