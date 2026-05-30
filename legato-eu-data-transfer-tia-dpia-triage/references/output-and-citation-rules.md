# 输出与引用规则：EU TIA/DPIA 初筛

## 何时读取本文件

当准备输出欧盟数据传输风险初筛、TIA / DPIA 结论、案例启示或正式报告时，必须先读取本文件。

## 本文件影响什么决策

本文件决定聊天摘要与正式 Markdown 报告结构、GDPR / EDPB / 判例引用方式、风险标签和人工复核边界。

## 不适用场景

仅做官方来源核验、DPA 检索或 query 构造时，不以本文件替代来源核验和搜索策略。

> 本文件供 `legato-eu-data-transfer-tia-dpia-triage` 运行时使用。
> 与 `official-source-verification.md` 协同工作：该文件已收录 12 个带 URL 的官方来源入口，本文件聚焦引用格式、确定性标签和输出纪律。
> 本 Skill 独立打包，不依赖 `_shared` 或上级目录。

## 1. 输出层级

Legato 产品中，本 Skill 输出固定为"聊天摘要 + 强制正式 Markdown 交付物"：

1. 聊天窗口简短 Markdown 摘要，只帮助用户快速理解方向。
2. 正式 Markdown 报告交付物，是研究任务的强制交付面。

Markdown / Word 导出由产品交付物功能承担。

内部工具协议：

- 首轮研究任务必须使用 `write_file` 生成完整 Markdown 交付物，再使用 `present_artifacts` 展示。
- 同一研究的后续修改、补充、纠错、扩写或结构调整，必须使用 `edit_file` 更新既有交付物，再使用 `present_artifacts` 展示。
- 后续对话如果是无关新研究，必须重新使用 `write_file` 创建新的 Markdown 交付物，再使用 `present_artifacts` 展示。
- 纯解释既有交付物中某段含义、且不新增结论、依据、结构或行动清单时，可以只在聊天窗口回答。
- 工具名只用于 Skill 内部执行协议、eval 和研发说明，不得进入用户可见报告。

## 2. 聊天窗口回答

聊天窗口回答要短，帮助用户快速判断结果方向。

默认结构：

```markdown
## 简要结论
-

## 关键依据 / 风险
-

## 正式报告
- 已生成正式 Markdown 交付物，并已展示。

## 限制与复核
-
```

要求：

- 先给答案，再讲依据。
- 只放关键结论和限制。
- 不把完整研究报告塞进聊天消息。
- 不展示内部工具、供应商、配置编号或函数名。

## 3. 正式 Markdown 报告

首轮研究任务必须生成一份最终 Markdown 报告。报告结构根据 TIA/DPIA 场景定制：

```markdown
# {TIA / DPIA 初筛报告标题}

## 1. 任务范围
## 2. 执行摘要
## 3. 数据流还原与业务场景
## 4. 检索范围与来源说明
## 5. GDPR 适用性判断
## 6. 跨境传输识别（含远程访问）
## 7. 传输机制分析（Adequacy / SCC / BCR / 例外）
## 8. TIA 初筛分析
## 9. DPIA 触发判断
## 10. 补充措施建议
## 11. 风险分级 / 结论强度
## 12. 引用与证据
## 13. 结论限制与人工复核触发
```

## 4. 来源层级

| 层级 | 来源 | 使用规则 |
| --- | --- | --- |
| 高 | GDPR 条文原文（Art.44-49）；EDPB 正式指南、建议和约束性决定；DPA 正式裁决和执法决定（Meta DPC IN-20-8-1、TikTok DPC IN-21-9-2 等）；CJEU 判例（C-311/18 Schrems II）；EU SCCs 2021 官方文本；adequacy decision 正式文件 | 可支撑决定性结论 |
| 中 | IAPP 专业报告和分析；律所深度文章（如 Freshfields、Hogan Lovells 数据传输专题）；ICLG、Chambers、Legal500 数据保护指南 | 可辅助框架和实务判断 |
| 低 | 行业新闻、博客评论、社交媒体讨论、培训材料 | 只作动态信号 |
| 待确认 | 未返回可定位片段、版本不明、来源冲突或事实缺失 | 必须提示人工复核 |

### 与 official-source-verification.md 的衔接

`official-source-verification.md` 已收录以下 12 个官方来源入口，本 Skill 的引用优先对齐这些已验证来源：

