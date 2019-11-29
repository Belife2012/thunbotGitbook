# 小型电机转动(风扇电机)

## 创建实例
* `motor_mini(motor_mini_index)` 
<br/>
  创建motor_mini实例，motor_mini_index 可取值为 `thunbot.PORT_A`, `thunbot.PORT_B`, `thunbot.PORT_1`, `thunbot.PORT_2`, `thunbot.PORT_3`, `thunbot.PORT_4`。

## 方法
* `set_speed(number)` 
<br/>
  设置小型电机转速为 number(取值范围是-100~100)。


**编程示范**

```python
from thunbot import motor_mini
import thunbot
import time

m1 = motor_mini(thunbot.PORT_A)

# 正向转动测试
# 加速
for i in range(0,100):
  print("set:",i)
  m1.set_speed(i)
  time.sleep_ms(200)
# 减速
for i in range(0,100):
  print("set:",100 - i)
  m1.set_speed(100 - i)
  time.sleep_ms(200)
  
# 逆向向转动测试
# 加速
for i in range(-100,0):
  print("set:", -i-100)
  m1.set_speed( -i-100)
  time.sleep_ms(200)
# 减速
for i in range(-100,0):
  print("set:",i)
  m1.set_speed(i)
  time.sleep_ms(200)

```