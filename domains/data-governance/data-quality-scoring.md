# Data Quality Scoring Framework

## Áp dụng cho Công ty Chứng khoán | Dựa trên DAMA-DMBOK 2nd Edition

---

## 1. Tổng quan

Data Quality Scoring (Chấm điểm chất lượng dữ liệu) là phương pháp đo lường mức độ dữ liệu đáp ứng được yêu cầu sử dụng của tổ chức. Theo DAMA-DMBOK, dữ liệu chất lượng cao là dữ liệu **fit for purpose** - phù hợp với mục đích sử dụng.

### Tại sao cần chấm điểm dữ liệu trong chứng khoán?

- Tuân thủ quy định UBCKNN, Ngân hàng Nhà nước
- Giảm rủi ro giao dịch sai, mất tiền khách hàng
- Đảm bảo báo cáo tài chính chính xác
- Nâng cao trải nghiệm khách hàng
- Hỗ trợ ra quyết định đầu tư dựa trên dữ liệu đáng tin cậy

---

## 2. Các chiều chất lượng dữ liệu (Data Quality Dimensions)

### 2.1 Sáu chiều cốt lõi (DAMA UK)

| # | Dimension | Tiếng Việt | Mô tả |
|---|-----------|------------|--------|
| 1 | **Completeness** | Đầy đủ | Tỷ lệ dữ liệu được điền so với 100% tiềm năng |
| 2 | **Uniqueness** | Duy nhất | Không có thực thể nào bị ghi trùng lặp |
| 3 | **Timeliness** | Kịp thời | Dữ liệu phản ánh đúng thời điểm yêu cầu |
| 4 | **Validity** | Hợp lệ | Dữ liệu tuân thủ format, kiểu dữ liệu, phạm vi |
| 5 | **Accuracy** | Chính xác | Dữ liệu mô tả đúng đối tượng thực tế |
| 6 | **Consistency** | Nhất quán | Không mâu thuẫn giữa các hệ thống/thời điểm |

### 2.2 Các chiều bổ sung

| Dimension | Tiếng Việt | Mô tả |
|-----------|------------|--------|
| **Integrity** | Toàn vẹn | Tham chiếu giữa các bảng/hệ thống không bị "mồ côi" |
| **Reasonability** | Hợp lý | Phân bố dữ liệu phù hợp với kỳ vọng thực tế |
| **Accessibility** | Khả dụng | Dữ liệu có thể truy cập khi cần |
| **Currency** | Cập nhật | Dữ liệu phản ánh trạng thái mới nhất |


---

## 3. Công thức chấm điểm

### 3.1 Công thức cơ bản (theo DAMA-DMBOK)

```
DQ Score (r) = (Total Records - Total Exceptions) / Total Records × 100%
```

**Ví dụ:**
- Tổng bản ghi kiểm tra: 10,000
- Số bản ghi vi phạm rule: 560
- DQ Score = (10,000 - 560) / 10,000 = **94.4%**

### 3.2 Công thức tổng hợp có trọng số

```
Overall DQ Score = Σ (Weight_i × DimensionScore_i) / Σ Weight_i
```

**Ví dụ cho dữ liệu giao dịch chứng khoán:**

| Dimension | Weight | Score | Weighted Score |
|-----------|--------|-------|----------------|
| Accuracy | 30% | 98% | 29.4 |
| Completeness | 25% | 95% | 23.75 |
| Timeliness | 25% | 99% | 24.75 |
| Validity | 10% | 97% | 9.7 |
| Consistency | 10% | 96% | 9.6 |
| **Tổng** | **100%** | | **97.2%** |

### 3.3 Ngưỡng đánh giá (Threshold)

| Mức | Score | Trạng thái | Hành động |
|-----|-------|------------|-----------|
| 🟢 Tốt | ≥ 95% | Đạt chuẩn | Tiếp tục giám sát |
| 🟡 Cảnh báo | 80% - 95% | Cần cải thiện | Lập kế hoạch khắc phục |
| 🔴 Nghiêm trọng | < 80% | Không chấp nhận | Hành động ngay lập tức |


