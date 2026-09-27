---
loai: meta
ma: M15
---
# 15 · Bill of materials — phần cứng theo phase (Phụ lục A)

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# PHỤ LỤC A · BILL OF MATERIALS

Giá tham chiếu VND, mua được ở Hà Nội (chợ Nhật Tảo / Trời Đất / Điện Tử Việt Nam, hoặc Shopee/Lazada, hoặc đặt từ LCSC/AliExpress nếu chờ được). Giá dao động; dùng để lập ngân sách, không để so giá.

## A.1 — Phase 0 · Gói khởi động — mua ngay ngày 3

| Món | Số lượng | Giá ước tính | Vì sao cần ngay |
|---|---|---|---|
| ESP32-S3 DevKit (hoặc Raspberry Pi Pico 2) | 2 | 150–250k/cái | Board chính; mua 2 để có cái dự phòng khi làm cháy |
| Breadboard 830 điểm | 2 | 40k/cái | |
| Bộ dây jumper (M-M, M-F, F-F) | 1 bộ | 60k | |
| Cảm biến nhiệt/ẩm/áp I²C (BME280) | 1 | 80k | Cảm biến đầu tiên — I²C, có datasheet tốt |
| IMU 6 trục (MPU6050) hoặc 9 trục | 1 | 50–150k | Cho P1 và sau này P3 |
| **Logic analyzer 8 kênh** | 1 | 200–350k | **ROI cao nhất trong toàn bộ BOM.** Không có nó, debug bus là đoán |
| Đồng hồ vạn năng số | 1 | 300–600k | Chọn loại có đo dòng và đo tụ |
| Cáp USB chất lượng (data, không chỉ sạc) | 2 | 50k/cái | Nguyên nhân phổ biến của "board không nhận" |
| **Tổng Phase 0** | | **~1,3–2,2tr** | |

## A.2 — Phase 1–2 · Mở rộng — tháng 4–18

| Món | Số lượng | Giá ước tính | Dùng cho |
|---|---|---|---|
| STM32 DevKit (Nucleo hoặc Blue Pill + ST-Link) | 1–2 | 150–400k | Họ MCU thứ hai — hệ sinh thái khác ESP32, học được nhiều |
| Probe SWD/JTAG (ST-Link V2 clone hoặc DAPLink) | 1 | 100–200k | Debug thật, không chỉ printf |
| Mỏ hàn + thiếc + flux + hút thiếc | 1 bộ | 400–800k | Perfboard và sửa board |
| Nguồn DC điều chỉnh được (0–30V, 0–5A) | 1 | 800k–1,5tr | Cấp nguồn ổn định, giới hạn dòng để không cháy board |
| Perfboard + header + connector | 1 bộ | 150k | Chuyển từ breadboard sang lắp đặt bền |
| Mic I²S (INMP441) | 1–2 | 60k/cái | Cho P3 nếu chọn hướng âm thanh |
| Module INA219 / INA226 đo dòng | 2 | 50k/cái | **Bắt buộc cho C6.9** — đo ngân sách năng lượng |
| Cảm biến nhiệt độ chính xác (RTD hoặc DS18B20) | 2 | 40k/cái | Cho C7.7 hiệu chuẩn — cần ≥2 để so sánh |
| Điện trở, tụ, diode, MOSFET, LED bộ tổng hợp | 1 bộ | 200k | |
| Pin 18650 + mạch sạc/bảo vệ + holder | 2 bộ | 150k/bộ | Cho P3 chạy pin |
| **Tổng Phase 1–2** | | **~2,5–4,5tr** | |

## A.3 — Phase 3 · Triển khai thực địa — tháng 18–36

| Món | Số lượng | Giá ước tính | Dùng cho |
|---|---|---|---|
| Raspberry Pi 5 (4GB hoặc 8GB) + nguồn + thẻ nhớ | 1 | 1,8–2,8tr | Gateway, embedded Linux, edge compute |
| SSD NVMe + adapter cho Pi | 1 | 800k–1,5tr | Thẻ nhớ SD chết sau vài tháng ghi liên tục — bài học thật |
| Vỏ hộp kín (IP54 trở lên) | 2–3 | 100–250k/cái | Triển khai 30 ngày ngoài môi trường thật |
| Nguồn 5V/12V ổn định có cách ly | 2 | 150k/cái | |
| Cáp và connector chống rung | 1 bộ | 200k | Lắp đặt lên máy đang chạy |
| Module LoRa (SX1276/SX1262) | 2 | 150–250k/cái | Nếu thử nghiệm truyền xa, C5.3 |
| **Oscilloscope** 2 kênh (rẻ: DSO138/FNIRSI; tốt: Rigol DS1054Z) | 1 | 700k–8tr | Tùy ngân sách. Rẻ vẫn hơn không có. C7.5, S2.6 |
| Cảm biến bổ sung tùy bài toán P3 | — | 300–800k | Rung, dòng, áp suất, khí |
| **Tổng Phase 3** | | **~4–14tr** | Biến động lớn nhất ở oscilloscope |

