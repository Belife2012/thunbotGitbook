# 空气温湿度

该传感器是温度、湿度一体的传感器，检测空气中温度和相对湿度。


**常用的 API**：
```cpp

/**
 * @brief: 获取温湿度传感器的相对湿度
 * 
 * @param sensorChannel:传感器接口编号
 * @return float : 湿度相对值（0~100）
 */
float SENSOR_HT::GetHumidity(uint8_t sensorChannel)

/**
 * @brief: 获取温湿度传感器的温度值
 * 
 * @param sensorChannel:传感器接口编号
 * @return float :温度（摄氏度℃）
 */
float SENSOR_HT::GetTemperature(uint8_t sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
int humidity; // 如需精度更高的数值，可以使用 float 类型
int temperature; // 如需精度更高的数值，可以使用 float 类型
humidity = Sensor_HumTemp.GetHumidity(1);
temperature = Sensor_HumTemp.GetTemperature(1);
```

