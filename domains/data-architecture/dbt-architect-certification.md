# dbt Architect Certification — Tài liệu ôn thi tổng hợp

> Tổng hợp từ [dbt Certified Architect Path (learn.getdbt.com)](https://learn.getdbt.com/learn/learning-path/dbt-certified-cloud-architect), [trang kỳ thi chính thức](https://www.getdbt.com/certifications/dbt-architect-certification-exam), [Study Guide PDF v6.3 của dbt Labs](https://www.getdbt.com/dbt-assets/dbt-certificate-study-guide-for-cloud-architect) và docs.getdbt.com.
> Nội dung đã được diễn giải lại/tóm lược sang tiếng Việt để tuân thủ giới hạn bản quyền của nguồn.
> Bản tiếng Anh: [dbt-architect-certification-en.md](./dbt-architect-certification-en.md)
> Cập nhật: 2026-07.

---

## Mục lục

1. [Tổng quan kỳ thi](#1-tổng-quan-kỳ-thi)
2. [Blueprint — 8 topic được đánh giá](#2-blueprint--8-topic-được-đánh-giá)
3. [Learning Path chính thức (6 Milestones) — có gắn link video](#3-learning-path-chính-thức-6-milestones)
4. [Kiến thức ôn tập chi tiết theo từng topic](#4-kiến-thức-ôn-tập-chi-tiết)
5. [10 câu hỏi mẫu chính thức + đáp án + giải thích](#5-10-câu-hỏi-mẫu-chính-thức)
6. [Những vùng dễ mất điểm nhất](#6-những-vùng-dễ-mất-điểm-nhất)
7. [Kế hoạch ôn 4–6 tuần + checklist trước ngày thi](#7-kế-hoạch-ôn-46-tuần)
8. [Nguồn tham khảo](#8-nguồn-tham-khảo)

---

## 1. Tổng quan kỳ thi

| Hạng mục | Chi tiết |
|---|---|
| Tên | dbt Architect Certification Exam (khi ra mắt gọi là "dbt Cloud Architect") |
| Thời lượng | 2 giờ |
| Số câu | 65 (có thêm một số câu **không tính điểm**, không phân biệt được với câu tính điểm) |
| Điểm đạt | 65% (~43 câu đúng) |
| Cách chấm | 1 điểm/câu đúng, 0 điểm câu sai, **mọi câu có trọng số bằng nhau**, không trừ điểm |
| Hình thức | Online proctored, đăng ký qua [Talview](https://pages.talview.com/dbtlabs/certifications/) |
| Trình duyệt | Caveon Web browser |
| Giá | 200 USD/lần thi (miễn phí phụ trội cho Coalesce premium attendee, giảm giá cho dbt Labs SI Partner) |
| Ngôn ngữ | Study guide PDF ghi "English only"; trang kỳ thi hiện tại đã có **English / Japanese / French** |
| Kết quả | Biết điểm ngay sau khi submit |
| Hiệu lực | **2 năm** kể từ ngày đạt |
| Thi lại | Được thi lại, phải trả phí lại. Hủy/đổi lịch miễn phí nếu ≥ 24h trước giờ thi. No-show không hoàn tiền |

### Đối tượng và điều kiện nền

- dbt Labs khuyến nghị: thành thạo SQL + **tối thiểu 6 tháng kinh nghiệm administrate một account dbt Enterprise**.
- Prerequisite thực tế của learning path: hoàn thành **dbt Fundamentals**, và tốt nhất là đã có **dbt Analytics Engineering Certification** trước.
- Nên biết về **ADLC (Analytics Development Lifecycle)** — framework dbt Labs dùng để định hình kiến trúc dbt.
- Đây là kỳ thi về **admin/platform**, không phải về phát triển model. Không kiểm tra chi tiết đặc thù của một warehouse hay một Git provider cụ thể — nó kiểm tra best practice mang tính tổng quát.

### Các dạng câu hỏi (rất quan trọng — không chỉ có trắc nghiệm)

| Dạng | Ghi chú chiến thuật |
|---|---|
| Multiple-choice (1 hoặc nhiều đáp án) | Đề có ghi rõ "2 possible solutions" khi cần chọn nhiều |
| Fill-in-the-blank | Phải nhớ chính xác tên setting/prefix/command |
| Matching | Ghép permission set ↔ quyền, job type ↔ trigger |
| Hotspot | Click đúng vùng trên ảnh screenshot UI / sơ đồ |
| Build list | Sắp xếp đúng **thứ tự** các bước / các command trong job |
| **DOMC** (Discrete Option Multiple Choice) | Từng đáp án hiện lên riêng lẻ, bạn phải trả lời Yes/No cho từng cái và **không xem lại được**. Không dùng được kỹ thuật loại trừ → phải biết chắc |

DOMC là dạng gây mất điểm nhiều nhất. Với DOMC, hãy tự trả lời câu hỏi trong đầu **trước khi** đọc option đầu tiên.

Quản lý thời gian: 65 câu / 120 phút ≈ **1 phút 50 giây/câu**. Câu nào bí thì flag và bỏ qua (trừ DOMC — không quay lại được).

---

## 2. Blueprint — 8 topic được đánh giá

Đây là topic outline chính thức mà các SME của dbt Labs dùng để viết đề. dbt Labs **không công bố tỷ lệ % cho từng topic** (mọi câu trọng số bằng nhau).

### Topic 1 — Configuring dbt data warehouse connections
- Cách kết nối warehouse
- Cấu hình IP whitelist
- Tạo và test connection cho project
- Xác thực qua OAuth để truy cập dữ liệu trong dbt
- Thêm Client ID và Secret cho OAuth

### Topic 2 — Configuring dbt git connections
- Kết nối git repo vào dbt
- Thiết lập integration với các git provider

### Topic 3 — Creating and maintaining dbt environments
- Access control giữa các environment khác nhau
- Khi nào dùng service account
- Rotate key pair authentication qua API
- Environment variables
- Tạo deployment environment mới
- Set default schema/dataset cho environment
- Custom branch và cách gán vào environment
- Cấu hình dbt để defer sang environment khác

### Topic 4 — Creating and maintaining job definitions
- Set up CI job có deferral
- Các step bên trong một dbt job
- Đặt schedule cho job
- Thứ tự đúng của các run command
- Tạo job mới
- Các setting optional: env var override, threads, deferral, target name, dbt version override
- Generate documentation trong job để populate trang dbt Catalog
- Job chaining (trigger job sau khi job khác xong)
- Cấu hình Advanced CI
- Cấu hình self-deferral
- Biết chọn **loại deferral nào** cho tình huống nào

### Topic 5 — Configuring dbt security and licenses
- Tạo service token cho API access
- Gán permission set
- Tạo license mapping
- Thêm/xóa user
- Thêm SSO application cho dbt Enterprise
- Tạo và gán RBAC

### Topic 6 — Setting up monitoring and alerting for jobs
- Email notification
- Webhooks cho integration event-driven với hệ thống khác

### Topic 7 — Setting up a dbt mesh and leveraging cross-project references
- Tạo thêm project dbt
- Environment type liên quan thế nào tới cross-project reference
- Model governance

### Topic 8 — Configuring and using dbt Catalog
- Dùng Catalog để hiểu lineage, troubleshoot, tối ưu cost/performance
- Dùng Catalog để tìm public model và cross-project reference

---

## 3. Learning Path chính thức (6 Milestones)

Nguồn: [dbt Certified Architect Path](https://learn.getdbt.com/learn/learning-path/dbt-certified-cloud-architect) — bản thân trang path có 1 video giới thiệu (3:23).

Ký hiệu: 🎥 = **có video** (Video / Course / MicroCourse trên dbt Learn đều là nội dung video + quiz) · 📄 = tài liệu đọc (doc/article) · **[R]** Required · **[E]** Elective

### Milestone #1 — Setting up dbt Connections

| | Nội dung | Loại | Link |
|---|---|---|---|
| **[R]** | dbt Architect Certification Learning Path Overview | 🎥 Video | [mở](https://learn.getdbt.com/courses/dbt-architect-certification-learning-path-overview) |
| **[R]** | dbt and Data Platforms (~2h) | 🎥 Course | [mở](https://learn.getdbt.com/courses/dbt-cloud-and-data-platforms) |
| **[R]** | Configuring public IP restrictions | 📄 Resource | [mở](https://learn.getdbt.com/courses/configuring-public-ip-restrictions) · [docs](https://docs.getdbt.com/docs/cloud/secure/ip-restrictions) |
| **[R]** | About data platform connections | 📄 Resource | [mở](https://learn.getdbt.com/courses/about-data-platform-connections) |
| **[R]** | Single sign-on (SSO) overview | 📄 Resource | [mở](https://learn.getdbt.com/courses/single-sign-on-sso-overview) · [docs](https://docs.getdbt.com/docs/cloud/manage-access/sso-overview) |
| **[E]** | Git Fundamentals | 🎥 Course | [mở](https://learn.getdbt.com/courses/git-fundamentals) |
| **[R]** | Connect to GitHub | 📄 Resource | [mở](https://learn.getdbt.com/courses/connect-to-github) |
| **[R]** | Connect to GitLab | 📄 Resource | [mở](https://learn.getdbt.com/courses/connect-to-gitlab) |
| **[R]** | Connect to Azure DevOps | 📄 Resource | [mở](https://learn.getdbt.com/courses/connect-to-azure-devops) |
| **[R]** | Connect with Git clone | 📄 Resource | [mở](https://learn.getdbt.com/courses/connect-with-git-clone) |
| **[E]** | dbt and Snowflake for Admins (~1h) | 🎥 Course | [mở](https://learn.getdbt.com/courses/dbt-cloud-and-snowflake-for-admins) |

Study guide PDF còn liệt kê các khóa admin theo platform khác (chọn theo warehouse bạn dùng):
🎥 [Databricks for Admins](https://learn.getdbt.com/courses/dbt-cloud-and-databricks-for-admins) · 🎥 [BigQuery for Admins](https://learn.getdbt.com/courses/dbt-cloud-and-bigquery-for-admins) · 🎥 [Redshift for Admins](https://learn.getdbt.com/courses/dbt-cloud-and-redshift-for-admins)

### Milestone #2 — Configuring and Managing Projects

| | Nội dung | Loại | Link |
|---|---|---|---|
| **[R]** | dbt Environments (~1h) | 🎥 Course | [mở](https://learn.getdbt.com/courses/dbt-environments) |
| **[R]** | Getting Started with git branching strategies in dbt | 📄 Article | [mở](https://learn.getdbt.com/courses/getting-started-with-git-branching-strategies-in-dbt) |
| **[R]** | dbt deferral | 🎥 MicroCourse | [mở](https://learn.getdbt.com/courses/dbt-deferral) |
| **[E]** | Using defer in dbt | 📄 Resource | [mở](https://learn.getdbt.com/courses/using-defer-in-dbt) |
| **[R]** | **Advanced Deployment (4h)** — khóa quan trọng nhất của path | 🎥 Course | [mở](https://learn.getdbt.com/courses/advanced-deployment) |
| **[R]** | Using threads | 📄 Resource | [mở](https://learn.getdbt.com/courses/using-threads) |
| **[R]** | dbt metadata | 📄 Resource | [mở](https://learn.getdbt.com/courses/generating-dbt-metadata) |
| **[R]** | Deploy jobs | 📄 Resource | [mở](https://learn.getdbt.com/courses/deploy-jobs) · [docs](https://docs.getdbt.com/docs/deploy/deploy-jobs) |
| **[R]** | Advanced Continuous Integration (CI) | 📄 Resource | [mở](https://learn.getdbt.com/courses/advanced-continuous-integration-ci) · [docs](https://docs.getdbt.com/docs/deploy/advanced-ci) |

### Milestone #3 — Security and Monitoring

| | Nội dung | Loại | Link |
|---|---|---|---|
| **[R]** | dbt Authentication Fundamentals (SSO, group, invite user, MFA) | 🎥 Video | [mở](https://learn.getdbt.com/courses/dbt-authentication-fundamentals) |
| **[R]** | Service account tokens | 📄 Resource | [mở](https://learn.getdbt.com/courses/service-account-tokens) · [docs](https://docs.getdbt.com/docs/dbt-cloud-apis/service-tokens) |
| **[R]** | dbt Licenses and Permissions | 🎥 Course | [mở](https://learn.getdbt.com/courses/dbt-licenses-permissions) |
| **[R]** | Enterprise permissions | 📄 Resource | [mở](https://learn.getdbt.com/courses/enterprise-permissions) · [docs](https://docs.getdbt.com/docs/cloud/manage-access/enterprise-permissions) |
| **[E]** | Self-service Starter account permissions | 📄 Resource | [mở](https://learn.getdbt.com/courses/self-service-starter-account-permissions) |
| **[R]** | Securing your account through SSO & RBAC | 📄 Article | [mở](https://learn.getdbt.com/courses/establishing-dbt-cloud-securing-your-account-through-sso-rbac) |
| **[R]** | Job Notifications | 📄 Resource | [mở](https://learn.getdbt.com/courses/job-notifications) · [docs](https://docs.getdbt.com/docs/deploy/job-notifications) |
| **[R]** | Webhooks (~1h) | 🎥 Course | [mở](https://learn.getdbt.com/courses/webhooks) |

Study guide PDF bổ sung các khóa SSO/RBAC theo IdP (đều là 🎥 course trên dbt Learn): Role-based access control với **dbt & Okta**, SSO với **Entra ID**, SSO với **Google Workspace**, SSO với **Okta** — tìm trong [Course Catalog](https://learn.getdbt.com/catalog).

### Milestone #4 — Governance and Discovery

| | Nội dung | Loại | Link |
|---|---|---|---|
| **[R]** | dbt Mesh | 🎥 Course | [mở](https://learn.getdbt.com/courses/dbt-mesh) |
| **[R]** | Project dependencies | 📄 Resource | [mở](https://learn.getdbt.com/courses/project-dependencies) · [docs](https://docs.getdbt.com/docs/collaborate/govern/project-dependencies) |
| **[R]** | dbt Catalog | 🎥 Course | [mở](https://learn.getdbt.com/courses/dbt-catalog) |

### Milestone #5 — Exam Preparation

| | Nội dung | Loại | Link |
|---|---|---|---|
| **[R]** | dbt Cloud Architect Exam Study Guide | 📄 Resource | [mở](https://learn.getdbt.com/courses/dbt-cloud-architect-exam-study-guide) · [PDF trực tiếp](https://www.getdbt.com/dbt-assets/dbt-certificate-study-guide-for-cloud-architect) |
| **[E]** | **Pro Tips for dbt Certifications** — Hope Watson (Resident Architect) chia sẻ chiến thuật thi | 🎥 Video | [mở](https://learn.getdbt.com/courses/pro-tips-for-dbt-certifications) |

### Milestone #6 — Exam Registration

| | Nội dung | Link |
|---|---|---|
| **[E]** | Register for dbt Cloud Architect Exam | [mở](https://learn.getdbt.com/courses/register-for-dbt-cloud-architect-exam) · [Talview](https://pages.talview.com/dbtlabs/certifications/) |
| **[E]** | Learning Path Survey (5 phút) | [mở](https://learn.getdbt.com/courses/learning-path-survey) |

### Video/khóa nền tảng nên xem trước

- 🎥 [dbt Fundamentals (~5h)](https://learn.getdbt.com/courses/dbt-fundamentals) — prerequisite bắt buộc về mặt kiến thức.
- 🎥 [dbt Certified Developer Path](https://learn.getdbt.com/learning-paths/dbt-certified-developer) — nếu chưa có cert Analytics Engineering.

---

## 4. Kiến thức ôn tập chi tiết

### 4.1 Data platform connections & authentication (Topic 1)

**Kiến trúc connection**
- Connection được cấu hình ở **account level** và **tái sử dụng** được cho nhiều project và nhiều environment. Một project có thể dùng nhiều connection cùng loại warehouse.
- Hệ quả quan trọng cho thiết kế: **không cần duplicate project** cho dev/prod. Dùng *environment-level isolation* (mỗi environment trỏ connection/credential riêng).
- `extended_attributes` cho phép override các thuộc tính profile theo từng environment mà UI không expose.
- Credential được chia 2 tầng: **connection** (host, account, warehouse, database…) ở account level và **credential** (user, role, schema, key) ở từng environment / từng user.

**Cơ chế xác thực — điểm thi hay hỏi nhất**

| Cơ chế | Dùng ở đâu | Ghi chú |
|---|---|---|
| Username + password | Dev & Deployment | Đơn giản, kém an toàn nhất |
| **Key pair** (Snowflake) | Deployment (service account) | Nên **rotate định kỳ**, có thể rotate qua **Admin API** |
| **OAuth / SSO OAuth** | **Chỉ Development environment** | Token có thời hạn do platform quyết định; user phải re-authorize khi hết hạn |
| Service account / service principal | Deployment (staging, prod) | **Best practice cho mọi deployment environment** |

> Nguyên tắc phải nhớ: **không dùng SSO/OAuth cho staging và production**, vì session/token hết hạn → job tự động fail. Deployment luôn dùng **service account**.

- Set up OAuth: Snowflake OAuth, Databricks OAuth, BigQuery OAuth, External OAuth (Okta/Entra) — đều cần **Client ID + Client Secret** nhập vào dbt, cùng redirect URI của dbt.
- Phân quyền warehouse theo persona: developer có **read** trên schema production + **read/write** trên schema dev của mình; service account production có **read/write** trên schema production (bao gồm cả schema snapshot).

**Network security**
- **IP restrictions**: chỉ có trên **Enterprise+ / Virtual Private**. Cấu hình tại `Account Settings → IP Restrictions`, theo **allowlist** và **blocklist**. Chặn đồng thời service token, request API bằng personal token, và cả UI. **Phải allowlist IP của Git provider** (webhook inbound từ GitHub/GitLab/ADO) nếu không CI sẽ đứt.
- **Egress IP của dbt**: phải allowlist ở phía warehouse (Access, Regions & IP addresses).
- **PrivateLink**: yêu cầu **Business Critical (Enterprise+ / Virtual Private)**. Đây là câu trả lời cho các bài toán *data residency* / GDPR / multi-region: dựng **PrivateLink endpoint riêng cho từng region** và cấu hình nhiều project trỏ vào endpoint tương ứng — **không** cần mua thêm account, và **không** dùng cross-platform Mesh để "nối" hai region (vì mục tiêu là cô lập dữ liệu).

### 4.2 Git connections (Topic 2)

| Provider | Native integration | Automated CI job | Git clone | Plan |
|---|---|---|---|---|
| GitHub | ✅ (dbt GitHub App) | ✅ | ✅ | Mọi plan |
| GitLab | ✅ (OAuth app) | ✅ | ✅ | Mọi plan |
| Azure DevOps | ✅ (service principal — khuyến nghị; OAuth 2.0) | ✅ | ✅ | **Enterprise / Enterprise+** (Starter/Developer chỉ deploy key, không có CI tự động) |
| BitBucket, AWS CodeCommit, khác | ❌ | ❌ | ✅ | Dùng custom pipeline + Administrative API |

- **GitLab Free**: merge request vẫn trigger được CI job, nhưng **status của CI job không báo ngược lại** GitLab.
- **Git clone**: dùng SSH URL + **deploy key** do dbt sinh ra (phải cấp write access ở repo). Không có webhook → **dbt không tự drop schema CI tạm thời**; phải tự trigger CI bằng Administrative API và tự dọn schema.
- Kết nối cấp project (repo) khác với **personal git credential** của từng developer (dùng cho IDE/CLI) — developer phải tự authorize profile GitHub của mình.
- **Branching strategy**:
  - *Direct promotion*: một branch `main` duy nhất, developer branch → `main`.
  - *Indirect promotion*: có branch trung gian (`qa`/`staging`) → developer branch → `staging` → `main`. Cần **custom branch** trên environment tương ứng, branch protection rule, và quy trình **hotfix** riêng.
- **Custom branch** trên environment: bắt buộc khi environment cần checkout branch khác `main` (ví dụ staging environment dùng branch `staging`; CI environment gắn custom branch để chỉ chạy khi PR nhắm vào branch đó).

### 4.3 Environments (Topic 3)

**Phân loại**
- **Development environment**: mỗi project chỉ có **1**; phục vụ Studio IDE / CLI; cho phép OAuth.
- **Deployment environment**, có **3 type**:
  - **Production** — nơi build dữ liệu production. **Chỉ được đánh dấu 1 environment là production** cho mỗi project; đây là *source of truth* và là điều kiện bắt buộc cho **dbt Catalog** và **cross-project reference**.
  - **Staging** — cho developer tiếp cận workflow deployment nhưng giới hạn quyền trên dữ liệu production; thường gắn long-lived branch `staging`.
  - **General** — deployment dùng chung; **không nên** dùng làm production cuối cùng.

**Environment quyết định điều gì khi job chạy**: phiên bản dbt / release track, thông tin connection + target database & schema, và version code (branch) được thực thi.

**Environment variables — nhớ chính xác**
- Prefix hợp lệ: **`DBT_`**, **`DBT_ENV_SECRET_`**, **`DBT_ENV_CUSTOM_ENV_`**.
- Key được **uppercase** và **case-sensitive** — gọi `{{ env_var('DBT_KEY') }}` phải khớp tuyệt đối.
- `DBT_ENV_SECRET_*` được **scrub khỏi toàn bộ log và error message**.
- dbt có sẵn một số biến pre-defined **không thể ghi đè**.
- **Thứ tự ưu tiên (thấp → cao)**:
  1. `default` argument trong `{{ env_var('KEY', 'default') }}`
  2. **Project default**
  3. **Environment level**
  4. **Job override** hoặc **personal override** trong Studio IDE
- Suy ra: xóa job-level override → giá trị fallback về **environment level**, *không* về project default.
- Thiếu giá trị ở mọi tầng → compile error "Env var required but not provided".
- Environment variable **không đồng nghĩa** với project variable (`vars:`).

**Schema/database/target**
- Mỗi environment set **target schema/dataset** riêng → cùng một job materialize vào schema khác nhau theo environment. Đây là cơ chế chính.
- Muốn logic phức tạp hơn thì **override macro `generate_schema_name`** (và `generate_database_name`, `generate_alias_name`).
- `+schema:` trong model config chỉ là **suffix custom schema**, tự nó không thay đổi theo environment.
- **Custom target name** (`{{ target.name }}`) để code rẽ nhánh theo ngữ cảnh (ví dụ CI chỉ xử lý subset dữ liệu).

**Deferral (defer)**
- Defer cho phép build **chỉ model đã thay đổi**, các parent không đổi được **resolve từ manifest của environment khác** thay vì build lại.
- Cần **manifest từ lần invoke trước** (`--state`, và có thể tách `--defer-state`). Kết hợp với selector `state:modified+` → "Slim CI".
- Trong dbt platform: bật *defer to another environment* trên environment (cho IDE/CLI dev) hoặc trên job (*Compare changes against an environment*).
- **Thứ tự resolve**: dbt ưu tiên object tồn tại trong schema đích của run hiện tại; chỉ những node chưa có mới lấy từ environment được defer.
- **Self-deferral**: job defer về **artifact của chính nó** (lần run thành công gần nhất) — dùng khi không có production environment phù hợp để so sánh.
- **defer vs `dbt clone`**: clone tạo bản copy (zero-copy nếu platform hỗ trợ) các object production sang schema dev — dùng khi cần object thật sự tồn tại; defer chỉ trỏ reference, rẻ hơn.
- **Threads**: điều khiển mức song song của connection. Tăng threads → chạy nhanh hơn nhưng tiêu concurrency của warehouse. Default job trong dbt platform là **4**.

### 4.4 Jobs (Topic 4)

**Các loại job và trigger**

| Loại | Trigger |
|---|---|
| **Deploy job** | Schedule (chọn ngày/giờ) · **custom cron** · **trigger on job completion** (job chaining) · API · Run now |
| **CI job** | Pull request được mở / có commit mới (có option *Run on draft PR*) |
| **Merge job** | Khi PR được merge vào branch (continuous deployment) |

- Scheduler dùng **UTC**, **không** tự điều chỉnh theo timezone hay DST.
- **Job chaining**: một job chạy sau khi job upstream hoàn tất (Starter trở lên); dùng để tách staging → production, hoặc phối hợp job giữa các project trong Mesh.

**Cấu hình bên trong job**
- **Commands**: `dbt deps` chạy tự động ở đầu run. Best practice: một step một mục đích — `dbt build --select ...` rồi `dbt test`/snapshot/seed/full-refresh tách riêng để dễ khoanh vùng lỗi.
- Checkbox **Run source freshness**: chạy `dbt source freshness` **trước** các command khác.
- Checkbox **Generate docs on run**: sinh artifact docs → **populate dbt Catalog**. Nên bật ở job production; **không** nên bật ở CI job.
- Advanced settings: **environment variable override**, **target name**, **dbt version override** (chỉ nên dùng khi đang nâng version), **threads**, **run timeout**.
- Artifact quan trọng: `manifest.json` (logical state), `run_results.json`, `catalog.json`.

**CI job — cấu hình chuẩn**
- Command mặc định: `dbt build --select state:modified+`.
- **State comparison chỉ hoạt động khi có deferred environment** để so sánh → mặc định defer về **Production**.
- Build vào **schema tạm riêng cho từng PR**; dbt tự drop schema khi PR đóng/merge **chỉ khi** dùng native git integration (webhook). Trigger qua API thì phải tự dọn.
- Nên đặt CI job trong **deployment environment riêng** trỏ database staging để cô lập khỏi production.
- Tính năng kèm theo: **concurrent CI checks**, **smart cancellation of stale builds** (Starter/Enterprise+), **SQL linting bằng SQLFluff** (chạy như bước đầu, chọn *stop* hoặc *continue on error*).
- Trigger CI bằng API: `job_type: ci` + payload cần `github_pull_request_id` / `gitlab_merge_request_id` / `azure_devops_pull_request_id` / `non_native_pull_request_id`, kèm `git_sha` hoặc `git_branch`.
- **Semantic validation trong CI**: `dbt sl validate --select state:modified+`.

**Advanced CI — compare changes**
- Yêu cầu: **Enterprise-tier** + feature được admin bật → checkbox **`dbt compare`** xuất hiện trong CI job.
- Platform hỗ trợ: BigQuery, Databricks, Postgres, Redshift, Snowflake.
- So sánh **last applied state của production environment** với **commit mới nhất của PR**, mỗi lần mở PR hoặc push commit.
- Báo cáo thay đổi ở **primary key, row, column**; xem ở tab **Compare** trong job run details, đồng thời tóm tắt thành **comment trên PR** ở Git provider.
- Cần **primary key constraint** hoặc **uniqueness test** để phân tích ở mức record; nếu không sẽ báo "Primary key missing".
- Cấu hình `event_time` trên model/seed/snapshot/source → so sánh **chỉ khoảng thời gian giao nhau**, tránh báo sai "deleted rows" khi CI chỉ build subset, hoặc "new rows" khi CI có dữ liệu mới hơn prod.
- Cache: tối đa **100 record mẫu/model đã đổi**, lưu tối đa **30 ngày**, mã hóa, lưu ở region của account. Xem run cũ hơn 30 ngày → thông báo dữ liệu đã hết hạn.
- Timeout mặc định khi bật `dbt compare`: **3600s**.
- Giới hạn: CI model và production model **phải cùng database host/connection**, nếu defer sang environment ở host khác thì compare không hoạt động.

**Hooks (dbt Labs không đưa vào study guide nhưng đề có hỏi)**
- `pre-hook` / `post-hook` ở mức model; `on-run-start` / `on-run-end` ở mức project.
- Điểm bẫy: hook **không** giải quyết được vấn đề phân quyền ghi, vì credential deployment cần quyền write **trước** khi tạo/alter table. Grant bằng hook chỉ xử lý được việc cấp quyền *sau khi* object đã tồn tại.

**Source freshness (cũng bị hỏi sâu hơn mong đợi)**
- Khai báo `loaded_at_field` + `freshness: {warn_after, error_after}` ở source (hoặc dùng metadata-based freshness của warehouse).
- `dbt source freshness` sinh `sources.json`; kết quả hiển thị trong Catalog và có thể trigger **notification loại Warns**.

### 4.5 Security, licenses & RBAC (Topic 5)

**License type (mua theo seat)** — `Developer`, `Read-only`, `IT`.
> **License luôn override permission set của group.** Một user license Read-only nằm trong group Account Admin vẫn **không** làm được hành động admin.

**Group + permission set = RBAC**
- Permission set gán cho **group**, group gán cho **user** (hoặc map từ IdP). Một group có thể có nhiều permission set; **quyền cao hơn thắng**.
- Group mặc định: **Owner** (Account admin), **Member** (Admin), **Everyone**.
- Chia làm 2 loại: **account-level** (quản trị account: invite user, SSO, tạo group, billing) và **project-level** (environment, IDE, job).

Bảng permission set (Enterprise / Enterprise+) — cần phân biệt được, đề hay hỏi dạng matching:

| Permission set | Cấp | Điểm đặc trưng |
|---|---|---|
| **Account admin** | Account | Quyền cao nhất, không giới hạn. Default cho người tạo account và group Owner |
| **Admin** | **Project** | Toàn quyền trên project **đã có**, không tạo được project mới; invite được user nhưng **không tạo group**. Default của group Member |
| **Project creator** | Account | Set duy nhất ngoài Account admin **tạo được project mới**; tạo/sửa connection, invite user, tạo group, gán license |
| **Account viewer** | Account | Read-only toàn account **bao gồm audit log** (nội dung sensitive). Không vào IDE |
| **Stakeholder / Read-Only** | Project | Giống Account viewer nhưng **không** thấy account settings, billing, audit log sensitive |
| **Security admin** | Account | User, group, license, **authentication & SSO**, **IP restrictions**, xem service token. Không có job/run/environment/IDE. Là default của **license IT** |
| **Billing admin** | Account | Chỉ khu vực Billing |
| **Analyst** | Project | Toàn quyền IDE + tự cấu hình personal credential; **read-only** environment config; xem job nhưng không sửa |
| **Developer** | Project | Tạo/sửa/test code trong IDE; read-only trên environment, job, run, Git config. ⚠️ **Khác** với *Developer license* |
| **Database admin** | Project | Write trên **data platform config trong environment** (credential, warehouse, schema) + environment variable + Semantic Layer; read-only trên connection/repo/job |
| **Git admin** | Project | Tạo Git integration, tạo environment variable, sửa project settings; **không có IDE**; read-only account settings |
| **Job admin** | Project | Tạo/sửa **job, run, environment variable, data warehouse config**; set up project integration; read-only project config |
| **Job creator** | Project | Tạo/sửa/chạy job trong project & environment được gán; **không tạo/xóa environment, không sửa env var** |
| **Job runner** | Project | Chỉ chạy job + xem kết quả |
| **Job viewer** | Project | Chỉ đọc kết quả/status/log của job |
| **Team admin** | Project | Quản lý project cho một team; read-only nhiều account settings (trừ billing, auth provider). Có thể mở rộng qua **environment-level permission** |
| **Metadata** | Project | Chỉ read metadata qua **Discovery API** |
| **Notification Manager** | Account | Quản lý rule notification (Slack/Teams/email) trên **toàn account** mà không cần Account admin; **không** connect/disconnect được Slack/Teams (việc đó chỉ Account admin) |
| **Semantic Layer** | Project | Chỉ query Semantic Layer (dùng cho service token) |
| **Cost Insights Admin / Viewer** | Cả hai | Cấu hình / xem dữ liệu Cost Insights |
| **Fusion admin** | — | Thực hiện Fusion upgrade; **chỉ gán cho user, không gán cho service token** |
| **Analyst read** (private beta) | Project | Read-only + `user_credential_write` để tự quản credential mà không có IDE |
| **Manage marketplace apps** | Account | Dành cho marketplace app (Snowflake Native App) |

> Phân biệt hay bị hỏi: **Git admin** (tạo Git integration + env var, không có IDE) ↔ **Team admin** (quản lý project cho team, read-only phần lớn account settings) ↔ **Job admin** (sửa được cả env var và warehouse config) ↔ **Job creator** (không sửa được env var/environment).

**SSO & provisioning**
- Hỗ trợ: **SAML 2.0** (generic), **Okta**, **Google Workspace**, **Microsoft Entra ID**; tài liệu migration sang **Auth0**.
- **JIT provisioning**: user được tạo trong dbt lần đầu login qua IdP; hỗ trợ **IdP-initiated login**; account có **login slug** riêng, có thể **enforce SSO**.
- **SCIM** (Okta, Entra ID): tự động provision/deprovision user và **tự gán license** — đây là đáp án cho bài toán "onboard nhân viên mới tự động nhận license Developer + vào group Analytics".
- **License mapping**: map group/attribute từ IdP → license type trong dbt.
- **MFA** cấu hình ở phía IdP.

**Token**
- **Service account token**: thuộc **account**, không thuộc user. Gán được **bất kỳ permission set** nào (Enterprise); phạm vi **toàn bộ project** hoặc **project cụ thể**; gán được nhiều permission set cho 1 token.
  - Tạo token cần: **license Developer** + **permission Account admin**.
  - Token **chỉ hiện 1 lần** khi tạo → lưu ngay. Rotate định kỳ; sau khi rotate phải verify job vẫn chạy.
  - Starter/Developer plan chỉ gán được Semantic Layer; legacy Team plan giới hạn ở Account Admin, Member, Job Admin, Read-Only, Metadata, Semantic Layer.
- **Personal access token (PAT)**: thay mặt user, kế thừa quyền của user đó → không dùng cho automation.
- **Audit log**: Enterprise, dùng để truy vết thay đổi cấu hình.

### 4.6 Monitoring & alerting (Topic 6)

**Job notifications**
- 4 outcome: **Succeeds**, **Warns**, **Fails**, **Is canceled**.
  - **Warns** được kích hoạt bởi **log level warning từ data test hoặc source freshness**, không phải bởi status tổng thể của run → một job "success" trên UI vẫn có thể bắn notification Warns.
- Channel: **Email**, **Slack (user-linked)**, **Slack (account-level)**, **Microsoft Teams**. Không dùng được Teams native thì gửi qua **email của channel** (external email).
- Quyền: developer user tự set cho mình; cấu hình rộng hơn cần **Account Admin / Owner / Member** hoặc permission set **Notification Manager**.

**Webhooks (outbound, event-driven)**
- 3 event: **`job.run.started`**, **`job.run.completed`** (bao gồm cả thành công và thất bại), **`job.run.errored`**.
- Tạo qua **UI** hoặc **API**. dbt gửi **JSON payload** tới endpoint URL của bạn.
- dbt **retry 5 lần**; log delivery lưu **7 ngày** (mục *Recent Deliveries*); **timeout 10 giây** — endpoint trả lời sau 10s sẽ bị coi là fail dù client tự cho là thành công.
- Nên verify payload bằng **HMAC signature** trong header.
- Quyền write webhook (Enterprise): **Account Admin, Admin, hoặc Developer** — giống nhau cho cả UI và service token.
- **Webhook vs polling**: cần trigger pipeline ngoài (Airflow…) ngay khi job xong → **webhook `job.run.completed`**, không polling Admin API theo chu kỳ. Job chaining chỉ hoạt động **trong dbt**, không trigger được DAG bên ngoài.
- Ứng dụng thường gặp: mở incident PagerDuty, push Slack/Teams, kick off DAG downstream.
- Giám sát sâu hơn: **Discovery API** (metadata, freshness, test result) + **Administrative API** (run history, trigger).
- Best practice vận hành: routing khác nhau cho prod vs staging; theo dõi trend run duration; job backup trễ 1 tiếng cho pipeline critical.

### 4.7 dbt Mesh & model governance (Topic 7)

**Model governance = 3 trụ**

1. **`access`** — access modifier trên model:

| access | Được `ref` từ |
|---|---|
| `private` | Cùng **group** |
| `protected` | Cùng **project** (hoặc project cài project đó như package) — **default** |
| `public` | Bất kỳ group, package, project nào. Sau khi đổi phải **chạy lại job production** để áp dụng |

2. **`groups`** — gom model theo owner/domain, mỗi model thuộc **đúng 1 group**, group **không nested**; set được ở mức thư mục trong `dbt_project.yml`, config trong model sẽ override.
3. **`contracts`** + **`versions`** — contract (`enforced: true` + `data_type`/constraints) chặn breaking change; versioning (`v1`, `v2`, `latest_version`, `deprecation_date`) cho phép deprecate có kiểm soát. Coi public model như **API**.

> Lưu ý: governance feature chỉ áp dụng cho **model**, không áp dụng cho snapshot, seed, source.

**Cross-project reference**
- Khai báo trong **`dependencies.yml`** (khác `packages.yml`):
  ```yaml
  projects:
    - name: jaffle_finance
  ```
  rồi `ref` 2 đối số: `{{ ref('jaffle_finance', 'fct_orders') }}` (có thể kèm version).
- **Package** = pull toàn bộ source code vào project mình. **Project dependency** = dbt resolve reference **on-the-fly** qua metadata service; bạn không parse/run model upstream, chỉ tiêu thụ nó như một dataset API.

**Điều kiện bắt buộc để cross-project ref hoạt động (rất hay ra đề)**
- Enterprise / Enterprise+.
- Model upstream có **`access: public`** và đã có **ít nhất 1 job run thành công sau khi** khai báo access.
- Project upstream có **Production deployment environment** và **≥1 deploy job chạy thành công** ở đó để sinh **`manifest.json`**.
- Nếu project upstream có **Staging environment** thì cũng cần ≥1 deploy job thành công ở đó để reference resolve đúng.
- **Tên project phải unique trong account** và **case-sensitive** — `dbt_project.yml` phải khớp chính xác với `dependencies.yml` (`jaffle_marketing` ≠ `JAFFLE_MARKETING`).
- Không tách project theo môi trường (đừng tạo `X - Dev` và `X - Prod`); dùng **environment-level isolation** + **Connections**.

**Khác**
- **Bidirectional dependency ở mức project** là hợp lệ, miễn không tạo cycle ở mức model.
- **Cross-platform Mesh**: reference giữa các project nằm trên các data platform khác nhau. Nhưng nếu yêu cầu là **cô lập dữ liệu theo region** thì cross-platform Mesh là lựa chọn **sai**.
- **Hybrid Mesh**: kết hợp project dbt Core (self-hosted) với dbt platform.

### 4.8 dbt Catalog (Topic 8) — trước đây tên là dbt Explorer

**Điều kiện**
- Plan Starter / Enterprise / Enterprise+.
- Mỗi project cần **production hoặc staging deployment environment**.
- Cần **≥1 job run thành công** trong environment đó. **CI job không cập nhật Catalog.**
- Muốn có docs đầy đủ → bật **Generate docs on run** trong job production.

**Dùng để làm gì**
- Xem toàn bộ **resource** (model, test, source, metric, exposure) ở **latest production state**.
- **Lineage** cấp model và **column-level lineage**; **project-level lineage** khi dùng Mesh.
- Tra **public model** và **cross-project reference** — nơi team downstream đi tìm "API" để consume.
- **Model performance** và **recommendations** → phục vụ tối ưu cost/performance.
- Trạng thái **test**, **source freshness**, **owner/group**, **contract/version**.
- Troubleshoot bằng cách đi lên/xuống lineage thay vì đoán.
- Metadata được surface qua **Discovery API**; có thể **ingest metadata warehouse bên ngoài** để thấy cả asset không định nghĩa trong dbt. Auto-exposure với Tableau.

---

## 5. 10 câu hỏi mẫu chính thức

Nguồn: [trang kỳ thi dbt Labs](https://www.getdbt.com/certifications/dbt-architect-certification-exam#sample-questions) và Study Guide PDF (4 câu đầu). ✅ = đáp án đúng.

### Câu 1 — Kết nối & xác thực
**Vì sao nên tránh dùng connection kiểu SSO cho staging và production deployment environment?**

- ✅ **A.** Chúng dựa trên session xác thực có thể hết hạn hoặc cần re-authenticate → job trong pipeline tự động sẽ fail bất ngờ.
- B. Không kết nối được cloud warehouse do giao thức xác thực không tương thích.
- C. Chúng chặn khả năng quản lý environment variable cần cho production.
- D. Chỉ user có role Account Admin dùng được.

**Giải thích**: dbt chỉ hỗ trợ OAuth ở **Development environment**. Sau khi user authorize qua IdP, dbt nhận access token để mở connection và chạy query trong Studio. **Thời hạn token do data platform quyết định**; hết hạn thì user phải authorize lại. Vì vậy deployment credential nên là **service account**. B sai vì kỹ thuật vẫn kết nối được, chỉ là không nên nên dbt không cho phép. C sai vì cách xác thực không liên quan tới env var. D sai vì bất kỳ user có **Developer license** đều dùng được SSO OAuth, bất kể permission.

### Câu 2 — Phân quyền theo environment
**Snapshot có `target_schema` = `prod_snapshot`. Muốn developer *read* được `prod_schema` ở dev nhưng job production có *read + write*. Làm thế nào?**

- A. Dùng `post-hook` để grant quyền trong snapshot config.
- ✅ **B.** Dùng **service account có read + write** trong setting của deployment environment.
- C. Dùng `on-run-end` để grant quyền trong snapshot config.
- D. Gán developer role **Job Admin**.

**Giải thích**: Bản chất là user/service account khác nhau phải có quyền khác nhau trên object khác nhau. Developer: read `prod_schema`, không write `prod_snapshot`. Credential deployment production: read + write cả hai. Giải pháp gọn là **credential riêng cho từng environment** + grant tương ứng trong data platform. A và C sai vì credential production cần quyền write **trước** khi tạo/alter table trong `prod_snapshot` — grant sau đó không giải quyết được yêu cầu. D sai vì **Job Admin** cho phép tạo/sửa job, run, env var, warehouse config nhưng **không** ảnh hưởng tới quyền cá nhân của user trên object trong database.

### Câu 3 — Precedence của environment variable

| Key | Project Default | Production | Development |
|---|---|---|---|
| `DBT_ENV_VALUE` | `not_set` | `prod` | `dev` |

Trong job có override biến này thành `finance`. **Nếu xóa cấu hình job-level, giá trị nào được dùng?**

- A. Project default `not_set`
- B. `default` argument của hàm Jinja `env_var` trong code
- ✅ **C.** Giá trị gán ở **environment** mà job đó chạy
- D. Env var ở job level là bắt buộc, không xóa được

**Giải thích**: Project Default dùng làm catch-all/token chung toàn project. Giá trị ở **environment level cao hơn project default**. Job **kế thừa** giá trị environment, job-level override thắng khi tồn tại; xóa override → fallback về environment (ở đây là `prod`). A sai vì Project Default thấp hơn environment. B sai vì `default` argument của Jinja thấp hơn cả Project Default và environment. D sai vì override job-level không bắt buộc.

### Câu 4 — Environment variables (chọn 2)
**Điều nào đúng về environment variables?**

- ✅ Env var trong dbt phải có prefix **`DBT_`**, **`DBT_ENV_SECRET_`** hoặc **`DBT_ENV_CUSTOM_ENV_`**.
- ✗ Prefix là `DBT_`, `DBT_SECRET_ENV` hoặc `DBT_CUSTOM_ENV_`.
- ✗ Key của env var **không phân biệt** chữ hoa/thường.
- ✗ dbt có sẵn một số biến pre-defined **có thể** ghi đè.
- ✅ dbt có sẵn một số biến pre-defined **không thể** ghi đè.
- ✗ Environment variable và project variable là như nhau.

**Giải thích**: dbt bắt buộc các prefix này để phân tách mối quan tâm — dbt không thể quét mọi env var của hệ thống nên dùng namespace để biết biến nào "opt-in" cho việc redact, thu metadata hay dùng chung. Key được uppercase theo quy ước để tránh nhập nhằng.

### Câu 5 — Schema theo environment (chọn 2)
**Muốn object materialize vào schema khác nhau cho mỗi deployment environment. Cách nào?**

- ✗ Định nghĩa `custom_schema` trong config block của từng model.
- ✅ **Đặt target schema khi cấu hình environment.**
- ✅ **Dùng/override macro `generate_schema_name`.**
- ✗ Đặt target schema trong job settings.
- ✗ Dùng macro `handle_existing_table`.

**Giải thích**: dbt resolve schema bằng cách kết hợp **target schema** với logic custom schema. Target schema theo environment là cơ chế chính (dev/staging/prod mỗi cái một schema). Override `generate_schema_name` cho phép tùy biến hoàn toàn logic đó. `custom_schema` ở model config chỉ tạo suffix, tự nó không đổi theo environment. Target schema ở job level ghi đè environment nhưng là chuyện của job, không phải của environment. `handle_existing_table` **không phải macro thật** của dbt — đây là distractor.

### Câu 6 — Deferral
**Team có production deployment environment, muốn developer chạy `dbt build --select state:modified+` đối chiếu state production — chỉ build model đã đổi, không build lại upstream không đổi. Architect cần cấu hình gì?**

- ✗ Clone schema production sang schema riêng của developer bằng post-hook.
- ✅ **Bật deferral trên development environment, trỏ tới production làm deferred environment.**
- ✗ Set custom branch trên production environment cho developer target vào.
- ✗ Dùng env var override trên job của từng developer để trỏ schema prod.

**Giải thích**: Deferral cho phép dbt resolve các model không đổi từ **manifest của production environment**, nên developer chỉ build model đã đổi và các dependent phía dưới.

### Câu 7 — CI job
**Khi PR được mở, dbt cần chỉ chạy model đã đổi + downstream, và so sánh với state production thay vì build lại toàn bộ. Cấu hình job nào?**

- ✗ Scheduled job với `dbt build --select state:modified+` và bật self-deferral.
- ✅ **CI job có deferral trỏ tới production environment, command `dbt build --select state:modified+`.**
- ✗ Merge job chạy `dbt run --full-refresh` mỗi PR.
- ✗ Triggered job qua webhook chỉ chạy `dbt test`.

**Giải thích**: **CI job** là loại job được thiết kế cho trigger từ pull request; cấu hình deferral tới production đảm bảo job chỉ build model đã thay đổi, so sánh với manifest production.

### Câu 8 — SSO / SCIM / RBAC
**Tổ chức dùng Okta làm IdP. Muốn nhân viên mới login qua SSO **tự động** nhận license "Developer" và vào group "Analytics" mà không cần can thiệp thủ công.**

- ✗ Tạo service token role Developer rồi chia sẻ cho nhân viên mới.
- ✅ **Thiết lập SCIM provisioning + cấu hình license mapping và RBAC group assignment gắn với attribute của Okta.**
- ✗ Yêu cầu user tự đăng ký rồi gửi request xin license.
- ✗ Đặt default license của account là Developer để mọi user SSO tự kế thừa, không cần RBAC.

**Giải thích**: **SCIM** xử lý provisioning/deprovisioning tự động; kết hợp **license mapping** và **RBAC rule** đảm bảo user nhận đúng license và đúng group dựa trên attribute Okta.

### Câu 9 — dbt Mesh
**Project downstream cần `ref` một model của project upstream trong dbt Mesh. Model upstream đang là `access: protected`. Chủ project upstream phải đổi gì?**

- ✗ Set `access: public` và khai báo nó trong `sources.yml` của project upstream.
- ✅ **Set `access: public` và đảm bảo environment upstream được cấu hình là environment type Production.**
- ✗ Set `access: private` và thêm project downstream vào allowlist.
- ✗ Không cần đổi gì — mọi model đều ref được cross-project bất kể access level.

**Giải thích**: Cross-project reference trong Mesh yêu cầu model có **`access: public`**. Environment upstream cũng phải là **environment type production** để dbt resolve được cross-project ref lúc runtime.

### Câu 10 — Webhooks vs polling
**Muốn trigger pipeline downstream ở orchestration tool bên ngoài (ví dụ Airflow) ngay khi job dbt thành công, mà không polling dbt API theo schedule. Cách khuyến nghị?**

- ✗ Bật email notification rồi để Airflow parse inbox.
- ✗ Dùng dbt API poll status job mỗi 60 giây từ Airflow.
- ✅ **Cấu hình webhook trên job dbt để gửi event `job.completed` tới REST API endpoint của Airflow.**
- ✗ Dùng job chaining trong dbt để trigger Airflow DAG như một job step cuối.

**Giải thích**: Webhook là cơ chế integration event-driven của dbt. Cấu hình webhook cho event job completed sẽ **push** notification tới endpoint bên ngoài ngay khi job kết thúc, loại bỏ nhu cầu polling.

---

## 6. Những vùng dễ mất điểm nhất

Tổng hợp từ chia sẻ của người đã thi đạt ([Nikita Volynets](https://nikitavolynets.substack.com/p/how-to-pass-dbt-cloud-architect-exam), [Daniel Bostrom](https://www.thedataschool.co.uk/daniel-bostrom/dbt-architect-certification)) — nội dung đã diễn giải lại:

1. **Permissions.** Câu hỏi rất nhiều và rất chi tiết. Phải phân biệt được **Git Admin vs Team Admin vs Job Admin vs Job Creator**, và biết set nào là **account-level** vs **project-level**. Học kỹ trang [Enterprise permissions](https://docs.getdbt.com/docs/cloud/manage-access/enterprise-permissions).
2. **Job configuration & source freshness.** Đề hỏi sâu hơn mức mà learning path dạy — nhất là **source freshness** và **docs on run** hoạt động thế nào khi bật, cùng khác biệt giữa **CI job và production job**.
3. **Environments & defer.** `defer` dùng environment nào, khác biệt dev/staging/prod và cách chúng tương tác. Nhớ cả **self-deferral** và khi nào chọn cái nào.
4. **Advanced CI.** "Compare changes" so sánh **cái gì với cái gì**, output ra đâu, giới hạn ra sao.
5. **dbt Mesh.** Bidirectional dependency, các bước thiết lập, cấu hình job xuyên project, environment giữa các project tương tác thế nào. Đây là phần khó nếu chưa từng làm tay.
6. **Hooks.** Không nằm trong study guide nhưng xuất hiện trong câu hỏi mẫu chính thức (câu 2) — đọc `pre-hook`/`post-hook`/`on-run-start`/`on-run-end`.
7. Learning path chỉ dạy **core concept**; đề thi hỏi mức **chi tiết của docs**. Ví dụ: path dạy best practice về RBAC, nhưng đề hỏi **tên chính xác của permission set**. → Bắt buộc đọc các trang docs được link trong study guide.

---

## 7. Kế hoạch ôn 4–6 tuần

| Tuần | Việc cần làm | Deliverable |
|---|---|---|
| 0 | Hoàn thành **dbt Fundamentals**. Đọc study guide PDF từ đầu đến cuối. Dựng sandbox dbt (trial/dev account) để phá thoải mái | Danh sách điểm yếu của bản thân |
| 1 | Milestone #1: connections, OAuth, IP restriction, kết nối Git 3 provider. Đọc docs: About data platform connections, Access/Regions/IP, Set up Snowflake/Databricks/BigQuery/external OAuth | Project kết nối xong, biết diễn giải pattern auth cho từng environment |
| 2 | Milestone #2 phần environment: tạo dev/staging/prod, custom branch, env var 4 tầng precedence, custom schema/target. Khóa **dbt Environments** | 3 environment chạy được + tài liệu branch strategy |
| 3 | Milestone #2 phần job: khóa **Advanced Deployment (4h)**, deploy job, cron, job chaining, CI job, deferral, self-deferral, Advanced CI, threads | Runbook mô tả job chaining + cách defer hoạt động |
| 4 | Milestone #3: license & permission set (học bảng thuộc lòng), SSO, SCIM, license mapping, service token + rotate, notification, webhook | Checklist audit RBAC/token; 1 webhook bắn khi job fail |
| 5 | Milestone #4: dựng Mesh 2 project (producer/consumer), `access: public`, `dependencies.yml`, contract + version; bật generate docs, khám phá Catalog + column-level lineage | Lineage xuyên 2 project trong Catalog |
| 6 | Ôn lại 8 topic, làm 10 câu mẫu có bấm thời gian, xem 🎥 [Pro Tips for dbt Certifications](https://learn.getdbt.com/courses/pro-tips-for-dbt-certifications). Diễn tập sự cố: xoay token/phá environment rồi phục hồi trong 15 phút. Đăng ký thi trên Talview + system check | Lịch thi đã book |

**Mẹo học chủ động**: nạp các link trong study guide vào NotebookLM (hoặc công cụ tương tự) và bắt nó quiz bạn. Câu hỏi sẽ dễ hơn đề thật, nhưng rất hiệu quả để lộ ra lỗ hổng. Cách khác: đọc từng trang docs rồi **viết lại bằng lời của mình** — hiệu quả hơn hẳn chỉ đọc.

### Checklist tuần cuối

- [ ] Phân biệt được **defer** và **self-deferral**, biết khi nào dùng cái nào
- [ ] Giải thích được **Advanced CI** so sánh gì, cần điều kiện gì (Enterprise, `dbt compare`, primary key/uniqueness test)
- [ ] Nhớ chính xác 3 prefix env var và **thứ tự precedence 4 tầng**
- [ ] Nhớ 3 event webhook, retry 5 lần, log 7 ngày, timeout 10s
- [ ] Nhớ 4 outcome notification và Warns đến từ đâu
- [ ] Đọc thuộc bảng permission set, phân biệt account-level vs project-level
- [ ] Biết **license override group permission**
- [ ] Tạo được và rotate được service token, verify job vẫn chạy sau khi rotate
- [ ] Cấu hình được RBAC cho team mới + map SSO group → role (SCIM)
- [ ] Publish được model cross-project và xác nhận lineage trong Catalog (nhớ 3 điều kiện: `access: public`, production env, ≥1 job run thành công)
- [ ] Nhớ **Catalog không được cập nhật bởi CI job**
- [ ] Nhớ **OAuth chỉ cho development**, deployment dùng service account
- [ ] Nhớ **PrivateLink = Business Critical**, IP restriction = Enterprise+
- [ ] Giải thích được branching strategy và branch protection của mình
- [ ] Làm 10 câu mẫu có bấm giờ (< 2 phút/câu)
- [ ] Đã book Talview, chạy system check, chuẩn bị phòng yên tĩnh + phương án dự phòng điện/internet

---

## 8. Nguồn tham khảo

**Chính thức dbt Labs**
- [dbt Certified Architect Path (learning path đầy đủ)](https://learn.getdbt.com/learn/learning-path/dbt-certified-cloud-architect)
- [Trang kỳ thi + 10 câu mẫu](https://www.getdbt.com/certifications/dbt-architect-certification-exam)
- [Study Guide PDF (v6.3)](https://www.getdbt.com/dbt-assets/dbt-certificate-study-guide-for-cloud-architect)
- [Blog ra mắt chứng chỉ](https://www.getdbt.com/blog/introducing-the-new-cloud-architect-certification)
- [Đăng ký thi — Talview](https://pages.talview.com/dbtlabs/certifications/) · Email: `certification@dbtlabs.com`
- [Course Catalog dbt Learn](https://learn.getdbt.com/catalog)

**Docs cần đọc (theo study guide)**
- Connections: [About data platform connections](https://docs.getdbt.com/docs/cloud/connect-data-platform/about-connections) · [Access, Regions & IP addresses](https://docs.getdbt.com/docs/cloud/about-cloud/access-regions-ip-addresses) · [IP restrictions](https://docs.getdbt.com/docs/cloud/secure/ip-restrictions)
- Git: [Connect to GitHub](https://docs.getdbt.com/docs/cloud/git/connect-github) · [GitLab](https://docs.getdbt.com/docs/cloud/git/connect-gitlab) · [Azure DevOps](https://docs.getdbt.com/docs/cloud/git/connect-azure-devops) · [Git clone](https://docs.getdbt.com/docs/cloud/git/import-a-project-by-git-url)
- Environments: [Deployment environments](https://docs.getdbt.com/docs/deploy/deploy-environments) · [Environment variables](https://docs.getdbt.com/docs/build/environment-variables) · [Custom schemas](https://docs.getdbt.com/docs/build/custom-schemas) · [Defer](https://docs.getdbt.com/reference/node-selection/defer) · [Using threads](https://docs.getdbt.com/docs/running-a-dbt-project/using-threads)
- Jobs/CI: [Deploy jobs](https://docs.getdbt.com/docs/deploy/deploy-jobs) · [CI jobs](https://docs.getdbt.com/docs/deploy/ci-jobs) · [Advanced CI](https://docs.getdbt.com/docs/deploy/advanced-ci) · [Job scheduler](https://docs.getdbt.com/docs/deploy/job-scheduler) · [Merge jobs](https://docs.getdbt.com/docs/deploy/merge-jobs) · [Source freshness](https://docs.getdbt.com/docs/deploy/source-freshness) · [Hooks](https://docs.getdbt.com/docs/build/hooks-operations)
- Security: [Enterprise permissions](https://docs.getdbt.com/docs/cloud/manage-access/enterprise-permissions) · [About user access](https://docs.getdbt.com/docs/cloud/manage-access/about-user-access) · [Users and licenses](https://docs.getdbt.com/docs/cloud/manage-access/seats-and-users) · [Service account tokens](https://docs.getdbt.com/docs/dbt-cloud-apis/service-tokens) · [SSO overview](https://docs.getdbt.com/docs/cloud/manage-access/sso-overview) · [SCIM](https://docs.getdbt.com/docs/platform/manage-access/scim) ([Okta](https://docs.getdbt.com/docs/platform/manage-access/scim-okta) · [Entra ID](https://docs.getdbt.com/docs/platform/manage-access/scim-entra-id) · [quản lý license qua SCIM](https://docs.getdbt.com/docs/platform/manage-access/scim-manage-user-licenses))
- Monitoring: [Job notifications](https://docs.getdbt.com/docs/deploy/job-notifications) · [Webhooks](https://docs.getdbt.com/docs/deploy/webhooks)
- Governance: [Intro to dbt Mesh](https://docs.getdbt.com/best-practices/how-we-mesh/mesh-1-intro) · [Project dependencies](https://docs.getdbt.com/docs/collaborate/govern/project-dependencies) · [Model access](https://docs.getdbt.com/docs/collaborate/govern/model-access) · [Model contracts](https://docs.getdbt.com/docs/collaborate/govern/model-contracts) · [Model versions](https://docs.getdbt.com/docs/collaborate/govern/model-versions) · [Discover data with Catalog](https://docs.getdbt.com/docs/collaborate/explore-projects) · [Quickstart with dbt Mesh](https://docs.getdbt.com/guides/mesh-qs)

**Kinh nghiệm cộng đồng**
- [How to pass dbt Cloud Architect exam — Nikita Volynets](https://nikitavolynets.substack.com/p/how-to-pass-dbt-cloud-architect-exam)
- [dbt Architect Certification — Daniel Bostrom, The Data School](https://www.thedataschool.co.uk/daniel-bostrom/dbt-architect-certification)
- [dbt Architect Certification: Complete 2025 Study Guide — FlashGenius](https://flashgenius.net/blog-article/dbt-architect-certification-the-complete-2025-study-guide)
- dbt Slack: `#dbt-certification`, `#learn-on-demand`, `#advice-dbt-for-power-users`, `#dbt-deployment-and-orchestration`

> *Content was rephrased for compliance with licensing restrictions.*
