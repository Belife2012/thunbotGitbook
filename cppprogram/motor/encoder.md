# 编码电机转动

**注意**：编码电机的保护电流为 1A ，当负载很大时，输出功率高于一定水平后会触发保险器件断开，电机就无法正常工作。保险器件被触发后，一般都需要重新开机才能恢复正常。

**常用的 API**：
```cpp
/**
 * @brief: 
 * 
 * @param _select: 0代表left 和 right的控制都起效；1代表left控制起效，right无效; 2代表right控制起效，left无效
 * @param _mode: 0: 无模式；1：控制时间（秒）；2：控制角度（度）；3：控制圈数（圈）
 * @param _data: 控制模式的参数，例如控制时间模式，_data=0.1时，代表控制电机转0.1秒
 * @param _left_speed: 左电机的转动速度
 * @param _right_speed: 右电机的转动速度
 */
void MOTOR_THUNDER::Control_Motor_Running(byte _select, byte _mode, float _data, float _left_speed, float _right_speed)

/**
 * @brief: 控制L、R电机以一定的差速实现小车转向行驶
 * 
 * @param _mode: 0: 无模式；1：控制时间（秒）；2：控制角度（度）；3：控制圈数（圈）
 * @param _data: 控制模式的参数，例如控制时间模式，_data=0.1时，代表控制电机转0.1秒
 * @param _percent: 方向转向程度，取值范围 -100~100
 * @param _speed: L、R电机中最大的转速
 */
void MOTOR_THUNDER::Control_Motor_Turnning(byte _mode, float _data, float _percent, float _speed)

/*
 * 获取电机旋转量
 * 电机编码器磁铁是四对磁极对，减速比是27
 * 编码器的计数器，计算了信号上下沿的数量，所以转一圈，编码器数值为216，实际测量也是
 * 轮子(没有轮胎)周长：16cm
 * 
 * @parameters: 
 * @return: 
 */
int32_t MOTOR_THUNDER::Get_RotateValue(int motor)

/**
 * @brief: 清零电机旋转量记录
 * 
 * @param motor: 电机编号 1 和 2
 */
void MOTOR_THUNDER::Clear_RotateValue(int motor)

/**
 * @brief: 电机闭环刹车，如果电机高速行驶中突然闭环刹车，会引起电机抖动
 * 
 * @param motor:
 */
void MOTOR_THUNDER::Motor_Brake(int motor)

/**
 * @brief: 电机惯性停止
 * 
 * @param motor:
 */
void MOTOR_THUNDER::Motor_Free(int motor)

/**
 * @brief: 电机控制；范围为-255 ~ 255（负数为反向转，正为正向转；没有做速度控制）
 * Set_Motor_Output 仅仅控制电机 PWM 输出，没有其他控制过程
 * 
 * @param motor: 1 是左电机，2 是右电机
 * @param M_output: 范围为-255 ~ 255，电池电压变化时，电机实际输出功率会变化
 */
void MOTOR_THUNDER::Set_Motor_Output(int motor, int M_output)

/**
 * @brief: 开环控制电机，电机功率随电压浮动的范围较小，
 * 在电池电压下降时，会提高电机控制PWM脉宽，保持电机实际输出功率相对稳定
 * 
 * @param motor: 1 是左电机，2 是右电机
 * @param power: 范围为-100 ~ 100，电池电压变化时，会相对于Set_Motor_Output稳定的输出电机功率
 */
void MOTOR_THUNDER::Set_Motor_Power(int motor, int power)

/**
 * @brief: PID闭环控制电机转速，PID控制周期为 MOTOR_CONTROL_PERIOD
 * PID控制周期采集的编码器数值最大为 MAX_DRIVE_SPEED
 * 最大PID控制速度 = MAX_DRIVE_SPEED * 1000 / MOTOR_CONTROL_PERIOD * 60 / ENCODER_NUM_EVERY_CIRCLE
 *                = 277.78(转/分)
 *                = 4.63(转/秒)
 * 
 * @param motor: 电机编号
 * @param target: 最大PID控制速度的百分比
 */
void MOTOR_THUNDER::Set_Target(int motor, float target)

/**
 * @brief: 获取电机速度, 这个数值是电机最大PID控制速度 的 百分比
 * 也可以用于开环控制的场景，获取电机转速
 * 
 * @param motor: 电机接口编号
 * @param times: 默认为0，可以设置计算周期, 周期越长，速度数值实时性差但是数值比较稳定
 * @return int16_t : 电机速度
 */
int16_t MOTOR_THUNDER::Get_Speed(int motor, uint8_t times)
```
<br />

**Tbot I 系统编程示范**
```cpp
    Motor_Thunder.Set_Motor_Power(MOTOR_THUNDER::L, 50);

    // 获取电机转速，显示在屏幕的LED点阵上
    int speed;
    speed = Motor_Thunder.Get_Speed(MOTOR_THUNDER::L, 10);
    Display_Screen.Play_LED_String(speed);
```
<br />

示例程序： `EncodeMotor.ino`
