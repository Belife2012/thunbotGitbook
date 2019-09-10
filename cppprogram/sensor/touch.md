# 触碰传感器

触碰传感器用于检测机械碰撞按压的情景，使用 `Get_Event` 获取三种事件：释放状态（0）、按下状态（1）、按下后释放（2）；触碰传感器上有一个RGB彩灯，可以通过 `Set_LED_RGBvalue` 设置灯光颜色和亮度，默认情况下，释放状态亮绿灯，按下状态亮红灯；`Check_Event` 检测事件有没有发生。


**常用的 API**：
```cpp
/* 
 * 获取触碰传感器事件
 * 
 * @parameters: 
 * @return: 
 *      0 未按下状态（释放状态）
 *      1 按下状态
 *      2 按下后释放（触碰）
 */
int SENSOR_TOUCH::Get_Event(uint8_t sensorChannel)

/* 
 * 检查触碰按键的相关按键事件是否有发生
 * 
 * @parameters: 
 * @return: true是有发生过，false是未发生过
 */
bool SENSOR_TOUCH::Check_Event(int check_event, unsigned char channel)

/* 
 * 设置触碰模块的LED灯颜色，范围 0-255
 * 
 * @parameters: 全部传入0 值时，即为关闭LED灯
 *      RedValue LED亮度的红色分量，范围 0-255
 *      GreenValue LED亮度的绿色分量，范围 0-255
 *      BlueValue LED亮度的蓝色分量，范围 0-255
 * @return: 
 *      0 写数据正常
 *      非0 写数据出错
 */
byte SENSOR_TOUCH::Set_LED_RGBvalue(byte RedValue, byte GreenValue, byte BlueValue, unsigned char channel)

/* 
 * 复位灯光模式：自动模式，释放状态亮绿灯，按下状态亮红灯
 * 
 * @parameters: 
 * @return: 
 */
byte SENSOR_TOUCH::Reset_Mode(unsigned char channel)

```
<br />

**Tbot I 系统编程示范**
```cpp
    uint16_t status;
    status = Sensor_Touch.Get_Event(1);

    Serial.printf("Touch Status: %d\n", status);
    Display_Screen.Play_LED_String(status);
```
<br />

示例程序： `TouchSensor.ino`
