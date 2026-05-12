# Hướng Dẫn Cấu Hình Quyền Hạn Agent (Agent Permissions)

Để đảm bảo an toàn tuyệt đối cho dự án và hệ thống máy tính của bạn, việc phân quyền chi tiết cho Agent (AI) là điều bắt buộc. Dưới đây là cấu hình đề xuất đủ linh hoạt để Agent có thể làm việc hiệu quả, đồng thời ngăn chặn mọi rủi ro bảo mật.

## 1. Luôn từ chối (Always Deny) – Chặn các hành vi nguy hiểm
Đây là nhóm các hành động mà Agent **tuyệt đối không được phép thực hiện**, bất kể có được hỏi hay không. Điều này bảo vệ cốt lõi hệ thống và tránh mất mát dữ liệu.

* **`shell_command(*)`**: Chặn toàn bộ việc tự động thực thi lệnh shell trên Terminal. Ngăn chặn rủi ro Agent vô tình chạy mã độc hoặc các lệnh xóa dữ liệu hệ thống (như `rm -rf`).
* **`fs_delete(*)`**: Ngăn cấm Agent xóa bất kỳ file nào trong project. Xóa nhầm file có thể phá vỡ cấu trúc và mã nguồn của dự án.
* **`network_request(*)`**: Chặn Agent gửi hoặc nhận dữ liệu tự do ra ngoài môi trường Internet, tránh rò rỉ dữ liệu hoặc mã nguồn (chỉ nên cho phép nếu bạn cung cấp một danh sách domain cụ thể được duyệt).
* **`read_file(~/.ssh/*)`**: Chặn hoàn toàn quyền truy cập vào các thư mục chứa khóa bảo mật (SSH keys), token hoặc chứng chỉ cấu hình của máy Mac.

## 2. Luôn hỏi (Always Ask) – Mặc định cho các tác vụ thay đổi trạng thái
Đây là nhóm tác vụ chính mà Agent được phép thực hiện, nhưng **bắt buộc phải có sự xác nhận của người lập trình (Human-in-the-loop)**. Điều này đảm bảo bạn luôn kiểm soát được AI đang sửa đổi gì.

* **`fs_write(*)`**: Mỗi khi Agent muốn tạo mới hoặc ghi đè code vào file, nó phải xin phép. Việc này giúp ngăn chặn AI ghi đè logic quan trọng, vô tình phá vỡ hệ thống hoặc chèn các đoạn code không mong muốn ("backdoor").
* **`fs_read(.env, *.yaml, *.properties)`**: Mặc dù chỉ là tác vụ đọc file, nhưng đối với các file chứa thông tin cấu hình nhạy cảm, mật khẩu hoặc khóa API (`.env`, `application.properties`, v.v.), Agent phải hỏi ý kiến bạn trước khi đọc.
* **`git_push(*)`**: Agent có thể hỗ trợ tạo `commit`, nhưng việc đẩy mã nguồn lên server từ xa (push) bắt buộc phải do con người kiểm tra và phê duyệt.
* **`run_tests(*)`**: Khi thực thi các bài Unit Test hoặc Integration Test, Agent nên yêu cầu xác nhận để tránh việc chạy các script test có tác động phụ ngoài ý muốn (nếu có).

## 3. Luôn cho phép (Always Allow) – Dành cho các tác vụ vô hại và tra cứu
Chỉ áp dụng cho các hành động không làm thay đổi trạng thái hệ thống, mang tính chất đọc hoặc phân tích thông tin nhằm phục vụ gợi ý code nhanh hơn.

* **`fs_list_files(*)`**: Cho phép Agent tự do xem danh sách các file và thư mục để nó có thể dễ dàng hiểu cấu trúc của dự án, phục vụ quá trình import và điều hướng mã nguồn.
* **`fs_read_metadata(*)`**: Cho phép đọc các thông tin siêu dữ liệu (metadata) của file (như kích thước, ngày sửa đổi) để phục vụ cho phân tích tĩnh.
* **`language_server(*)`**: Cho phép Agent kết nối và tương tác tự do với trình phân tích ngôn ngữ (Language Server Protocol) của Java. Việc này tối ưu hoá tốc độ phân tích cú pháp, báo lỗi và gợi ý code (autocomplete).
* **`search_symbol(*)`**: Cho phép tìm kiếm tự do các class, method, variable (ký hiệu) trong toàn bộ cấu trúc dự án.
