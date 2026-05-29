# Bảo vệ Dữ liệu Cá nhân — Công ty Chứng khoán Việt Nam

> Cập nhật lần cuối: 29/05/2026
>
> Hướng dẫn triển khai bảo vệ dữ liệu cá nhân (BVDLCN) cho công ty chứng khoán, phù hợp với Luật BVDLCN 91/2025/QH15 và Nghị định 356/2025/NĐ-CP.

---

## 1. Tại sao công ty chứng khoán cần đặc biệt chú ý?

Công ty chứng khoán (CTCK) xử lý lượng lớn **dữ liệu cá nhân nhạy cảm** — đây là loại dữ liệu chịu yêu cầu bảo vệ nghiêm ngặt nhất theo pháp luật Việt Nam.

### Dữ liệu nhạy cảm mà CTCK thường xử lý

| Loại dữ liệu | Ví dụ cụ thể |
|---------------|---------------|
| **Thông tin tài chính** | Thu nhập, tài sản ròng, lịch sử tín dụng, số dư tài khoản |
| **Dữ liệu giao dịch** | Lịch sử mua/bán chứng khoán, lệnh đặt, margin |
| **Sinh trắc học** | Khuôn mặt (eKYC), vân tay |
| **Thông tin định danh** | CCCD, hộ chiếu, địa chỉ, số điện thoại |
| **Dữ liệu hành vi** | Lịch sử đăng nhập, hoạt động trên app/web |
| **Thông tin tài khoản** | Số tài khoản, mật khẩu, OTP |

### Rủi ro đặc thù

- Phạt đến **5% doanh thu** cho vi phạm chuyển dữ liệu xuyên biên giới
- Phạt đến **3 tỷ VNĐ** cho các vi phạm khác
- Phạt **10 lần lợi nhuận bất hợp pháp** nếu mua bán dữ liệu trái phép
- Rủi ro uy tín: mất niềm tin khách hàng → mất tài sản quản lý
- Rủi ro pháp lý: bị thu hồi giấy phép hoạt động

---

## 2. Khung pháp lý áp dụng

### Văn bản chính

| Văn bản | Hiệu lực | Ghi chú |
|---------|----------|---------|
| Luật BVDLCN (91/2025/QH15) | 01/01/2026 | Luật chính, thay thế NĐ 13/2023 |
| Nghị định 356/2025/NĐ-CP | 01/01/2026 | Hướng dẫn chi tiết, thay thế NĐ 13/2023 |
| Luật Chứng khoán 2019 (54/2019/QH14) | 01/01/2021 | Quy định bảo mật thông tin khách hàng |
| Luật An ninh mạng (24/2018/QH14) | 01/01/2019 | Data localization |
| Luật Phòng chống rửa tiền 2022 | 01/03/2023 | KYC/AML bắt buộc |
| Thông tư UBCKNN về eKYC | Đang áp dụng | Xác thực khách hàng điện tử |

### Lưu ý quan trọng

- NĐ 356/2025 **thay thế hoàn toàn** NĐ 13/2023 từ 01/01/2026
- Dữ liệu tài chính (thu nhập, tín dụng, tài khoản) được xếp vào **dữ liệu nhạy cảm**
- Xử lý dữ liệu nhạy cảm yêu cầu **consent riêng biệt** và **biện pháp bảo vệ tăng cường**

---

## 3. Dữ liệu cá nhân trong CTCK — Phân loại

### Dữ liệu cơ bản

- Họ tên, ngày sinh, giới tính
- Số điện thoại, email
- Địa chỉ thường trú/tạm trú
- Quốc tịch
- Tình trạng hôn nhân
- Ảnh cá nhân

### Dữ liệu nhạy cảm (yêu cầu bảo vệ cao hơn)

- **Tài chính:** Thu nhập, nguồn tiền, tài sản, nợ, lịch sử tín dụng
- **Sinh trắc học:** Ảnh khuôn mặt (eKYC), vân tay, giọng nói
- **Tài khoản:** Số tài khoản chứng khoán, tài khoản ngân hàng liên kết
- **Giao dịch:** Lịch sử giao dịch, danh mục đầu tư, margin
- **Hành vi trực tuyến:** Log đăng nhập, lịch sử truy cập, IP address
- **Vị trí:** Dữ liệu GPS từ app mobile

---

## 4. Nghĩa vụ pháp lý cần tuân thủ

### 4.1. Đồng ý (Consent)

