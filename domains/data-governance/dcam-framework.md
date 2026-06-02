# DCAM - Data Management Capability Assessment Model

## Framework của EDM Council (Enterprise Data Management Council)

---

## 1. Tổng quan

**DCAM** (Data Management Capability Assessment Model) là framework được phát triển bởi **EDM Council** (nay là EDM Association) nhằm đánh giá và nâng cao năng lực quản lý dữ liệu của tổ chức.

DCAM cung cấp:
- Mô hình tiêu chuẩn để đánh giá maturity quản lý dữ liệu
- Best practices cho việc thiết lập, vận hành và duy trì chương trình data management
- Hệ thống scoring để đo lường và benchmark giữa các tổ chức
- Lộ trình cải tiến dựa trên gap analysis

### Đặc điểm nổi bật
- Xuất phát từ **ngành tài chính** (ngân hàng, chứng khoán, bảo hiểm)
- Focus vào **business alignment** và **regulatory compliance**
- Có hệ thống chấm điểm chi tiết (scoring 1-6)
- Gồm 38 capabilities và 136 sub-capabilities (v2.2)
- Phiên bản mới nhất: **DCAM v3** (2025)

### Phiên bản
| Version | Năm | Ghi chú |
|---------|-----|---------|
| DCAM v1 | 2014 | Phiên bản đầu tiên |
| DCAM v2 | 2018 | Mở rộng capabilities |
| DCAM v2.2 | 2021 | Cập nhật, 38 capabilities, 136 sub-capabilities |
| DCAM v3 | 2025 | Phiên bản mới nhất, cập nhật AI/Cloud |

---

## 2. Cấu trúc DCAM Framework

### 2.1 Ba lớp chính (Three Layers)

```
┌─────────────────────────────────────────────────────┐
│              FOUNDATION COMPONENTS                    │
│  (Chiến lược, Business Case, Tổ chức)               │
├─────────────────────────────────────────────────────┤
│              EXECUTION COMPONENTS                     │
│  (Data Quality, Architecture, Operations, Controls)  │
├─────────────────────────────────────────────────────┤
│              COLLABORATION COMPONENTS                 │
│  (Đưa vào vận hành bởi data producers & consumers)  │
└─────────────────────────────────────────────────────┘
```

### 2.2 Tám thành phần cốt lõi (Eight Core Components)


| # | Component | Mô tả | Layer |
|---|-----------|--------|-------|
| 1 | **Data Management Strategy & Governance** | Thiết lập tầm nhìn, mục tiêu, cơ chế giám sát cho data management | Foundation |
| 2 | **Data Quality** | Đảm bảo dữ liệu chính xác, đầy đủ, nhất quán, đáng tin cậy | Execution |
| 3 | **Data Architecture** | Thiết kế framework có thể mở rộng cho lưu trữ, tích hợp, sử dụng dữ liệu | Execution |
| 4 | **Data Operations** | Quản lý quy trình hàng ngày: ingestion, transformation, storage | Execution |
| 5 | **Data Governance & Stewardship** | Định nghĩa roles, responsibilities, policies cho ownership và compliance | Foundation |
| 6 | **Technology Architecture** | Triển khai và quản lý hạ tầng công nghệ hỗ trợ data management | Execution |
| 7 | **Data Risk Management** | Xác định và giảm thiểu rủi ro liên quan đến bảo mật, privacy, sử dụng dữ liệu | Execution |
| 8 | **Data Analytics & Insights** | Khai thác dữ liệu cho analytics và ra quyết định | Collaboration |

---

## 3. Chi tiết từng Component

### Component 1: Data Management Strategy & Governance

**Mục tiêu:** Xác định cách data management được định nghĩa, tổ chức, tài trợ, quản trị và nhúng vào tổ chức.

**Capabilities:**
- Xây dựng Data Management Strategy
- Phát triển Business Case cho data management
- Thiết lập cấu trúc tổ chức (organizational structure)
- Xác định funding model
- Đo lường program effectiveness

**Key Questions:**
- Tổ chức có chiến lược data management rõ ràng không?
- Có business case cho đầu tư vào data management không?
- Executive sponsorship ở mức nào?
- Chiến lược DM có align với chiến lược kinh doanh không?

### Component 2: Data Quality

