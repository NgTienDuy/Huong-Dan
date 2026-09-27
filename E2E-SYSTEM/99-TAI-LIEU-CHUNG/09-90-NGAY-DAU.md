---
loai: meta
ma: M09
---
# 09 · 90 ngày đầu

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# 14. 90 NGÀY ĐẦU

Việc cụ thể, không phải "đọc về X". Mục tiêu của 90 ngày: **hoàn thành Phase 0 và bước vào Phase 1 với đà**.

Ngân sách: 25–30 h/tuần ≈ **330–390 h** trong 90 ngày.

## 14.1 — Tuần 1 (ngày 1–7)

| Ngày | Việc | Giờ | Xong khi |
|---|---|---|---|
| **1** | Cài Linux (dual boot hoặc WSL2). Dựng dotfiles, terminal, editor. Học 20 lệnh shell **bằng cách dùng chúng**. Xem *The Missing Semester* bài 1–2. | 5 | Bạn điều hướng và sửa file mà không rời terminal |
| **2** | Chương trình C đầu tiên: đọc file text, đếm tần suất từ, in top 10. Không thư viện ngoài. Chạy qua `gdb` một lần, `valgrind` một lần. | 5 | Chạy đúng và valgrind báo sạch |
| **3** | **Đặt mua phần cứng** (Phụ lục A, gói khởi động). Trong lúc chờ: cài toolchain cho MCU, build và chạy blink trên simulator hoặc QEMU. | 5 | Đơn đã đặt; toolchain build được binary |
| **4** | Git: mô hình đối tượng, tạo repo public, commit công việc ngày 2. Viết README mô tả **bạn học được gì**, không phải bạn làm gì. | 4 | Repo có ≥3 commit với message nghĩa lý |
| **5** | **Nand2Tetris project 1** — cổng logic cơ bản từ NAND. | 6 | Toàn bộ test project 1 pass |
| **6** | Python: script đọc CSV, tính thống kê, vẽ biểu đồ, lưu SQLite. Có `pytest` với ≥3 test. | 5 | Test pass; script chạy từ dòng lệnh với tham số |
| **7** | Viết **một trang**: mục tiêu 90 ngày, giờ cam kết mỗi tuần, và checkpoint bạn dùng để tự kiểm ở ngày 90. Mở file STATE ở §16 và điền lần đầu. | 3 | Một trang tồn tại, có số, có ngày, **không có từ "sẽ cố gắng"** |

## 14.2 — Tuần 2–4 (ngày 8–30) — ~90 h

| Khối | Nội dung | Giờ | Xong khi |
|---|---|---|---|
| C — con trỏ và bộ nhớ | K&R chương 5–6. Tự cài: dynamic array, linked list, hash table đơn giản. Mỗi cái có test và chạy sạch dưới sanitizer. | 30 | Ba cấu trúc chạy sạch dưới ASAN + valgrind; bạn giải thích được padding của mỗi struct |
| Nand2Tetris project 2–3 | ALU, thanh ghi, bộ nhớ | 18 | Test pass |
| Phần cứng về → blink thật | Nạp firmware **tự build**, không dùng IDE. Đọc GPIO section của reference manual. | 12 | LED chớp bằng code bạn hiểu từng dòng, cấu hình bằng register hoặc HAL thật |
| Đọc cảm biến I²C | Đọc datasheet cảm biến, viết driver tối giản, in giá trị qua UART | 15 | Giá trị hợp lý, xác nhận bằng thay đổi môi trường vật lý |
| Toán — logic và chứng minh | 6.042 chương 1–3: logic, chứng minh, quy nạp | 12 | Giải được bài tập cuối chương, viết chứng minh đầy đủ |
| Shell + tooling | *Missing Semester* bài 3–6: scripting, công cụ, debugging, metaprogramming | 8 | Bạn viết được script tự động hóa một việc bạn làm lặp lại |

**Checkpoint ngày 30:**
- [ ] Ba cấu trúc dữ liệu tự cài, sạch dưới sanitizer
- [ ] Nand2Tetris project 1–3 pass
- [ ] Cảm biến đọc được, giá trị hợp lý, driver do bạn viết
- [ ] Bạn dùng `gdb` để tìm một bug mà không cần thêm `printf`

## 14.3 — Tháng 2 (ngày 31–60) — ~120 h

| Khối | Nội dung | Giờ | Xong khi |
|---|---|---|---|
| **P1 — xây thật** | Sensor node → UART/Wi-Fi → script → SQLite → đồ thị. Theo đặc tả §10 P1. | 40 | M1–M5 của P1 hoàn thành |
| Nand2Tetris project 4–5 | Assembly, kiến trúc máy tính, CPU hoàn chỉnh | 25 | CPU chạy được chương trình assembly |
| C nâng cao | *Modern C*: UB, `const`/`volatile`/`restrict`, struct layout, preprocessor | 20 | Bạn liệt kê được 10 loại UB hay gặp và giải thích compiler khai thác chúng thế nào |
| Python lên mức package | Chuyển script của P1 thành package có `pyproject.toml`, test, type hints, CLI | 15 | `pip install .` chạy được từ repo sạch; `mypy` pass |
| Toán — tổ hợp và đồ thị | 6.042 chương 4–5 | 12 | Bài tập |
| Build system | `make`/`CMake`, cross-compile cho ARM từ x86 | 8 | Cross-compile thành công, binary chạy trên board |

