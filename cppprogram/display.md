# 灯板显示

Tbot I 的显示屏幕包含了 18\*12 的白色LED点阵`Display_Screen`和 2\*6 的RGB彩灯条`LED_Color`。功能库提供了易用的API，可以实现动态显示，LED点阵可以用于显示字母和数字，RGB彩灯条内置了四种显示效果：0|静态（`LED_COLOR::COLOR_MODE_STATIC`）、1|闪烁（`LED_COLOR::COLOR_MODE_BLINK`）、2|滚动（`LED_COLOR::COLOR_MODE_ROLL`）、3|呼吸（`LED_COLOR::COLOR_MODE_BREATH`）。

`Display_Screen`可以使用 `DISPLAY_SCREEN::t_picture_buff` 定义一个二维数组变量来放置显示数据，1表示亮灯 0表示灭灯。

`LED_Color`可以使用`LED_COLOR::t_color_led_buff` 定义一个二维数组变量来放置灯光数据，数值为八位RGB分量值。