| Yêu cầu | Chi tiết |
|----------|---------|
| Hình thức | Rõ ràng, cụ thể, có thể chứng minh được |
| Nội dung | Mục đích xử lý, loại dữ liệu, thời gian lưu trữ, bên thứ ba nhận dữ liệu |
| Dữ liệu nhạy cảm | Consent **riêng biệt** cho từng loại dữ liệu nhạy cảm |
| Rút consent | Phải có cơ chế cho khách hàng rút lại bất kỳ lúc nào |
| Lưu trữ | Giữ bằng chứng consent (timestamp, nội dung đã đồng ý) |

#### Áp dụng cho CTCK

```
Khi mở tài khoản:
├── Consent cơ bản: xử lý dữ liệu để mở/quản lý tài khoản
├── Consent nhạy cảm (tài chính): thu thập thông tin thu nhập, tài sản
├── Consent nhạy cảm (sinh trắc): eKYC bằng khuôn mặt
├── Consent marketing: gửi tin khuyến mãi, tư vấn đầu tư
└── Consent chuyển dữ liệu: chia sẻ với đối tác/bên thứ ba
```

### 4.2. Thông báo xử lý dữ liệu (Privacy Notice)

Phải thông báo cho khách hàng **trước khi** xử lý, bao gồm:

- [ ] Danh tính và thông tin liên hệ của bên kiểm soát dữ liệu
- [ ] Mục đích xử lý dữ liệu
- [ ] Loại dữ liệu được thu thập
- [ ] Cơ sở pháp lý cho việc xử lý
- [ ] Thời gian lưu trữ
- [ ] Bên thứ ba nhận dữ liệu (nếu có)
- [ ] Quyền của chủ thể dữ liệu
- [ ] Thông tin về chuyển dữ liệu xuyên biên giới (nếu có)

### 4.3. Quyền của khách hàng (Data Subject Rights)

CTCK phải có quy trình xử lý khi khách hàng yêu cầu:

| Quyền | Thời hạn phản hồi | Lưu ý cho CTCK |
|-------|-------------------|----------------|
| Quyền được biết | Ngay lập tức | Cung cấp privacy notice |
| Quyền truy cập | 72 giờ | Cho xem dữ liệu đang lưu |
| Quyền chỉnh sửa | 72 giờ | Cập nhật thông tin sai |
| Quyền xóa | 72 giờ | *Ngoại trừ* dữ liệu phải giữ theo Luật CK, AML |
| Quyền hạn chế xử lý | 72 giờ | Ngừng dùng cho mục đích cụ thể |
| Quyền phản đối | 72 giờ | Opt-out marketing |
| Quyền data portability | 72 giờ | Xuất dữ liệu cho khách |
| Quyền rút consent | Ngay lập tức | Không ảnh hưởng xử lý trước đó |

#### Xung đột với quy định ngành

⚠️ **Lưu ý quan trọng:** Một số dữ liệu CTCK **không được xóa** dù khách hàng yêu cầu:
- Dữ liệu KYC/AML: phải giữ tối thiểu 5 năm sau khi đóng tài khoản (Luật Phòng chống rửa tiền)
- Dữ liệu giao dịch: phải giữ theo quy định của UBCKNN
- Dữ liệu kế toán: phải giữ theo Luật Kế toán

→ Khi từ chối yêu cầu xóa, phải giải thích rõ cơ sở pháp lý cho khách hàng.

### 4.4. Đánh giá tác động (DPIA)

CTCK **bắt buộc** phải thực hiện DPIA khi:
- Xử lý dữ liệu nhạy cảm quy mô lớn (→ luôn áp dụng cho CTCK)
- Chuyển dữ liệu xuyên biên giới
- Sử dụng công nghệ mới (AI scoring, automated decision-making)
- Profiling khách hàng

#### Nội dung DPIA

1. Mô tả hoạt động xử lý dữ liệu
2. Đánh giá tính cần thiết và tương xứng
3. Đánh giá rủi ro cho chủ thể dữ liệu
4. Biện pháp giảm thiểu rủi ro
5. Kế hoạch ứng phó sự cố

### 4.5. Bổ nhiệm nhân sự bảo vệ dữ liệu

| Yêu cầu | Chi tiết |
|----------|---------|
| Bộ phận/Nhân sự BVDLCN | Bắt buộc cho CTCK (xử lý dữ liệu nhạy cảm quy mô lớn) |
| Báo cáo | Trực tiếp cho Ban lãnh đạo |
| Nhiệm vụ | Giám sát tuân thủ, đào tạo, xử lý yêu cầu, liên hệ cơ quan quản lý |

