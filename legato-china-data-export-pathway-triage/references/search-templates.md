# 搜索查询模板（中国数据出境路径分流）

## 何时读取本文件

当已经确定需要联网搜索，并需要构造数据出境、安全评估、标准合同、认证、豁免或地方负面清单 query 时，读取本文件。

## 本文件影响什么决策

本文件决定查询词、官方域名限定方式和不同主题的搜索模板，避免模型自行生成过宽或不可复用的 query。

## 不适用场景

尚未判断是否需要联网检索、已有官方 URL 可直达，或只需根据既有来源输出结论时，不优先读取本文件。

> 本文件是 `legato-china-data-export-pathway-triage` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{topic}`、`{keyword}` 为占位符，运行时替换为实际值。

## 1. 官方域名限定搜索

### 网信办 cac.gov.cn

```
数据出境安全评估 site:cac.gov.cn
个人信息出境 标准合同 site:cac.gov.cn
数据出境 认证 site:cac.gov.cn
数据跨境流动 site:cac.gov.cn
重要数据 site:cac.gov.cn
数据出境 申报指南 site:cac.gov.cn
{keyword} site:cac.gov.cn
```

### 国家法律法规数据库 flk.npc.gov.cn

```
数据跨境传输 site:flk.npc.gov.cn
个人信息保护 site:flk.npc.gov.cn
数据安全 site:flk.npc.gov.cn
网络安全 数据 site:flk.npc.gov.cn
```

### 国务院 gov.cn

```
数据出境 site:gov.cn
数据跨境 site:gov.cn
个人信息出境 site:gov.cn
```

### 市场监管总局 samr.gov.cn

```
个人信息保护 认证 site:samr.gov.cn
数据安全 认证 site:samr.gov.cn
```

## 2. 核心法规直达搜索

按数据出境分流路径的法规体系，使用以下直达搜索模板：

| 路径 | 搜索模板 |
| --- | --- |
| 安全评估 | `数据出境安全评估办法 site:cac.gov.cn` |
| 安全评估 | `数据出境安全评估 申报指南 site:cac.gov.cn` |
| 标准合同 | `个人信息出境 标准合同办法 site:cac.gov.cn` |
| 标准合同 | `标准合同 备案 site:cac.gov.cn` |
| 认证 | `个人信息保护认证 实施规则 site:cac.gov.cn` |
| 认证 | `数据出境 认证 site:samr.gov.cn` |
| 新规/豁免 | `促进和规范数据跨境流动规定 site:cac.gov.cn` |
| 网络数据安全管理条例 | `网络数据安全管理条例 site:gov.cn` |
| PIPL 原文 | `个人信息保护法 site:flk.npc.gov.cn` |
| 自贸区清单 | `{自贸区名称} 数据出境 负面清单` |

## 3. 路径分流判断要素搜索

分流判断的关键要素需要精确搜索：

### CIIO 相关

```
关键信息基础设施运营者 认定 site:cac.gov.cn
CIIO 数据出境 site:cac.gov.cn
关键信息基础设施 安全保护条例 site:flk.npc.gov.cn
```

### 重要数据相关

```
重要数据 识别 site:cac.gov.cn
重要数据 目录 site:cac.gov.cn
数据分类分级 site:cac.gov.cn
重要数据 认定 国家标准
```

### 数量级阈值相关

```
数据出境 100万人 site:cac.gov.cn
敏感个人信息 1万人 site:cac.gov.cn
个人信息 出境 数量 site:cac.gov.cn
```

### 免申报/豁免相关

```
数据出境 免申报 site:cac.gov.cn
数据出境 豁免 site:cac.gov.cn
数据跨境 负面清单 site:cac.gov.cn
{自贸区名称} 数据出境 负面清单 site:cac.gov.cn
```

## 4. 高质量指南和权威解读搜索

```
China data protection site:dlapiperdataprotection.com
China data export site:iclg.com
China cross-border data transfer site:practiceguides.chambers.com
China data protection GDPR site:iclg.com
China data localization site:practiceguides.chambers.com
```

## 5. 律所实务文章搜索

### 通过 Lexology 发现

```
China data export site:lexology.com {year}
China cross-border data site:lexology.com {year}
```

找到相关文章标题和作者后，去律所官网查找免费全文。

### 主要国际所搜索

```
"China" "data export" OR "cross-border data" legal update OR client alert {year}
"China" "data export" site:bakermckenzie.com
"China" "data export" site:herbertsmithfreehills.com
```

### 中文律所搜索

```
数据出境 安全评估 site:wechat.qq.com 金杜 OR 中伦 OR 方达 OR 汉坤
数据出境 路径 site:wechat.qq.com 天元 OR 世辉 OR 通商
数据出境 合规 实务 走出去智库 OR CGG
数据出境 申报 经验 律所
```

## 6. 确定性标签在分流判断中的使用示例

分流类 Skill 的每一条判断依据必须标注确定性标签。以下为典型使用示例：

### 安全评估路径判断

```markdown
根据《数据出境安全评估办法》第四条[^1]，数据处理者向境外提供以下数据时，应当申报安全评估：
（一）向境外提供重要数据；
（二）关键信息基础设施运营者向境外提供个人信息；
（三）处理 100 万人以上个人信息的数据处理者向境外提供个人信息；
（四）自上年 1 月 1 日起累计向境外提供 10 万人以上个人信息或者 1 万人以上敏感个人信息。

