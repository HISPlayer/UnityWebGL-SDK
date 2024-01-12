# Update the SDK

Through this guide, you will be introduced how to update the SDK if you already have installed the SDK previously. Please, restart the Editor before continuing.

## Remove Old Package

Remove the previous HISPlayer SDK package from Unity Package Manager

**Window > Package Manager > Packages - HISPlayer > HISPlayer SDK > Remove**

<p align="center">
  <img width="793" alt="Remove" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/00071022-a78b-4b36-bd1d-eaf64aad49fc">
</p>

<br>

## Import New package

Importing the new package is the same as importing other normal packages in Unity. 
Select the package of HISPlayer SDK and import it.

**Assets > Import Package > Custom Package > HISPlayerSDK.unitypackage**

<p align="center">
<img width="450" src="./assets/import-package.png">
</p>

<br>

## Configure Unity for WebGL

Open the window **Tools > HISPlayer** located in the upper side of the screen > Click on Player Settings Configuration > Select **Build Target to WebGL** > Set all the required settings.

<p align="center">
<img width="314" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/d058e22c-72c7-4f47-bbe5-5389c4d8d72a">
</p>

Copy the **WebGLTemplates** folder from the **HISPlayer** package folder into the **Unity Assets** folder.
<p align="center">
<img width=30% alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/9a4a54c7-bafc-427b-a40b-e3bfc3494fe3">
<img width=30% alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/39784f17-9eb5-4e14-ab14-fbce80580e49">
</p>

Select the **HisPlayerTemplate** by opening **Tools > HISPlayer** and clicking the on **Use WebGL HISPlayer Template**:

<p align="center">
<img width="321" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/609c4938-f3ff-4fd6-a0f6-ea4c5765c1ec">
</p>

## Update License Key
Input the license key that is associated with the SDK through HISPlayer properties. If the license key is not valid, the player won't work and will throw an error message.

License key is not required for Unity Editor.

<p align="center">
<img width="478" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/50b10c75-c6e0-438d-ba1f-da6e66d51eed">
</p>

