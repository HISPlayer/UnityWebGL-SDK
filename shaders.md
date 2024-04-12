# Custom Shaders for Linear Color Space
Unity allows you to create [Custom Shaders](https://docs.unity3d.com/Manual/Shaders.html) to improve and generate your own materials 
and graphics. 

We provide examples that simulate the Gamma color space even if you are using Linear color space. The color space plays an important role when rendering the scene and there are differences between Gamma and Linear color spaces 
(refer to this [Unity Manual](https://docs.unity3d.com/Manual/LinearRendering-LinearOrGammaWorkflow.html))
 
If you follow the [Import Sample](https://hisplayer.github.io/UnityWebGL-SDK/#/import-sample) section, please, refer to the GameObject **ScreenRawImage** and check the **Raw Image** component. You
will see there is a material attach to the **material** attribute named **HISPlayerDefaultMaterialRawImage**.

<p align="center">
 <img width="600" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/ecbdc910-7ca4-4e3c-a471-8489e7b36245">
</p>

This material is using the custom shader **HISPlayer/HISPlayerDefaultShaderRawImage**. 
For more details, you can check the following folders and files:

- **Packages/HisPlayerSDK/HisPlayer/Scripts/Shaders/** - Here you can find the custom shaders. These files contain the code to simulate the Gamma color space when using Linear color space.
  - **HISPlayerDefaultShader.shader**
  - **HISPlayerDefaultShaderRawImage.shader**
 
<p align="center">
<img width = "600" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/bdf50347-4c15-4190-a4ac-4a51d5217575">
</p>

- **Packages/HisPlayerSDK/HisPlayer/Resources/Materials/** - Here you can find 3 different Unity materials:
  - **HISPlayerDefaultMaterial.mat**: It uses the **HISPlayerDefaultShader.shader** and can be used for the HISPlayer RenderMode “Material”.
  - **HISPlayerDefaultMaterialRawImage.mat**: It uses the **HISPlayerDefaultShaderRawImage.shader** and can be used attaching the material to the material attribute of the RawImage component.
  - **HISPlayerDefaultMaterialRenderTexture.mat**: It uses the HISPlayerDefaultShader.shader and the HISPlayerDefaultRenderTexture.renderTexture.


<p align="center">
<img width = "600" alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/b2a883a7-3b37-42a7-8418-d034d43ed8a7">
</p>

- **Packages/HisPlayerSDK/HisPlayer/Resources/RenderTextures/**
  - **HISPlayerDefaultRenderTexture.renderTexture** - This file is a custom RenderTexture to be used with the **HISPlayerDefaultMaterialRenderTexture.mat**.

## HISPlayer 360 Shader for Linear Color Space
If you are using **HISPlayer SDK version 3.4.0** and above, you will find **HISPlayer360Shader.shader** in *Packages/com.hisplayer.hisplayersdk/HISPlayer/Scripts/Shaders/*.
<p align="center">
  <img width="70%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/e95a25a0-82ca-4c7b-b27b-e5ea3a84ae84">
</p>

When building 360 application, you might use different shaders such as the Unity Skybox/Panoramic shader.

If you use Linear Color Space, please change the default shader to HISPlayer360Shader which will improve the video rendering quality by following these steps : 
* Open your 360 material, for example: Assets/HISPlayerOculusSample/Resources/RenderTextures/Materials/HISPlayer_360_Material.mat
<p align="center">
  <img width="70%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/2e32d3c3-86b9-4bc2-829a-e1750a8524ba">
</p>

* In the Inspector window, change Shader to HISPlayer360Shader
<p align="center">
  <img width="60%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/a981eb80-d2e6-4c99-8ba6-201d4ca615a9">
</p>

* Make sure you have the following setting of the material:
<p align="center">
  <img width="60%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/5ba12394-cc6a-4846-b7fc-4a682669dd66">
</p>
