##三体纯音频SDK发版说明
###2.3.0版本
该版本于2019年8月19日发布。
###新增功能

####伴奏功能，相关接口以及回调
```
/**
 * 调节伴奏本地播放音量。
 *
 * @param volume 伴奏音量范围为0~100。默认50为原始文件音量。
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int adjustAudioMixingPlayoutVolume(int volume);
```

```
/**
 * 调节伴奏远端播放音量。
 *
 * @param volume 伴奏音量范围为0~100。默认50为原始文件音量。
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int adjustAudioMixingPublishVolume(int volume);
```

####外部音频源功能，相关接口以及回调
```
/**
 * 该方法设置是否使用外部音频源。
 *
 * @param enable     是否使用外部音频源。true使用，false不使用
 * @param sampleRate 外部音频源的采样率
 * @param channels   外部音频源的通道数，支持的参数为单声道(1)，双声道(2)
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int setExternalAudioSource(boolean enable, int sampleRate, int channels);
```

```
/**
 * 推送外部音频帧。
 *
 * @param data 外部音频数据。
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int pushExternalAudioFrame(byte[] data);
```

####本地音频录音功能，相关接口以及回调

```
/**
 * 开始客户端录音
 *
 * @param filePath 录音文件的本地保存路径: xxx/.../xxx.aac
 * @param quality  录音质量，类型如下：<br/>
 *                 {@link Constants#TTT_AUDIO_RECORDING_QUALITY_LOW} 低音质。采样率为 48 kHz，码率 16 kpbs，录制 10 分钟的文件大小为 1.2 M 左右。<br/>
 *                 {@link Constants#TTT_AUDIO_RECORDING_QUALITY_MEDIUM} 中音质。采样率为 48 kHz，码率 32 kpbs，录制 10 分钟的文件大小为 2 M 左右。<br/>
 *                 {@link Constants#TTT_AUDIO_RECORDING_QUALITY_HIGH} 高音质。采样率为 48 kHz，码率 64 kpbs，录制 10 分钟的文件大小为 3.75 M 左右。<br/>
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int startAudioRecording(String filePath, int quality);
```

```
/**
 * 停止客户端录音。
 *
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int stopAudioRecording();
```

```
/**
 * 本地音频录音完成通知。
 */
void onAudioRecordFinish();
```

####其他功能，相关接口以及回调
```
/**
 * 设置耳返音量，在打开耳返的情况下有效。
 *
 * @param volume 设置耳返音量，取值范围在 [0,100] 默认值为 100。
 * @return 0代表方法调用成功，其他代表失败。see {@link LocalSDKConstants#FUNCTION_SUCCESS}
 */
public abstract int setAudioEarBackVolume(int volume);
```

```
/**
 * 获取网络连接状态
 *
 * @return 返回当前网络连接状态，类型如下：
 * {@link Constants#TTT_CS_DISCONNECTED} 未加入房间,加入房间失败后，或者离开房间之后。<br/>
 * {@link Constants#TTT_CS_CONNECTING} 加入房间正在建立网络连接。<br/>
 * {@link Constants#TTT_CS_CONNECTED} 网络连接建立成功。<br/>
 * {@link Constants#TTT_CS_RECONNECTING} 网络连接重连中。<br/>
 * {@link Constants#TTT_CS_FAILED} 网络连接失败。<br/>
 */
public abstract int getConnectionState();
```

```
/**
 * 网络连接状态发生改变。
 *
 * @param status 当前网络连接状态
 */
void onConnectionChangedToState(int status);
```

