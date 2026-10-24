# 第三方组件与源码来源

安装包保留第三方组件的原始许可和来源信息，自有程序集封装不改变这些组件的许可。

| 组件 | 版本 / 许可 | 官方来源 |
| --- | --- | --- |
| LibreHardwareMonitor | 0.9.6，MPL-2.0，未修改第三方程序集 | [官方 v0.9.6 源码](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor/tree/v0.9.6) |
| Microsoft WebView2 SDK | 1.0.4258.31，包内微软许可 | [官方 NuGet](https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.4258.31) |
| Apache ECharts | 6.1.0，Apache-2.0 | [官方项目](https://github.com/apache/echarts) |
| Microsoft Fluent UI System Icons | MIT | [官方项目](https://github.com/microsoft/fluentui-system-icons) |
| BlackSharp.Core / DiskInfoToolkit / RAMSPDToolkit-NDD | 1.0.7 / 1.1.2 / 1.4.2，MPL-2.0 | 安装包内各自 `.nuspec` 的 repository / projectUrl |
| HidSharp | 2.6.4，按包内 LICENSE.txt | [官方项目](https://github.com/IntergatedCircuits/HidSharp) |
| Microsoft System.* 运行依赖 | MIT | 安装包内各自许可与 `.nuspec` 来源 |

许可全文、原包元数据和源码仓库/提交信息见安装包 `licenses`，包括 `runtime-licenses`。这些文件随软件分发。

程序使用 Windows 已有的 winsqlite3、WMI 与系统接口；NVIDIA NVML 来自用户已安装的驱动。PawnIO 驱动不随安装包分发，软件只使用已经安装且兼容的驱动。
