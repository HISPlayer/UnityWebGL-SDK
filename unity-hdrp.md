# Unity HDRP (High Definition Render Pipeline)

HDRP is a plugin of Unity for using several options of shader with high definition and it's available in the **Window > Package Manager > Packages: Unity Registry**. 

It is also possible to create a project directly with HDRP:

<img width="762" alt="image" src="https://github.com/HISPlayer/UnityWindows-SDK/assets/47497948/8b4f284c-fde0-4533-9f9b-bd2c69a0de8d">

After installing the HDRP, you will be able to create the material with the attached Render Texture following the same steps from [Render Texture](https://hisplayer.github.io/UnityWebGL-SDK/#/setup-guide?id=configure-hisplayer-properties)

<img width="762" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/fbdf3cdd-991f-4884-a720-6af9c93a1e23">

This process will create a material with the shader **HDRP/Lit** with the RenderTexture attached to the *Base Map* attribute as you can see in the following screenshot:

<img width="762" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/8d00c6f3-5500-4eaf-8e21-50153dd06ac1">

Attach the created Render Texture to the *Multi Stream Properties* in the Editor (more information in [Configure HISPlayer properties](https://hisplayer.github.io/UnityWebGL-SDK/#/setup-guide?id=multi-stream-properties)) and play the scene.

## Trying other shaders

The created RenderTexture will work with all the shaders provided by HDRP, but not all of them are useful for playing a stream or a normal video (it depends on the objective of the project), because they have different attributes and combinations.

For using the render texture in other shaders, you must be sure that the RenderTexture is attached in the correct places. Otherwise it may don't work as expected or don't work at all. Also some shaders could have effect to other shaders, so for example, if you try with **HDRP/Fabric/CottonWool** it's possible to attach the RenderTexture to the *NormalMap* attribute disabling the *Use Thread Map*.

<img width="762" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/1c47e961-5d4e-4a91-9ab2-89563ffdd10f">

Nevertheless, this is going to affect the **HDRP/Lit**. If you put **HDRP/Lit** again, after using **HDRP/Fabric/CottonWool**, you will see the effects by playing the scene.

In the case of **HDRP/3DSMaxPhysicalMaterial/PhysicalMaterial3DsMax**, the RenderTexture can be attached to the *BaseColorMap* attribute, so it will render the content of the playback. 

<img width="762" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/3df85d79-acb2-4578-a895-f0022432eaae">

With the rest of the shaders is almost the same, because they all have different settings and the way of attaching a RenderTexture to them could change.
