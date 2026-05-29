# Skills - AI Training Files

Thư mục chứa các skill files (.md) dùng để huấn luyện AI assistant.

## Format chuẩn

Mỗi skill file nên tuân theo cấu trúc sau:

```markdown
---
name: Tên skill
category: coding | analysis | architecture | governance
level: beginner | intermediate | advanced
roles: [data-engineer, data-analyst, ...]
---

# Tên Skill

## Mô tả
Mô tả ngắn gọn skill này làm gì, khi nào cần dùng.

## Ngữ cảnh áp dụng
Liệt kê các tình huống AI nên kích hoạt skill này.

## Hướng dẫn chi tiết
Các quy tắc, pattern, best practices cụ thể.

## Ví dụ
Input/Output mẫu để AI học theo.
```

## Cách tổ chức

```
skills/
├── coding/          # Kỹ năng lập trình (SQL, Python, dbt)
├── analysis/        # Kỹ năng phân tích
├── architecture/    # Kỹ năng thiết kế hệ thống
└── governance/      # Kỹ năng quản trị dữ liệu
```
