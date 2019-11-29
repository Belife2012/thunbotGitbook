# 计时器


**常用的 API**：
```cpp

/**
 * @brief: 获取虚拟计时器的时间，单位：毫秒ms
 * 
 * @param timer_index: 计时器序号 1~5
 * @return uint32_t : 返回计时时间，单位：毫秒ms
 */
uint32_t BELL_THUNDER::Get_Virtual_Timer(uint32_t timer_index)

/**
 * @brief 将虚拟计时器清零，清零后的计时器数值变为0，然后立刻从 0 开始计时，+1/ms
 * 
 * @param timer_index 计时器序号 1~5
 */
void BELL_THUNDER::Reset_Virtual_Timer(uint32_t timer_index)
```
<br />

**Tbot I 系统编程示范**
```cpp
// 在程序的某个位置，复位计时器
Bell_Thunder.Reset_Virtual_Timer(1); // 复位计时器1

// 在程序的某个位置，获取计时器的时间
int use_time;
use_time = Bell_Thunder.Get_Virtual_Timer(1); // 获取计时器1的时间
```

