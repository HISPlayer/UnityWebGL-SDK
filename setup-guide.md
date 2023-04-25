# Setup Guide
Through this guide, you will be introduced to the basic steps for setting up the playback.

## Import package
Importing the package is the same as importing other normal packages in Unity. Select the package of HISPlayer SDK and import it.
<br>
**Assets > Import Package > Custom Package**

<p align="center">
<img src="./assets/import-package.png">
</p>

<br>

## Configure Unity for WebGL
Once the package is imported, it is time to do some configuration inside Unity.
First of all switch the platform for **WebGL**. Open **File > Build Settings** and then select **WebGL platform** and **switch platform**.

<p align="center">
<img src="./assets/build-settings.png" width="45%"/>
&nbsp; &nbsp; &nbsp; &nbsp;  
<img src="./assets/switch-platform.png" width="45%"/> 
</p>

Inside the previous image in the right there is a button in the bottom left corner to open **Player Settings**. Now inside Player configuration, select **WebGL > Other Settings**. The Color Space can be Gamma or Linear. In the second case, it is needed to disable the **Auto Graphics API** option. 

<p align="center">
<img src="./assets/player-settings.png" width="45%"/>
&nbsp; &nbsp; &nbsp; &nbsp;  
<img src="./assets/linear-space.png" width="45%"/> 
</p>

Select the **HisPlayerTemplate** inside the **Resolution and Presentation** section.

If this option doesn’t appear, then copy the **WebGLTemplates** folder from the **HISPlayer** package folder into the **Unity Assets** folder.
