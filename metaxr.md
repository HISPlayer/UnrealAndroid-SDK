# Meta XR Plugin / Meta Quest Set Up Guide

## Requirements

#### Meta XR Plugin version
- Minimum Meta XR Plugin: 51.0
  
#### Unreal version
- Minimum Unreal version: 5.1

#### HISPlayer SDK version
- Minimum HISPlayer SDK version: 2.4.0
  
#### Supported Android Version
- Minor version - Android 12
- Recommended SDK: 32
- Recommended NDK: 25.1.8937393
- Recommended JDK: JDK 11

## Install the Oculus PC app for Meta Quest Link app for Windows

Setup your Meta Quest device on your Windows system, by downloading the app for Meta Quest link. You can follow the [official guide](https://www.meta.com/help/quest/articles/headsets-and-accessories/oculus-rift-s/install-app-for-link/).

You may also use [Meta Quest Developer Hub](https://developer.oculus.com/documentation/unity/ts-odh/).

## Unreal 5 and Meta XR Plugin Integration

First, please configure your Unreal engine version for Meta Quest by installing the [Unreal 5 Meta XR Plugin](https://developer.oculus.com/downloads/package/unreal-engine-5-integration/64.0/) into your engine. Make sure that the version you are installing is the correct one for your UE version.

<p align="center">
<img width="605" alt="image" src="./images/UE5VRIntegration.png">
</p>

You can refer to any of the following guides for the Meta XR Plugin set-up for your project:
- [Creating Your First Meta Quest VR App in Unreal Engine](https://developer.oculus.com/documentation/unreal/unreal-quick-start-guide-quest/)
- [Unreal Engine 5.3.2 for Meta Quest VR Setup Guides](https://dev.epicgames.com/community/learning/tutorials/3Vx6/unreal-engine-5-3-2-for-meta-quest-vr) .

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Setup Guide](./setup-guide.md).

The HISPlayer SDK plugin default UE version is 5.1. If you want to update it to a higher UE version, please do the following:
- Update the Plugins/HISPlayer/HISPlayer.uplugin file with the Engine Version you will be using. For more information, refer to the [setup guide](./setup-guide.md).

## Using HISPlayer VR Sample
Please, download the sample here: [**HISPlayer VR Sample**]() (no need to download it if you have received it in the email). 

The HISPlayer VR Sample default UE version is 5.1. If you want to update it to a higher UE version, please do the following:
- Right click on the HISPlayerSample.uproject file, select the option "Switch Unreal Engine Version" and select your UE version.

Once the project is opened, you should be inside the **HISPlayerVRLevel** map. 

<p align="center">
  <img width="100%" alt="image" src="./images/Level.png">
</p>

To build for Meta Quest, you should configure your Android platform setting by following official guide from Meta: [Configure the Project for Meta Quest Development](https://developer.oculus.com/documentation/unreal/unreal-quick-start-guide-quest/#configure) or follow below steps:

- Go to Edit > Plugins and select the Virtual Reality section.
- Enable the Meta XR plugin.

<p align="center">
  <img width="100%" alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/b556773d-a5f8-41ed-9351-a4c4dfabacc5">
</p>

- Choose restart editor on the prompt.
- Select the Meta XR tools button then Project Setup Tool to open the Project Setup Tool.
<p align="center">
  <img width="100%" alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/737e3e7b-1f61-46a6-b095-af9392b5d459">
</p>

- Select Apply All for Required and Recommended Rules for all devices you are targeting.
<p align="center">
  <img width="100%" alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/4afb7f6c-b788-4a26-bc18-2a129ba73acf">
</p>

- Restart the editor after applying settings. Note: This may require multiple restarts after applying a setting.

Then, package the project for the Android Platform, or deploy for your Quest device, in case it is connected to your PC through the Meta Quest Link App.
<p align="center">
  <img width="100%" alt="image" src="./images/package-quest.png">
</p>
