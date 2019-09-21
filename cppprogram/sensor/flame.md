# 火焰

火焰传感器利用两个感应器件的组合数据进行测量火焰的相对强度和相对夹角，定义相对强度范围0~100；测量角度范围在-45°~45°，定义左边相对角度为负值，右边相对角度为正值。

**注意**：由于火焰传感器感应的是火焰红外光，其他发热光源（例如 太阳光）一样会存在这种红外光，所以这些光源也会被传感器检测到，导致误判为火焰。光滑面的反射也会带来一定的误判概率。


**常用的 API**：
```cpp

/**
 * @brief 获取传感器的火焰源相对角度，可以通过返回数值判断火焰位置的
 *  偏离方向和偏离程度
 * 
 * @return int8_t 火焰源相对角度，取值范围 -45 ~ 45
 */
int8_t SENSOR_FLAME::Get_Flame_Angle(unsigned char channel)

/**
 * @brief 获取传感器的火焰相对强度，可以通过返回数值判断火焰相对强度
 * 
 * @return unsigned char 火焰相对强度，取值范围0~100
 */
unsigned char SENSOR_FLAME::Get_Flame_Intensity(unsigned char channel)

/**
 * @brief 判断有没有火苗，如果测量到红外强度大于CHECK_FLAME_INTENSITY，
 *  则判断为有火苗，否则判断为没有火苗；可以通过改变CHECK_FLAME_INTENSITY
 *  修改灵敏度（如果CHECK_FLAME_INTENSITY设置太小，太阳光就会判断为有火苗）
 * 
 * 一般情况使用 Get_Flame_Intensity 自行判断
 * 
 * @return true 有火苗
 * @return false 没有火苗
 */
bool SENSOR_FLAME::Check_Flame(unsigned char channel)

```
<br />

**Tbot I 系统编程示范**
```cpp
int intensity;
int angle;
intensity = Sensor_Flame.Get_Flame_Intensity(1);
angle = Sensor_Flame.Get_Flame_Angle(1);
```
