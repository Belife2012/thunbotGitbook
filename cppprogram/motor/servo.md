# 舵机转动

**常用的 API**：
```cpp
/**
 * @brief: 控制舵机旋转位置
 * 
 * @param servo: 舵机接口编号（A:1  B:2）
 * @param percent: 舵机旋转范围内的旋转百分比（正数为最大值方向的百分比，负数为最小值方向的百分比）
 * @param speed: 控制速度时会阻塞直到转到固定位置，参数数值范围 0 ~ 100 
 */
void MOTOR_SERVO::Servo_Turn_Percent(int servo, float percent, float speed)

/**
 * @brief: 设置舵机旋转范围（初始值为 -100 ~ 100）
 * 
 * @param servo_index: 舵机接口编号（A:1  B:2）
 * @param max_value: 范围最大值，默认 100
 * @param min_value: 范围最小值，默认 -100
 * @param zero_value: 范围零点，默认 0
 * @param direction: 默认为1，当 < 0 时 最小值与最大值互换
 */
void MOTOR_SERVO::Servo_Percent_Setting(int servo_index, float max_value, float min_value, float zero_value, int direction)
```
<br />

**Tbot I 系统编程示范**
```cpp
    delay(2000);
    Motor_Servo.Servo_Turn_Percent(1, -100); // 没有控制速度时，不产生阻塞
    Motor_Servo.Servo_Turn_Percent(2, -100);

    delay(2000);
    Motor_Servo.Servo_Turn_Percent(1, -100, 10); // 控制速度时会阻塞直到转到固定位置
    Motor_Servo.Servo_Turn_Percent(2, -100, 10);
```
<br />

示例程序： `ServoMotor.ino`