# 彩色


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
 * @brief: 获取检测结果，可以获取环境光检测结果、反射光检测结果（红、绿、蓝分量），颜色检测结果；
 * 还可以获取颜色模式的数据: HSV数据和RGB数据
 * 
 * @param result_index: 
 * 0|环境光，1|反射红光分量，2|反射绿光分量，3|反射蓝光分量，4|颜色（颜色结果参考SENSOR_COLORLIGHT::enum_Color）
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
 * @brief 设置反射模式检测的范围
 * 
 * @param max_value 最大值
 * @param min_value 最小值
 * @param sensorChannel 
 */
void SENSOR_COLORLIGHT::SetDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)

/**
 * @brief: 复位反射模式的范围设置
 * 
 * @param channel:传感器接口编号 
 */
void SENSOR_COLORLIGHT::Reset(unsigned char channel)
```