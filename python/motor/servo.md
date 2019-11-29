# 舵机转动


## 创建实例
* `servo(servo_index)` 
<br/>
  创建servo实例，servo_index 可取值为 `thunbot.PORT_A`, `thunbot.PORT_B`。

## 方法
* `turn_percent(number, speed)` 
<br/>
  舵机旋转至 number(范围 -100~100) 位置，speed通常为100，如果小于100，舵机运行时会阻塞程序运行直到舵机运行到指定位置。

* `percent_set(max, min, zero)` 
<br/>
  设置舵机位置，分别指定最大位置max，最小位置min，零点位置zero 。


**编程示范**

```python
from thunbot import servo
import thunbot
import time

s1 = servo(thunbot.PORT_A)
s2 = servo(thunbot.PORT_B)

s1.turn_percent(-100,100)
s2.turn_percent(-100,100)

```