### 4.6. Thông báo vi phạm dữ liệu (Data Breach Notification)

| Hành động | Thời hạn | Đối tượng |
|-----------|----------|-----------|
| Phát hiện & ghi nhận | Ngay lập tức | Nội bộ |
| Thông báo cơ quan quản lý | **72 giờ** | Bộ Công an (Cục A05) |
| Thông báo chủ thể dữ liệu | **72 giờ** | Khách hàng bị ảnh hưởng |

#### Nội dung thông báo

- Mô tả sự cố
- Loại và số lượng dữ liệu bị ảnh hưởng
- Hậu quả có thể xảy ra
- Biện pháp đã và đang thực hiện
- Thông tin liên hệ bộ phận BVDLCN

### 4.7. Chuyển dữ liệu xuyên biên giới

Áp dụng khi CTCK:
- Dùng cloud server nước ngoài
- Chia sẻ dữ liệu với công ty mẹ/đối tác nước ngoài
- Sử dụng SaaS/vendor nước ngoài xử lý dữ liệu khách hàng

#### Yêu cầu

- [ ] Lấy consent riêng cho việc chuyển dữ liệu ra nước ngoài
- [ ] Lập hồ sơ đánh giá tác động chuyển dữ liệu
- [ ] Xác định biện pháp bảo vệ của bên nhận
- [ ] Ký hợp đồng chuyển dữ liệu (data transfer agreement)
- [ ] Lưu bản sao dữ liệu tại Việt Nam
- [ ] Gửi hồ sơ cho Bộ Công an (theo NĐ 356)

---

## 5. Kế hoạch triển khai

### Phase 1: Đánh giá hiện trạng (1-2 tháng)

#### 1.1. Data Mapping & Inventory

- [ ] Liệt kê tất cả dữ liệu cá nhân đang thu thập
- [ ] Phân loại: cơ bản vs nhạy cảm
- [ ] Xác định nguồn thu thập (app, web, offline, đối tác)
- [ ] Xác định nơi lưu trữ (server nội bộ, cloud, vendor)
- [ ] Xác định ai có quyền truy cập
- [ ] Xác định dữ liệu nào được chia sẻ với bên thứ ba
- [ ] Xác định dữ liệu nào chuyển ra nước ngoài

#### 1.2. Gap Analysis

- [ ] So sánh hiện trạng với yêu cầu pháp luật
- [ ] Xác định gaps cần khắc phục
- [ ] Ưu tiên theo mức độ rủi ro

### Phase 2: Xây dựng framework (2-3 tháng)

#### 2.1. Chính sách & Quy trình

- [ ] **Chính sách BVDLCN** (Privacy Policy) — công khai cho khách hàng
- [ ] **Quy trình thu thập & consent** — form đồng ý, cơ chế opt-in/opt-out
- [ ] **Quy trình xử lý yêu cầu** — khi khách hàng thực hiện quyền
- [ ] **Quy trình ứng phó sự cố** — data breach response plan
- [ ] **Quy trình DPIA** — template và workflow đánh giá tác động
- [ ] **Chính sách lưu trữ & hủy** — retention schedule cho từng loại dữ liệu
- [ ] **Quy trình chuyển dữ liệu xuyên biên giới** — nếu áp dụng
- [ ] **Nội quy bảo mật nội bộ** — cho nhân viên

#### 2.2. Tổ chức nhân sự

- [ ] Bổ nhiệm Trưởng bộ phận BVDLCN (hoặc DPO)
- [ ] Thành lập team BVDLCN (có thể kiêm nhiệm)
- [ ] Xác định trách nhiệm từng phòng ban
- [ ] Thiết lập kênh báo cáo lên Ban lãnh đạo

#### 2.3. Hợp đồng & Pháp lý

- [ ] Cập nhật hợp đồng mở tài khoản (thêm consent clauses)
- [ ] Cập nhật Terms of Service và Privacy Policy trên website/app
- [ ] Rà soát hợp đồng với vendors/đối tác (thêm data processing agreement)
- [ ] Chuẩn bị data transfer agreement cho chuyển dữ liệu xuyên biên giới

### Phase 3: Triển khai kỹ thuật (3-6 tháng)

#### 3.1. Consent Management

- [ ] Xây dựng hệ thống quản lý consent (consent management platform)
- [ ] Lưu trữ bằng chứng consent (ai đồng ý, khi nào, nội dung gì)
- [ ] Cơ chế rút consent trên app/web
- [ ] Granular consent cho từng mục đích

#### 3.2. Access Control & Security

