# Data Vault 2.0 - Tổng hợp kiến thức

> Nguồn: "Building a Scalable Data Warehouse with Data Vault 2.0" - Daniel Linstedt & Michael Olschimke (2016)

## 1. Tổng quan Data Vault 2.0

Data Vault 2.0 là một **System of Business Intelligence** (tên đầy đủ: Common Foundational Warehouse Architecture) bao gồm 4 trụ cột:

| Trụ cột | Mô tả |
|---------|-------|
| **Modeling** | Mô hình dữ liệu dựa trên Hub, Link, Satellite - tối ưu cho performance và scalability |
| **Methodology** | Áp dụng Scrum/Agile với sprint 2-3 tuần, kết hợp CMMI, Six Sigma, TQM |
| **Architecture** | Hỗ trợ NoSQL, Big Data, real-time và unstructured data |
| **Implementation** | Pattern-based, automation, code generation (CMMI Level 5) |

### Lịch sử
- Được phát minh bởi **Dan Linstedt** từ những năm 1990 tại Department of Defense (Mỹ)
- Data Vault 1.0 tập trung vào modeling
- Data Vault 2.0 mở rộng thành hệ thống hoàn chỉnh (model + methodology + architecture + implementation)
- Hệ thống gốc xử lý hơn **15 petabytes** dữ liệu

### Nguyên tắc cốt lõi
- **Single Version of Facts**: Lưu trữ tất cả raw data, mọi lúc (Raw Data Vault)
- **Single Version of Truth**: Cung cấp dữ liệu đã tích hợp, cleansed cho business (Information Mart)
- **Auditability**: Mọi dữ liệu đều có thể truy vết nguồn gốc và thời điểm load
- **Agility**: Mô hình dễ mở rộng, không phá vỡ cấu trúc hiện có

---

## 2. Kiến trúc Data Vault 2.0

### Các layer chính

```
Source Systems → Staging Area → Raw Data Vault → Business Vault → Information Mart → Business Users
```

| Layer | Vai trò |
|-------|---------|
| **Staging Area** | Copy nguyên bản dữ liệu từ source, không transform |
| **Raw Data Vault** | Lưu trữ raw data theo mô hình Hub/Link/Satellite, tích hợp bằng business key |
| **Business Vault** | Áp dụng business rules lên raw data, có thể drop & regenerate |
| **Information Mart** | Dimensional model (star schema) phục vụ business users |

### Các thành phần mở rộng

- **Metrics Vault**: Lưu trữ metadata và KPIs về hệ thống DWH
- **Error Mart**: Quản lý và báo cáo lỗi data quality
- **Operational Vault**: Cho phép operational systems đọc/ghi trực tiếp vào DWH (real-time, MDM)
- **Managed Self-Service BI**: Business users tự tạo reports từ Raw/Business Vault

### So sánh với kiến trúc truyền thống

| Đặc điểm | Kimball (2-layer) | Inmon (3-layer) | Data Vault 2.0 |
|-----------|-------------------|-----------------|----------------|
| Staging → Target | Dimensional model | 3NF ODS → Dimensional | Hub/Link/Sat → Business Vault → Dimensional |
| Flexibility | Thấp (phải reload từ staging) | Trung bình | Cao (chỉ thêm, không sửa) |
| Auditability | Hạn chế | Trung bình | Đầy đủ |
| Scalability | Hạn chế | Trung bình | Cao (MPP, NoSQL ready) |

---

## 3. Data Vault Modeling

### 3 Entity Types cơ bản

Data Vault model lấy cảm hứng từ **scale-free networks** (mạng lưới phi tỷ lệ) trong tự nhiên - tương tự hệ thống hàng không với airports (hubs) và flight connections (links).

### 3.1. Hub (Trung tâm)

> Hub lưu trữ **business keys** - các khóa mà business sử dụng để nhận diện business objects.

**Cấu trúc bắt buộc:**

| Attribute | Mô tả |
|-----------|-------|
| **Hash Key** (PK) | MD5/SHA-1 hash của business key, dùng làm primary key |
| **Business Key(s)** | Khóa nghiệp vụ (customer number, invoice number, VIN...) |
| **Load Date** | Thời điểm business key lần đầu xuất hiện trong DWH |
| **Record Source** | Nguồn dữ liệu (chi tiết nhất có thể, vd: "SAP.FINANCE.GL") |

**Attribute tùy chọn:**
- **Last Seen Date**: Dùng khi source chỉ cung cấp full dump (không có CDC)