---

## 4. Template: Data Quality Scorecard theo Domain

### 4.1 Domain: Dữ liệu Khách hàng (Customer/KYC)

| # | Business Rule | Dimension | Cách đo | Ngưỡng | Trọng số |
|---|---------------|-----------|---------|--------|----------|
| 1 | CMND/CCCD phải được điền đầy đủ | Completeness | % bản ghi có CMND | ≥ 99% | 20% |
| 2 | Số điện thoại đúng format 10 số | Validity | % SĐT hợp lệ | ≥ 95% | 10% |
| 3 | Mã khách hàng không trùng lặp | Uniqueness | % bản ghi unique | = 100% | 20% |
| 4 | Email đúng format | Validity | % email hợp lệ | ≥ 90% | 5% |
| 5 | Địa chỉ khớp với dữ liệu hành chính | Accuracy | % khớp reference | ≥ 85% | 15% |
| 6 | Thông tin KYC cập nhật trong 12 tháng | Currency | % KH cập nhật | ≥ 90% | 15% |
| 7 | Dữ liệu KH giữa Core và CRM nhất quán | Consistency | % khớp giữa 2 hệ thống | ≥ 98% | 15% |

### 4.2 Domain: Dữ liệu Giao dịch (Trading)

| # | Business Rule | Dimension | Cách đo | Ngưỡng | Trọng số |
|---|---------------|-----------|---------|--------|----------|
| 1 | Lệnh phải được ghi nhận trong 5 giây | Timeliness | % lệnh ≤ 5s | ≥ 99.5% | 25% |
| 2 | Giá lệnh trong biên độ cho phép | Validity | % giá hợp lệ | = 100% | 20% |
| 3 | Khối lượng lệnh > 0 và là bội số lot | Validity | % KL hợp lệ | = 100% | 15% |
| 4 | Mã CK tồn tại trong danh mục niêm yết | Validity | % mã CK hợp lệ | = 100% | 15% |
| 5 | Số dư trước/sau giao dịch nhất quán | Consistency | % khớp balance | = 100% | 15% |
| 6 | Không có giao dịch duplicate | Uniqueness | % giao dịch unique | = 100% | 10% |

### 4.3 Domain: Dữ liệu Giá Thị trường (Market Data)

| # | Business Rule | Dimension | Cách đo | Ngưỡng | Trọng số |
|---|---------------|-----------|---------|--------|----------|
| 1 | Giá real-time delay ≤ 3 giây so với sàn | Timeliness | % cập nhật ≤ 3s | ≥ 99% | 30% |
| 2 | Giá khớp với nguồn từ HOSE/HNX | Accuracy | % khớp chính xác | = 100% | 30% |
| 3 | Tất cả mã CK đang giao dịch có giá | Completeness | % mã có giá | = 100% | 20% |
| 4 | Giá nằm trong biên độ trần/sàn | Validity | % giá hợp lệ | = 100% | 10% |
| 5 | Khối lượng khớp lệnh hợp lý (không đột biến phi lý) | Reasonability | % nằm trong 3σ | ≥ 99% | 10% |


### 4.4 Domain: Dữ liệu Tài khoản & Số dư (Account/Balance)

| # | Business Rule | Dimension | Cách đo | Ngưỡng | Trọng số |
|---|---------------|-----------|---------|--------|----------|
| 1 | Mỗi KH chỉ có 1 tài khoản chính/loại | Uniqueness | % unique per type | = 100% | 15% |
| 2 | Số dư tiền khớp giữa hệ thống giao dịch và kế toán | Consistency | % khớp | = 100% | 25% |
| 3 | Số dư CK khớp giữa hệ thống và VSD | Accuracy | % khớp VSD | = 100% | 25% |
| 4 | Tất cả TK có đủ trường bắt buộc | Completeness | % complete | ≥ 99% | 15% |
| 5 | Tham chiếu TK → KH không orphan | Integrity | % valid FK | = 100% | 10% |
| 6 | Trạng thái TK phản ánh đúng thực tế | Currency | % TK đúng status | ≥ 99% | 10% |

