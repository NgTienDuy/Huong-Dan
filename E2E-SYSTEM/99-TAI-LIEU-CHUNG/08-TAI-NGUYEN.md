---
loai: meta
ma: M08
---
# 08 · Tài nguyên theo thứ tự học

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# 13. TÀI NGUYÊN THEO THỨ TỰ HỌC

Ghi **tên tổ chức + tên tài nguyên**, không ghi URL (URL thay đổi; tên thì không). Một số thứ có thể đã đổi kể từ khi tôi kiểm tra (9/2026) — kiểm tra lại trước khi cam kết thời gian.

**Cách đọc bảng:** cột "Giờ" là ước lượng cho **mức độ sử dụng trong roadmap này**, không phải thời lượng đầy đủ của tài nguyên. Nhiều tài nguyên bạn chỉ dùng vài chương.

## 13.1 — Phase 0 · Bootstrap (~350 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | *The Missing Semester of Your CS Education* | MIT | môi trường | 15 | Shell, git, debugging — bắt đầu bằng cái này |
| 2 | *The C Programming Language* (K&R) | — | C1.1 | 40 | Làm hết bài tập, không đọc lướt |
| 3 | Python official tutorial + *Automate the Boring Stuff* | PSF / — | C1.2 | 30 | Đủ để viết script có test |
| 4 | *Beej's Guide to C* — miễn phí | — | C1.1 | 15 | Bổ sung cho K&R, hiện đại hơn |
| 5 | GDB tutorial + valgrind quickstart | GNU / — | C1.9 | 15 | **Không hoãn phần này** |
| 6 | *Pro Git* chương 1–3, 7 — miễn phí | — | C1.10 | 15 | Mô hình đối tượng ở chương 10 |
| 7 | Datasheet + getting-started của board bạn chọn | Espressif / ST / RPi | C6 | 40 | Primary source từ ngày đầu |
| 8 | *Mathematics for Computer Science* (6.042) chương 1–5 | MIT OCW | S1.1 | 40 | Logic, chứng minh, quy nạp |
| 9 | pytest documentation | — | C1.2 | 10 | |

## 13.2 — Phase 1 · Nền tính toán (~1.200 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | ***Nand2Tetris* phần 1** | Hebrew University of Jerusalem | C3.1–C3.3 | 70 | **ROI cao nhất của Phase 1.** Miễn phí trên trang chính thức và trên Coursera (audit) |
| 2 | *Computer Systems: A Programmer's Perspective* (CS:APP) + lab | CMU | C1.1, C1.4, C3.4–C3.6, C3.12 | 120 | Sách **đáng mua**; lab miễn phí và là phần giá trị nhất (Bomb, Attack, Cache, Malloc) |
| 3 | *Introduction to Algorithms* 6.006 | MIT OCW | C2.1–C2.9 | 90 | Làm problem set, không chỉ xem lecture |
| 4 | *Linear Algebra* 18.06 (Strang) | MIT OCW | S1.2 | 60 | Xem kèm *Essence of Linear Algebra* (3Blue1Brown) để có trực giác trước |
| 5 | *Essence of Linear Algebra* + *Essence of Calculus* | 3Blue1Brown | S1.2, S1.4 | 20 | Trực giác, không thay thế bài tập |
| 6 | *Mathematics for Computer Science* (6.042) phần còn lại | MIT OCW | S1.1 | 50 | Tổ hợp, đồ thị, xác suất rời rạc |
| 7 | *Modern C* (Jens Gustedt) — miễn phí | — | C1.1 | 30 | Chuẩn C hiện đại, UB, và cách viết C an toàn |
| 8 | *Operating Systems: Three Easy Pieces* (OSTEP) chương 1–20 — **miễn phí toàn văn** | University of Wisconsin–Madison | C4.1–C4.3 | 60 | Bắt đầu phần virtualization |
| 9 | *Algorithm Design Manual* (Skiena) — phần "war stories" | — | C2 | 20 | Nối lý thuyết với thực tế |
| 10 | *What Every Programmer Should Know About Memory* (Drepper) | — | C3.6, C2.11 | 15 | Dài nhưng đáng; đọc phần 1–5 |
| 11 | CMake tutorial + linker documentation | Kitware / GNU | C1.7 | 25 | Đủ để cross-compile |
| 12 | ARM Cortex-M Generic User Guide | ARM | C3.4, C6.1 | 25 | Primary source |
| 13 | RISC-V ISA specification (unprivileged) | RISC-V International | C3.4 | 15 | Đọc để so sánh với ARM |
| 14 | LeetCode / Codeforces | — | C2 | 60 | **Trần 80 h tổng cho cả roadmap** |

