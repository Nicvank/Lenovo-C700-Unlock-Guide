# Lenovo Legion C700 Fastboot Notes

这是我对手上 Lenovo Legion Cloud Gaming Handheld C700（`LCGHCC700`）进行 Android、fastboot、USB 驱动和 Bootloader 研究时整理的记录。

> 这是我的个人研究资料，不是 Lenovo、MediaTek、Google 或 Microsoft 官方项目。

## 设备信息

| 项目 | 信息 |
|---|---|
| 设备 | Lenovo Legion Cloud Gaming Handheld C700 |
| 型号 | `LCGHCC700` |
| 产品标识 | `LCGHCC700_PRC` |
| SoC | MediaTek Dimensity 7400 |
| fastboot product | `aiot8873p2_64_bsp_wifi` |
| fastboot USB ID | `USB\\VID_0E8D&PID_201C` |
| Bootloader 状态 | 我已验证为 `unlocked: yes` |

## 解锁过程

设备正常进入 Android 且 USB 调试已开启时：

```text
adb devices
adb reboot bootloader
```

进入 fastboot 后检查连接：

```text
fastboot devices
```

再输入以下指令解锁：

```text
fastboot flashing unlock
```
输入后在5秒内按下音量+/-即可解锁

具体流程可以查看视频：

## Windows 驱动

设备硬件 ID：

```text
USB\\VID_0E8D&PID_201C
```

我使用并核对过的驱动来源：

<https://www.catalog.update.microsoft.com/ScopedViewInline.aspx?updateid=67446b50-e7f8-454a-9155-f48ddf362d01>

我确认适配这台设备的驱动 INF 应包含：

```text
android_winusb.inf
USB\\VID_0E8D&PID_201C
CatalogFile.NTamd64 = androidwinusba64.cat
```

## 免责声明

本项目仅供设备所有者研究和复现。解锁、擦除、刷写或系统修改可能导致数据丢失、系统无法启动、售后支持受限或设备损坏；其他人参考本项目时，需要自行确认设备归属、完成备份并承担操作风险。

```
