# PowerLimit 充电阈值控制程序

## 选择语言
- [English Version](./README_en.md)
- [中文版本](./README_zh.md)

## 简介
PowerLimit 是一个轻量级工具，旨在帮助用户自定义笔记本的充电阈值，避免技嘉控制中心对充电设置的控制。通过此工具，用户可以手动设置充电限制，从而保护电池寿命。

## 特别感谢
[s-h-a-d-o-w 的 alfc 项目](https://github.com/s-h-a-d-o-w/alfc) 提供的支持与帮助。

## 兼容性

| 型号 | 系统 |
|------|------|
| Aorus 15P XD | Windows 10/11 |

据我所知，在 Windows 11 24H2 版本中，控制中心已经无法打开，我也因此开发了这个工具。在其他版本的系统中，这个工具可能也会存在一些问题。如果您能确认表中尚未列出的内容，请提交 PR 或 issue。在代码中我也提供了命令行版本可以以供参考，如果在其他型号或者系统上有兼容性问题，欢迎提交PR。

## 系统要求
- **操作系统**: Windows

## 使用说明

### 配置技嘉控制中心
1. 解压技嘉控制中心的安装包。
2. 将其中的 `acpimof.dll` 文件复制到 `C:\Windows\SysWOW64` 目录下。
3. 打开注册表编辑器，在 `Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WmiAcpi` 路径下创建一个字符串值 `MofImagePath`，并将其值设置为 `C:\Windows\SysWOW64\acpimof.dll`。
4. 完成后，重启计算机。

### 启动 PowerLimit 程序
![image](https://github.com/user-attachments/assets/a29a3656-5fd0-4074-b6e3-dbe95cda7c0f)

打开 PowerLimit 程序后，界面将显示当前的充电策略和阈值。

### 设置充电阈值
- 点击“标准”按钮以恢复默认充电阈值。
- 点击“自定义”按钮，输入所需的充电阈值（如 85%），然后点击“保存”以应用设置。

### 保存并退出
点击“保存”后，您的设置将立即生效，并且即使退出程序，设置也会保持。

## 设置 PowerLimit 自启
如果希望 PowerLimit 在每次启动时自动运行并保持设置生效，可以通过任务计划程序添加 `PowerLimit.exe` 为开机自启程序，并使用 `background` 参数。

### 设置流程
1. 打开“任务计划程序”，点击右侧的“创建基本任务”。
2. 在“名称”中输入“PowerLimit”，点击“下一步”。
3. 选择“当计算机启动时”触发任务，点击“下一步”。
4. 选择“启动程序”并点击“下一步”。
5. 在“程序/脚本”框中浏览并选择 `PowerLimit.exe` 文件的路径。
6. 在“添加参数”框中输入 `background`，以确保 PowerLimit 在后台运行。
7. 点击“完成”以保存任务。

这样，PowerLimit 就会在每次计算机启动时自动运行，确保充电阈值始终生效，并且不会占用屏幕空间。

## 设置失效说明
- PowerLimit 设置将在计算机断电并且重启后失效，但通过设置自启任务，您可以确保每次开机时 PowerLimit 会重新应用设置。

## 注意事项
- 请确保操作系统和驱动程序版本支持此工具的设置更改。
- 更改注册表存在一定风险，建议在操作前备份注册表。
