---
loai: project
ma: P4
trang_thai: chua-bat-dau
gio_du_kien: "*realistic-complex* — tháng 20–30 — ~180 h"
---
# P4 · INGESTION & SERVING PLATFORM

***realistic-complex* — tháng 20–30 — ~180 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

### Mục tiêu
Vận hành dữ liệu ở quy mô và dưới điều kiện xấu.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | Nhận dữ liệu từ ≥10 thiết bị (thật hoặc giả lập từ dữ liệu thật của P3) |
| F2 | Gateway/broker MQTT, xác thực bằng mTLS, mỗi thiết bị có định danh riêng |
| F3 | Ingest vào stream có thứ tự trong partition |
| F4 | Xử lý: validation, dedup theo idempotency key, enrichment |
| F5 | Lưu vào time-series store với retention policy nhiều tầng |
| F6 | API truy vấn: theo thiết bị, theo khoảng thời gian, theo mức tổng hợp |
| F7 | Dashboard: trạng thái đội thiết bị, dữ liệu mới nhất, cảnh báo |
| F8 | Device management: đăng ký, provisioning, trạng thái online/offline |
| F9 | Schema registry với kiểm tra tương thích trong CI |
| F10 | Backfill: nạp dữ liệu lịch sử mà không phá thống kê |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Ingest throughput | ≥ 10.000 điểm/giây, đo được |
| N2 | Độ trễ ingest | p99 từ thiết bị tới truy vấn được < 10 giây |
| N3 | Đồng bộ hàng loạt | 20 thiết bị offline 24 h cùng trở lại: tải server **không vượt 2×** bình thường |
| N4 | Truy vấn | "trung bình theo giờ, 30 ngày" trả về < 1 giây |
| N5 | Dung lượng | 1 năm dữ liệu 100 thiết bị × 5 cảm biến × 1 Hz trong ngân sách bạn đặt |
| N6 | SLO | định nghĩa ≥3 SLI với mục tiêu, có dashboard |
| N7 | Observability | trace từ thiết bị tới DB với correlation ID |
| N8 | Khôi phục | thực hiện restore thật, đo RTO/RPO |

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Hạ tầng bằng IaC | Phá hủy và dựng lại hoàn toàn từ code, dịch vụ hoạt động |
| M2 | Broker + mTLS + provisioning | Thiết bị mới tự đăng ký và nhận chứng chỉ |
| M3 | Pipeline ingest + dedup | Test gửi trùng 3× cho kết quả giống hệt |
| M4 | Time-series store + retention | Tính toán dung lượng khớp với thực tế trong 20% |
| M5 | API + dashboard | Trả lời "hệ có khỏe không" trong ≤10 giây |
| M6 | Observability | Trace đi qua ≥4 thành phần |
| M7 | SLO + cảnh báo | Cảnh báo burn-rate nhiều cửa sổ |
| M8 | Test đồng bộ hàng loạt | Đồ thị tải chứng minh N3 |
| M9 | Backup + restore thật | RTO/RPO đo được |
| M10 | Schema evolution | Đổi schema, consumer cũ vẫn chạy, chứng minh trong CI |

### Tiêu chí nghiệm thu
- [ ] Toàn bộ hạ tầng dựng lại từ zero bằng một lệnh
- [ ] 10 thiết bị chạy liên tục 7 ngày, dashboard phản ánh đúng
- [ ] Test đồng bộ hàng loạt pass với đồ thị chứng minh
- [ ] Restore thật thành công, RTO đo được
- [ ] Bạn tìm được một sự cố (tự dựng) chỉ bằng trace và metric, không đọc code

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C9 (Ad), C10 (In→Ad), C11 (In), C5.9, C5.13, C10.13, S7 | Vận hành dữ liệu ở quy mô, dưới điều kiện xấu | edge ↔ streaming ↔ storage ↔ API ↔ observability |

**Mở đường cho:** P5, P6.

### Cạm bẫy
Dựng dashboard trước khi có metric đáng nhìn. Thứ tự đúng: instrument → thu metric → biết câu hỏi nào cần trả lời → dashboard.

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

