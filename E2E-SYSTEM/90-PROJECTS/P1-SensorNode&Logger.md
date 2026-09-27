---
loai: project
ma: P1
trang_thai: chua-bat-dau
gio_du_kien: "*toy* — tháng 2–4 — ~40 h"
---
# P1 · SENSOR NODE + LOGGER

***toy* — tháng 2–4 — ~40 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

### Mục tiêu
Nối được thế giới vật lý với phần mềm, đầu-cuối, một lần, dù xấu.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | MCU đọc ≥1 cảm biến (nhiệt độ hoặc IMU) ở tần số cố định |
| F2 | Truyền dữ liệu về máy tính qua UART hoặc Wi-Fi |
| F3 | Script trên máy nhận, parse, và lưu vào SQLite |
| F4 | Script thứ hai đọc SQLite và vẽ đồ thị theo thời gian |
| F5 | Timestamp gắn ở phía máy tính (chưa cần đồng bộ) |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Chạy liên tục không crash | ≥ 6 giờ |
| N2 | Tần số lấy mẫu ổn định | sai lệch < 5% |
| N3 | Không mất mẫu khi đường truyền tốt | 0 mẫu mất trong 1 giờ |

### BOM
ESP32-S3 hoặc Pico 2 · một cảm biến I²C (BME280, MPU6050, hoặc DS18B20) · breadboard + dây · cáp USB.

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Blink + toolchain | Nạp được firmware tự build, không dùng IDE có sẵn |
| M2 | Đọc cảm biến qua I²C | Giá trị hợp lý, xác nhận bằng cách thay đổi môi trường vật lý |
| M3 | Truyền và parse | Máy tính nhận đúng 1000 mẫu liên tiếp |
| M4 | Lưu trữ | SQLite có schema, không phải CSV dump |
| M5 | Trực quan hóa | Đồ thị đọc được, có nhãn trục và đơn vị |

### Tiêu chí nghiệm thu
- [ ] Chạy 6 giờ liên tục, dữ liệu đầy đủ
- [ ] Bạn giải thích được **từng dòng** firmware, kể cả phần khởi tạo peripheral
- [ ] Bạn giải thích được vì sao chọn tần số lấy mẫu đó
- [ ] Dựng lại toàn bộ từ đầu trong một buổi, không copy-paste

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C1.1, C1.2, C6.1, C6.3, C7.6, C9.1 | Bạn nối được hai thế giới | firmware ↔ phần mềm ↔ lưu trữ |

**Mở đường cho:** tất cả. Đây là bộ xương của mọi project sau.

### Cạm bẫy
Dùng thư viện Arduino cho mọi thứ. Cho phép ở M1–M2 để có động lực, nhưng **phải quay lại viết bằng register hoặc HAL thật** trước khi tuyên bố P1 xong — nếu không, C6.1 sẽ không bao giờ đạt.

---

---

## ✎ Nhật ký thực thi

| Ngày | Milestone | Giờ | Kết quả | Chặn ở đâu |
|---|---|---|---|---|
|  |  |  |  |  |

## ✎ ADR — quyết định không hiển nhiên

| # | Quyết định | Phương án bị loại | Lý do | Ngày |
|---|---|---|---|---|
|  |  |  |  |  |

## ✎ Nghiệm thu

| Tiêu chí | Đạt | Bằng chứng | Ngày |
|---|---|---|---|
|  | ☐ |  |  |

## ✎ Hậu kiểm

**Cái gì tôi sẽ làm khác lần sau:**

**Leaf nào project này chứng minh tôi CHƯA nắm:**

