# Claude Code Dev Kit

Kho tài liệu + skeleton để chuẩn hoá cách dùng **Claude Code** cho team dev:
- Tổ chức `skills`, `hooks`, `commands` theo chuẩn dễ mở rộng.
- Chuẩn bị sẵn cấu trúc để publish thành plugin sau này.
- Có hướng dẫn cài đặt để dùng local ngay.

## Mục tiêu

- Dùng repo này làm nguồn chuẩn cho workflow Claude Code trong dự án.
- Gom best-practice về prompt/skill/hook/cmd vào một chỗ.
- Có thể phát triển dần thành plugin riêng cho team.

## Cấu trúc repo

```text
.
├── .codex-plugin/
│   └── plugin.json
├── commands/
│   └── README.md
├── hooks/
│   └── README.md
├── skills/
│   └── README.md
└── docs/
    └── INSTALL_PLUGIN.md
```

## Thành phần chính

### 1) Skills

- Chứa workflow theo từng use case:
  - tạo feature
  - review code
  - fix bug
  - viết test
- Mỗi skill nên có:
  - `SKILL.md`
  - ví dụ input/output
  - rule rõ ràng về quality gate

Chi tiết: `skills/README.md`

### 2) Hooks

- Tự động chạy các bước kiểm tra trước/sau tác vụ:
  - format/lint
  - unit test nhanh
  - policy check
- Giúp giảm lỗi khi agent thao tác code.

Chi tiết: `hooks/README.md`

### 3) Commands

- Tập hợp lệnh chuẩn để dùng nhất quán:
  - bootstrap môi trường
  - chạy test
  - chạy pipeline kiểm tra
- Có thể map thành command shortcuts cho team.

Chi tiết: `commands/README.md`

## Plugin skeleton

Repo đã có file:

- `.codex-plugin/plugin.json`

Đây là manifest tối thiểu để bắt đầu đóng gói plugin nội bộ. Khi mở rộng, có thể bổ sung:
- metadata versioning
- danh sách skill public
- hook registration
- command aliases

## Cách cài plugin local

Xem file hướng dẫn:

- `docs/INSTALL_PLUGIN.md`

## Quy ước đóng góp

- Ưu tiên nội dung ngắn, rõ, có ví dụ chạy được.
- Mỗi thay đổi nên kèm use case thực tế.
- Nếu thêm skill mới: cần mô tả mục tiêu + đầu vào/đầu ra + checklist xác nhận.

## Roadmap gợi ý

- V1: chuẩn hoá docs + skill templates.
- V2: chuẩn hoá hooks lint/test/policy.
- V3: plugin hoá đầy đủ và có release process.
