# Import HISPlayer Sample

Please, download the sample here -> [**HISPlayer Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_Sample.unitypackage) 
(no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_Sample.unitypackage**

<p align="center">
<img width=50% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/95592ff6-8467-4137-9eda-d9cd3b387acb">
</p>

- Complete the configuration for WebGL ->  [**Configure Unity for WebGL**](./setup-guide.md#12-configure-unity-for-webgl)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayerSample.unity**

<p align="center">
  <img width=60% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/0c4b5314-d835-4e56-879c-6d48c16312b2">
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector. **HISPlayerController** GameObject -> **HISPlayerController** component -> **License Key**

<p align="center">
  <img width=80% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/f99d01df-847e-4289-9a33-364ce9210e53">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
  <img width=70% alt="webgl-settings" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/b0cd1caf-e3fc-4c9c-beeb-80c9b477ef58">
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerSample/Scripts/HISPlayerController.cs** and **HISPlayerController GameObject** in the Editor.

## MultiStream UI Demo
The UI components in the sample scene are fully modifiable and each stream has its own UI. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate features such as play, pause, seek, etc using the multi stream feature. 

<p align="center">
  <img width=55% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/312e37e7-aff3-4537-8dc3-d5843b86441c">
</p>

<p align="center">
  <img width=90% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/640453d1-8a58-45cf-9260-c659cb308655">
</p>

## Add/Remove Streams and URLs
In order to add/remove streams and URLs, please refer to the component **HISPlayerMultiStreamController** attached to the **HISPlayerMultiStreamController GameObject** in the **Inspector**. 

### Add/Remove Streams

You can add/remove streams by pressing the buttons **+/-** in the **Multi Stream Properties list**. Once a new stream is added, please, select the render mode and the surface where you want to display your videos (Material, Raw Image or RenderTexture). 

<p align="center">
  <img width=70% alt="streams" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/f0a1521d-807a-48f5-893e-58135516b37e">
</p>

<p align="center">
  <img width=70% alt="render-mode" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/e65f23af-cf95-4858-b654-d0199feecd71">
</p>

### Change URL
To change the default video URL using your own URL, please replace the element value with your own URL in the **URL list** of the stream you want to modify.

<p align="center">
  <img width=60% alt="replace-url" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/5b876db4-f3c9-4c98-84df-f23737070f50">
</p>

### Add/Remove URLs

You can add/remove URLs by selecting one element from the **Multi Stream Properties list** and then pressing the buttons **+/-** in the **Url list**. For changing the content of the videos, please refer to **[ChangeVideoContent](https://hisplayer.github.io/UnityWebGL-SDK/#/hisplayer-api?id=protected-void-changevideocontentint-playerindex-int-urlindex-int-resumeposition-0-adsproperties-ads-null)** API.

<p align="center">
  <img width=70% alt="add-url" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b65bf99f-202b-436e-a9c3-f1a6b9b97eaa">
</p>