[^1]: [《数据出境安全评估办法》第四条](https://www.cac.gov.cn/2022-07/07/c_1658811536396503.htm) - 高 | 法规原文 | 2022-07-07 | 明确列明四类强制安全评估情形
```

### 标准合同路径判断

```markdown
根据《个人信息出境标准合同办法》第四条[^2]，非 CIIO 且处理个人信息不满 100 万人、累计向境外提供不满 10 万人（或敏感信息不满 1 万人）的，可采用标准合同路径。

[^2]: [《个人信息出境标准合同办法》第四条](https://www.cac.gov.cn/2023-02/24/c_1678884830036813.htm) - 高 | 法规原文 | 2023-02-24 | 规定标准合同适用条件
```

### 免申报情形判断

```markdown
根据《促进和规范数据跨境流动规定》第五条[^3]，以下情形免予申报安全评估、订立标准合同、通过认证...

[^3]: [《促进和规范数据跨境流动规定》第五条](https://www.cac.gov.cn/2024-03/22/c_1712776611775634.htm) - 高 | 法规原文 | 2024-03-22 | 规定免申报情形
```

### 待确认情形示例

```markdown
某律所文章提到可能存在"10 万人"的新门槛[^4]，但在《促进和规范数据跨境流动规定》法规原文中未找到对应条文调整，建议以法规原文为准并关注后续配套细则。

[^4]: [某律所 - 数据出境新规解读](URL) - 中 | 实务解读 | 2025 | 此为律所解读中的观点，具体门槛仍需法规原文核验 [待验证]
```

### 冲突来源处理示例

```markdown
关于安全评估门槛，存在以下两种口径：
- 《数据出境安全评估办法》第四条[^1]：100 万人
- 某解读文章[^5]：提到可能调整为 XX 万人

由于《促进和规范数据跨境流动规定》未明确修改此门槛，当前仍以 100 万人为基准。

[^5]: [某律所 - 新规影响分析](URL) - 中 | 实务解读 | 2025 | 可能的调整方向 [待验证]
```

## 7. 搜索结果评估纪律

### 确定性标签

报告中的每条数据出境分流信息必须标注确定性等级：

| 标签 | 含义 | 适用来源 |
| --- | --- | --- |
| [法规原文] | 直接引用法条或法规原文 | L1 高层级：PIPL、安全评估办法、标准合同办法、新规原文 |
| [权威解读] | 来自网信办官方解读、TC260 标准、权威法律指南 | L2 中层级 |
| [一般评论] | 来自律所文章、行业分析 | L3 中/低层级 |
| [待验证] | 来自 AI 生成、论坛、无法确认来源 | L4 或无来源 |

关键规则：

- 法规中说"可以"不得转述为"应当"。
- 法规中说"一般"不得转述为"一律"。
- 数量级阈值必须引用法规原文条款号。
- 多个来源说法不一致时，分别列明，不揉成折中结论。

### 联网搜索后的行为边界

- 搜到指南类页面（DLA Piper / ICLG / Chambers），只提取框架结构，不直接概括其中的法律条文作为自己的分析。
- 需要法条内容时，从指南中找到法条引用，再回 `cac.gov.cn` 或 `flk.npc.gov.cn` 查原文。
- 不能把搜索摘要直接写成分流结论。
- 不能把律所解读的内容等同于法规本身。
- 分流判断的核心门槛和条件必须有法规原文支撑。

### 访问状态标注

对推荐的每个资源，标注其访问状态：

- [已验证可访问]：URL 可用，内容可读
- [需注册]：URL 可用但需免费注册
- [需付费]：需要订阅
- [未找到]：该资源无相关内容
- [已失效]：URL 返回 404 或内容已迁移
- [未验证]：无法检查（如网络问题）
