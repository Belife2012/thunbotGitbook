# 初识Tbot-I C++编程

本章主要介绍一些Tbot-I 相关的 C++ 基础知识，扩展阅读请参考相关教材。

## 命名规则
* 类名称全部大写，实例名称的首字母大写。枚举变量、类方法使用的是类名，调用函数使用的是实例名称。

## 传入数据与返回数据
* 一般的传感器返回数据是整型数据，一般使用 `int` 数据类型即可，要获得更大范围的整型数据使用无符号类型`uint32_t`。同时有一些传感器可以返回浮点数，可以使用`float`数据类型变量存储该传感器的返回值。

## API使用说明
* 有一部分传感器有设置检测范围（也称为`校准`）的API，例如声音强度传感器中的 `SetDetectRange(unsigned char max_value, unsigned char min_value, unsigned char sensorChannel)` ，max_value传入最大值，min_value传入最小值，这里最大值最小值指的是对传感器检测范围进行调整，检测最大范围改为默认检测范围时的`max_value`，检测最小范围改为默认检测范围时的`min_value`，例如：没有设置检测范围时，假设检测120分贝的声音时结果为100，检测90分贝的声音时结果为50，检测70分贝的声音时结果为20，当 `Sensor_Sound.SetDetectRange(50, 20, 1);` 后，检测120分贝的声音时结果为100，检测90分贝的声音时结果为100，检测70分贝的声音时结果为0；


## Tbot-I系统编程模板
```cpp
#include <bell_thunder.h>

/*************************************************************
 * @brief: thunder系统相关配置
 *************************************************************/
void setup()
{
    Bell_Thunder.Setup_All();
    Bell_Thunder.Set_Ble_Type(BLE_TYPE_CLIENT); 
    Motor_Servo.Servo_Turn(1, 90);
    Motor_Servo.Servo_Turn(2, 90);
}
void loop()
{
    Programs_System();
    vTaskDelay(pdMS_TO_TICKS(10));
}

// 系统参数thunder_system_parameter 为赛事时，启动Program_AutoCtrl，此环节蓝牙遥控器不能遥控 
void Program_AutoCtrl() {}
// ThunderGo依赖于此程序，开机后切换为ThunderGo模式时，执行该程序
void Program_ThunderGo()
{
    Bell_Thunder.Set_Ble_Type(BLE_TYPE_SERVER);
    Bell_Thunder.Set_Need_Communication(true);
}

/*************************************************************
 * @brief: thunder用户程序的启动代码，只在用户程序启动时执行一次
 * 一般在此过程创建用户线程，用户程序最多4个，分别为Program_1、
 * Program_2、Program_3、Program_4
 *************************************************************/
void Program_1()
{
    // 创建一个任务
    System_Task.Create_New_Loop(PROGRAM_USER_1, setup_1_1, loop_1_1);
}
void Program_2() {}
void Program_3() {}
void Program_4() {}

/*************************************************************
 * @brief: thunder用户线程
 *************************************************************/
void setup_1_1()
{
    // 任务初始化设置函数，在这里添加任务的初始化设置
}
void loop_1_1()
{
    // 任务运行函数，在这里添加任务的运行代码
}

```