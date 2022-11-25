# TCL_BT_CORE
TCL_BT_CORE

玩无线通信最基础的是时间戳，除了编解码，传输的时间戳就是核心

半个slot 312.5us
半个slot/625 =0.5us

所以TS*625+TUS 就是核心

所以需要两个计数器

1/32k  = 30.25us 再来个10分频 就有一个312.5us的计数器
还需要一个0.5u的计数器

一般蓝牙芯片内部有个大于1M的RTC外面再贴一个32.768k的

比如8M的，那4分频，就有一个0.5us的计数器


在基带上写的各种协议代码，蓝牙的时间戳在里面表示都是按照半个slot来玩的

比如一个Interval 11.25ms = 36个半slot

evt_cnt也是按照半slot来叠加，剩下TUS就是按照0.5us来计数

所以TS*625+TUS  可以表示蓝牙的任何一个时间点
