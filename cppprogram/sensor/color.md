# 颜色

颜色传感器根据反射光的RGB成分来判别颜色，识别的颜色种类：0|无（传感器前方没有色卡）、1|红、2|黄、3|绿、4|蓝、5|棕、6|白、7|黑，可以使用枚举变量 enum_Color_Card 来方便记忆，例如：`SENSOR_COLOR::CARD_WHITE`。除了内置的颜色识别，还可以分别读取RGB分量的数值，自主编写颜色识别算法。

**注意**：颜色传感器在白光环境下使用才能保证其识别的准确度。


**常用的 API**：
```cpp
/**
 * @brief: 获取颜色传感器检测到的色卡颜色
 * 
 * @param sensorChannel:传感器接口编号
 * @return uint8_t :色卡颜色编号: 0|无（传感器前方没有色卡）、1|红、2|黄、3|绿、4|蓝、5|棕、6|白、7|黑
 */
uint8_t SENSOR_COLOR::Get_Color_Result(uint8_t sensorChannel)

/**
 * @brief: 获取颜色（红色）分量
 * 
 * @param channel: 传感器接口编号
 * @return uint16_t : R颜色分量
 */
uint16_t SENSOR_COLOR::Get_Red(uint8_t channel) 

/**
 * @brief: 获取颜色（绿色）分量
 * 
 * @param channel: 传感器接口编号
 * @return uint16_t : G颜色分量
 */
uint16_t SENSOR_COLOR::Get_Green(uint8_t channel) 

/**
 * @brief: 获取颜色（蓝牙）分量
 * 
 * @param channel: 传感器接口编号
 * @return uint16_t : B颜色分量
 */
uint16_t SENSOR_COLOR::Get_Blue(uint8_t channel) 

```
<br />

**Tbot I 系统编程示范**
```cpp
int value;

value = Sensor_Color.Get_Color_Result(1);
switch(value)
{
    case SENSOR_COLOR::CARD_NO: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C0);
        break;
    case SENSOR_COLOR::CARD_RED: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C1);
        break;
    case SENSOR_COLOR::CARD_BROWN: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C2);
        break;
    case SENSOR_COLOR::CARD_YELLOW: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C3);
        break;
    case SENSOR_COLOR::CARD_GREEN: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C4);
        break;
    case SENSOR_COLOR::CARD_BLUE: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C5);
        break;
    case SENSOR_COLOR::CARD_WHITE: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C6);
        break;
    case SENSOR_COLOR::CARD_BLACK: 
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C7);
        break;
    default: break;
}
```
<br />

示例程序： `ColorSensor.ino`