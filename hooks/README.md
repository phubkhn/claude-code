# Hooks Directory

Thư mục này mô tả các hook dùng để kiểm soát chất lượng khi Claude Code thao tác.

## Use cases phổ biến

- `pre-task`: kiểm tra ngữ cảnh trước khi chạy task
- `pre-commit`: format + lint + test nhanh
- `post-task`: tổng hợp kết quả và cảnh báo rủi ro

## Khuyến nghị

- Hook cần chạy nhanh, deterministic.
- Nếu hook fail, trả thông báo rõ ràng và có action fix.
