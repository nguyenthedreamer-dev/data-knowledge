# Tóm tắt: DQOps eBook - Hướng dẫn từng bước cải thiện Data Quality

## Tổng quan

DQOps là nền tảng data quality mã nguồn mở, bao trùm toàn bộ vòng đời dữ liệu: từ profiling data sources mới đến tự động hóa hoàn toàn việc giám sát data quality. Nền tảng hỗ trợ nhiều giao diện: UI, Python code, REST API, command line, YAML files.

---

## Các khái niệm cốt lõi

### Data Quality Dimensions (Các chiều đo lường chất lượng dữ liệu)
| Dimension | Định nghĩa | Ví dụ vấn đề |
|-----------|------------|---------------|
| **Accuracy** | Mức độ gần đúng của dữ liệu so với giá trị thực | Dữ liệu không đáng tin cậy cho BI, forecasting |
| **Completeness** | Mức độ đầy đủ của các bản ghi/giá trị | Thiếu giá trị, thiếu hàng |
| **Consistency** | Mức độ nhất quán giữa các bản ghi/file/thời điểm | Số hàng không nhất quán, thông tin mâu thuẫn |
| **Reasonableness** | Mức độ hợp lý của data pattern | Giá trị không hợp lý |
| **Timeliness** | Mức độ cập nhật kịp thời | Dữ liệu không up-to-date |
| **Uniqueness** | Mức độ không trùng lặp | Dữ liệu bị duplicate |
| **Validity** | Mức độ tuân thủ business rules (format, type, range) | Sai format dữ liệu |

### Các bên liên quan (Stakeholders)
- **Data Owner (DO)**: Hiểu mục đích dữ liệu, data model, business processes; xác định bảng cần kiểm tra và ngưỡng cảnh báo
- **Data Producer**: Chủ sở hữu platform nguồn cung cấp dữ liệu
- **Data Engineering Team (DE)**: Thu thập, quản lý, chuyển đổi raw data; xây dựng và bảo trì data pipelines
- **Data Quality Team (DQ)**: Import metadata, cấu hình data quality checks, giám sát issues

### Kiến trúc DQOps Check
- **Sensor**: Template SQL query thu thập metrics (row count, % null, data freshness...)
- **Rule**: Tập điều kiện so sánh sensor readout với threshold
- **Check = Sensor + Rule**: Kết quả là passed hoặc failed
- **KPI**: Tỷ lệ % các checks passed cho mỗi table/database/connection

---

## Phần I: Thiết lập Data Quality Monitoring

### Bước 1: Xác định yêu cầu từ góc nhìn Business (Data Owner)

**DO.1. Phân tích và xác định nhu cầu business:**
- Đặt business goals và scope cho data quality
- Xác định Critical Data Elements (CDEs)
- Đánh giá data quality dimensions phù hợp (timeliness, validity, completeness...)
- Thiết lập mức độ ưu tiên

**DO.2. Cung cấp danh sách tables và columns cần giám sát:**
- Xác định databases, data warehouses, data lakes cần monitor
- Quyết định stages nào cần giám sát (ingestion, reporting layer, data mart)
- Ưu tiên bảng theo tầm quan trọng (hỗ trợ sprints)
- Xác định bảng lớn (cần kế hoạch đặc biệt), bảng date-partitioned, bảng append-only
- Chỉ định tần suất cập nhật, các thay đổi schema dự kiến

**DO.3. Cung cấp danh sách metrics:**
- Xác định data quality expectations
- Liên kết metrics với dimensions (timeliness, completeness, validity, consistency, uniqueness)
- Thảo luận với Data Quality Team
- DQOps có hơn 150 built-in checks và hỗ trợ custom checks

**DO.4. (Tùy chọn) Xác định business KPIs:**
- KPIs tách riêng theo business areas, organizational units, geographical locations, suppliers
- DQOps cung cấp hơn 50 built-in dashboards, hỗ trợ tùy chỉnh qua Looker Studio

### Bước 2: Xác định yêu cầu từ góc nhìn Data Engineering

