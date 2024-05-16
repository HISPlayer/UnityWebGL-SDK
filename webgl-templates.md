# WebGL Templates

**Important**: To use the templates feature in WebGL, you need prior knowledge of JavaScript concepts and terminology.

A WebGL template is a configuration setting that lets you control the appearance of the HTML page, so that you can: test, demonstrate, and preview your WebGL application in a browser.

We provide our custom HISPlayerTemplate for you to use our SDK. In the case you want to create your own template, please, refer to [Custom WebGL Template](#custom-webgl-template). 

A WebGL Template is always needed for creating a WebGL application and it will always be stored within **Assets > WebGL Templates** to be used. 
You can refer to [Unity: WebGL Templates](https://docs.unity3d.com/Manual/webgl-templates.html) for more information. 

## HISPlayer Template

The HISPlayer Template folder is located in **Packages > HISPlayer SDK > WebGL Templates > HisPlayerTemplate**. 
In the case you want to use it, please refer to [Configure Unity for WebGL](https://hisplayer.github.io/UnityWebGL-SDK/#/setup-guide?id=_12-configure-unity-for-webgl).

The most important files within HISPlayer Template are:

* HisPlayerTemplate > index.html
* HisPlayerTemplate > hisplayer.js
* HisPlayerTemplate > js > HisPlayerUnity.js

Please, keep in mind that you will always need these files for HISPlayer SDK to work on your project.

<p align="center">
<img width=70% src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/9d87a913-f278-4772-9f8f-3f9c4130c303">
</p>

### Index File

The **index.html** contains the code necessary to load the build. Use this file to modify the entire page where your application will be running. 

The _\<head\>_ is containing the references to *hisplayer.js* and *HisPlayerUnity.js*. 
You can always modify this file, but these references are needed. Otherwise, HISPlayer won't work on your sample.

```html
  <head>
    ...
    <script src="./hisplayer.js"></script>
    <script src="./js/HisPlayerUnity.js"></script>
    ...
  </head>
```

### Custom WebGL Template
It is also possible to create your own template from scratch. The easiest way to create a new custom WebGL template is to make a copy of the built-in Default or Minimal templates,
which are stored in corresponding subfolders under **\<Unity Installation\> > PlaybackEngines > WebGLSupport > BuildTools > WebGLTemplates**.

Every Unity Project includes these templates by default. Copy a template and place it in your own **Assets > WebGLTemplates** folder,
and rename it to something meaningful so you can identify your template later.

Once you have created your own template, please, copy the files *hisplayer.js* and *HisPlayerUnity.js* into your files, open the index.html file and
refer to those files following the previous point [Index.html](#index-file).

The files are located in:

* **Packages > HISPlayer SDK > WebGL Templates > HisPlayerTemplate > hisplayer.js**
* **Packages > HISPlayer SDK > WebGL Templates > HisPlayerTemplate > js > HisPlayerUnity.js**

Finally, open **Edit > Project Settings > Player > Resolution and Presentation** and choose your template. 

<p align="center">
<img width=70% src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/bc6f2f0b-cbee-47b9-95ae-c9cd2d7b1bf3">
</p>

At this point, you can also ignore the error that appears on the _HISPlayer Settings_ related with the **WebGL HISPlayer Template**:

<p align="center">
  <img width=70% src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/5178ee53-7412-478b-9fac-c7e6970ac4e2">
</p>

