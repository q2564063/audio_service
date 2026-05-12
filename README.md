> 模板版本: v0.0.1

<p align="center">
  <h1 align="center"> <code>audio_service</code> </h1>
</p>

本项目基于 [audio_service@0.18.18](https://pub.dev/packages/audio_service/versions/0.18.18) 开发。

## 1. 安装与使用

### 1.1 安装方式

进入到工程目录并在 pubspec.yaml 中添加以下依赖：

<!-- tabs:start -->

#### pubspec.yaml

```yaml
---
dependencies:
  audio_service:
    git:
      url: https://gitcode.com/openharmony-sig/fluttertpc_audio_service.git
      path: audio_service
      ref: br_v0.18.18_ohos
```

执行命令

```bash
flutter pub get
```

<!-- tabs:end -->

### 1.2 使用案例

使用案例详见 [audio_service/example](./audio_service/example/lib/main.dart)

## 2. 约束与限制

### 2.1 兼容性

在以下版本中已测试通过

1. Flutter: 3.27.5-ohos-0.0.1; SDK: 5.0.0(12); IDE: DevEco Studio: 5.1.0.828; ROM: 5.1.0.130 SP8;

## 3. API

> [!TIP] "ohos Support"列为 yes 表示 ohos 平台支持该属性；no 则表示不支持；partially 表示部分支持。使用方法跨平台一致，效果对标 iOS 或 Android 的效果。

### AudioService API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| cacheManager | 获取缓存管理器 | property | / | BaseCacheManager | no |
| config | 获取当前配置 | property | / | AudioServiceConfig | no |
| notificationClicked | 监听通知点击事件 | property | / | ValueStream<bool> | no |
| init | 初始化音频服务 | function | AudioServiceConfig, AudioHandler | Future<void> | partially |
| start | 启动音频服务 | function | Map<String, dynamic>? | Future<void> | no |
| stop | 停止音频服务 | function | / | Future<void> | yes |


### BaseAudioHandler API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| prepare | 准备播放资源 | function | / | Future<void> | no |
| prepareFromMediaId | 通过MediaId准备资源 | function | String | Future<void> | no |
| prepareFromSearch | 通过搜索准备资源 | function | String, Map? | Future<void> | no |
| prepareFromUri | 通过URI准备资源 | function | Uri, Map? | Future<void> | no |
| play | 开始播放 | function | / | Future<void> | yes |
| pause | 暂停播放 | function | / | Future<void> | yes |
| stop | 停止播放 | function | / | Future<void> | yes |
| skipToNext | 跳转下一曲 | function | / | Future<void> | yes |
| skipToPrevious | 跳转上一曲 | function | / | Future<void> | yes |
| fastForward | 快进操作 | function | / | Future<void> | yes |
| rewind | 快退操作 | function | / | Future<void> | yes |
| skipToQueueItem | 跳转到队列某项 | function | int | Future<void> | no |
| seek | 跳转到指定位置 | function | Duration | Future<void> | yes |
| setRating | 设置评分 | function | Rating, Map? | Future<void> | no |
| setCaptioningEnabled | 设置字幕启用状态 | function | bool | Future<void> | no |
| setRepeatMode | 设置重复模式 | function | AudioServiceRepeatMode | Future<void> | yes |
| setShuffleMode | 设置随机播放模式 | function | AudioServiceShuffleMode | Future<void> | no |
| seekBackward | 持续快退 | function | bool | Future<void> | no |
| seekForward | 持续快进 | function | bool | Future<void> | no |
| setSpeed | 设置播放速度 | function | double | Future<void> | yes |
| customAction | 自定义动作 | function | String, Map? | Future<dynamic> | no |
| onTaskRemoved | 任务被移除时处理 | function | / | Future<void> | no |
| onNotificationDeleted | 通知被删除时处理 | function | / | Future<void> | no |
| getChildren | 获取子媒体项 | function | String, Map? | Future<List<MediaItem>> | no |


### PlaybackState API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| processingState | 音频处理状态（缓冲/就绪等） | enum | / | / | yes |
| playing | 是否正在播放 | bool | / | / | yes |
| controls | 当前可用的媒体控件 | List<MediaControl> | / | / | partially |
| systemActions | 系统级操作（如拖动进度条） | Set<MediaAction> | / | / | partially |
| updatePosition | 最后更新的播放位置 | Duration | / | / | yes |
| bufferedPosition | 已缓冲的位置 | Duration | / | / | no |
| speed | 当前播放速度（1.0为正常） | double | / | / | yes |
| updateTime | 上次更新时间 | DateTime | / | / | yes |
| errorCode | 错误代码（当processingState为error时） | int? | / | / | no |
| errorMessage | 错误信息（当processingState为error时） | String? | / | / | no |
| repeatMode | 当前重复模式 | AudioServiceRepeatMode | / | / | yes |
| shuffleMode | 当前随机模式 | AudioServiceShuffleMode | / | / | no |
| captioningEnabled | 字幕是否启用 | bool | / | / | no |
| queueIndex | 当前队列索引 | int? | / | / | yes |
| position | 实时计算的播放位置（getter） | Duration | / | / | yes |


### MediaItem API

| Name | Description | Type | Input | Output | ohos Support |
|------|-------------|------|-------|--------|--------------|
| id | 媒体唯一标识 | String | / | / | yes |
| title | 媒体标题 | String | / | / | yes |
| album | 专辑信息 | String? | / | / | yes |
| artist | 艺术家信息 | String? | / | / | yes |
| genre | 音乐类型 | String? | / | / | yes |
| duration | 媒体时长 | Duration? | / | / | yes |
| artUri | 封面资源路径 | Uri? | / | / | partially |
| artHeaders | HTTP请求头 | Map<String, String>? | / | / | partially |
| playable | 是否可播放 | bool? | / | / | yes |
| displayTitle | 自定义显示标题 | String? | / | / | yes |
| displaySubtitle | 自定义显示副标题 | String? | / | / | yes |
| displayDescription | 自定义显示描述 | String? | / | / | yes |
| rating | 媒体评分信息 | Rating? | / | / | no |
| extras | 扩展元数据 | Map<String, dynamic>? | / | / | yes |



## 4. 遗留问题

- [ ] ohos 端 audio_service  cacheManager, prepare,setShuffleMode,onNotificationDelete 等设置使用无效
- [ ] ohos 端 audio_service init,  controls, systemActions, artUri等仅部分支持

## 5. 其他

## 6. 开源协议

本项目基于 [The MIT License (MIT)](https://gitcode.com/openharmony-sig/fluttertpc_audio_service/blob/br_v0.18.18_ohos/audio_service/LICENSE) ，请自由地享受和参与开源。