- [ ] Implement RBAC (Role-Based Access Control)
- [ ] Principle of least privilege
- [ ] Mã hóa dữ liệu nhạy cảm (at rest & in transit)
- [ ] Multi-factor authentication cho truy cập dữ liệu nhạy cảm
- [ ] Audit logging cho mọi truy cập dữ liệu cá nhân

#### 3.3. Data Masking & Anonymization

- [ ] Masking dữ liệu nhạy cảm trong môi trường non-production
- [ ] Anonymization cho analytics/reporting khi không cần PII
- [ ] Pseudonymization cho internal processing

#### 3.4. Data Retention & Deletion

- [ ] Implement retention policies tự động
- [ ] Quy trình xóa dữ liệu khi hết thời hạn lưu trữ
- [ ] Quy trình xóa theo yêu cầu khách hàng (trừ ngoại lệ pháp lý)

#### 3.5. Monitoring & Incident Response

- [ ] Hệ thống phát hiện data breach (SIEM, DLP)
- [ ] Quy trình escalation khi phát hiện sự cố
- [ ] Template thông báo vi phạm (cho cơ quan quản lý + khách hàng)
- [ ] Diễn tập ứng phó sự cố định kỳ

### Phase 4: Vận hành & Cải tiến (liên tục)

- [ ] Đào tạo nhân viên định kỳ (ít nhất 1 lần/năm)
- [ ] Audit nội bộ tuân thủ BVDLCN (ít nhất 1 lần/năm)
- [ ] Cập nhật DPIA khi có thay đổi quy trình
- [ ] Review và cập nhật chính sách khi có văn bản pháp luật mới
- [ ] Báo cáo định kỳ cho Ban lãnh đạo

---

## 6. Retention Schedule — Thời gian lưu trữ

| Loại dữ liệu | Thời gian lưu | Cơ sở pháp lý |
|---------------|---------------|----------------|
| KYC/AML (định danh khách hàng) | 5 năm sau đóng TK | Luật Phòng chống rửa tiền |
| Dữ liệu giao dịch chứng khoán | 10 năm | Quy định UBCKNN |
| Chứng từ kế toán | 10 năm | Luật Kế toán |
| Consent records | Suốt thời gian xử lý + 5 năm | Luật BVDLCN |
| Dữ liệu marketing | Đến khi rút consent | Luật BVDLCN |
| Log truy cập hệ thống | 3 năm | Luật An ninh mạng |
| Dữ liệu eKYC (sinh trắc) | Theo KYC (5 năm sau đóng TK) | NĐ 356 + Luật PCRT |
| Hồ sơ DPIA | 5 năm | NĐ 356 |

---

## 7. Các bên thứ ba cần rà soát

CTCK thường chia sẻ dữ liệu với:

| Bên thứ ba | Dữ liệu chia sẻ | Hành động cần làm |
|------------|-----------------|-------------------|
| Ngân hàng liên kết | Thông tin TK, giao dịch tiền | Data Processing Agreement |
| Sở GDCK (HOSE/HNX) | Lệnh giao dịch, thông tin TK | Tuân thủ quy định sở |
| VSD (Trung tâm Lưu ký) | Thông tin sở hữu CK | Tuân thủ quy định VSD |
| Vendor công nghệ | Dữ liệu trên hệ thống | DPA + security requirements |
| Cloud provider | Toàn bộ dữ liệu trên cloud | DPA + data localization check |
| Đối tác marketing | Email, phone, hành vi | Consent riêng + DPA |
| Cơ quan quản lý (UBCKNN, BCA) | Theo yêu cầu pháp luật | Cơ sở pháp lý: tuân thủ luật |

---

## 8. Checklist tuân thủ nhanh

### Bắt buộc (phải có ngay)

- [ ] Privacy Policy công khai trên website/app
- [ ] Cơ chế lấy consent khi mở tài khoản
- [ ] Consent riêng cho dữ liệu nhạy cảm (tài chính, sinh trắc)
- [ ] Bổ nhiệm nhân sự/bộ phận BVDLCN
- [ ] Quy trình xử lý yêu cầu từ khách hàng (72 giờ)
- [ ] Quy trình thông báo vi phạm dữ liệu (72 giờ)
- [ ] DPIA cho hoạt động xử lý dữ liệu nhạy cảm
- [ ] Mã hóa dữ liệu nhạy cảm

### Quan trọng (nên triển khai sớm)

