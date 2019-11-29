# 小型电机转动

小型电机模块可以实现正反转动，模块内置了控制器，数字接口：IIC接口，可以实现连续调速，***连接接口为传感器接口***。模块中没有减速器，可以高速转动，功能灵活，使用简易，满足丰富的应用场景。


**注意**：电机持续处于高速转动时，会容易损坏电机。

**常用的 API**：
```cpp

/**
 * @brief: 设置风扇电机的功率
 * 
 * @param speed: 功率值-100~100，负数表示反转，数值的绝对值越大，电机功率越大
 * @param channel:风扇电机接口的编号：1/2/3/4/5(A)/6(B)
 */
void MOTOR_FAN::Set_Fan_Speed(signed char speed, unsigned char channel)
```
<br />

**Tbot I 系统编程示范**
```cpp
int speed;
speed = 50;
Motor_Fan.Set_Fan_Speed(speed, MOTOR_FAN::PORT_A);// 小型电机模块连接到接口A

```