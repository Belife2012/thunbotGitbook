# 彩灯条显示（led_color）

屏幕两侧分布有`彩色LED灯`，总共12个彩灯，位置序号如下。程序可以控制每个彩灯的RGB亮度值，编程可实现丰富的灯光模式。
```
每个 彩灯LED灯 的位置序号（正面看过去）：
1                        7
2                        8
3                        9
4                        10
5                        11
6                        12
```

## 方法
* `led_color.set_led_data(number, bytearray_3)` 
<br/>
  写入彩灯数据，number 传入彩灯的位置序号，取值范围1~12；bytearray_3 传入彩灯的RGB值（），3个元素的bytearray数据，元素的取值范围 0~255。写入数据后需要调用 `led_color.on()` 进行显示。

* `led_color.on()` 
<br/>
  写入彩灯数据后需要调用`led_color.on()`进行显示。

* `led_color.clear()` 
<br/>
  关闭所有彩灯。

**编程示范**
```python
from thunbot import led_color
import time

ledColorData = bytearray([0,0,255])
led_color.set_led_data(1, ledColorData)
led_color.on()

time.sleep_ms(1000)

ledColorData = bytearray([255,0,0])
led_color.set_led_data(1, ledColorData)
led_color.set_led_data(2, ledColorData)
led_color.set_led_data(3, ledColorData)
led_color.set_led_data(4, ledColorData)
led_color.set_led_data(5, ledColorData)
led_color.set_led_data(6, ledColorData)
led_color.on()

time.sleep_ms(1000)
led_color.clear()
```
<br />

示例程序： `led_color_test.py`