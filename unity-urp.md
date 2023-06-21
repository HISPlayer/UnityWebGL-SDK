# URP (Universal Render Pipeline)
The Universal Render Pipeline (URP) is a prebuilt Scriptable Render Pipeline, made by Unity. URP provides artist-friendly workflows that let you 
quickly and easily create optimized graphics.

### Installing URP
Unity provides a template creating a URP Project. You can create both 2D and 3D scene with URP. Otherwise, you will need to install the *Universal RP* package from from **Window > Package Manager > Packagges: Unity Registry** and then set your own [Render Pipeline](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@7.1/manual/configuring-universalrp-for-use.html).

<p align="center">
<img width="600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/9bfdc177-e79b-4a87-929b-cfc858ab2e74">
</p>

### Using *Universal Render Pipeline/Lit* Material
After setting up correctly the URP, you can create a Material in the Assets folder and select different shaders. You can try with *Universal Render PipeLine/Lit* shader. 

Attach the material to a GameObject (you can try with a simple cube), create a Render Texture and attach it to the *Base Map* attribute from the material. 

Finally, attach the created Render Texture to the Multi Stream Properties in the Editor (more information in [**Configure HISPlayer Properties**](./setup-guide.md#Configure-HISPlayer-properties)) and play the scene.

|<img width="363" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/0a80a410-cc1b-44c7-8c87-c05c0429a94f">|<img width="361" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/a89815f2-cc97-49d1-a8f7-dd0bf2c81f30">|
|-|-|

### Trying other shaders
The created RenderTexture will work with the rest of the shaders provided by URP, but not all of them are useful for playing a stream or a normal video (it depends on the objective of the project), because they have different attributes and combinations. For using the render texture in other shaders, please make sure that the RenderTexture is attached in the correct places. Otherwise it may not work as expected. Also some shaders could have effect to other shaders.

If you try with **Universal Render Pipeline/Particles/Lit** , it's possible to attach the RenderTexture to the *BaseMap* attribute. 
Nevertheless, if you change the color in this shader, it is going to affect the **Universal Render Pipeline/Lit** color as well.

With the rest of the shaders is almost the same, because they all have different settings and the way of attaching a RenderTexture to them could change.

|<img width="363" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/0dbfd019-2bc8-452f-90a4-1d865f3a4f95">|<img width="363" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/589b3c4a-ed3a-4f23-8bc2-7e4a955a76cf">|
|-|-|