**Mục tiêu:** Đảm bảo dữ liệu đạt chất lượng phù hợp cho mục đích sử dụng.

**Capabilities:**
- Xác định Critical Data Elements (CDEs)
- Thiết lập Data Quality rules và standards
- Đo lường và monitoring DQ
- Remediation và root cause analysis
- DQ reporting và dashboards

**Key Questions:**
- CDEs đã được xác định chưa?
- Có business rules cho DQ chưa?
- DQ được đo lường tự động hay thủ công?
- Có quy trình remediation khi phát hiện issues?

### Component 3: Data Architecture

**Mục tiêu:** Thiết kế kiến trúc dữ liệu bền vững, có khả năng mở rộng.

**Capabilities:**
- Enterprise Data Model
- Data flow documentation
- Data lineage
- Integration architecture
- Reference data architecture

**Key Questions:**
- Có enterprise data model không?
- Data lineage có được track end-to-end không?
- Kiến trúc có support scalability không?

### Component 4: Data Operations

**Mục tiêu:** Quản lý vận hành dữ liệu hàng ngày hiệu quả.

**Capabilities:**
- Data ingestion & integration processes
- Data transformation & enrichment
- Data storage management
- Batch & real-time processing
- Monitoring & alerting

**Key Questions:**
- Quy trình ETL/ELT có được document và monitor?
- Có SLAs cho data delivery không?
- Incident management cho data issues như thế nào?

### Component 5: Data Governance & Stewardship

**Mục tiêu:** Thiết lập cấu trúc quản trị với roles, responsibilities, policies rõ ràng.

**Capabilities:**
- Data Governance operating model
- Data ownership & stewardship
- Policy & standards management
- Issue escalation & resolution
- Business glossary & metadata management

**Key Questions:**
- Có Data Governance Council không?
- Data Owners và Stewards đã được chỉ định?
- Policies có được communicate và enforce?
- Business glossary có được duy trì?

### Component 6: Technology Architecture

**Mục tiêu:** Hạ tầng công nghệ hỗ trợ đầy đủ cho data management.

**Capabilities:**
- Data management tooling
- Data catalog & metadata tools
- DQ monitoring tools
- Data integration platforms
- Security & access control technology

**Key Questions:**
- Có data catalog enterprise-wide không?
- Tools có integrate với nhau không?
- Automation level ở mức nào?

### Component 7: Data Risk Management

**Mục tiêu:** Xác định, đánh giá và giảm thiểu rủi ro dữ liệu.

**Capabilities:**
- Data risk identification & assessment
- Data security & privacy controls
- Regulatory compliance monitoring
- Data retention & disposal
- Business continuity for data

**Key Questions:**
- Data risks có được identify và assess định kỳ?
- Có data classification scheme không?
- Compliance monitoring có automated không?

### Component 8: Data Analytics & Insights

**Mục tiêu:** Khai thác giá trị từ dữ liệu cho analytics và decision-making.

**Capabilities:**
- Self-service analytics enablement
- Advanced analytics & AI/ML
- Data visualization & reporting
- Data sharing & collaboration
- Data monetization

**Key Questions:**
- Business users có thể self-serve analytics không?
- Dữ liệu có trusted đủ để drive decisions không?
- Có data products / data marketplace không?


---

## 4. Hệ thống chấm điểm DCAM (Scoring System)

### 4.1 Thang điểm 6 mức (Maturity Levels)

| Level | Tên | Mô tả |
|-------|-----|--------|
| **1** | Not Initiated | Chưa bắt đầu, không có hoạt động nào |
| **2** | Conceptual | Đang nhận thức, có kế hoạch nhưng chưa triển khai |
| **3** | Developmental | Đang phát triển, triển khai một phần |
| **4** | Defined | Đã định nghĩa, có quy trình và policy rõ ràng |
| **5** | Achieved | Đạt được, vận hành ổn định và đo lường được |
| **6** | Enhanced | Tối ưu, liên tục cải tiến và dẫn đầu industry |

### 4.2 Cách tính điểm

Mỗi **sub-capability** được chấm điểm từ 1-6 dựa trên:
- **Evidence (Bằng chứng):** Tài liệu, artifacts chứng minh capability tồn tại
- **Stakeholder validation:** Xác nhận từ người liên quan
- **Operational effectiveness:** Mức độ hoạt động hiệu quả trong thực tế

