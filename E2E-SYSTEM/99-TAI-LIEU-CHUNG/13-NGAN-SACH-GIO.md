---
loai: meta
ma: M13
---
# 13 · Ngân sách giờ chi tiết (Phụ lục B) + bản đồ công việc (Phụ lục D)

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# PHỤ LỤC B · NGÂN SÁCH GIỜ CHI TIẾT

**v3:** hai nguồn giờ, không phải một.

| Nguồn | Giờ / 5 năm | Kiểm soát được? |
|---|---|---|
| Tự học | **3.600** | Có, hoàn toàn |
| Công việc quy đổi | **~2.100** | Không — phụ thuộc dự án được giao |
| **Hiệu dụng** | **~5.700** | |

## B.1 — Phân bổ giờ tự học theo nhãn

| Nhãn | Giờ tự học | % |
|---|---|---|
| Core (12 nhánh) | 2.250 | 62,5% |
| Supporting (8 nhánh) | 450 | 12,5% |
| Adjacent (6 nhánh) | 150 | 4,2% |
| Project tích hợp | 700 | 19,4% |
| Slack, review, viết lách | 50 | 1,4% |
| **Tổng** | **3.600** | **100%** |

## B.2 — Core · giờ tự học × giờ công việc quy đổi

| Nhánh | Tự học | Công việc | **Hiệu dụng** | Mức đạt được |
|---|---|---|---|---|
| C1 Programming & runtimes | 280 | 20 | **300** | Advanced |
| C2 DSA | 180 | 0 | **180** | Intermediate–Advanced |
| C3 Computer architecture | 200 | 0 | **200** | Intermediate–Advanced |
| C4 OS & concurrency | 240 | 30 | **270** | Advanced |
| C5 Networking | 160 | 250 | **410** | Advanced |
| C6 Embedded & firmware | 200 | 300 | **500** | Advanced |
| C7 Sensing & signals | 80 | 350 | **430** | Advanced |
| C8 ML & inference systems | 320 | 0 | **320** | Advanced → **Expert nếu chọn** |
| C9 Data engineering & storage | 190 | 40 | **230** | Intermediate–Advanced |
| C10 Distributed & cloud | 200 | 0 | **200** | Intermediate–Advanced |
| C11 Observability & performance | 130 | 100 | **230** | Intermediate–Advanced |
| C12 Systems architecture | 80 | 300 | **380** | Advanced → **Expert nếu chọn** |
| **Core tổng** | **2.260** | **1.390** | **3.650** | |

## B.3 — Supporting

| Nhánh | Tự học | Công việc | **Hiệu dụng** |
|---|---|---|---|
| S1 Mathematics | 220 | 0 | **220** |
| S2 Electronics & power | 30 | 250 | **280** |
| S3 Control theory | 30 | 250 | **280** |
| S4 Security | 60 | 40 | **100** |
| S5 Testing & verification | 50 | 30 | **80** |
| S6 Reliability & safety | 20 | 150 | **170** |
| S7 Queueing & economics | 20 | 10 | **30** |
| S8 Technical communication | 20 | 60 | **80** |
| **Supporting tổng** | **450** | **790** | **1.240** |

## B.4 — Adjacent

| Nhánh | Tự học | Công việc | **Hiệu dụng** |
|---|---|---|---|
| A1 Robotics & autonomy | 40 | 20 | **60** |
| A2 Simulation & digital twins | 30 | 20 | **50** |
| A3 HCI & human factors | 25 | 40 | **65** |
| A4 Business & operations | 10 | 80 | **90** |
| A5 Standards & regulation | 15 | 120 | **135** |
| A6 Licensing & IP | 30 | 0 | **30** |
| **Adjacent tổng** | **150** | **280** | **430** |

*Tổng công việc quy đổi: 1.390 + 790 + 280 = **2.460 h**. Tôi ghi ~2.100 ở §0 để dự phòng — giờ công việc trùng lặp giữa các nhánh (một buổi commissioning đóng góp vào C11 và C12 cùng lúc), nên tổng thực tế thấp hơn tổng cộng dồn.*

