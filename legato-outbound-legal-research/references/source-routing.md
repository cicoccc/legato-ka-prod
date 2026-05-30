# 出海法律研究来源路由规则

> 本文件是 `legato-outbound-legal-research` 自带的来源路由表。  
> 目标是把泛搜互联网改成“按法域和主题限定可信来源”的研究路径。  
> 本 Skill 独立打包时不得依赖上级目录、兄弟目录或外部共享文件。

## 何时读取本文件

- 开始任何出海法律与合规研究任务时。
- 需要确定目标法域、主题、官方来源、专业数据库或可信指南入口时。

## 本文件影响什么决策

- 决定优先检索哪些法域来源、是否先用专业数据库，以及后续搜索是否可进入开放搜索。

## 不适用场景

- 不用于生成搜索 query 的具体写法；query 模板见 `search-templates.md`。
- 不用于引用脚注和报告结构；输出规则见 `output-and-citation-rules.md`。

## 1. 来源地图

本 Skill 自带以下来源入口。表格不是穷尽清单；运行时可在这些入口不足时继续寻找目标国官方来源，并降低结论强度。

| 法域 / 来源类型 | 优先域名 | 主要用途 |
| --- | --- | --- |
| 中国大陆补充 | `flk.npc.gov.cn`、`court.gov.cn`、`spp.gov.cn`、`mofcom.gov.cn`、`samr.gov.cn`、`pbc.gov.cn`、`safe.gov.cn`、`customs.gov.cn` | 出海问题中的中国侧法规、监管、外汇、海关、商务背景 |
| 新加坡 | `sso.agc.gov.sg`、`judiciary.gov.sg`、`acra.gov.sg`、`mti.gov.sg`、`mom.gov.sg`、`iras.gov.sg`、`pdpc.gov.sg` | 法规、法院、公司注册、投资、劳动、税务、数据 |
| 越南 | `vbpl.vn`、`moj.gov.vn`、`mpi.gov.vn`、`dangkykinhdoanh.gov.vn`、`vnsw.gov.vn`、`viac.vn` | 法规、司法部、投资、企业注册、劳动、仲裁 |
| 印度尼西亚 | `peraturan.go.id`、`jdihn.go.id`、`oss.go.id`、`kemnaker.go.id`、`imigrasi.go.id`、`baniarbitration.org` | 法规、投资许可、劳动、移民、仲裁 |
| 泰国 | `ratchakitcha.soc.go.th`、`boi.go.th`、`doe.go.th`、`labour.go.th`、`immigration.go.th`、`thac.or.th` | 公报、投资、劳动、工作许可、移民、仲裁 |
| 德国 | `gesetze-im-internet.de`、`bmas.de`、`arbeitsagentur.de`、`make-it-in-germany.com`、`unternehmensregister.de`、`bundesfinanzministerium.de` | 法规、劳动、工作许可、公司、税务 |
| 英国 | `legislation.gov.uk`、`gov.uk`、`companieshouse.gov.uk`、`acas.org.uk`、`ico.org.uk` | 法规、政府指南、公司注册、劳动、数据 |
| 美国 | `congress.gov`、`ecfr.gov`、`federalregister.gov`、`state.gov`、`treasury.gov`、`ofac.treasury.gov`、`uscis.gov`、`dol.gov` | 法规、投资环境、制裁、移民、劳动 |
| 欧盟 | `eur-lex.europa.eu`、`commission.europa.eu`、`edpb.europa.eu`、`trade.ec.europa.eu` | 欧盟法规、政策、数据保护、贸易 |
| 高质量法律指南 | `iclg.com`、`practiceguides.chambers.com`、`legal500.com`、`lexmundi.com`、`lexology.com`、`state.gov` | 框架搭建、多法域比较、官方来源不足时的辅助 |
| 中国香港 | `legislation.gov.hk`、`sfc.hk`、`hkexnews.hk`、`legco.gov.hk`、`judiciary.hk`、`mpfa.org.hk` | 法例、资本市场、上市规则、监管指引、判例和强积金 |
| 哈萨克斯坦 | `zan.kz`、`gov.kz`、`invest.gov.kz`、`adilet.zan.kz`、`iaea.org` | 法规、政府政策、投资、能源和核能相关资料 |
| 尼日利亚 | `cac.gov.ng`、`cbn.gov.ng`、`firs.gov.ng`、`nipc.gov.ng`、`aluko-oyebode.com` | 公司注册、央行、税务、投资促进和本地强所实务 |
| 开曼群岛 | `legislation.gov.ky`、`cima.ky`、`judicial.ky`、`harneys.com`、`ogier.com`、`mourant.com` | 法例、金融监管、法院和离岸律所实务 |
| 澳大利亚 | `legislation.gov.au`、`austlii.edu.au`、`asic.gov.au`、`fwc.gov.au`、`oaic.gov.au` | 法规、案例、公司监管、劳动和数据保护 |

