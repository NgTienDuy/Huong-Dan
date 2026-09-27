---
loai: meta
ma: M06
---
# 06 · Kiến trúc 5–6 năm theo phase

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# 9. KIẾN TRÚC 5–6 NĂM THEO PHASE

**Thay đổi cấu trúc so với v2:** giờ có **hai track chạy song song**, không phải một.

| Track | Nguồn | Điều khiển bởi | Nhánh chính |
|---|---|---|---|
| **Track OT** | Công việc | Dự án được giao — bạn không kiểm soát | C7, S2, S3, S6, A4, A5, phần OT của C5/C6/C12 |
| **Track IT** | Tự học | Roadmap này — bạn kiểm soát hoàn toàn | C1, C2, C3, C4, C8, C9, C10, C11, S1, S4, S5, phần IT của C5/C6/C12 |
| **Cầu nối** | Project cá nhân | Bạn thiết kế | Nơi hai track gặp nhau, và nguồn cung `observe→adapt` duy nhất |

Track OT **không lập lịch được** — nó phụ thuộc dự án công ty giao. Nên roadmap chỉ lập lịch cho Track IT, và coi Track OT là đầu vào ngẫu nhiên có xu hướng tích cực.

## Bản đồ tổng

```
Tháng:  0    6    12   18   24   30   36   42   48   54   60   66   72
        |----|----|----|----|----|----|----|----|----|----|----|----|

TRACK OT (công việc — không lập lịch được)
 Thử việc ██
 Định hướng, theo dõi, đọc bản vẽ  ████████████
 Tham gia commissioning có giám sát     ████████████████
 Commissioning độc lập, đóng góp thiết kế     ██████████████████████
 Trách nhiệm cấp hệ thống                            ████████████████████████

TRACK IT (tự học — lập lịch được)
P0 ██████
P1   ████████████████████
P2          ████████████████████████
P3                    ████████████████████████
P4                              ████████████████████████
P5                                        ████████████████████████

CẦU NỐI (project)
 P1 ████
 P2      ██████████
 P3              ████████████
 P4                      ████████████
 P5                              ████████████
 P6                                    ████████████████████████
                    ▲                          ▲
                    │                          └─ điểm rẽ nhánh (§11.4)
                    └─ hết thử việc + P2 xong
```

---

## ◆ PHASE 0 · BOOTSTRAP — tháng 0–6 · ~350 h tự học

**Giãn từ 3 tháng lên 6** vì thử việc và định hướng công việc ăn phần lớn năng lượng.

| Hạng mục | Giờ | Nội dung |
|---|---|---|
| C1 — C và Python cơ bản | 150 | Con trỏ, bộ nhớ, cấu trúc; Python + pytest |
| C1.9 — Tooling debug | 30 | gdb, valgrind, sanitizer — **sớm, không hoãn** |
| C4.12 + môi trường | 30 | Linux như môi trường sống, shell, dotfiles |
| C1.10 — Git | 20 | Mô hình đối tượng, workflow |
| C6 — Blink + toolchain | 40 | Board đầu tiên, cross-compile |
| S1.1 — Discrete math | 40 | Logic, tập hợp, quy nạp |
| **P1** — Sensor node + logger | 40 | Project đầu tiên |

**Song song ở Track OT:** ghi lại **mọi khái niệm vendor bạn gặp** và khái niệm trung lập bên dưới nó (bảng ở §2.3d). Đây là thói quen rẻ nhất có ROI cao nhất trong toàn bộ 6 năm — bắt đầu từ tuần đầu tiên.

**Tín hiệu sang Phase 1:** dựng lại P1 từ đầu trong một buổi, không copy-paste. Và: bạn có một file ghi chú ≥30 cặp *khái niệm vendor ↔ khái niệm trung lập*.

---

## ◆ PHASE 1 · NỀN TÍNH TOÁN — tháng 3–24 · ~800 h tự học

**Giãn từ 12 lên 21 tháng.** Đây là phase dài nhất và khó nhất khi vừa đi làm — vì nó cho cảm giác chậm và không nối trực tiếp với công việc.

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C1 Programming | 180 | C nâng cao, UB, build system, Python packaging |
| C2 DSA | 140 | Độ phức tạp → DP |
| C3 Computer architecture | 130 | **nand2tetris phần 1** (70 h) + ISA + assembly |
| C4 OS | 70 | Tiến trình, luồng, bộ nhớ ảo |
| S1 Mathematics | 140 | **Đợt 1**: discrete + đại số tuyến tính |
| C6 Embedded | 50 | Đọc datasheet, GPIO, timer |
| Project | 90 | **P2a + P2b** |