### 4.5 Domain: Dữ liệu Báo cáo Quy định (Regulatory Reporting)

| # | Business Rule | Dimension | Cách đo | Ngưỡng | Trọng số |
|---|---------------|-----------|---------|--------|----------|
| 1 | Báo cáo nộp đúng deadline quy định | Timeliness | % nộp đúng hạn | = 100% | 25% |
| 2 | Dữ liệu đúng format UBCKNN yêu cầu | Validity | % đúng format | = 100% | 25% |
| 3 | Số liệu khớp với sổ sách kế toán | Accuracy | % khớp | = 100% | 20% |
| 4 | Tất cả trường bắt buộc được điền | Completeness | % complete | = 100% | 15% |
| 5 | Số liệu nhất quán giữa các báo cáo liên quan | Consistency | % nhất quán | = 100% | 15% |

---

## 5. Template: Data Quality Rule Documentation

### Mẫu tài liệu hóa rule chất lượng dữ liệu

```markdown
## Rule ID: DQ-[DOMAIN]-[###]

**Tên rule:** [Mô tả ngắn gọn]
**Domain:** [Customer | Trading | Market Data | Account | Regulatory]
**Dimension:** [Completeness | Uniqueness | Timeliness | Validity | Accuracy | Consistency]
**Mức độ nghiêm trọng:** [Critical | High | Medium | Low]

### Mô tả
[Mô tả chi tiết rule và lý do tồn tại]

### Đối tượng dữ liệu
- **Database/Table:** [tên bảng]
- **Column(s):** [tên cột]
- **Scope:** [All records | Filtered by condition]

### Công thức đo
- **Positive:** (Số bản ghi đạt / Tổng bản ghi) × 100
- **Negative:** (Số bản ghi vi phạm / Tổng bản ghi) × 100

### Ngưỡng
- 🟢 Acceptable: [≥ X%]
- 🟡 Warning: [Y% - X%]
- 🔴 Unacceptable: [< Y%]

### Hành động khi vi phạm
- **Escalation:** [Data Steward → DG Council → Management]
- **Remediation:** [Mô tả cách khắc phục]
- **Root Cause Analysis:** [Có/Không bắt buộc]

### Metadata
- **Owner:** [Tên/Phòng ban]
- **Steward:** [Tên người phụ trách]
- **Tần suất đo:** [Real-time | Daily | Weekly | Monthly]
- **Ngày tạo:** [YYYY-MM-DD]
- **Ngày review gần nhất:** [YYYY-MM-DD]
```


---

## 6. Template: Data Quality Dashboard Report

### Báo cáo tổng hợp chất lượng dữ liệu hàng tháng

