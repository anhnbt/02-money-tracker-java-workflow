# Antigravity IDE — Quy trình (Workflow) dự án Money Tracker Java

Quy trình sử dụng AI Agent để tự động tạo ứng dụng Money Tracker (Quản lý chi tiêu) bằng Java Core và cơ sở dữ liệu MySQL.

## Mục tiêu

Tạo ra một ứng dụng Money Tracker chạy trên Console (Terminal) hoàn chỉnh bằng cách chạy quy trình (workflow) ngay bên trong Antigravity IDE.

Repository này bao gồm:
- Cấu trúc quy trình AI (workflow structure)
- Các câu lệnh hệ thống (system prompts)
- Các file bối cảnh (context files)
- Các quy tắc ràng buộc (rules)
- Hướng dẫn điều phối Agent (agent orchestration)

Lưu ý: Repository này là điểm xuất phát (starting point) để thực hành. AI sẽ tự động sinh ra mã nguồn logic dựa trên các quy tắc đã thiết lập.

---

## Yêu cầu chuẩn bị

- Đã cài đặt Antigravity IDE
- Đã kích hoạt tính năng Gemini / AI Agent
- Có kiến thức cơ bản về:
  - Java Core (tương thích JDK 1.8)
  - Cơ sở dữ liệu MySQL / JDBC
  - Quy trình giao việc cho AI (Prompt workflow)
  - Cấu trúc file trong dự án Java

---

## Hướng dẫn thực hành (Workflow)

1. Clone repository về máy

```bash
git clone <repo-url>
```

2. Mở dự án bằng Antigravity IDE

3. Mở file:

```txt
SYSTEM_PROMPT.md
```

4. Chạy workflow với AI Agent (Sử dụng tổ hợp phím Cmd/Ctrl + L)

5. Tương tác và lặp lại (Iterate) cho đến khi ứng dụng hoạt động chính xác

---

## Kết quả đầu ra (Expected Output)

Sau khi hoàn thành, AI Agent sẽ tự động tạo ra:
- Các class đối tượng (Java POJO classes)
- Kết nối CSDL và các hàm xử lý dữ liệu (Database Connection & CRUD operations)
- Giao diện điều khiển (Console UI / Menu)
- Xử lý các ngoại lệ (Exception Handling)

---

## Lưu ý quan trọng

- Không copy/paste những Prompt quá dài, nhồi nhét một cách liên tục.
- Hãy cấp quyền để AI tự quét và đọc cấu trúc dự án.
- Lặp lại (Iterate) theo từng bước nhỏ, hoàn thiện từng tính năng một.
- Luôn kiểm tra (Review) cẩn thận mã nguồn do AI sinh ra.
- Đảm bảo cơ sở dữ liệu (MySQL) đã được khởi chạy trên máy cục bộ (localhost).

---

## Cấu trúc thư mục

```txt
.agents/
.prompt/
SYSTEM_PROMPT.md
GEMINI.md
src/
```

---

## Về Seminar

Chủ đề:
> AGENTIC AI: ĐỂ ANTIGRAVITY IDE TỰ CODE
