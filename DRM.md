# DRM

In the video streaming industry, the DRM (Digital Rights Management) makes possible a secure distribution of contents over the network.
Encrypted content is prepared using an encryption server and stored in a content library. The encrypted content is streamed or downloaded 
from the content library to client devices via content servers. Licenses to view the content are obtained from the License Server.

The HISPlayer Unreal SDK for Android supports [Widevine DRM](https://www.widevine.com/solutions/widevine-drm). Only Widevine with security L3 is supported.
It is also possible to add another level of protection with DRM tokens, using a token header and a token value.

It is possible to add the URL, the Key Server URI and the tokens from the Editor. Please, refer to the **HISPlayer_Blueprint** located in 
**Plugins > HISPlayer Content > Blueprint > HISPlayer_Blueprint**

<p align="center">
<img width=80% alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/47497948/97908896-3c80-47af-ad21-fa4e9cad8ada">
</p>

Parameters:

* **Enable DRM**: Check to enable DRM usage. When enabled, there should be a Key Server URI and/or a Token Header and a Token Value associated
  to the URL that is going to be used. In the case of non-DRM content, please disable this parameter.

* **Key Server URI**: The license URL key associated to an URL. **Enable DRM** must be true to make it work

* **DRM Tokens**:  If your key server needs more information, add DRM tokens for DRM-protected contents alongside the respective Key Server URI.
   The tokens are composed of a Header and a Value. **Enable DRM** must be true and a **Key Server URI** must be provided to make it work.

You can see these fields in the Unreal window "Details" under the component **HISPlayer > DRM (Platform: Android)**. In the case you're using a 
custom blueprint, please refer to the function [**OpenPlayerWithDRM**](https://hisplayer.github.io/UnrealAndroid-SDK/#/hisplayer-api?id=functions).

<p align="center">
<img width=60% alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/47497948/b42f22e1-93a4-46fd-b3f2-a33743abd226">
</p>