```
╔══════════════════════════════════════════════════════════════╗
║           DATA QUALITY MONTHLY REPORT                       ║
║           Tháng: [MM/YYYY]                                  ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  OVERALL DQ SCORE:  [XX.X%]  [🟢/🟡/🔴]                     ║
║                                                              ║
╠══════════════════════════════════════════════════════════════╣
║  DOMAIN SCORES                                               ║
╠─────────────────────────┬────────┬───────┬───────────────────╣
║  Domain                 │ Score  │ Trend │ Status            ║
╠─────────────────────────┼────────┼───────┼───────────────────╣
║  Khách hàng (KYC)       │ XX.X%  │ ↑/↓/→ │ 🟢/🟡/🔴          ║
║  Giao dịch (Trading)    │ XX.X%  │ ↑/↓/→ │ 🟢/🟡/🔴          ║
║  Giá thị trường         │ XX.X%  │ ↑/↓/→ │ 🟢/🟡/🔴          ║
║  Tài khoản/Số dư        │ XX.X%  │ ↑/↓/→ │ 🟢/🟡/🔴          ║
║  Báo cáo quy định       │ XX.X%  │ ↑/↓/→ │ 🟢/🟡/🔴          ║
╠─────────────────────────┴────────┴───────┴───────────────────╣
║  TOP ISSUES                                                  ║
║  1. [Mô tả issue] - Impact: [High/Medium/Low]               ║
║  2. [Mô tả issue] - Impact: [High/Medium/Low]               ║
║  3. [Mô tả issue] - Impact: [High/Medium/Low]               ║
╠══════════════════════════════════════════════════════════════╣
║  ACTIONS REQUIRED                                            ║
║  • [Action item 1] - Owner: [Name] - Deadline: [Date]       ║
║  • [Action item 2] - Owner: [Name] - Deadline: [Date]       ║
╚══════════════════════════════════════════════════════════════╝
```

### Chi tiết theo Dimension

| Dimension | Tháng trước | Tháng này | Thay đổi | Target |
|-----------|-------------|-----------|----------|--------|
| Completeness | X% | X% | +/-X% | ≥95% |
| Uniqueness | X% | X% | +/-X% | =100% |
| Timeliness | X% | X% | +/-X% | ≥99% |
| Validity | X% | X% | +/-X% | ≥98% |
| Accuracy | X% | X% | +/-X% | ≥97% |
| Consistency | X% | X% | +/-X% | ≥98% |


---

## 7. Template: Data Quality Issue Log

| Issue ID | Ngày phát hiện | Domain | Dimension | Mô tả | Severity | Root Cause | Owner | Status | Deadline |
|----------|---------------|--------|-----------|--------|----------|------------|-------|--------|----------|
| DQI-001 | YYYY-MM-DD | Trading | Timeliness | Lệnh delay > 5s | Critical | Network latency | IT Ops | Open | YYYY-MM-DD |
| DQI-002 | YYYY-MM-DD | KYC | Completeness | 5% KH thiếu SĐT | Medium | UI không validate | Dev Team | In Progress | YYYY-MM-DD |
| DQI-003 | YYYY-MM-DD | Account | Consistency | Lệch số dư 0.1% | High | ETL timing | DBA | Resolved | YYYY-MM-DD |

---

## 8. Quy trình chấm điểm (Data Quality Management Cycle)

Theo DAMA-DMBOK, áp dụng chu trình **Plan-Do-Check-Act** (Shewhart/Deming):

### PLAN (Lập kế hoạch)
1. Xác định dữ liệu quan trọng (Critical Data Elements)
2. Định nghĩa business rules cho từng dimension
3. Thiết lập ngưỡng chấp nhận
4. Xác định trọng số cho từng rule/dimension
5. Chỉ định Data Steward chịu trách nhiệm

### DO (Thực hiện)
1. Triển khai công cụ đo lường (profiling, monitoring)
2. Chạy đánh giá ban đầu (initial assessment)
3. Ghi nhận kết quả baseline
4. Thực hiện remediation cho issues được phát hiện

### CHECK (Kiểm tra)
1. Đo lường định kỳ (daily/weekly/monthly)
2. So sánh với ngưỡng và baseline
3. Phát hiện xu hướng (trending)
4. Áp dụng Statistical Process Control (SPC) khi process ổn định

### ACT (Hành động)
1. Root cause analysis cho issues mới
2. Escalate issues vượt ngưỡng
3. Cập nhật rules nếu business thay đổi
4. Cải tiến quy trình để ngăn ngừa tái phát

---

## 9. Statistical Process Control (SPC) cho Data Quality

