# LED点阵显示（display）

Tbot I 的显示屏幕包含了 18\*12 的白色LED点阵，内置了丰富的动画显示，还可以用于显示字母和数字信息，可以灵活控制每个灯珠的亮灭，编程实现各种自定义画面或者动画。
```
点阵排序（正面看过去）：
(0,0)│――――――――――――――――――――――――――――――→ X 轴 
     │
     │
     │
     │
     │
     │
     │
     ↓                             (17,11)
    Y 轴
```

## 方法
* `display.set_dot(number_x, number_y, number_data)` 
<br/>
  number_data=1 时，在坐标位置 (number_x, number_y) 亮灯，number_data=0 时，则是在坐标位置 (number_x, number_y) 灭灯。

* `display.picture(bytearray_18_12)` 
<br/>
  显示自定义画面，bytearray_18_12 是存有 18\*12=216 个元素的 bytearray变量。

* `display.move_picture_to(number_x, number_y)` 
<br/>
  移动画面，number_x 表示在X轴上移动的像素点，number_y 表示在y轴上移动的像素点。

* `display.clear()` 
<br/>
  清除并关闭显示。

**编程示范**
```python
from thunbot import display
import time

# 显示自定义图片 
image = \
[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
 1,1,1,1,0,0,1,1,1,1,0,1,0,0,0,1,0,0,
 1,0,0,0,1,0,1,0,0,0,0,1,0,0,0,1,0,0,
 1,0,0,0,1,0,1,0,0,0,0,1,0,0,0,1,0,0,
 1,0,0,0,1,0,1,0,0,0,0,1,0,0,0,1,0,0,
 1,1,1,1,0,0,1,1,1,1,0,1,0,0,0,1,0,0,
 1,0,0,0,1,0,1,0,0,0,0,1,0,0,0,1,0,0,
 1,0,0,0,1,0,1,0,0,0,0,1,0,0,0,1,0,0,
 1,1,1,1,0,0,1,1,1,1,0,1,1,1,0,1,1,1,
 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]   

# 整体偏移
# 存在问题：如果画面移出了画面再移回来，移出部分会被清除
image = bytearray(image)
display.picture(image)
time.sleep_ms(1000)

for i in range(0,10):
  display.move_picture_to(0,2)
  time.sleep_ms(200)
  display.move_picture_to(0,-2)
  time.sleep_ms(200)

display.clear()
for i in range(0,12):
  for j in range(0,18):
    display.set_dot(j,i,1)
    time.sleep_ms(20)
    
for i in range(0,12):
  for j in range(0,18):
    display.set_dot(j,i,0)
    time.sleep_ms(20)

```
<br />

示例程序： `display_test.py`