## 2. 主题-专业数据库速查表

部分法律主题有专属权威数据库，其结构化覆盖通常比泛搜更精准。Agent 在启动研究时应先查本表，确认该主题是否有专属数据库可优先使用。

| 法律主题 | 最佳专业数据库（按优先级） | 说明 |
| --- | --- | --- |
| 数据隐私 / 数据保护 | DLA Piper Data Protection Laws of the World > ICLG Data Protection > Legal500 | DLA Piper 交互式地图通常是最快入口 |
| 劳动 / 就业 | ILO NATLEX > ICLG Employment & Labour > Chambers | NATLEX 查法规原文；ICLG/Chambers 查实务概览 |
| 外资准入 / 投资政策 | UNCTAD Investment Policy Hub > 商务部国别指南 > Doing Business 系列 | UNCTAD 查双边投资条约和投资政策；商务部提供中文视角 |
| 知识产权 / 专利 / 商标 | WIPO Lex > ICLG Patents / Trademarks / Copyright | WIPO 查法规原文；ICLG 查实务指南 |
| 公司 / 商事 | Chambers > Legal500 > ICLG Corporate Governance | 三者覆盖均好；Chambers 无需注册 |
| 税务（公司税） | Chambers Corporate Tax > EY/Deloitte Tax Guides > ICLG Corporate Tax | Chambers 完全免费无需注册 |
| 欧盟法律 | EUR-Lex > ICLG（EU 专章） | EUR-Lex 是欧盟法规权威来源 |
| 银行金融 | Legal500 Banking & Finance > ICLG Lending & Secured Finance > Chambers | Legal500 在此领域法域覆盖广 |
| 仲裁 / 争议解决 | Legal500 Arbitration > ICLG International Arbitration > Chambers | 三者均有较强覆盖 |
| 房地产 | ICLG Real Estate > Chambers > Legal500 | ICLG 在房地产领域覆盖最广 |
| 并购 | Legal500 M&A > Chambers > ICLG M&A | 三者均强；Legal500 的法域比较工具有用 |
| 竞争 / 反垄断 | ICLG Merger Control / Competition > Chambers > Legal500 | ICLG 在竞争法领域覆盖尤为突出 |
| 环境 / ESG | ICLG Environment & Climate Change > Legal500 | 新兴领域，部分法域覆盖可能较薄 |

## 3. 总原则

- 先识别法域，再识别主题，再查主题-专业数据库速查表，再选择域名。
- 官方法源、监管机构、法院、仲裁机构和主管机关页面优先。
- 高质量法律指南用于搭框架和多法域比较，不替代官方来源。
- 中文资料可帮助快速理解问题，但关键结论应回到官方、英文或原语言来源核验。
- 低强度来源只能作动态信号，不能单独支撑决定性法律结论。

## 4. 法域识别

从用户问题中识别：

- 国家或地区：例如新加坡、越南、德国、阿联酋、尼日利亚、美国、英国。
- 区域或制度：例如欧盟、RCEP、OHADA、海牙公约、WTO。
- 多法域比较：例如越南 + 印尼 + 泰国。
- 中国大陆：若主任务是中国法，转交中国法律研究 Skill；若只是出海问题中的中国法背景，只作为补充边界处理。

