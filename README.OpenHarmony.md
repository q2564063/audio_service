> Template version: v0.0.1

<p align="center">
  <h1 align="center"> <code>audio_service</code> </h1>
</p>

This project is based on [audio_service@0.18.18](https://pub.dev/packages/audio_service/versions/0.18.18).

## 1. Installation and Usage

### 1.1 Installation

Go to the project directory and add the following dependencies in pubspec.yaml

<!-- tabs:start -->

#### pubspec.yaml

```yaml
...

dependencies:
  audio_service:
    git:
      url: https://gitcode.com/openharmony-sig/fluttertpc_audio_service.git
      path: audio_service
      ref: br_v0.18.18_ohos

...
```

Execute Command

```bash
flutter pub get
```

<!-- tabs:end -->

### 1.2 Usage

For use cases [audio_service/example](./audio_service/example/lib/main.dart)

## 2. Constraints

### 2.1 Compatibility

This document is verified based on the following versions:

1. Flutter: 3.27.5-ohos-0.0.1; SDK: 5.0.0(12); IDE: DevEco Studio: 5.1.0.828; ROM: 5.1.0.130 SP8;

## 3. API

> [!TIP] If the value of **ohos Support** is **yes**, it means that the ohos platform supports this property; **no** means the opposite; **partially** means some capabilities of this property are supported. The usage method is the same on different platforms and the effect is the same as that of iOS or Android.

### AudioService API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| cacheManager | Get the cache manager used for loading artwork | property | / | BaseCacheManager | no |
| config | Get the current configuration | property | / | AudioServiceConfig | no |
| notificationClicked | Listen for notification click events | property | / | ValueStream<bool> | no |
| init | Initialize the audio service | function | AudioServiceConfig, AudioHandler | Future<void> | partially |
| start | Start the audio service | function | Map<String, dynamic>? | Future<void> | no |
| stop | Stop the audio service | function | / | Future<void> | yes |

### BaseAudioHandler API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| prepare | Prepare audio resources for playback | function | / | Future<void> | no |
| prepareFromMediaId | Prepare resources by MediaId | function | String | Future<void> | no |
| prepareFromSearch | Prepare resources from a search | function | String, Map? | Future<void> | no |
| prepareFromUri | Prepare resources from a URI | function | Uri, Map? | Future<void> | no |
| play | Start playback | function | / | Future<void> | yes |
| pause | Pause playback | function | / | Future<void> | yes |
| stop | Stop playback | function | / | Future<void> | yes |
| skipToNext | Skip to next track | function | / | Future<void> | yes |
| skipToPrevious | Skip to previous track | function | / | Future<void> | yes |
| fastForward | Fast forward operation | function | / | Future<void> | yes |
| rewind | Rewind operation | function | / | Future<void> | yes |
| skipToQueueItem | Skip to a queue item | function | int | Future<void> | no |
| seek | Seek to specified position | function | Duration | Future<void> | yes |
| setRating | Set rating for media item | function | Rating, Map? | Future<void> | no |
| setCaptioningEnabled | Enable/disable subtitles | function | bool | Future<void> | no |
| setRepeatMode | Set repeat mode | function | AudioServiceRepeatMode | Future<void> | yes |
| setShuffleMode | Set shuffle playback mode | function | AudioServiceShuffleMode | Future<void> | no |
| seekBackward | Begin/end continuous backward seeking | function | bool | Future<void> | no |
| seekForward | Begin/end continuous forward seeking | function | bool | Future<void> | no |
| setSpeed | Set playback speed | function | double | Future<void> | yes |
| customAction | Custom app-specific action | function | String, Map? | Future<dynamic> | no |
| onTaskRemoved | Handle task removal | function | / | Future<void> | no |
| onNotificationDeleted | Handle notification deletion | function | / | Future<void> | no |
| getChildren | Get children of parent media item | function | String, Map? | Future<List<MediaItem>> | no |


### PlaybackState API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| processingState | Audio processing state (buffering/ready/etc.) | enum | / | / | yes |
| playing | Whether audio is playing | bool | / | / | yes |
| controls | Currently enabled media controls | List<MediaControl> | / | / | partially |
| systemActions | System-level actions (e.g. seek bar) | Set<MediaAction> | / | / | partially |
| updatePosition | Last updated playback position | Duration | / | / | yes |
| bufferedPosition | Buffered position | Duration | / | / | no |
| speed | Current playback speed (1.0=normal) | double | / | / | yes |
| updateTime | Last position update time | DateTime | / | / | yes |
| errorCode | Error code when state is error | int? | / | / | no |
| errorMessage | Error message when state is error | String? | / | / | no |
| repeatMode | Current repeat mode | AudioServiceRepeatMode | / | / | yes |
| shuffleMode | Current shuffle mode | AudioServiceShuffleMode | / | / | no |
| captioningEnabled | Whether captioning is enabled | bool | / | / | no |
| queueIndex | Current queue item index | int? | / | / | yes |
| position | Real-time calculated playback position (getter) | Duration | / | / | yes |


### MediaItem API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| id | The unique identifier of the media item | String | / | / | yes |
| title | The title of the media item | String | / | / | yes |
| album | Album information | String? | / | / | yes |
| artist | Artist information | String? | / | / | yes |
| genre | Music genre | String? | / | / | yes |
| duration | Media item duration | Duration? | / | / | yes |
| artUri | Artwork resource path (file://, http://, content://) | Uri? | / | / | partially |
| artHeaders | HTTP headers for artUri requests | Map<String, String>? | / | / | partially |
| playable | Whether the item is playable | bool? | / | / | yes |
| displayTitle | Custom display title override | String? | / | / | yes |
| displaySubtitle | Custom display subtitle override | String? | / | / | yes |
| displayDescription | Custom display description override | String? | / | / | yes |
| rating | Media item rating information | Rating? | / | / | no |
| extras | Extended metadata map | Map<String, dynamic>? | / | / | yes |

## 4. Known Issues

- [ ] ohos audio_service cacheManager, prepare, setShuffleMode, onNotificationDelete and other settings are invalid
- [ ] ohos audio_service init, controls, systemActions, artUri and other settings are only partially supported

## 5. Others

## 6. License

This project is licensed under [The MIT License (MIT)](https://gitcode.com/openharmony-sig/fluttertpc_audio_service/blob/br_v0.18.18_ohos/audio_service/LICENSE).
