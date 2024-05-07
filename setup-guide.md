# Setup Guide
Through this guide, you will be introduced to the basic steps for setting up the playback.

## Import Package
First, extract the SDK from the .zip file, copy the **HISPlayer** folder and paste into the **Plugins/** directory in your project’s root (If that directory doesn’t exist, create one).

<p align="center">
<img src="./images/root-dir.png">
</p>

Then, go into the HISPlayer directory and check that the engine version in your **HISPlayer.uplugin** file is the same as your project’s Unreal version. If it's not, change the value. 
The "Engine Version" field will only take into account the major and middle version number (For example, if you are using UE 5.3.2, just add 5.3.0 to that field).
Also make sure that "Android" is added to the PlatformAllowList field. 

<p align="center">
<img src="./images/uplugin-file.png">
</p>

Open your project and go into Edit > Plugins, look for the HISPlayer plugin and if it’s disabled, enable it and restart the project.

<p align="center">
<img src="./images/hisplayer-plugin.png">
</p>

## Set Default Build Settings Version
It is preferable to use the HISPlayer SDK in a C++ project, rather than in an only blueprint one. To create a C++ project from an only blueprint one, go to **Tools > New C++ Class** and follow the indications to create a new one. Any kind of C++ parent class will work.

<p align="center">
<img src="./images/CreateScript.png">
</p>

For UE versions 5.0, 5.1, 5.2 and 5.3 it is necessary to set the DefaultBuildSettings to BuildSettingsVersion.V2. In order to do so, please add the line `DefaultBuildSettings = BuildSettingsVersion.V2;` in the "YourProjectName".Target.cs and "YourProjectName"Editor.Target.cs scripts: 

<p align="center">
<img src="./images/TargetSettings.png">
</p>

## Import HISPlayer_Blueprint
To use HISPlayer’s functionalities in your Level, you need to add the **HISPlayer_Blueprint**. The is located inside **Content Browser > HISPlayer Content > Blueprint**.

<p align="center">
<img src="./images/browser-structure.png">
</p>

If you can’t find the **HISPlayer Content directory** in the Content Browser, check “Show Plugin Content” in “View Options”.

<p align="center">
<img src="./images/show-content.png">
</p>

Add the **HISPlayer_Blueprint**.

<p align="center">
<img src="./images/insert-blueprint.png">
</p>

To render the content, you need to set an actor with **HISPlayer_Material** as Material.

<p align="center">
<img src="./images/add-actor.png">
</p>

You can modify the behavior of the **HISPlayer_Blueprint** as desired or use a custom blueprint, as long as it follows the original structure.

<p align="center">
<img src="./images/graphic.png">
</p>

Use the **HISPlayer API** to add your own implementation.

<p align="center">
<img src="./images/sample.png">
</p>

## License Key
Input the license key that is associated with the SDK. If the license key is not valid, the player won’t work and will throw an error message. To find this field, go to the Level Outliner and look for the HISPlayer_Blueprint actor. Then, on the Details window, look for the HISPlayer section.

<p align="center">
<img src="./images/licensekey.png">
</p>

## Disable Anti-Aliasing
If you are experiencing a ghosting effect on the stream, then you will need to disable the anti-aliasing effect on your project. 
To do that on Unreal 5, go to **Edit > Project Settings > Engine > Rendering > Default Settings > Anti-Aliasing Method** and set it to **None**.

<p align="center">
<img src="./images/AntiAliasing.png">
</p>

## Default Windows Editor RHIs
To use the SDK in the Windows Editor, make sure that the **Default RHIs** option is settled to **DirectX11** or **DirectX12**. Otherwise, go to **Edit > Project Settings > Platforms > Windows > Targeted RHIs**.

<p align="center">
<img src="./images/DefaultRHI.png">
</p>

## Configure Android Project Settings
Please go to  **Edit > Project Settings > Platforms > Android**.

Make sure that you have clicked Configure Android Settings.
<p align="center">
<img src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/a804c07a-1a17-4fe0-8ef5-c3ed0c006930">
</p>

If you are using **HISPlayerSDK version 2.2.0 and above**, both Vulkan and OpenGL ES3 are supported. You can select either Vulkan or OpenGL ES3 or both according to your project requirement. 
<p align="center">
<img src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/78f51424-f796-4097-95f3-49456cde929b">
</p>

If you are using **HISPlayerSDK version 2.1.0 and below**, make sure that only **Support OpenGL ES3** option is enabled, **Vulkan Support** is disabled. 
<p align="center">
<img src="./images/OpenGL.png">
</p>

All the Android Settings must be configurated according to your project needs.

## Packaging the project
Before packaging the project, please make sure first that you are using the right NDK and JDK versions needed for your specific Unreal Engine version. You can check which ones to install on the [official Unreal documentation page](https://docs.unrealengine.com/5.2/en-US/android-development-requirements-for-unreal-engine/) . If you have installed different NDK or JDK versions on your computer, you can always change the ones you are targeting on the **Project Settings > Platforms > Android SDK** menu.

In order to package the project, you need to make sure that **Your_Project.uproject** file has been correctly updated on the **“Plugins”** field:

<p align="center">
<img src="./images/PluginUproject.png">
</p>

You can update this file manually, or by clicking on the Update button when this message appears when opening the project with the plugin installed.

<p align="center">
<img src="./images/Update.png">
</p>

## Updating the SDK

To update a HISPlayer SDK of a previous version, please follow these steps:
* Go to your Root project folder > Plugins and delete the HISPlayer folder.
* Paste your new HISPlayer SDK folder inside the Plugins folder.
* Go again to your Root project folder and delete the Binaries and Intermediate folders.
* Execute Your_Project.uproject file.

Make sure that your project is closed while doing this process.
