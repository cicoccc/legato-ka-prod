# 搜索查询模板：数据跨境合规

## 何时读取本文件

当已经确定需要联网搜索，并需要构造中国侧、欧盟侧、行业监管或国际传输 query 时，读取本文件。

## 本文件影响什么决策

本文件决定查询词、官方域名限定方式和主题模板，避免将入口型数据合规问题泛化为无边界搜索。

## 不适用场景

尚未确定检索路径、已有足够可定位来源，或只是在判断转交路径时，不优先读取本文件。

> 本文件是 `legato-cross-border-data-flow-compliance` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{country}`、`{topic}`、`{year}`、`{law_name}` 为占位符，运行时替换为实际值。

## 1. 中国侧官方域名限定搜索

### 网信办（cac.gov.cn）

```
数据出境 site:cac.gov.cn
个人信息出境安全评估 site:cac.gov.cn
标准合同 site:cac.gov.cn
数据出境安全评估办法 site:cac.gov.cn
个人信息出境标准合同办法 site:cac.gov.cn
数据出境认证 site:cac.gov.cn
数据跨境传输 site:cac.gov.cn
重要数据 site:cac.gov.cn
```

### 法律法规数据库（flk.npc.gov.cn）

```
个人信息保护法 site:flk.npc.gov.cn
数据安全法 site:flk.npc.gov.cn
网络安全法 site:flk.npc.gov.cn
```

### 工信部（miit.gov.cn）

```
数据安全管理 site:miit.gov.cn
网络安全审查 site:miit.gov.cn
```

### 市场监管总局（samr.gov.cn）

```
数据安全 个人信息 site:samr.gov.cn
信息安全技术 数据出境 site:samr.gov.cn
```

## 2. 欧盟侧官方域名限定搜索

### EDPB（edpb.europa.eu）

```
data transfer GDPR adequacy site:edpb.europa.eu
standard contractual clauses site:edpb.europa.eu
transfer impact assessment site:edpb.europa.eu
supplementary measures site:edpb.europa.eu
international transfer site:edpb.europa.eu
```

### EUR-Lex（eur-lex.europa.eu）

```
standard contractual clauses site:eur-lex.europa.eu
adequacy decision data protection site:eur-lex.europa.eu
GDPR chapter V site:eur-lex.europa.eu
```

### 欧委会（ec.europa.eu / commission.europa.eu）

```
standard contractual clauses site:ec.europa.eu
data protection adequacy site:ec.europa.eu
international data transfer site:commission.europa.eu
```

## 3. 高质量法律指南搜索

```
cross-border data transfer site:iclg.com
data protection {country} site:dlapiperdataprotection.com
data protection China site:dlapiperdataprotection.com
data transfer {country} site:practiceguides.chambers.com
GDPR international transfer site:practiceguides.chambers.com
data protection {country} site:legal500.com/guides
```

### 特定实践领域的搜索

| 领域 | 最佳搜索指南 | 搜索模板示例 |
| --- | --- | --- |
| 中国数据出境 | DLA Piper > ICLG > Chambers | `China data protection site:dlapiperdataprotection.com` |
| GDPR 跨境传输 | EDPB > DLA Piper > ICLG | `GDPR international transfer site:iclg.com` |
| SCC 路径 | EDPB > EUR-Lex > Chambers | `standard contractual clauses site:practiceguides.chambers.com` |
| TIA 方法论 | EDPB > IAPP > 律所文章 | `transfer impact assessment methodology site:iclg.com` |
| 特定国家数据保护 | DLA Piper > ICLG | `data protection {country} site:dlapiperdataprotection.com` |

## 4. 律所实务文章搜索

### 通过 Lexology 发现

```
{country} data transfer site:lexology.com {year}
China data export site:lexology.com {year}
GDPR cross-border transfer site:lexology.com {year}
```

### 直接在主要律所网站搜索

```
"China" "data export" OR "data transfer" legal update OR client alert {year}
"China" "data export" site:bakermckenzie.com
"cross-border" "data transfer" site:cliffordchance.com
"China" "data protection" site:herbertsmithfreehills.com
"GDPR" "international transfer" site:dlapiper.com
```

### 中文律所文章搜索

```
数据出境 合规 site:wechat.qq.com 金杜 OR 中伦 OR 方达 OR 汉坤
数据跨境 安全评估 律所分析
个人信息出境 标准合同 实务
```

## 5. 行业特定搜索模板

部分行业有额外的数据出境监管要求，需要补充行业特定搜索：

| 行业 | 补充搜索 |
| --- | --- |
| 金融 | `金融数据 site:cac.gov.cn`、`银行保险 数据出境 site:cbirc.gov.cn` |
| 医疗 | `医疗健康 数据安全 site:nhc.gov.cn`、`健康医疗数据 site:cac.gov.cn` |
| 汽车/车联网 | `汽车数据 site:cac.gov.cn`、`智能网联汽车 数据安全 site:miit.gov.cn` |
| AI 训练数据 | `生成式人工智能 site:cac.gov.cn`、`训练数据 site:cac.gov.cn` |
| 跨境电商 | `跨境电商 数据 site:mofcom.gov.cn` |

## 6. 搜索结果评估纪律

### 确定性标签

报告中的每条法律信息必须标注确定性等级：

| 标签 | 含义 | 适用来源 |
| --- | --- | --- |
| [法规原文] | 直接引用法条或法规原文 | 中国法律法规数据库、EUR-Lex、政府公报 |
| [权威解读] | 来自主管机关官方解读或 EDPB 正式指南 | 网信办 FAQ、EDPB 指南、DPA 裁决 |
| [一般评论] | 来自律所文章、行业分析 | ICLG、Chambers、律所 client alert |
| [待验证] | 来源不确定、无法确认版本、或 AI 生成补全 | 未找到官方核验的二手信息 |

关键规则：

- 源文件说 "may require" 不得转述为 "requires"。
- 源文件说 "in general" 或 "typically" 不得转述为 "always"。
- 中国法规中"应当"不得转述为"可以"，反之亦然。
- 多个来源说法不一致时，分别列明，不揉成折中结论。

### 联网搜索后的行为边界

- 搜到指南类页面（Chambers / ICLG / DLA Piper），只提取目录结构和章节标题，不直接概括其中的法律条文作为自己的分析。
- 需要法律条文时，从指南中找到法条引用，再回官方域名查原文。
- 不能把搜索摘要直接写成法律结论。
- 不能把高质量指南的内容等同于法律本身。

### 访问状态标注

对推荐的每个资源，标注其访问状态：

- [已验证可访问]：URL 可用，内容可读
- [需注册]：URL 可用但需免费注册
- [需付费]：需要订阅
- [未找到该法域]：该资源不覆盖目标法域
- [未验证]：无法检查（如网络问题）