## 13.3 — Phase 2 · Nền hệ thống (~1.500 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | **OSTEP** chương 25–47 + project CS 537 | UW–Madison | C4.4–C4.9 | 120 | Concurrency và persistence; làm project |
| 2 | **CS144 + lab tự viết TCP** | Stanford | C5.1–C5.5, C5.10 | 120 | **Lab mạng giá trị nhất tồn tại công khai** |
| 3 | *Beej's Guide to Network Programming* — miễn phí | — | C5.10 | 10 | Đọc trước CS144 lab để khởi động |
| 4 | *Computer Networking: A Top-Down Approach* (Kurose & Ross) | — | C5 | 40 | Tham chiếu nền |
| 5 | *Database Systems* 15-445 | CMU Database Group | C9.1–C9.4 | 90 | Chất lượng cao bất thường; làm project |
| 6 | *The Linux Programming Interface* (Kerrisk) | — | C4.9, C4.12 | 40 | Tra cứu, không đọc tuần tự |
| 7 | *Probabilistic Systems Analysis* 6.041 | MIT OCW | S1.3 | 60 | Hoặc *Introduction to Probability* (Blitzstein, Harvard — miễn phí) |
| 8 | *An Introduction to Statistical Learning* — miễn phí | — | C8.1, C8.2 | 40 | Nền thống kê học; đọc trước mọi deep learning |
| 9 | *Designing Data-Intensive Applications* phần I | — | C9.1, C9.3 | 25 | **Đáng mua** |
| 10 | PostgreSQL documentation | PostgreSQL Global Dev Group | C9.2, C9.3 | 30 | Primary source |
| 11 | *Use The Index, Luke* — miễn phí | — | C9.2 | 15 | Index và query plan |
| 12 | *Fluent Python* | — | C1.2 | 30 | Python ở mức Advanced |
| 13 | RFC 9293 (TCP), RFC 9110–9114 (HTTP) | IETF | C5.5, C5.7 | 25 | Primary source; đọc khi cần chi tiết |
| 14 | Wireshark documentation + sample capture | Wireshark Foundation | C5.12 | 20 | |
| 15 | OpenTelemetry documentation | CNCF | C11.2 | 25 | Mô hình quan trọng hơn công cụ |
| 16 | *A Philosophy of Software Design* (Ousterhout) | — | C1.12, C12.3 | 15 | Ngắn, mật độ cao |
| 17 | Google *Technical Writing* courses — miễn phí | Google | S8 | 15 | |
| 18 | Reference manual của MCU bạn chọn | ST / Espressif / Nordic | C6.1–C6.3 | 60 | **Đọc nhiều nhất trong Phase 2 cho C6** |
| 19 | *The Scientist and Engineer's Guide to DSP* (Smith) chương 1–9 — **miễn phí** | — | C7.1, C7.2 | 30 | Lấy mẫu và aliasing trước mọi việc đọc cảm biến |

