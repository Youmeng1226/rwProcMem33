# 驱动1名称：Linux ARM64内核硬件进程内存读写驱动37
本驱动支持所有能解锁BL的手机，无论小米、黑鲨、红魔、ROG、一加、三星、摩托罗拉等等，并且不需要手机厂商开放内核源码。只需要手动修改五六处地方，就可以跑在任意机型的内核上！具体修改过程不再本文章的论述中。本文章仅提供驱动源代码。

### 本驱动接口列表：
1. 驱动_设置驱动设备接口文件允许同时被使用的最大值: SetMaxDevFileOpen
2. 驱动_隐藏驱动（卸载驱动需重启机器）: HideKernelModule
3. 驱动_打开进程: OpenProcess
4. 驱动_读取进程内存: ReadProcessMemory
5. 驱动_写入进程内存: WriteProcessMemory
6. 驱动_关闭进程: CloseHandle
7. 驱动_获取进程内存块列表: VirtualQueryExFull（可选：显示全部内存、只显示在物理内存中的内存）
8. 驱动_获取进程PID列表: GetProcessPidList
9. 驱动_获取进程权限等级: GetProcessGroup
10. 驱动_提升进程权限到Root: SetProcessRoot
11. 驱动_获取进程占用物理内存大小: GetProcessRSS
12. 驱动_获取进程命令行: GetProcessCmdline


# 驱动2名称: Linux ARM64内核硬件断点进程调试驱动3
### 本驱动接口列表：
1.  驱动_打开进程: OpenProcess
2.  驱动_关闭进程: CloseHandle
3.  驱动_获取CPU支持硬件执行断点的数量: GetNumBRPS
4.  驱动_获取CPU支持硬件访问断点的数量: GetNumWRPS
5.  驱动_设置进程硬件断点: AddProcessHwBp
6.  驱动_删除进程硬件断点: DelProcessHwBp
7.  驱动_暂停硬件断点: SuspendProcessHwBp
8.  驱动_恢复硬件断点: ResumeProcessHwBp
9.  驱动_读取硬件断点命中信息: ReadHwBpInfo
10. 驱动_设置无条件Hook跳转: SetHookPc

## 目录说明：
> **rwProcMem33Module**：进程内存读写驱动
>>* **rwProcMem_module**：（*内核层*）驱动源码
>>* **testKo**：（*应用层*）调用驱动demo
>>* **testTarge**t：（*应用层*）读取第三方进程demo
>>* **testMemSearch**：（*应用层*）搜索第三方进程内存demo
>>* **testDumpMem**：（*应用层*）保存第三方进程内存demo
>>* **testCEServer**：（*应用层*）CheatEngine远程服务器，可配合CheatEngine7.1远程连接使用

> **hwBreakpointProcModule**：硬件断点进程调试驱动
>>* **hwBreakpointProc_module**：（*内核层*）驱动源码
>>* **testHwBp**：（*应用层*）调用驱动demo
>>* **testHwBpTarget**：（*应用层*）硬件断点第三方进程demo
>>* **testHwBpClient**：（*应用层*）硬件断点工具之远程客户端
>>* **testHwBpServer**：（*应用层*）硬件断点工具之远程服务端

## 更新日志（2024-10）：
1.支持Linux5.10、6.1

2.修复硬件断点会卡死的bug

3.修复搜索Kit的一些bug

