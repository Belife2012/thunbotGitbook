# 蓝牙遥控器

蓝牙遥控器采用 BLE 技术连接 Tbot-I 主控，可以方便的遥控雷霆，大大提升了雷霆的可玩性和竞技性。

Tbot I 功能库提供了方便应用的API，获取按键的事件和数据。在用户程序中，主控的蓝牙遥控默认是打开，用户编程时可以通过 `Turnon_Remote` 打开/关闭蓝牙遥控服务。  
使用 `Check_Key` 获取按键状态，`Check_Key_Action` 检测按键动作，可以获取按键事件的按键标识为`KEY_UP`, `KEY_DOWN`, `KEY_LEFT`, `KEY_RIGHT`, `KEY_SELECT`, `KEY_BACK`, `KEY_A`, `KEY_B`, `KEY_X`, `KEY_Y`, `KEY_L1`, `KEY_L2`, `KEY_R1`, `KEY_R2`, `KEY_ROCKER_L`, `KEY_ROCKER_R`；  
 使用 `Get_Control_Value` 获得摇杆的模拟数值（按键数据），可以获取按键数据的按键标识为 `KEY_ROCKER_L_X`, `KEY_ROCKER_L_Y`, `KEY_ROCKER_R_X`, `KEY_ROCKER_R_Y`, `KEY_L2_ANALOG`, `KEY_R2_ANALOG` 。

**常用的 API**：
```cpp
/**
 * @brief 打开/关闭蓝牙遥控器功能，默认是打开蓝牙遥控器功能的，但是蓝牙遥控器功能会占用
 * 系统资源，如果不需要蓝牙遥控器功能，可以使用此函数关闭
 * 
 * @param enable: true打开蓝牙遥控器功能， false关闭蓝牙遥控器功能
 */
void SENSOR_REMOTER::Turnon_Remote(bool enable)


/**
 * @brief 判断按键状态
 * 
 * @param key_index 按键标识，参照枚举变量 enum_Remoter_Key
 * @return true 按键状态为按下
 * @return false 按键状态为释放
 */
bool SENSOR_REMOTER::Check_Key(int key_index)

/**
 * @brief 检测是否发生了按下动作（每次按下只能读到一次true）或释放动作（每次释放只能读到一次true）
 * 
 * @param key_index 按键标识，参照枚举变量 enum_Remoter_Key
 * @param key_action 检测的动作，0为释放按键，1为按下按键
 * @return true 检测的动作有发生
 * @return false 检测的动作没有发生
 */
bool SENSOR_REMOTER::Check_Key_Action(int key_index, int key_action)

/**
 * @brief 获取摇杆或按键的数值
 * 
 * @param key_index 摇杆、按键标识，参照枚举变量 enum_Remoter_Value
 * @return int 摇杆、按键的模拟数值
 */
int SENSOR_REMOTER::Get_Control_Value(int key_index)
```
<br />

**Tbot I 系统编程示范**
```cpp
    if (BLE_Remoter.Check_Key_Action(KEY_Y, KEY_PRESSING))
    {
        Speaker_Thunder.Set_Sound_Volume(100);
        Speaker_Thunder.Play_Song(SPEAKER_THUNDER::SOUND_MUSIC_C5);
    }
    
    Motor_Thunder.Set_Target(1, (BLE_Remoter.Get_Control_Value(KEY_ROCKER_L_Y) + BLE_Remoter.Get_Control_Value(KEY_ROCKER_L_X)) * 0.4);
    Motor_Thunder.Set_Target(2, (BLE_Remoter.Get_Control_Value(KEY_ROCKER_L_Y) - BLE_Remoter.Get_Control_Value(KEY_ROCKER_L_X)) * 0.4);
```
<br />

示例程序： `BleRemoter.ino`