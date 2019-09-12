# 彩灯条显示


**彩灯条 常用的 API**：
```cpp
/**
 * @brief: 修改单个彩灯的RGB数据
 * 
 * @param address: 彩灯编号，左边上面第一个为1，右上面第一个为7
 * @param r: 单个彩灯R值
 * @param g: 单个彩灯G值
 * @param b: 单个彩灯B值
 */
void LED_COLOR::Set_LED_Data(uint8_t address, uint8_t r, uint8_t g, uint8_t b)

/**
 * @brief: 修改全部彩灯的缓存，修改后需要调用LED_Updata进行刷新彩灯显示
 * 修改后显示模式恢复为静态，如果需要改变显示模式，需要调用Set_LED_Dynamic
 * 
 * @param data: 显示数据
 */
void LED_COLOR::Set_LEDs_Data(t_color_led_buff data)

/**
 * @brief: 修改多个彩灯的缓存，显示模式恢复为静态显示
 * 
 * @param address: 起始编号
 * @param data: 数据
 * @param size: 数据长度
 */
void LED_COLOR::Set_LEDs_Data(uint8_t address, uint8_t *data, uint8_t size)

/* 
 * 设置彩灯的动态显示模式，有四种模式，
 *   当设置好模式后，编辑好的彩灯显示将一直以该模式显示直到自行改变
 * 
 * @parameters: 动态模式的参数，有四种 0：静态 1：闪烁 2：滚动 3：呼吸
 * @return: 
 */
void LED_COLOR::Set_LED_Dynamic(uint8_t dynamicMode)

/**
 * @brief: 依据显示内存更新显示
 * 
 */
void LED_COLOR::LED_Updata(void)

/**
 * @brief: 关闭彩灯显示
 * 
 */
void LED_COLOR::LED_OFF(void)

```
<br />

**Tbot I 系统编程示范**
```cpp
LED_COLOR::t_color_led_buff colorData = {{182, 180, 245}, {132, 129, 239}, {90, 86, 235}, {44, 39, 228}, {29, 24, 205}, {22, 19, 155}, {182, 180, 245}, {132, 129, 239}, {90, 86, 235}, {44, 39, 228}, {29, 24, 205}, {22, 19, 155}};
LED_Color.Set_LEDs_Data(colorData);
LED_Color.Set_LED_Dynamic(LED_COLOR::COLOR_MODE_BREATH);
```
<br />

示例程序： `ColorLEDs.ino`