## 13.4 — Phase 3 · Vòng lặp khép lại (~1.600 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | FreeRTOS documentation + *Mastering the FreeRTOS Kernel* — miễn phí | FreeRTOS | C4.10, C6.7 | 35 | |
| 2 | Zephyr Project documentation | Zephyr Project / Linux Foundation | C6.7, C6.8, C6.12 | 35 | Mô hình khác FreeRTOS; đáng biết cả hai |
| 3 | *Making Embedded Systems* (White) | — | C6.12 | 20 | Kiến trúc firmware |
| 4 | *Test-Driven Development for Embedded C* (Grenning) | — | C6.12, S5.3 | 25 | Cách test firmware trên host |
| 5 | MCUboot documentation | MCUboot project | C6.10 | 20 | Bootloader và OTA |
| 6 | *The Scientist and Engineer's Guide to DSP* phần còn lại | — | C7.3, C7.4 | 20 | Lọc và FFT |
| 7 | *Understanding Digital Signal Processing* (Lyons) | — | C7.3, C7.4 | 30 | Sâu hơn Smith |
| 8 | CMSIS-DSP documentation | ARM | C7.3, C7.4 | 15 | DSP trên Cortex-M |
| 9 | Application note về nhiễu, nối đất, nguồn | Texas Instruments, Analog Devices | S2.3, S2.5, C7.5 | 30 | **Chất lượng rất cao, miễn phí** |
| 10 | *The Art of Electronics* chương 1, 8, 9 | — | S2.1, S2.6 | 25 | Tra cứu |
| 11 | *Kalman and Bayesian Filters in Python* (Labbe) — **miễn phí** | — | C7.8 | 30 | Notebook chạy được |
| 12 | *Feedback Systems* (Åström & Murray) — **miễn phí** | Caltech | S3, C7.12 | 30 | |
| 13 | Series "từ zero" của Andrej Karpathy | — | C8.4, C8.5 | 60 | **Đúng tinh thần §1.1**: micrograd → makemore → nanoGPT |
| 14 | *Practical Deep Learning for Coders* | fast.ai | C8.4, C8.7 | 50 | Vào nhanh, engineering-first |
| 15 | CS231n | Stanford | C8.5 | 45 | Thị giác |
| 16 | *Designing Data-Intensive Applications* phần II | — | C10.3, C10.4, C10.6 | 30 | |
| 17 | *Distributed Systems* lecture series (Kleppmann) — miễn phí | University of Cambridge | C10.2, C10.3 | 35 | |
| 18 | MQTT 5.0 specification | OASIS | C5.8 | 12 | Primary source |
| 19 | Paper Gorilla (nén chuỗi thời gian) | — | C9.5 | 8 | Primary source |
| 20 | TimescaleDB / ClickHouse / Prometheus TSDB docs | vendor | C9.5 | 25 | So sánh ba mô hình |
| 21 | Kafka documentation + *Kafka: The Definitive Guide* | Apache / — | C9.9 | 35 | |
| 22 | *Systems Performance* (Gregg) chương 1–6 | — | C11.1, C11.4, C11.6 | 30 | |
| 23 | *TinyML* (Warden & Situnayake) | — | C6.14, C7.10, C8.9 | 40 | |
| 24 | TensorFlow Lite Micro documentation | Google | C6.14 | 20 | |
| 25 | Edge Impulse documentation | Edge Impulse | C6.14 | 20 | Học workflow, rồi **tự dựng lại bằng tay** |
| 26 | Edge AI Foundation — tài liệu và talk công khai | Edge AI Foundation | C6.14 | 15 | Trạng thái hiện tại của lĩnh vực |
| 27 | *The Rust Book* **hoặc** *A Tour of Go* + *Effective Go* | Rust / Go teams | C1.3 | 60 | Chọn một |
| 28 | Datasheet + AN của mọi cảm biến bạn dùng | vendor | C7.6, C7.7 | 30 | Primary source |
| 29 | NIST — tài liệu về bất định đo | NIST | C7.7 | 15 | |

