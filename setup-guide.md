# Setup Guide
Through this guide, you will be introduced to the basic steps for setting up the playback.

## Import Package
First, extract the SDK from the .zip file, copy the **HISPlayer** folder and paste into the **Plugins/** directory in your project’s root (If that directory doesn’t exist, create one).

<p align="center">
<img src="./images/root-dir.png">
</p>

Then, go into the **HISPlayer** directory and open the **HISPlayer.uplugin** file. You need to check that the **Engine Version** in this file matches the Unreal Engine version of your project.

> ⚠ Don’t worry about the full version number. The **Engine Version** field only cares about the **major** and **minor** version numbers. Ignore the patch number.

Example:
1. Suppose your project uses **Unreal Engine 5.5.4**.  
2. Open **HISPlayer.uplugin**.  
3. Locate the field **"Engine Version"**.  
4. Enter only the **major** and **minor** numbers: `5.5.0`.  
   - ✅ Correct: `5.5.0`  
   - ❌ Incorrect: `5.5.4` (the patch number `.4` will be ignored anyway)  

This ensures that HISPlayer is recognized as compatible with your Unreal Engine project.  

If you are unsure, always use `X.Y.0` where `X` is the major version and `Y` is the minor version of your Unreal Engine.

<p align="center">
<img width="300" height="39" alt="image" src="https://github.com/user-attachments/assets/99731622-62ef-423c-8875-9aff98f5de60" />
</p>

Open your project and go into Edit > Plugins, look for the HISPlayer plugin and if it’s disabled, enable it and restart the project.

<p align="center">
<img width="933" height="121" alt="image" src="https://github.com/user-attachments/assets/ac60e0a0-0625-45ed-9ae0-067ef31b63d3" />
</p>

## Set Default Build Settings Version
It is preferable to use the HISPlayer SDK in a C++ project, rather than in an only blueprint one. To create a C++ project from an only blueprint project, go to **Tools > New C++ Class** and follow the indications to create a new one. Any kind of C++ parent class will work.

<p align="center">
<img src="./images/CreateScript.png">
</p>

Make sure that the "YourProjectName".Target.cs and "YourProjectName"Editor.Target.cs scripts located in the Source directory have the following setup:

<p align="center">
<img width="673" height="535" alt="image" src="https://github.com/user-attachments/assets/a57357b2-2aff-43f5-8c53-4bcbc87ef90f" />
<img width="683" height="552" alt="image" src="https://github.com/user-attachments/assets/a13086a7-5196-438e-9f5b-d643340383df" />
</p>

The HISPlayerSample and HISPlayerVRSample are C++ projects which already include this lines of code so, in case you are using them, you can skip to the next section.

## Import BP_HISPlayer
To use HISPlayer’s functionalities in your Level, you need to add the **BP_HISPlayer**. The is located inside **Content Browser > HISPlayer Content > Blueprint**.

<p align="center">
<img src="./images/browser-structure.png">
</p>

If you can’t find the **HISPlayer Content directory** in the Content Browser, check “Show Plugin Content” in “View Options”.

<p align="center">
<img src="./images/show-content.png">
</p>

Add the **BP_HISPlayer**.

<p align="center">
<img alt="image" src="https://github.com/user-attachments/assets/e6ab4108-7e0c-4a2b-85bb-fc27af38c8e4" />
</p>

To render the content, you need to set an actor with **M_HISPlayerMat** as Material.

<p align="center">
<img alt="image" src="https://github.com/user-attachments/assets/8ddc98d7-77d1-484d-91a0-dfe1a546a54a" />
</p>

## Configure HISPlayer multistream properties
Set the player’s parameters as desired in your **BP_HISPlayer** actor for single stream and multistream.
It is possible to add more than one stream using one instance of the **BP_HISPlayer**, by adding more elements to the Stream URL and Target Actors arrays.

<p align="center">
<img src="./images/playback-props.png">
</p>

You can modify the behavior of the **BP_HISPlayer** as desired or use a custom blueprint, as long as it follows the original structure.

<p align="center">
<img src="./images/graphic.png">
</p>

Use the **HISPlayer API** to add your own implementation.

## License Key

Input the license key that is associated with the SDK. If the license key is not valid, the player won’t work and will throw an error message.

To find this field, go to the Level Outliner and look for the **BP_HISPlayer** actor. Then, in the **Details** window, locate the **HISPlayer** section.

> Note: If you are using the FAB marketplace package, entering a license key is not required.

<p align="center">
<img width="849" height="681" alt="image" src="https://github.com/user-attachments/assets/74e9097f-4ab4-41f9-adf0-570e11995b91" />
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
