# 德国投资税务搜索策略

## 何时读取本文件

当德国投资运营初筛需要检索税务、劳动用工、企业设立、董事责任、PE、VAT、TP 或欧盟税务材料时，必须先读取本文件。

## 本文件影响什么决策

本文件决定官方 URL 速查、德国官方域名、BMF / BFH / 企业登记和欧盟来源的执行顺序，以及搜索失败后的降级动作。

## 不适用场景

用户已经提供足够可定位官方材料、只需整理报告，或仅需查询官方入口列表时，不以本文件替代来源核验文件。

> 本文件是 `legato-germany-investment-tax-compliance` 自带的搜索策略指引。
> 目标是把"官方来源优先"的抽象原则翻译为 Agent 可逐步执行的具体搜索链路。
> 本 Skill 独立打包时不得依赖上级目录、兄弟目录或外部共享文件。

## 1. 搜索顺序

对每个子问题，Agent 必须按以下顺序执行搜索，不得跳过前序步骤直接泛搜：

### 第 1 步：official-source-verification.md 官方 URL 速查

查本 Skill 目录内 `references/official-source-verification.md` 的第 1 节和第 4 节，看该税务主题是否有已核验的官方来源 URL。

如有，优先直接访问该 URL 获取官方口径。已核验的 URL 包括：

- BMAS Mindestlohn 页面（最低工资）
- NachwG 官方文本（书面形式要求）
- BMF 2024 转让定价行政原则（转让定价）
- 中德税收协定官方页面和 PDF（PE、股息、利息、特许权使用费）

### 第 2 步：德国法规库联网核验

从 `official-source-verification.md` 中未覆盖的税务主题，在以下官方域名中搜索：

| 域名 | 用途 | 说明 |
| --- | --- | --- |
| `gesetze-im-internet.de` | 联邦法规原文 | 覆盖 EStG、KStG、GewStG、UStG、AO、GmbHG 等核心税法 |
| `bundesfinanzministerium.de` | 财政部 BMF | 行政指引、通知、国际税收协定、转让定价指引 |
| `bundesfinanzhof.de` | 联邦财政法院 BFH | 税务判例、裁判要旨 |
| `unternehmensregister.de` | 企业登记 | 公司注册信息、财务报告 |
| `eur-lex.europa.eu` | 欧盟法律 | EU 税务指令（ATAD、Pillar Two、VAT Directive） |
| `ec.europa.eu/taxation_customs` | 欧委会税务海关 | EU 税务政策动态 |

使用域名限定搜索（如 `site:gesetze-im-internet.de`）在官方来源中检索。

目标是找到官方法规原文、财政部指引、法院判例或主管机关办事指南。

### 第 3 步：高质量税务指南搜索

官方域名无结果或覆盖不足时，在以下高质量税务指南中搜索：

- Chambers Practice Guides - Germany Tax（完全免费，无需注册）
- ICLG - Corporate Tax / Transfer Pricing - Germany（免费注册后可阅读全文）
- Legal500 - Germany Tax Country Guide（完全免费，无需注册）
- Deloitte / EY / PwC / KPMG - Germany Tax Facts（会计师事务所年度税务手册）

这些来源用于搭框架、做比较和识别需要官方核验的关键点，不替代官方来源。

### 第 4 步：国际所税务实务文章搜索

对时效性热点问题（近期税法修订、新行政指引、BFH 新判例），在国际所和本地强所的网站或聚合平台中搜索 tax update / client alert：

- 优先使用 Lexology 作为发现工具：在 Lexology 上找到相关文章标题和作者后，去律所官网查找免费全文
- 直接在主要律所官网搜索（Baker McKenzie、Clifford Chance、Freshfields、Linklaters、Allen & Overy 等德国办公室）

### 第 5 步：中文律所和财税实务文章搜索

对中国投资者视角的德国税务实务文章：

```
德国 投资 税务 {关键词} site:wechat.qq.com 金杜 OR 中伦 OR 方达 OR 锦天城
德国 税务 {关键词} 走出去智库 OR CGG
```

中文来源用于理解中国投资者关注点和实务框架，不作为决定性依据。

### 第 6 步：开放搜索

以上步骤均不足时，使用开放搜索补充。但结论强度自动降级，输出中必须标注为"待确认"。

## 2. 各步骤失败后的处理链