**Cạm bẫy đặc thù của người vừa đi làm:** phase này không cho bạn thứ gì dùng được ở công ty ngay, nên nó dễ bị bỏ. Chống bằng hai cách: giữ P2 chạy để luôn có thứ hữu hình, và dùng bảng §2.3d để thấy nand2tetris đang giải thích chính cái PLC bạn dùng hằng ngày.

**Tín hiệu sang Phase 2:** bạn debug bằng lập luận về bộ nhớ, không bằng thêm `print`. Và bạn giải thích được scan cycle của PLC bằng từ vựng của C4.2 và C6.15.

---

## ◆ PHASE 2 · NỀN HỆ THỐNG — tháng 18–38 · ~800 h tự học

**Mục tiêu:** mạng, dữ liệu, OS ở mức Advanced. Đây là phase bắt đầu **giao với công việc** — bạn sẽ hiểu tầng dưới của Profinet, của historian, của mạng nhà máy.

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C4 OS & concurrency | 170 | Concurrency, I/O model, filesystem, scheduling |
| C5 Networking | 160 | TCP sâu, socket, packet capture, DNS, HTTP |
| C9 Data engineering | 130 | Mô hình dữ liệu, SQL sâu, transaction, chuỗi thời gian |
| C10 Distributed | 60 | **Mô hình lỗi** — nền tư duy |
| C8 ML | 70 | Nền học thống kê + **đánh giá** (trước mọi modeling) |
| C11 Observability | 40 | Bốn tín hiệu + instrumentation |
| C1 + C2 tiếp | 80 | Error handling, runtime internals |
| C3 tiếp | 50 | **Phân cấp bộ nhớ** + phương pháp đo |
| S1 Mathematics | 60 | **Đợt 2**: xác suất + thống kê |
| S8 Communication | 20 | Design doc, ADR |
| Project | 160 | **P2c** xong, **P3** khởi động |

**Giao thoa với Track OT:** khi bạn học C5.5 (TCP sâu) và C5.16 (giao thức công nghiệp), lần đầu bạn sẽ thấy Profinet, Modbus TCP và IEC 61850 không phải ba thứ ma thuật riêng biệt mà là ba điểm khác nhau trên cùng một phổ đánh đổi.

**Tín hiệu sang Phase 3:** từ packet capture giải thích được một sự cố mạng nhà máy — và giải thích được cho cả kỹ sư OT lẫn kỹ sư IT, bằng từ vựng của mỗi bên.

---

## ◆ PHASE 3 · VÒNG LẶP KHÉP LẠI — tháng 30–50 · ~850 h tự học

**Mục tiêu:** mua ba cung `learn`, `infer`, `adapt` mà cả công việc lẫn ngành OT đều không cho.

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C8 ML & inference | 230 | Neural net từ đầu, kiến trúc, **nén model**, eval |
| C6 Embedded | 150 | RTOS, DMA, năng lượng, kiến trúc firmware, **bootloader/OTA** |
| C7 Sensing — **phần công việc không cho** | 80 | DSP, FFT, sensor fusion, trích đặc trưng cho ML |
| C10 Distributed | 140 | **Idempotency**, nhất quán, **kiểm soát tải** |
| C9 Data | 90 | **Ingest từ edge**, streaming, schema contract |
| C5 Networking | 80 | TLS, MQTT/gRPC, kết nối thực địa |
| C11 Observability | 40 | Profiling, phân phối độ trễ |
| C12 Architecture | 40 | ADR, mẫu kiến trúc, **ISA-95** |
| S4 Security | 40 | Threat modeling, **IEC 62443** |
| Project | 160 | **P3** hoàn thành (30 ngày thực địa), **P4** khởi động |

**Lưu ý phân bổ C7:** ở v2 nhánh này là 260 h tự học. Ở v3 chỉ còn 80 h vì công việc cấp phần lớn — nhưng **chỉ phần instrumentation công nghiệp**. Phần DSP, FFT, sensor fusion và trích xuất đặc trưng cho ML thì công việc không cho, và đó chính là 80 h này.

**Tín hiệu sang Phase 4:** P3 chạy 30 ngày ngoài thực địa. Và bạn chẩn đoán được một lỗi mà nguyên nhân nằm ở tầng khác với tầng triệu chứng, ≥3 lần, với 3 cặp tầng khác nhau.

---