## 13.5 — Phase 4 · Quy mô & production (~1.500 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | ***Distributed Systems* 6.824 + lab Raft** | MIT | C10.1–C10.5 | 110 | Lab Raft là chuẩn vàng |
| 2 | Paper Raft (*In Search of an Understandable Consensus Algorithm*) | — | C10.5 | 10 | Primary source |
| 3 | *Site Reliability Engineering* + *SRE Workbook* — **miễn phí toàn văn** | Google | C11.3, C11.9, C11.11, C10.10 | 45 | Đọc chương SLO trước |
| 4 | *Systems Performance* (Gregg) phần còn lại | — | C11.6, C11.7 | 25 | |
| 5 | *BPF Performance Tools* (Gregg) | — | C4.13, C11.6 | 25 | |
| 6 | *Release It!* (Nygard) | — | C10.10, C11.12 | 20 | Mẫu ổn định |
| 7 | Kubernetes documentation — phần Concepts | CNCF | C10.12 | 35 | **Bỏ qua tutorial cho tới khi hiểu Concepts** |
| 8 | *Programming Kubernetes* hoặc kubebuilder book | — | C10.12 | 25 | Viết controller |
| 9 | OpenTofu / Terraform documentation | OpenTofu / HashiCorp | C10.13 | 25 | Mô hình giống nhau ở cả hai |
| 10 | vLLM documentation + blog kỹ thuật | vLLM project | C8.10 | 30 | **Primary source cho serving** |
| 11 | Paper PagedAttention | — | C8.10 | 8 | |
| 12 | Paper FlashAttention | — | C8.5, C8.10 | 8 | |
| 13 | Paper LoRA, AWQ, GPTQ | — | C8.8, C8.9 | 15 | |
| 14 | CUDA Programming Guide | NVIDIA | C3.9 | 30 | |
| 15 | *Programming Massively Parallel Processors* | — | C3.9 | 25 | |
| 16 | CS336 *Language Modeling from Scratch* | Stanford | C8.5, C8.10 | 50 | |
| 17 | CS224n | Stanford | C8.5 | 45 | Ngôn ngữ |
| 18 | *Designing Machine Learning Systems* (Chip Huyen) | — | C8.14, C8.15, C8.16 | 25 | |
| 19 | MCP specification | Linux Foundation | C8.11 | 10 | Primary source |
| 20 | LangGraph documentation | LangChain | C8.12 | 20 | **Trần cứng 20 h** |
| 21 | *Building Secure and Reliable Systems* — miễn phí | Google | S4, C12.14 | 25 | |
| 22 | OWASP Top 10 + OWASP LLM Top 10 | OWASP | S4.7 | 15 | |
| 23 | *Security Engineering* (Ross Anderson) — **miễn phí bản 3** | — | S4 | 25 | Chọn chương |
| 24 | NASA Fault Tree Handbook — miễn phí | NASA | S6.2 | 15 | |
| 25 | *Quantitative System Performance* — miễn phí | — | S7, C11.5 | 20 | |
| 26 | Bài viết Jepsen (Kyle Kingsbury) | Jepsen | C10.3, C10.4 | 20 | Kiểm chứng thực nghiệm các tuyên bố về nhất quán |
| 27 | Postmortem công khai (Google, Cloudflare, GitHub, AWS) | các công ty | C11.9 | 25 | **Đọc ≥20 cái** |
| 28 | Parquet + Arrow specification | Apache | C9.6 | 15 | |
| 29 | Paper HNSW | — | C9.8 | 8 | |
| 30 | ROS 2 documentation | Open Robotics | A1.1 | 30 | |
| 31 | *Ironies of Automation* (Bainbridge) | — | A3.2 | 3 | Ngắn, kinh điển, đọc được trong một buổi |

