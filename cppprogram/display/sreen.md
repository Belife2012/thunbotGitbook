# LED点阵显示

**LED点阵 常用的 API**：
```cpp
/**
 * @brief: 设置将要播放的内置动画编号
 * 
 * @param Animation_No: 有效编号：3 ~ 15
 */
void DISPLAY_SCREEN::Play_Animation(uint8_t Animation_No)

/**
 * @brief: 点亮画面的一个x,y点
 * 
 * @param x: 水平轴位置
 * @param y: 垂直轴位置
 */
void DISPLAY_SCREEN::Set_Single_Dot(uint8_t x, uint8_t y)

/**
 * @brief: 熄灭画面的一个x,y点
 * 
 * @param x: 水平轴位置
 * @param y: 垂直轴位置
 */
void DISPLAY_SCREEN::Clear_Single_Dot(uint8_t x, uint8_t y)

/**
 * @brief: 显示18*12的点阵画面
 * 
 * @param picture_dots: 存有显示数据的二维数组数据
 * @param display_flag: 默认为1 表示立刻显示，0表示仅仅修改显示内存
 */
void DISPLAY_SCREEN::Display_Picture(const byte picture_dots[LED_MATRIX_COL_NUM][LED_MATRIX_ROW_NUM], byte display_flag)

/* 
 * 显示字符，长字符串以滚动方式呈现，循环显示 直到 修改显示内容
 * 可输入字符为 '0'~'9' 'A'~'Z' 'a'~'z'，小写字母显示的是大写, 其他字符显示为井号 #
 * 如果显示内容不超过显示范围，将是居中静态显示
 * 最长可以支持40个字符
 * 
 * @parameters: 传入字符串首地址，字符串最长40字节，NULL 表示清空显示
 * @return: 
 */
void DISPLAY_SCREEN::Play_LED_String(const char *playString)

/* 
 * 显示数字（可以整数，负数，小数），小数保留最大3位，会进行四舍五入
 * 
 * @parameters: 
 * @return: 
 */
void DISPLAY_SCREEN::Play_LED_String(double number)
```
<br />

**Tbot I 系统编程示范**
```cpp
DISPLAY_SCREEN::t_picture_buff myPic = {
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
    {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0},
};
Display_Screen.Display_Picture(myPic);
delay(300);
Display_Screen.Move_Picture_To(3, 0);
delay(300);
Display_Screen.Move_Picture_To(-3, 0);
```
<br />

示例程序： `DisplayPic.ino`