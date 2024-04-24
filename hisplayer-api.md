# HISPlayer API

## Public API
The following public APIs are provided by **HISPlayerTypes**.
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
  * **OnTrackChanged**: The track of the stream has changed. 
    * **Param1**: Stream's index.
  * **OnInitComplete**: The stream has finished loading process, and its ready to start playing. *(SDK v2.3.0 and above)*
    * **Param1**: Stream's index.
  * **OnSeekComplete**: The stream has finished loading process, and its ready to start playing. *(SDK v2.3.0 and above)*
    * **Param1**: Stream's index. 
<p align="center">
<img src="./images/blueprint-example.png">
</p>

* **public struct HISPlayerTrack** *(SDK v2.3.0 and above)*:
  * **string id**: Id of the track.
  * **int bitrate**: Bitrate of the track in bits per second.
  * **int width**: Width of the track.
  * **int framerate**: Framerate of the track in frames per second.
 
## Functions
Use the following UFunctions in your blueprint or script to make your custom HISPlayer implementation.

#### static void BeginPlay(int numStreams) // HISPlayer BeginPlay
Pre-initialize HISPlayer. You must call this function on BeginPlay before the SetUp.
  * **Param1**: The number of streams to instantiate.

#### static void Setup(int streamIndex, UTexture2D*& outputTexture) // HISPlayer Setup
Initialize HISPlayer. It creates a texture in runtime internally.
  * **Param1**: Stream index.
  * **Param2**: Result texture reference.

#### static int OpenPlayer(int streamIndex, const FString& url) // HISPlayer Open Player
Start HISPlayer. A valid URL must be passed as parameter.
  * **Param1**: Stream index.
  * **Return**: 0 on success.

#### static int OpenPlayerWithDRM(int streamIndex, const FString& url, const FString& keyServerUri, const FString& tokenHeader, const FString& tokenValue) // HISPlayer Open Player With DRM
Start HISPlayer. A valid URL and Key Server URI must be passed as parameter. In the case of using DRM Token, a valid Token Header and Token Value must be passed as well.
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

#### static void Seek(int streamIndex, int msec) // HISPlayer Seek
Seeks the video to a certain position
  * **Param1**: Stream index.
  * **Param2**: Position to seek in miliseconds.

#### static void SetVolume(int streamIndex, float newVolume) // HISPlayer SetVolume
Set Playback volume.
  * **Param1**: Stream index.
  * **Param2**: Must be included in the range [0.0f, 1.0f].

#### static void SetMute(int streamIndex, bool isMute) // HISPlayer SetMute
Mute the current audio.
  * **Param1**: Stream index.
  * **Param2**: True for mute, False for unmute.

#### static int GetCurrentPosition(int streamIndex) // HISPlayer GetCurrentPosition
Returns the current time position of the current track.
  * **Param1**: Stream index.
  * **Return**: Returns the current time position of the current track in miliseconds.

#### static int GetTotalTime(int streamIndex) // HISPlayer GetTotalTime
Returns the total time of the current track.
  * **Param1**: Stream index.
  * **Return**: Returns the current time position of the current track in miliseconds.

#### static void Close(int streamIndex) // HISPlayer Close
Must be called for closing and releasing HISPlayer.
  * **Param1**: Stream index.

#### static void CreateNewTexture(int streamIndex, FIntPoint resolution, UTexture2D*& outputTexture) // HISPlayer Create New Texture 
 Create a new texture of a new resolution for a particular stream. 
  * **Param1**: Stream index.
	 * **Param2**: FIntPoint for resolution. X value for Width, Y value for Height.
	 * **Param3**: Result texture reference.
    
#### static void SetPlaybackProperties(int streamIndex, const FHISPlayerPlaybackProperties& Properties) // HISPlayer Set PlayBack Properties
Set the current playback properties of the stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: PlayerPlaybackProperties type.

#### static int GetVideoHeight(int streamIndex) // HISPlayer Get Video Height
Get the height of the current track of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Return**: Video height.

#### static int GetVideoWidth(int streamIndex) // HISPlayer Get Video Width
Get the width of the current track of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Return**: Video width.

#### static int GetTrackCount(int streamIndex) // HISPlayer Get Track Count
Get the number of tracks of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.

#### static TArray<HISPlayerTrack> GetTracks(int streamIndex) // HISPlayer Get Tracks
Provides information about all the tracks of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
  * **Return**: TArray of HISPlayerTracks.
    
#### static int GetTrackBitrate(int streamIndex, int trackIndex) // HISPlayer Get Track Bitrate
Get the number of tracks of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
  * **Return**: Bitrate of the track.

#### static int GetTrackFramerate(int streamIndex, int trackIndex) // HISPlayer HISPlayer Get Track Framerate
Get the width of a certain track of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
  * **Return**: Framerate of the track.

#### static int GetTrackWidth(int streamIndex, int trackIndex) // HISPlayer Get Track Width
Get the width in pixels of a certain track of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
  * **Return**: Width in pixels of the track.

#### static int GetTrackHeight(int streamIndex, int trackIndex) // HISPlayer Get Track Height
Get the width of a certain track of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
  * **Return**: Height in pixels of the track.

#### static FString GetTrackID(int streamIndex, int trackIndex) // HISPlayer Get Track ID
Get the ID of a certain track of a certain stream. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
  * **Return**: FString of the ID.

#### static void SelectTrack(int streamIndex, int trackIndex) // HISPlayer Select Track
Select a certain track of a certain stream to be used as the main track. The available tracks can be obtained from the tracks returned from the method GetTracks. *(SDK v2.3.0 and above)*
  * **Param1**: Stream index.
  * **Param2**: Track index.
