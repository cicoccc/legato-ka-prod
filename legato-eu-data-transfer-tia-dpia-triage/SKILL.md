---
name: legato-eu-data-transfer-tia-dpia-triage
description: 当用户明确询问 GDPR 下 EU / EEA 数据向中国或第三国传输、欧洲用户数据由中国总部或中国工程师访问、远程访问是否构成传输、SCC 是否足够、是否需要 TIA、是否触发 DPIA、欧盟法院 C-311/18、Meta 或 TikTok DPC 裁决对企业的启示时使用。本 Skill 只处理欧盟侧数据传输、SCC、TIA、DPIA 和相关裁决红旗。不用于中国数据出境安全评估 / 标准合同 / 认证 / 豁免路径判断、全球数据流动结构入口初筛、纯中国法条检索、纯劳动 / 税务 / 组织问题或正式法律意见。
---

# 欧盟数据传输风险初筛 Skill

> 版本：v0.4  
> 日期：2026-05-31  
> 状态：productized  
> 维护者：Legato产品团队  
> 运行模式：v0.1 固定 `agent`

## 定位

本 Skill 是 `跨境数据合规研究包` 中的欧盟 / GDPR 专精 Skill，用于 EU / EEA 数据向中国或第三国传输的早期风险初筛，尤其是远程访问、SCC、TIA、DPIA 和典型裁决红旗。

它的核心不是 GDPR 百科，而是把欧盟法院 C-311/18 判决后的传输影响评估逻辑、EDPB 六步框架、DPC 裁决中的中国远程访问风险和 DPIA 触发判断产品化。

本 Skill 只做初筛、风险雷达、材料清单和人工复核触发，不替代欧盟律师、DPO、当地监管沟通、正式 TIA / DPIA 或最终法律意见。

## 适用场景

- 欧洲用户数据能否由中国总部、中国研发、中国运维或中国供应商访问。
- 数据在 EU / EEA 服务器，但中国工程师 VPN / 后台 / 工单系统远程访问。
- 已签 SCC，但需要判断是否仍需 TIA、补充措施或 DPIA。
- 评估欧盟法院 C-311/18、Meta DPC、TikTok DPC 对 EU -> 中国传输的影响。
- 欧洲产品涉及敏感数据、大规模监控、自动化决策、新技术或 AI 训练，需要判断 DPIA 触发。

## 不适用边界

- 中国数据出境安全评估、标准合同、认证、豁免、自贸区负面清单，应转 `legato-china-data-export-pathway-triage`。
- 全球数据流动结构和管理层风险雷达，应转 `legato-cross-border-data-flow-compliance`。
- 纯中国法条检索，应转 `legato-china-legal-research`。
- 纯劳动、税务、组织或德国运营问题，应转对应出海组织 / 德国税务合规 Skill。
- 监管调查抗辩、罚款申辩、正式 TIA / DPIA、DPA 沟通或最终法律意见，不由本 Skill 闭环。

## 最低输入

最低可启动输入：

- GDPR 适用线索：EU / EEA 设立、面向 EU / EEA 个人提供服务、监控 EU / EEA 个人行为。
- 传输方向：EU / EEA -> 中国或第三国。
- 传输方式：网络传输、远程访问、后台访问、工单、物理介质、集团内共享。
- 数据类型和规模。

推荐输入：

- 角色：controller、processor、sub-processor、joint controller。
- 已采取保障：adequacy、SCC、BCR、认证、加密、访问控制、日志、数据本地化。
- 是否涉及敏感数据、大规模监控、自动化决策、新技术、未成年人或 AI 训练。

信息不足时不调用即时追问工具；基于明确假设输出有限初筛，并列出会改变结论的事实缺口。

## 研究执行顺序

1. 判断 GDPR 是否适用：设立标准、定向提供商品 / 服务、监控行为。
2. 判断是否发生跨境传输，包括远程访问、集团内访问、处理者 / 子处理者访问。
3. 按 `Reference 使用路由` 读取官方来源与裁决核验范围，先确认 GDPR / EDPB / CJEU / DPC 等来源优先级。
4. 判断传输路径：adequacy -> SCC / BCR / 认证等适当保障 -> 特殊例外。
5. 对 SCC 路径执行 TIA 初筛：目的地国法律和实践、公共机构访问权、监管监督、救济权利、国际条约和补充措施。
6. 判断补充措施是否仅是技术 / 合同 / 组织措施，是否足以应对具体传输风险。
7. 判断 DPIA 触发：高风险处理、敏感数据、大规模监控、自动化决策、新技术等。
8. 输出传输风险雷达、行动清单、证据缺口和人工复核触发。

## Reference 使用路由