## 13.6 — Phase 5 · Kiến trúc & chuyên sâu (~1.450 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | *Software Architecture in Practice* (Bass, Clements, Kazman) | SEI / Carnegie Mellon | C12.1, C12.2 | 35 | |
| 2 | *Fundamentals of Software Architecture* (Richards & Ford) | — | C12.8 | 25 | |
| 3 | *Designing Data-Intensive Applications* phần III | — | C12.9 | 20 | |
| 4 | Mô hình C4 — tài liệu Simon Brown | — | C12.12, S8.3 | 10 | |
| 5 | Bài gốc về ADR (Michael Nygard) + kho mẫu ADR | — | C12.12, S8.2 | 10 | |
| 6 | Design doc và RFC công khai (Rust RFC, Kubernetes KEP, IETF) | — | S8.1 | 25 | **Đọc ≥15 cái** để thấy cấu trúc tốt |
| 7 | *Engineering a Safer World* (Leveson) | MIT | S6, A3 | 30 | STAMP — tiếp cận khác biệt và đáng đọc |
| 8 | IEC 60812 (FMEA) hoặc hướng dẫn công khai tương đương | IEC / — | C12.5, S6.2 | 15 | |
| 9 | *Normal Accidents* (Perrow) | — | S6 | 20 | Trực giác về lỗi trong hệ phức tạp |
| 10 | Báo cáo điều tra tai nạn (NTSB, hàng không) | NTSB | S6, A3.2 | 20 | Nguồn học tập chất lượng rất cao về failure analysis |
| 11 | *Is Parallel Programming Hard* (McKenney) — miễn phí | — | C4.6, C4.7 | 30 | Nâng cao |
| 12 | Văn bản EU AI Act + GDPR (phần liên quan) | EU | A5.1, A5.2 | 20 | Primary source |
| 13 | Nghị định bảo vệ dữ liệu cá nhân của Việt Nam | Chính phủ VN | A5.2 | 10 | |
| 14 | choosealicense.com + SPDX license list + OSI | — | A6.1 | 10 | |
| 15 | Source code của một dự án bạn chọn để đóng góp | — | P7b, C1.11 | 100+ | Đây là "tài nguyên" chính của Phase 5 |
| 16 | *The Art of Capacity Planning* (Allspaw) | — | S7.2 | 15 | |
| 17 | *Accelerate* (Forsgren, Humble, Kim) | — | A4 | 12 | |
| 18 | *The Goal* (Goldratt) | — | A4.1 | 12 | Tiểu thuyết về lý thuyết ràng buộc |

## 13.6b — Tài nguyên cho tầng công nghiệp (OT)

*Bổ sung ở v3, phục vụ các leaf mới C5.16, C6.16, S3.8, S4.9, C12.15. Phần lớn học được **tại công việc**; danh sách này để bạn học có hệ thống thay vì học ngẫu nhiên theo dự án được giao.*

| Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|
| Tài liệu chính thức TIA Portal / STEP 7 | Siemens | C6.16 | 40 | **Primary source.** Đọc phần kiến trúc hệ thống, không chỉ phần thao tác |
| Tài liệu ABB 800xA hoặc AC500 | ABB | C6.16 | 30 | Tùy hệ bạn gặp |
| IEC 61131-3 — chuẩn hoặc tài liệu diễn giải | IEC / PLCopen | C6.16 | 20 | Ngôn ngữ lập trình PLC, vendor-neutral |
| PLCopen — tài liệu công khai | PLCopen | C6.16 | 15 | Khối chức năng chuẩn hóa, motion control |
| Modbus Application Protocol Specification | Modbus Organization | C5.16 | 8 | Ngắn, đọc hết được. Primary source |
| IEC 61850 — tài liệu giới thiệu và SCL | IEC / vendor | C5.16 | 30 | Mô hình dữ liệu phân cấp là phần đáng học nhất |
| IEC 60870-5-104 / DNP3 — tài liệu kỹ thuật | IEC / DNP Users Group | C5.16 | 15 | Telemetry SCADA |
| OPC UA specification + companion spec | OPC Foundation | C5.16, C12.15 | 30 | **Cầu nối IT/OT quan trọng nhất.** Đọc phần information model |
| Profinet / Profibus — tài liệu kỹ thuật | PI (Profibus & Profinet International) | C5.16 | 20 | |
| *Process Dynamics and Control* (Seborg et al.) | — | S3.8 | 35 | Sách chuẩn cho điều khiển quá trình công nghiệp |
| *Practical Process Control* (Blevins/Nixon) hoặc tương đương | — | S3.8 | 20 | Thực hành hơn Seborg |
| ISA-95 / IEC 62264 — tài liệu giới thiệu | ISA / IEC | C12.15 | 20 | |
| IEC 62443 — tài liệu giới thiệu và hướng dẫn | IEC / ISA | S4.9 | 25 | An ninh hệ điều khiển công nghiệp |
| CISA — hướng dẫn công khai về ICS security | CISA | S4.9 | 15 | Miễn phí, chất lượng cao |
| Grid code Việt Nam và thông tư đấu nối | Bộ Công Thương / EVN | S3.8, A5 | 15 | Ràng buộc pháp lý định hình kiến trúc điều khiển |
| Tài liệu inverter / turbine của nhà sản xuất | vendor | C7, S3.8 | 30 | Primary source cho hệ bạn thực sự gặp |
| *The Unified Namespace* — tài liệu và thảo luận công khai | cộng đồng IIoT | C12.15 | 10 | Xu hướng đang định hình lại ISA-95 |

