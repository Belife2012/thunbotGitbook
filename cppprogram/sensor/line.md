# 巡线

巡线传感器使用红外收发管来检测黑白，基本原理：黑色反射光弱，白色反射光强。该传感器的有效检测范围是 5mm~20mm，通过直接读取引脚的逻辑来判断黑(1)、白(0)，读取引脚逻辑的Arduino接口是`digitalRead` 。巡线传感器有两个探测头 A 和 B ，对应的引脚分别是`LINE_PORT_A` 和 `LINE_PORT_B`，例如：读取探测头 A 的值使用 `digitalRead(LINE_PORT_A)`，读取探测头 B 的值使用 `digitalRead(LINE_PORT_B)` 。 

**注意**：IIC接口4 与 巡线传感器共用接口，该接口用于IIC传感器后，需要调用 `SENSOR_IIC::Set_Port4_IIC(false);` 后才能用于巡线传感器接口。

<br />

**Tbot I 系统编程示范**
```cpp
uint8_t data[2];

data[0] = digitalRead(LINE_PORT_A);
data[1] = digitalRead(LINE_PORT_B);
```

**附**：巡线接口使用的是普通输入引脚模式来获取引脚逻辑的，所以该接口除了应用于巡线传感器，用户还可以自主编程应用于其他普通输出引脚（GPIO）的传感器，例如开关。
