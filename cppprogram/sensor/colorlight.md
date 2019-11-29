# 彩色

彩色传感器采用了RGB三色灯作为信号灯光，光电传感器件感应环境光和反射光，通过分析反射光得知色卡颜色。该传感器可以用于很多光学实验中，激发用户更多的相关灵感。

传感器可以通过 `Set_Operate_Mode` 选择工作在某种模式下：0|环境光模式、1|反射模式、2|颜色模式。

* `环境光模式` 时蓝灯会亮起， `Get_Result` 可以测量传感器前方光强程度，0代表比较暗的环境，100代表检测到很强的光；
* `反射模式` 时默认红灯会亮起，可以通过 `Set_Reflect_Led` 设置信号灯颜色，而且 `Get_Result` 获取检测结果时还可以分别获取RGB分量的反射光相对强度，使用 `SetDetectRange` 可以设置检测范围最大值和最小值，缩小范围时可以提升检测精度；
* `颜色模式` 时RGB灯都会亮起， `Get_Result` 可以获得颜色编号（颜色结果编号参考SENSOR_COLORLIGHT::enum_Color），还可以获取HSV颜色空间数据（H：0~360，S/V：0~100）和RGB数据（0~100）

**常用的 API**：
```cpp

/**
 * @brief: 设置工作模式
 * 
 * @param optMode:设置工作模式，SENSOR_COLORLIGHT::enum_Mode，0|环境光模式，1|反射模式，2|颜色模式
 * @param channel:传感器接口编号
 * @return byte :返回0表示成功，否则失败
 */
byte SENSOR_COLORLIGHT::Set_Operate_Mode(byte optMode, unsigned char channel)

/**
 * @brief: 获取检测结果，可以获取环境光模式的检测结果、反射光模式的检测结果（红、绿、蓝分量），
 * 颜色模式的检测结果，还可以获取颜色模式的数据: HSV数据和RGB数据；
 * 
 * @param result_index: 
 * 0|环境光，1|反射红光分量，2|反射绿光分量，3|反射蓝光分量，
 * 4|颜色（颜色结果参考SENSOR_COLORLIGHT::enum_Color 0~8分别代表 无颜色/黑/白/红/黄/绿/青/蓝/紫）
 * 10|H值，11|S值，12|V值，13|R值，14|G值，15|B值
 * @param channel:传感器接口编号
 * @return int :返回的检测数据结果
 */
int SENSOR_COLORLIGHT::Get_Result(unsigned char result_index, unsigned char channel)

/**
 * @brief: 设置工作模式为反射模式，并设置反射模式的灯光
 * 
 * @param optData:设置反射模式的灯光，相应的bit=1表示灯亮，否则为灯灭，bit0|红，bit1|绿，bit2|蓝
 * 0x01|红亮，绿灭，蓝灭
 * 0x03|红亮，绿亮，蓝灭
 * 0x05|红亮，绿灭，蓝亮
 * 0x07|红亮，绿亮，蓝亮
 * 0x02|红灭，绿亮，蓝灭
 * 0x06|红灭，绿亮，蓝亮
 * 0x04|红灭，绿灭，蓝亮
 * @param channel:传感器接口编号
 * @return byte :返回0表示成功，否则失败
 */
byte SENSOR_COLORLIGHT::Set_Reflect_Led(byte optData, unsigned char channel)

/**
 * @brief: 校准传感器的最大值或最小值
 * 
 * @param mode: 0 设置值为反射光最大值，1 设置值为反射光最小值, 2 重置反射光设置值
 *              3 设置值为环境光最大值，4 设置值为环境光最小值, 5 重置环境光设置值
 * @param value: 新设置的数值（0~100）
 * @param sensorChannel: 传感器接口编号
 */
void SENSOR_COLORLIGHT::Set_Extremum(int mode, float value, uint8_t channel)

/**
 * @brief 设置反射光模式检测的范围
 * 
 * @param max_value 最大值
 * @param min_value 最小值
 * @param sensorChannel 
 */
void SENSOR_COLORLIGHT::SetReflectDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)

/**
 * @brief 设置环境光模式检测的范围
 * 
 * @param max_value 最大值
 * @param min_value 最小值
 * @param sensorChannel 
 */
void SENSOR_COLORLIGHT::SetEnvDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)

/**
 * @brief: 复位传感器的反射光最大最小值设置，环境光最大最小值设置
 * 
 * @param channel:传感器接口编号 
 */
void SENSOR_COLORLIGHT::Reset(unsigned char channel)
```
<br />

**Tbot I 系统编程示范**
```cpp
int work_mode = 0;
int result;
// 环境光模式
if (work_mode != 3)
{
    Sensor_ColorLight.Set_Operate_Mode(SENSOR_COLORLIGHT::MODE_ENV, channel);
    work_mode = 3;
}
result = Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::RESULT_ENV, channel);
Serial.printf("env: %d\n", result); // 通过log窗口显示出来

// 反射模式
if (work_mode != 1)
{ 
    // Sensor_ColorLight.SetDetectRange(50, 0, channel); // 设置范围
    Sensor_ColorLight.Set_Operate_Mode(SENSOR_COLORLIGHT::MODE_REFLECT, channel);
    Sensor_ColorLight.Set_Reflect_Led(0x07, channel); // RGB全亮
    work_mode = 1;
}
reslut = Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::RESULT_REFLECT_R, channel);
Serial.printf("R: %d\n", result); // 通过log窗口显示出来
reslut = Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::RESULT_REFLECT_G, channel);
Serial.printf("G: %d\n", result); // 通过log窗口显示出来
reslut = Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::RESULT_REFLECT_B, channel);
Serial.printf("B: %d\n", result); // 通过log窗口显示出来

// 颜色模式
if (work_mode != 2)
{
    Sensor_ColorLight.Set_Operate_Mode(SENSOR_COLORLIGHT::MODE_COLOR, channel);
    work_mode = 2;
}
result = Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::RESULT_COLOR, channel);
Serial.printf("Color: %2d\n", result);

Serial.printf("data: %3d %3d %3d %3d %3d %3d",  \
Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::DATA_HSV_H, channel), \
Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::DATA_HSV_S, channel), \
Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::DATA_HSV_V, channel), \
Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::DATA_COLOR_R, channel), \
Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::DATA_COLOR_G, channel), \
Sensor_ColorLight.Get_Result(SENSOR_COLORLIGHT::DATA_COLOR_B, channel)); // 通过log窗口显示HSV数据和 RGB数据

```
