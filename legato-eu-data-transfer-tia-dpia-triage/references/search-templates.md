# 搜索查询模板：TIA / DPIA 初筛

## 何时读取本文件

当已经确定需要联网搜索，并需要构造 TIA、DPIA、SCC、远程访问、adequacy 或 DPA enforcement query 时，读取本文件。

## 本文件影响什么决策

本文件决定欧盟官方域名、成员国 DPA、案例和目的地国风险的查询模板。

## 不适用场景

尚未确定检索策略、已有官方 URL 可直接核验，或只是在输出报告时，不优先读取本文件。

> 本文件是 `legato-eu-data-transfer-tia-dpia-triage` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{country}`、`{topic}`、`{year}`、`{dpa_domain}` 为占位符，运行时替换为实际值。

## 1. EDPB / EUR-Lex 官方域名限定搜索

### EDPB（edpb.europa.eu）

```
transfer impact assessment site:edpb.europa.eu
data protection impact assessment site:edpb.europa.eu
supplementary measures site:edpb.europa.eu
standard contractual clauses site:edpb.europa.eu
international transfer site:edpb.europa.eu
adequacy decision site:edpb.europa.eu
binding decision site:edpb.europa.eu
enforcement data transfer site:edpb.europa.eu
```

### EUR-Lex（eur-lex.europa.eu）

```
standard contractual clauses site:eur-lex.europa.eu
adequacy decision data protection site:eur-lex.europa.eu
GDPR chapter V site:eur-lex.europa.eu
data transfer third country site:eur-lex.europa.eu
```

### 欧委会（ec.europa.eu / commission.europa.eu）

```
adequacy decision site:ec.europa.eu
standard contractual clauses site:ec.europa.eu
international data protection transfer site:ec.europa.eu
data protection adequacy countries site:ec.europa.eu
```

## 2. 各成员国 DPA 官网限定搜索

### 按 DPA 域名搜索

```
transfer impact assessment site:{dpa_domain}
international transfer enforcement site:{dpa_domain}
data transfer fine site:{dpa_domain}
SCC assessment site:{dpa_domain}
DPIA guidance site:{dpa_domain}
```

### 主要 DPA 域名速查

| DPA | 域名 | 常见搜索关键词 |
| --- | --- | --- |
| 爱尔兰 DPC | `dataprotection.ie` | transfer, SCC, TIA, enforcement |
| 法国 CNIL | `cnil.fr` | transfert, TIA, DPIA, sanction |
| 德国 BfDI | `datenschutz.de` | Datenuebermittlung, DSGVO, TIA |
| 英国 ICO | `ico.org.uk` | international transfer, adequacy, DPIA |
| 荷兰 AP | `autoriteitpersoonsgegevens.nl` | internationale doorgifte |
| 意大利 Garante | `garanteprivacy.it` | trasferimento dati |
| 西班牙 AEPD | `aepd.es` | transferencia internacional |
| 奥地利 DSB | `dsb.gv.at` | Datenuebermittlung, DSGVO |
| 波兰 UODO | `uodo.gov.pl` | transfer danych |
| 瑞典 IMY | `imy.se` | internationell overforing |

### 特定 DPA 裁决搜索

```
{dpa_name} fine OR penalty data transfer {year}
{dpa_name} decision enforcement international transfer {year}
{dpa_name} binding decision {topic} site:edpb.europa.eu
```

## 3. 高质量法律指南搜索

```
transfer impact assessment site:iclg.com
data protection {country} site:dlapiperdataprotection.com
GDPR international transfer site:practiceguides.chambers.com
data protection {country} site:legal500.com/guides
```

### 特定主题的搜索指南

| 主题 | 最佳搜索指南 | 搜索模板示例 |
| --- | --- | --- |
| TIA 方法论 | EDPB > IAPP > ICLG | `transfer impact assessment site:iclg.com` |
| SCC 路径 | EDPB > EUR-Lex > Chambers | `standard contractual clauses site:practiceguides.chambers.com` |
| DPIA 触发 | EDPB > 各 DPA > ICLG | `data protection impact assessment site:iclg.com` |
| Adequacy Decision | 欧委会 > EDPB > DLA Piper | `adequacy decision site:dlapiperdataprotection.com` |
| DPA 执法 | DPA 官网 > EDPB > IAPP | `{country} data protection enforcement site:iclg.com` |
| BCR 路径 | EDPB > ICLG > Chambers | `binding corporate rules site:iclg.com` |

## 4. IAPP 和专业机构搜索

```
transfer impact assessment site:iapp.org {year}
DPIA GDPR methodology site:iapp.org
data transfer enforcement site:iapp.org {year}
GDPR adequacy decision analysis site:iapp.org
```

## 5. 律所实务文章搜索

### 通过 Lexology 发现

```
GDPR international transfer site:lexology.com {year}
transfer impact assessment site:lexology.com {year}
DPIA guidance site:lexology.com {year}
{country} data protection enforcement site:lexology.com {year}
```

### 直接在主要律所网站搜索

```
"transfer impact assessment" site:freshfields.com
"SCC" "data transfer" site:hoganlovells.com
"GDPR" "international transfer" site:dlapiper.com
"DPIA" "guidance" site:cliffordchance.com
"data transfer" "enforcement" site:nortonrosefulbright.com
"Schrems" "transfer" site:herbertsmithfreehills.com
```

### 按知名数据保护律所搜索

```
{topic} site:dataprotection.ie
{topic} site:noerr.com
{topic} site:bindmans.com
```

## 6. DPA 裁决和案例搜索

### 已知重要案例的定向搜索

| 案例 | 搜索模板 |
| --- | --- |
| Meta DPC 裁决 | `Meta Ireland data transfer fine site:dataprotection.ie` |
| TikTok DPC 裁决 | `TikTok data transfer China site:dataprotection.ie` |
| Google Analytics 相关裁决 | `Google Analytics data transfer site:edpb.europa.eu` |
| Clearview AI 裁决 | `Clearview AI site:cnil.fr OR site:garanteprivacy.it` |
| 某 DPA 最新执法 | `{dpa_name} enforcement action data transfer {year}` |

### 批量搜索 DPA 执法趋势

```
GDPR enforcement data transfer fine {year} site:edpb.europa.eu
data protection fine international transfer {year}
{country} DPA decision cross-border transfer {year}
```

## 7. 搜索结果评估纪律

### 确定性标签

报告中的每条法律信息必须标注确定性等级：

| 标签 | 含义 | 适用来源 |
| --- | --- | --- |
| [法规原文] | 直接引用 GDPR 条文或 EU 法规原文 | EUR-Lex、GDPR 官方文本 |
| [权威解读] | 来自 EDPB 正式指南或 DPA 正式裁决 | EDPB Recommendations、DPA 裁决 PDF、CJEU 判例 |
| [一般评论] | 来自律所文章、IAPP 分析 | ICLG、Chambers、律所 client alert |
| [待验证] | 来源不确定、无法确认版本、或 AI 生成补全 | 未找到官方核验的二手信息 |

关键规则：

- 源文件说 "may require" 不得转述为 "requires"。
- 源文件说 "in general" 或 "typically" 不得转述为 "always"。
- GDPR 条文中 "shall" = 强制义务，"may" = 许可或裁量，不得互换。
- EDPB 指南中的 "recommendations" 不等同于 GDPR 条文的法律约束力。
- 多个来源说法不一致时，分别列明，不揉成折中结论。

### 联网搜索后的行为边界

- 搜到指南类页面（Chambers / ICLG / IAPP），只提取目录结构和章节标题，不直接概括其中的法律条文作为自己的分析。
- 需要法律条文时，从指南中找到法条引用，再回 EUR-Lex 查原文。
- 不能把搜索摘要直接写成法律结论。
- 不能把 DPA 裁决的新闻报道等同于裁决原文。

### 访问状态标注

对推荐的每个资源，标注其访问状态：

- [已验证可访问]：URL 可用，内容可读
- [需注册]：URL 可用但需免费注册
- [需付费]：需要订阅
- [未找到]：该资源不覆盖目标主题
- [未验证]：无法检查（如网络问题）
