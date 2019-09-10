# 播放声音

Tbot I 的喇叭`Speaker_Thunder`内置了丰富的声音，包括了音符、吉他和弦、英语、汉语、机器声、动物声和一些功能声音，各种声音的编号定义在 `SPEAKER_THUNDER::enum_speaker` 里面。

**常用的 API**：
```cpp
/**
 * @brief 物理上音量有15档，此函数输入有效范围 0~100 
 * 
 * @param data：最大音量的百分比
 */
void SPEAKER_THUNDER::Set_Sound_Volume(int data)

/**
 * @brief: 播放声音
 * 
 * @param data: 歌曲的地址编号，
 * 例如 音符A音调0的编号，可以使用 SPEAKER_THUNDER::SOUND_MUSIC_A0 来代表 
 */
void SPEAKER_THUNDER::Play_Song(int data)
```
<br />

**Tbot I 系统编程示范**
```cpp
Speaker_Thunder.Set_Sound_Volume(100);
Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C5);
```
<br />

示例程序： `Speaker.ino`
