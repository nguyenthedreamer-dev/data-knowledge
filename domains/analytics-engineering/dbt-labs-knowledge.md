# Tổng hợp kiến thức quan trọng từ dbt Labs

> Nguồn tham khảo chính: [dbt Best Practices](https://docs.getdbt.com/guides/best-practices), [Analytics Engineering Guide](https://www.getdbt.com/blog/analytics-engineering-six-best-practices)

---

## 1. Analytics Engineering là gì?

Analytics engineering áp dụng các nguyên tắc software engineering vào quá trình transform dữ liệu — cleaning, modeling, testing, documenting — để đảm bảo dữ liệu sẵn sàng cho phân tích.

### Lợi ích chính

- Tạo single source of truth cho business metrics
- Giảm duplicate work giữa các team
- Đảm bảo data consistency và reliability
- Tăng tốc từ raw data đến insights
- Cho phép self-service analytics

---

## 2. Cấu trúc dbt Project (How We Structure)

Nguồn: [How we structure our dbt projects](https://docs.getdbt.com/guides/best-practices/how-we-structure/1-guide-overview)

### Nguyên tắc nền tảng

Dữ liệu di chuyển theo arc từ **source-conformed** (định hình bởi hệ thống bên ngoài) sang **business-conformed** (định hình bởi nhu cầu và định nghĩa nội bộ).

### 3 layers chính

```
models/
├── staging/          # Source-conformed, atomic building blocks
├── intermediate/     # Logic phức tạp, chuẩn bị cho marts
└── marts/            # Business-conformed, sẵn sàng cho end-user
```

### Staging Layer

- 1:1 mapping với source tables
- Chỉ thực hiện: rename, cast, basic cleaning
- Naming convention: `stg_<source>__<entity>.sql`
- Materialization: `view`
- Không chứa joins hay business logic

### Intermediate Layer

- Xử lý logic phức tạp, joins giữa staging models
- Naming convention: `int_<entity>_<verb>.sql`
- Materialization: `ephemeral` hoặc `view`
- Ví dụ: `int_orders_pivoted.sql`, `int_payments_aggregated.sql`

### Marts Layer

- Business-conformed, wide và denormalized
- Chia theo business domain: `marts/finance/`, `marts/marketing/`
- Naming convention: `dim_<entity>.sql`, `fct_<entity>.sql`
- Materialization: `table` hoặc `incremental`
- Đây là nơi end-users query trực tiếp

---

## 3. Naming Conventions

| Layer | Prefix | Ví dụ |
|-------|--------|-------|
| Staging | `stg_` | `stg_stripe__payments` |
| Intermediate | `int_` | `int_payments_pivoted_to_orders` |
| Dimensions | `dim_` | `dim_customers` |
| Facts | `fct_` | `fct_orders` |

### Quy tắc chung

- Tên model = tên bảng trong warehouse
- Dùng snake_case
- Plural cho tên entity (customers, orders)
- Source prefix dùng double underscore: `stg_<source>__<entity>`

---

## 4. Testing

Nguồn: [dbt Testing docs](https://docs.getdbt.com/docs/building-a-dbt-project/tests/)

### Generic Tests (built-in)

4 tests có sẵn:
- `not_null` — column không được null
- `unique` — giá trị không trùng lặp
- `accepted_values` — giá trị nằm trong danh sách cho phép
- `relationships` — referential integrity

```yaml
models:
  - name: stg_orders
    columns:
      - name: order_id
        tests:
          - not_null
          - unique
      - name: status
        tests:
          - accepted_values:
              values: ['placed', 'shipped', 'completed', 'returned']
```

### Singular Tests

- Custom SQL queries trong folder `tests/`
- Query trả về rows = test FAIL
- Query trả về 0 rows = test PASS

### Unit Tests (dbt 1.8+)

- Test transformation logic trước khi chạy production
- Validate business logic ở model level

### Best Practices

- Mọi model nên có ít nhất `not_null` + `unique` trên primary key
- Test relationships giữa các layers
- Dùng packages như `dbt_expectations` cho advanced tests
- Chạy tests trong CI/CD pipeline

---

## 5. Documentation

### Inline documentation trong schema.yml

```yaml
models:
  - name: dim_customers
    description: "One record per customer with lifetime metrics"
    columns:
      - name: customer_id
        description: "Primary key - unique identifier for each customer"
      - name: lifetime_value
        description: "Total revenue from this customer across all orders"
```

### dbt Docs

- `dbt docs generate` — tạo documentation site
- `dbt docs serve` — serve locally
- Bao gồm DAG visualization
- Auto-generated từ schema.yml + markdown files

---

## 6. Semantic Layer & MetricFlow

Nguồn: [dbt Semantic Layer](https://docs.getdbt.com/docs/use-dbt-semantic-layer/dbt-sl)

### Khái niệm

Semantic Layer cho phép định nghĩa metrics một lần trong dbt project (YAML), sau đó serve nhất quán cho mọi downstream tool (BI, notebooks, AI agents).

### MetricFlow

- Engine xử lý metric definitions
- Xây dựng semantic graph từ YAML configs
- Tự động generate SQL queries cho metrics
- Hỗ trợ dimensions, entities, measures

### Cấu trúc

```yaml
semantic_models:
  - name: orders
    defaults:
      agg_time_dimension: order_date
    entities:
      - name: order_id
        type: primary
      - name: customer_id
        type: foreign
    measures:
      - name: order_total
        agg: sum
        expr: amount
    dimensions:
      - name: order_date
        type: time

metrics:
  - name: revenue
    type: simple
    type_params:
      measure: order_total
```

### Lợi ích

- Single source of truth cho metrics
- Không duplicate logic giữa BI tools
- Version-controlled, testable
- Governed access

---

## 7. Materializations

| Type | Khi nào dùng |
|------|-------------|
| `view` | Staging models, lightweight transforms |
| `table` | Marts, models được query thường xuyên |
| `incremental` | Large fact tables, append-heavy data |
| `ephemeral` | Intermediate CTEs, không cần persist |

### Incremental Best Practices

- Luôn define `unique_key`
- Dùng `on_schema_change: sync_all_columns`
- Có strategy cho late-arriving data
- Test với `--full-refresh` định kỳ

---

## 8. Sources & Freshness

```yaml
sources:
  - name: stripe
    database: raw
    schema: stripe
    freshness:
      warn_after: {count: 12, period: hour}
      error_after: {count: 24, period: hour}
    loaded_at_field: _loaded_at
    tables:
      - name: payments
      - name: customers
```

- `dbt source freshness` — kiểm tra data có fresh không
- Alert khi source data bị stale

---

## 9. CI/CD cho dbt

### Workflow chuẩn

1. Developer tạo branch, viết/sửa models
2. PR triggers CI job: `dbt build --select state:modified+`
3. Chỉ build models bị thay đổi + downstream
4. Tests pass → merge
5. Production job chạy full build theo schedule

### Slim CI

- So sánh với production manifest (`state:modified`)
- Chỉ build những gì thay đổi
- Tiết kiệm compute cost

---

## 10. dbt Mesh (Multi-project)

Cho organizations lớn:

- Chia dbt project thành nhiều projects nhỏ
- Mỗi team own 1 project
- Cross-project references qua `ref` với project name
- Governance: control ai được access model nào
- Phù hợp với Data Mesh philosophy

---

## 11. Six Best Practices (từ dbt Labs)

Nguồn: [Analytics Engineering Six Best Practices](https://www.getdbt.com/blog/analytics-engineering-six-best-practices)

1. **Version control everything** — Mọi transformation logic trong Git
2. **Test your data** — Automated tests cho mọi model
3. **Document as you go** — Documentation là phần của workflow, không phải afterthought
4. **Build modularly** — DRY principle, reusable models
5. **Design for the consumer** — Marts phục vụ business users, không phục vụ engineers
6. **Automate workflows** — CI/CD, scheduled runs, alerting

---

## 12. Packages hữu ích

| Package | Mục đích |
|---------|----------|
| `dbt_utils` | Macros tiện ích (surrogate_key, pivot, union) |
| `dbt_expectations` | Advanced data testing |
| `dbt_date` | Date dimension generation |
| `dbt_project_evaluator` | Audit project structure |
| `codegen` | Generate source/model YAML |
| `audit_helper` | Compare model outputs |

---

## Tài liệu tham khảo

- [How we structure our dbt projects](https://docs.getdbt.com/guides/best-practices/how-we-structure/1-guide-overview)
- [dbt Semantic Layer](https://docs.getdbt.com/docs/use-dbt-semantic-layer/dbt-sl)
- [Analytics Engineering Best Practices](https://www.getdbt.com/blog/analytics-engineering-six-best-practices)
- [dbt Testing](https://docs.getdbt.com/docs/building-a-dbt-project/tests/)
- [State of Analytics Engineering 2024](https://www.getdbt.com/resources/state-of-analytics-engineering-2024)
- [How to Build a Mature dbt Project](https://docs.getdbt.com/blog/how-to-build-a-mature-dbt-project-from-scratch)

*Content was rephrased for compliance with licensing restrictions.*