**Quy tắc quan trọng:**
- Mỗi hub chứa **một loại** business key duy nhất
- Business key phải có cùng **semantic granularity** (vd: individual ≠ corporation)
- Composite keys (smart keys) được giữ nguyên trong cùng một hub
- Hash key thay thế sequence number từ Data Vault 1.0 (hỗ trợ NoSQL, cross-platform)

**Ví dụ business keys:**
- Customer numbers, Product numbers (UPC, EAN, ISBN)
- Vehicle Identification Numbers (VIN) - composite key
- Invoice numbers, Account numbers
- Employee badge numbers

### 3.2. Link (Liên kết)

> Link mô hình hóa **relationships** giữa business objects (transactions, associations, hierarchies).

**Cấu trúc bắt buộc:**

| Attribute | Mô tả |
|-----------|-------|
| **Hash Key** (PK) | Hash của tổ hợp tất cả business keys được liên kết |
| **Hub Hash Keys** (FK) | References đến các hub được kết nối (≥ 2) |
| **Load Date** | Thời điểm relationship được load |
| **Record Source** | Nguồn dữ liệu |

**Attribute tùy chọn:**
- **Dependent Child Key**: Degenerate field (vd: line-item number trên invoice)
- **Last Seen Date**

**Đặc điểm quan trọng:**
- Luôn là **many-to-many** relationship (có thể biểu diễn 1:1, 1:m, m:n)
- **Không có end-date** - link chỉ ghi nhận relationship đã/đang tồn tại
- Không chứa context/temporal information (đó là việc của satellite)
- Granularity = số lượng hubs được kết nối (càng nhiều hub → grain càng mịn)

**Tại sao chỉ dùng many-to-many?**
- Khi business rule thay đổi (1:m → m:n), không cần re-engineer model
- ETL loading routines không bị ảnh hưởng
- Zero re-engineering effort khi relationship type thay đổi

**Unit-of-Work**: Không được tách (normalize) một link thành nhiều links nhỏ hơn nếu điều đó phá vỡ tính toàn vẹn dữ liệu (multivalued dependencies).

### 3.3. Satellite (Vệ tinh)

> Satellite lưu trữ **descriptive attributes** (context) của business objects hoặc relationships, bao gồm lịch sử thay đổi.

**Cấu trúc bắt buộc:**

| Attribute | Mô tả |
|-----------|-------|
| **Parent Hash Key** (PK, FK) | Reference đến hub hoặc link cha |
| **Load Date** (PK) | Thời điểm thay đổi được ghi nhận |
| **Load End Date** | Thời điểm record bị thay thế bởi version mới |
| **Record Source** | Nguồn dữ liệu |
| **Descriptive Attributes** | Các thuộc tính mô tả |

**Attribute tùy chọn:**
- **Extract Date**: Thời điểm dữ liệu được extract từ source
- **Hash Diff**: Hash của tất cả descriptive attributes (tối ưu delta detection)

**Quy tắc quan trọng:**
- Mỗi satellite chỉ phụ thuộc vào **MỘT** hub hoặc link (không snowflake)
- **Không được UPDATE** dữ liệu trong satellite (trừ Load End Date)
- Chỉ insert khi có **thay đổi** (delta-driven, tương tự SCD Type 2)
- Data types phải **gần nhất** với source system

**Best practices tách satellite:**

1. **Tách theo Source System**: Mỗi source → satellite riêng
   - Cho phép thêm source mới mà không thay đổi satellite hiện có
   - Tối đa hóa load parallelism
   - Giữ audit trail rõ ràng

2. **Tách theo Rate of Change**: Attributes thay đổi thường xuyên → satellite riêng
   - Giảm storage waste (không duplicate unchanged attributes)
   - Ví dụ: thông tin tĩnh (số ghế máy bay) vs. thông tin động (tổng km bay)

---

## 4. Intermediate Data Vault Modeling

### 4.1. Hub Applications

- **Multi-Business Key Hub**: Hub chứa nhiều business keys từ nhiều source systems cho cùng một business object

### 4.2. Link Applications

| Loại Link | Mô tả | Thuộc layer |
|-----------|-------|-------------|
| **Same-As Link** | Liên kết các business keys đại diện cùng một entity (deduplication) | Business Vault |
| **Hierarchical Link** | Self-referencing link (parent-child trong cùng hub) | Raw Data Vault |
| **Non-Historized Link** | Link cho transactions không thay đổi (vd: invoice) | Raw Data Vault |
| **Nondescriptive Link** | Link không có satellite (chỉ ghi nhận relationship tồn tại) | Raw Data Vault |
| **Computed Aggregate Link** | Link được tính toán từ raw data (GROUP BY) | Business Vault |
| **Exploration Link** | Link tạo ra để phân tích relationship không có trong source | Business Vault |

