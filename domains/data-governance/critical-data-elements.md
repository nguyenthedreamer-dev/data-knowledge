# Critical Data Elements (CDE)

## Khái niệm, Phương pháp Xác định & Áp dụng cho Chứng khoán

---

## 1. Định nghĩa

### 1.1 CDE là gì?

**Critical Data Elements (CDEs)** là các phần tử dữ liệu cụ thể mà nếu chất lượng không đạt yêu cầu, sẽ gây ảnh hưởng trực tiếp hoặc gián tiếp về **tài chính, pháp lý, vận hành** cho tổ chức.

Nói cách khác: CDEs là **10-20% data elements quan trọng nhất** mà tổ chức phải ưu tiên đảm bảo chất lượng cao.

### 1.2 Đặc điểm của CDE

- Thiết yếu cho quy trình kinh doanh cốt lõi
- Bắt buộc cho báo cáo tài chính hoặc quy định
- Gây tổn thất tài chính nếu sai
- Ảnh hưởng trực tiếp đến khách hàng
- Được sử dụng cho ra quyết định quan trọng
- Có yêu cầu bảo mật/privacy cao

### 1.3 CDE trong các Framework

| Framework | Cách tiếp cận CDE |
|-----------|-------------------|
| **DCAM** (EDM Council) | CDE là khái niệm trung tâm, có capability riêng trong Component 2 (Data Quality) |
| **DAMA-DMBOK** | Nhắc đến trong Data Quality chapter: "Identify Critical Data and Business Rules" |
| **BCBS 239** | Yêu cầu xác định critical data cho risk aggregation & reporting |
| **ISO 8000** | Focus vào Master Data quality, implicitly covers CDEs |

---

## 2. Tại sao CDE quan trọng?

### 2.1 Lợi ích của việc xác định CDE


```
┌─────────────────────────────────────────────────────────────┐
│                    TẠI SAO CẦN XÁC ĐỊNH CDE?                │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ✓ Focus governance vào nơi quan trọng nhất                  │
│  ✓ Giảm chi phí (không cần quản lý tất cả data elements)    │
│  ✓ Ưu tiên resources cho dữ liệu có business impact cao     │
│  ✓ Đáp ứng yêu cầu regulatory compliance                    │
│  ✓ Đo lường ROI rõ ràng hơn cho DQ program                  │
│  ✓ Tạo quick wins để build momentum                          │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### 2.2 Rủi ro khi không có CDE

- Cố gắng quản lý chất lượng **tất cả** dữ liệu → tốn kém, không hiệu quả
- Không biết ưu tiên → mọi issue đều "quan trọng" → không action gì
- Không thể chứng minh ROI cho data governance program
- Không đáp ứng được kỳ vọng regulatory
- Data stewards bị overwhelmed

---

## 3. Tiêu chí xác định CDE

### 3.1 Sáu tiêu chí chính (DCAM approach)

| # | Tiêu chí | Câu hỏi kiểm tra | Trọng số gợi ý |
|---|----------|-------------------|:---:|
| 1 | **Regulatory Impact** | Dữ liệu này bắt buộc cho báo cáo quy định? | 25% |
| 2 | **Financial Materiality** | Nếu sai, gây tổn thất tài chính bao nhiêu? | 25% |
| 3 | **Business Process Dependency** | Bao nhiêu quy trình cốt lõi phụ thuộc vào data element này? | 20% |
| 4 | **Risk Exposure** | Mức độ rủi ro nếu data element này không chính xác? | 15% |
| 5 | **Customer Impact** | Ảnh hưởng trực tiếp đến khách hàng như thế nào? | 10% |
| 6 | **Decision-Making Reliance** | Data element này được dùng cho quyết định quan trọng nào? | 5% |

### 3.2 Phân loại mức độ Critical

| Level | Tên | Mô tả | Ví dụ trong CTCK |
|:---:|------|--------|------------------|
| **1** | Mission Critical | Sai = dừng hoạt động hoặc vi phạm pháp luật | Số dư tiền KH, Giá giao dịch |
| **2** | Business Critical | Sai = tổn thất tài chính đáng kể | Tỷ lệ margin, NAV quỹ |
| **3** | Important | Sai = giảm hiệu quả vận hành | SĐT khách hàng, Email |
| **4** | Standard | Sai = bất tiện nhưng không critical | Ghi chú nội bộ, preferences |

---

## 4. Quy trình xác định CDE (Identification Process)

### 4.1 Methodology: Funnel Approach

```
    ┌─────────────────────────────────┐
    │    ALL DATA ELEMENTS             │  ← Hàng ngàn elements
    │    (Full Inventory)              │
    ├─────────────────────────────────┤
    │  Filter 1: Regulatory Required   │  ← Loại bỏ non-regulated
    ├─────────────────────────────────┤
    │  Filter 2: Business Process      │  ← Chỉ giữ core processes
    │  Dependency                      │
    ├─────────────────────────────────┤
    │  Filter 3: Financial Impact      │  ← Chỉ giữ high-impact
    ├─────────────────────────────────┤
    │  Filter 4: Risk Assessment       │  ← Đánh giá rủi ro
    ├───────────────────┤
    │  CRITICAL DATA    │  ← 10-20% tổng data elements
    │  ELEMENTS (CDEs)  │
    └───────────────────┘