## B.5 — Project · giờ tự học

| Project | Giờ | Ghi chú |
|---|---|---|
| P1 Sensor node + logger | 40 | Phase 0 |
| P2 Tự viết lại hạ tầng | 110 | Phase 1–2 |
| P3 Edge anomaly detector | 150 | Phase 2–3. **30 ngày thực địa — bắt buộc** |
| P4 Ingestion platform | 130 | Phase 3–4 |
| P5 Inference service | 120 | Phase 4 |
| P6 Closed-loop system | 250 | Phase 5. **90 ngày vận hành — bắt buộc** |
| P7 Làm cứng / open source | tùy chọn | Sau tháng 72 |
| **Tổng** | **~800** | 700 h ròng sau khi trừ phần chồng với giờ nhánh |

## B.6 — Tổng theo phase (chỉ tự học)

| Phase | Tháng | Core | Supporting | Adjacent | Project | Slack | **Tổng** |
|---|---|---|---|---|---|---|---|
| P0 Bootstrap | 0–6 | 250 | 50 | — | 40 | 10 | **350** |
| P1 Nền tính toán | 3–24 | 560 | 140 | — | 90 | 10 | **800** |
| P2 Nền hệ thống | 18–38 | 600 | 80 | — | 110 | 10 | **800** |
| P3 Vòng lặp khép lại | 30–50 | 610 | 70 | — | 160 | 10 | **850** |
| P4 Quy mô & production | 42–62 | 490 | 70 | 60 | 120 | 10 | **750** |
| P5 Kiến trúc & chuyên sâu | 54–78 | 340 | 40 | 90 | 180 | 50 | **700** |
| **Tổng** | | **2.850** | **450** | **150** | **700** | **100** | **3.600** |

*Core cộng dồn 2.850 > 2.260 ở B.2 vì phần chênh là giờ ôn và giờ project tính vào nhánh. Tổng ròng vẫn 3.600.*

## B.7 — Cách dùng bảng này

| Tình huống | Làm gì |
|---|---|
| Giờ tự học thực tế thấp hơn 20% (≈12 h/tuần) | Bình thường. Cắt theo thứ tự: Adjacent → Supporting mức thấp → P7 |
| Thấp hơn 40% (≈9 h/tuần) | Cắt sâu hơn: giữ C8, C10, C1, C2 và P3; hoãn C3, C9, C11 sang sau tháng 60 |
| Thấp hơn 60% (≈6 h/tuần) trong ≥6 tháng | **Đổi kiến trúc:** giữ đúng một nhánh Advanced (C8), phần còn lại Working. Kéo timeline lên 8 năm. Thà đạt sâu một chỗ còn hơn nông khắp nơi |
| Công việc **không** cấp như bảng dự kiến | Sau 12 tháng, đối chiếu cột "công việc" với thực tế. Chênh lệch phải được bù bằng giờ tự học — hoặc bằng việc đổi vị trí trong công ty |
| Công việc cấp **nhiều hơn** dự kiến | Dồn giờ tự học tiết kiệm được vào C8 và C10 — hai nhánh không bao giờ có nguồn nào khác |
| Một nhánh tốn nhiều hơn dự kiến | Lấy từ Slack trước, rồi từ Adjacent. Đừng lấy từ nhánh core khác |
| Bạn đã biết một nhánh | Trừ giờ, nhưng **giữ lại checkpoint**. Không pass checkpoint nghĩa là chưa biết ở mức roadmap yêu cầu |

---

# PHỤ LỤC D · BẢN ĐỒ CÔNG VIỆC ↔ ROADMAP

**Mục đích:** trả lời một câu hỏi duy nhất — *giờ tự học khan hiếm của tôi nên đi vào đâu?*

**Nguyên tắc:** nhãn core/supporting/adjacent ở §3 **không đổi** theo bảng này. Bảng này nói về **chi phí thu nhận**, không nói về **tầm quan trọng**. Một nhánh adjacent mà công việc cấp miễn phí vẫn là adjacent — bạn chỉ may mắn được nó rẻ.

