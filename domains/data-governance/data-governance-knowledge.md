# Tổng hợp kiến thức Data Governance

> Nguồn tham khảo: [DAMA-DMBOK](https://www.damadmbok.org/), [Snowflake Data Governance](https://www.snowflake.com/en/fundamentals/data-governance/), [ICO UK GDPR Guide](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/)

---

## 1. Data Governance là gì?

Data Governance là tập hợp các chính sách, quy trình, vai trò và tiêu chuẩn nhằm quản lý dữ liệu như một tài sản chiến lược của tổ chức. Mục tiêu là đảm bảo dữ liệu chính xác, an toàn, tuân thủ quy định và sẵn sàng cho việc ra quyết định.

### Lợi ích chính

- Tăng data trust — người dùng tin tưởng dữ liệu để ra quyết định
- Giảm rủi ro compliance (GDPR, regulations)
- Cải thiện data quality toàn tổ chức
- Giảm duplicate effort và inconsistency
- Hỗ trợ self-service analytics an toàn

---

## 2. DAMA-DMBOK Framework

Nguồn: [DAMA-DMBOK](https://www.damadmbok.org/)

DAMA-DMBOK (Data Management Body of Knowledge) là framework chuẩn quốc tế cho data management, hiện đang phát triển phiên bản 3.0 (2026) bổ sung AI governance và cloud architectures.

### 11 Knowledge Areas

| # | Knowledge Area | Mô tả |
|---|---------------|--------|
| 1 | **Data Governance** | Chính sách, quy trình, trách nhiệm quản lý dữ liệu |
| 2 | **Data Architecture** | Thiết kế cấu trúc tổng thể cho hệ thống dữ liệu |
| 3 | **Data Modeling & Design** | Phát triển data models hỗ trợ business |
| 4 | **Data Storage & Operations** | Quản lý lưu trữ và vận hành dữ liệu |
| 5 | **Data Security** | Bảo mật, access control, encryption |
| 6 | **Data Integration & Interoperability** | Tích hợp dữ liệu giữa các hệ thống |
| 7 | **Document & Content Management** | Quản lý tài liệu và nội dung phi cấu trúc |
| 8 | **Reference & Master Data** | Quản lý dữ liệu tham chiếu và dữ liệu chủ |
| 9 | **Data Warehousing & BI** | Kho dữ liệu và business intelligence |
| 10 | **Metadata Management** | Quản lý metadata (technical, business, operational) |
| 11 | **Data Quality** | Đảm bảo chất lượng dữ liệu |

---

## 3. 7 Pillars of Data Governance

Nguồn: [Data Governance Pillars](https://murdio.com/insights/data-governance-pillars/)

1. **Data Stewardship** — Vai trò và trách nhiệm quản lý dữ liệu hàng ngày
2. **Data Quality** — Đo lường và cải thiện chất lượng dữ liệu
3. **Data Security & Privacy** — Bảo vệ dữ liệu nhạy cảm
4. **Data Architecture** — Cấu trúc và thiết kế hệ thống
5. **Data Analytics & Usage** — Đảm bảo dữ liệu được sử dụng hiệu quả
6. **Data Lifecycle Management** — Quản lý vòng đời dữ liệu
7. **Data Culture** — Xây dựng văn hóa data-driven

---

## 4. Vai trò trong Data Governance

### Data Owner

- Business leader chịu trách nhiệm cuối cùng cho data asset
- Quyết định ai được access, dưới điều kiện nào
- Phê duyệt policies và standards cho domain của mình

### Data Steward

- Duy trì data accuracy, consistency, quality
- Enforce policies hàng ngày
- Xử lý data issues và escalation
- Viết và maintain business definitions

### Data Custodian

- Technical expert quản lý hệ thống
- Implement security measures (encryption, access control)
- Đảm bảo data được lưu trữ và bảo vệ đúng cách
- Thực thi backup, recovery

### Data Governance Council

- Gồm senior leaders (CDO, CTO, heads of business units)
- Set policies, approve standards
- Allocate resources cho governance initiatives
- Giải quyết conflicts giữa các domains

### Tóm tắt phân biệt

| Vai trò | Trách nhiệm chính | Thuộc |
|---------|-------------------|-------|
| Owner | Quyết định "what" và "who" | Business |
| Steward | Thực thi "how" và monitor | Business + IT |
| Custodian | Implement technical controls | IT |

---

## 5. Data Quality Dimensions

Nguồn: [IBM Data Quality Dimensions](https://www.ibm.com/id-id/think/topics/data-quality-dimensions)

### 6 dimensions cốt lõi

| Dimension | Mô tả | Ví dụ kiểm tra |
|-----------|--------|----------------|
| **Accuracy** | Dữ liệu phản ánh đúng thực tế | Email có đúng format không? |
| **Completeness** | Không thiếu dữ liệu cần thiết | % records có đủ required fields |
| **Consistency** | Đồng nhất giữa các hệ thống | Customer name giống nhau ở CRM và DWH |
| **Timeliness** | Dữ liệu cập nhật kịp thời | Data freshness < 24h |
| **Validity** | Tuân thủ format và business rules | Date format đúng, status trong allowed values |
| **Uniqueness** | Không trùng lặp | Không có duplicate customer records |

### Dimensions mở rộng

- **Integrity** — Referential integrity giữa các bảng
- **Reliability** — Nguồn dữ liệu đáng tin cậy
- **Accessibility** — Dữ liệu dễ tìm và truy cập

### Data Quality Framework

```
1. Define    → Xác định quality rules và thresholds
2. Measure   → Đo lường hiện trạng (profiling)
3. Monitor   → Theo dõi liên tục (automated checks)
4. Improve   → Sửa lỗi và cải thiện quy trình
5. Report    → Báo cáo DQ metrics cho stakeholders
```

---

## 6. Data Lineage

Nguồn: [Snowflake Data Lineage](https://www.snowflake.com/en/fundamentals/data-lineage-provenance/)

### Định nghĩa

Data lineage theo dõi nguồn gốc, luồng di chuyển và biến đổi của dữ liệu từ source đến destination.

### Tại sao quan trọng?

- **Trust** — Biết data từ đâu đến → tin tưởng insights
- **Impact analysis** — Thay đổi source → biết downstream nào bị ảnh hưởng
- **Root cause analysis** — Dashboard sai → trace ngược tìm lỗi nhanh
- **Compliance** — Audit trail cho regulatory requirements
- **Data quality** — Phát hiện và sửa lỗi tại nguồn

### Các level lineage

| Level | Mô tả |
|-------|--------|
| Table-level | Bảng A → Bảng B |
| Column-level | Column X trong bảng A → Column Y trong bảng B |
| Row-level | Record cụ thể đi qua pipeline nào |

### Best Practices

1. Automate lineage capture (không rely vào manual documentation)
2. Integrate lineage với data catalog
3. Maintain column-level lineage cho critical data
4. Update lineage khi pipeline thay đổi
5. Dùng lineage trong change management process

### Tools

- dbt (built-in lineage qua DAG)
- OpenLineage (open standard)
- Atlan, Collibra, DataHub (enterprise)
- Apache Atlas (open-source)

---

## 7. Data Catalog

Nguồn: [Data Catalog Tools Comparison](https://www.basedash.com/blog/best-data-catalog-tools-compared-2026)

### Định nghĩa

Data catalog là hệ thống quản lý metadata, giúp người dùng tìm kiếm, hiểu và tin tưởng dữ liệu.

### Chức năng chính

- **Discovery** — Tìm kiếm data assets
- **Documentation** — Business definitions, descriptions
- **Lineage** — Theo dõi nguồn gốc dữ liệu
- **Access control** — Quản lý quyền truy cập
- **Data quality** — Hiển thị quality scores
- **Collaboration** — Comments, ratings, usage tracking

### So sánh tools phổ biến

| Tool | Đặc điểm | Phù hợp |
|------|-----------|---------|
| **Collibra** | Enterprise-grade, configurable workflows | Regulated industries (banking, healthcare) |
| **Atlan** | Modern UX, active metadata, AI-powered | Data teams muốn tốc độ triển khai |
| **DataHub** | Open-source (LinkedIn), extensible | Teams muốn customize, budget-conscious |
| **OpenMetadata** | Open-source, full-featured | Alternative cho DataHub |
| **Alation** | Strong search, behavioral analytics | Organizations cần adoption cao |
| **Microsoft Purview** | Integrated với Azure ecosystem | Azure-heavy organizations |

### Xu hướng 2024-2026

- AI-assisted discovery và metadata enrichment
- Convergence catalog + governance thành unified platform
- Integration sâu với modern data stack (dbt, Airflow)
- Automated data quality monitoring built-in

---

## 8. Master Data Management (MDM)

Nguồn: [Microsoft Purview MDM](https://learn.microsoft.com/en-us/purview/master-data-management)

### Định nghĩa

MDM là quy trình tạo và duy trì một bản ghi chính (golden record) cho các entity cốt lõi của tổ chức, đảm bảo tính nhất quán giữa tất cả hệ thống.

### Master Data Domains phổ biến

- **Customer** — Thông tin khách hàng
- **Product** — Danh mục sản phẩm
- **Supplier/Vendor** — Nhà cung cấp
- **Employee** — Nhân viên
- **Location** — Địa điểm, chi nhánh
- **Account** — Tài khoản

### Golden Record

Golden record là bản ghi duy nhất, chính xác nhất cho mỗi entity, được tạo bằng cách:

1. **Identify** — Tìm tất cả records liên quan đến cùng entity
2. **Match** — So khớp records từ nhiều sources
3. **Merge** — Gộp thành 1 record với survivorship rules
4. **Validate** — Kiểm tra chất lượng golden record
5. **Distribute** — Đồng bộ về các consuming systems

### Implementation Styles

| Style | Mô tả | Khi nào dùng |
|-------|--------|-------------|
| **Registry** | Không copy data, chỉ link references | Khi không muốn move data |
| **Consolidation** | Copy vào MDM hub, read-only | Reporting, analytics |
| **Coexistence** | MDM hub + source systems cùng update | Phức tạp nhưng flexible |
| **Transaction** | MDM hub là system of record | Full control, high effort |

---

## 9. Data Privacy & Compliance

### GDPR — 7 Principles

Nguồn: [ICO Guide to Data Protection Principles](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-protection-principles/)

| # | Principle | Mô tả |
|---|-----------|--------|
| 1 | **Lawfulness, fairness, transparency** | Xử lý hợp pháp, công bằng, minh bạch |
| 2 | **Purpose limitation** | Chỉ dùng cho mục đích đã khai báo |
| 3 | **Data minimisation** | Chỉ thu thập dữ liệu cần thiết |
| 4 | **Accuracy** | Dữ liệu phải chính xác, cập nhật |
| 5 | **Storage limitation** | Chỉ lưu trữ khi còn cần thiết |
| 6 | **Integrity & confidentiality** | Bảo mật, toàn vẹn dữ liệu |
| 7 | **Accountability** | Chứng minh được tuân thủ |

### Data Subject Rights (GDPR)

- Right to access
- Right to rectification
- Right to erasure ("right to be forgotten")
- Right to restrict processing
- Right to data portability
- Right to object

### Governance cho Compliance

- **Data classification** — Phân loại dữ liệu (public, internal, confidential, restricted)
- **Data retention policies** — Quy định thời gian lưu trữ
- **Access controls** — RBAC, least privilege principle
- **Audit logging** — Ghi lại mọi truy cập và thay đổi
- **Data masking/anonymization** — Ẩn PII khi không cần thiết
- **Consent management** — Quản lý đồng ý của data subjects

---

## 10. Data Governance Maturity Model

### 5 Levels

| Level | Tên | Đặc điểm |
|-------|-----|-----------|
| 1 | **Initial** | Không có governance formal, ad-hoc |
| 2 | **Managed** | Một số policies, roles được define |
| 3 | **Defined** | Framework rõ ràng, processes documented |
| 4 | **Measured** | KPIs, metrics, continuous monitoring |
| 5 | **Optimized** | Automated, predictive, culture-driven |

### KPIs cho Data Governance

- Data quality score (% records pass quality checks)
- Data catalog coverage (% assets documented)
- Policy compliance rate
- Time to resolve data issues
- Data literacy adoption rate
- Number of data incidents

---

## 11. Implementation Roadmap

### Phase 1: Foundation (0-3 tháng)

- Define governance vision và objectives
- Identify executive sponsor
- Establish governance council
- Assess current state (maturity assessment)
- Prioritize critical data domains

### Phase 2: Framework (3-6 tháng)

- Define roles (owners, stewards, custodians)
- Create data policies và standards
- Implement data catalog (start small)
- Define data quality rules cho priority domains
- Set up communication channels

### Phase 3: Operationalize (6-12 tháng)

- Automate data quality monitoring
- Implement data lineage
- Roll out training programs
- Establish data quality SLAs
- Integrate governance vào development workflow

### Phase 4: Scale & Optimize (12+ tháng)

- Expand to all data domains
- Advanced automation (AI-assisted)
- Measure ROI of governance
- Continuous improvement cycle
- Build data culture organization-wide

---

## 12. Tools & Technology Stack

### Governance & Catalog

| Category | Tools |
|----------|-------|
| Enterprise Catalog | Collibra, Alation, Informatica |
| Modern Catalog | Atlan, DataHub, OpenMetadata |
| Cloud-native | Microsoft Purview, AWS Glue Catalog, Google Dataplex |

### Data Quality

| Category | Tools |
|----------|-------|
| Enterprise | Informatica DQ, Talend DQ |
| Modern/Open-source | Great Expectations, Soda, dbt tests |
| Monitoring | Monte Carlo, Bigeye, Elementary |

### Data Lineage

| Category | Tools |
|----------|-------|
| Standard | OpenLineage |
| Built-in | dbt (DAG), Airflow |
| Platform | Atlan, Collibra, DataHub |

### Privacy & Security

| Category | Tools |
|----------|-------|
| Data masking | Delphix, Informatica |
| Access control | Apache Ranger, cloud IAM |
| Classification | Microsoft Purview, BigID |

---

## Tài liệu tham khảo

- [DAMA-DMBOK Framework](https://www.damadmbok.org/)
- [Snowflake Data Governance Guide](https://www.snowflake.com/en/fundamentals/data-governance/)
- [IBM Data Quality Dimensions](https://www.ibm.com/id-id/think/topics/data-quality-dimensions)
- [ICO GDPR Principles](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-protection-principles/)
- [Data Governance Roles](https://murdio.com/insights/data-governance-roles/)
- [Data Lineage Best Practices](https://www.snowflake.com/en/fundamentals/data-lineage-provenance/)
- [State of Analytics Engineering 2024](https://www.getdbt.com/resources/state-of-analytics-engineering-2024)

*Content was rephrased for compliance with licensing restrictions.*
