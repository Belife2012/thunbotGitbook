# 电机转动

Tbot I 目前支持了多种电机：编码电机、舵机、小型电机，编码电机能够进行多种控制，开环控制，闭环控制，可以自主实现控制算法进行个性化的控制；舵机能实现固定位置的控制，启动后自动恢复到固定位置，Tbot I 功能库为大家提供舵机转速控制的API，更方便的应用。

舵机接口连接的接口编号是 1：接口A，2：接口B，可以直接使用`MOTOR_SERVO::A` 和 `MOTOR_SERVO::B`表示舵机接口A和舵机接口B。

编码电机连接的接口编号是 1：接口L，2：接口R，可以直接使用`MOTOR_THUNDER::L` 和 `MOTOR_THUNDER::R` 表示电机接口L和电机接口R。

小型电机连接的接口编号是传感器接口，1|接口1，2|接口2，3|接口3，4|接口4，5|接口A，6|接口B，为了方便记忆，可以直接使用MOTOR_FAN::PORT_1，MOTOR_FAN::PORT_2，MOTOR_FAN::PORT_3，MOTOR_FAN::PORT_4，MOTOR_FAN::PORT_A，MOTOR_FAN::PORT_B。