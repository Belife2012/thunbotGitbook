# 声音强度

该传感器感应声音的强度，获取声音的相对强度值（0~100）。

**注意**：传感器的灵敏度最高的感应角度为麦克风正前方向，距离越近灵敏度越高。


**常用的 API**：
```cpp

/**
 * @brief 获取声音的相对强度值
 * 
 * @param sensorChannel 
 * @return unsigned char 声音的相对强度值（0~100）
 */
unsigned char SENSOR_SOUND::GetSoundDB(unsigned char sensorChannel)

/**
 * @brief 设置声音强度检测的最大值和最小值
 * 
 * @param max_value 最大值，取默认最大值的 max_value% 为最大值
 * @param min_value 最小值，取默认最大值的 min_value% 为最小值
 * @param sensorChannel 
 */
void SENSOR_SOUND::SetDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
Sensor_Sound.SetDetectRange(100, 10, 1); // 设置声音强度检测的最大值为100和最小值为10

int intensity; 
intensity = Sensor_Sound.GetSoundDB(1);
```



