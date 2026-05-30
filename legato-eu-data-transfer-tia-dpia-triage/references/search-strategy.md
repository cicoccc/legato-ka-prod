# TIA/DPIA 搜索策略

## 何时读取本文件

当需要检索 EDPB、EUR-Lex、欧委会、CJEU、DPA 或 SCC / TIA / DPIA 官方材料时，必须先读取本文件。

## 本文件影响什么决策

本文件决定已收录官方来源、EDPB / EUR-Lex 域名搜索、DPA 搜索和失败处理的执行顺序。

## 不适用场景

只是在引用已收录来源、撰写报告格式，或不需要新增检索时，不以本文件替代输出规则。

> 本文件是 `legato-eu-data-transfer-tia-dpia-triage` 自带的搜索策略指引。
> 目标是把"官方来源优先"的抽象原则翻译为 Agent 可逐步执行的具体搜索链路。
> 与 `official-source-verification.md` 协同工作：该文件已收录 12 个带 URL 的官方来源，本文件聚焦搜索执行顺序和失败处理。
> 本 Skill 独立打包时不得依赖上级目录、兄弟目录或外部共享文件。

## 1. 通用搜索顺序

对每个子问题，Agent 必须按以下顺序执行搜索，不得跳过前序步骤直接泛搜：

### 第 1 步：official-source-verification.md 已收录来源核验

首先查阅 `official-source-verification.md` 中已收录的 12 个官方来源，看是否有直接匹配的主题。如有，优先使用已收录的 URL 进行联网核验，确认链接仍然可用、内容未更新。

已收录来源优先级：

| 优先级 | 来源 | 适用场景 |
| --- | --- | --- |
| 最高 | GDPR Chapter V（来源 1） | Art.44-49 条文基础 |
| 最高 | EDPB Recommendations 01/2020 v2.0（来源 3） | TIA 六步框架 |
| 最高 | CJEU C-311/18（来源 7） | Schrems II 判例 |
| 高 | EDPB/WP29 DPIA Guidelines（来源 5） | DPIA 触发和方法论 |
| 高 | Meta DPC IN-20-8-1（来源 8） | TIA 不充分案例 |
| 高 | TikTok DPC Decision（来源 10/11） | EU -> 中国传输案例 |
| 高 | EU SCCs 2021（来源 12） | SCC 路径核验 |
| 中 | EDPB DPIA Template 2026（来源 6） | DPIA 模板动态 |
| 中 | Meta EDPB Binding Decision（来源 9） | 案例补充 |

### 第 2 步：EDPB / EUR-Lex 联网搜索

如已收录来源无法覆盖问题，使用域名限定搜索在欧盟官方来源中补充检索：

| 优先域名 | 来源 | 搜索重点 |
| --- | --- | --- |
| `edpb.europa.eu` | 欧洲数据保护委员会 | 指南、建议、约束性决定、FAQ、公开咨询 |
| `eur-lex.europa.eu` | 欧盟法规数据库 | GDPR 条文、adequacy decision、立法历史 |
| `ec.europa.eu` | 欧委会 | 数据保护 Q&A、SCC 官方页面、adequacy decision 列表 |
| `commission.europa.eu` | 欧委会 | SCCs 文本、跨境传输机制 |

### 第 3 步：各成员国 DPA 官网搜索

当问题涉及特定成员国的 DPA 立场或执法时，在该 DPA 官网搜索：

| DPA | 官方域名 | 搜索重点 |
| --- | --- | --- |
| 爱尔兰 DPC | `dataprotection.ie` | Big Tech 裁决、SCC/TIA 案例 |
| 法国 CNIL | `cnil.fr` | 执法决定、DPIA 指南 |
| 德国 BfDI / 各州 DPA | `datenschutz.de` | 德国联邦和各州数据保护 |
| 英国 ICO | `ico.org.uk` | DPIA 指导、国际传输指南、执法行动 |
| 荷兰 AP | `autoriteitpersoonsgegevens.nl` | 荷兰执法案例 |
| 意大利 Garante | `garanteprivacy.it` | 意大利执法案例 |
| 西班牙 AEPD | `aepd.es` | 西班牙执法案例 |

搜索模板：

```
transfer impact assessment site:{dpa_domain}
international transfer site:{dpa_domain}
enforcement action data transfer site:{dpa_domain}
```

### 第 4 步：高质量法律指南搜索

官方域名无结果或覆盖不足时，在以下高质量法律指南中搜索：

- ICLG Data Protection
- Chambers Practice Guides
- Legal500 Country Guides
- DLA Piper Data Protection
- IAPP（专业协会报告和分析）

