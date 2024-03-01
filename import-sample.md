# Import HISPlayer Sample
Please, download the sample here -> [**HISPlayer Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_Sample.unitypackage) (no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_Sample.unitypackage**

<p align="center">
<img src="./assets/import-package.png">
</p>

- Complete the configuration for WebGL ->  [**Configure Unity for WebGL**](./setup-guide.md#12-configure-unity-for-webgl)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayerSample.unity**

<p align="center">
<img width="392" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/daee6484-ac9f-4313-b4d3-857b7d0b3b9a">
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector Window. **StreamController** GameObject -> **HISPlayerSample** component -> **License Key**

<p align="center">
  <img width="475" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/09c245f6-0dfb-44ca-9618-3d1aa7174b14"
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
  <img width="710" alt="AddScene" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/3ae1218a-3478-461f-a27d-f7b0619faefd">
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerSample/Scripts/HISPlayerSample.cs** and **StreamController GameObject** in the Editor.

To change the default video URL using your own URL, go to **StreamController** game object > Inspector Window > HISPlayerSample (Script) > HISPlayer Attributes > MultiStreamProperties > Url > Replace the element value with your own URL.

![image](https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/72f32617-88d6-4d10-b1f6-f44463a60ce0)

## UI Demo
The UI components in the sample scene are fully modifiable. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate features such as play, pause, seek, etc.

<p align="center">
  <img width="196" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/5ca70635-f2e0-4873-863e-d9eaf108255b">
</p>

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/e61b9ade-e10c-424a-ac27-c13055bf0829">
</p>