**Checkpoint ngày 60:**
- [ ] P1 chạy 6 giờ liên tục, dữ liệu đầy đủ
- [ ] Nand2Tetris phần 1 hoàn thành (project 1–5)
- [ ] Package Python cài được và pass `mypy --strict`
- [ ] Cross-compile hoạt động, bạn giải thích được linker script

## 14.4 — Tháng 3 (ngày 61–90) — ~120 h

| Khối | Nội dung | Giờ | Xong khi |
|---|---|---|---|
| **P1 — hoàn thiện và nghiệm thu** | Chạy 6 h, viết README, dựng lại từ đầu trong một buổi | 20 | Toàn bộ tiêu chí nghiệm thu P1 tick |
| Nand2Tetris project 6 | Assembler | 15 | Assembler chạy được, dịch đúng chương trình test |
| CS:APP khởi động | Chương 1–3: biểu diễn thông tin, biểu diễn số, assembly cơ bản | 30 | Làm Data Lab và Bomb Lab (hoặc ít nhất một trong hai) |
| DSA khởi động | 6.006 bài 1–6: độ phức tạp, mảng, sắp xếp, cây | 25 | Problem set 1–2 |
| Đại số tuyến tính khởi động | *Essence of Linear Algebra* (toàn bộ) + 18.06 bài 1–5 | 20 | Bạn giải thích được nhân ma trận bằng cả hai cách: hàng-cột và tổ hợp tuyến tính |
| Đọc datasheet có hệ thống | Chọn một peripheral bạn **chưa dùng** (bộ so sánh, RTC, watchdog), cấu hình chỉ bằng reference manual | 10 | Peripheral hoạt động, không copy ví dụ |

## 14.5 — Nghiệm thu ngày 90 — tiêu chí chuyển sang Phase 1 đầy đủ

**Bắt buộc (không đạt thì lặp lại tháng 3, không đi tiếp):**
- [ ] **P1 hoàn thành** theo toàn bộ tiêu chí nghiệm thu ở §10
- [ ] Bạn **dựng lại P1 từ đầu trong một buổi**, không copy-paste
- [ ] Nand2Tetris phần 1 hoàn thành (project 1–6)
- [ ] Ba cấu trúc dữ liệu tự cài bằng C, sạch dưới sanitizer
- [ ] Bạn cấu hình được một peripheral lạ **chỉ bằng datasheet**
- [ ] Bạn dùng `gdb` như công cụ đầu tiên khi có bug, không phải `printf`

**Nên có:**
- [ ] Repo public với ≥4 commit mỗi tuần, message có nghĩa
- [ ] File STATE (§16) được cập nhật hàng tuần
- [ ] Bạn đã viết ≥1 ghi chú kỹ thuật giải thích một thứ bạn học cho người khác

**Tín hiệu cảnh báo — nếu thấy, dừng và đọc lại §0.3:**
- Giờ thực tế dưới 15 h/tuần trong ≥4 tuần liên tiếp
- Bạn tránh né nhánh phần cứng và chỉ làm phần mềm (hoặc ngược lại)
- Bạn học nhiều mà không xây gì trong 3 tuần liền
- Bạn thấy chán chứ không thấy khó — **hai thứ này khác nhau, và cái đầu nghiêm trọng hơn**

## 14.6 — Nhịp hàng tuần, áp dụng suốt 5 năm

| Ngày | Việc | Giờ điển hình |
|---|---|---|
| Thứ 2–6 | 2 khối sâu × 2 h, hoặc 1 khối × 4 h | 3–4 h/ngày |
| Thứ 7 | Khối dài cho project (phần cứng cần thời gian liên tục) | 6–8 h |
| Chủ nhật | Ôn, viết ghi chú, cập nhật STATE, lập kế hoạch tuần | 2–3 h |

**Ba quy tắc nhịp độ:**
1. **Khối sâu tối thiểu 90 phút** cho việc học khái niệm mới. Dưới mức đó là đọc, không phải học.
2. **Luôn có một project đang chạy song song** với việc học nhánh. Học thuần lý thuyết quá 3 tuần là dấu hiệu sắp bỏ cuộc.
3. **Chủ nhật viết lại một thứ bạn học trong tuần bằng lời của bạn.** Nếu không viết ra được, bạn chưa hiểu.

---
---

## ✎ Phần của tôi — theo dõi

| Tuần | Kế hoạch | Giờ thật | Đã xong | Chặn ở đâu |
|---|---|---|---|---|
| 1 |  |  | ☐ |  |
| 2 |  |  | ☐ |  |
| … |  |  | ☐ |  |

