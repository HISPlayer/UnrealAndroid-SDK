# HISPlayer API

## Public API
The following public APIs are provided by **HISPlayerManager**.

* **enum class HISPlayerStatus**: The different status in which the stream can be settled:
  * **NONE**
  * **CLOSE**: The stream is closed.
  * **STOP**: The content is stopped.
  * **PLAY**: The content is playing.
  * **PAUSE**: The content is paused.

* **struct FHISPlayerPlaybackProperties**: Use these properties to change the playback’s behavior from the editor.
  * **bool bAutoplay**: The content will automatically play after buffering is complete.
  * **bool bLooping**: The content will automatically loop after it ends.
  * **bool bMute**: The content audio will be muted.

* **public class UDelegateManager**: Use this delegate to receive the different HISPlayer events.
  * **OnLoading**: The content starts loading.
    * **Param1**: Stream's index.
  * **OnPlay**: The content starts playing.
    * **Param1**: Stream's index.
  * **OnPause**: The content pauses.
    * **Param1**: Stream's index.
  * **OnStop**: The content stops.
    * **Param1**: Stream's index.
  * **OnEndContent**: The content ends.
    * **Param1**: Stream's index.
  * **OnBuffering (float percentage)**: The content is buffering.
    * **Param1**: Stream's index. 
    * **Param2**: The current percentage of the buffering process.
  * **OnStatusChanged**: The HISPlayer Status has changed.
    * **Param1**: Stream's index. 
  * **OnTrackChanged**: The track of the stream has changed. 
    * **Param1**: Stream's index. 
  * **OnError**: The track of the stream has changed.
    * **Param1**: Stream's index. 
<p align="center">
<img src="./images/blueprint-example.png">
</p>

## Functions
Use the following UFunctions in your blueprint or script to make your custom HISPlayer implementation.

#### static void BeginPlay(int numStreams) // HISPlayer BeginPlay
Pre-initialize HISPlayer. You must call this function on BeginPlay before the SetUp.
  * **Param1**: The number of streams to instantiate.
 
#### static void Setup(int streamIndex, UTexture2D*& outputTexture) // HISPlayer Setup
Initialize HISPlayer. It creates a texture in runtime internally.
  * **Param1**: Stream index.
  * **Param2**: Result texture reference.
 
#### static void SetPlayBackProperties (int streamIndex, const FHISPlayerPlaybackProperties& Properties) // HISPlayer Set PlayBack Properties
Set the playback properties.
  * **Param1**: Stream index.
  * **Param2**: HISPlayer playback properties to set.

#### static FHISPlayerPlaybackProperties& GetPlaybackProperties(int streamIndex) // HISPlayer Set PlayBack Properties
Get the current playback properties.
  * **Param1**: Stream index.
  * **Return**: The actual stream's HISPlayer playback properties.
  
#### static int OpenPlayer(int streamIndex, const FString& url) // HISPlayer Open Player
Start HISPlayer. A valid URL must be passed as parameter.
  * **Param1**: Stream index.
  * **Return**: 0 on success.

#### static void Update(int streamIndex) // HISPlayer Update
Update each frame, needs to be called every frame.
  * **Param1**: Stream index.

#### static void Resume(int streamIndex) // HISPlayer Resume
Update each frame, needs to be called every frame.
  * **Param1**: Stream index.

#### static void Pause(int streamIndex) // HISPlayer Pause
Pause the video.
  * **Param1**: Stream index.

#### static void Stop(int streamIndex) // HISPlayer Stop
Stop the video and, next time it's played, it will begin from start.
  * **Param1**: Stream index.

#### static void Close(int streamIndex) // HISPlayer Close
Must be called for closing and releasing HISPlayer.
  * **Param1**: Stream index.

#### static void CreateNewTexture(int streamIndex, FIntPoint resolution, UTexture2D*& outputTexture) // HISPlayer Create New Texture 
 Create a new texture of a new resolution for a particular stream.
  * **Param1**: Stream index.
	 * **Param2**: FIntPoint for resolution. X value for Width, Y value for Height.
	 * **Param3**: Result texture reference.