无法识别具体法域时：

- 先按用户明确业务区域、市场或目标客户推断。
- 仍无法推断时，输出有限研究框架，并列明需要用户补充的目标法域。
- 不伪造目标国家，不把“海外”当成可检索法域。

## 5. 主题路由

| 主题 | 优先域名类型 | 说明 |
| --- | --- | --- |
| 法规原文 / 规则是否存在 | 法规库、政府公报、司法部、监管机构 | 用于决定性法律结论 |
| 公司设立 / 董事 / 企业注册 | 公司注册机关、投资主管机关、商事登记系统 | 用于主体设立和登记流程 |
| 外资准入 / 投资限制 | 投资主管机关、商务 / 投资部、投资政策数据库 | 用于市场进入、负面清单和审批 |
| 劳动 / 用工 / 移民 | 劳动主管机关、移民局、官方法规库 | 用于雇佣、工时、最低工资、签证 |
| 税务 / 发票 / VAT | 税务机关、财政部、官方法规库 | 用于税务注册、申报和税种确认 |
| 数据 / 隐私 / 网络安全 | 数据保护监管机构、官方法规库、权威指南 | 用于数据处理和跨境传输 |
| 仲裁 / 争议解决 | 仲裁机构、法院、司法机构 | 用于争议解决路径和程序 |
| 多法域比较 | ICLG、Chambers、Legal500、Lex Mundi、Lexology、官方来源核验 | 先搭框架，再回官方来源核关键点 |
| 动态追踪 | 最新官方公告、监管页面、日期敏感公开来源 | 区分现行规则、草案和快讯 |

## 5.1 紧凑来源包选择规则

本文件的来源地图来自共享涉外可信信源母库的压缩版。运行时只读取本 Skill 自带来源包，不依赖 `_shared`。

选择来源包时：

1. 先识别法域，再识别主题。
2. 每个法域先取 3-8 个与主题最相关的官方、监管、法院、企业注册、仲裁或高质量指南域名。
3. 主题涉及资本市场、土地、能源、劳动、数据、税务等专门领域时，优先加入对应主管机关或专业组织。
4. 来源包没有覆盖目标法域时，先寻找该国官方法规库、监管机构、法院、企业注册和仲裁入口，再使用高质量指南搭框架。
5. 新发现的官方来源可以使用，但必须在输出中标注“新发现官方来源，待纳入来源包复核”。

## 5.2 样板法域-主题来源包

以下来源包用于验证本 Skill 是否真正按“法域 -> 主题 -> 来源包”执行，而不是只做原则性说明。

| 场景 | 官方 / 监管来源 | 专业指南 / 实务来源 | 默认覆盖预期 | 使用限制 |
| --- | --- | --- | --- | --- |
| 中国香港资本市场 / 上市监管 | `legislation.gov.hk`、`sfc.hk`、`hkexnews.hk`、`legco.gov.hk`、`judiciary.hk` | 香港资本市场头部律所文章、高质量法律指南 | 强或中，取决于是否找到具体规则 / 指引页面 | 律所文章只解释交易结构和市场实践，不能替代上市规则、SFC 指引或香港法例 |
| 尼日利亚土地 / 外资投资路径 | `cac.gov.ng`、`nipc.gov.ng`、`cbn.gov.ng`、`firs.gov.ng` | `aluko-oyebode.com` 等本地强所文章、ICLG / Chambers 如有覆盖 | 中或弱，除非找到土地或投资限制的官方原文 | 如果只找到本地律所或指南，应标注“基于二手来源”，不得给确定法律意见 |
| 哈萨克斯坦能源 / 核能投资 | `zan.kz`、`adilet.zan.kz`、`gov.kz`、`invest.gov.kz`、`iaea.org` | 国际组织、能源投资指南、国际律所文章 | 中，找到当地法规原文时可升为强 | IAEA 可作为主题权威补充，但当地投资和许可规则仍需哈萨克斯坦官方来源支撑 |

新增法域或新主题时，按同一字段补入本文件，而不是让成品 Skill 运行时读取共享信源母库。

