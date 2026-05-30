# 欧盟数据跨境传输与 TIA/DPIA 初筛：官方来源与裁决边界

> 本文件供 `legato-eu-data-transfer-tia-dpia-triage` 运行时使用。  
> 本 Skill 独立打包，不依赖 `_shared` 或研究包素材总表。

## 何时读取本文件

- 开始任何欧盟数据传输风险初筛任务时。
- 涉及 GDPR Chapter V、SCC、TIA、DPIA、C-311/18、Meta、TikTok、远程访问或 EU / EEA 数据向中国 / 第三国传输时。

## 本文件影响什么决策

- 决定 EU 官方来源、EDPB 指南、CJEU / DPC 裁决的核验顺序和决定性结论支撑范围。

## 不适用场景

- 不用于中国数据出境安全评估、标准合同、认证或豁免路径判断。
- 不用于全球数据流动结构入口初筛。

## 1. EU 官方来源入口

| 主题 | 官方来源 | 可定位重点 | 使用口径 |
| --- | --- | --- | --- |
| GDPR Chapter V | `https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679` | Art.44-49 | 跨境传输机制基础 |
| GDPR Art.44-49 逐条页面 | `https://cnpd.public.lu/en/legislation/droit-europ/union-europeenne/rgpd/chapitre-5.html` | 卢森堡 CNPD 逐条英文版 | 辅助快速定位条文 |
| EDPB Recommendations 01/2020 v2.0 | `https://edpb.europa.eu/system/files/2021-06/edpb_recommendations_202001vo.2.0_supplementarymeasurestransferstools_en.pdf` | 六步 TIA、补充措施示例 | TIA 初筛主框架 |
| EDPB Recommendations 01/2020 概览页 | `https://www.edpb.europa.eu/our-work-tools/documents/public-consultations/2020/recommendations-012020-measures-supplement_en` | 官方入口和 PDF | 版本核验 |
| EDPB / WP29 DPIA Guidelines | `https://ec.europa.eu/newsroom/just/document.cfm?doc_id=47711` | DPIA 高风险判断和方法论 | DPIA 触发初筛 |
| EDPB DPIA Template 2026 | `https://www.edpb.europa.eu/our-work-tools/documents/public-consultations/2026/edpb-dpia-template_en` | 2026-04-14 起公开征求意见，截止 2026-06-09 | 作为最新模板动态，不写成已最终定稿 |
| 欧盟法院 C-311/18 判决 | `https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX%3A62018CJ0311` | Privacy Shield 无效，SCC 有效但需逐案核实 | TIA 法理基础 |
| Meta DPC IN-20-8-1 | `https://www.edpb.europa.eu/system/files/2023-05/final_for_issue_ov_transfers_decision_12-05-23.pdf` | SCC / TIA 不充分、12 亿欧元罚款 | 案例红旗 |
| Meta EDPB Binding Decision 1/2023 | `https://www.edpb.europa.eu/system/files/2023-05/edpb_bindingdecision_202301_ie_sa_facebooktransfers_redacted.pdf` | EDPB 约束性决定 | 案例补充 |
| TikTok DPC Inquiry 页面 | `https://www.dataprotection.ie/ga/node/1126` | IN-21-9-2、2025-04-30 final decision、EEA 用户数据向中国传输 | TikTok 案官方入口 |
| TikTok DPC final decision PDF | `https://www.dataprotection.ie/sites/default/files/uploads/2025-10/Inquiry%20into%20TikTok%20Technology%20Limited%20April%202025.pdf` | 远程访问、SCC、TIA、中国法律评估 | EU -> 中国传输核心案例 |
| EU SCCs 2021 | `https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en` | 4 模块、Q&A | SCC 路径核验 |
| EDPB-EDPS Joint Opinion 2/2021 on SCCs | `https://www.edpb.europa.eu/our-work-tools/our-documents/edpbedps-joint-opinion/edpb-edps-joint-opinion-22021-standard_en` | SCC 草案意见 | SCC 背景补充 |

## 2. 补充参考来源

| 来源 | 用途 | 禁止写法 |
| --- | --- | --- |
| IAPP、律所、专业机构文章 | 辅助理解裁决背景和实务影响 | 不得单独支撑法律结论 |
| TikTok 官方回应 | 当事方观点和 Project Clover 背景 | 不得当作监管结论 |
| GDPR 培训逐字稿 | 场景化解释、eval 和报告语言参考 | 不得写成官方规则 |

## 3. TIA 初筛框架

按以下顺序执行：

1. 确认 GDPR 是否适用。
2. 确认是否发生跨境传输，包括远程访问。
3. 确认传输机制：adequacy、SCC、BCR、认证或例外。
4. 对 SCC / BCR / 认证路径做 TIA 初筛。
5. 核查目的地国法律和实践、公共机构访问、监管监督、救济权利、国际条约。
6. 核查技术、组织和合同补充措施。
7. 判断风险是否需人工复核或暂停。

## 4. DPIA 初筛框架

需要提示 DPIA 或人工复核的信号：

- 敏感数据或特殊类别数据。
- 大规模处理或系统性监控。
- 自动化决策、画像、AI 训练或新技术。
- 数据主体为儿童、员工、弱势群体。
- EU / EEA 数据向中国或其他非充分性认定国家传输。
- 处理活动可能对个人权利和自由造成高风险。

## 5. 结论强度

| 情况 | 结论强度 |
| --- | --- |
| 官方来源 + 用户事实足够 | 可输出初筛结论 |
| 官方来源足够但用户事实不足 | 输出假设下初筛和事实缺口 |
| 仅有培训材料或专业文章 | 输出参考提示，不输出法律结论 |
| 涉及监管调查、罚款、暂停传输 | 必须提示人工复核 |
