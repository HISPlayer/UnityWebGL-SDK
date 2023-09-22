# Import HISPlayer Sample
Please, download the sample here -> [**HISPlayer WebGL Sample**](https://downloads.hisplayer.com/Unity/WebGL/HISPlayerWebGLSample.unitypackage) (no need to download it if you have received it in the email).

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayerUnityWebGLSample.unitypackage**

<p align="center">
<img src="./assets/import-package.png">
</p>

- Complete the configuration for WebGL ->  [**Configure Unity for WebGL**](./setup-guide.md#12-configure-unity-for-webgl)

- Open the scene **Assets/HISPlayerWebGLSample/Scenes/HISPlayerWebGLSample.unity**

<p align="center">
<img src="./assets/webglsample-addscene.PNG" width=50%>
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector Window. **WebGLStreamController** game object -> **HISPlayerWebGLSample** component -> **License Key**

<p align="center">
<img src="./assets/license-key.png">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
<img src="./assets/webglsample-buildsetting.PNG" width=80%>
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerWebGLSample/Scripts/HISPlayerWebGLSample.cs** and **WebGLStreamController GameObject** in the Editor.

## UI Demo
The UI components in the sample scene are fully modifiable. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate features such as play, pause, seek, etc.

<p align="center">
<img src="./assets/webglsample-ui.PNG">
</p>

<p align="center">
<img width="70%" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/928ca4d0-5bfe-4231-a511-63e13292b892">
</p>