## A.4 — Phase 4–5 · Tùy chọn — tháng 36+

| Món | Giá ước tính | Khi nào mua |
|---|---|---|
| MCU có NPU (STM32N6, hoặc board NXP/Renesas tương đương) | 1–3tr | Khi C6.14 cần so sánh NPU vs CPU thật |
| Thêm 3–5 thiết bị cho đội P6 | 1–2tr | Khi P6 cần ≥5 thiết bị |
| GPU rời ≥24GB VRAM | 40–70tr | **Chỉ khi** chi phí thuê hàng tháng > 1/24 giá máy (§0.2) |
| Máy phân tích năng lượng (Nordic PPK2 hoặc tương đương) | 2–3tr | Khi đo dòng ngủ µA bằng INA219 không đủ chính xác |
| Bàn hàn khí nóng + kính lúp | 1,5–3tr | Chỉ nếu làm SMD |
| In 3D (thuê dịch vụ, không mua máy) | 50–200k/lần | Vỏ tùy chỉnh cho P3, P6 |

## A.5 — Tổng ngân sách 5 năm

| Phase | Thấp | Cao |
|---|---|---|
| Phase 0 | 1,3tr | 2,2tr |
| Phase 1–2 | 2,5tr | 4,5tr |
| Phase 3 | 4,0tr | 14,0tr |
| Phase 4–5 (không tính GPU) | 2,0tr | 8,0tr |
| **Tổng (không GPU)** | **~10tr** | **~29tr** |
| Thuê GPU Phase 1–4 | 3tr | 8tr |
| Sách (3 cuốn ở §13.8) | 2tr | 3tr |
| **Tổng cộng** | **~15tr** | **~40tr** |

**[Recommendation] Thứ tự ưu tiên nếu phải cắt:**
1. **Không cắt:** logic analyzer, đồng hồ vạn năng, 2 board, INA219. Đây là bộ tối thiểu để **đo được** — và không đo được thì không học được C6/C7.
2. **Hoãn được:** oscilloscope (tới Phase 3), nguồn DC điều chỉnh (dùng USB trước), Raspberry Pi 5 (tới Phase 3).
3. **Bỏ được:** MCU có NPU (dùng CPU và mô phỏng để hiểu nguyên lý), máy phân tích năng lượng, bàn hàn khí nóng.
4. **Không mua GPU** cho tới khi có số liệu chứng minh (§0.2).

## A.6 — Quy tắc mua sắm

| Quy tắc | Lý do |
|---|---|
| **Không mua board mới cho tới khi board hiện tại đã chạy một project ≥30 ngày** | Chống cạm bẫy "sưu tầm board" (§12.3) |
| Mua 2 cái cho mọi thứ rẻ dễ hỏng | Bạn **sẽ** làm cháy board. Chờ hàng 1 tuần giữa chừng project là cách giết động lực |
| Ưu tiên linh kiện có datasheet tốt hơn linh kiện rẻ hơn | Datasheet kém = hàng chục giờ đoán mò |
| Kiểm tra trạng thái vòng đời (EOL) trước khi chọn MCU cho P3/P6 | Chọn con sắp ngừng sản xuất là lỗi đắt (S2.2) |
| Thiết bị đo: mua tốt hơn khả năng hiện tại của bạn | Bạn sẽ lớn lên vừa nó; đồng hồ rẻ nói dối và bạn không biết |
| Với cảm biến: mua ≥2 cái cùng loại | Hiệu chuẩn (C7.7) cần so sánh; một cái không nói lên gì |

---
---

## ✎ Phần của tôi — theo dõi

| Thiết bị | Phase | Ngày mua | Giá thật | Đã dùng vào việc gì | Đáng không |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

