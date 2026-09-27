---
loai: meta
ma: M01
---
# 01 · Bản đồ 38 lĩnh vực → nhánh → leaf

Mục đích: chứng minh **không họ lĩnh vực nào bị rơi** khi 38 họ ở roadmap §3 được gom thành 35 nhánh ở §5.
Khi bạn nghi ngờ "cái này học ở đâu?", tra bảng này trước.

## A · 26 họ bắt buộc (§3.1)

| # | Họ lĩnh vực | Nhãn | Nằm ở đâu trong bộ tài liệu |
|---|---|---|---|
| 1 | Mathematics | core (chọn lọc) | S1 toàn nhánh |
| 2 | Physics & natural science | supporting | S2 (điện) · C7.1–C7.5 (sóng, tín hiệu) · C3.13 + S2.8 (nhiệt) · S2.4 (năng lượng) |
| 3 | Electronics & circuits | core | S2 toàn nhánh |
| 4 | Computer architecture & digital logic | core | C3 toàn nhánh |
| 5 | Embedded systems & firmware | core — spine | C6 toàn nhánh |
| 6 | Control theory & signal processing | core (DSP) / supporting (control) | C7.1–C7.4, C7.10 (DSP) · S3 toàn nhánh + C7.12 (control) |
| 7 | Robotics / mechatronics | adjacent → supporting | A1 toàn nhánh · C7.11 (actuation) |
| 8 | Programming languages, compilers, runtimes | core / supporting | C1 toàn nhánh (C1.8 runtime) · P1 (compiler backend — peripheral) |
| 9 | Data structures & algorithms | core | C2 toàn nhánh |
| 10 | Software engineering & design patterns | core | C1.12 · C1.10 · C12.8 |
| 11 | Operating systems & concurrency | core | C4 toàn nhánh · C2.13 |
| 12 | Networking | core | C5 toàn nhánh |
| 13 | Distributed systems | core | C10.1–C10.10 |
| 14 | Databases & storage systems | core | C9.1–C9.8 |
| 15 | Data engineering & pipelines | core | C9.9–C9.14 |
| 16 | AI / ML / statistical learning | core | C8 toàn nhánh · C6.14 (trên thiết bị) |
| 17 | Cloud & infrastructure | core | C10.11–C10.14 · C5.13 |
| 18 | DevOps / SRE / observability | core | C11.1–C11.3 · C11.9–C11.11 · C10.13 |
| 19 | Security & cryptography | supporting (4 sub-part core) | S4 toàn nhánh · C5.9 · C6.13 · C12.14 |
| 20 | Performance engineering | core | C11.4–C11.8 · C11.12–C11.14 · C3.14 · C2.11 |
| 21 | Testing, verification, formal methods | supporting | S5 toàn nhánh (S5.8 = formal, mức Aw) · P5 (proof assistant — peripheral) |
| 22 | Systems architecture & design | core — đỉnh | C12 toàn nhánh |
| 23 | HCI / UX | adjacent | A3.3 · A3.5 · P7 (frontend — peripheral) |
| 24 | Business, process & operations engineering | adjacent | A4 toàn nhánh |
| 25 | Standards, compliance, regulation | adjacent | A5 toàn nhánh |
| 26 | Economics of engineering | supporting | S7 toàn nhánh · C8.15 · C11.13 · C12.10 |

## B · 12 họ bổ sung ngoài danh sách 26 (§3.2)

| # | Họ lĩnh vực | Nhãn | Nằm ở đâu |
|---|---|---|---|
| 27 | Reliability & safety engineering | supporting | S6 toàn nhánh · C12.5 · S3.6 · A1.5 |
| 28 | Queueing theory & capacity planning | supporting | S1.8 · S7.1–S7.2 · C11.5 · C11.8 |
| 29 | Information theory | supporting | S1.7 |
| 30 | Numerical methods & floating-point | supporting | S1.6 · C3.12 · C8.9 |
| 31 | Metrology, sensor science & calibration | supporting | C7.6 · C7.7 · S2.6 |
| 32 | Time & synchronization | supporting | C7.9 · C10.2 · C9.11 |
| 33 | Simulation & digital twins | adjacent | A2 toàn nhánh |
| 34 | Human factors of automation | adjacent | A3.1 · A3.2 · A3.4 · C11.11 (mệt mỏi cảnh báo) |
| 35 | Technical writing & design documentation | supporting | S8 toàn nhánh · C12.12 |
| 36 | Licensing, IP & data rights | adjacent | A6 toàn nhánh |
| 37 | Energy & power engineering | core | S2.3 · S2.4 · S2.8 · C3.13 · C6.9 |
| 38 | Supply chain & component lifecycle | peripheral | P6 · S2.2 (EOL part) |

## C · 9 lĩnh vực peripheral (§5.4)

| Mã | Lĩnh vực |
|---|---|
| [P1](../P0-Peripheral&Awareness/P1-CompilerBackend&Codegen.md) | Compiler backend & codegen |
| [P2](../P0-Peripheral&Awareness/P2-VLSI-ASIC-FPGA.md) | VLSI / ASIC / FPGA RTL |
| [P3](../P0-Peripheral&Awareness/P3-RF&AntennaDesign.md) | RF & antenna design |
| [P4](../P0-Peripheral&Awareness/P4-MechanicalDesign&CAD.md) | Mechanical design & CAD |
| [P5](../P0-Peripheral&Awareness/P5-FormalMethods-ProofAssistants.md) | Formal methods với proof assistant |
| [P6](../P0-Peripheral&Awareness/P6-SupplyChain&DFM.md) | Supply chain & DFM |
| [P7](../P0-Peripheral&Awareness/P7-FrontendFrameworks.md) | Frontend framework ecosystem |
| [P8](../P0-Peripheral&Awareness/P8-QuantumComputing.md) | Quantum computing |
| [P9](../P0-Peripheral&Awareness/P9-Blockchain&DLT.md) | Blockchain / distributed ledger |

## D · 5 leaf bổ sung ở v3 — lấp lỗ hổng tầng công nghiệp

Đây là phần roadmap v2 **thiếu**, không phải phần được ưu ái vì bạn đang làm ngành năng lượng.
Chúng đáng học kể cả nếu bạn đổi nghề.

| Leaf | Nội dung | Nhánh |
|---|---|---|
| [C5.16](../C5-Networking/C5.16-IndustrialProtocols-OT.md) | Giao thức công nghiệp (OT) | C5 |
| [C6.16](../C6-EmbeddedSystems&Firmware/C6.16-PLC&DCS.md) | PLC và DCS như mô hình tính toán thứ tư | C6 |
| [S3.8](../S3-ControlTheory&Feedback/S3.8-IndustrialProcessControl.md) | Điều khiển quá trình công nghiệp | S3 |
| [S4.9](../S4-SecurityEngineering/S4.9-OTSecurity-IEC62443.md) | An ninh OT / ICS (IEC 62443) | S4 |
| [C12.15](../C12-SystemsArchitecture&Integration/C12.15-ISA95&PurdueModel.md) | ISA-95 và mô hình Purdue | C12 |

---

## ✎ Ô kiểm tra của tôi

| Câu hỏi | Trả lời |
|---|---|
| Có khái niệm nào tôi gặp mà không tìm được chỗ đặt trong bảng này? |  |
| Nếu có — nó thuộc leaf nào, hay cần thêm leaf mới? |  |
| Ngày rà soát gần nhất |  |

> Nếu bạn gặp một chủ đề **không** thuộc bất kỳ ô nào ở trên, ghi vào đây trước khi tạo file mới —
> phần lớn trường hợp nó thật ra là một sub-leaf của leaf đã có.
