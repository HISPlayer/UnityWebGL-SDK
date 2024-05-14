# Audio Autoplay

Audio will not play in WebGL without having interaction with the web page due to [browser autoplay policy](https://developer.chrome.com/blog/autoplay/). 
You need to call [SetVolume() API](https://hisplayer.github.io/UnityWebGL-SDK/#/hisplayer-api?id=protected-void-setvolumeint-playerindex-float-volume) after you interact with the screen.

You may refer to [HISPlayer Sample](https://hisplayer.github.io/UnitySamples/#/hisplayer-sample). After building the project for WebGL, we interact first with the web page by clicking the "Start" button. 
Then, **SetVolume** API is called through the script **HISPlayerController.cs** after interacting with the web page.

<p align="center">
<img width="70%" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/32887298/e34becf1-6c3c-4213-99b5-70cde41e5dc4">
</p>