### Khái niệm
- Dùng biểu đồ kiểm soát (Control Chart) để theo dõi DQ score theo thời gian
- **UCL** (Upper Control Limit): Giới hạn trên = Mean + 3σ
- **LCL** (Lower Control Limit): Giới hạn dưới = Mean - 3σ
- Điểm nằm ngoài UCL/LCL → **Special Cause** → cần điều tra ngay

### Áp dụng cho chứng khoán

```
Ví dụ: Monitoring DQ Score của dữ liệu giao dịch hàng ngày

UCL = 99.8% ──────────────────────────────
                  ╱╲      ╱╲
Mean = 99.2% ───╱──╲────╱──╲───────────────
              ╱    ╲  ╱    ╲    ╱╲
LCL = 98.6% ╱──────╲╱──────╲──╱──╲────────
                                    ╲
                              ← Special Cause (cần điều tra)
```


---

## 10. Đặc điểm của Metric hiệu quả

Theo DAMA-DMBOK, mỗi metric chấm điểm cần đảm bảo 6 đặc điểm:

| Đặc điểm | Mô tả | Câu hỏi kiểm tra |
|-----------|--------|-------------------|
| **Measurability** | Phải đo được bằng con số | Có thể đếm/tính toán được không? |
| **Business Relevance** | Liên quan đến hoạt động kinh doanh | Metric này ảnh hưởng gì đến business? |
| **Acceptability** | Có ngưỡng chấp nhận rõ ràng | Bao nhiêu là "đạt", bao nhiêu là "không đạt"? |
| **Accountability** | Có người chịu trách nhiệm | Ai là Data Steward? Ai được notify khi lỗi? |
| **Controllability** | Có thể hành động khi vượt ngưỡng | Khi metric đỏ, có quy trình fix không? |
| **Trending** | Theo dõi được xu hướng | Có thể so sánh qua các kỳ không? |

---

## 11. Data Model Scorecard® (Hoberman)

Dùng để chấm điểm chất lượng mô hình dữ liệu (Logical/Physical Data Model):

| # | Tiêu chí | Điểm tối đa | Mô tả |
|---|----------|-------------|--------|
| 1 | Capture đúng requirements | 15 | Model phản ánh đúng yêu cầu business |
| 2 | Completeness | 15 | Đầy đủ entities, attributes, relationships |
| 3 | Schema đúng chuẩn hóa | 10 | Normalization phù hợp |
| 4 | Dễ sử dụng | 5 | Abstraction hợp lý |
| 5 | Sử dụng đúng patterns | 5 | Best practices modeling |
| 6 | Naming conventions | 10 | Đặt tên nhất quán, rõ ràng |
| 7 | Readability | 5 | Layout dễ đọc |
| 8 | Definitions rõ ràng | 15 | Metadata đầy đủ, chính xác |
| 9 | Nhất quán với enterprise | 5 | Phù hợp enterprise data model |
| 10 | Metadata khớp data thực | 10 | Không có gap giữa model và reality |
| | **TỔNG** | **100** | |

---

## 12. Lộ trình triển khai (Roadmap)

### Phase 1: Foundation (Tháng 1-3)
- [ ] Xác định Critical Data Elements (CDEs) cho từng domain
- [ ] Thiết lập Data Quality rules cơ bản
- [ ] Chỉ định Data Stewards
- [ ] Chạy Initial Assessment (baseline)
- [ ] Thiết lập ngưỡng chấp nhận

### Phase 2: Operations (Tháng 4-6)
- [ ] Triển khai automated monitoring
- [ ] Thiết lập DQ Dashboard
- [ ] Quy trình issue management
- [ ] Training cho stakeholders
- [ ] Đo lường và báo cáo định kỳ (weekly)

### Phase 3: Optimization (Tháng 7-12)
- [ ] Áp dụng SPC cho các metrics ổn định
- [ ] Root cause analysis cho issues tái phát
- [ ] Tích hợp DQ checks vào CI/CD pipeline
- [ ] Mở rộng scope sang thêm domains
- [ ] Review và cập nhật rules hàng quý

