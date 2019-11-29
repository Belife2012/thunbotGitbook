# 编码电机转动


## 创建实例
* `motor(motor_index)` 
<br/>
  创建motor实例，motor_index 可取值为 `thunbot.PORT_L`, `thunbot.PORT_R`。

## 方法
* `run(number)` 
<br/>
  使电机按照 number 功率运行。

* `get_rotate_angle()` 
<br/>
  获取电机旋转的角度。

* `clear_position()` 
<br/>
  复位旋转角度，重新开始计算电机旋转角度。

* `get_speed(number)` 
<br/>
  获取电机转速，number 设置取样次数，根据多次取样计算平均值，一般设置为 10 。


**编程示范**

```python
from thunbot import motor
import thunbot
import time

motor_l = motor(thunbot.PORT_L)
motor_r = motor(thunbot.PORT_R)

for i in range(-100,100):
  motor_l.run(i)
  motor_r.run(-i)
  print("motor_l speed:",motor_l.get_speed(10),"postion:",motor_l.get_position(),"angle:",motor_l.get_rotate_angle())
  print("motor_r speed:",motor_r.get_speed(10),"postion:",motor_r.get_position(),"angle:",motor_r.get_rotate_angle())
  time.sleep_ms(100)

motor_l.run(0)
motor_r.run(0)
time.sleep_ms(1000)
motor_l.clear_position()
motor_r.clear_position()
# 分别旋转轮子看angle是否为360度
while 1:
  print("motor_l speed:",motor_l.get_speed(10),"postion:",motor_l.get_position(),"angle:",motor_l.get_rotate_angle())
  print("motor_r speed:",motor_r.get_speed(10),"postion:",motor_r.get_position(),"angle:",motor_r.get_rotate_angle())
  time.sleep_ms(100)

```