**DE.1. Xác định yêu cầu cho quy trình DE:**
- Review feasibility từ data engineering
- Định nghĩa incident resolution process
- Xác định notification channels (Slack, Teams, Jira, ServiceNow...)
- Tích hợp với DevOps/DataOps (Git, Airflow, dbt, Python Client)

**DE.2. Danh sách issues gần đây với data pipelines:**
- Nguyên nhân phổ biến: canceled jobs, timeouts, disk space, out-of-memory, network failures, bugs
- Ưu tiên data pipelines theo tầm quan trọng
- Xác định tần suất loading, parallel data streams (data groupings)
- DQOps hỗ trợ timeliness checks: freshness, staleness, ingestion delay

**DE.3. Review data quality checks hiện có:**
- Xác định logging framework
- Thu thập danh sách checks đã implement
- DQOps hỗ trợ custom SQL expressions cho checks nhanh

**DE.4. Giới thiệu Data Quality Team với infrastructure**

**DE.5. Cung cấp credentials cần thiết**

### Bước 3: Kết nối Data Quality Checks (Data Quality Team)

**DQ.1. Tạo môi trường data quality**

**DQ.2. Import metadata:**
- DQOps hỗ trợ: MySQL, PostgreSQL, Oracle, Redshift, Snowflake, BigQuery, Spark, Databricks, Trino, Athena, CSV, Parquet, JSON

**DQ.3. Deploy data quality checks:**

*3 loại checks trong DQOps:*
1. **Profiling checks**: Đánh giá data quality ban đầu, dùng cho exploration/experimentation
2. **Monitoring checks**: Giám sát liên tục, capture end-of-day/end-of-month status, hỗ trợ anomaly detection
3. **Partition checks**: Tính data quality riêng cho mỗi daily/monthly partition, phù hợp big tables

*Các loại rules:*
1. **Simple rules**: So sánh trực tiếp với threshold (equals, not equals, range, between)
2. **Relative value rules**: So sánh với giá trị trước đó (unchanged, change from similar time window)
3. **Time series rules**: Phân tích thay đổi qua thời gian (% deviation from average, standard deviation, anomaly detection với ARIMA/Prophet)

*Time slicing và Data grouping:*
- **Time slicing**: Tính metrics riêng cho mỗi time period (hourly, daily, weekly, monthly...) bằng GROUP BY timestamp
- **Data grouping**: Tính metrics riêng cho mỗi nhóm dữ liệu (country, vendor, department...) bằng GROUP BY discriminator column
- Kết hợp cả hai để xác định chính xác nguồn gốc issue

**DQ.4. Cấu hình alerting thresholds ban đầu:**
- 3 severity levels: **Warning** (quan sát), **Error** (cần sửa), **Fatal Error** (dừng pipeline)
- Nếu nhiều rules fail, DQOps chọn mức severity cao nhất

**DQ.5. (Tùy chọn) Phát triển custom data quality checks:**
- DQOps dùng Jinja2 templating cho SQL sensors
- Hỗ trợ custom Python rules

**DQ.6. Tạo data quality KPI dashboards:**
- **Governance dashboards**: KPIs tổng thể theo dimension
- **Operational dashboards**: Danh sách tables/columns bị ảnh hưởng, ưu tiên
- **Detailed dashboards**: Phân tích chuyên sâu (historical readouts, dimension-specific issues)

---

## Phần II: Cải thiện Data Quality KPIs

### Bước 4: Tối ưu hóa data quality scores

**DQ.7. Kiểm tra KPIs trên dashboards:**
- Xác định dimensions chưa đạt KPI
- Xác định data areas chưa đạt KPI
- Đánh giá mức KPI chấp nhận được
- Ưu tiên các data areas cần fix

**DQ.8. Xác định tables bị ảnh hưởng:**
- Chọn 1 KPI để cải thiện trước
- Ưu tiên tables theo số lượng issues
- Review theo thứ tự: Fatal Error → Error → Warning
- Phân biệt issues thực vs misconfiguration

