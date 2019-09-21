# 湿度探测

该传感器是温度探测传感器，外接了探头，可以延伸到液体、沙子、泥土等等物体中去探测温度。

**注意**：数值稳定后才是正确结果。

**常用的 API**：
```cpp

/**
 * @brief 获取温度
 * 
 * @param sensorChannel 
 * @return float 温度值
 */
float SENSOR_TEMP::GetTemperature(uint8_t sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
int temperature; // 如需精度更高的数值，可以使用 float 类型
temperature = Sensor_Temp.GetTemperature(1);
```

