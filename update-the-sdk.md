# Update the SDK

Through this guide, you will be introduced how to update the SDK if you already have installed the SDK previously.

## Remove Old Package

Remove the previous HISPlayer WebGL SDK package from Unity Package Manager

**Window > Package Manager > Packages - HISPlayer > HISPlayer WebGL SDK > Remove**

<p align="center">
<img width="700" src="./assets/remove-package-webgl.PNG">
</p>

<br>

## Import New package

Importing the new package is the same as importing other normal packages in Unity. 
Select the package of HISPlayer SDK and import it.

**Assets > Import Package > Custom Package > HISPlayerWebGLSDK unity package**


<p align="center">
<img width="450" src="./assets/import-package.png">
</p>

<br>

## Configure Unity for WebGL
Once the package is imported, please follow below steps.

Copy the **WebGLTemplates** folder from the **HISPlayer** package folder into the **Unity Assets** folder. This should replace the old template.
<p align="center">
<img src="./assets/webgl.png" width="45%" height="50%"/>
&nbsp; &nbsp; &nbsp; &nbsp;  
<img src="./assets/webgl-assets.png" width="45%" height="50%"/> 
</p>

Select the **HisPlayerTemplate** inside the **Player Settings** > **Resolution and Presentation** section.
<p align="center">
<img src="./assets/resolution-presentation.png"/>
</p>

## Update License Key
Input the license key that is associated with the SDK through HISPlayer properties. If the license key is not valid, the player won't work and will throw an error message.

<p align="center">
<img width="400" src="./assets/license-key.png">
</p>