**Non-Historized Link (Transactional Link):**
- Dùng cho transactions không bao giờ thay đổi (invoice, payment)
- Hash key = hash(business keys + transaction identifier)
- Có 2 cách implement:
  1. Standard link + satellite không có LoadEndDate (recommended)
  2. Attributes trực tiếp trong link (chỉ khi cần performance cực cao)

### 4.3. Satellite Applications

| Loại Satellite | Mô tả |
|----------------|-------|
| **Multi-Active Satellite** | Nhiều records active cùng lúc cho 1 parent (vd: nhiều phone numbers) |
| **Status Tracking Satellite** | Lưu audit trail / CDC operations (CRUD) |
| **Effectivity Satellite** | Track begin/end dates của relationship (trên link) |
| **Record Tracking Satellite** | Track sự xuất hiện/biến mất của keys trong source systems |
| **Overloaded Satellite** | Satellite chứa data từ nhiều sources (KHÔNG recommended) |

---

## 5. Advanced Data Vault Modeling

### 5.1. Point-in-Time (PIT) Tables

- **Mục đích**: Tối ưu query performance khi join nhiều satellites
- **Cách hoạt động**: Pre-join các satellite hash keys tại mỗi thời điểm thay đổi
- **Đặc điểm**: Có thể drop & regenerate, thuộc Business Vault
- **Khi nào dùng**: Khi hub/link có nhiều satellites và queries cần join tất cả

### 5.2. Bridge Tables

- **Mục đích**: Pre-join nhiều links và hubs để tối ưu query
- **Tương tự**: Denormalized view của một phần Data Vault model
- **Đặc điểm**: Có thể drop & regenerate, thuộc Business Vault

### 5.3. Reference Tables

- **Mục đích**: Lưu trữ reference data (code tables, lookup values)
- **Đặc điểm**: Không có hash key, shared across toàn bộ model
- **Ví dụ**: Country codes, currency codes, status codes

---

## 6. Loading Patterns

### Staging Area
- Copy nguyên bản từ source (không transform)
- Hash keys được tính tại staging
- Load Date và Record Source được gán tại staging
- Truncate sau khi load xong vào Data Vault

### Loading Rules

| Entity | Rule |
|--------|------|
| Hub | INSERT nếu business key chưa tồn tại (lookup bằng hash key) |
| Link | INSERT nếu combination of hash keys chưa tồn tại |
| Satellite | INSERT nếu có thay đổi (so sánh hash diff hoặc từng attribute) |

### Hashing Best Practices
- Dùng **MD5** (recommended) hoặc SHA-1
- Hash trên **business key** (cho hub hash key)
- Hash trên **tổ hợp business keys** (cho link hash key)
- Hash trên **tất cả descriptive attributes** (cho hash diff trong satellite)
- Chuẩn hóa input trước khi hash: UPPER, TRIM, handle NULL consistently

---

## 7. Business Vault

### Đặc điểm
- Tuân theo Data Vault modeling rules nhưng chứa **business-rule transformed data**
- Có thể **drop & regenerate** từ Raw Data Vault bất kỳ lúc nào
- Là layer trung gian giữa Raw Data Vault và Information Mart
- Giảm complexity khi load Information Mart

### Các entity types trong Business Vault
- Same-As Links (deduplication/consolidation)
- Computed Aggregate Links
- Exploration Links
- Computed Satellites (derived/calculated attributes)
- PIT Tables
- Bridge Tables

---

## 8. Information Mart (Dimensional Layer)

### Vai trò
- Phục vụ trực tiếp cho business users
- Mô hình Star Schema (facts + dimensions)
- Áp dụng business rules phức tạp (soft rules)
- Source từ Business Vault và/hoặc Raw Data Vault

### Loading strategies
- **Materialized**: Physical tables, scheduled refresh
- **Virtualized**: Views trên PIT/Bridge tables (real-time nhưng performance thấp hơn)

---

## 9. Data Quality trong Data Vault

### Nguyên tắc
- Raw Data Vault lưu **tất cả** data kể cả dirty data (single version of facts)
- Data cleansing xảy ra ở **Business Vault** hoặc **Information Mart** layer
- Errors được track trong **Error Mart**
- Business rules KHÔNG được áp dụng trong Raw Data Vault