### Phase 4: Maturity (Năm 2+)
- [ ] Predictive data quality (phát hiện trước khi xảy ra)
- [ ] Self-healing data pipelines
- [ ] Data Quality SLAs với vendors/đối tác
- [ ] Tích hợp DQ scoring vào enterprise data catalog
- [ ] Liên kết DQ metrics với business KPIs


---

## 13. RACI Matrix cho Data Quality

| Hoạt động | Data Owner | Data Steward | DQ Analyst | IT/DBA | Management |
|-----------|-----------|--------------|------------|--------|------------|
| Định nghĩa business rules | A | R | C | I | I |
| Thiết lập ngưỡng | A | R | C | I | I |
| Đo lường DQ | I | C | R | C | I |
| Báo cáo DQ scores | I | C | R | I | I |
| Điều tra root cause | I | A | R | R | I |
| Remediation | A | R | C | R | I |
| Escalation | I | R | R | I | A |
| Review & cập nhật rules | A | R | C | C | I |

> R = Responsible, A = Accountable, C = Consulted, I = Informed

---

## 14. Ví dụ thực tế: DQ Rule cho Giao dịch Chứng khoán

### Rule ID: DQ-TRD-001

**Tên rule:** Equity Order Timeliness Check
**Domain:** Trading
**Dimension:** Timeliness
**Mức độ nghiêm trọng:** Critical

#### Mô tả
Mỗi lệnh mua/bán cổ phiếu phải được ghi nhận vào hệ thống giao dịch trong vòng 5 giây kể từ khi khách hàng submit lệnh.

#### Đối tượng dữ liệu
- **Database:** TradingDB
- **Table:** Orders
- **Columns:** order_submitted_time, order_received_time
- **Scope:** Tất cả lệnh trong phiên giao dịch (9:00 - 14:45)

#### Công thức đo
```sql
-- Positive measure
SELECT 
  COUNT(CASE WHEN DATEDIFF(second, order_submitted_time, order_received_time) <= 5 THEN 1 END) * 100.0 
  / COUNT(*) AS dq_score_pct
FROM Orders
WHERE order_date = @report_date
  AND order_submitted_time BETWEEN '09:00:00' AND '14:45:00';
```

#### Ngưỡng
- 🟢 Acceptable: ≥ 99.5%
- 🟡 Warning: 98% - 99.5%
- 🔴 Unacceptable: < 98%

#### Hành động khi vi phạm
- **🟡 Warning:** Notify Data Steward, ghi log để theo dõi trend
- **🔴 Unacceptable:** 
  - Escalate ngay cho IT Operations Manager
  - Kiểm tra network/system performance
  - Báo cáo Risk Management nếu ảnh hưởng khách hàng

#### Metadata
- **Owner:** Giám đốc Phòng Giao dịch
- **Steward:** Trưởng nhóm Data Operations
- **Tần suất đo:** Real-time (alert) + Daily (report)
- **Ngày tạo:** 2024-01-15
- **Review cycle:** Hàng quý

---

## 15. Tài liệu tham khảo

- DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge*, 2nd Edition. Technics Publications, 2017.
- DAMA UK. *The Six Primary Dimensions for Data Quality Assessment*. White Paper, 2013.
- Hoberman, Steve. *Data Model Scorecard*. Technics Publications, 2015.
- Sebastian-Coleman, Laura. *Measuring Data Quality for Ongoing Improvement*. Morgan Kaufmann, 2013.
- ISO 8000 - Data Quality Standard.
- Maydanchik, Arkady. *Data Quality Assessment*. Technics Publications, 2007.

---

> **Ghi chú:** File này được tổng hợp từ DAMA-DMBOK 2nd Edition và customize cho ngành chứng khoán Việt Nam. Cần điều chỉnh rules, ngưỡng, và trọng số cụ thể theo đặc thù từng công ty.
