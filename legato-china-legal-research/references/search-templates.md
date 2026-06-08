# 中国法搜索查询模板

## 何时读取本文件

当已经确定需要使用元典 MCP 或联网搜索，并需要构造法条、案例、监管材料或企业法律事实 query 时，读取本文件。

**前置依赖**：应先读取 `search-strategy.md` 确定检索路径后，再读取本文件构造查询。

## 本文件影响什么决策

本文件决定语义检索、关键词检索、案例检索、官方域名搜索和引用复核的查询写法。

## 不适用场景

尚未确定检索路径、已有精确法条 / 案号可直接获取详情，或只是在生成报告结构时，不优先读取本文件。

> 本文件是 `legato-china-legal-research` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{关键词}`、`{法规名}`、`{案由}`、`{年份}` 为占位符，运行时替换为实际值。

## 1. 元典 MCP 使用指引

### 何时用语义检索 vs 关键词检索

| 场景 | 推荐工具 | 原因 |
| --- | --- | --- |
| 不确定该看哪部法、涉及哪个法律领域 | 法条语义检索（`yuandian_law_vector_search`） | 用自然语言描述问题，由模型匹配最相关法条 |
| 已知法规名、条号、制度关键词 | 法条关键词检索（`yuandian_rh_ft_search`、`yuandian_rh_fg_search`） | 精确定位，效率最高 |
| 按事实场景寻找相似裁判口径 | 案例语义检索（`yuandian_case_vector_search`） | 用自然语言描述场景，匹配相似案例 |
| 按案由、法院、省份、案号等线索定位 | 案例结构化检索（`yuandian_rh_qwal_search`、`yuandian_rh_ptal_search`） | 已知线索明确，结构化条件效率最高 |
| 已有模糊结果，需确认引用准确性 | 引用复核（`yuandian_hall_detect`） | 复核法规、法条、案号、案例名等引用 |

### 语义检索关键词构造模板

```
{用户问题的法律主题} 相关法条
{具体制度名称} 法律依据
{业务场景描述} 涉及哪些法律规定
```

示例：

```
竞业限制 违约金 相关法条
个人信息跨境传输 法律依据
股权代持 实际出资人 涉及哪些法律规定
```

### 关键词检索模板

```
法规名：{法规名}，关键词：{关键词}
法规名：{法规名}，条号：{条号}
```

示例：

```
法规名：劳动合同法，关键词：竞业限制
法规名：个人信息保护法，条号：第38条
```

## 2. 法规库联网搜索模板

当需要核验法条时效状态、确认最新修订时，使用以下模板限定官方域名搜索：

### 全国人大法律法规数据库（flk.npc.gov.cn）

```
{关键词} site:flk.npc.gov.cn
{法规名} site:flk.npc.gov.cn
{法规名} 最新修订 site:flk.npc.gov.cn
```

示例：

```
反垄断法 site:flk.npc.gov.cn
个人信息保护法 site:flk.npc.gov.cn
公司法 2023修订 site:flk.npc.gov.cn
```

### 法律、法规、司法解释搜索

```
"{法规名}" site:flk.npc.gov.cn
"{法规名}" "{具体条款}" site:flk.npc.gov.cn
{关键词} 司法解释 site:flk.npc.gov.cn
```

示例：

```
"劳动争议司法解释" site:flk.npc.gov.cn
"反不正当竞争法" "商业秘密" site:flk.npc.gov.cn
合同纠纷 司法解释 site:flk.npc.gov.cn
```

## 3. 法院 / 检察院搜索模板

### 最高人民法院（court.gov.cn）

```
{关键词} site:court.gov.cn
{案由} 指导性案例 site:court.gov.cn
{关键词} 司法解释 site:court.gov.cn
{关键词} 典型案例 {年份} site:court.gov.cn
```

示例：

```
知识产权侵权 site:court.gov.cn
民间借贷 指导性案例 site:court.gov.cn
个人信息保护 司法解释 site:court.gov.cn
劳动争议 典型案例 2025 site:court.gov.cn
```

### 最高人民检察院（spp.gov.cn）

```
{关键词} site:spp.gov.cn
{关键词} 典型案例 site:spp.gov.cn
{关键词} 检察解释 site:spp.gov.cn
```

示例：

```
知识产权保护 site:spp.gov.cn
企业合规 典型案例 site:spp.gov.cn
```

### 其他政府机构

```
{关键词} site:mofcom.gov.cn
{关键词} site:samr.gov.cn
{关键词} site:pbc.gov.cn
{关键词} site:safe.gov.cn
{关键词} site:customs.gov.cn
```

## 4. 高质量指南搜索模板

```
{关键词} site:iclg.com
{关键词} site:practiceguides.chambers.com
{关键词} site:lexology.com
{关键词} site:lexmundi.com
```

### 中文法律资源搜索

```
{关键词} site:chinalawedu.com
{关键词} site:pkulaw.com
{关键词} site:law.wkinfo.com.cn
{关键词} 走出去智库 OR CGG
```

### 中文律所实务文章搜索

```
"{关键词}" site:kingandwood.com
"{关键词}" site:zhonglun.com
"{关键词}" site:fangda.com
"{关键词}" site:hankunlaw.com
"{关键词}" site:jingtian.com
```

## 5. 确定性标签在报告中的使用示例

### 示例 1：法条原文

```markdown
根据《劳动合同法》第 23 条，竞业限制期限不得超过二年[^1]。

[^1]: 《劳动合同法》第 23 条 - 高 | 法条原文 | 2026-05-25 | 法条原文明确规定竞业限制期限上限为二年
```

### 示例 2：权威案例

```markdown
最高法指导案例认为，实际出资人与名义股东之间的代持协议在不违反法律强制性规定时有效[^2]。

[^2]: 指导性案例第 XX 号（{案号}）- 高 | 权威解读 | 2024 | 最高法指导案例确认股权代持协议效力的一般规则
```

### 示例 3：实务解读

```markdown
实务中，法院通常会综合考虑竞业限制的范围、地域和期限来判断合理性[^3]。

[^3]: [某律所竞业限制实务分析](URL) - 中 | 一般评论 | 2025 | 梳理近年司法实践中的常见裁判思路；具体案件仍需个案判断
```

### 示例 4：待验证

```markdown
有观点认为，该类安排可能被认定为变相竞业限制[^4]。

[^4]: 开放搜索结果 - 待确认 | 待验证 | 2026 | 未找到法规原文或权威案例支撑，仅为行业观点；建议人工复核
```

### 示例 5：时效敏感

```markdown
当前个人信息出境标准合同备案制度已生效实施[^5]。

[^5]: 国家互联网信息办公室《个人信息出境标准合同办法》第 2 条 - 高 | 法条原文 | 2026-05-25 | 现行有效；该领域规则变化频繁，建议核实最新版本
```