### Phân loại Business Rules

| Loại | Mô tả | Áp dụng tại |
|------|--------|-------------|
| **Hard Rules** | Technical rules (data type casting, deduplication, formatting) | Staging → Raw Data Vault |
| **Soft Rules** | Business logic (calculations, derivations, interpretations) | Business Vault → Information Mart |

---

## 10. Methodology - Agile Data Warehousing

### Sprint Structure
- **2-3 tuần** per sprint
- Mini-waterfall trong mỗi sprint (plan → design → develop → test → deploy)
- Deliverables có thể đưa vào production sau mỗi sprint

### Release Stages
1. **Alpha**: Chỉ IT team + Technical Business Analysts test
2. **Beta**: Thêm Business Sponsor + selected business users
3. **Gamma**: Production release cho tất cả users

### Key Roles
- Business Sponsor
- Technical Business Analyst (cầu nối business-IT)
- Project Manager
- Data Architect / Information Architect
- ETL Developer
- Report Developer
- Metadata Manager
- Change Manager

---

## 11. Scalability & Performance

### Tại sao Data Vault scale tốt?

1. **Parallel Loading**: Mỗi hub, link, satellite load độc lập → maximize parallelism
2. **Insert-Only**: Không update (trừ Load End Date) → không lock contention
3. **Narrow Tables**: Hub/Link/Satellite đều narrow → nhiều rows per page → I/O hiệu quả
4. **Hash Keys**: Fixed-length keys → join performance ổn định
5. **Additive Model**: Thêm hub/link/satellite mới không ảnh hưởng existing structures
6. **MPP Ready**: Hash-based distribution phù hợp với MPP databases

### Anti-patterns cần tránh
- Overloaded satellites (nhiều sources trong 1 satellite)
- Quá nhiều attributes trong 1 satellite (wide tables)
- Áp dụng business rules trong Raw Data Vault
- End-dating links
- Modifying existing link structures (thêm/bớt hub references)

---

## 12. Master Data Management (MDM)

- Data Vault tích hợp tốt với MDM systems (vd: Microsoft MDS)
- Same-As Links dùng để consolidate duplicate business keys
- MDM có thể đọc/ghi trực tiếp vào Operational Vault
- Business keys từ MDM được load như bất kỳ source system nào khác

---

## 13. Metadata Management

### Các thành phần
- **Meta Mart**: Lưu trữ technical metadata (table definitions, column mappings)
- **Metrics Vault**: Track operational metrics (load times, row counts, errors)
- **Metrics Mart**: Reporting trên operational metrics
- **Error Mart**: Quản lý data quality errors

---

## 14. So sánh Data Vault vs. Dimensional Modeling

| Tiêu chí | Data Vault | Dimensional (Kimball) |
|-----------|-----------|----------------------|
| Mục đích chính | Integration & storage | Presentation & analysis |
| Flexibility | Rất cao (additive) | Thấp (redesign khi thay đổi) |
| Auditability | Đầy đủ | Hạn chế |
| Query complexity | Cao (nhiều joins) | Thấp (star schema) |
| End-user friendly | Không (cần Information Mart) | Có |
| Historical tracking | Tự động (satellites) | Manual (SCD types) |
| Loading speed | Nhanh (parallel, insert-only) | Chậm hơn (lookups, updates) |
| Phù hợp cho | Enterprise DWH layer | Reporting/Analytics layer |

**Kết luận**: Data Vault và Dimensional Modeling **bổ sung** cho nhau - Data Vault làm integration layer, Dimensional Model làm presentation layer.

---

## 15. Khi nào nên dùng Data Vault?

✅ **Nên dùng khi:**
- Nhiều source systems cần tích hợp
- Business requirements thay đổi thường xuyên
- Cần auditability và compliance
- Data volume lớn, cần scalability
- Team cần agility (parallel development)
- Cần lưu trữ full history

❌ **Không cần thiết khi:**
- Chỉ có 1-2 source systems đơn giản
- Không có yêu cầu audit/compliance
- Project nhỏ, timeline ngắn
- Team không có kinh nghiệm Data Vault (learning curve cao)

---

## Tài liệu tham khảo

- Linstedt, D. & Olschimke, M. (2016). *Building a Scalable Data Warehouse with Data Vault 2.0*. Morgan Kaufmann.
- Data Vault Alliance: https://datavaultalliance.com
- Dan Linstedt's training materials
