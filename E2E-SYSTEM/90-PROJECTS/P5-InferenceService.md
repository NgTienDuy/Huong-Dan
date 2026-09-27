---
loai: project
ma: P5
trang_thai: chua-bat-dau
gio_du_kien: "*complex* — tháng 28–38 — ~180 h"
---
# P5 · INFERENCE SERVICE

***complex* — tháng 28–38 — ~180 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

### Mục tiêu
Hiểu **kinh tế học và vật lý** của inference, không chỉ API của nó.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | Tự host một model (LLM nhỏ, hoặc model thị giác, hoặc model từ P3 ở quy mô lớn hơn) |
| F2 | API tương thích chuẩn (OpenAI-compatible hoặc gRPC có schema) |
| F3 | Continuous batching hoặc dynamic batching |
| F4 | Hỗ trợ ≥2 cấu hình quantization, chuyển đổi được |
| F5 | Autoscaling theo độ sâu hàng đợi hoặc theo latency, có scale-to-zero |
| F6 | Kiểm soát tải: rate limit theo client, load shedding, circuit breaker |
| F7 | Đo và ghi nhận: TTFT, TPOT, throughput, độ sâu hàng đợi, cost-per-inference |
| F8 | Eval harness chạy trong CI trước mỗi lần đổi cấu hình |
| F9 | Fallback khi model không khả dụng |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Cải thiện throughput | **≥2×** so với cấu hình ngây thơ, bằng thay đổi cấu hình, có số đo |
| N2 | Latency budget | p50 và p99 dưới ngưỡng bạn đặt ở tải mục tiêu |
| N3 | Sống sót quá tải | ở **3× tải thiết kế**, suy giảm có kiểm soát thay vì sập |
| N4 | Cost-per-inference | tính được, và so sánh với chi phí gọi API bên thứ ba |
| N5 | Mất chính xác do quantization | dưới ngưỡng đặt trước, đo trên eval set riêng |
| N6 | Khởi động lạnh | đo được, và có chiến lược giảm thiểu |

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Serving cơ bản chạy | Model trả về kết quả đúng qua API |
| M2 | Đo baseline | Throughput, TTFT, TPOT, mức dùng VRAM |
| M3 | Batching | Throughput tăng, đồ thị theo kích thước batch |
| M4 | Quantization | Đường cong Pareto ≥4 điểm |
| M5 | Kiểm soát tải | Đồ thị hành vi ở 1×, 2×, 3×, 5× tải |
| M6 | Autoscaling | Phản ứng với spike, đo thời gian phản ứng |
| M7 | Eval harness trong CI | Bắt được một regression bạn cố ý tạo ra |
| M8 | Mô hình chi phí | Bảng tính có phân tích độ nhạy |
| M9 | Load test tới điểm gãy | Mô tả **chính xác cách nó gãy** |

### Tiêu chí nghiệm thu
- [ ] Throughput ≥2× baseline, với giải thích **cơ chế** của mỗi cải thiện
- [ ] Ở 3× tải, hệ từ chối rõ ràng thay vì treo hoặc sập
- [ ] Bảng so sánh tự host vs API bên thứ ba với điểm hòa vốn tính được
- [ ] Bạn chỉ ra được kernel/giai đoạn nào là nút thắt và vì sao (memory-bound hay compute-bound)

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C8.10 (Ad→Ex), C8.9, C3.9, C3.6, C10.10, C11 (Ad), S7 | Kinh tế học và vật lý của inference | kiến trúc máy tính ↔ ML ↔ hạ tầng ↔ chi phí |

**Mở đường cho:** P6.

### Cạm bẫy
Đo throughput tối đa thay vì throughput ở latency cố định. Con số "10.000 token/giây" vô nghĩa nếu p99 latency là 30 giây.

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

