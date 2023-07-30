# 配置

### 设备规格

| 类别     | 型号                                                                                                                                         |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 主板     | MSI B360 MORTAR [\[说明书\]](./docs/M7B23v1.0_SC.pdf)                                                                                        |
| CPU      | Intel 8700 [\[规格\]](https://ark.intel.com/content/www/cn/zh/ark/products/126686/intel-core-i78700-processor-12m-cache-up-to-4-60-ghz.html) |
| SSD      | GLOWAY Basic1TNVMe-M.2/80, 基础版 (_驱动比较糟糕，不太推荐，但是能用_)                                                                       |
| 显示器 1 | MSI MAG274QRF-QD + HDMI 1.4                                                                                                                  |
| 显示器 2 | MSI PAG272QR + DP 1.2                                                                                                                        |
| 显卡     | IGPU (主板载有 Nvidia 3070，但 htihacktosh 无法使用，所以直接屏蔽了, 两个显示器都接在集显上)                                                 |
| 鼠标     | 罗技（G）G502 HERO                                                                                                                           |
| 键盘     | 京东京造 樱桃轴背光机械键盘                                                                                                                  |

### BIOS 设置

| 选项     |       值       |
| :------- | :------------: |
| CFG Lock |      禁用      |
| VT-D     |      禁用      |
| 首选 GPU | IGPU(VRAM 64M) |

# Opencore

版本: 0.93

### Drivers

| 名称            |                                         版本                                         |
| :-------------- | :----------------------------------------------------------------------------------: |
| OpenRuntime.efi |                                     同 Opencore                                      |
| OpenCanopy.efi  |                                     同 Opencore                                      |
| HflPlus.efi     | [Visit](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi) |

### Kexts

| 名称          |     版本      |
| :------------ | :-----------: |
| Lilu          |     1.6.6     |
| WhateverGreen |     1.6.5     |
| ApppleALC     |     1.8.3     |
| VirtualSMC    |     1.3.2     |
| SMCProcessor  | 同 VirtualSMC |
| SMCSuperIO    | 同 VirtualSMC |
| USBToolBox    |      0.2      |
| NVMeFix       |     1.1.0     |
| IntelMausi    |     1.0.7     |

# 存在的问题

### 1. 当同时连接了 HDMI 接口和 DP 接口（双显示器，均连接集显）, 启动到第二阶段，HDMI 显示器会出现花屏，DP 显示器黑屏。直到登陆窗口出现后，还需要等待 10s ～ 30s，两个显示器才能点亮。

**具体现象**

1. [请查看此视频](https://vimeo.com/849849015?share=copy)
2. 视频中有两个显示器和一个 mac 笔记本。 两个大的显示器连接在 hacinto 的 IGPU 上。
3. 最左边是 HDMI 接口，看过来第二个是 DP 接口。
4. mac 笔记本在通过 vnc 远程开机过程中的 hacktosh。
5. 通过笔记本的远程画面可以看到，从跑进度条直到登陆窗口出现很久后，大的显示器才点亮。

内核日志：[kernel.log](https://github.com/daoye/hackintosh/files/12208577/kernal.log)
启动日志：[boot.log](https://github.com/daoye/hackintosh/files/12208578/boot.log)

**解决方案，寻求中**