```
Component Score = Average(Sub-capability Scores)
Overall DCAM Score = Weighted Average(Component Scores)
```

### 4.3 Maturity Assessment Process

```
1. Scope Definition    → Xác định phạm vi đánh giá
2. Evidence Collection → Thu thập bằng chứng (documents, interviews)
3. Scoring             → Chấm điểm từng sub-capability
4. Gap Analysis        → Phân tích khoảng cách với target
5. Roadmap             → Xây dựng lộ trình cải thiện
6. Benchmarking        → So sánh với industry peers
```

### 4.4 Ví dụ Scorecard

| Component | Current Score | Target Score | Gap | Priority |
|-----------|:---:|:---:|:---:|:---:|
| 1. Strategy & Governance | 3.2 | 4.5 | -1.3 | High |
| 2. Data Quality | 2.8 | 4.0 | -1.2 | Critical |
| 3. Data Architecture | 3.5 | 4.0 | -0.5 | Medium |
| 4. Data Operations | 3.0 | 4.0 | -1.0 | High |
| 5. Governance & Stewardship | 2.5 | 4.0 | -1.5 | Critical |
| 6. Technology Architecture | 3.8 | 4.5 | -0.7 | Medium |
| 7. Data Risk Management | 3.0 | 4.5 | -1.5 | Critical |
| 8. Analytics & Insights | 2.5 | 3.5 | -1.0 | Medium |
| **Overall** | **3.0** | **4.1** | **-1.1** | |

---

## 5. DCAM vs Các Framework khác

| Tiêu chí | DCAM (EDM Council) | DAMA-DMBOK | CMMI-DMM |
|-----------|-------------------|------------|----------|
| **Nguồn gốc** | EDM Council (Financial Services) | DAMA International | CMMI Institute |
| **Focus** | Assessment & Maturity | Knowledge & Best Practices | Process Maturity |
| **Ngành chính** | Tài chính, Banking, Securities | Đa ngành | Đa ngành |
| **Cấu trúc** | 8 Components, 38 Capabilities | 11 Knowledge Areas | 25 Process Areas |
| **Scoring** | 1-6 (6 levels) | Không có scoring gốc | 1-5 (5 levels) |
| **Regulatory focus** | Rất mạnh (BCBS 239, MiFID II) | Trung bình | Thấp |
| **Certification** | DCAM Practitioner | CDMP (DAMA) | Organizational |
| **Phù hợp cho** | Assessment, Benchmarking | Learning, Reference | Process Improvement |
| **Chi phí** | Paid (EDM membership) | Book purchase | Paid assessment |

### Khi nào dùng DCAM?
- Tổ chức tài chính (ngân hàng, chứng khoán, bảo hiểm)
- Cần assessment và benchmarking với industry
- Regulatory-driven (BCBS 239, SOX, MiFID)
- Cần scoring system rõ ràng

### Khi nào dùng DAMA-DMBOK?
- Xây dựng knowledge base về data management
- Training và certification cá nhân (CDMP)
- Tham khảo best practices đa ngành
- Giai đoạn đầu xây dựng program

---

## 6. Áp dụng DCAM cho Công ty Chứng khoán Việt Nam

### 6.1 Regulatory Alignment

| Quy định VN | DCAM Component liên quan |
|---|---|
| Thông tư UBCKNN về BCTC | Component 2 (DQ), 7 (Risk) |
| Quy định KYC/AML | Component 5 (Governance), 7 (Risk) |
| Quy định về an toàn vốn | Component 2 (DQ), 8 (Analytics) |
| Bảo mật thông tin KH | Component 7 (Risk) |
| Báo cáo VSD (lưu ký) | Component 4 (Operations), 2 (DQ) |

### 6.2 Lộ trình triển khai DCAM Assessment

**Phase 1: Preparation (2-4 tuần)**
- Xác định scope assessment
- Identify stakeholders
- Thu thập tài liệu hiện có
- Training team về DCAM framework

**Phase 2: Assessment (4-6 tuần)**
- Interviews với Data Owners, Stewards, IT
- Review documents và artifacts
- Scoring từng sub-capability
- Validate scores với stakeholders

**Phase 3: Analysis & Roadmap (2-4 tuần)**
- Gap analysis
- Prioritization dựa trên business impact & regulatory risk
- Develop improvement roadmap
- Estimate resources & timeline

