# 投资标的筛查 — MCP 路由与工具映射

---

## 何时读取本文件

- 需要调用企查查、元典或联网来源前。
- 需要控制 MCP 调用成本、顺序、fallback 或区分必需 / 可选工具时。

## 本文件影响什么决策

- 决定企业工商与风险数据、管理层画像、知产数据和法律法规 / 案例数据的工具分工。

## 不适用场景

- 不用于判断法律红旗本身；红旗规则见 `expert-method.md`。
- 不用于报告引用和输出措辞；输出规则见 `output-and-citation-rules.md`。

## 1. MCP 依赖配置

```yaml
mcp_dependencies:
  - provider: qichacha
    mcp_id: qcc-company
    server: 企业基座
    tools:
      - get_company_by_query
      - get_company_registration_info
      - verify_company_accuracy
      - get_shareholder_info
      - get_actual_controller
      - get_beneficial_owners
      - get_key_personnel
      - get_financial_data
    purpose: 企业识别、工商核验、股权穿透、实控人、UBO、管理层、财报
    required: true
    fallback: 无法识别企业时提示用户提供 USCC

  - provider: qichacha
    mcp_id: qcc-risk
    server: 风控大脑
    tools:
      - get_dishonest_info
      - get_judgment_debtor_info
      - get_high_consumption_restriction
      - get_exit_restriction
      - get_equity_freeze
      - get_equity_pledge_info
      - get_business_exception
      - get_serious_violation
      - get_administrative_penalty
      - get_tax_arrears_notice
      - get_tax_abnormal
    purpose: 全维风险扫描
    required: true
    fallback: 无

  - provider: qichacha
    mcp_id: qcc-executive
    server: 董监高画像
    tools:
      - get_personnel_dishonest
      - get_personnel_high_consumption_ban
      - get_personnel_judgment_debtor
      - get_personnel_exit_restriction
    purpose: 实控人和法代个人信用红线快扫
    required: false
    fallback: 仅使用 get_key_personnel 做基础管理层展示

  - provider: qichacha
    mcp_id: qcc-ipr
    server: 知产引擎
    tools:
      - get_patent_info
      - get_trademark_info
      - get_software_copyright_info
      - get_ipr_pledge
    purpose: 知产资产概览和出质检查
    required: false
    fallback: 报告中标注"知产数据未获取"

  - provider: qichacha
    mcp_id: qcc-operation
    server: 经营罗盘
    tools:
      - get_financing_records
      - get_recruitment_info
      - get_honor_info
    purpose: 融资记录、招聘活跃度、荣誉标签
    required: false
    fallback: 仅展示工商信息中可获取的融资数据

  - provider: qichacha
    mcp_id: qcc-history
    server: 历史存档
    tools:
      - get_historical_legal_rep
      - get_historical_registration
      - get_historical_shareholders
    purpose: 治理稳定性判断（历史法代变更、历史股东变迁）
    required: false
    fallback: 治理稳定性标注"历史数据未获取，无法判断"

  - provider: yuandian
    mcp_id: yuandian-law
    server: 法律法规
    tools:
      - yuandian_law_vector_search
      - yuandian_rh_fg_search
      - yuandian_rh_fg_detail
    purpose: 按需检索投资场景相关法规（对赌协议效力、股权代持、VIE 合规等）
    required: false
    fallback: 联网搜索公开法规解读
```

## 2. 调用顺序与成本控制

**第一轮（必选，约 8 次调用）：**
1. `get_company_by_query` → 企业识别
2. `get_company_registration_info` → 工商核验
3. `verify_company_accuracy` → 名称/USCC 校验
4. `get_shareholder_info` → 股东结构
5. `get_actual_controller` → 实控人
6. `get_beneficial_owners` → UBO
7. `get_dishonest_info` → 失信
8. `get_judgment_debtor_info` + `get_high_consumption_restriction` + `get_equity_freeze` + `get_business_exception` + `get_administrative_penalty` → 风险快扫

**第二轮（建议，约 5 次调用）：**
9. `get_personnel_dishonest` + `get_personnel_high_consumption_ban` + `get_personnel_judgment_debtor` + `get_personnel_exit_restriction` → 管理层红线（实控人）
10. `get_patent_info` + `get_trademark_info` + `get_software_copyright_info` + `get_ipr_pledge` → 知产概览

**第三轮（可选，按需）：**
11. `get_financing_records` → 融资历史
12. `get_historical_legal_rep` → 治理稳定性
13. 元典法规检索 → 投资场景法规

## 3. 用户可见来源命名

| 内部来源 | 用户可见名称 |
| --- | --- |
| `qcc-company` / `qcc-risk` / `qcc-executive` / `qcc-ipr` / `qcc-operation` / `qcc-history` | 企业工商与风险数据 |
| `yuandian-law` | 中国法律法规库 |
| 运行时可见联网搜索工具 | 联网公开来源 |
| `query_legato_ragflow` | 本次挂载资料 / 项目资料 |

用户可见输出中不得出现企查查、元典、MCP 等供应商名称或工具函数名。
