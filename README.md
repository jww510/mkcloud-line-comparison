# mkcloud 线路对比：按出口方向与接入方式选对香港/日本/美国专线

打开 Mkcloud 商店页，云服务器线路会让人有点头晕。"广东-香港 IEPL"、"沪日 IPLC"、"沪港 IPLC"、"沪美 IPLC"、"福建-香港 高防 IPLC"、"上海 CN2"——这些不是营销话术，而是出口方向、入口省份、计费模型、共享还是独享的不同组合。如果只看名字和数字，很容易买错。等到正式跑业务时延迟对不上、流量包不够用、独享档撑不起来，才发现原本只是选错了线路。

下面的内容基于当前 [Mkcloud 官网商店](https://www.mkcloud.net/)及知识库文章的公开资料整理，把"广港、深港IX、沪港、沪港IX、沪港独享、沪日、沪日独享、沪美独享、上海 CN2、港法 IPLC"等线放在一起对比，按出口方向、接入方式、计费方式三个维度拆开，方便看清每条线实际适合谁。

## 一、先看全貌：Mkcloud 的线路不是"大小排序"

Mkcloud 主页上写的是"上云互联优化专线、广港 IEPL、沪日 IPLC、沪美 IPLC 和港法 IPLC 等多种专线服务"，但实际上当前商店把在售线路分成了 6 个出口地区：

| 出口地区 | 系列类型 | 端内参考延迟 |
| --- | --- | --- |
| 广东-香港 | IEPL 专线 | 1~2ms |
| 上海-香港 | IPLC（共享/独享） | 21ms |
| 上海-日本 | IPLC（共享/独享） | 25~28ms |
| 上海-美国 | IPLC（独享） | 124~134ms |
| 福建-香港 | 高防 IPLC | 1~2ms |
| 上海 CN2 | 国内优化 | 国内出站 |

这些延迟数字来自 Mkcloud 产品资料的端内参考，并不等于你从本地宽带跑到目标网站的全链路延迟，也不是 SLA 承诺。把它理解成"出口到接入点之间的参考值"比较合适。

> **重要提醒**：所有专线 VPS 均采用省级白名单措施，每个产品只允许一个省份的 IP 连入（CX/IX 系列除外）。后续可以自行切换绑定省份。

## 二、按出口方向选：港、日、美各走哪条

业务最终要访问的目标决定了出口方向，再倒推到线路。

**香港方向**：从香港出口对应华南对港团队、独立站、亚马逊、TikTok Shop 多账号运营、金融量化对港等。最常见的是"广港 IEPL"和"沪港 IPLC"，分别对应广州和上海入口。如果已有符合条件的云厂前置机，深港IX 或沪港IX 是更便宜的选项，但需要把云前置机费用算进去。

**日本方向**：从日本出口，常用于雅虎、乐天、日本亚马逊等本地平台，以及手游与电商素材回传。Mkcloud 只有"沪日 IPLC"一条线，对应上海电信或上海 BGP 入口，端内 25~28ms。

**美国方向**：从美国出口，包括亚马逊美国、TikTok 美区、独立站全球用户、ERP/PUSH 等持续上行场景。Mkcloud 的"沪美 IPLC"目前以独享带宽款为主，按 5M/10M/20M/50M/100M 配置，端内 124~134ms。

**国内优化**：上海 CN2 不是香港/日本/美国的替代品，而是给"接受动态 IP、需要国内出站组合"的用户准备的，比如已经用海外线路但内部系统需要走 CN2 的场景。

按出口与入口匹配后，剩下要选的就是"直连还是 IX"、"共享还是独享"。这两个选择决定了价格、接入方式和实际表现。

## 三、直连 vs IX（云前置）：接入方式决定价格

直连款适合"本地宽带+一台 VPS"的常见用法。每个入口绑定一个省份，只有当前绑定省份的 IP 可连入，使用地点变化时可以自己切换绑定省份。

IX（即"上云互联优化入口"）适合"已有云厂机器+专线 VPS"的用法。不限连入省份，但必须从支持范围内的云厂机器和网络接入。购买时要把云前置机的费用、配置和管理成本一起算上，不能只看 Mkcloud 套餐报价。

Mkcloud 的 IX 支持范围当前覆盖：阿里云国内全网（已部分下架）、腾讯云国内全网、百度云国内全网、火山云华东/华南、华为云华东/华南、UCloud 华东。以官方页面公告为准，下单前建议先确认自家的云厂、地域和网络环境是否一致。

如果不满足前置条件而硬买 IX，结果是根本无法连入。这是"线路对比"中最容易踩的坑。

> **选资金提示**：没有符合条件的云厂就别买 IX。广港直连起步 ¥358/月，沪港独享起步 ¥388/月，对 1~2ms / 21ms 端内参考不刚需且用量不大的用户来说够用。

## 四、共享 vs 独享：带宽数字不是唯一比较项

共享带宽和独享带宽是两种计费，不是"质量排序"。

**共享（流量计费）**：按峰值带宽和月流量选择。适合可以估算用量、传输集中在一段时间的任务。共享带宽不保证持续跑满；月流量按上行与下行双向统计。

**独享（带宽计费）**：按配置的带宽选择，不设月流量额度。适合需要长时间保持一定传输速率的任务。

以沪港入门为例：共享版 1 核 2GB 20GB 200Mbps 峰值 + 1024GB 月流量，月付 ¥288；独享版 2 核 4GB 40GB 5Mbps 不限流量，月付 ¥388。共享看重短时峰值，独享看重持续速率与不设上限。协议、磁盘、CPU 和对方限速都会影响实际速度。

> 重要提醒：所有专线 VPS 在购买后均不支持更换到其他地域的产品。

## 五、按入口选择：上海、广州、福建差异在哪

入口决定"从哪里连进去"和"端内参考延迟"。

- **广州入口（腾讯广州八线BGP）**：出口至香港，端内 1~2ms。华南团队或华南云厂前置时优先。
- **上海电信入口**：出口至香港 21ms，出口至日本 25~28ms。上海本地宽带或长三角团队优先。
- **UCloud 上海BGP / 上云互联优化入口**：沪港独享和沪美独享系列端内参考与上海电信一致，21ms 或 124~134ms，但走的是云厂网络通道。
- **福建入口（厦港/泉港）**：端内 1~2ms，且为高防 IPLC，适合福建本地或需要 DDoS 防护的场景。厦港/泉港是独立款，档位与广港不通用，确认防护范围、工单细节后再下单。

> 重要提醒：300G 高防目前为广东三线 IEPL 200M-2000M 独享产品的能力（28核64GB512GB配置）。厦港/泉港 的高防口径与门槛以官方公告为准，触发条件当前未公开。

## 六、Mkcloud 全线路套餐对比表

下面这张表覆盖官网商店当前公开展示的全部主要线路。点击套餐锚链接即可跳转到对应购买页，参数持续按 mb/Mbps 计算，部分套餐按 GB/TB 流量或无月额区分。

### 1. 广东-香港 IEPL 专线（广州BGP / 直连）

| 套餐 | CPU | 内存 | 硬盘 | 峰值带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1TB 流量款 | 1 核 | 2GB | 20GB | 200Mbps | 1TB | ¥358 | [ 选购广港 IEPL 1TB 专线](https://www.mkcloud.net/index.php/store/gz-hk-sh?aff=390) |
| 2TB 流量款 | 2 核 | 4GB | 40GB | 300Mbps | 2TB | ¥568 | [ 选购广港 IEPL 2TB 专线](https://www.mkcloud.net/index.php/store/gz-hk-sh?aff=390) |
| 4TB 流量款 | 2 核 | 4GB | 40GB | 300Mbps | 4TB | ¥998 | [ 选购广港 IEPL 4TB 专线](https://www.mkcloud.net/index.php/store/gz-hk-sh?aff=390) |
| 6TB 流量款 | 4 核 | 8GB | 60GB | 500Mbps | 6TB | ¥1388 | [ 选购广港 IEPL 6TB 专线](https://www.mkcloud.net/index.php/store/gz-hk-sh?aff=390) |
| 10TB 流量款 | 4 核 | 8GB | 60GB | 500Mbps | 10TB | ¥2288 | [ 选购广港 IEPL 10TB 专线](https://www.mkcloud.net/index.php/store/gz-hk-sh?aff=390) |
| 20TB 流量款 | 4 核 | 8GB | 60GB | 1Gbps | 20TB | ¥4500 | [ 选购广港 IEPL 20TB 专线](https://www.mkcloud.net/index.php/store/gz-hk-sh?aff=390) |

入口腾讯广州八线BGP，出口香港BGP，端内 1~2ms，独享 IPv4×2。

### 2. 广东-香港 IEPL（IX / 上云互联优化入口）

| 套餐 | CPU | 内存 | 硬盘 | 峰值带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2TB 流量款 | 2 核 | 4GB | 40GB | 1Gbps | 2TB | ¥158 | [ 选购深港 IX 2TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 4TB 流量款 | 2 核 | 4GB | 40GB | 1Gbps | 4TB | ¥258 | [ 选购深港 IX 4TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 6TB 流量款 | 4 核 | 8GB | 40GB | 2Gbps | 6TB | ¥378 | [ 选购深港 IX 6TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 10TB 流量款 | 4 核 | 8GB | 40GB | 2Gbps | 10TB | ¥826 | [ 选购深港 IX 10TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 20TB 流量款 | 4 核 | 8GB | 40GB | 2Gbps | 20TB | ¥1639 | [ 选购深港 IX 20TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 30TB 流量款 | 4 核 | 8GB | 60GB | 3Gbps | 30TB | ¥2458 | [ 选购深港 IX 30TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 50TB 流量款 | 8 核 | 8GB | 60GB | 3Gbps | 50TB | ¥3588 | [ 选购深港 IX 50TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 100TB 流量款 | 8 核 | 16GB | 80GB | 5Gbps | 100TB | ¥7168 | [ 选购深港 IX 100TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 200TB 流量款 | 8 核 | 16GB | 80GB | 5Gbps | 200TB | ¥12288 | [ 选购深港 IX 200TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |
| 300TB 流量款 | 8 核 | 16GB | 80GB | 5Gbps | 300TB | ¥18428 | [ 选购深港 IX 300TB 专线](https://www.mkcloud.net/index.php/store/cloud-hk-sh?aff=390) |

入口云厂优化网络通道，出口香港BGP，端内 1~2ms，必须从支持的云厂网络接入。

### 3. 上海-香港 IPLC（上海电信 / 直连）

| 套餐 | CPU | 内存 | 硬盘 | 峰值带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1TB 流量款 | 1 核 | 2GB | 20GB | 200Mbps | 1TB | ¥288 | [ 选购沪港 IPLC 1TB 专线](https://www.mkcloud.net/index.php/store/sh-hk-sh?aff=390) |
| 2TB 流量款 | 2 核 | 4GB | 40GB | 300Mbps | 2TB | ¥428 | [ 选购沪港 IPLC 2TB 专线](https://www.mkcloud.net/index.php/store/sh-hk-sh?aff=390) |
| 4TB 流量款 | 2 核 | 4GB | 40GB | 300Mbps | 4TB | ¥696 | [ 选购沪港 IPLC 4TB 专线](https://www.mkcloud.net/index.php/store/sh-hk-sh?aff=390) |
| 6TB 流量款 | 4 核 | 8GB | 60GB | 500Mbps | 6TB | ¥988 | [ 选购沪港 IPLC 6TB 专线](https://www.mkcloud.net/index.php/store/sh-hk-sh?aff=390) |
| 10TB 流量款 | 4 核 | 8GB | 60GB | 500Mbps | 10TB | ¥1536 | [ 选购沪港 IPLC 10TB 专线](https://www.mkcloud.net/index.php/store/sh-hk-sh?aff=390) |
| 20TB 流量款 | 4 核 | 8GB | 60GB | 1Gbps | 20TB | ¥3072 | [ 选购沪港 IPLC 20TB 专线](https://www.mkcloud.net/index.php/store/sh-hk-sh?aff=390) |

入口上海电信，出口香港BGP，端内 21ms。

### 4. 上海-香港 IPLC（IX / 上云互联优化入口）

| 套餐 | CPU | 内存 | 硬盘 | 峰值带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2TB 流量款 | 2 核 | 4GB | 40GB | 500Mbps | 2TB | ¥198 | [ 选购沪港 IX 2TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |
| 3TB 流量款 | 2 核 | 4GB | 40GB | 500Mbps | 3TB | ¥288 | [ 选购沪港 IX 3TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |
| 6TB 流量款 | 4 核 | 8GB | 40GB | 1Gbps | 6TB | ¥398 | [ 选购沪港 IX 6TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |
| 10TB 流量款 | 4 核 | 8GB | 40GB | 1Gbps | 10TB | ¥666 | [ 选购沪港 IX 10TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |
| 20TB 流量款 | 4 核 | 8GB | 40GB | 1Gbps | 20TB | ¥1290 | [ 选购沪港 IX 20TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |
| 30TB 流量款 | 4 核 | 8GB | 60GB | 2Gbps | 30TB | ¥1900 | [ 选购沪港 IX 30TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |
| 50TB 流量款 | 8 核 | 8GB | 60GB | 2Gbps | 50TB | ¥3120 | [ 选购沪港 IX 50TB 专线](https://www.mkcloud.net/index.php/store/cloud-sh-hk-sh?aff=390) |

入口云厂优化网络通道，出口香港BGP，端内 21ms。

### 5. 上海-香港 IPLC 独享带宽（上海BGP）

| 套餐 | CPU | 内存 | 硬盘 | 独享带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 5M 独享 | 2 核 | 4GB | 40GB | 5Mbps | 无限制 | ¥650 | [ 选购沪港 5M 独享专线](https://www.mkcloud.net/index.php/store/sh-hk-ex?aff=390) |
| 10M 独享 | 2 核 | 4GB | 40GB | 10Mbps | 无限制 | ¥950 | [ 选购沪港 10M 独享专线](https://www.mkcloud.net/index.php/store/sh-hk-ex?aff=390) |
| 20M 独享 | 2 核 | 4GB | 40GB | 20Mbps | 无限制 | ¥1760 | [ 选购沪港 20M 独享专线](https://www.mkcloud.net/index.php/store/sh-hk-ex?aff=390) |
| 50M 独享 | 4 核 | 8GB | 60GB | 50Mbps | 无限制 | ¥4000 | [ 选购沪港 50M 独享专线](https://www.mkcloud.net/index.php/store/sh-hk-ex?aff=390) |
| 100M 独享 | 4 核 | 8GB | 60GB | 100Mbps | 无限制 | ¥7500 | [ 选购沪港 100M 独享专线](https://www.mkcloud.net/index.php/store/sh-hk-ex?aff=390) |

入口UCloud上海BGP，出口香港BGP，端内 21ms。

### 6. 上海-日本 IPLC（上海电信 / 共享）

| 套餐 | CPU | 内存 | 硬盘 | 峰值带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 500GB 流量款 | 1 核 | 2GB | 20GB | 150Mbps | 500GB | ¥228 | [ 选购沪日 500GB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |
| 1TB 流量款 | 1 核 | 2GB | 20GB | 200Mbps | 1TB | ¥358 | [ 选购沪日 1TB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |
| 2TB 流量款 | 2 核 | 4GB | 40GB | 300Mbps | 2TB | ¥568 | [ 选购沪日 2TB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |
| 4TB 流量款 | 2 核 | 4GB | 40GB | 300Mbps | 4TB | ¥998 | [ 选购沪日 4TB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |
| 6TB 流量款 | 4 核 | 8GB | 60GB | 500Mbps | 6TB | ¥1388 | [ 选购沪日 6TB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |
| 10TB 流量款 | 4 核 | 8GB | 60GB | 500Mbps | 10TB | ¥2288 | [ 选购沪日 10TB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |
| 20TB 流量款 | 4 核 | 8GB | 60GB | 1Gbps | 20TB | ¥4500 | [ 选购沪日 20TB 专线](https://www.mkcloud.net/index.php/store/sh-jp-sh?aff=390) |

入口上海电信，出口日本BGP，端内 25~28ms。

### 7. 上海-日本 IPLC 独享带宽（上海电信）

| 套餐 | CPU | 内存 | 硬盘 | 独享带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 5M 独享 | 2 核 | 4GB | 40GB | 5Mbps | 无限制 | ¥600 | [ 选购沪日 5M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |
| 10M 独享 | 2 核 | 4GB | 40GB | 10Mbps | 无限制 | ¥800 | [ 选购沪日 10M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |
| 20M 独享 | 2 核 | 4GB | 40GB | 20Mbps | 无限制 | ¥1560 | [ 选购沪日 20M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |
| 50M 独享 | 4 核 | 8GB | 60GB | 50Mbps | 无限制 | ¥3500 | [ 选购沪日 50M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |
| 100M 独享 | 4 核 | 8GB | 60GB | 100Mbps | 无限制 | ¥6000 | [ 选购沪日 100M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |
| 200M 独享 | 4 核 | 8GB | 60GB | 200Mbps | 无限制 | ¥12000 | [ 选购沪日 200M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |
| 300M 独享 | 4 核 | 8GB | 60GB | 300Mbps | 无限制 | ¥18000 | [ 选购沪日 300M 独享专线](https://www.mkcloud.net/index.php/store/sh-jp-ex?aff=390) |

入口上海电信，出口日本BGP，端内 25~28ms。

### 8. 上海-美国 IPLC 独享带宽（上海BGP）

| 套餐 | CPU | 内存 | 硬盘 | 独享带宽 | 月流量 | 月付 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 5M 独享 | 2 核 | 4GB | 40GB | 5Mbps | 无限制 | ¥850 | [ 选购沪美 5M 独享专线](https://www.mkcloud.net/index.php/store/shh-us-ex?aff=390) |
| 10M 独享 | 2 核 | 4GB | 40GB | 10Mbps | 无限制 | ¥1300 | [ 选购沪美 10M 独享专线](https://www.mkcloud.net/index.php/store/shh-us-ex?aff=390) |
| 20M 独享 | 2 核 | 4GB | 40GB | 20Mbps | 无限制 | ¥2560 | [ 选购沪美 20M 独享专线](https://www.mkcloud.net/index.php/store/shh-us-ex?aff=390) |
| 50M 独享 | 4 核 | 8GB | 60GB | 50Mbps | 无限制 | ¥6000 | [ 选购沪美 50M 独享专线](https://www.mkcloud.net/index.php/store/shh-us-ex?aff=390) |
| 100M 独享 | 4 核 | 8GB | 60GB | 100Mbps | 无限制 | ¥11500 | [ 选购沪美 100M 独享专线](https://www.mkcloud.net/index.php/store/shh-us-ex?aff=390) |

入口UCloud上海BGP，出口美国BGP，端内 124~134ms。

### 9. 上海 CN2（国内优化）

首页标注起步价为 ¥4500/月，详情以 [👉 进入上海 CN2 选购页](https://www.mkcloud.net/index.php/store/cn2-sh?aff=390) 当下展示为准。该产品属于上海动态联通入口 + 上海电信 CN2 出口，不是香港/日本/美国的替代品。

### 10. 大带宽独享系列（广东三线 IEPL + 300G 高防）

这是 28核64GB512GB 配置的大带宽独享，起步月付约 ¥17000（1Gbps）、¥32000（2Gbps）、¥75000（5Gbps），自带有 300G DDoS 防护口径。详情请看 [👉 进入广东三线 IEPL 大带宽独享选购页](https://bit.ly/MKCLoud)。

> 上述价格均为月付首月档，仅作预算参考。季付、年付、两年、三年等档位的总价/折扣以下单页面结算结果为准。

## 七、共享与独享的预算示例

光看 Mbps 数字很容易选过头，下面是两个对照例子：

- **沪港共享入门**：1 核 / 2GB / 20GB / 200Mbps 峰值 / 1024GB 月流量 / 月付 ¥288。适合每天集中 1~2 小时上传下载，普通亚马逊店铺运营够用。
- **沪港独享入门**：2 核 / 4GB / 40GB / 5Mbps / 无限流量 / 月付 ¥388。200Mbps 峰值和 5Mbps 是不同的"计费资源"：前者短时峰值更高，后者长时间保持速率且无上限。适合持续上行（直播推流、PUSH 拉流）场景。
- **沪美 50M 独享**：4 核 / 8GB / 60GB / 50Mbps 独享 / 无月流量，¥6000/月。跨境 ERP/视频素材长期上行最常见档位。

如果是 IX 系列，则还需要把云前置机的费用算进来。比如深港 IX 2TB 月付 ¥158，但云前置机的腾讯云/UCloud 月费另算。预算不能漏这一段。

> **预算提醒**：预算应覆盖套餐、接入和所需服务三个部分。共享套餐按"上行 + 下行"双向计量；不限流量不等于不限速，也不要把默认套餐默认成"包含 SLA"。如果需要 SLA、定制路由，应单独确认费用和交付范围。

## 八、常见选择误区

**误区 1：端内延迟最低就是最合适**。广港 1~2ms、沪港 21ms、沪日 25~28ms、沪美 124~134ms，这是出口到接入点之间的参考。在"沪港 IPLC 独享"和"沪美 5M 独享"中间选时，不能只看延迟，还要看带宽档位、流量包和 CPU/内存是否跑得动。

**误区 2：以为共享 = 共享 IP**。Mkcloud 共享和独享两种套餐每台 VPS 都分配 1 个独立入口 IP 和 1 个独立出口 IP。共享和独享的区别在带宽计费模型，不是 IP 是否独享。

**误区 3：从家宽也能连 IX**。IX 必须从支持范围内的云厂机器和网络接入。如果只有家用宽带，应该选直连款（绑定一个省份），别想用 IX 套到普通家宽上。

**误区 4：以为专线可以搭公开站点**。Mkcloud 当前专线产品出口用于向外访问，不接受外部连入。公开网站、邮件接收、支付回调、公网游戏服务端需要另选支持入站的产品。

**误区 5：把"全站最低价"当成"任何线路的最低价"**。158 元/月是深港 IX 共享 2TB 流量款，不是沪港独享、厦港高防或上海 CN2 的价。每条线起步价都不一样，盲用最低价会买错线路。

> **退款说明**：本页所有产品仅支持质量问题退款，需要在工单中提交延迟/速度测试截图与具体问题，由 Mkcloud 审核判断；服务开通后不支持更换到其他地域。

## 九、结论：哪类需求该选哪条

把上面的维度收一收，得到一个相对直接的对照：

- **华南团队，间歇性对港访问**：广港 IEPL 共享。1TB 起步 ¥358，地理优势明显。
- **上海/长三角，日常对港**：沪港 IPLC 共享。1TB 起步 ¥288；或深港 IX 共享给云前置方案。
- **对港持续传输（直播、PUSH、量化）**：沪港 IPLC 独享 5M/10M，按带宽档选。
- **日本方向（雅虎、乐天、日本亚马逊）**：沪日 IPLC 共享或独享。共同点是走上海电信进出。
- **美国方向（亚马逊美区、独立站素材、PUSH）**：沪美 IPLC 独享，按 5M/20M/50M/100M 配置明确选了。
- **已有云厂机器、想压成本**：广港/沪港 IX 系列。需要把云前置费用算进来。
- **需要高防或边界保护**：广东三线 IEPL 大带宽独享（28核64GB512GB），或厦港/泉港高防 IPLC（具体口径以官方为准）。
- **国内优化、动态 IP 出站组合**：上海 CN2，不是海外出口替代品。

剩下的事情就很机械：决定出口方向、确认接入方式（家宽/云前置）、估算月用量、选择共享或独享、把沪港/沪日/沪美 当前价格表对一下，按目标档位下单即可。如果用 AFF 链接下单可以拿到 10% 一次性拉新奖励（具体活动状态以官网为准），新用户首单专享优惠码当前主要有 MK-NEW / MK-8.8 / MK-7.8 / IXCLOUD 等，使用时以下单页提示为准。

如果把"线路对比"理解成"端内延迟数字大小的对比"，那很容易买错。把它拆成出口方向、入口、接入方式、计费模型四个变量，对照具体数字选择就清晰得多。
