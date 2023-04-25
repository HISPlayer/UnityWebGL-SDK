# HISPlayer API

## Public API

The following public APIs are provided by **HISPlayerManager**

* **public List < StreamProperties > multiStreamProperties**: List of properties for multi stream
* **public class StreamProperties**:
  * **public HisPlayerRenderMode renderMode**: Type of texture for rendering. Currently only RenderTexture is supported.
  * **public List < string > url**: List of the URLs for the stream.
  * **public RenderTexture renderTexture**: Reference to the Unity Render Texture.
* **public bool autoPlay**: If true, the players will start playing automatically after set-up.
* **public string licenseKey**: The license key associated with the SDK.
* **public enum HISPlayerRenderMode**: Type of texture for rendering.
    * **RenderTexture**
    * **Material**
    * **RawImage**
* **public enum HISPlayerEvent**: The list of events provided by HisPlayer SDK. You can use the event using the virtual functions in the next section.
  * **HISPLAYER_EVENT_INIT_COMPLETE**
  * **HISPLAYER_EVENT_PLAYBACK_PLAY**
  * **HISPLAYER_EVENT_END_OF_CONTENT**
  * **HISPLAYER_EVENT_ON_TIME**
  * **HISPLAYER_EVENT_PLAYBACK_PAUSE**
  * **HISPLAYER_EVENT_PLAYBACK_STOP**
  * **HISPLAYER_EVENT_PLAYBACK_SEEK**
* **public struct HISPlayerEventInfo**: The information of the triggered event.
  * **public HisPlayerEvent eventType**: The type of the triggered event.
  * **public int playerIndex**: The index of the player where the event is triggered.

## Functions
The following functions are provided by **HISPlayerManager**. They are not public so it’s necessary to create a custom script which inherits from **HISPlayerManager**.

### Virtual functions - These functions can be overriden

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
Override this method to add custom logic when **HisPlayerEvent.HISPLAYER_EVENT_VIDEO_TRACK_CHANGE** is triggered. This event occurs whenever an internal playback has track change.

### Non-virtual functions
These functions can’t be overridden and they can be used only inside the inherited script. If it’s needed to use some of these functions into the Unity scene, for example with buttons, it is needed to create a public function which connects the button with the API.

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
