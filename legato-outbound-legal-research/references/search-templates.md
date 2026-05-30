# 搜索查询模板

> 本文件是 `legato-outbound-legal-research` 自带的搜索查询模板库。
> Agent 在执行搜索时应优先使用本文件中的模板构造查询，而非自行生成泛化查询。
> 模板中的 `{country}`、`{topic}`、`{domain}`、`{year}` 为占位符，运行时替换为实际值。

## 何时读取本文件

- 已确定法域、主题和来源层级后，需要构造联网搜索 query 时。
- 需要做官方域名限定搜索、专业数据库搜索或高质量指南搜索时。

## 本文件影响什么决策

- 决定 query 结构、关键词组合和是否使用 `site:` 限定，不决定结论本身。

## 不适用场景

- 不用于判断哪个来源优先；来源优先级见 `source-routing.md` 和 `search-strategy.md`。

## 1. 官方域名限定搜索

按法域从 `references/source-routing.md` 的「来源地图」中取域名，替换 `{domain}`：

```
{topic_keywords} site:{domain}
{topic_keywords} regulation OR law site:{domain}
{topic_keywords} guidelines OR requirements site:{domain}
```

示例：

```
foreign investment approval site:mpi.gov.vn
data protection registration site:pdpc.gov.sg
company incorporation site:acra.gov.sg
labour law employment contract site:mom.gov.sg
```

## 2. 专业数据库直达搜索

按法律主题直接在专属数据库中搜索：

| 主题 | 搜索模板 |
| --- | --- |
| 数据隐私 / 数据保护 | `{country} site:dlapiperdataprotection.com` |
| 劳动 / 就业 | `site:natlex.ilo.org {country} labour OR employment` |
| 外资准入 / 投资政策 | `site:investmentpolicy.unctad.org {country}` |
| 知识产权 / 专利 / 商标 | `site:wipo.int/wipolex {country} patent OR trademark` |
| 欧盟法律 | `site:eur-lex.europa.eu {topic_keywords}` |
| 翻译法规原文 | `"{country}" "{law_name}" site:global-regulation.com` |

## 3. 高质量法律指南搜索

```
{country} {topic} site:practiceguides.chambers.com
{country} {topic} site:iclg.com
{country} {topic} site:legal500.com/guides
{country} {topic} site:lexmundi.com
{country} {topic} site:lexology.com
```

针对特定实践领域的搜索：

| 领域 | 最佳搜索指南 | 搜索模板示例 |
| --- | --- | --- |
| 数据隐私 | DLA Piper > ICLG > Legal500 | `Vietnam site:dlapiperdataprotection.com` |
| 劳动用工 | ILO NATLEX > ICLG > Chambers | `Indonesia employment site:iclg.com` |
| 外资准入 | UNCTAD > 商务部 > Doing Business | `Thailand foreign investment site:practiceguides.chambers.com` |
| 知识产权 | WIPO Lex > ICLG | `Singapore patent site:wipo.int/wipolex` |
| 公司 / 商事 | Chambers > Legal500 > ICLG | `Germany corporate governance site:practiceguides.chambers.com` |
| 税务 | Chambers > EY/Deloitte > ICLG | `Vietnam corporate tax site:practiceguides.chambers.com` |
| 银行金融 | Legal500 > ICLG > Chambers | `Singapore banking finance site:legal500.com/guides` |
| 仲裁 / 争议 | Legal500 > ICLG > Chambers | `Indonesia arbitration site:legal500.com/guides` |
| 竞争 / 反垄断 | ICLG > Chambers > Legal500 | `Thailand merger control site:iclg.com` |
| 房地产 | ICLG > Chambers > Legal500 | `Vietnam real estate site:iclg.com` |
| 环境 / ESG | ICLG > Legal500 | `Indonesia environment climate site:iclg.com` |
| 并购 | Legal500 > Chambers > ICLG | `Singapore mergers acquisitions site:legal500.com/guides` |

## 4. Doing Business 系列搜索

```
"doing business in {country}" filetype:pdf {year}
"doing business in {country}" baker mckenzie OR deloitte OR ey OR pwc
"investing in {country}" legal guide filetype:pdf
```

## 5. 律所实务文章搜索

用于查找近期立法变化、新监管动态、热点合规话题的实务解读。

### 通过 Lexology 发现

```
{country} {topic} site:lexology.com {year}
```

找到相关文章标题和作者后，去律所官网查找免费全文。

### 直接在主要律所网站搜索

```
"{country}" "{topic}" legal update OR client alert {year}
"{country}" "{topic}" site:bakermckenzie.com
"{country}" "{topic}" site:cliffordchance.com
"{country}" "{topic}" site:nortonrosefulbright.com
"{country}" "{topic}" site:herbertsmithfreehills.com
"{country}" "{topic}" site:dlapiper.com
```

### 中文律所文章搜索

```
"{country}" "{topic}" site:wechat.qq.com 金杜 OR 中伦 OR 方达
"{country}" "{topic}" 走出去智库 OR CGG
```

## 6. 法规原文搜索

当需要找到特定法律或法规的原文时：

```
"{country}" "{law_name}" official translation OR English version
"{country}" "{law_name}" site:global-regulation.com
{country} {law_name} English text filetype:pdf
{country} {law_name} official gazette
```

## 7. 搜索结果评估纪律

### 确定性标签

报告中的每条法律信息必须标注确定性等级：

| 标签 | 含义 | 适用来源 |
| --- | --- | --- |
| [法规原文] | 直接引用法条或法规原文 | L1 官方法规库、政府公报、条约文本 |
| [权威指南] | 来自 Chambers / ICLG / Legal500 等权威指南 | L2 高质量法律指南 |
| [一般评论] | 来自律所文章、新闻、行业分析 | L3 律所实务文章、媒体 |
| [待验证] | 来自 AI 生成、论坛、无法确认来源，或未找到官方核验 | L4 或无来源 |

关键规则：

- 源文件说 "may require"，不得转述为 "requires"。
- 源文件说 "in general" 或 "typically"，不得转述为 "always"。
- 多个来源说法不一致时，分别列明，不揉成折中结论。

### 联网搜索后的行为边界

- 搜到指南类页面（Chambers / ICLG / Legal500），只提取目录结构和章节标题，不直接概括其中的法律条文作为自己的分析。
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