这些来源用于搭框架、做比较和识别需要官方核验的关键点，不替代官方来源。

### 第 5 步：律所实务文章搜索

对时效性热点问题（近期 DPA 裁决、新 adequacy decision、SCC 发展），在国际所和聚合平台中搜索：

- 优先使用 Lexology 作为发现工具
- 直接在主要律所官网搜索

### 第 6 步：开放搜索

以上步骤均不足时，使用开放搜索补充。但结论强度自动降级，输出中必须标注为"待确认"。

## 2. 各步骤失败后的处理链

| 失败情况 | 下一步动作 | 输出要求 |
| --- | --- | --- |
| official-source-verification.md 无相关来源 | 进入第 2 步 | 记录"已收录来源未覆盖该主题" |
| 已收录 URL 失效或内容更新 | 搜索同一来源的最新版本，同时记录失效情况 | 标注"原始链接可能已更新，以下为最新可用版本" |
| EDPB / EUR-Lex 限定搜索无结果 | 进入第 3 步或第 4 步 | 标注"EDPB/EUR-Lex 未检索到" |
| DPA 官网 404 或改版 | 换同 DPA 其他页面，再试一次 | 不因单个页面不可用就放弃该 DPA 来源 |
| 高质量指南无相关覆盖 | 进入第 5 步或第 6 步 | 结论强度降为"待确认" |
| 开放搜索仅找到行业文章 | 用作问题理解框架 | 不作为决定性依据，标注"仅找到行业解读，需 EDPB/EUR-Lex 核验" |
| 开放搜索仅找到新闻 | 仅作为动态信号 | 结论标为"待确认"，不可单独支撑法律结论 |
| 来源之间存在冲突 | 比较效力层级、发布时间、适用范围 | 无法收口时标为"不明确"或"需当地 DPA 确认" |

## 3. 时效性前置判断

| 敏感度 | 典型子领域 | 来源有效期窗口 | 行为要求 |
| --- | --- | --- | --- |
| 极高 | Schrems 相关判例、新 SCC 修订、新 adequacy decision（如 EU-US DPF）、DPA 新裁决 | 3-6 个月 | 在执行摘要中加醒目时效警告；推荐用户直接查阅 EDPB 最新动态 |
| 高 | DPA 裁决执行、新 adequacy decision 生效、EDPB 新指南征求意见 | 6-12 个月 | 注明所有来源的发布日期；关键结论交叉验证至少两个来源 |
| 中 | EDPB 已发布指南（如 Rec.01/2020 v2.0、DPIA Guidelines）、CJEU 判例 | 1-3 年 | 标准来源日期意识；注意是否有新指南或判例修正 |
| 低 | GDPR 基本框架（Chapter V 结构）、数据保护基本原则 | 相对稳定 | 仍应注明来源日期 |

对"极高"敏感度领域，报告的执行摘要和结论限制中必须包含：

> 本领域规则变化频繁（Schrems II 后 TIA 框架持续演进，DPA 执法案例不断更新）。以下信息基于截至 [日期] 的来源，可能未反映最新变化。建议直接查阅 EDPB 最新动态或咨询数据保护律师。

## 4. 特殊搜索注意事项

### EU -> 中国传输场景

涉及 EU 数据向中国传输的 TIA，需要特别关注：

- TikTok DPC 裁决（IN-21-9-2）是目前最重要的 EU -> 中国传输案例，必须参考。
- 需要评估中国《个人信息保护法》《数据安全法》《国家安全法》《反恐法》等法律对政府数据访问的影响。
- 中国法律评估应参考 EDPB Recommendations 01/2020 第三步（目的地国法律分析）。
- 不得简单结论"中国法律不允许数据保护"，应逐条分析相关法律条文及其实际适用条件。

### Adequacy Decision 场景

搜索 adequacy decision 时注意：

- 欧委会当前 adequacy decision 列表可通过 `ec.europa.eu` 查阅。
- EU-US Data Privacy Framework 有特殊背景（Privacy Shield 被 Schrems II 推翻后的替代方案），需确认最新状态。
- 部分 adequacy decision 可能附有条件或日落条款。

### DPIA 触发场景

DPIA 搜索时注意：

- GDPR Art.35(3) 列出了必须进行 DPIA 的三种情形，但非穷尽列举。
- 各成员国 DPA 可能有额外的 DPIA 强制清单（under Art.35(4)）。
- EDPB DPIA Template 2026 仍在征求意见阶段（截止 2026-06-09），不得写成已最终定稿。