| 编号 | 来源 | 定位 |
| --- | --- | --- |
| 1 | GDPR Chapter V（EUR-Lex PDF） | Art.44-49 条文 |
| 2 | GDPR Art.44-49 逐条页面（卢森堡 CNPD） | 辅助快速定位 |
| 3 | EDPB Recommendations 01/2020 v2.0 | TIA 六步框架 |
| 4 | EDPB Recommendations 01/2020 概览页 | 版本核验 |
| 5 | EDPB / WP29 DPIA Guidelines | DPIA 触发判断 |
| 6 | EDPB DPIA Template 2026 | 最新模板动态 |
| 7 | CJEU C-311/18（Schrems II） | TIA 法理基础 |
| 8 | Meta DPC IN-20-8-1 | 案例红旗 |
| 9 | Meta EDPB Binding Decision 1/2023 | 案例补充 |
| 10 | TikTok DPC Inquiry 页面 | EU -> 中国传输案例 |
| 11 | TikTok DPC final decision PDF | 远程访问/TIA 核心案例 |
| 12 | EU SCCs 2021 / EDPB-EDPS Joint Opinion | SCC 路径核验 |

引用时应优先使用上述已收录 URL，而非自行搜索到的替代链接。

### 用户可见来源命名

报告、聊天回答、引用脚注和来源说明只使用用户能理解的来源名称：

| 用户可见名称 | 使用场景 |
| --- | --- |
| 本次挂载资料 / 项目资料 | 用户本轮选择或挂载的项目文件、内部材料 |
| GDPR 条文 | EUR-Lex 或 CNPD 上的 GDPR Chapter V |
| EDPB 正式指南 | EDPB 官方发布的 Recommendations、Guidelines |
| DPA 裁决 | 数据保护机构（DPC、CNIL、BfDI 等）正式裁决 |
| CJEU 判例 | 欧盟法院判例 |
| 高质量法律指南 | ICLG、Chambers、Legal500、DLA Piper Data Protection 等 |
| 专业实务解读 | 律所、IAPP 等专业机构文章 |
| 联网公开来源 | 公开网页、新闻、专业文章 |

不要在用户可见内容中写供应商名称、内部配置编号或工具函数名。

## 5. 脚注格式

优先使用 Markdown 脚注：

```markdown
正文中的关键法律结论[^1]。

[^1]: [来源标题](URL) - 层级 | 来源类型 | 日期 | 结论说明
```

GDPR 条文脚注示例：

```markdown
[^1]: [GDPR Article 46](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679) - 高 | 法规原文 | 2016-05-04 | 规定在缺乏 adequacy decision 时，控制者或处理者只有在提供适当保障措施后才可传输
```

EDPB 指南脚注示例：

```markdown
[^2]: [EDPB Recommendations 01/2020 v2.0](https://edpb.europa.eu/system/files/2021-06/edpb_recommendations_202001vo.2.0_supplementarymeasurestransferstools_en.pdf) - 高 | 官方指南 | 2021-06 | 提供六步 TIA 框架和补充措施示例清单
```

DPA 裁决脚注示例：

```markdown
[^3]: [Meta DPC Decision IN-20-8-1](https://www.edpb.europa.eu/system/files/2023-05/final_for_issue_ov_transfers_decision_12-05-23.pdf) - 高 | DPA 裁决 | 2023-05 | 认定 SCC + TIA 不充分，处以 12 亿欧元罚款
```

指南类脚注示例：

```markdown
[^4]: [ICLG Data Protection - EU](https://iclg.com/practice-areas/data-protection-laws-and-regulations/eu) - 中 | 专业指南 | 2024 | 用于搭建 TIA 分析框架；关键法律结论仍需 EDPB/EUR-Lex 核验
```

## 6. 确定性标签

| 标签 | 含义 | 适用来源 |
| --- | --- | --- |
| [法规原文] | 直接引用 GDPR 条文或 EU 法规原文 | GDPR Art.44-49、EU SCCs 2021、adequacy decision 官方文本 |
| [权威解读] | 来自 EDPB 正式指南或 DPA 正式裁决 | EDPB Recommendations 01/2020、DPA 裁决 PDF、CJEU 判例 |
| [一般评论] | 来自律所文章、IAPP 分析、指南概述 | ICLG、Chambers、律所 client alert |
| [待验证] | 来源不确定、无法确认版本、或 AI 生成补全 | 未找到官方核验的二手信息 |

