---
loai: project
ma: P2
trang_thai: chua-bat-dau
gio_du_kien: "*small* — tháng 6–12 — ~120 h"
---
# P2 · TỰ VIẾT LẠI HẠ TẦNG

***small* — tháng 6–12 — ~120 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

### Mục tiêu
Hiểu các trừu tượng bạn dùng hàng ngày, bằng cách tự dựng lại chúng. **Đây là project khiến hồ sơ của bạn khác phần lớn ứng viên.**

Ba thành phần, làm tuần tự:

### P2a · TCP server từ socket thuần — ~45 h

| # | Yêu cầu |
|---|---|
| F1 | Server nhận kết nối TCP, xử lý giao thức dòng đơn giản (hoặc HTTP/1.1 tối giản) |
| F2 | Không dùng framework; chỉ dùng API socket của OS |
| F3 | Xử lý đúng partial read và partial write |
| F4 | Event loop dùng `epoll` (Linux), single-threaded |
| F5 | Timeout cho kết nối nhàn rỗi; graceful shutdown drain kết nối đang xử lý |
| N1 | ≥10.000 kết nối đồng thời, bộ nhớ < 500 MB |
| N2 | p99 latency < 10 ms ở 1.000 req/s trên localhost |
| N3 | Không rò rỉ mô tả file sau 1 triệu kết nối |

**Nghiệm thu:** chạy load test, đồ thị kết nối/bộ nhớ/latency; `lsof` xác nhận không rò rỉ fd; giải thích được vì sao `epoll` edge-triggered cần đọc tới `EAGAIN`.

### P2b · Key-value store có write-ahead log — ~50 h

| # | Yêu cầu |
|---|---|
| F1 | `get`, `put`, `delete` qua giao thức mạng (dùng lại P2a) |
| F2 | Write-ahead log ghi trước khi cập nhật memtable |
| F3 | Phục hồi đầy đủ sau crash bằng cách replay WAL |
| F4 | Checkpoint định kỳ và cắt WAL |
| F5 | Tùy chọn: LSM tree với SSTable và compaction cơ bản |
| N1 | **Không mất dữ liệu đã ack** khi kill -9 hoặc cắt điện |
| N2 | Throughput ghi ≥ 20.000 op/s với `fsync` mỗi N op (nêu rõ N và đánh đổi) |
| N3 | Thời gian phục hồi < 10 giây với WAL 1 GB |

**Nghiệm thu:** script tự động kill process ngẫu nhiên ≥200 lần trong lúc ghi; sau mỗi lần, xác nhận mọi giá trị đã ack vẫn đọc được. Đây là tiêu chí khó nhất của P2.

### P2c · Shell tối giản — ~25 h

| # | Yêu cầu |
|---|---|
| F1 | Parse dòng lệnh, `fork`/`exec`, `wait` |
| F2 | Pipe giữa các lệnh, redirect vào/ra |
| F3 | Job control cơ bản: chạy nền, `jobs`, `fg` |
| F4 | Xử lý tín hiệu đúng: Ctrl-C tới foreground job, không tới shell |
| F5 | Biến môi trường và built-in `cd`, `export` |

**Nghiệm thu:** chạy được `cat file | grep x | wc -l > out.txt`; Ctrl-C giết đúng tiến trình; không tạo zombie.

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C1 (Ad), C2, C4.1, C4.5, C4.6, C4.9, C5.10, C9.4 | Bạn hiểu trừu tượng bạn dùng, không chỉ gọi được chúng | OS ↔ mạng ↔ lưu trữ bền vững |

**Mở đường cho:** P4, và toàn bộ năng lực debug ở tầng hệ thống.

### Cạm bẫy
Làm cả ba cùng lúc. Làm tuần tự; P2b dùng lại P2a là một phần của bài học (interface design).

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