**Data Quality Incident Automation:**
- DQOps nhóm issues tương tự thành **incidents**
- 4 trạng thái: Open → Acknowledged → Resolved / Muted
- Hỗ trợ grouping theo: Table, Dimension, Check category, Check type, Check name

**DQ.9. Re-execute data quality checks:**
- Xác định tables outdated, invalid checks, outdated checks
- Re-execute cho tables/partitions bị ảnh hưởng
- Cleanup outdated readouts và alerts
- Review KPIs lại trên dashboards

**DQ.10. Xác định unresolved issues:**
- Tạo báo cáo gồm: unmet KPIs, data areas có KPI thấp, tables bị ảnh hưởng
- Chuyển giao cho data quality operations team

### Bước 5: Sửa source data issues

**DO.6. Review data quality issue:**
- Data Owner kiểm tra dữ liệu ở source platform vs target platform
- Review data lineage, kiểm tra trực tiếp source table
- So sánh với issues tương tự trong quá khứ

**DO.7. Xác định root cause:**
- Kiểm tra maintenance windows, change logs, error logs
- Đánh giá alerting thresholds (quá nhạy?)
- Đánh giá mức độ liên quan của dữ liệu

**DO.8. Review/fix với Data Producer:**
- Thu thập thông tin, chuẩn bị information package
- Liên hệ external party, đề xuất deadline
- Thông báo schema changes cho DE và DQ teams

**DO.9. Tạo danh sách data quality exceptions:**
- Các phương án: cập nhật data model, thay đổi processing logic, decommission tables
- Hạ alerting thresholds, giảm severity level
- Customize sensors/rules
- Lập kế hoạch long-term improvement project

**DQ.12. Điều chỉnh thresholds và KPIs cho low-quality tables:**
- Deactivate checks (xóa hoặc set "disable" flag)
- Exclude tables khỏi monitoring
- Remove outdated results (DQOps lưu Parquet files theo connection/table/month)
- Reconfigure checks, recalculate, update dashboards

### Bước 6: Sửa data pipeline issues

**DE.7. Review issues trong data pipelines:**
- Timeliness: Pipeline không start đúng giờ, quá nhiều tasks, pipeline không finish
- Completeness: Pipeline không chạy, files corrupted, partial loading, maintenance
- Validity: Columns bị truncated, invalid values không bị exclude
- Consistency: Sai thứ tự columns, load duplicate
- Uniqueness: Table load 2 lần, files load nhiều lần

**DE.8. Fix issues trong data pipelines**

**DE.9. Tạo danh sách tables chưa production-ready**

**DQ.11. Reconfigure data quality checks**

---

## Quy trình tổng thể (Iterative)

```
Setting up monitoring → Check KPIs → Identify issues → 
  → Source data issue? → Data Owner reviews → Fix with Data Producer → Re-execute checks
  → Pipeline issue? → DE Team reviews → Fix pipelines → Re-execute checks
  → Cannot fix? → Create exceptions → Adjust thresholds/KPIs → Continue monitoring
```

---

## Điểm nổi bật của DQOps Platform

1. **150+ built-in checks** + khả năng tạo custom checks
2. **50+ built-in dashboards** (Looker Studio), hỗ trợ tùy chỉnh
3. **Incremental monitoring** cho big tables (partition elimination)
4. **Multi-cloud** data collection, lưu trữ local bằng Apache Parquet
5. **DevOps-friendly**: YAML configs trong Git, Python Client, REST API, CLI
6. **Data grouping** lên đến 9 levels
7. **Incident management** tự động với workflow 4 trạng thái
8. **Anomaly detection**: ARIMA, Prophet, standard deviation
9. **Tích hợp**: Airflow, dbt, Slack, Teams, Jira, ServiceNow, Azure DevOps
10. **Hỗ trợ data sources**: MySQL, PostgreSQL, Oracle, Redshift, Snowflake, BigQuery, Spark, Databricks, Trino, Athena, CSV, Parquet, JSON