**[Recommendation] về cách dùng danh mục này:** đừng đọc trước. Đọc **ngay sau** khi gặp thứ đó ở công việc — đó là lúc bạn có ngữ cảnh để hiểu, và là lúc kiến thức dính lại. Với mỗi tài nguyên, viết ra bảng ánh xạ sang khái niệm trung lập (§2.3d). Ngân sách: ~380 h, rải đều 5 năm, **phần lớn trong giờ làm việc**.

---


## 13.7 — Tài nguyên tra cứu suốt 5 năm

| Tài nguyên | Dùng cho |
|---|---|
| Linux man pages (mục 2, 3, 7) | C1, C4 — tra hàng ngày |
| Datasheet, reference manual, errata, application note của vendor | C6, C7, S2 — **primary source quan trọng nhất của nhánh phần cứng** |
| RFC (IETF) | C5 — khi cần chi tiết chính xác |
| Documentation chính thức của mọi công cụ bạn dùng | Luôn đọc trước blog post |
| CLRS (*Introduction to Algorithms*) | C2 — tra cứu, không đọc tuần tự |
| *Computer Architecture: A Quantitative Approach* (Hennessy & Patterson) | C3 — tra cứu |

## 13.8 — Về tài nguyên trả phí

Chỉ **ba** thứ tôi cho là đáng trả tiền, và không thứ nào bắt buộc:

| # | Thứ | Vì sao | Chi phí ước tính |
|---|---|---|---|
| 1 | *Designing Data-Intensive Applications* | Khó thay thế bằng nguồn miễn phí; mật độ kiến thức cao nhất trong danh mục | ~1tr VND |
| 2 | *Computer Systems: A Programmer's Perspective* | Lab miễn phí nhưng sách làm chúng dễ tiêu hóa hơn nhiều | ~1,5tr VND |
| 3 | **Phần cứng** (Phụ lục A) | ROI cao nhất trong toàn bộ roadmap | 8–15tr VND rải 5 năm |

Cộng thêm, tùy tình huống: **thuê GPU theo giờ** (§0.2), ước tính 3–8tr VND tổng cho Phase 1–4 nếu có kỷ luật bật/tắt.

**Certification:** [Recommendation] không mua trong 2 năm đầu. Cân nhắc lại ở Phase 4, và **chỉ khi** một nhà tuyển dụng cụ thể yêu cầu tên cụ thể.

**Khóa học trả phí trên các nền tảng thương mại:** [Recommendation] không. Mọi thứ trong danh mục trên đều có chất lượng cao hơn, và phần lớn miễn phí. Ngoại lệ duy nhất đáng cân nhắc: một khóa có **phòng lab phần cứng thật** mà bạn không tự dựng được.

## 13.9 — Cách dùng tài nguyên — ba quy tắc

1. **Primary source trước blog post.** Datasheet, RFC, specification, documentation chính thức. Blog post để hiểu nhanh; primary source để hiểu đúng. Với nhánh phần cứng, tỷ lệ này nghiêng hẳn về primary source.

2. **Một tài nguyên một lúc cho mỗi nhánh.** Đọc song song ba cuốn về cùng một chủ đề cho cảm giác bận rộn và kết quả nông. Chọn một, làm hết bài tập, rồi chuyển.

3. **Tài nguyên không có bài tập thì không tính là đã học.** Với mọi tài nguyên trong danh mục, tìm bài tập — có sẵn, hoặc bạn tự đặt ra bằng cách lấy checkpoint ở §5 làm đề.

---
---

## ✎ Phần của tôi — theo dõi

| Tài nguyên | Nhánh | Bắt đầu | Xong | Giờ thật | Đáng không (1–5) |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