```

### 4.2 Quy trình 6 bước

#### Bước 1: Inventory (Kiểm kê)
- Liệt kê tất cả data elements trong scope
- Nguồn: Data models, Data dictionaries, System catalogs
- Output: Danh sách tất cả data elements theo domain

#### Bước 2: Classify (Phân loại)
- Phân loại theo business domain
- Gán metadata: system of record, owner, usage
- Output: Data elements được phân nhóm

#### Bước 3: Assess (Đánh giá)
- Đánh giá mỗi element theo 6 tiêu chí (Section 3.1)
- Scoring: 1 (thấp) → 5 (cao) cho mỗi tiêu chí
- Input từ: Business SMEs, Compliance, Risk, Operations
- Output: Score cho từng data element

#### Bước 4: Prioritize (Ưu tiên hóa)
- Rank dựa trên tổng score
- Xác định threshold (cutoff point)
- Thường top 10-20% sẽ là CDEs
- Output: Danh sách CDE chính thức

#### Bước 5: Govern (Quản trị)
- Gán Data Owner và Data Steward cho mỗi CDE
- Định nghĩa DQ rules và thresholds
- Thiết lập monitoring và reporting
- Output: CDE governance framework

#### Bước 6: Measure (Đo lường)
- Implement DQ rules
- Monitor liên tục
- Report DQ scores
- Review và update CDEs định kỳ (quarterly/annually)
- Output: DQ dashboards, issue logs


---

## 5. Template: CDE Assessment Scorecard

### 5.1 Mẫu đánh giá CDE

| Data Element | Domain | Regulatory (1-5) | Financial (1-5) | Process (1-5) | Risk (1-5) | Customer (1-5) | Decision (1-5) | Total Score | CDE? |
|---|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Customer_ID | KYC | 5 | 4 | 5 | 4 | 5 | 3 | **26** | ✅ |
| ID_Number (CMND) | KYC | 5 | 3 | 5 | 5 | 5 | 3 | **26** | ✅ |
| Account_Balance | Account | 5 | 5 | 5 | 5 | 5 | 5 | **30** | ✅ |
| Order_Price | Trading | 5 | 5 | 5 | 5 | 4 | 5 | **29** | ✅ |
| Stock_Code | Trading | 5 | 5 | 5 | 4 | 4 | 5 | **28** | ✅ |
| Margin_Ratio | Risk | 5 | 5 | 4 | 5 | 3 | 5 | **27** | ✅ |
| Email | KYC | 2 | 1 | 3 | 1 | 3 | 1 | **11** | ❌ |
| Preferred_Language | Profile | 1 | 1 | 1 | 1 | 2 | 1 | **7** | ❌ |

> **Threshold gợi ý:** Total Score ≥ 20/30 → CDE

### 5.2 CDE Inventory Template

```markdown
## CDE-[DOMAIN]-[###]

