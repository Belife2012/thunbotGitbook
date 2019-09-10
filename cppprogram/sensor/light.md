# 光线

光线传感器用于检测光亮度，返回 100 以内的数值，代表检测到光线的强度，默认情况下，传感器不亮灯，直接调用 `Get_Light_Value` 检测环境中光线到传感器的强度。由于白色比黑色的反射光更强，传感器点亮灯光 `Set_Operate_Mode` ，照射物体后检测光线强度，可以分辨出黑白 或者 其他反射光强度不同的情况。根据这个原理，光线传感器可以应用于巡线、光源跟踪等等场景。

**注意**：使用发射光模式时，可以根据实际情况调整传感器安装距离，安装距离不一样，照射出来的光斑不同，一般使用距离是5mm ~ 20mm。


**常用的 API**：
```cpp
/**
 * @brief: 获取光电传感器相对数值（0~100）
 * 
 * @param channel: 传感器接口编号
 * @return float : 返回值
 */
float SENSOR_LIGHT::Get_Light_Value(unsigned char channel )

/* 
 * 设置光电传感器的模式
 * 
 * @parameters: 
 *      LED亮灯可设置等级为 0 ~ 100，可以设置对应的LED亮度等级，用于不同模式
 * @return: 
 *      0 写数据正常
 *      非0 写数据出错
 */
byte SENSOR_LIGHT::Set_Operate_Mode(byte optMode,unsigned char channel)

/**
 * @brief: 设置光电传感器的最大值或最小值
 * 
 * @param mode: 0 设置值为最大值，1 设置值为最小值
 * @param value: 新设置的数值（0~100）
 * @param sensorChannel: 传感器接口编号
 */
void SENSOR_LIGHT::Set_Extremum(int mode, float value, uint8_t sensorChannel)

/**
 * @brief 设置光线检测的最大值和最小值
 * 
 * @param max_value 最大值
 * @param min_value 最小值
 * @param sensorChannel 
 */
void SENSOR_LIGHT::SetDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)
```
<br />

**Tbot I 系统编程示范**
```cpp
    Sensor_Light.Set_Operate_Mode(100, 1);
    Sensor_Light.Set_Extremum(0, 25, 1); // 设置最大值
    
    int light_value;
    light_value = Sensor_Light.Get_Light_Value(1);
    Serial.printf("light: %d\n", light_value);
```
<br />

示例程序： `DoubleTask.ino`