| 触发情况 | 必读文件 | 读取目的 | 读后动作 |
| --- | --- | --- | --- |
| 开始任何欧盟数据传输风险初筛 | `references/official-source-verification.md` | 确认 GDPR、EDPB、欧盟委员会、CJEU、DPC 等官方来源和裁决核验边界 | 再判断传输路径、SCC、TIA 或 DPIA |
| 涉及 C-311/18、Meta、TikTok、远程访问、SCC、TIA 或 DPIA | `references/official-source-verification.md` | 确认哪些裁决或指南可支撑决定性结论，哪些只能作为参考 | 再形成风险雷达和人工复核提示 |
| 需要检索 EDPB、EUR-Lex、欧委会或 DPA 材料 | `references/search-strategy.md` | 确认已收录来源、官方域名搜索和 DPA 搜索的顺序 | 再执行联网核验 |
| 需要构造 TIA、DPIA、SCC 或远程访问 query | `references/search-templates.md` | 复用欧盟官方域名、DPA 和案例查询模板 | 再调用联网搜索；不得自行泛化 query |
| 准备输出传输风险初筛或正式报告 | `references/output-and-citation-rules.md` | 检查 GDPR / EDPB / 判例引用、风险标签和人工复核边界 | 再生成交付物 |
| 准备生成正式报告、更新既有交付物或创建无关新研究交付物 | `assets/eu-data-transfer-tia-dpia-report-template.md` | 使用正式报告模板作为唯一结构真源，避免只输出聊天短答或沿用旧报告结构 | 再调用 `write_file` / `edit_file` 和 `present_artifacts` |

## 任务分型

| 类型 | 主路径 | 输出重点 |
| --- | --- | --- |
| EU -> 中国远程访问 | 访问方式 + 角色 + 数据类型 | 是否构成传输、SCC / TIA 红旗 |
| SCC / TIA 初筛 | SCC 状态 + 目的地国 + 补充措施 | TIA 缺口、补充措施、复核点 |
| DPIA 触发 | 处理活动 + 高风险因素 | DPIA 触发、模板字段、行动清单 |
| 案例启示 | 欧盟法院 C-311/18 / Meta / TikTok | 裁决要点、对中企启示、限制 |
| 传输机制比较 | adequacy、SCC、BCR、认证、例外 | 可用路径、禁止滥用例外 |

## 运行约束

- `mode = agent`。
- 不调用 `ask_user_question`。
- 不使用旧 `query_kb`。
- 知识库检索主工具为 `query_legato_ragflow(query_text, top_k)`。
- 不自行选择知识库、文件夹或文件范围；检索范围由前端挂载和研究包配置决定。
- 联网搜索默认开启；GDPR、EDPB、欧盟委员会、DPC、CJEU、ICO 等规则和裁决必须以官方来源优先核验。
- 首轮研究任务必须使用 `write_file` 生成完整 Markdown 交付物，并使用 `present_artifacts` 展示；不得因只是 SCC、TIA、DPIA 或远程访问单点判断而省略交付物。
- 同一研究后续修改、补充、纠错或结构调整，必须使用 `edit_file` 更新既有交付物，再使用 `present_artifacts` 展示。
- 后续无关新研究必须重新使用 `write_file` 创建新的 Markdown 交付物，再使用 `present_artifacts` 展示。
- 不固定底层输出路径或文件名模板，由产品运行时处理落盘位置。
- 用户可见输出不得暴露内部工具名、供应商名、MCP ID 或函数名。

## 用户可见来源命名

| 内部来源 | 用户可见名称 |
| --- | --- |
| 当前挂载资料 / RAGFlow 检索 | 本次挂载资料 / 项目资料 |
| GDPR / EDPB / 欧盟委员会 / CJEU / DPC 官方材料 | EU 官方来源 |
| GDPR 培训和课程逐字稿 | 培训参考材料 |
| IAPP、律所和专业机构文章 | 联网公开来源 |
| 报告交付工具 | 正式报告交付物 |

## 引用与复核规则

- GDPR 条文、EDPB 指南、SCC、DPIA、DPC / CJEU 裁决必须使用官方来源或监管机构页面核验。
- IAPP 分析、TikTok 官方回应、律所文章只能作为补充参考，不能单独支撑决定性法律结论。
- GDPR 培训材料只能表述为培训参考材料，不得写成官方规则或其他专家心法。
- 无可定位片段不得挂引用编号。
- 涉及中国法律适用、SCC 是否充分、补充措施可接受性、DPIA 是否完成、监管调查或正式法律意见时，必须提示人工复核。

## 输出要求

聊天窗口只放传输初判、关键依据、TIA / DPIA 红旗、行动清单和交付物状态；聊天摘要不能替代正式交付物。

正式报告必须先读取并使用 `assets/eu-data-transfer-tia-dpia-report-template.md`。同一研究后续修改用 `edit_file` 更新原报告；无关新研究新建交付物。官方来源核验范围按 Reference 使用路由中的 `references/official-source-verification.md` 执行。

## 文件导航

- 官方来源与裁决核验范围：`references/official-source-verification.md`
- 搜索策略与结果评估纪律：`references/search-strategy.md`
- 搜索查询模板：`references/search-templates.md`
- 输出与引用规则：`references/output-and-citation-rules.md`
- 报告模板：`assets/eu-data-transfer-tia-dpia-report-template.md`
- Eval：`evals/evals.json`
