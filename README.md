# LapTrinhMangNangCao
 # Secure Client-Server System (Subdomain Scanner)

Một hệ thống Client-Server bảo mật cao được thiết kế để thực hiện các tác vụ quét subdomain, tích hợp nhiều lớp mã hóa và cơ chế xác thực tiên tiến.

## 🛡️ Tính năng Bảo mật Nổi bật

Dự án tập trung vào việc đảm bảo tính toàn vẹn, bảo mật và khả năng chống giả mạo thông qua các cơ chế:

### 1. Xác thực mạnh mẽ với Chữ ký số
Hệ thống sử dụng thuật toán **SHA256withRSA** để thiết lập quy trình xác thực:
*   Mỗi yêu cầu (request) từ Client được ký bằng **Private Key**.
*   Server sử dụng **Public Key** tương ứng để xác minh danh tính và đảm bảo dữ liệu không bị thay đổi trong quá trình truyền tải.

### 2. Mã hóa dữ liệu hai lớp (Hybrid Encryption)
Sự kết hợp giữa mã hóa đối xứng và bất đối xứng nhằm tối ưu hiệu suất và an toàn:
*   **AES-CBC:** Sử dụng để mã hóa dữ liệu nhạy cảm (như Public Key của client) trước khi gửi đi.
*   Cơ chế này giúp ngăn chặn việc lộ thông tin ngay cả khi kênh truyền bị can thiệp.

### 3. Bảo vệ kết nối End-to-End với TLS
Toàn bộ đường truyền giữa Client và Server được bao bọc bởi lớp giao thức **TLS (Transport Layer Security)**:
*   Chống tấn công nghe lén (Eavesdropping).
*   Ngăn chặn tấn công trung gian (Man-in-the-middle).

### 4. Quản lý phiên làm việc (Session Management)
Hệ thống quản lý trạng thái kết nối thông minh và an toàn:
*   **UUID:** Mỗi Client được cấp một định danh duy nhất.
*   **Isolated Keys:** Mỗi phiên làm việc sở hữu bộ khóa mã hóa (AES và IV) riêng biệt, được lưu trữ an toàn để ngăn chặn **Replay Attack**.

### 5. Kiểm soát truy cập chặt chẽ (Access Control)
Hệ thống áp dụng chính sách Zero Trust cho các tác vụ nhạy cảm:
*   Chỉ những Client đã vượt qua xác thực chữ ký số và giải mã thành công mới được cấp quyền sử dụng tính năng **Quét Subdomain**.

## 🛠 Công nghệ sử dụng

*   **Ngôn ngữ:** (Ví dụ: Python/Java/Go - Bạn hãy điền vào đây)
*   **Mã hóa:** AES-256-CBC, RSA-2048.
*   **Hashing:** SHA-256.
*   **Giao thức:** HTTPS/TLS 1.3.

## 🚀 Quy trình hoạt động

1.  **Handshake:** Client và Server thiết lập kết nối TLS và trao đổi khóa.
2.  **Authentication:** Client ký request bằng Private Key; Server xác thực qua Public Key.
3.  **Data Exchange:** Dữ liệu được mã hóa AES-CBC và truyền tải an toàn.
4.  **Execution:** Server xử lý yêu cầu quét subdomain và trả kết quả đã mã hóa về cho Client.

---
