# Unity HDRP (High Definition Render Pipeline)

### Installing HDRP
HDRP is a plugin of Unity for using several options of shader with high definition and it's available in the **Window > Package Manager > Packages: Unity Registry**. 

It is also possible to create a project directly with HDRP:

<p align="center">
<img width="762" alt="image" src="https://github.com/HISPlayer/UnityWindows-SDK/assets/47497948/8b4f284c-fde0-4533-9f9b-bd2c69a0de8d">
</p>


### Creating HDRP/Lit Material

After installing the HDRP, you will be able to create the material with the attached Render Texture following the same steps from  [**Render Texture**](./setup-guide.md#RenderTexture)

This process will create a material with the shader **HDRP/Lit** with the RenderTexture attached to the *Base Map* attribute. 

Finally, attach the created Render Texture to the *Multi Stream Properties* in the Editor (more information in [**Configure HISPlayer Properties**](./setup-guide.md#Configure-HISPlayer-properties)) and play the scene.

<p align="center">
<img width="700" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/fbdf3cdd-991f-4884-a720-6af9c93a1e23">
</p>

|<img width="400" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/8d00c6f3-5500-4eaf-8e21-50153dd06ac1">|<img width="400" alt="image" src="https://github.com/HISPlayer/UnityWindows-SDK/assets/47497948/3b61ee4e-bd2b-476f-9202-79275b27550c">|
|-|-|

## Trying other shaders
The created RenderTexture will work with all the shaders provided by HDRP, but not all of them are useful for playing a stream or a normal video (it depends on the objective of the project), because they have different attributes and combinations. For using the render texture in other shaders, please make sure that the RenderTexture is attached in the correct places. Otherwise it may not work as expected. Also some shaders could have effect to other shaders.

### Example 1
If you try with **HDRP/Fabric/CottonWool** , it's possible to attach the RenderTexture to the *NormalMap* attribute and disable the *Use Thread Map*.
Nevertheless, this is going to affect the **HDRP/Lit**. If you put **HDRP/Lit** again, after using **HDRP/Fabric/CottonWool**, you will see the effects by playing the scene.

<p align="center">
<img width="500" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/1c47e961-5d4e-4a91-9ab2-89563ffdd10f">
</p>

### Example 2
In the case of **HDRP/3DSMaxPhysicalMaterial/PhysicalMaterial3DsMax**, the RenderTexture can be attached to the *BaseColorMap* attribute, so it will render the content of the playback. 

With the rest of the shaders is almost the same, because they all have different settings and the way of attaching a RenderTexture to them could change.

<p align="center">
<img width="500" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/3df85d79-acb2-4578-a895-f0022432eaae">
</p>


