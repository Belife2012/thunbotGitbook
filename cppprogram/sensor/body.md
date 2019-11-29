# 人体感应

该传感器通过感应人体散发的红外线变化，得知有人经过，一般使用方式都是位置固定安装的。

**注意**：由于其他物体也一样的散发出红外线，所以当其他相当的物体经过传感器前方时，该传感器也会返回“有人经过”；当传感器出现晃动时，也出现跟有人经过时一样的结果。


**常用的 API**：
```cpp

/**
 * @brief: 获取传感器感应结果，如果有人体红外变化（或者其他变化情况），返回1：“有人经过”， 否则返回0
 * 
 * @param sensorChannel: 传感器接口编号
 * @return unsigned char : 有人体红外变化，返回1， 否则返回0
 */
unsigned char SENSOR_HUMAN::GetStatus(uint8_t sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
int body; 
body = Sensor_Human.GetStatus(1);
```
