# 出海组织与用工模式 Skill 官方入口与核验范围

> 日期：2026-05-25  
> 目的：为 `legato-overseas-organization-workforce-triage` 提供目标国劳动、签证、工作许可、员工数据等规则的官方核验入口。  
> 重要边界：本文件只记录官方入口和检索范围，不直接固化具体法条结论。具体国家规则必须在运行时按用户事实和当前官方来源再次核验。

## 何时读取本文件

- 开始任何海外团队与用工模式初筛任务时。
- 需要核验目标国劳动、签证、工作许可、员工数据、EOR 或 payroll 相关规则时。

## 本文件影响什么决策

- 决定优先进入哪些目标国官方入口，以及官方入口不足时应如何降级。

## 不适用场景

- 不用于构造具体搜索 query；查询模板见 `search-templates.md`。
- 不用于输出引用和分流报告结构；输出规则见 `output-and-citation-rules.md`。

## 1. 使用原则

- 贾丽丽专家材料用于组织、岗位、用工模式、跨文化和服务承接方法。
- 目标国劳动法、签证、工作许可、解雇、试用期、员工数据等规则必须回到官方来源或高质量公开来源核验。
- 本 Skill 不输出最终法律意见；官方入口核验后仍可能需要当地劳动律师、移民律师、数据合规律师或 payroll 服务商复核。
- 如果官方来源返回为空、无法访问或语言不支持，输出中必须说明“外部核验受限”，并降级为初筛。

## 2. 首批法域入口

| 法域 | 劳动 / 雇佣官方入口 | 签证 / 工作许可入口 | 员工数据 / 隐私入口 | 当前状态 |
| --- | --- | --- | --- | --- |
| 德国 | `bmas.de`、`gesetze-im-internet.de`、`arbeitsagentur.de` | `make-it-in-germany.com`、`auswaertiges-amt.de`、`arbeitsagentur.de` | `bfdi.bund.de` | 本 Skill 自带入口；需按题试跑 |
| 越南 | `vbpl.vn`、`molisa.gov.vn`、`vnsw.gov.vn`、`hochiminh.mofcom.gov.cn` | `evisa.gov.vn`、`immigration.gov.vn`、相关劳动许可官方入口 | `mic.gov.vn`、`ais.gov.vn` 等需运行时确认 | 本 Skill 自带入口；劳动部域名需再核验可访问性 |
| 印度尼西亚 | `peraturan.go.id`、`jdihn.go.id`、`kemnaker.go.id` | `imigrasi.go.id`、`molina.imigrasi.go.id`、`oss.go.id` | `kominfo.go.id` | 本 Skill 自带入口；劳动和移民入口需补充试跑 |
| 泰国 | `ratchakitcha.soc.go.th`、`doe.go.th`、`labour.go.th` | `immigration.go.th`、`doe.go.th`、`boi.go.th` | `pdpc.or.th` | 本 Skill 自带入口；劳动 / 移民入口需补充试跑 |
| 英国 | `gov.uk`、`legislation.gov.uk`、`acas.org.uk` | `gov.uk` Skilled Worker / sponsor licence pages | `ico.org.uk` | 本 Skill 自带入口 |
| 法国 | `travail-emploi.gouv.fr`、`code.travail.gouv.fr`、`service-public.fr` | `france-visas.gouv.fr`、`service-public.fr`、`administration-etrangers-en-france.interieur.gouv.fr` | `cnil.fr` | 本 Skill 自带入口 |

## 3. 运行时检索建议

### 德国

- 劳动规则：`Germany labour law BMAS official`、`site:bmas.de Arbeitsrecht employment`、`site:gesetze-im-internet.de Kündigungsschutzgesetz`.
- 工作许可：`site:make-it-in-germany.com work visa China employees Germany`、`site:arbeitsagentur.de work permit Germany foreign workers`.
- 员工数据：`site:bfdi.bund.de employee data protection Germany GDPR`.

### 越南

- 劳动规则：`site:molisa.gov.vn labour code Vietnam foreign workers`、`site:vbpl.vn Vietnam labor code foreign workers`.
- 工作许可：`Vietnam work permit foreign employee official site:molisa.gov.vn`。
- 国别投资资料：`site:mofcom.gov.cn 越南 劳动法 外国人就业`.

### 印度尼西亚

- 劳动规则：`site:kemnaker.go.id foreign workers Indonesia employment regulation`、`site:peraturan.go.id tenaga kerja asing`.
- 移民：`site:imigrasi.go.id work visa foreign worker Indonesia`.
- 投资/许可：`site:oss.go.id foreign workers permit`.

### 泰国

- 劳动规则：`site:labour.go.th employment Thailand foreign worker`、`site:doe.go.th work permit Thailand foreigner`.
- 移民：`site:immigration.go.th work visa Thailand`.
- BOI 场景：`site:boi.go.th work permit foreign experts Thailand`.

### 英国

- 雇佣合同 / 工时：`site:gov.uk employment contract working hours`、`site:legislation.gov.uk Employment Rights Act`.
- 工作签证：`site:gov.uk skilled worker visa sponsor licence`.
- 员工数据：`site:ico.org.uk employment data protection`.

### 法国

- 雇佣合同 / 劳动法：`site:travail-emploi.gouv.fr contrat de travail`、`site:code.travail.gouv.fr contrat de travail`.
- 工作许可：`site:service-public.fr autorisation de travail salarié étranger`、`site:france-visas.gouv.fr salarié`.
- 员工数据：`site:cnil.fr travail RGPD collaborateurs`.

## 4. 不应固化为当前结论的内容

- 各国试用期长度、通知期、解雇期限、外籍员工比例、工作许可周期、社保缴纳义务。
- 各国是否允许商务签从事某类活动。
- 各国员工数据跨境的最终合法依据。
- EOR、payroll、劳务派遣或雇主代理模式在各国的合法性。

上述内容必须按具体国家、员工国籍、岗位、实体状态、合同关系、项目周期和当前官方规则重新核验。

## 5. 独立打包规则

本文件是本 Skill 的任务入口清单。运行时只依赖本 Skill 目录内文件，不依赖上级目录、兄弟目录或外部共享文件。

运行时建议：

1. 先判断目标法域。
2. 从本文件找劳动 / 签证 / 员工数据入口。
3. 如果本文件未覆盖目标法域，先寻找目标国官方法规库、劳动主管机关、移民机关、数据监管机关和政府办事指南。
4. 官方入口不足时，可用高质量律所或专业机构指南补框架，但结论强度必须降级。

## 6. 待补齐

| 缺口 | 影响 | 补齐方式 |
| --- | --- | --- |
| 越南劳动部、印尼劳动部、泰国劳动部官方页面可访问性未测试 | 运行时可能搜索失败 | 用产品联网工具试跑 |
| 各国 EOR/payroll 合法性和服务能力边界未整理 | 服务承接建议只能保持类型级，不做具体服务商推荐 | 后续服务生态数据库或专家补访 |