**Data Element Name:** [Tên element]
**Business Name:** [Tên business dễ hiểu]
**Domain:** [KYC | Trading | Account | Market | Risk | Regulatory]
**System of Record:** [Hệ thống gốc]

### Classification
- **Criticality Level:** [1-Mission Critical | 2-Business Critical | 3-Important]
- **Data Type:** [String | Numeric | Date | Boolean]
- **Sensitivity:** [Public | Internal | Confidential | Restricted]

### Ownership
- **Data Owner:** [Tên/Chức vụ]
- **Data Steward:** [Tên/Chức vụ]
- **Technical Custodian:** [Tên/Team]

### Quality Rules
| Rule ID | Dimension | Rule Description | Threshold |
|---------|-----------|-----------------|-----------|
| R1 | Completeness | Phải có giá trị (not null) | ≥ 99% |
| R2 | Validity | Phải thuộc domain values | = 100% |
| R3 | Accuracy | Khớp với source of record | ≥ 99.5% |
| R4 | Timeliness | Cập nhật trong X phút | ≥ 99% |

### Lineage
- **Source:** [Hệ thống nguồn]
- **Transformations:** [Mô tả biến đổi]
- **Consumers:** [Hệ thống/Báo cáo sử dụng]

### Regulatory Mapping
- **Quy định liên quan:** [UBCKNN / VSD / NHNN / Internal]
- **Reporting requirements:** [Tên báo cáo cụ thể]

