![世界可以没有日本，人类不能没有海洋](./logo.jpeg)

# Multi-adaptation Wi-Fi Geiger Counter - Double Tube Type (MWGC-2T)

⭐ 中文固件多管型 Wi-Fi 盖革计数器（MWGC-2T） ⭐

[![pipeline status](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/badges/master/pipeline.svg)](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/-/commits/master) [![Latest Release](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/-/badges/release.svg)](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/-/releases) [![vercel](https://vercelbadge.soraharu.com/?app=interactivehtmlbom)](https://interactivehtmlbom.soraharu.com/)

🔗 [GitLab (Homepage)](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type) | 🔗 [OSHWHub](https://oshwhub.com/yanranxiaoxi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type) | 🔗 [GitHub](https://github.com/yanranxiaoxi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type)

![实拍图](https://downloadserver.soraharu.com:7000/Multi-adaptation%20Wi-Fi%20Geiger%20Counter%20-%20Double%20Tube%20Type/Image/Product_quality_1620x1080px.jpg)

## 🤔 这是什么

这是一个拥有中文固件的盖革-米勒计数器，并且支持多种盖革计数管管型，意图最大化降低盖革计数器的制作成本，使用 [嘉立创 EDA](https://lceda.cn/) 进行开发。

本设计软件部分衍生于 [Emmanuel Odunlade](https://twitter.com/emmaodunlade) 在 [electronics-lab](https://www.electronics-lab.com/) 开源的 [GC-20](https://www.electronics-lab.com/project/new-improved-geiger-counter-now-wifi/)，开源协议为 [Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://choosealicense.com/licenses/cc-by-sa-4.0/)。

本设计采用 ESP-12F 高集成度 ESP8266 Wi-Fi 模组作为核心逻辑控制器，采用 ILI9341 18Pin SPI 触摸显示屏作为用户交互部分，板型设计有 90mm、110mm 双盖革计数管槽位，固件支持前端配置校准系数与报警阈值，可以支持多种规格制式的盖革计数管，详细支持列表见下文使用说明部分表格。

本设计除硬件设计外，还有配套中文固件（当前提供已编译文件，源代码将于 2023 年第三季度开源）、亚克力外壳设计、电池板（已预留连接位及定位孔，预计 2023 年内开源）。

## 🍭 使用说明

本设计在采购及焊接阶段应该注意的细节均已在原理图中特别标注，请注意查阅。

`LCD BK Light` 为 ILI9341 显示屏的背光调节电位器，可以调整显示屏的背光亮度，但注意不要过亮，可能会导致品控不良的显示屏排线侧温度过高从而烧毁显示屏。

`DC Voltage` 为盖革计数管两端电压调节电位器，用以适配不同的盖革计数管管型，具体的盖革计数管型号 - 工作电压对应关系见下文表格。**请注意：只有在电压调节完成后才能安装盖革计数管，否则你的盖革计数管将有可能被过大的电压击穿损毁。**

在安装盖革计数管时，推荐使用可拆卸式安装，因为盖革计数管相对较为贵重。最简单的安装方式为扎带窟住双侧电极（已预留开槽），使电极金属部分贴于板上喷锡焊盘位置（注意不要过于追求扎带的紧实，以防产生形变从而影响盖革计数管的真空气密性），实测此种安装方式足够稳固且成本低廉。

当前发布的固件将会上传于 [立创开源硬件平台工程附件](https://oshwhub.com/yanranxiaoxi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type) 内，烧录固件建议使用 [乐鑫科技 Flash 下载工具](https://www.espressif.com.cn/zh-hans/support/download/other-tools?keys=Flash+%E4%B8%8B%E8%BD%BD%E5%B7%A5%E5%85%B7)。

在固件烧录完成后，建议按照下表中的盖革计数管型号 - 校准系数对应关系调整校准系数（`显示屏` -> `设置` -> `校正` -> `计算系数`），如果你有测试更多的盖革计数管型号，或有其它针对性建议，可以直接在 [立创开源硬件平台](https://oshwhub.com/yanranxiaoxi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type) 或 [GitHub](https://github.com/yanranxiaoxi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/issues) 提出。

| 盖革计数管型号 | 管壳材料 | 推荐校准系数（单位：CPM/uSv/hr） | 工作电压（单位：V） | 坪区范围（单位：V） | 本底（单位：次/min） | 极限电压（单位：V） | 备注         |
| -------------- | -------- | -------------------------------- | ------------------- | ------------------- | -------------------- | ------------------- | ------------ |
| J305βγ         | 玻璃     | 210                              | 380                 | 360-440             | 25                   | 550                 | 推荐，已测试 |
| M4011          | 玻璃     | 200                              | 380                 | 360-440             | 25                   | 600                 | 已测试       |
| J321βγ         | 玻璃     | 200                              | 380                 | 360-440             | 25                   | 600                 |              |
| SBM-20         | 不锈钢   | 175                              | 400                 | 350-475             | 60                   | 475                 | 已测试       |
| STS-5          | 不锈钢   | 175                              | 400                 | 350-475             | 60                   | 475                 |              |

虽然上表中提供了推荐的校准系数，但这 **仍然不会** 让你的盖革计数器输出正确的辐射剂量，这是由于以下几个方面：

1. 盖革计数管在生产时无法保证每根管的灵敏度一致，在专业领域使用的盖革计数管需要进行逐根标定；
2. 盖革计数管对于不同辐射源的灵敏度是不同的，例如 SBM-20 的中心标定 Ra-226 灵敏度是 174CPM/uSv/hr，Co60 灵敏度是 132CPM/uSv/hr；
3. 我们在计数时受盖革计数管本身死区时间及检测上限的影响，在辐射值很低或很高时的读数都是不可信的。

Wi-Fi 及 API 相关功能还处于开发阶段，预计将于 2024 年上线，预期成果是一个由用户自愿数据上传的辐射监测站地图，当然，也就是爱好者们圈地自萌的地方而已，数据的干扰因素非常多，所以数据将完全不可信。

本 PCB 设计已通过完整功能性测试，可直接进行 SMT 贴片生产。但请注意，本设计完整开源并遵循 [Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://choosealicense.com/licenses/cc-by-sa-4.0/) 开源协议，开源作者不对作品的安全性、完整性作任何承诺，且不对因此产生的任何损失承担后果。

本设计的所有元器件封装均为小汐个人绘制，绘制时遵循视觉统一、密尔对齐、手焊优化原则，已在保证贴片可靠的前提下最大限度地降低手工焊接的难度，你可以使用本项目的 [焊接助手](https://interactivehtmlbom.soraharu.com/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type.html) 有效地提升手工焊接效率，本助手通过 [InteractiveHtmlBom](https://gitlab.soraharu.com/XiaoXi/InteractiveHtmlBom) 流水线自动化生成。

## 🛠️ 生产电路板

本项目的 Gerber 文件可以从 [Releases](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/-/releases) 页面获取，并允许在开源许可范围内的商业目的使用。

*建议使用 [嘉立创](https://www.jlc.com/) 生产高品质电路板。

*It is recommended to use [JLCPCB](https://jlcpcb.com/) to produce high-quality circuit boards.

## 🔩 生产外壳（亚克力）

🎉 2023 年 03 月 30 日，亚克力外壳设计已正式发布，现在可以借助简单的亚克力切割工艺生产外壳啦！

> Warning
>
> 如欲装配当前版本的外壳，因为空间限制问题，在焊接 ILI9341 显示屏时需要将其排线尽可能向高压区方向靠近，否则可能导致显示屏排线阻挡外壳 `中夹板` 部分，影响最终美观性。
>
> *此问题的修正当前处在验证阶段。*

你可以在工程中找到四个带有「面板」标记的 PCB 设计，这些设计仅有边框层，分别为 `顶板`、`中夹板`、`底板` 以及 `垫片`，一块 MWGC-2T 需要使用 `4×垫片`、`1×顶板`、`1×中夹板` 以及 `1×底板`。

以下生产步骤以 [嘉立创面板打印服务](https://dos.szlcsc.com/) 为例：

1. 首先，你需要分别打开四个面板设计，将它们全部导出为 `dxf` 格式文件，并打包为 `zip` 格式文件；
2. 接下来，前往 [嘉立创面板打印服务下单页面](https://dos.szlcsc.com/dos/panel/print.html) 参考以下参数定制面板（当然，如果你知道自己在干什么的话，可以按照自己的想法来）：

	- 计价产品：`亚克力面板`
	- 定制材料：`透明亚克力`
	- 打印方式：`无打印`
	- 材料厚度：`2.8mm`
	- 材料尺寸：`200mm×300mm`
	- 3M 背胶：`不需要背胶`
	- 遮光程度：`常规`
	- 备注信息：`无打印，纯切割，参考「顶板」、「底板」的最大长宽均为 10cm，顶板、底板、中夹板各拼 2 片，垫片至少需要 8 片`

3. 将你刚才打包的文件上传至平台并完成后续的常规信息流程。

在完成亚克力外壳的下单流程后，你还需要购买适配的五金连接件，以下是测试完成后的最简推荐清单：

| 类型           | 型号  | 数量 |
| -------------- | ----- | ---- |
| 双通六角铜柱   | M3*9  | 3    |
| 沉头十字铜螺丝 | M3*12 | 6    |

如果希望减少亚克力垫片的用量，且使主板与放置平面完全隔离，可以参考以下推荐清单：

| 类型           | 型号         | 数量 |
| -------------- | ------------ | ---- |
| 双通六角铜柱   | M3*9         | 3    |
| 沉头十字铜螺丝 | M3*10        | 3    |
| 六角铜螺母     | M3 (M3*2.55) | 3    |
| 单通六角尼龙柱 | M3*5+6       | 3    |

最后，你还需要使用背胶将显示屏与中夹板贴合，我使用的是 **3M 4910VHB** 型号，不作太多推荐，以下是几个选型参考因素：透明、厚度薄、亚克力与不锈钢平面材质粘黏。

## ⚙️ 部署至嘉立创 EDA

1. 克隆本项目 [源代码](https://gitlab.soraharu.com/XiaoXi/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type/-/archive/master/Multi-adaptation-Wi-Fi-Geiger-Counter-Double-Tube-Type-master.zip) 到本地
2. 在嘉立创 EDA 标准版编辑器中选择 `文件` -> `打开` -> `嘉立创EDA...`
3. 选择本项目源代码中的 `/EasyEDA/*.json` 文件并分别导入

## 📜 开源许可

基于 [Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://choosealicense.com/licenses/cc-by-sa-4.0/) 许可进行开源。

本设计已在 [中国版权保护中心](https://www.ccopyright.com.cn/) 登记注册，商业支持及定制化可联系 [admin@soraharu.com](mailto:admin@soraharu.com)。