**Phase 4: Implementation (Ongoing)**
- Quick wins (3-6 tháng)
- Medium-term improvements (6-12 tháng)
- Long-term transformation (12-24 tháng)
- Re-assessment hàng năm


### 6.3 Quick Assessment Template

Dùng để đánh giá nhanh trước khi làm full DCAM assessment:

| # | Câu hỏi | Yes/No/Partial | Score (1-6) |
|---|---------|:-:|:-:|
| 1 | Có Data Management Strategy document? | | |
| 2 | Có executive sponsor cho data program? | | |
| 3 | Có Data Governance Council hoặc tương đương? | | |
| 4 | Data Owners đã được chỉ định cho critical domains? | | |
| 5 | Critical Data Elements đã được xác định? | | |
| 6 | Có Data Quality rules và monitoring? | | |
| 7 | Có Business Glossary / Data Dictionary? | | |
| 8 | Data lineage được document? | | |
| 9 | Có data classification policy? | | |
| 10 | DQ metrics được report định kỳ? | | |
| 11 | Có incident management cho data issues? | | |
| 12 | Có data retention/disposal policy? | | |
| 13 | Regulatory compliance được monitor? | | |
| 14 | Có data catalog hoặc metadata tool? | | |
| 15 | Self-service analytics available cho business? | | |

---

## 7. Governance Principles trong DCAM

DCAM nhấn mạnh governance là nền tảng cho data management hiệu quả:

### 7.1 Accountability & Ownership
- Mỗi data domain phải có Data Owner (business)
- Data Stewards chịu trách nhiệm day-to-day
- Rõ ràng RACI cho mọi hoạt động data

### 7.2 Policy & Standards
- Policies phải được document, communicate, enforce
- Standards phải measurable và auditable
- Regular review và update cycle

### 7.3 Compliance Monitoring
- Ongoing assessment tuân thủ quy định nội bộ và pháp luật
- Automated monitoring khi có thể
- Regular audits

### 7.4 Performance Measurement
- KPIs cho data management program
- Tracking governance effectiveness
- Regular reporting lên executive level

---

## 8. BCBS 239 và DCAM

BCBS 239 (Basel Committee on Banking Supervision - Principles for Effective Risk Data Aggregation and Reporting) là driver chính cho DCAM trong ngành tài chính.

### 14 Principles của BCBS 239:

| # | Principle | DCAM Component |
|---|-----------|----------------|
| 1 | Governance | 1, 5 |
| 2 | Data Architecture & IT Infrastructure | 3, 6 |
| 3 | Accuracy and Integrity | 2 |
| 4 | Completeness | 2 |
| 5 | Timeliness | 2, 4 |
| 6 | Adaptability | 3, 6 |
| 7 | Accuracy (reporting) | 2, 8 |
| 8 | Comprehensiveness (reporting) | 8 |
| 9 | Clarity and Usefulness | 8 |
| 10 | Frequency | 4, 8 |
| 11 | Distribution | 8 |
| 12 | Review | 5, 7 |
| 13 | Remedial actions | 2, 5 |
| 14 | Supervisory review | 7 |

> **Lưu ý cho CTCK VN:** Tuy BCBS 239 chủ yếu áp dụng cho ngân hàng, nhưng các nguyên tắc về data aggregation và reporting cũng phù hợp cho công ty chứng khoán, đặc biệt khi UBCKNN tăng cường yêu cầu về risk reporting.

---

## 9. Tài liệu tham khảo

- EDM Council. *DCAM - Data Management Capability Assessment Model*. https://edmcouncil.org/frameworks/dcam
- EDM Council. *DCAM v3 Announcement*. 2025.
- Capco. *Elevating The Governance And Management Of Data - The DCAM Framework*. 2023.
- Sogeti Labs. *Data Governance Frameworks - The DCAM CDGC*. 2025.
- Collibra. *Scoring on all DCAM capabilities*. 2022.
- Snowflake. *DCAM Explained: Data Management Framework*. 2025.

---

> **Ghi chú:** DCAM là framework proprietary của EDM Council. Tài liệu đầy đủ cần EDM membership hoặc mua license. Nội dung file này tổng hợp từ các nguồn public để sử dụng nội bộ cho mục đích học tập và reference.
