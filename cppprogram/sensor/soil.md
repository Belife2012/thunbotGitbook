# 土壤湿度

由于带有水分的土壤是电解质，电阻率因水分比例不同而不同，根据这个原理，我们可以检测土壤相对湿度（0~100）。

**注意**：数值稳定后才是正确结果。

**常用的 API**：
```cpp

/**
 * @brief 获取土壤湿度相对值
 * 
 * @param sensorChannel 
 * @return unsigned char 土壤湿度相对值（0~100）
 */
unsigned char SENSOR_SOIL::GetHumidity(unsigned char sensorChannel)

/**
 * @brief 设置土壤湿度检测的最大值和最小值
 * 
 * @param max_value 最大值，取默认最大值的 max_value% 为最大值
 * @param min_value 最小值，取默认最大值的 min_value% 为最小值
 * @param sensorChannel 
 */
void SENSOR_SOIL::SetDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
Sensor_Soil.SetDetectRange(80, 0, 1); // 取默认最大值的80%为最大值

int humidity; // 如需精度更高的数值，可以使用 float 类型
humidity = Sensor_Soil.GetHumidity(1);
```
