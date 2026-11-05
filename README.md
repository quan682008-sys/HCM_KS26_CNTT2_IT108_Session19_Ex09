# HCM_KS26_CNTT2_IT108_Session19_Ex09
# Bài 9: Quản lý mật khẩu Bitwarden – PixelForge Studio

## Phần 1: Phân tích kiến trúc bảo mật

### Câu 1. Rủi ro khi lưu mật khẩu trên Chrome

Chrome lưu mật khẩu trong tệp `Login Data` và được hệ điều hành mã hóa. Nếu máy bị nhiễm Infostealer, hacker có thể tìm cách lấy mật khẩu, Cookie đăng nhập và chiếm tài khoản.

Đặc biệt, nếu dùng chung mật khẩu cho nhiều dịch vụ thì chỉ cần lộ một tài khoản, các tài khoản khác cũng có nguy cơ bị tấn công.

### Câu 2. Zero-Knowledge và Client-side Decryption

- Zero-Knowledge: Bitwarden không thể tự xem mật khẩu được lưu trong Vault.
- Client-side Decryption: Dữ liệu được mã hóa bằng AES-256 và giải mã ngay trên thiết bị người dùng.

Nếu máy chủ Bitwarden bị hack, hacker chủ yếu lấy được dữ liệu đã mã hóa (Ciphertext), không thể đọc trực tiếp mật khẩu. Tuy nhiên, Master Password yếu hoặc bị lộ vẫn có thể khiến dữ liệu gặp nguy hiểm.

---

## Phần 2: Chính sách quản lý mật khẩu

### Câu 3. Tạo Master Passphrase mạnh

Sử dụng nhiều từ ngẫu nhiên, dễ nhớ nhưng khó đoán, kết hợp chữ hoa, chữ thường, số và ký tự đặc biệt.

Ví dụ: `ConMeo-BauTroi#MayBay-72!`

Mật khẩu dài trên 20 ký tự. Khi sử dụng thực tế cần tự tạo Passphrase riêng, không dùng lại ví dụ.

### Câu 4. Cấu hình Password Generator

| Tiêu chí | Cấu hình |
|---|---|
| Độ dài | 24 ký tự (tối thiểu 16) |
| Chữ hoa A–Z | Bật |
| Chữ thường a–z | Bật |
| Chữ số 0–9 | Bật |
| Ký tự đặc biệt | Bật |

Áp dụng nguyên tắc mỗi tài khoản một mật khẩu riêng, lưu 40 tài khoản vào Bitwarden và phân quyền theo từng nhân viên.

### Câu 5. Auto-fill chống Phishing

Bitwarden kiểm tra tên miền trước khi đề xuất điền mật khẩu.

Ví dụ: `github.com` khác `githúb.com`, nên Bitwarden thường không tự điền mật khẩu vào trang giả khi cấu hình so khớp phù hợp.

Nhờ vậy, người dùng giảm nguy cơ nhập mật khẩu vào website giả mạo.

### Câu 6. Quy trình Emergency Kit

1. Chuẩn bị: Thiết lập Emergency Access, chỉ định Trưởng nhóm làm người liên hệ tin cậy.
2. Cấu hình: Chọn quyền View hoặc Takeover, đặt thời gian chờ 24 giờ.
3. Khôi phục: Khi có sự cố, Trưởng nhóm gửi yêu cầu. Hết thời gian chờ mà không bị từ chối thì được cấp quyền.
4. Hoàn tất: Khôi phục tài khoản, cấp lại quyền cho nhân viên và kiểm tra bảo mật.

Ngoài ra, cần lưu thông tin khôi phục ở nơi an toàn, không chia sẻ công khai.
