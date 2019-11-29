# 多任务编程


**常用的 API**：
```cpp

/**
 * @brief: 创建多一个线程，新的 program_setup 和 program_loop 就会运行
 * 
 * @param program_sequence: 程序编号，表示该任务是属于哪个程序的，取值 0~3 
 * 或者使用 PROGRAM_USER_1、PROGRAM_USER_2、PROGRAM_USER_3、PROGRAM_USER_4 分别表示程序1/2/3/4
 * 
 * @param program_setup: 任务初始化设置函数
 * @param program_loop: 任务运行函数
 * @return uint8_t :返回0表示创建成功，返回1表示创建数目已经达到最大值，不能继续创建
 */
uint8_t SYSTEM_TASK::Create_New_Loop(uint8_t program_sequence, func_Program_Setup program_setup, func_Program_Loop program_loop )
```
<br />

**Tbot I 系统编程示范**
```cpp
// 在程序1中创建两个任务
void Program_1()
{
    System_Task.Create_New_Loop(PROGRAM_USER_1, setup_1_1, loop_1_1);
    System_Task.Create_New_Loop(PROGRAM_USER_1, setup_1_2, loop_1_2);
}
// 任务 1
void setup_1_1()
{ 
    // 任务初始化设置函数，在这里添加任务的初始化设置
}
void loop_1_1()
{
    // 任务运行函数，在这里添加任务的运行代码
}

// 任务 2
void setup_1_2()
{
}
void loop_1_2()
{
}

```
<br />

示例程序： `DoubleTask.ino`
