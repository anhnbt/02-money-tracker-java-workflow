# Kịch bản Hướng dẫn: Phát triển tính năng CRUD với Antigravity IDE

Hãy áp dụng quy trình Multi-Agent Ecosystem chuẩn TDD để làm tính năng "Quản lý giao dịch (CRUD) với thiết kế DAO Pattern" cho ứng dụng Money Tracker. Hãy thực hiện tuần tự các bước sau:

## 0. Yêu cầu Kỹ thuật & Ràng buộc (Technical Rules)

- **Tech Stack**: JDK 1.8, MySQL 8, JDBC, Flyway (Migration), Maven, JUnit 4.
- **Kiến trúc (N-Tier)**:
  - `Main` (Console I/O).
  - `Service` (Business Logic thuần túy, tuyệt đối không chứa JDBC).
  - `DAO` (Toàn bộ logic truy xuất DB).
- **An toàn dữ liệu**: Dùng `PreparedStatement` chống SQL Injection. Xử lý Input Terminal chống crash (InputMismatchException).
- **Format hiển thị**: BẮT BUỘC Override `toString()` trong POJO `Transaction`, cấm nối chuỗi thủ công khi in.

## 1. BƯỚC 1 - Product Management

- **Tầm nhìn**: Money Tracker giúp quản lý tài chính qua ghi chép, lập ngân sách và báo cáo.
- **Scope Phase này**: CHỈ làm CRUD cho "Ghi chép thu chi". Lập ngân sách và báo cáo đưa vào **Out of Scope**.
- **Action**: Dùng skill `@prd-development` và `@user-story` để phân tích yêu cầu.
- Tạo Artifact `product_requirements` (PRD) chứa Problem Statement và ít nhất 3 User Stories (chuẩn Mike Cohn) + Acceptance Criteria (chuẩn Gherkin).
- DỪNG LẠI chờ người dùng duyệt.

## 2. BƯỚC 2 - Lập kế hoạch Kỹ thuật

- Tech Lead đọc PRD vừa duyệt. Dùng skill `@tech-lead-manager`.
- Chạy lệnh `/plan` để thiết lập Planning Mode.
- Tạo Artifact `implementation_plan` (đặt `request_feedback = true`). Vẽ sơ đồ Mermaid cho DAO Pattern. Đặt 3 câu hỏi (Open Questions) về edge cases. DỪNG LẠI chờ duyệt.

## 3. BƯỚC 3 - Red Phase (Test-First)

- Tạo Artifact `task` để theo dõi tiến độ.
- **Quy tắc**: Hàm test BẮT BUỘC chuẩn `given[Condition]_when[Action]_then[Result]`.
- Dùng skill `@qa-tester` kết hợp lệnh `/tdd`: Sinh file Unit Test cho CRUD dựa trên Acceptance Criteria.
- Chạy lệnh Terminal để Test (phải LỖI ĐỎ). Check hoàn thành task Red Phase.

## 4. BƯỚC 4 - Green Phase (Implementation)

- **Quy tắc (Chain of Thought)**: Phân tích kỹ log lỗi Terminal trước khi code.
- Dùng skill `@senior-coder`: Viết code Java logic thực sự (vừa đủ để pass test), tuân thủ cực kỳ nghiêm ngặt kiến trúc DAO. Check hoàn thành task.

## 5. BƯỚC 5 - Verify & Walkthrough

- Dùng skill `@qa-tester` và chạy lệnh `/verify` (hoặc `mvn clean test`). Đảm bảo xanh (Pass).
- **E2E Simulation**: Chạy App Interactive Mode trên Terminal. Nhập Input tuần tự từng bước để test CRUD thật.
- Tạo Artifact `walkthrough` chứa log quá trình.

## 6. BƯỚC 6 - Lưu trữ Context

- Chạy lệnh lưu tiến độ vào `backlog/01_Feature_CRUD_DAO.md` (bao gồm Done và Next Steps) để giải phóng Context Window cho session sau.