## D.1 — Bốn nhóm nhánh

| Nhóm | Đặc điểm | Chiến lược |
|---|---|---|
| **① Công việc không bao giờ cho** | Không có nguồn nào khác ngoài tự học | **Ưu tiên tuyệt đối.** Mất ngân sách ở đây là mất vĩnh viễn |
| **② Công việc cho một phần** | Cần bổ sung có mục tiêu | Xác định **chính xác** phần thiếu, chỉ học phần đó |
| **③ Công việc cho phần lớn** | Chỉ cần hệ thống hóa | Học **sau khi** gặp ở công việc, không học trước |
| **④ Công việc cho, nhưng cần dịch** | Có nguyên liệu, thiếu từ vựng chuyển nhượng | Thói quen dịch §2.3d, không cần giờ riêng |

## D.2 — Bảng đầy đủ 26 nhánh

| Nhánh | Nhãn | Nhóm | Công việc cấp gì | Tự học phải mua gì | Giờ tự học |
|---|---|---|---|---|---|
| **C1** Programming & runtimes | core | **①** | Gần như không (ST/ladder khác mô hình) | Toàn bộ C, Python, Go/Rust, debug, build, git, design | **280** |
| **C2** DSA | core | **①** | Không | Toàn bộ | **180** |
| **C3** Computer architecture | core | **①** | Không | Toàn bộ | **200** |
| **C4** OS & concurrency | core | **①②** | Khái niệm tất định, chu kỳ, ưu tiên (qua PLC) | Bộ nhớ ảo, I/O model, concurrency, container, eBPF | **240** |
| **C5** Networking | core | **②** | Giao thức công nghiệp (C5.16), mạng nhà máy | TCP/IP sâu, HTTP, TLS, socket, mạng cloud, chế độ hỏng | **160** |
| **C6** Embedded & firmware | core | **②④** | Mô hình PLC/DCS (C6.16), I/O, thời gian thực | Firmware MCU, bare-metal, RTOS, DMA, OTA, năng lượng, inference trên thiết bị | **200** |
| **C7** Sensing & signals | core | **③②** | Instrumentation, hiệu chuẩn, nhiễu, actuation thật | **DSP, FFT, lọc số, sensor fusion, trích đặc trưng cho ML** | **80** |
| **C8** ML & inference systems | core | **①** | **Không gì cả** | **Toàn bộ — và đây là cung `learn/infer` của vòng lặp** | **320** |
| **C9** Data engineering | core | **①②** | Historian ở mức người dùng | Mô hình dữ liệu, SQL sâu, transaction, time-series hiện đại, streaming, ingest từ edge | **190** |
| **C10** Distributed & cloud | core | **①** | Không | Toàn bộ | **200** |
| **C11** Observability & performance | core | **①②** | Commissioning debug, alarm (từ vựng khác) | Metric/log/trace/profile, SLO, benchmark, chaos, hàng đợi | **130** |
| **C12** Systems architecture | core | **②④** | **Thực hành**: tích hợp đa bên, commissioning xuyên tầng, ISA-95 trong thực tế | **Từ vựng và khung**: pattern, ADR, đánh đổi định lượng, FMEA có hệ thống, edge-cloud | **80** |
| **S1** Mathematics | supporting | **①** | Không | Toàn bộ | **220** |
| **S2** Electronics & power | supporting | **③** | Mạch thật, nguồn thật, đo thật, tải thật | Điện tử số mức MCU, power budget µA | **30** |
| **S3** Control theory | supporting | **③②** | Vòng kín thật, đối tượng thật, tuning thật, an toàn | Toán điều khiển, Kalman, control vs learned policy | **30** |
| **S4** Security | supporting | **②** | An ninh OT khi gặp (S4.9) | Threat modeling, identity, crypto, **bảo mật ML** | **60** |
| **S5** Testing & verification | supporting | **①②** | FAT/SAT, nghiệm thu | Test tự động, CI, property-based, **test hệ phi tất định** | **50** |
| **S6** Reliability & safety | supporting | **③④** | Bảo vệ, interlock, dự phòng, an toàn thật | FMEA có hệ thống, fault tree | **20** |
| **S7** Queueing & economics | supporting | **①** | Ngân sách dự án | Little's law, capacity, cost-per-inference, TCO phần mềm | **20** |
| **S8** Technical communication | supporting | **③②** | Spec, báo cáo, biên bản nghiệm thu | ADR, RFC, postmortem, C4 | **20** |
| **A1** Robotics | adjacent | **②** | Actuation, an toàn máy chuyển động | ROS 2, perception, SLAM, planning | **40** |
| **A2** Simulation | adjacent | **②** | Mô phỏng trước commissioning | HIL tự dựng, dữ liệu tổng hợp, sim-to-real | **30** |
| **A3** Human factors | adjacent | **③②** | HMI thật, người vận hành thật | Lý thuyết autonomy levels, mode confusion | **25** |
| **A4** Business & operations | adjacent | **③** | Quy trình, tiến độ, nhà thầu, ràng buộc thật | ROI kỹ thuật, tiêu chí tự động hóa | **10** |
| **A5** Standards & regulation | adjacent | **③②** | Grid code, tiêu chuẩn thiết bị, chứng nhận | EU AI Act, bảo vệ dữ liệu | **15** |
| **A6** Licensing & IP | adjacent | **①** | Rất ít | Toàn bộ | **30** |