| 失败情况 | 下一步动作 | 输出要求 |
| --- | --- | --- |
| official-source-verification.md 无该主题覆盖 | 跳过，进入第 2 步 | 记录"该主题尚未核验，以下结论基于联网检索" |
| 已核验 URL 失效（404/改版） | 进入第 2 步在法规库中重新搜索 | 不因 URL 失效就放弃该主题官方来源 |
| 德国法规库搜索无结果 | 不写"该规则不存在"，进入第 3 步 | 标注"官方来源未检索到，以下结论基于二手来源" |
| 法规库仅返回德语结果 | 使用浏览器翻译辅助理解，关键条文保留原文 | 注明"原文为德语，以下为辅助翻译" |
| 高质量指南无该税务主题覆盖 | 进入第 4 步或第 5 步 | 结论强度降为"待确认" |
| 开放搜索仅找到中文文章 | 用作问题理解框架 | 不作为决定性依据，标注"仅找到中文解读，需官方来源核验" |
| 开放搜索仅找到新闻或媒体 | 仅作为动态信号 | 结论标为"待确认"，不可单独支撑税务结论 |
| 来源之间存在冲突 | 比较效力层级、发布时间、适用范围 | 无法收口时标为"不明确"或"需德国税务顾问确认" |

## 3. 时效性前置判断

德国税法时效性总体为"高"，启动研究时应先判断该子领域属于哪一级时效敏感度：

| 敏感度 | 典型领域 | 来源有效期窗口 | 行为要求 |
| --- | --- | --- | --- |
| 极高 | 税率变动（如 KSt 税率、GewSt Hebesatz 区域差异）、新税收优惠（如 Forschungszulage）、最新 BMF 通知、EU 新指令转化 | 3-6 个月 | 在执行摘要中加醒目时效警告；推荐用户直接查阅官方最新来源；明确说明指南可能已过时 |
| 高 | 反避税规则修订（Hinzurechnungsbesteuerung、ATAD 转化）、转让定价文档要求（BMF 2024 VWG）、预提税变动、Pillar Two GloBE | 6-12 个月 | 注明所有来源的发布日期；关键结论建议交叉验证至少两个来源 |
| 中 | GmbH/AG 设立框架、中德税收协定（已签署文本）、商法/公司法框架 | 1-3 年 | 标准来源日期意识；使用指南时注明年份 |
| 低 | 基本税法结构（所得税分类、法人实体类型）、法律体系结构 | 相对稳定 | 时效性不是关键问题，但仍应注明来源日期 |

对"极高"敏感度领域，报告的执行摘要和结论限制中必须包含：

> 本领域规则变化频繁。以下信息基于截至 [日期] 的来源，可能未反映最新变化。建议直接查阅官方最新来源或咨询德国税务顾问（Steuerberater）。

## 4. 德语搜索提示

部分德国税法关键内容仅在德语来源中有完整覆盖，Agent 应注意：

| 中文主题 | 德语关键词示例 |
| --- | --- |
| 公司所得税 | Körperschaftsteuer, KStG |
| 营业税/贸易税 | Gewerbesteuer, GewStG, Hebesatz |
| 增值税 | Umsatzsteuer, UStG, Mehrwertsteuer |
| 个人所得税 | Einkommensteuer, EStG |
| 预提税 | Abzugsteuer, Quellensteuer |
| 转让定价 | Verrechnungspreise |
| 常设机构 | Betriebsstätte |
| 参与免税 | Schachtelprivileg, § 8b KStG |
| 反避税/受控外国公司 | Hinzurechnungsbesteuerung, Außensteuergesetz, AStG |
| 税收协定 | Doppelbesteuerungsabkommen, DBA |
| 破产/资不抵债 | Insolvenz |
| 商事登记 | Handelsregister |
| 最低工资 | Mindestlohn |

当英语搜索无结果时，使用德语关键词在 `gesetze-im-internet.de` 或 `bundesfinanzministerium.de` 中搜索。

## 5. 结论强度标注

根据搜索链路中的来源覆盖情况，在报告中标注结论强度：

| 情况 | 结论强度 |
| --- | --- |
| 有 official-source-verification.md 已核验口径 + 用户事实足够 | 可输出确定性较高的结论 |
| 有官方法规原文 + 用户事实足够 | 可输出决定性结论 |
| 有官方法规但用户事实不足 | 输出假设下的结论和事实缺口 |
| 仅有高质量指南 | 输出框架性结论，标注需官方核验 |
| 仅有实务文章或中文来源 | 输出实务信号，不输出法律结论 |
| 来源冲突或最新规则不明 | 降级为待核验，提示人工复核 |

## 6. 人工复核触发条件

以下情况必须触发人工复核提示：

- 涉及具体税率、有效税负计算或税收优惠的精确数值。
- 涉及税收协定解释和适用（特别是 PE 判断、预提税率适用）。
- 涉及反避税条款适用（Hinzurechnungsbesteuerung、AStG、ATAD）。
- 涉及转让定价方法选择和基准分析。
- 涉及 GmbH/Geschäftsführer 个人责任和破产义务。
- 仅找到中文来源或二手来源，未取得德语官方原文。
- 用户需要对外承诺、合同签署、监管沟通或正式税务意见。