## ◆ PHASE 4 · QUY MÔ, ĐỘ TIN CẬY, PRODUCTION — tháng 42–62 · ~750 h tự học

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C8 ML | 150 | **Serving**, LLM systems, **eval harness**, drift |
| C11 Observability | 90 | SLO, hàng đợi, capacity, chaos, incident |
| C10 Distributed & cloud | 100 | Cloud, IaC, **Kubernetes** (sau distributed) |
| C9 Data | 60 | Object storage, vector, chất lượng dữ liệu, backup |
| C6 Embedded | 80 | **Inference trên thiết bị**, bảo mật, real-time |
| C3 Architecture | 50 | GPU, **NPU & accelerator** |
| C12 Architecture | 40 | Interface, đánh đổi, kiến trúc tham chiếu |
| S5 Testing | 50 | Test hệ phi tất định, eval như testing, HIL |
| S7 Economics | 20 | Mô hình chi phí, capacity |
| A1–A3 Adjacent | 60 | Robotics, simulation, human factors |
| Project | 190 | **P4** hoàn thành, **P5** hoàn thành |

**Tín hiệu sang Phase 5:** dự đoán được hành vi hệ thống dưới tải trước khi đo, đúng thường xuyên hơn sai. Ghi 10 dự đoán, đo, đếm.

---

## ◆ PHASE 5 · KIẾN TRÚC & CHIỀU SÂU — tháng 54–78 · ~700 h tự học

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C12 Architecture | 60 | **FMEA xuyên tầng**, **phân chia edge–cloud**, migration, security by design |
| Nhánh Expert đã chọn | 180 | Đẩy tới mức tự implement lại core components |
| C8 ML | 80 | Mẫu agentic, monitoring, chi phí, chế độ hỏng |
| A4–A6 Adjacent | 80 | Business, standards, licensing |
| **P6** — hệ end-to-end | 250 | **North Star ở dạng sản phẩm — 90 ngày vận hành** |
| Slack | 50 | |

**P7** (làm cứng hoặc đóng góp mã nguồn mở) chuyển sang tùy chọn sau tháng 72.

**Tín hiệu hoàn thành:** người khác đến hỏi bạn *nên thiết kế thế nào*, và bạn trả lời bằng đánh đổi có số liệu. Và bạn nêu được rõ ràng cái bạn **không** biết.

---

## 9.1 — Bảng tổng giờ theo phase (chỉ Track IT)

| Phase | Tháng | Giờ tự học | % |
|---|---|---|---|
| P0 Bootstrap | 0–6 | 350 | 10% |
| P1 Nền tính toán | 3–24 | 800 | 22% |
| P2 Nền hệ thống | 18–38 | 800 | 22% |
| P3 Vòng lặp khép lại | 30–50 | 850 | 24% |
| P4 Quy mô & production | 42–62 | 750 | 21% |
| P5 Kiến trúc & chuyên sâu | 54–78 | 700 | 19% |
| | | **~3.600 h** (có chồng lấn) | |

*Tổng vượt 100% vì phase chồng lấn về thời gian; tổng giờ thực là ~3.600 h.*

Cộng **~2.100 h** quy đổi từ công việc (Phụ lục D) → **~5.700 h hiệu dụng**.

## 9.2 — Ba quy tắc cho người vừa đi làm vừa tự học

1. **Nhánh nào công việc đang dạy thì đừng tự học song song.** Chờ. Nếu tháng này bạn đang commissioning một hệ điều khiển, đừng dành tối để đọc control theory — dành tối cho C1 hoặc C8. Học cùng lúc cùng chủ đề từ hai nguồn nghe có vẻ tăng tốc nhưng thực tế là trùng lặp.

2. **Ưu tiên nhánh công việc không bao giờ cho.** Thứ tự bất biến: C8 > C10 > C2/C3/C4 > C1 > phần còn lại. Lý do: đây là những thứ mà nếu bạn không tự học thì **không có nguồn nào khác**, mãi mãi.

3. **Chuyển đổi mỗi thứ học được ở công ty thành khái niệm trung lập trong vòng 1 tuần.** Nếu sau một tháng bạn chỉ nói được "tôi cấu hình OB35 chu kỳ 100ms", bạn chưa học gì chuyển nhượng được. Nếu bạn nói được "tôi cấu hình một tác vụ chu kỳ với ngân sách WCET 100ms, và tôi biết cách đo jitter của nó" — đó là kiến thức đi theo bạn suốt đời.
---

## ✎ Phần của tôi — theo dõi

| Phase | Bắt đầu thật | Kết thúc thật | Giờ thật | Trượt bao nhiêu | Vì sao |
|---|---|---|---|---|---|
| 0 |  |  |  |  |  |
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |
| 4 |  |  |  |  |  |
| 5 |  |  |  |  |  |

