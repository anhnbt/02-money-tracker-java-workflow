# Antigravity IDE - Global Rules (Dự án Money Tracker)

## 1. Project Context
- Đọc thêm tại: `@SYSTEM_PROMPT.md`
- Ứng dụng Console Terminal: Tập trung vào logic chặt chẽ, hiển thị log rõ ràng, không có giao diện đồ họa.
- **Ngôn ngữ giao tiếp:** Antigravity IDE phải LUÔN LUÔN suy nghĩ, giải thích và giao tiếp với người dùng bằng Tiếng Việt trong suốt quá trình làm việc.

## 2. Code Style & Architecture
- **Ngôn ngữ ưu tiên:** Java Core.
- **Tiêu chuẩn Code:** Code đảm bảo tương thích tuyệt đối với JDK 1.8. Sử dụng cấu trúc POJO truyền thống (tạo class với thuộc tính private và đầy đủ Getter/Setter) cho các đối tượng dữ liệu. Sử dụng vòng lặp `for` hoặc `while` cơ bản để xử lý danh sách thay vì Stream API để học viên dễ hiểu.
- Bám sát file `@SYSTEM_PROMPT.md` để đặt tên hàm Unit Test theo đúng quy chuẩn `given...when...then...`.

## 3. Workflow (TDD)
- Mọi logic tính toán (ví dụ đọc file CSV) đều phải viết Unit Test trước. 
- Sử dụng quy trình Suy luận từng bước (đọc `@SYSTEM_PROMPT.md`) để phân tích dữ liệu trước khi thực thi.
- Khi gặp lỗi `Exception`, Agent phải tự chủ động đọc log và tự đề xuất fix bug cho đến khi test PASS, không được dừng lại chờ người dùng nhắc.