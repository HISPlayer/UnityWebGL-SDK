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
<p align="center">
<img src="./assets/resolution-presentation.png"/>
</p>

If this option doesn’t appear, then copy the **WebGLTemplates** folder from the **HISPlayer** package folder into the **Unity Assets** folder.
<p align="center">
<img src="./assets/webgl.png" width="45%" height="50%"/>
&nbsp; &nbsp; &nbsp; &nbsp;  
<img src="./assets/webgl-assets.png" width="45%" height="50%"/> 
</p>

## Setup HISPlayer Manager
Create a script (for example **WebGLStreamController**) which is going to inherit from **HisPlayerManager**. It is needed to include the namespace by adding **‘using HisPlayerAPI;’** and add this component to a GameObject. It is recommended to create an **Empty GameObject** for this.
<br>
Now it’s time to call the **‘SetUpPlayer()’** function in order to initialize the stream environment internally. This function can be called whenever it’s needed, so it could be from the beginning of with an input.
<br>
For example, using the Awake function:
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using HisPlayerAPI;

public class WebGLStreamController : HisPlayerManager
{
    protected override void Awake()
    {
        base.Awake();
        SetUpPlayer();
    }
}
```
It is strictly necessary to use **SetUpPlayer** before using anything else, because this function will initialize everything from the SDK in order to be able to use the rest of the functions (Play, Pause, Seek…).
