# OpenXR Plugin / Meta Quest Set Up Guide

## OpenXR Plugins

You need to enable the OpenXR plugins. Go to **Edit > Plugins**, search for and enable the following:

- `OpenXR`
- `OpenXREyeTracker`
- `OpenXRHandTracking`

<p align="center">
  <img 
    alt="image" 
    src="https://github.com/user-attachments/assets/0d578793-dcb2-4bbd-915c-83d800a993ee"
    style="max-width: 100%; height: auto;"
  />
</p>

The `HISPlayerVRSample` is a C++ project which already includes this lines of code so, in case you are using it, you can skip to the next section.

## HISPlayer VR Sample
### Download the Sample
Please, download the sample here: [**HISPlayer VR Sample**](https://downloads.hisplayer.com/Unreal/AllPlatforms/HISPlayerVRSample_1.0.4_AllPlatforms.zip) (no need to download it if you have received it in the email).

### Import HISPlayer SDK
Please use HISPlayer SDK v2.2.0 and above with **Vulkan** support.

If you have not imported HISPlayer SDK yet, please follow the [Setup Guide](./setup-guide.md).
Extract the SDK from the .zip file, copy the `HISPlayer` folder and paste into the `HISPlayerVRSample\Plugins` directory.

### Using the Sample
The HISPlayer VR Sample default UE version is 5.5. If you want to update it to a higher UE version, please do the following:
- Right click on the `HISPlayerVRSample.uproject` file, select the option **"Switch Unreal Engine Version"** and select your UE version.

Open `HISPlayerVRSample.uproject`.

### Available Levels
Once the project is opened, you should be inside the `HISPlayerVRLevel` map. You can select other levels from `Content Browser > HISPlayerResources > Levels`:
- `HISPlayerVRLevel`
- `HISPlayerVRLevelMultistream`

### Sample Description
The HISPlayer VR Sample is made based on the Unreal Engine [Virtual Reality Template](https://dev.epicgames.com/documentation/en-us/unreal-engine/vr-template-in-unreal-engine?application_version=5.3)

The important UI components are located in `HISPlayerVRSample\Content\HISPlayerResources\UI`:
- `HISPlayer_UI.uasset`: Widget Blueprint of the video playback control UI
- `HISPlayer_UI_Actor.uasset`: Blueprint class to place the `HISPlayer_UI` widget to VR space. The `HISPlayer_UI` is attached as a widget component.
- `HISPlayer_UI_OnClick.uasset`: Represents an abstract game action for `HISPlayer_UI` that can be mapped to Meta Quest left and right hand controllers 

<p align="center">
  <img alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/f8ea1676-89c7-4bf0-a6f7-e1c57291c764">
</p>

The HISPlayer UI components are connected to the default VRTemplate's device input action mapping (`IMC_Default`) and Blueprint class (`VRPawn`):
- `HISPlayerVRSample\Content\VRTemplate\Input\IMC_Default.uasset`: The `HISPlayer_UI_OnClick` is mapped in this input mapping context asset. It represents the Meta Quest left and right hand controllers input action for `HISPlayer_UI`.
<p align="center">
  <img alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/62b5a0d8-720d-4cba-8de5-790a715a88ed">
</p>

- `HISPlayerVRSample\Content\VRTemplate\Blueprints\VRPawn.uasset`: a Pawn is the physical representation of the user and defines how the user interacts with the virtual world. In the VR Template, the Pawn contains the logic for input events from the motion controllers. You can also control the behavior of Meta Quest left and right hand controller through `WidgetInteractionLeft` and `WidgetInteractionRight`. The Blueprint also controls the UI interaction with the Meta Quest left and right hand controllers emulating the left-mouse click. 
<p align="center">
  <img alt="image" src="https://github.com/HISPlayer/UnrealAndroid-SDK/assets/32887298/77e24f0b-32b8-4ea9-a22c-6c98b2582ece">
</p>