- [ ] Data mapping & inventory đầy đủ
- [ ] Access control (RBAC) cho dữ liệu cá nhân
- [ ] Audit logging
- [ ] Retention schedule & auto-deletion
- [ ] Đào tạo nhân viên
- [ ] Rà soát hợp đồng với vendors

### Nâng cao (best practice)

- [ ] Consent management platform tự động
- [ ] Data masking cho môi trường test/dev
- [ ] Data lineage tracking cho PII
- [ ] Automated data quality checks
- [ ] Penetration testing định kỳ
- [ ] Privacy by Design trong phát triển sản phẩm mới

---

## 9. Template — Mục đích xử lý dữ liệu cho CTCK

Khi soạn Privacy Notice, các mục đích xử lý thường gặp:

| # | Mục đích | Cơ sở pháp lý | Loại dữ liệu |
|---|----------|---------------|---------------|
| 1 | Mở và quản lý tài khoản chứng khoán | Hợp đồng + Pháp luật | Cơ bản + Nhạy cảm (tài chính) |
| 2 | Xác thực danh tính (KYC/eKYC) | Pháp luật (Luật PCRT) | Cơ bản + Sinh trắc |
| 3 | Thực hiện giao dịch chứng khoán | Hợp đồng | Cơ bản + Giao dịch |
| 4 | Quản lý rủi ro & margin | Hợp đồng + Pháp luật | Tài chính + Giao dịch |
| 5 | Phòng chống rửa tiền (AML) | Pháp luật | Cơ bản + Tài chính + Giao dịch |
| 6 | Báo cáo cơ quan quản lý | Pháp luật | Theo yêu cầu |
| 7 | Chăm sóc khách hàng | Lợi ích hợp pháp | Cơ bản |
| 8 | Marketing & tư vấn đầu tư | **Consent** | Cơ bản + Hành vi |
| 9 | Phân tích & cải thiện dịch vụ | Lợi ích hợp pháp / Consent | Hành vi (anonymized) |
| 10 | Bảo mật hệ thống | Lợi ích hợp pháp | Log, IP, device info |

---

## 10. Rủi ro thường gặp & Cách phòng tránh

| Rủi ro | Hậu quả | Phòng tránh |
|--------|---------|-------------|
| Không lấy consent đúng cách | Phạt + vô hiệu hóa xử lý | Consent granular, lưu bằng chứng |
| Data breach không thông báo kịp | Phạt nặng + mất uy tín | Incident response plan + diễn tập |
| Nhân viên truy cập trái phép | Phạt + rủi ro hình sự | RBAC + audit log + đào tạo |
| Vendor nước ngoài không tuân thủ | Phạt CTCK (không phải vendor) | DPA chặt + audit vendor |
| Giữ dữ liệu quá thời hạn | Vi phạm storage limitation | Auto-deletion + retention policy |
| Dùng dữ liệu sai mục đích | Vi phạm purpose limitation | Consent riêng cho từng mục đích |
| Không có DPIA | Vi phạm nghĩa vụ | DPIA template + review định kỳ |

---

## 11. Tài liệu tham khảo

- [Luật BVDLCN 91/2025/QH15](https://luatvietnam.vn/) — Văn bản gốc
- [Nghị định 356/2025/NĐ-CP](https://luatvietnam.vn/) — Hướng dẫn chi tiết
- [Vietnam Briefing — PDPL Compliance Roadmap](https://www.vietnam-briefing.com/news/vietnams-cybersecurity-and-data-protection-rules-a-compliance-roadmap-for-businesses.html/)
- [China Briefing — Decree 356 Analysis](http://china-briefing.com/china-outbound-news/vietnam-personal-data-protection-regulation-decree-356)
- [IAPP — Vietnam PDPL Overview](https://iapp.org/news/a/vietnams-pdpl-in-focus-what-to-know-and-watch-for)
- [Rouse — What Businesses Need to Know](https://rouse.com/insights/news/2025/vietnam-s-new-personal-data-protection-law-what-businesses-need-to-know/)
- [Chambers — New Legal Framework](https://chambers.com/articles/new-legal-framework-on-personal-data-protection-in-vietnam)

---

## 12. Ghi chú cập nhật

| Ngày | Nội dung cập nhật |
|------|-------------------|
| 29/05/2026 | Tạo file ban đầu, dựa trên Luật 91/2025 + NĐ 356/2025 |

<!-- Thêm ghi chú khi có cập nhật mới -->

---

*Content was rephrased for compliance with licensing restrictions. Đây là tài liệu tham khảo, cần verify với văn bản pháp luật gốc và tư vấn pháp lý chuyên nghiệp trước khi áp dụng.*