### GDPR 条文特殊注意事项

GDPR 条文中的情态动词有严格法律含义差异，直接影响结论强度：

| GDPR 措辞 | 法律含义 | 转述规则 |
| --- | --- | --- |
| "shall" | 强制义务，必须遵守 | 不得弱化为"应当考虑"或"建议" |
| "shall not" | 绝对禁止 | 不得转述为"不建议"或"通常不被允许" |
| "may" | 许可或裁量，可以选择 | 不得强化为"必须"或"应当" |
| "should" | 推荐（recital 中常见） | 不得等同于 "shall" 的强制义务 |
| "in particular" | 举例但非穷尽 | 不得转述为"仅限于" |
| "without prejudice to" | 不影响/不妨碍 | 不得理解为"替代"或"优先于" |

## 7. 精度纪律

- 源文件说 "may require" 不得转述为 "requires"。
- 源文件说 "in general" 或 "typically" 不得转述为 "always"。
- 源文件说 "should" 不得转述为 "must"。
- GDPR 条文中的 "shall" 和 "may" 有严格法律含义差异（见上表）。
- EDPB 指南中的 "recommendations" 是建议性质，不等同于 GDPR 条文的法律约束力。
- DPA 裁决的效力通常限于该 DPA 管辖范围，不得直接推及全欧盟（除非 EDPB 约束性决定）。
- CJEU 判例对所有 EU 成员国法院有约束力，但具体适用仍需结合个案事实。
- 多个来源说法不一致时，分别列明，不揉成折中结论。

## 8. 必须引用的内容

- 所有决定性法律结论。
- GDPR 适用性判断依据（Art.3 地域范围、Art.44 跨境传输定义）。
- 传输机制判断（adequacy、SCC、BCR、认证、例外）。
- TIA 初筛的每一步结论。
- DPIA 触发判断依据。
- 补充措施的技术和法律依据。
- "当前有效""最新变化""草案 / 已生效"等时效判断。
- DPA 裁决中的关键事实和裁决理由。
- 依赖二手来源或弱来源的判断。
- 实务操作建议中的关键步骤。

## 9. 不得引用的内容

- 只有文件名、知识库名、网页标题，但没有可定位原文片段。
- 搜索摘要不足以支撑结论的内容。
- 推测性常识补全。
- AI 生成答案本身。
- GDPR 培训材料中的非官方解释（仅作辅助理解，不作法律依据）。

### 引用真实性底线

以下内容属于 LLM 模板占位符或幻觉产物，不得出现在任何引用、脚注或来源标注中：

- `[Valid]`、`[Effective]`、`[Current Date]`、`[现行有效]`、`[有效]`
- `[Body]`、`[X]`、`[Name]`、`[Date]`、`[数量]`、`[客户名称]`
- 未经实际检索验证的 URL 或域名（不得编造看起来合理但未实际访问的来源地址）
- 无对应脚注实体的纯数字标记（如 `[1]`、`[2]` 但文末无对应脚注条目）

引用必须来自实际检索命中或知识库召回的结果。不确定来源是否真实存在时，标为 [待验证] 而非伪造引用。

## 10. 冲突处理

来源冲突时：

- 分别列明冲突来源。
- 比较效力层级：GDPR 条文 > EDPB 约束性决定 > DPA 裁决 > EDPB 指南 > 律所文章。
- 比较发布时间：更晚的 EDPB 指南可能修正或补充早期指南。
- 比较适用范围：单个 DPA 裁决 vs EDPB 约束性决定的全欧盟效力差异。
- 如果仍无法收口，标为"不明确"或"需当地 DPA 确认"。

不要把冲突来源揉成一个看似确定的折中结论。

特别注意：不同成员国 DPA 可能对同一问题持不同立场。当出现 DPA 立场分歧时，应明确指出分歧存在，并建议用户根据数据处理主要 establishment 所在成员国确定适用立场。

## 11. 翻译和原文

- GDPR 条文引用必须使用官方英文版，不得使用中文译本作为权威依据。
- 关键 GDPR 术语保留英文原文：Transfer Impact Assessment、Standard Contractual Clauses、Binding Corporate Rules、Adequacy Decision。
- 用中文交付时，第一次出现原文术语后应解释含义。
- DPA 裁决引用应注明 DPA 名称和管辖区。
- CJEU 判例引用应使用标准引用格式：Case C-xxx/xx, [当事人名称]。