## 6. 域名限定搜索

内部执行规则：

1. 根据法域从本文件自带来源入口取 3-8 个最相关域名。
2. 根据主题筛选官方域名或高质量指南域名。
3. 按运行时工具 schema 表达“可信域名优先 / 域名限定 / 站内检索”等约束，不在 Skill 中写死具体参数名。
4. 若限定搜索无结果，先换同法域其他可信域名，再使用高质量法律指南。
5. 仍不足时开放搜索，但输出中必须降低结论强度。

注意：

- 不要把“限定域名无结果”写成“该规则不存在”。
- 域名可用性会随政府网站改版变化，需要在输出中保留检索限制。
- 本文件未覆盖的法域，先寻找目标国官方法规库、主管机关、法院、仲裁机构和企业注册入口，再使用高质量法律指南搭框架。

## 7. 中国大陆特殊处理

- 纯中国法主问题交给中国法律研究 Skill。
- 中国大陆来源在出海研究中只用于补充中国侧监管、条约、商务部国别指南、贸易救济、外汇、海关、条约等背景。
- 中国大陆法条、案例和国内合规决定性问题不由本 Skill 深挖。

## 8. 可信来源层级

| 层级 | 用户可见名称 | 典型来源 | 使用规则 |
| --- | --- | --- | --- |
| 高 | 各国官方来源 | 官方法规库、政府公报、监管机构、法院、仲裁机构、条约官网、官方 FAQ | 可支撑决定性结论 |
| 中 | 高质量法律指南 | ICLG、Chambers、Legal500、Lex Mundi、Lexology、专业机构指南 | 搭框架、做比较、辅助理解 |
| 中 | 专业实务解读 | 国际律所、本地强所、会计师事务所、专业机构文章 | 补充落地经验和常见坑点 |
| 低 | 媒体与市场信号 | 新闻、博客、行业快讯、社区讨论 | 只作动态线索 |
| 待确认 | 待人工核验 | 无可定位片段、版本不明、来源冲突 | 必须提示人工复核 |

## 8.1 覆盖状态

每轮研究应按实际检索结果表达覆盖状态：

| 状态 | 条件 | 输出要求 |
| --- | --- | --- |
| 强 | 有官方原文、监管 / 法院来源或法规库，并有可定位片段 | 可给出有依据的初步结论 |
| 中 | 主要来自高质量指南或律所实务，官方来源不足 | 标注基于二手来源，关键结论需官方核验 |
| 弱 | 只有零散开放法源、新闻、中文解读或不可完整访问来源 | 结论降级，建议当地律师或人工复核 |
| 未覆盖 | 未找到可定位来源 | 不挂引用编号，不伪装为已核验结论 |

## 9. 多法域比较规则

多法域比较必须先统一比较维度，例如：

- 是否需要本地主体。
- 是否需要审批、备案或许可。
- 核心义务。
- 时间要求。
- 处罚风险。
- 实务难点。
- 主管机关和办理入口。

执行要求：

- 每个法域按同一维度填充。
- 对关键结论回到该法域官方来源或高强度来源核验。
- 如果某个法域只找到二手指南，要明确降低该法域结论强度。

## 10. fallback 规则

| 失败情形 | 处理方式 |
| --- | --- |
| 官方域名无结果 | 改用同法域其他官方域名或监管机构页面 |
| 官方来源可访问性差 | 使用高质量法律指南搭框架，并标注官方核验缺口 |
| 高质量指南无覆盖 | 开放搜索找本地律所、会计师事务所或主管机关页面 |
| 只找到中文文章 | 用作 framing，不作决定性依据 |
| 只找到新闻或媒体 | 只作动态信号，结论标为待确认 |
| 来源冲突 | 比较效力层级、时间、适用范围；无法收口时标为不明确 |

## 11. 禁止路径

- 不要用搜索摘要直接写法律结论。
- 不要把高质量指南写成法律本身。
- 不要把一个国家的规则泛化到区域或其他国家。
- 不要用旧文章支撑最新规则。
- 不要把翻译文本当成无风险原文，关键术语应保留原文并解释。
