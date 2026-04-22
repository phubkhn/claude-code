# Cài Plugin Local Cho Claude Code

Tài liệu này hướng dẫn cài plugin từ repo này để dùng nội bộ.

## 1) Clone repo

```bash
git clone https://github.com/phubkhn/claude-code.git
cd claude-code
```

## 2) Kiểm tra manifest plugin

Đảm bảo file tồn tại:

```text
.codex-plugin/plugin.json
```

## 3) Liên kết plugin vào môi trường Claude Code

Tuỳ môi trường, bạn có thể:
- thêm repo vào danh sách plugin local của Claude Code
- hoặc symlink repo vào thư mục plugin local mà Claude Code đang đọc

Ví dụ symlink (Linux/macOS):

```bash
mkdir -p "$HOME/.codex/plugins/local"
ln -s "$(pwd)" "$HOME/.codex/plugins/local/claude-code-dev-kit"
```

## 4) Khởi động lại Claude Code

- Restart app/CLI để Claude Code load plugin mới.
- Xác nhận plugin được nhận bằng cách kiểm tra danh sách skills/hooks/commands.

## 5) Kiểm tra nhanh

- Mở thư mục `skills/`, `hooks/`, `commands/`
- Thêm 1 skill thử nghiệm
- Reload Claude Code và kiểm tra skill đã xuất hiện

## Gợi ý mở rộng

- Tách skill theo domain: backend/frontend/devops
- Hook pre-commit cho lint/test
- Bundle command templates theo stack (Python/Node/Go)
