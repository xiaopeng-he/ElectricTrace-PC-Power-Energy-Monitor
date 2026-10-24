# 平台与硬件兼容

## 选择安装包

Windows x64 和 32 位 x86 使用同一个安装器或便携包。启动器根据操作系统自动选取对应程序。

| 系统 / 架构 | 处理与验证状态 |
| --- | --- |
| Windows 11 x64 | 已核对本机 CPU / GPU 实际采样、完整窗口和发布程序集 |
| Windows 11 WOW64 x86 | 32 位发布程序集、存储/序列化/安全/备份/还原检查已运行 |
| Windows 10 1709+ x64 / x86 | 目标范围，尚待对应实体系统验收 |
| Windows 11 ARM | 暂按 x64 仿真基本指标处理；未在实体设备验证，不启用 CPU 驱动采集 |
| Windows Server 桌面环境 | 未验收 |
| Windows 7 / 8 / XP | 不支持 |
| macOS / Linux | 当前没有安装包 |

这张表按实际验证进度更新，便于选择合适的运行环境。

## 运行环境

- .NET Framework 4.8 或更新版本：[微软官方下载](https://dotnet.microsoft.com/download/dotnet-framework/net48)。
- 完整界面：WebView2 Runtime 120 或更新版本：[微软官方下载](https://developer.microsoft.com/microsoft-edge/webview2/#download-section)。缺少时可先选择基本 WinForms 界面。
- 不需要 Node.js、Python 或 .NET SDK 来运行安装包。

## 可读取哪些传感器

CPU 温度、封装功率、时钟和核心传感器依赖硬件库与兼容驱动。增强采集由单独进程请求管理员确认，主界面保持普通权限；没有 PawnIO 时不会静默安装。

0.5.1 在可识别的单插槽 Intel CPU 上分开采集封装功率、温度和核心详情：前两项约每秒读取，核心详情独立刷新并显示更新时间。其他 CPU 沿用硬件库的读取方式。此次连续采样实测环境为 Windows 11 x64、Intel 处理器与 NVIDIA 独立显卡；其他设备的传感器能力以实际返回为准。

NVIDIA 优先用已有驱动提供的 NVML；其他显卡使用硬件库的可用传感器。电池、内存等读取系统接口。风扇、显卡频率、功耗分项、电压等指标并非所有设备都会提供。

不提供的项目显示“—”，不当作零值计入。CPU 数据延迟时，其他有效指标继续更新；部件合计仅在范围不重叠且两项同时有效时显示。
