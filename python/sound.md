# 播放声音（speaker）

Tbot-I 喇叭可以发出内置的声音，speaker 模块包含了相关方法和声音序号的常量定义，详情描述如下。

## 方法
* `speaker.play(number)` 
<br/>
  播放内置的声音，参数number的取值范围是 0~174 ，为了更好的表达这些序号的意义，可以使用模块中定义的常量，例如 `speaker.A0` 表示音符A0、`speaker.WIND` 表示风声。
  
* `speaker.set_volume(number)` 
<br/>
  设置音量大小，number取值范围 0~100，可以通过设置音量为 0 来设置静音，音量最大为 100。

* `speaker.check_busy()` 
<br/>
  检查声音是否播放完毕，还在播放声音中返回 0 ，播放完毕返回 1 。
  

## 定义的常量
```
speaker.A0
speaker.A1
speaker.A2
speaker.A3
speaker.A4
speaker.A5
speaker.A6
speaker.A_1
speaker.AP0
speaker.AP1
speaker.AP3
speaker.AP2
speaker.AP4
speaker.AP5
speaker.AP6
speaker.AP_1
speaker.B0
speaker.B1
speaker.B2
speaker.B3
speaker.B4
speaker.B5
speaker.B6
speaker.B_1
speaker.C0
speaker.C1
speaker.C2
speaker.C3
speaker.C4
speaker.C5
speaker.C6
speaker.C7
speaker.CP0
speaker.CP1
speaker.CP2
speaker.CP3
speaker.CP4
speaker.CP5
speaker.CP6
speaker.D0
speaker.D1
speaker.D2
speaker.D3
speaker.D4
speaker.D5
speaker.D6
speaker.DP0
speaker.DP1
speaker.DP2
speaker.DP3
speaker.DP4
speaker.DP5
speaker.DP6
speaker.E0
speaker.E1
speaker.E2
speaker.E3
speaker.E4
speaker.E5
speaker.E6
speaker.F0
speaker.F1
speaker.F2
speaker.F3
speaker.F4
speaker.F5
speaker.F6
speaker.FP0
speaker.FP1
speaker.FP2
speaker.FP3
speaker.FP4
speaker.FP5
speaker.FP6
speaker.G0
speaker.G1
speaker.G2
speaker.G3
speaker.G4
speaker.G5
speaker.G6
speaker.GP0
speaker.GP1
speaker.GP2
speaker.GP3
speaker.GP4
speaker.GP5
speaker.GP6
speaker.AM
speaker.BM
speaker.C 
speaker.DM
speaker.EM
speaker.F 
speaker.G 
speaker.SEND
speaker.WHINY
speaker.RECEIVE
speaker.GOODDD
speaker.GOOD
speaker.NOTHAPPY
speaker.LETSGO
speaker.OHMYGOD
speaker.OHNO
speaker.AMAZING
speaker.VOC
speaker.SOHAPPY
speaker.AHHHH
speaker.AIIII
speaker.AOOOO
speaker.HAHAHA
speaker.HUM
speaker.WHISTLE
speaker.LALALA
speaker.EMEMEM
speaker.ROAR
speaker.AWESOME
speaker.SOHAPPY
speaker.WAWAWA
speaker.WAWAO
speaker.WAO
speaker.WUWUWU
speaker.YEYEYE
speaker.YOYOYO
speaker.WHAT
speaker.PLANE
speaker.LANDING
speaker.TRAIN
speaker.BRAKE
speaker.CAR
speaker.TRUMPET
speaker.SHIP
speaker.TYRE
speaker.MOTORBIKE
speaker.SPORTCAR
speaker.RACING
speaker.JET
speaker.TANK
speaker.TRACTOR
speaker.ENGINE
speaker.COPTER
speaker.ELEPHANT
speaker.COCK
speaker.DOG
speaker.DINOSAUR
speaker.WOLF
speaker.TIGER
speaker.CAT
speaker.BIRD
speaker.GOAT
speaker.LION
speaker.PIG
speaker.CRACKER
speaker.GLASS
speaker.EAT
speaker.HICCUP
speaker.THUNDER
speaker.CANNON
speaker.WATER
speaker.PHONE
speaker.ALARM
speaker.FART
speaker.WIND
speaker.SEA
speaker.DRINKING
speaker.GUN
speaker.CUT
speaker.DOORBELL
speaker.KNOCK
speaker.TOLL
speaker.BOMB
speaker.SHOOT
speaker.CLEANER
speaker.RAIN
speaker.BULLET
```

**编程示范**
```python
from thunbot import speaker
import time

speaker.play(speaker.A0)
time.sleep_ms(10)
while speaker.check_busy() == 0:
    print('.', end='')
    time.sleep_ms(200)
print("end")
```
<br />

示例程序： `speaker_test.py`