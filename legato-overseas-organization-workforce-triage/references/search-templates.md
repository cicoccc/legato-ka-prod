# 海外组织与用工分流搜索查询模板

> 本文件是 `legato-overseas-organization-workforce-triage` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{country}`、`{topic}`、`{domain}`、`{year}`、`{law_name}` 为占位符，运行时替换为实际值。

## 何时读取本文件

- 已确定目标国、用工主题和来源层级后，需要构造联网搜索 query 时。
- 需要搜索 EOR / payroll 合法性、工作许可、解雇保护或外籍员工限制时。

## 本文件影响什么决策

- 决定 query 结构、关键词组合和域名限定方式，不决定最终法律结论。

## 不适用场景

- 不用于判断哪个来源优先；搜索顺序见 `search-strategy.md`。

## 1. 法域官方入口限定搜索

从 `references/official-source-entrypoints.md` 的「首批法域入口」中取域名，替换 `{domain}`：

```
{labour_topic_keywords} site:{domain}
{labour_topic_keywords} regulation OR law site:{domain}
{labour_topic_keywords} foreign worker OR expatriate site:{domain}
```

示例（均来自 official-source-entrypoints.md 中已整理的法域入口）：

```
employment contract foreign worker site:bmas.de
work permit visa foreign employee site:make-it-in-germany.com
labour code foreign workers site:molisa.gov.vn
work permit foreign worker site:imigrasi.go.id
employment contract working hours site:gov.uk
contrat de travail étranger site:travail-emploi.gouv.fr
work permit foreigner site:doe.go.th
```

## 2. ILO NATLEX 搜索模板

ILO NATLEX 是国际劳工组织维护的各国劳动法规索引数据库，提供法规名称、颁布日期、覆盖范围和原文链接。

```
site:natlex.ilo.org {country} labour OR employment
site:natlex.ilo.org {country} foreign workers OR expatriate
site:natlex.ilo.org {country} employment contract
site:natlex.ilo.org {country} working hours OR overtime
site:natlex.ilo.org {country} dismissal OR termination
site:natlex.ilo.org {country} social security OR social insurance
site:natlex.ilo.org {country} minimum wage
site:natlex.ilo.org {country} maternity OR parental leave
```

示例：

```
site:natlex.ilo.org Germany labour employment
site:natlex.ilo.org Vietnam foreign workers
site:natlex.ilo.org Indonesia employment contract
site:natlex.ilo.org Thailand minimum wage
site:natlex.ilo.org United Kingdom dismissal termination
```

访问状态：NATLEX 可免费在线浏览，但部分法规全文可能需要跳转到各国官方来源。

## 3. ICLG Employment 搜索模板

ICLG Employment & Labour Law 指南覆盖全球主要法域的劳动法概览，免费注册后可阅读全文。

```
{country} employment labour site:iclg.com
{country} employment contract site:iclg.com
{country} termination dismissal site:iclg.com
{country} foreign workers work permit site:iclg.com
{country} social security employment site:iclg.com
{country} collective bargaining trade union site:iclg.com
```

示例：

```
Germany employment labour site:iclg.com
Vietnam employment contract site:iclg.com
Indonesia termination dismissal site:iclg.com
Thailand foreign workers work permit site:iclg.com
France collective bargaining trade union site:iclg.com
```

访问状态：需免费注册，[需注册]。

## 4. Chambers Employment 搜索模板

Chambers Practice Guides — Employment 覆盖主要法域，完全免费，无需注册。

```
{country} employment site:practiceguides.chambers.com
{country} employment contracts site:practiceguides.chambers.com
{country} termination of employment site:practiceguides.chambers.com
{country} employment dispute resolution site:practiceguides.chambers.com
{country} employee benefits site:practiceguides.chambers.com
```

示例：

```
Germany employment site:practiceguides.chambers.com
Vietnam employment contracts site:practiceguides.chambers.com
United Kingdom termination of employment site:practiceguides.chambers.com
France employee benefits site:practiceguides.chambers.com
```

访问状态：完全免费，无需注册，[已验证可访问]。

## 5. 各法域劳动主管机关搜索

以下域名均来自 `references/official-source-entrypoints.md`，按法域整理：

### 德国

```
site:bmas.de Arbeitsrecht employment foreign worker
site:bmas.de minimum wage Mindestlohn
site:gesetze-im-internet.de BGB Arbeitsvertrag
site:gesetze-im-internet.de Kündigungsschutzgesetz
site:arbeitsagentur.de work permit foreign workers
site:make-it-in-germany.com work visa employment
```

### 越南

```
site:molisa.gov.vn labour code Vietnam foreign workers
site:molisa.gov.vn work permit foreign employee
site:vbpl.vn Vietnam labor code foreign workers
site:mofcom.gov.cn 越南 劳动法 外国人就业
```

### 印度尼西亚

```
site:kemnaker.go.id foreign workers Indonesia employment regulation
site:kemnaker.go.id minimum wage upah minimum
site:peraturan.go.id tenaga kerja asing
site:imigrasi.go.id work visa foreign worker Indonesia
site:oss.go.id foreign workers permit
```

### 泰国

```
site:labour.go.th employment Thailand foreign worker
site:labour.go.th minimum wage Thailand
site:doe.go.th work permit Thailand foreigner
site:immigration.go.th work visa Thailand
site:boi.go.th work permit foreign experts Thailand
```

### 英国

```
site:gov.uk employment contract working hours
site:gov.uk skilled worker visa sponsor licence
site:gov.uk national minimum wage rates
site:legislation.gov.uk Employment Rights Act
site:acas.org.uk dismissal redundancy
site:ico.org.uk employment data protection
```

### 法国

```
site:travail-emploi.gouv.fr contrat de travail
site:code.travail.gouv.fr contrat de travail licenciement
site:service-public.fr autorisation de travail salarié étranger
site:france-visas.gouv.fr salarié
site:cnil.fr travail RGPD collaborateurs
```

## 6. 法律指南聚合搜索

```
{country} doing business employment labour law filetype:pdf
{country} doing business baker mckenzie OR deloitte OR ey OR pwc employment
"doing business in {country}" employment {year}
{country} employment law guide filetype:pdf
```

## 7. 律所实务文章搜索

用于查找近期劳动法修订、签证政策变化、EOR 监管动态等时效性话题。

### 通过 Lexology 发现

```
{country} employment site:lexology.com {year}
{country} employer of record site:lexology.com {year}
{country} work permit immigration site:lexology.com {year}
```

找到相关文章标题和作者后，去律所官网查找免费全文。

### 直接在主要律所网站搜索

```
"{country}" employment labour law legal update OR client alert {year}
"{country}" employer of record EOR site:bakermckenzie.com
"{country}" employment site:cliffordchance.com
"{country}" employment immigration site:nortonrosefulbright.com
"{country}" employment site:herbertsmithfreehills.com
"{country}" employment site:dlapiper.com
```

### 中文律所文章搜索

```
"{country}" 劳动法 就业 site:wechat.qq.com 金杜 OR 中伦 OR 方达
"{country}" 用工 EOR OR 雇主代理 site:wechat.qq.com
"{country}" 劳动法 走出去智库 OR CGG
```

## 8. 特定分流场景搜索模板

### EOR / 雇主代理合法性

```
"{country}" employer of record EOR legality OR legal
"{country}" employer of record labour law
"{country}" EOR employment relationship
"{country}" employer of record site:iclg.com OR site:practiceguides.chambers.com
```

### 本地实体要求

```
"{country}" local entity requirement employment foreign company
"{country}" subsidiary requirement hire employees
"{country}" branch office employment law
"{country}" representative office hiring
```

### 工作许可与签证

```
"{country}" work permit foreign employee requirements {year}
"{country}" work visa application process employer
"{country}" skilled worker visa {year}
"{country}" intra-company transfer visa
```

### 最低工资与社保

```
"{country}" minimum wage {year}
"{country}" social security contribution employer employee {year}
"{country}" statutory benefits mandatory
"{country}" payroll tax employer obligation
```

### 解雇保护

```
"{country}" termination employment law requirements
"{country}" dismissal notice period severance
"{country}" unfair dismissal protection
"{country}" redundancy collective dismissal
```

## 9. 确定性标签在分流判断中的使用示例

以下示例展示如何在分流结论中正确标注确定性标签：

### 示例 1：有法规原文支撑的分流判断

```markdown
德国法律要求外国雇主在德国雇佣员工时必须在当地设立实体或通过符合条件的雇主代理[^1]。