### Monitoring
- **Frequency:** [Real-time | Hourly | Daily | Weekly]
- **Alert recipients:** [Distribution list]
- **Escalation path:** [Steward → Owner → DG Council]
```

---

## 6. CDEs cho Công ty Chứng khoán Việt Nam

### 6.1 Domain: Khách hàng (Customer/KYC)

| # | CDE | Business Name | Lý do Critical | Quy định |
|---|-----|---------------|----------------|----------|
| 1 | customer_id | Mã khách hàng | Định danh duy nhất, liên kết mọi giao dịch | UBCKNN |
| 2 | id_number | Số CMND/CCCD | KYC bắt buộc, AML | Luật PCRT |
| 3 | full_name | Họ và tên | Xác minh danh tính | UBCKNN |
| 4 | date_of_birth | Ngày sinh | KYC, xác minh tuổi giao dịch | UBCKNN |
| 5 | nationality | Quốc tịch | Phân loại NĐT nước ngoài | UBCKNN |
| 6 | tax_id | Mã số thuế | Báo cáo thuế, withholding | Tổng cục thuế |
| 7 | bank_account | Số TK ngân hàng | Chuyển tiền, thanh toán | NHNN |
| 8 | kyc_status | Trạng thái KYC | Cho phép/không cho phép giao dịch | UBCKNN |

### 6.2 Domain: Giao dịch (Trading)

| # | CDE | Business Name | Lý do Critical | Quy định |
|---|-----|---------------|----------------|----------|
| 1 | order_id | Mã lệnh | Định danh giao dịch, audit trail | UBCKNN |
| 2 | stock_code | Mã chứng khoán | Xác định tài sản giao dịch | HOSE/HNX |
| 3 | order_type | Loại lệnh (mua/bán) | Xác định chiều giao dịch | |
| 4 | order_price | Giá đặt lệnh | Xác định giá trị giao dịch | UBCKNN |
| 5 | order_quantity | Khối lượng đặt | Xác định quy mô | |
| 6 | matched_price | Giá khớp lệnh | Giá trị thực tế | HOSE/HNX |
| 7 | matched_quantity | Khối lượng khớp | Quy mô thực tế | |
| 8 | order_time | Thời gian đặt lệnh | Audit, regulatory | UBCKNN |
| 9 | settlement_date | Ngày thanh toán (T+2) | Chu kỳ thanh toán | VSD |

### 6.3 Domain: Tài khoản & Số dư (Account/Balance)

| # | CDE | Business Name | Lý do Critical | Quy định |
|---|-----|---------------|----------------|----------|
| 1 | cash_balance | Số dư tiền | Sức mua, khả năng đặt lệnh | UBCKNN |
| 2 | stock_balance | Số dư CK (per mã) | Khả năng bán, tài sản KH | VSD |
| 3 | margin_ratio | Tỷ lệ ký quỹ | Quản lý rủi ro margin | UBCKNN |
| 4 | buying_power | Sức mua | Giới hạn đặt lệnh mua | |
| 5 | collateral_value | Giá trị tài sản đảm bảo | Quản lý nợ margin | UBCKNN |
| 6 | account_status | Trạng thái tài khoản | Active/Frozen/Closed | UBCKNN |
| 7 | debt_balance | Dư nợ margin | Quản lý rủi ro tín dụng | UBCKNN |

### 6.4 Domain: Dữ liệu Thị trường (Market Data)

| # | CDE | Business Name | Lý do Critical | Quy định |
|---|-----|---------------|----------------|----------|
| 1 | reference_price | Giá tham chiếu | Cơ sở tính biên độ | HOSE/HNX |
| 2 | ceiling_price | Giá trần | Giới hạn mua | HOSE/HNX |
| 3 | floor_price | Giá sàn | Giới hạn bán | HOSE/HNX |
| 4 | last_price | Giá khớp gần nhất | Hiển thị cho KH, tính NAV | |
| 5 | total_volume | Tổng KL khớp | Thanh khoản thị trường | |
| 6 | stock_status | Trạng thái CK | Cho phép giao dịch hay không | HOSE/HNX |

### 6.5 Domain: Quản lý Rủi ro (Risk)

| # | CDE | Business Name | Lý do Critical | Quy định |
|---|-----|---------------|----------------|----------|
| 1 | capital_adequacy_ratio | Tỷ lệ an toàn vốn | Regulatory requirement | UBCKNN |
| 2 | net_asset_value | NAV (quỹ) | Định giá quỹ | UBCKNN |
| 3 | concentration_ratio | Tỷ lệ tập trung | Giới hạn đầu tư | UBCKNN |
| 4 | total_exposure | Tổng dư nợ cho vay | Quản lý rủi ro tín dụng | UBCKNN |
| 5 | maintenance_margin | Tỷ lệ duy trì | Trigger force sell | UBCKNN |


---

## 7. CDE Governance Model

### 7.1 Roles & Responsibilities

```
┌──────────────────────────────────────────────────────┐
│                  DATA GOVERNANCE COUNCIL              │
│         (Approve CDE list, Resolve escalations)      │
├──────────────────────────────────────────────────────┤
│                                                       │
│   DATA OWNER (per Domain)                            │
│   • Accountable cho CDE quality                      │
│   • Approve business rules                           │
│   • Fund remediation                                 │
│                                                       │
├──────────────────────────────────────────────────────┤
│                                                       │
│   DATA STEWARD (per Domain)                          │
│   • Day-to-day quality monitoring                    │
│   • Define & refine DQ rules                         │
│   • Investigate issues                               │
│   • Coordinate remediation                           │
│                                                       │
├──────────────────────────────────────────────────────┤
│                                                       │
│   DATA CUSTODIAN (IT/DBA)                            │
│   • Implement DQ checks                             │
│   • Maintain monitoring tools                        │
│   • Execute technical remediation                    │
│                                                       │
└──────────────────────────────────────────────────────┘
```

### 7.2 CDE Lifecycle

```
┌────────┐    ┌──────────┐    ┌─────────┐    ┌──────────┐    ┌────────┐
│Identify│ →  │ Define   │ →  │ Monitor │ →  │ Improve  │ →  │ Review │
│        │    │ Rules    │    │         │    │          │    │        │
└────────┘    └──────────┘    └─────────┘    └──────────┘    └────────┘
     ↑                                                             │
     └─────────────────────────────────────────────────────────────┘
                        (Quarterly/Annual review)
