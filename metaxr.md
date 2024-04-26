# HISPlayer VR Sample

# Install the Oculus PC app for Meta Quest Link app for Windows

Setup your Meta Quest device on your Windows system, by downloading the app for Meta Quest link. You can follo the official [guide] (https://www.meta.com/help/quest/articles/headsets-and-accessories/oculus-rift-s/install-app-for-link/).


## Integrate Unreal 5 Meta Quest integration

First, please configure your Unreal engine version for Meta Quest by installing the [Unreal 5 Meta Quest Plugin](https://developer.oculus.com/downloads/package/unreal-engine-5-integration/64.0/) SDK into your engine. Make sure that the version you are installing is the correct one for your UE version. Yu can refer to the [Unreal Engine 5.3.2 for Meta Quest VR Setup Guides](https://dev.epicgames.com/community/learning/tutorials/3Vx6/unreal-engine-5-3-2-for-meta-quest-vr).

<p align="center">
<img width="605" alt="image" src="./images/UE5VRIntegration.png">
</p>

## Requirements

#### Meta XR All-in-One version
- Minimal Unreal 5 Meta Quest: 51.0
  
#### Unity version
- Minimal Unreal version: 5.1

#### HISPlayer SDK version
- Minimal HISPlayer SDK version: 2.4.0
  
#### Supported Android Version
- Minor version - Android 12
- Recommended SDK: 32
- Recommended NDK: 25.1.8937393
- Recommended JDK: JDK 11

## Import HISPlayer VR Sample
Please, download the sample here: [**HISPlayer VR Sample**]() (no need to download it if you have received it in the email). 

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Setup Guide](./setup-guide.md).

The HISPlayer VR Sample and the SDK plugin default UE version is 5.1. If you want to update it to a higher UE version, please do the following:
- Right click on the HISPlayerSample.uproject file, select the option "Switch Unreal Engine Version" and select your UE version.
- Update the Plugins/HISPlayer/HISPlayer.uplugin file with the Engine Version you will be using. For more information, refer to the [setup guide](./setup-guide.md).

## Export the project

Once the project is opened, you should be inside the **HISPlayerVRLevel** map. 

<p align="center">
  <img width="100%" alt="image" src="./images/Level.png">
</p>

To build for Meta Quest, you should configure your [Android Platform settings](./setup-guide.md#Configure-Android-Project-Settings).

Then, package the project for the Android Platform, or deploy for your Quest device, in case it is connected to your PC through the Meta Quest Link App.

<p align="center">
  <img width="100%" alt="image" src="./images/package-quest.png">
</p>

## HISPlayer Oculus Controllers
<p align="center">
  <img width="100%" alt="image" src="./images/Meta_Controller.png">
</p>