[^1]: [德国商法典 (GewO) 第 14 条](https://www.gesetze-im-internet.de/gewo/__14.html) - 高 | 法规原文 | 2026-01 | 明确规定商业经营需在当地设立或通过授权代理人
```

### 示例 2：基于权威指南的分流判断

```markdown
越南法律允许通过 EOR 模式雇佣当地员工，但 EOR 提供商需在越南持有合法人力资源服务牌照[^2]。

[^2]: [ICLG Employment & Labour Law: Vietnam](https://iclg.com/practice-areas/employment-and-labour-law/vietnam) - 中 | 权威指南 | 2026 | EOR 模式实务描述；具体牌照要求建议查阅越南劳动部官网核验
```

### 示例 3：来源不足的降级分流判断

```markdown
老挝的 EOR 法律框架在主流法律指南中覆盖极为有限，无法从公开来源确认其合法性[^3]。

[^3]: ILO NATLEX 和 ICLG Employment 指南均未找到老挝 EOR 相关条目 - 待确认 | 来源缺失 | 2026-05-25 | 强烈建议咨询当地劳动律师确认
```

### 示例 4：时效性敏感的分流判断

```markdown
泰国 2025 年修订的《劳动保护法》新增了远程工作相关条款，可能影响 EOR 模式下的用工安排[^4]。

[^4]: [泰国内政部劳动保护公告](URL) - 高 | 官方说明 | 2025-12 | 泰国劳动法近期修订频繁，本结论基于截至 2026-05 的来源，建议查阅官方最新规定
```
