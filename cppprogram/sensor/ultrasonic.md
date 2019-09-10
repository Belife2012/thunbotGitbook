# 超声波传感器

超声波传感器应用于测量前方障碍物的距离，利用了超声波反射传输的时间来计算超声波行程，传感器返回距离的单位为 cm 。

**测量注意事项**：超声波会因为与物体表面呈现一定夹角而无法检测到反射声波，传感器有效测量距离 3cm ~ 300cm，小于 3cm 时传感器会产生较大误测概率。


**常用的 API**：
```cpp
/**
 * 获取超声波数据[cm]
 * 量程：3.0~300.0
 * 
 * 如果返回300.0，代表超出量程；可能超出最大，可能超出最小
 * 如果返回0.0，则代表无法获取数据，数据无效
 */
float SENSOR_US::Get_Distance(unsigned char channel)
```
<br />

**Tbot I 系统编程示范**
```cpp
    uint16_t distance;
    distance = Sensor_Ultrasonic.Get_Distance(1);

    Serial.printf("Ultrasonic: %d\n", distance);
    Display_Screen.Play_LED_String(distance);
```
<br />

示例程序： `UltrasonicSensor.ino`