## D.3 — Thứ tự ưu tiên tuyệt đối cho giờ tự học

Khi bạn chỉ có 6 giờ trong một tuần, dùng thứ tự này:

```
1. C8   ML & inference systems       ← cung learn/infer, KHÔNG có nguồn khác
2. C10  Distributed & cloud          ← KHÔNG có nguồn khác
3. C2   DSA        ┐
4. C3   Computer architecture  ├──── KHÔNG có nguồn khác, và là nền
5. C1   Programming            ┘
6. C4   OS & concurrency             ← phần lớn không có nguồn khác
7. S1   Mathematics                  ← chặn C8
8. C9   Data engineering
9. C11  Observability
10. C5  Networking (phần IT)
11. C6  Embedded (phần MCU)
12. phần còn lại
```

**Lý do C8 đứng đầu, không phải C1:** C1 chậm hơn nhưng bạn *sẽ* học được nó vì mọi project đều cần. C8 thì không có gì ép bạn — và nó là cung duy nhất mà cả công việc lẫn toàn bộ ngành OT quanh bạn đều đang thiếu. Bỏ C8 thì roadmap này biến thành "kỹ sư tự động hóa biết thêm ít phần mềm", không phải Intelligent Systems Integration Engineering.

## D.4 — Chín thứ ở công việc cần dịch ngay sang khái niệm trung lập

*Đây là bảng §2.3d mở rộng. Làm hằng tuần, mỗi lần gặp một cái mới. Ghi vào một file duy nhất.*

| Bạn thấy | Khái niệm trung lập | Nhánh | Vì sao quan trọng |
|---|---|---|---|
| Scan cycle, cycle time monitoring | Vòng lặp tất định, WCET, jitter, ngân sách thời gian | C4.10, C6.15, C6.16 | Mọi hệ real-time đều có khái niệm này |
| OB chu kỳ, OB ngắt | ISR, lập lịch rate-monotonic, phân tích khả năng lập lịch | C4.2, C6.2 | |
| Hardware config, GSD/GSDML | Mô tả thiết bị, device tree, khám phá thiết bị | C4.12, C6.1 | |
| Profinet IRT, distributed clock | Mạng thời gian thực, đồng bộ đồng hồ, PTP | C5.3, C7.9 | Nối thẳng sang hệ phân tán |
| Alarm class, alarm suppression | Thiết kế cảnh báo, triệu chứng vs nguyên nhân, mệt mỏi cảnh báo | C11.11, A3 | **Cùng bài toán, khác từ vựng hoàn toàn** |
| Redundancy H-system, hot standby | Dự phòng nóng, chuyển đổi dự phòng, split-brain, fencing | S6.3, C10.4 | |
| Historian, trend, compression | Lưu trữ chuỗi thời gian, downsampling, retention | C9.5 | |
| Interlock, permissive, trip | Fail-safe, giới hạn cứng, cô lập lỗi | S6.3, C7.11 | |
| FAT / SAT / punch list | Tiêu chí nghiệm thu, contract test, regression suite | S5.4, C12.3 | |

