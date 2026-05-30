# 搜索查询模板（德国投资税务合规）

## 何时读取本文件

当已经确定需要联网搜索，并需要构造德国税务、劳动、企业登记、董事责任、PE、VAT 或转让定价 query 时，读取本文件。

## 本文件影响什么决策

本文件决定德文 / 英文查询词、官方域名限定方式、法规直达模板和主题搜索模板。

## 不适用场景

尚未确定检索策略、已有官方 URL 可直达，或只是在输出报告时，不优先读取本文件。

> 本文件是 `legato-germany-investment-tax-compliance` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{topic}`、`{keyword}` 为占位符，运行时替换为实际值。

## 1. 官方域名限定搜索

### 德国联邦法规库（gesetze-im-internet.de）

```
{keyword} site:gesetze-im-internet.de
{Steuerrecht OR Körperschaftsteuer OR Einkommensteuer OR Umsatzsteuer} site:gesetze-im-internet.de
```

具体法规直达：

| 法规 | 搜索模板 |
| --- | --- |
| 所得税法 EStG | `Einkommensteuergesetz site:gesetze-im-internet.de/estg` |
| 公司法 KStG | `Körperschaftsteuergesetz site:gesetze-im-internet.de/kstg` |
| 营业税 GewStG | `Gewerbesteuergesetz site:gesetze-im-internet.de/gewstg` |
| 增值税 UStG | `Umsatzsteuergesetz site:gesetze-im-internet.de/ustg` |
| 税收通则 AO | `Abgabenordnung site:gesetze-im-internet.de/ao_1977` |
| 有限责任公司法 GmbHG | `GmbH-Gesetz site:gesetze-im-internet.de/gmbhg` |
| 外国税法 AStG | `Außensteuergesetz site:gesetze-im-internet.de/astg` |

### 财政部 BMF

```
{keyword} site:bundesfinanzministerium.de
{keyword} BMF Schreiben OR Verwaltungsgrundsätze site:bundesfinanzministerium.de
{keyword} BMF Verwaltungsgrundsätze Verrechnungspreise 2024 site:bundesfinanzministerium.de
```

### 联邦财政法院 BFH

```
{keyword} site:bundesfinanzhof.de
{keyword} Urteil OR Beschluss site:bundesfinanzhof.de
```

### 企业登记

```
{company_name} site:unternehmensregister.de
```

### 欧盟法律

```
{keyword} tax directive site:eur-lex.europa.eu
ATAD OR Pillar Two OR minimum tax site:eur-lex.europa.eu
```

## 2. 高质量税务指南搜索

```
Germany {topic} site:practiceguides.chambers.com
Germany {topic} site:iclg.com
Germany {topic} site:legal500.com/guides
Germany {topic} tax site:practiceguides.chambers.com
```

按具体税务主题：

| 主题 | 最佳搜索指南 | 搜索模板示例 |
| --- | --- | --- |
| 公司所得税 | Chambers > ICLG | `Germany corporate tax site:practiceguides.chambers.com` |
| 转让定价 | Chambers > ICLG | `Germany transfer pricing site:iclg.com` |
| 预提税 | Chambers > ICLG | `Germany withholding tax site:practiceguides.chambers.com` |
| 增值税 | Chambers > ICLG | `Germany indirect tax VAT site:practiceguides.chambers.com` |
| 税收协定/条约 | Chambers | `Germany double tax treaties site:practiceguides.chambers.com` |
| 反避税/CFC | ICLG > Chambers | `Germany anti-avoidance controlled foreign company site:iclg.com` |
| 个人所得税 | Chambers > Legal500 | `Germany personal income tax site:practiceguides.chambers.com` |
| 资本税/交易税 | Chambers > ICLG | `Germany capital transfer tax stamp duty site:practiceguides.chambers.com` |

## 3. Doing Business 系列搜索

```
"doing business in Germany" tax filetype:pdf {year}
"doing business in Germany" baker mckenzie OR deloitte OR ey OR pwc tax
"investing in Germany" tax guide filetype:pdf
Germany tax facts {year} deloitte OR ey OR pwc OR kpmg
```

## 4. 国际所税务实务文章搜索

### 通过 Lexology 发现

```
Germany {topic} tax site:lexology.com {year}
Germany tax update site:lexology.com {year}
```

找到相关文章标题和作者后，去律所官网查找免费全文。

### 直接在主要律所网站搜索

```
"Germany" "{topic}" tax update OR client alert {year}
"Germany" "{topic}" site:bakermckenzie.com
"Germany" "{topic}" site:cliffordchance.com
"Germany" "{topic}" site:freshfields.com
"Germany" "{topic}" site:linklaters.com
"Germany" "{topic}" site:allenovery.com
"Germany" "{topic}" site:ashurst.com
```

## 5. 中文律所和财税文章搜索

```
德国 投资 税务 {keyword} site:wechat.qq.com 金杜 OR 中伦 OR 方达 OR 锦天城
德国 税务 {keyword} 走出去智库 OR CGG
德国 {keyword} 税 税务顾问 OR 税务筹划
```

## 6. 特定场景搜索模板

### 中德税收协定

```
China Germany double tax agreement site:bundesfinanzministerium.de
中德 税收协定 site:bundesfinanzministerium.de
China Germany DBA site:gesetze-im-internet.de
```

### 常设机构 PE

```
Germany permanent establishment {industry} site:practiceguides.chambers.com
Germany Betriebsstätte {industry} site:gesetze-im-internet.de
```

### 转让定价

```
Germany transfer pricing documentation site:iclg.com
BMF Verwaltungsgrundsätze Verrechnungspreise 2024 site:bundesfinanzministerium.de
Germany transfer pricing benchmark site:bakermckenzie.com
```

### VAT / 电子商务

```
Germany VAT e-commerce platform site:bundesfinanzministerium.de
Germany Umsatzsteuer marketplace OR platform site:gesetze-im-internet.de
Germany OSS IOSS VAT site:ec.europa.eu
```

### 最低工资和劳动税务

```
Germany Mindestlohn 2026 site:bmas.de
Germany minimum wage site:gesetze-im-internet.de
Germany payroll tax social security site:practiceguides.chambers.com
```

### Pillar Two / 全球最低税

```
Germany Pillar Two minimum tax GloBE site:bundesfinanzministerium.de
Germany global minimum tax site:gesetze-im-internet.de
Germany minimum tax implementation site:practiceguides.chambers.com
```

## 7. 搜索结果评估纪律

### 确定性标签

报告中的每条德国税务信息必须标注确定性等级：

| 标签 | 含义 | 适用来源 |
| --- | --- | --- |
| [法规原文] | 直接引用法条或法规原文 | L1 高层级：gesetze-im-internet.de、BFH、BMF 正式指引 |
| [权威解读] | 来自 Chambers/ICLG/OECD 指南、BMF 行政原则 | L2 中层级：高质量税务指南和官方行政指引 |
| [一般评论] | 来自律所文章、Steuerberater 文章、行业分析 | L3 中/低层级 |
| [待验证] | 来自 AI 生成、论坛、无法确认来源 | L4 或无来源 |

关键规则：

- 源文件说 "kann" / "may"，不得转述为 "muss" / "requires"。
- 源文件说 "in der Regel" / "typically"，不得转述为 "immer" / "always"。
- 税率数值必须引用官方法规或 BMF 指引原文，不得凭记忆写税率。
- 多个来源说法不一致时，分别列明，不揉成折中结论。

### 联网搜索后的行为边界

- 搜到指南类页面（Chambers / ICLG / Legal500），只提取目录结构和章节标题，不直接概括其中的法律条文作为自己的分析。
- 需要法律条文时，从指南中找到法条引用，再回 `gesetze-im-internet.de` 查原文。
- 不能把搜索摘要直接写成税务结论。
- 不能把高质量指南的内容等同于法律本身。

### 访问状态标注

对推荐的每个资源，标注其访问状态：

- [已验证可访问]：URL 可用，内容可读
- [需注册]：URL 可用但需免费注册
- [需付费]：需要订阅
- [德语原文]：仅德语版本可用
- [未找到]：该资源无相关内容
- [未验证]：无法检查（如网络问题）
