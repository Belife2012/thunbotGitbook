# 主控通信

多主控通信模块总共有5个端口：1个管理端口（地址为 0），4个普通端口（地址为 1~4）。管理端口是必须连接的端口，其他端口根据应用来连接。

默认不打开主控通信的，在使用前需要调用 `Open_Multi_Message` 打开多主控通信。每次调用 `RecvNameVarInt` 获取信息的值时，返回的数据是最新值，该信息如果没有更新，则返回前面接收到的值。

**注意**：多主控通信模块不支持热拔插，使用时请保证可靠连接。

**常用的 API**：
```cpp

/**
 * @brief 由于通信收发需要消耗RAM和CPU线程运行时间，
 * 因此只有在需要用到通信时再打开多机通信，不需要后就关闭多机通信，
 * 调用 Open_Multi_Message() 打开多机通信，调用 Close_Multi_Message() 关闭多机通信，
 * 
 */
void BELL_THUNDER::Open_Multi_Message()

/**
 * @brief 由于通信收发需要消耗RAM和CPU线程运行时间，
 * 因此只有在需要用到通信时再打开多机通信，不需要后就关闭多机通信，
 * 调用 Close_Multi_Message() 关闭多机通信，
 * 
 */
void BELL_THUNDER::Close_Multi_Message()

/**
 * @brief 为了方便使用多机通信，可以将数据传输进行 命名，
 * 支持设置最多 32个 命名变量，名字长度最大 16个字符，
 * 可以调用 InitNameVarInt() 设置 int 变量初始值，否则变量的初始值为 0
 * 
 * @param name 传入被传输的变量名称字符串，
 * @param init_value 传入 int 变量数值
 */
void BELL_THUNDER::InitNameVarInt(const char *name, int init_value)

/**
 * @brief 为了方便使用多机通信，可以将数据传输进行 命名，
 * 支持设置最多 32个 命名变量，名字长度最大 16个字符，
 * 可以调用 SendNameVarInt() 向某个地址传输一个命名 int变量
 * 
 * @param addr 传入目的地址 0~4
 * @param name 传入被传输的变量名称字符串，
 * @param var_value 传入 int 变量数值
 * @return int 返回错误码，正常发送返回0
 */
int BELL_THUNDER::SendNameVarInt(unsigned char addr, const char *name, int var_value)

/**
 * @brief 为了方便使用多机通信，可以将数据传输进行 命名，
 * 支持设置最多 32个 命名变量，名字长度最大 16个字符，
 * 可以调用 RecvNameVarInt() 更新命名 int变量，
 * 如果没有该命名数值的更新，则返回旧的数值
 * 
 * @param name 传入被传输的变量名称字符串，
 * @return int 返回最新数值
 */
int BELL_THUNDER::RecvNameVarInt(const char *name)
```
<br />

**Tbot I 系统编程示范**
```cpp
// 打开主控通信
Bell_Thunder.Open_Multi_Message();
Bell_Thunder.InitNameVarInt("message", 0); // 初始化“message”值为0

// 发送数据
Bell_Thunder.SendNameVarInt(1, "message", 100); // 向 端口1 发送的信息为“message”，值为 100

// 接收数据
Bell_Thunder.RecvNameVarInt("message"); // 获取信息为“message”的值

```

