# 气体浓度

该气体浓度传感器感应的是可燃气体的相对浓度，传感器上电后需要60秒以上的加热时间。

**注意**：传感器不易长时间处于高浓度的气体环境中，否者会损坏传感器。

**常用的 API**：
```cpp

/**
 * @brief: 获取传感器检测到的气体浓度
 * 
 * @param sensorChannel: 传感器接口编号
 * @return unsigned char : 气体浓度（0~100）
 */
unsigned char SENSOR_GAS::GetToxicgasRatio(unsigned char sensorChannel)

/**
 * @brief: 设置传感器检测的最大值和最小值
 * 
 * @param max_value 最大值，取默认最大值的 max_value% 为最大值
 * @param min_value 最小值，取默认最大值的 min_value% 为最小值
 * @param sensorChannel: 传感器接口编号
 */
void SENSOR_GAS::SetDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
int gas;
Sensor_Gas.SetDetectRange(50, 0, 1); // 最大值设置为默认最大值的50%
gas = Sensor_Gas.GetToxicgasRatio(1);
```