```

### 7.3 CDE Change Management

Khi nào CDE list thay đổi:
- Business process thay đổi
- Quy định mới từ UBCKNN/VSD
- Sản phẩm mới ra mắt (VD: phái sinh, trái phiếu)
- M&A hoặc tái cơ cấu
- Kết quả từ DQ assessment cho thấy elements mới cần governance

**Quy trình thay đổi:**
1. Đề xuất thay đổi (bởi Steward hoặc Owner)
2. Impact assessment
3. Review bởi DG Council
4. Approve/Reject
5. Update CDE registry
6. Implement new rules & monitoring
7. Communicate changes

---

## 8. CDE Quality Monitoring Dashboard

### 8.1 Mẫu Dashboard

```
╔══════════════════════════════════════════════════════════════╗
║              CDE QUALITY DASHBOARD                          ║
║              Ngày: [DD/MM/YYYY]                             ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  TỔNG CDE: [XX]    │  ĐẠT: [XX] 🟢  │  CẢNH BÁO: [X] 🟡  │  LỖI: [X] 🔴  ║
║                                                              ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  TOP CDEs CẦN CHÚ Ý:                                        ║
║  ┌────────────────────┬─────────┬──────────┬───────────┐    ║
║  │ CDE                │ Score   │ Trend    │ Issue     │    ║
║  ├────────────────────┼─────────┼──────────┼───────────┤    ║
║  │ margin_ratio       │ 94.2% 🟡│ ↓ -0.3% │ DQI-045   │    ║
║  │ customer_id_number │ 97.1% 🟡│ → 0.0%  │ DQI-032   │    ║
║  │ order_price        │ 99.99%🟢│ ↑ +0.01%│ None      │    ║
║  └────────────────────┴─────────┴──────────┴───────────┘    ║
║                                                              ║
╠══════════════════════════════════════════════════════════════╣
║  DOMAIN SUMMARY                                              ║
║  ┌──────────────┬───────┬──────┬──────┬──────┬─────────┐   ║
║  │ Domain       │ CDEs  │ Pass │ Warn │ Fail │ Score   │   ║
║  ├──────────────┼───────┼──────┼──────┼──────┼─────────┤   ║
║  │ Customer     │  8    │  7   │  1   │  0   │ 97.5%   │   ║
║  │ Trading      │  9    │  9   │  0   │  0   │ 99.8%   │   ║
║  │ Account      │  7    │  6   │  1   │  0   │ 98.2%   │   ║
║  │ Market Data  │  6    │  6   │  0   │  0   │ 99.9%   │   ║
║  │ Risk         │  5    │  4   │  1   │  0   │ 96.8%   │   ║
║  └──────────────┴───────┴──────┴──────┴──────┴─────────┘   ║
╚══════════════════════════════════════════════════════════════╝
```

### 8.2 KPIs cho CDE Program

| KPI | Mô tả | Target | Frequency |
|-----|--------|--------|-----------|
| CDE Coverage | % CDEs có DQ rules | 100% | Monthly |
| CDE Pass Rate | % CDEs đạt threshold | ≥ 95% | Daily |
| Mean Time to Detect | Thời gian phát hiện issue | < 1 hour | Per incident |
| Mean Time to Resolve | Thời gian giải quyết issue | < 24 hours | Per incident |
| CDE Ownership | % CDEs có Owner + Steward | 100% | Monthly |
| Rule Automation | % DQ rules automated | ≥ 80% | Quarterly |
| Issue Recurrence | % issues tái phát | < 5% | Quarterly |

---

## 9. Best Practices

### 9.1 Dos ✅

- **Bắt đầu nhỏ:** 20-30 CDEs cho phase 1, mở rộng dần
- **Business-led:** CDE phải được xác định bởi business, không phải IT
- **Document lý do:** Mỗi CDE phải có justification rõ ràng
- **Automate sớm:** Invest vào automated monitoring từ đầu
- **Report regularly:** DQ scores phải visible cho stakeholders
- **Review quarterly:** CDE list phải được review ít nhất hàng quý
- **Link to business outcomes:** Luôn gắn DQ metrics với business impact

### 9.2 Don'ts ❌

- **Đừng chọn quá nhiều:** > 100 CDEs ban đầu = không focus, fail
- **Đừng chỉ IT-driven:** CDE program không có business buy-in = vô nghĩa
- **Đừng chỉ measure, không act:** Metrics không dẫn đến improvement = lãng phí
- **Đừng skip root cause:** Chỉ fix symptoms → issues tái phát
- **Đừng quên lineage:** Không biết data đến từ đâu = không fix được root cause
- **Đừng one-and-done:** CDE list phải sống, phải evolve theo business

### 9.3 Common Pitfalls

| Pitfall | Hậu quả | Giải pháp |
|---------|---------|-----------|
| Chọn CDEs dựa trên ý kiến cá nhân | Bias, miss critical elements | Dùng scoring matrix + multiple stakeholders |
| Không có executive sponsor | Thiếu resources, bị deprioritize | Gắn CDE program vào regulatory requirement |
| Rules quá strict | False positives quá nhiều → alert fatigue | Calibrate thresholds dựa trên baseline data |
| Không phân biệt environments | Prod vs Non-prod khác nhau | Chỉ monitor CDEs trên Production |
| Thiếu feedback loop | Rules lỗi thời, không phản ánh thực tế | Quarterly review với business SMEs |

---

## 10. Lộ trình triển khai CDE Program

### Phase 1: Pilot (Tháng 1-2)
- [ ] Chọn 1 domain pilot (recommend: Trading hoặc Account)
- [ ] Workshop với business SMEs để identify CDEs
- [ ] Scoring assessment (15-25 CDEs)
- [ ] Define DQ rules cho top 10 CDEs
- [ ] Implement basic monitoring
- [ ] Baseline measurement

### Phase 2: Expand (Tháng 3-4)
- [ ] Mở rộng sang 2-3 domains nữa
- [ ] Tổng cộng 30-50 CDEs
- [ ] Automate DQ checks
- [ ] Thiết lập reporting cadence
- [ ] Assign Owners & Stewards chính thức
- [ ] First remediation projects

### Phase 3: Operate (Tháng 5-8)
- [ ] Full CDE registry (tất cả domains)
- [ ] Dashboard operational
- [ ] SLAs established
- [ ] Issue management process mature
- [ ] Integration với Data Catalog
- [ ] Training cho broader organization

### Phase 4: Optimize (Tháng 9-12+)
- [ ] Predictive DQ (phát hiện trước issues)
- [ ] CDE scoring integrated vào SDLC
- [ ] Vendor DQ SLAs (data providers)
- [ ] Benchmarking với industry
- [ ] Mature governance operating model
- [ ] Annual DCAM assessment

---

## 11. Tài liệu tham khảo

- EDM Council. *DCAM - Data Management Capability Assessment Model*. https://edmcouncil.org/frameworks/dcam
- DAMA International. *DAMA-DMBOK 2nd Edition*, Chapter 13: Data Quality. 2017.
- Mahanti, Rupa. *Data Quality: Dimensions, Measurement, Strategy, Management, and Governance*. ASQ Quality Press, 2019.
- Oracle. *Critical Data Elements in Data Governance*. Oracle Documentation.
- Alation. *Critical Data Elements Best Practices for Data Governance*. 2025.
- Alation. *Mastering Critical Data Elements for Financial Services*. 2025.
- DataKitchen. *Critical Data Elements: Your Shortcut to Data Governance*. 2025.
- BCBS 239. *Principles for Effective Risk Data Aggregation and Risk Reporting*. Basel Committee, 2013.

---

> **Ghi chú:** Nội dung tổng hợp từ DCAM framework (EDM Council), DAMA-DMBOK, và các nguồn public. Customize cho ngành chứng khoán Việt Nam. Cần điều chỉnh danh sách CDEs cụ thể theo đặc thù từng công ty.