**Cách dùng:** mỗi tuần thêm ít nhất 2 dòng. Sau 1 năm bạn có ~100 cặp. Đó là lúc bạn nói được về công việc của mình bằng ngôn ngữ mà một kỹ sư phần mềm hiểu — và ngược lại. **Đó chính là năng lực liên ngành, ở dạng cụ thể nhất.**

## D.5 — Kiểm tra lại bảng này ở tháng 12

Toàn bộ Phụ lục D dựa trên một giả định chưa kiểm chứng: **công việc sẽ cấp kỹ thuật thật, không phải chủ yếu giấy tờ và giám sát nhà thầu.** Đây là điều không chắc số 9 ở §15.3.

Ở tháng 12, làm bài kiểm tra này:

| Câu hỏi | Nếu "có" | Nếu "không" |
|---|---|---|
| Tôi đã tự cấu hình/lập trình một hệ điều khiển chưa? | C6.16 đang được cấp | Chuyển C6 sang nhóm ① |
| Tôi đã đấu nối, hiệu chuẩn, hoặc debug cảm biến thật chưa? | C7, S2 đang được cấp | **Chuyển C7 và S2 sang nhóm ①: +200 h tự học** |
| Tôi đã tune hoặc sửa một vòng điều khiển chưa? | S3 đang được cấp | Chuyển S3 sang nhóm ①: +60 h |
| Tôi đã tham gia commissioning và tự tìm ra ≥1 lỗi chưa? | C11, C12 đang được cấp | Chuyển sang nhóm ①: +150 h |
| Sổ dịch khái niệm của tôi có ≥60 cặp chưa? | Thói quen §2.3d đang chạy | Thói quen chưa hình thành — sửa trước khi làm gì khác |

**Nếu ≥3 câu trả lời "không":** ngân sách tự học phải gánh thêm ~400 h, và điều đó có nghĩa timeline giãn thêm 1–1,5 năm, **hoặc** bạn cần đổi vị trí trong công ty sang vai trò kỹ thuật hơn. Cả hai đều là quyết định hợp lệ; điều không hợp lệ là không nhận ra và tiếp tục dùng bảng này như thể nó đúng.

---

*Kết thúc tài liệu · v3.0 · 14/09/2026*
*Cập nhật khi: ước lượng sai · đổi spine · đổi việc · tài nguyên biến mất · một điều ở §15.3 được chứng minh hoặc bác bỏ.*

## Nhật ký cập nhật

| Ngày | Thay đổi | Lý do |
|---|---|---|
| 14/09/2026 | v1.0 — bản đầu, nhiều nhánh nén | — |
| 14/09/2026 | v2.0 — mở rộng đầy đủ, không nhánh nào nén | Xác nhận ngân sách phần cứng và thời gian |
| 14/09/2026 | **v3.0** — hiệu chỉnh tình huống nghề nghiệp | Đã đi làm: kỹ sư tự động hóa, EPC không O&M, đích liên ngành. **Giữ nguyên 38 lĩnh vực**; đổi trình tự, ngân sách giờ, và bổ sung 5 leaf lấp lỗ hổng tầng công nghiệp (C5.16, C6.16, S3.8, S4.9, C12.15) |
| | | |
---

## ✎ Phần của tôi — theo dõi

| Tháng | Giờ kế hoạch | Giờ thật | Nhánh nhận nhiều nhất | Ghi chú |
|---|---|---|---|---|
|  |  |  |  |  |

