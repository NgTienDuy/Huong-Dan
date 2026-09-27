---
loai: meta
ma: M20
tieu_de: "Từ điển tra cứu Việt → Anh theo nhánh"
---

# 20 · Từ điển tra cứu: tiếng Việt → tiếng Anh

> **Mục đích duy nhất:** bạn đọc một sub-leaf bằng tiếng Việt trong roadmap, và cần biết **gõ chữ gì vào ô tìm kiếm**.
> Đây không phải từ điển dịch thuật — đây là **từ khoá tra cứu**. Cột phải là thứ bạn gõ, nguyên văn.

**Cách dùng:** mở file leaf → đọc tiêu đề sub-leaf → tra bảng của nhánh tương ứng → gõ cụm tiếng Anh → áp mẫu truy vấn ở [`19-CACH-TIM-TAI-LIEU.md`](19-CACH-TIM-TAI-LIEU.md) §6.

**Nếu không có trong bảng:** phần lớn sub-leaf trong roadmap **đã chứa sẵn thuật ngữ tiếng Anh** (Bloom filter, HyperLogLog, PagedAttention, MVCC…). Bảng này chỉ liệt kê những chỗ roadmap **dịch sang tiếng Việt** — tức là đúng những chỗ mà gõ tiếng Việt sẽ không ra gì.

> ⚠ Một cảnh báo: đừng gõ cụm tiếng Việt vào ô tìm kiếm rồi kết luận "không có tài liệu". Gần như mọi lần, tài liệu có — bằng tiếng Anh, rất nhiều, và tốt.

---

## C1 · Programming & language runtimes

**Nguồn cấp 1 điển hình:** chuẩn ngôn ngữ (ISO C), tài liệu chính thức của toolchain, source code thư viện chuẩn.
**Truy vấn mở đầu:** `<term> C standard` · `<term> compiler explorer` · `<term> "undefined behavior"`

| Roadmap (VI) | Gõ cái này |
|---|---|
| số học con trỏ | pointer arithmetic |
| con trỏ hàm | function pointer |
| mảng suy biến thành con trỏ | array decay |
| đệm và căn chỉnh struct | struct padding and alignment |
| trường bit | bit field |
| hành vi không xác định | undefined behavior |
| quy ước gọi hàm | calling convention / ABI |
| bộ cấp phát vùng / bể | arena allocator / pool allocator |
| cấp phát tĩnh | static allocation |
| quản lý bộ nhớ thủ công | manual memory management |
| bố cục bộ nhớ tiến trình | process memory layout |
| khung ngăn xếp | stack frame |
| phân mảnh heap | heap fragmentation |
| dùng sau khi giải phóng | use-after-free |
| thu gom rác | garbage collection |
| hệ thống kiểu | type system |
| thiết kế interface | interface design |
| ngữ nghĩa lỗi | error semantics / error handling strategy |
| hệ thống build | build system |
| chuỗi công cụ | toolchain |
| liên kết tĩnh / động | static linking / dynamic linking |
| biên dịch chéo | cross-compilation |
| nội tại runtime | runtime internals |
| công cụ truy vết | tracing tools |
| đọc mã nguồn dự án lớn | reading large codebases |
| mẫu thiết kế | design pattern |
| phát triển có AI hỗ trợ | AI-assisted development / AI pair programming |

---

## C2 · Data structures & algorithms

**Nguồn cấp 1:** sách giáo trình + lecture notes đại học. Đây là nhánh mà sách thắng tuyệt đối.
**Truy vấn mở đầu:** `<term> lecture notes filetype:pdf` · `<term> invariant proof` · `<term> when does it fail`

| Roadmap (VI) | Gõ cái này |
|---|---|
| phân tích độ phức tạp | complexity analysis / asymptotic analysis |
| phân tích khấu hao | amortized analysis |
| bảng băm | hash table |
| va chạm | hash collision |
| nối chuỗi vs địa chỉ mở | chaining vs open addressing |
| hệ số tải, băm lại | load factor, rehashing |
| cây tìm kiếm nhị phân | binary search tree |
| cây cân bằng | self-balancing tree |
| hàng đợi ưu tiên | priority queue |
| đồ thị, danh sách kề | graph, adjacency list |
| duyệt theo chiều rộng / sâu | breadth-first / depth-first search |
| sắp xếp tô-pô | topological sort |
| thành phần liên thông mạnh | strongly connected component |
| cây khung nhỏ nhất | minimum spanning tree |
| đường đi ngắn nhất | shortest path |
| luồng cực đại, lát cắt nhỏ nhất | max-flow min-cut |
| sắp xếp ngoài | external merge sort |
| chọn phần tử thứ k | selection / quickselect |
| quy hoạch động | dynamic programming |
| bài toán con gối nhau | overlapping subproblems |
| ghi nhớ | memoization |
| tham lam | greedy algorithm |
| lập luận trao đổi | exchange argument |
| cấu trúc dữ liệu xác suất | probabilistic data structure |
| ước lượng lực lượng | cardinality estimation |
| lấy mẫu hồ chứa | reservoir sampling |
| ước lượng phân vị | quantile estimation |
| nhận biết cache | cache-aware / cache-oblivious algorithm |
| chia ô | loop tiling / blocking |
| mảng cấu trúc vs cấu trúc mảng | array of structs vs struct of arrays (AoS/SoA) |
| chia sẻ sai | false sharing |
| tìm nạp trước | prefetching |
| thuật toán trực tuyến | online algorithm |
| cửa sổ trượt | sliding window |
| không khóa | lock-free |
| so sánh và hoán đổi | compare-and-swap |
| thu hồi theo kỷ nguyên | epoch-based reclamation |

---

## C3 · Computer architecture & digital logic

**Nguồn cấp 1:** sách kiến trúc + optimization manual của Intel/ARM/AMD + tài liệu PMU.
**Truy vấn mở đầu:** `<term> microarchitecture` · `<vendor> optimization manual <term>` · `perf <term> counter`

| Roadmap (VI) | Gõ cái này |
|---|---|
| mạch tổ hợp | combinational logic |
| mạch tuần tự | sequential logic |
| bảng chân lý, dạng chuẩn tắc | truth table, canonical form |
| bản đồ Karnaugh | Karnaugh map |
| bộ chọn kênh, bộ giải mã | multiplexer, decoder |
| độ trễ lan truyền, đường tới hạn | propagation delay, critical path |
| máy trạng thái Moore / Mealy | Moore / Mealy state machine |
| vượt miền xung nhịp | clock domain crossing |
| thiết lập / giữ, siêu ổn định | setup/hold time, metastability |
| đường dữ liệu, khối điều khiển | datapath, control unit |
| chu trình nạp–giải mã–thực thi | fetch-decode-execute cycle |
| xung đột dữ liệu, chuyển tiếp, dừng | data hazard, forwarding, stall |
| dự đoán nhánh | branch prediction |
| thực thi suy đoán | speculative execution |
| thực thi ngoài thứ tự | out-of-order execution |
| đa luồng đồng thời | simultaneous multithreading |
| phân cấp bộ nhớ | memory hierarchy |
| nguyên lý cục bộ | locality of reference |
| mạch lạc cache | cache coherence |
| mô hình nhất quán bộ nhớ | memory consistency model |
| hàng rào bộ nhớ | memory barrier / memory fence |
| thứ tự thu nhận / giải phóng | acquire/release ordering |
| tính toán vector | vectorization |
| tự động vector hoá | auto-vectorization |
| phân kỳ warp | warp divergence |
| gộp truy cập bộ nhớ | memory coalescing |
| mảng tâm thu | systolic array |
| độ phủ toán tử | operator coverage |
| biểu diễn số | number representation |
| dấu phẩy động | floating point |
| hủy bỏ thảm khốc | catastrophic cancellation |
| công suất động / tĩnh | dynamic / static power |
| điều chỉnh xung nhịp theo nhiệt | thermal throttling |
| bộ đếm hiệu năng phần cứng | hardware performance counters (PMU) |

---

## C4 · Operating systems & concurrency

**Nguồn cấp 1:** man page, Linux kernel documentation, source code, POSIX spec.
**Truy vấn mở đầu:** `man 2 <syscall>` · `<term> site:docs.kernel.org` · `<term> lwn.net`

| Roadmap (VI) | Gõ cái này |
|---|---|
| chuyển ngữ cảnh | context switch |
| khối điều khiển tiến trình | process control block |
| tiến trình mồ côi / zombie | orphan / zombie process |
| an toàn trong bộ xử lý tín hiệu | async-signal-safe |
| lập lịch | scheduling |
| lập lịch đơn điệu theo tốc độ | rate-monotonic scheduling |
| hạn chót sớm nhất trước | earliest deadline first |
| phân tích khả năng lập lịch | schedulability analysis |
| đảo ngược ưu tiên | priority inversion |
| kế thừa ưu tiên | priority inheritance |
| bộ nhớ ảo, phân trang | virtual memory, paging |
| bảng trang, đi bảng trang | page table, page table walk |
| lỗi trang nhỏ / lớn | minor / major page fault |
| sao chép khi ghi | copy-on-write |
| trang lớn | huge page |
| cấp phát quá mức | memory overcommit |
| đập (bộ nhớ) | thrashing |
| hệ thống file nhật ký | journaling filesystem |
| ngữ nghĩa độ bền | durability semantics (fsync) |
| cache trang | page cache |
| mô hình I/O chặn / không chặn | blocking / non-blocking I/O |
| ghép kênh I/O | I/O multiplexing |
| kích hoạt theo mức / theo cạnh | level-triggered / edge-triggered |
| vòng lặp sự kiện | event loop |
| sao chép không | zero-copy |
| áp lực ngược | backpressure |
| loại trừ lẫn nhau | mutual exclusion |
| biến điều kiện | condition variable |
| thức dậy giả | spurious wakeup |
| khóa đọc–ghi | reader-writer lock |
| rào chắn | barrier / latch |
| lưu trữ cục bộ theo luồng | thread-local storage |
| truyền thông điệp, mô hình actor | message passing, actor model |
| đánh cắp công việc | work stealing |
| bể luồng | thread pool |
| bế tắc, khoá sống, bỏ đói | deadlock, livelock, starvation |
| đồ thị chờ | wait-for graph |
| giao tiếp liên tiến trình | inter-process communication |
| tính toán thời gian thực | real-time computing |
| không gian tên, nhóm điều khiển | namespace, cgroup |
| hệ thống file lớp | union / overlay filesystem |
| giảm quyền | privilege dropping |
| quan sát kernel | kernel observability / tracing |

---

## C5 · Networking

**Nguồn cấp 1:** RFC (rfc-editor.org), spec giao thức, packet capture của chính bạn.
**Truy vấn mở đầu:** `<term> RFC` · `<term> wireshark` · `<term> failure mode`

| Roadmap (VI) | Gõ cái này |
|---|---|
| đóng khung | framing |
| phát hiện lỗi, tổng kiểm | error detection, checksum, CRC |
| đóng gói | encapsulation |
| miền va chạm | collision domain |
| chuyển mạch, bảng địa chỉ | switching, MAC address table |
| giả mạo ARP | ARP spoofing |
| khung lớn | jumbo frame |
| chia mạng con | subnetting |
| dịch địa chỉ mạng | network address translation |
| phát hiện MTU đường truyền | path MTU discovery |
| định tuyến tĩnh / động | static / dynamic routing |
| phát đa hướng | multicast |
| lọc đường về | reverse path filtering |
| bắt tay ba bước | three-way handshake |
| điều khiển tắc nghẽn | congestion control |
| khởi động chậm | slow start |
| tích băng thông–độ trễ | bandwidth-delay product |
| chặn đầu hàng | head-of-line blocking |
| phân giải đệ quy / lặp | recursive / iterative resolution |
| cache âm | negative caching |
| khám phá dịch vụ | service discovery |
| thương lượng nội dung | content negotiation |
| ghép kênh luồng | stream multiplexing |
| bắt tay TLS | TLS handshake |
| chuỗi chứng chỉ | certificate chain |
| bí mật chuyển tiếp hoàn hảo | perfect forward secrecy |
| xác thực hai chiều | mutual TLS |
| thu hồi chứng chỉ | certificate revocation |
| ghim chứng chỉ | certificate pinning |
| xoay vòng chứng chỉ | certificate rotation |
| đọc/ghi một phần | partial read / partial write |
| đóng duyên dáng | graceful shutdown |
| cạn kiệt cổng tạm | ephemeral port exhaustion |
| phình bộ đệm | bufferbloat |
| quản lý hàng đợi chủ động | active queue management |
| bắt gói | packet capture |
| vượt NAT | NAT traversal |
| kết nối khởi tạo từ thiết bị | outbound-only connection |
| giãn cách theo cấp số nhân + nhiễu | exponential backoff with jitter |
| thiết kế ưu tiên ngoại tuyến | offline-first design |
| phân vùng một chiều | one-way network partition |
| lỗi xám | gray failure |
| bão thử lại | retry storm |
| sụp đổ do tắc nghẽn | congestion collapse |
| đám đông sấm sét | thundering herd |
| giao thức công nghiệp | industrial protocol / fieldbus |
| bản đồ thanh ghi | register map |
| mã chức năng | function code |
| thứ tự byte | endianness |
| đồng hồ phân tán | distributed clock |
| mô hình thông tin | information model |
| đặc tả đồng hành | companion specification |
| cổng chuyển giao thức | protocol gateway |

---

## C6 · Embedded systems & firmware

**Nguồn cấp 1:** datasheet + reference manual + **errata** + application note của nhà sản xuất.
**Truy vấn mở đầu:** `<part> reference manual` · `<part> errata` · `<vendor> application note <term>`

| Roadmap (VI) | Gõ cái này |
|---|---|
| bản đồ bộ nhớ | memory map |
| cây xung nhịp | clock tree |
| miền nguồn | power domain |
| bộ điều khiển ngắt lồng nhau | nested vectored interrupt controller (NVIC) |
| vector reset, mã khởi động | reset vector, startup code |
| chức năng thay thế của chân | pin alternate function |
| đặc tính điện | electrical characteristics |
| chống dội | debouncing |
| bộ chia trước, tự nạp lại | prescaler, auto-reload |
| thu giữ đầu vào | input capture |
| thời gian chết (cầu nửa) | dead-time (half-bridge) |
| trình xử lý ngắt | interrupt service routine |
| độ trễ ngắt, rung pha | interrupt latency, jitter |
| kéo dài xung nhịp | clock stretching |
| phân xử bus | bus arbitration |
| điện trở kéo lên | pull-up resistor |
| khôi phục bus | I2C bus recovery |
| điều khiển luồng | flow control |
| khung lỗi, tắt bus | error frame, bus-off (CAN) |
| điện trở kết cuối | termination resistor |
| điện áp tham chiếu | voltage reference |
| lấy mẫu quá mức | oversampling |
| điều hòa tín hiệu | signal conditioning |
| thu thập phân tán | scatter-gather DMA |
| đệm vòng | circular buffer |
| đệm đôi | double buffering |
| căn chỉnh bộ đệm | buffer alignment |
| kịch bản liên kết | linker script |
| tô màu ngăn xếp, canary | stack painting, stack canary |
| tràn ngăn xếp | stack overflow |
| bộ nhớ EEPROM mô phỏng | emulated EEPROM |
| san bằng hao mòn | wear leveling |
| thông báo tác vụ | task notification |
| nghỉ không tick | tickless idle |
| siêu vòng lặp | superloop |
| đơn vị bảo vệ bộ nhớ | memory protection unit (MPU) |
| chế độ ngủ sâu | deep sleep / standby mode |
| nguồn đánh thức | wakeup source |
| chu kỳ hoạt động | duty cycling |
| chạy nhanh rồi ngủ | race-to-sleep |
| ngân sách năng lượng | energy budget |
| bộ nạp khởi động | bootloader |
| phân vùng A/B | A/B partitioning |
| cập nhật qua mạng | over-the-air update (OTA) |
| cập nhật sai khác | delta update |
| chống quay lui | anti-rollback |
| triển khai theo giai đoạn | staged rollout |
| điểm dừng phần cứng | hardware breakpoint |
| điểm theo dõi | watchpoint |
| lớp trừu tượng phần cứng | hardware abstraction layer (HAL) |
| tiêm phụ thuộc | dependency injection |
| bộ xử lý lỗi nghiêm trọng | fault handler / hard fault |
| khởi động an toàn | secure boot |
| phần tử an toàn | secure element |
| cấp phát danh tính tại nhà máy | factory provisioning |
| bảo vệ đọc ngược | readout protection |
| tấn công gây lỗi | fault injection / glitching attack |
| kênh bên | side-channel |
| thời gian thực hiện xấu nhất | worst-case execution time (WCET) |
| phân tích thời gian đáp ứng | response time analysis |
| giám sát, cửa sổ giám sát | watchdog, windowed watchdog |
| chu kỳ quét | scan cycle |
| ảnh quá trình | process image |
| khối tổ chức | organization block |
| biến giữ lại | retentive variable |
| dự phòng nóng | hot standby redundancy |
| chuyển đổi không va đập | bumpless transfer |

---

## C7 · Sensing, signals & physical interface

**Nguồn cấp 1:** sách DSP + application note của TI/Analog Devices + datasheet cảm biến.
**Truy vấn mở đầu:** `<term> DSP` · `analog devices application note <term>` · `<sensor> calibration procedure`

| Roadmap (VI) | Gõ cái này |
|---|---|
| định lý lấy mẫu | sampling theorem (Nyquist–Shannon) |
| chồng phổ | aliasing |
| bộ lọc chống chồng phổ | anti-aliasing filter |
| giảm mẫu có lọc | decimation |
| lấy mẫu dải thông | bandpass sampling |
| rung pha của xung nhịp lấy mẫu | sampling clock jitter |
| nhiễu lượng tử hoá | quantization noise |
| số bit hiệu dụng | effective number of bits (ENOB) |
| sàn nhiễu | noise floor |
| nhiễu nhiệt / bắn / nhấp nháy | thermal / shot / flicker noise |
| dải động | dynamic range |
| phi tuyến tích phân / vi phân | integral / differential nonlinearity (INL/DNL) |
| trôi theo nhiệt độ | temperature drift |
| đáp ứng xung | impulse response |
| pha tuyến tính | linear phase |
| thiết kế bằng cửa sổ | window method filter design |
| trung bình trượt hàm mũ | exponential moving average |
| lọc trung vị | median filter |
| độ trễ nhóm | group delay |
| điểm cố định | fixed-point arithmetic |
| lọc đa tốc độ | multirate filtering |
| rò rỉ phổ | spectral leakage |
| hàm cửa sổ | window function |
| mật độ phổ công suất | power spectral density |
| phương pháp Welch | Welch's method |
| nội suy đỉnh | peak interpolation |
| nhiễu điện từ | electromagnetic interference (EMI) |
| ghép nối dẫn / cảm ứng / điện dung | conductive / inductive / capacitive coupling |
| vòng lặp đất | ground loop |
| mặt phẳng đất | ground plane |
| tụ tách nguồn | decoupling capacitor |
| cặp vi sai, loại bỏ nhiễu chung | differential pair, common-mode rejection |
| che chắn | shielding |
| cách ly | galvanic isolation |
| chế độ hỏng của cảm biến | sensor failure mode |
| kẹt giá trị | stuck-at / frozen value |
| bão hòa | saturation |
| lão hoá | aging / drift over life |
| hiệu chuẩn | calibration |
| độ chính xác vs độ chụm | accuracy vs precision |
| truy xuất nguồn gốc | metrological traceability |
| bù phi tuyến | nonlinearity compensation |
| hiệu chuẩn tại chỗ | in-situ calibration |
| sắt cứng / sắt mềm (từ kế) | hard-iron / soft-iron calibration |
| bất định đo | measurement uncertainty |
| truyền bất định | uncertainty propagation |
| hợp nhất cảm biến | sensor fusion |
| bộ lọc bổ sung | complementary filter |
| ước lượng trạng thái | state estimation |
| bộ lọc hạt | particle filter |
| hợp nhất tư thế | attitude/orientation fusion (AHRS) |
| trôi xung nhịp | clock drift |
| đồng hồ đơn điệu vs đồng hồ tường | monotonic clock vs wall clock |
| nhảy giây | leap second |
| căn chỉnh chuỗi thời gian | time-series alignment |
| tái lấy mẫu | resampling |
| trích xuất đặc trưng | feature extraction |
| tốc độ cắt không | zero-crossing rate |
| trọng tâm phổ | spectral centroid |
| hệ số đỉnh | crest factor |
| đặc trưng đường bao | envelope feature |
| chấp hành | actuation |
| cầu H | H-bridge |
| mất bước (động cơ bước) | step loss / missed steps |
| tải cảm | inductive load |
| điốt dập | flyback diode |
| mạch hãm | snubber |
| khóa liên động | interlock |

---

## C8 · Machine learning & inference systems

**Nguồn cấp 1:** paper gốc trên arXiv + docs của engine (vLLM, ONNX Runtime, TensorRT).
**Truy vấn mở đầu:** `<term> site:arxiv.org` · `<term> original paper` · `<engine> docs <term>`

| Roadmap (VI) | Gõ cái này |
|---|---|
| học có giám sát / không giám sát / tự giám sát | supervised / unsupervised / self-supervised learning |
| đánh đổi độ chệch–phương sai | bias-variance tradeoff |
| quá khớp / thiếu khớp | overfitting / underfitting |
| chính quy hoá | regularization |
| dừng sớm | early stopping |
| tăng cường dữ liệu | data augmentation |
| kiểm định chéo | cross-validation |
| rò rỉ dữ liệu | data leakage |
| ma trận nhầm lẫn | confusion matrix |
| hiệu chuẩn xác suất | probability calibration |
| biểu đồ độ tin cậy | reliability diagram |
| ngưỡng quyết định | decision threshold |
| đánh giá theo lát cắt | slice-based evaluation |
| mất cân bằng lớp | class imbalance |
| đường cơ sở | baseline |
| tập đánh giá | evaluation set / holdout set |
| lan truyền ngược | backpropagation |
| vi phân tự động | automatic differentiation |
| đồ thị tính toán | computational graph |
| lịch trình tốc độ học | learning rate schedule |
| khởi tạo trọng số | weight initialization |
| chuẩn hoá theo lô / theo lớp | batch norm / layer norm |
| trường tiếp nhận | receptive field |
| tích chập tách theo chiều sâu | depthwise separable convolution |
| phát hiện đối tượng | object detection |
| mã hoá vị trí | positional encoding |
| nhúng | embedding |
| học tương phản | contrastive learning |
| sụp đổ biểu diễn | representation / embedding collapse |
| dịch chuyển phân phối | distribution shift |
| theo dõi thí nghiệm | experiment tracking |
| khả năng tái lập | reproducibility |
| điểm kiểm tra | checkpointing |
| độ chính xác hỗn hợp | mixed precision |
| tinh chỉnh | fine-tuning |
| quên thảm hoạ | catastrophic forgetting |
| nén model | model compression |
| lượng tử hoá sau huấn luyện | post-training quantization |
| huấn luyện nhận biết lượng tử hoá | quantization-aware training |
| dữ liệu hiệu chuẩn | calibration dataset |
| ngoại lai trong kích hoạt | activation outliers |
| cắt tỉa có / không cấu trúc | structured / unstructured pruning |
| chưng cất tri thức | knowledge distillation |
| đường cong Pareto | Pareto frontier |
| gộp lô liên tục | continuous batching |
| giai đoạn nạp / giải mã | prefill / decode phase |
| song song tensor / pipeline | tensor / pipeline parallelism |
| giải mã suy đoán | speculative decoding |
| chia sẻ tiền tố | prefix sharing |
| khởi động nguội | cold start |
| thời gian tới token đầu tiên | time to first token (TTFT) |
| cửa sổ ngữ cảnh | context window |
| đầu ra có cấu trúc | structured output |
| gọi công cụ | tool calling |
| ràng buộc bằng văn phạm | grammar-constrained decoding |
| truy hồi lai | hybrid retrieval |
| xếp hạng lại | reranking |
| bộ nhớ đệm ngữ nghĩa | semantic cache |
| thực thi bền vững | durable execution |
| rào chắn | guardrail |
| ngân sách bước / token | step / token budget |
| dịch chuyển dữ liệu / khái niệm | data drift / concept drift |
| độ trễ nhãn | label delay |
| suy giảm âm thầm | silent degradation |
| vòng phản hồi tự củng cố | self-reinforcing feedback loop |
| tự tin sai | overconfidence / miscalibration |
| tối ưu sai mục tiêu | reward hacking / specification gaming |
| ngộ độc dữ liệu | data poisoning |
| tấn công đối kháng | adversarial attack |

---

## C9 · Data engineering & storage

**Nguồn cấp 1:** docs của chính hệ CSDL bạn dùng + paper gốc (Dynamo, Bigtable, LSM, Gorilla).
**Truy vấn mở đầu:** `<db> docs <term>` · `<term> original paper` · `EXPLAIN ANALYZE <term>`

| Roadmap (VI) | Gõ cái này |
|---|---|
| đại số quan hệ | relational algebra |
| chuẩn hoá (CSDL) | database normalization (1NF–BCNF) |
| phi chuẩn hoá | denormalization |
| mô hình hoá chiều | dimensional modeling |
| lược đồ sao / bông tuyết | star schema / snowflake schema |
| chiều thay đổi chậm | slowly changing dimension |
| khoá tự nhiên / thay thế | natural key / surrogate key |
| nguồn sự kiện | event sourcing |
| hàm cửa sổ (SQL) | window function |
| biểu thức bảng chung | common table expression (CTE) |
| truy vấn con tương quan | correlated subquery |
| kế hoạch truy vấn | query plan |
| chỉ mục phủ / một phần | covering / partial index |
| mức cô lập | isolation level |
| đọc bẩn / đọc không lặp lại / bóng ma | dirty read / non-repeatable read / phantom read |
| lệch ghi | write skew |
| mất cập nhật | lost update |
| điều khiển đồng thời nhiều phiên bản | multiversion concurrency control (MVCC) |
| khoá khoảng | gap lock |
| leo thang khoá | lock escalation |
| khoá lạc quan / bi quan | optimistic / pessimistic locking |
| khuếch đại ghi / đọc / không gian | write / read / space amplification |
| dồn nén (LSM) | compaction |
| nhật ký ghi trước | write-ahead log (WAL) |
| bể đệm | buffer pool |
| lưu theo hàng / theo cột | row-oriented / columnar storage |
| mã hoá delta, XOR | delta encoding, XOR encoding (Gorilla) |
| giảm mẫu, gộp trước | downsampling, rollup |
| chính sách lưu giữ | retention policy |
| dữ liệu đến muộn | late-arriving / out-of-order data |
| đẩy vị từ xuống | predicate pushdown |
| cắt tỉa phân vùng | partition pruning |
| vấn đề file nhỏ | small files problem |
| định dạng bảng | table format (Iceberg, Delta) |
| cache-aside, ghi xuyên qua | cache-aside, write-through |
| chính sách thu hồi | eviction policy |
| vô hiệu hoá cache | cache invalidation |
| giẫm đạp cache | cache stampede |
| hết hạn sớm theo xác suất | probabilistic early expiration |
| tìm kiếm láng giềng gần xấp xỉ | approximate nearest neighbor (ANN) |
| lượng tử hoá tích | product quantization |
| độ bao phủ (recall) | recall |
| lọc theo siêu dữ liệu | metadata filtering |
| nhật ký chỉ ghi thêm | append-only log |
| nhóm tiêu thụ, tái cân bằng | consumer group, rebalance |
| nén log | log compaction |
| nhà sản xuất bất biến | idempotent producer |
| thời gian sự kiện vs thời gian xử lý | event time vs processing time |
| tính toán tăng tiến | incremental computation |
| nạp bù lịch sử | backfill |
| tiến hoá lược đồ | schema evolution |
| tương thích ngược / tiến | backward / forward compatibility |
| sổ đăng ký lược đồ | schema registry |
| hợp đồng dữ liệu | data contract |
| dòng dõi dữ liệu | data lineage |
| độ tươi | data freshness |
| điểm khôi phục / thời gian khôi phục | recovery point objective / recovery time objective (RPO/RTO) |
| khôi phục tới thời điểm | point-in-time recovery |
| lưu trữ lạnh | cold storage |
| quyền được xoá | right to erasure |

---

## C10 · Distributed systems & cloud

**Nguồn cấp 1:** paper kinh điển + Jepsen reports + docs của hệ bạn đang chạy.
**Truy vấn mở đầu:** `<system> jepsen` · `<term> paper` · `<term> failure mode production`

| Roadmap (VI) | Gõ cái này |
|---|---|
| lỗi từng phần | partial failure |
| dừng khi lỗi / chậm khi lỗi | fail-stop / fail-slow |
| lỗi Byzantine | Byzantine fault |
| lỗi xám | gray failure |
| phân vùng mạng | network partition |
| lỗi tương quan | correlated failure |
| quan hệ xảy-ra-trước | happens-before relation |
| đồng hồ Lamport / vector | Lamport clock / vector clock |
| đồng hồ lai | hybrid logical clock |
| biên bất định của đồng hồ | clock uncertainty bound |
| tuyến tính hoá | linearizability |
| nhất quán nhân quả | causal consistency |
| nhất quán cuối cùng | eventual consistency |
| đọc được cái mình vừa ghi | read-your-writes consistency |
| kiểu dữ liệu sao chép không xung đột | CRDT |
| sao chép một lãnh đạo / nhiều lãnh đạo | single-leader / multi-leader replication |
| độ trễ sao chép | replication lag |
| chuyển đổi dự phòng | failover |
| bầu lãnh đạo | leader election |
| não chia đôi | split-brain |
| thẻ rào | fencing token |
| sửa chữa khi đọc | read repair |
| chống entropy | anti-entropy |
| ghi cuối thắng | last-write-wins |
| đồng thuận | consensus |
| kết quả bất khả thi FLP | FLP impossibility |
| thay đổi thành viên cụm | cluster membership change |
| hợp đồng thuê của lãnh đạo | leader lease |
| ngữ nghĩa giao hàng | delivery semantics |
| khoá bất biến | idempotency key |
| khử trùng lặp | deduplication |
| hành động bù trừ | compensating action |
| mẫu hộp thư đi / hộp thư đến | outbox / inbox pattern |
| hoà giải | reconciliation |
| phân mảnh | sharding |
| băm nhất quán | consistent hashing |
| tái cân bằng | rebalancing |
| phân vùng nóng | hot partition |
| khoá phân vùng | partition key |
| chỉ mục toàn cục / cục bộ | global / local secondary index |
| ghép nối thời gian | temporal coupling |
| lan truyền hạn chót | deadline propagation |
| sự kiện mỏng / dày | thin event / event-carried state transfer |
| điều phối vs vũ đạo | orchestration vs choreography |
| loại bỏ tải | load shedding |
| giới hạn tốc độ | rate limiting |
| thùng token / thùng rò | token bucket / leaky bucket |
| cầu dao | circuit breaker |
| vách ngăn | bulkhead |
| suy giảm duyên dáng | graceful degradation |
| thăm dò sống / sẵn sàng | liveness / readiness probe |
| vòng lặp điều hoà | reconciliation loop |
| trạng thái mong muốn | desired state |
| hạ tầng dưới dạng mã | infrastructure as code |
| trôi cấu hình | configuration drift |
| chủ động–chủ động / chủ động–bị động | active-active / active-passive |
| trọng lực dữ liệu | data gravity |
| chủ quyền dữ liệu | data sovereignty |

---

## C11 · Observability, reliability & performance

**Nguồn cấp 1:** Google SRE book, AWS Builders' Library, postmortem công khai, docs OpenTelemetry.
**Truy vấn mở đầu:** `<term> SRE` · `<company> postmortem <term>` · `<term> "we learned"`

| Roadmap (VI) | Gõ cái này |
|---|---|
| đo đạc / thiết bị hoá mã | instrumentation |
| bùng nổ lực lượng nhãn | label cardinality explosion |
| log có cấu trúc | structured logging |
| lan truyền ngữ cảnh | context propagation |
| quy ước ngữ nghĩa | semantic conventions |
| lấy mẫu theo đầu / theo đuôi | head-based / tail-based sampling |
| chỉ số cấp dịch vụ | service level indicator (SLI) |
| ngân sách lỗi | error budget |
| cảnh báo theo tốc độ tiêu thụ | burn-rate alerting |
| phân vị | percentile |
| phân vị không cộng được | percentiles are not additive |
| bỏ sót phối hợp | coordinated omission |
| khuếch đại đuôi | tail amplification |
| yêu cầu phòng hờ | hedged request |
| lập hồ sơ lấy mẫu | sampling profiler |
| biểu đồ ngọn lửa | flame graph |
| lập hồ sơ ngoài CPU | off-CPU profiling |
| tranh chấp khoá | lock contention |
| khoảng dư | headroom |
| kiểm thử tải: tăng dần / ngâm / đột biến | ramp / soak / spike test |
| điểm gãy | breaking point |
| phân loại sự cố | incident triage |
| chỉ huy sự cố | incident commander |
| sổ tay xử lý | runbook |
| khám nghiệm không đổ lỗi | blameless postmortem |
| tiêm lỗi | fault injection |
| bán kính nổ | blast radius |
| ngày diễn tập | game day |
| cảnh báo theo triệu chứng | symptom-based alerting |
| mệt mỏi cảnh báo | alert fatigue |
| gom nhóm, chống trùng | alert grouping, deduplication |
| leo thang | escalation |
| kiểm tra sức khoẻ nông / sâu | shallow / deep health check |
| mã tương quan | correlation ID |
| phát lại | replay |
| lưu lượng bóng | shadow traffic |
| quy kết chi phí | cost attribution |
| chi phí ẩn | hidden cost |

---

## C12 · Systems architecture & integration

**Nguồn cấp 1:** sách kiến trúc + ADR công khai + kiến trúc tham chiếu của nhà cung cấp.
**Truy vấn mở đầu:** `<term> architecture decision record` · `<term> reference architecture` · `<term> tradeoff analysis`

| Roadmap (VI) | Gõ cái này |
|---|---|
| yêu cầu chức năng / phi chức năng | functional / non-functional requirement |
| thuộc tính chất lượng | quality attribute |
| kịch bản chất lượng | quality attribute scenario |
| chiến thuật kiến trúc | architectural tactic |
| ràng buộc cứng / ưu tiên mềm | hard constraint / soft preference |
| khả năng tiến hoá | evolvability |
| khả năng vận hành | operability |
| mặt Pareto | Pareto frontier |
| che giấu thông tin | information hiding |
| hợp đồng interface | interface contract |
| kiểm thử hợp đồng | contract testing |
| phiên bản hoá API | API versioning |
| chiến lược ngừng hỗ trợ | deprecation strategy |
| mặt phẳng dữ liệu / điều khiển | data plane / control plane |
| phân tích chế độ hỏng và tác động | failure mode and effects analysis (FMEA) |
| phân tích cây lỗi | fault tree analysis |
| phân tích cây sự kiện | event tree analysis |
| điểm hỏng đơn | single point of failure |
| lỗi im lặng | silent failure |
| nguồn sự thật duy nhất | single source of truth |
| trạng thái dẫn xuất | derived state |
| kiến trúc lục giác | hexagonal architecture |
| cổng và bộ điều hợp | ports and adapters |
| khối đơn dạng module | modular monolith |
| khối đơn phân tán (mẫu chống) | distributed monolith (anti-pattern) |
| kiến trúc tham chiếu | reference architecture |
| tổng chi phí sở hữu | total cost of ownership |
| khoá nhà cung cấp | vendor lock-in |
| chi phí thoát | switching / exit cost |
| cây bóp nghẹt | strangler fig pattern |
| ghi kép | dual write |
| đọc bóng | shadow read |
| cờ tính năng | feature flag |
| mở rộng–di trú–thu hẹp | expand–migrate–contract |
| xanh–lam / kim tước | blue-green / canary deployment |
| bản ghi quyết định kiến trúc | architecture decision record (ADR) |
| sơ đồ tuần tự | sequence diagram |
| ranh giới tin cậy | trust boundary |
| đặc quyền tối thiểu | least privilege |
| tối thiểu hoá dữ liệu | data minimization |
| kiến trúc phân tầng công nghiệp | industrial automation hierarchy |
| không gian tên hợp nhất | unified namespace |

---

## S1 · Mathematics

**Nguồn cấp 1:** sách giáo trình + lecture notes. Toán không có "phiên bản mới".
**Truy vấn mở đầu:** `<term> lecture notes pdf` · `<term> intuition` · `<term> worked example`

| Roadmap (VI) | Gõ cái này |
|---|---|
| tập hợp, quan hệ, hàm | sets, relations, functions |
| logic mệnh đề / vị từ | propositional / predicate logic |
| chứng minh phản chứng | proof by contradiction |
| quy nạp | mathematical induction |
| quan hệ đệ quy | recurrence relation |
| bất biến | loop invariant |
| không gian vector, cơ sở | vector space, basis |
| hạng, hạt nhân | rank, null space (kernel) |
| trị riêng, vector riêng | eigenvalue, eigenvector |
| phân rã giá trị kỳ dị | singular value decomposition |
| chuẩn | norm |
| phép chiếu, bình phương tối thiểu | projection, least squares |
| biến ngẫu nhiên | random variable |
| kỳ vọng, phương sai, hiệp phương sai | expectation, variance, covariance |
| xác suất có điều kiện | conditional probability |
| luật số lớn | law of large numbers |
| định lý giới hạn trung tâm | central limit theorem |
| ước lượng điểm / khoảng | point / interval estimation |
| kiểm định giả thuyết | hypothesis testing |
| lỗi loại I / loại II | type I / type II error |
| công suất thống kê | statistical power |
| vấn đề nhiều so sánh | multiple comparisons problem |
| kiểm định hoán vị | permutation test |
| quy tắc chuỗi | chain rule |
| ma trận Jacobi / Hessian | Jacobian / Hessian matrix |
| điểm yên ngựa | saddle point |
| khai triển Taylor | Taylor expansion |
| hàm lồi, tập lồi | convex function, convex set |
| tốc độ hội tụ | convergence rate |
| nhân tử Lagrange | Lagrange multiplier |
| tối ưu đa mục tiêu | multi-objective optimization |
| sai số làm tròn | rounding error |
| số điều kiện | condition number |
| ổn định số | numerical stability |
| tổng có bù | compensated (Kahan) summation |
| phân rã LU / QR | LU / QR decomposition |
| phương pháp lặp | iterative method |
| entropy có điều kiện | conditional entropy |
| thông tin tương hỗ | mutual information |
| dung lượng kênh | channel capacity |
| tỷ lệ–méo | rate–distortion |
| định luật Little | Little's law |
| ký hiệu Kendall | Kendall's notation |
| mức sử dụng | utilization |
| biến đổi Fourier rời rạc | discrete Fourier transform |
| tích chập | convolution |
| định lý Parseval | Parseval's theorem |
| biến đổi Laplace / Z | Laplace / Z transform |

---

## S2 · Electronics & power

**Nguồn cấp 1:** datasheet, application note của TI / Analog Devices, sách mạch kinh điển.
**Truy vấn mở đầu:** `ti.com application note <term>` · `<term> layout guidelines` · `<part> datasheet`

| Roadmap (VI) | Gõ cái này |
|---|---|
| định luật Kirchhoff | Kirchhoff's laws |
| phân áp / phân dòng | voltage / current divider |
| hằng số thời gian RC | RC time constant |
| transistor như khoá | transistor as a switch |
| trở kháng vào / ra | input / output impedance |
| phối hợp trở kháng | impedance matching |
| mạch tương đương Thévenin | Thévenin equivalent |
| phiếu dữ liệu | datasheet |
| đặc tính tuyệt đối tối đa | absolute maximum ratings |
| điều kiện hoạt động khuyến nghị | recommended operating conditions |
| kiểu đóng gói | package type |
| hết vòng đời | end-of-life (EOL) |
| ổn áp tuyến tính | linear regulator (LDO) |
| điện áp rơi tối thiểu | dropout voltage |
| nguồn chuyển mạch tăng / giảm áp | buck / boost converter |
| tụ tách nguồn | decoupling capacitor |
| thứ tự cấp nguồn | power sequencing |
| dòng khởi động | inrush current |
| sụt áp nguồn | brownout |
| giám sát nguồn và reset | supervisor / reset IC |
| hoá học pin | battery chemistry |
| đường cong phóng điện | discharge curve |
| điện áp cắt | cutoff voltage |
| tự phóng, dòng rò | self-discharge, leakage current |
| mạch bảo vệ pin | battery protection circuit |
| ngân sách năng lượng | energy budget |
| tính toàn vẹn tín hiệu | signal integrity |
| nhiễu xuyên âm | crosstalk |
| phản xạ, kết cuối đường truyền | reflection, transmission line termination |
| hạt ferrite | ferrite bead |
| điện trở shunt đo dòng | current sense shunt |
| máy hiện sóng: băng thông, đầu dò | oscilloscope bandwidth, probe |
| bộ phân tích logic | logic analyzer |
| bo cắm thử | breadboard |
| điện dung ký sinh | parasitic capacitance |
| hàn linh kiện dán | SMD soldering |
| trở kháng nhiệt | thermal resistance |
| nhiệt độ mối nối | junction temperature |
| tản nhiệt, đối lưu | heat sink, convection |

---

## S3 · Control theory & feedback

**Nguồn cấp 1:** sách điều khiển + tài liệu tuning của nhà cung cấp DCS/PLC.
**Truy vấn mở đầu:** `<term> control` · `PID tuning <process type>` · `<vendor> loop tuning guide`

| Roadmap (VI) | Gõ cái này |
|---|---|
| vòng hở / vòng kín | open-loop / closed-loop |
| tín hiệu đặt | setpoint |
| biến quá trình | process variable |
| nhiễu đo | measurement noise |
| độ nhạy, độ bền | sensitivity, robustness |
| chống bão hoà tích phân | integral anti-windup |
| chuyển chế độ không va đập | bumpless transfer |
| giới hạn tốc độ thay đổi | rate limiting / slew rate limiting |
| biên độ lợi, biên pha | gain margin, phase margin |
| đáp ứng bước | step response |
| vọt lố | overshoot |
| thời gian lên / ổn định | rise time / settling time |
| biểu đồ Bode | Bode plot |
| trễ vận chuyển | dead time / transport delay |
| không gian trạng thái | state space |
| điều khiển được / quan sát được | controllability / observability |
| phản hồi trạng thái | state feedback |
| bộ quan sát | state observer |
| bộ giữ mẫu bậc không | zero-order hold |
| rời rạc hoá | discretization |
| điều khiển tầng | cascade control |
| điều khiển tỷ lệ | ratio control |
| điều khiển chia dải | split-range control |
| chọn lựa / ghi đè | override / selective control |
| bù nhiễu trước | feedforward compensation |
| nhận dạng đối tượng | plant / system identification |
| bậc nhất có trễ | first-order plus dead time (FOPDT) |
| tách kênh | decoupling |
| dao động lan truyền | oscillation propagation / plant-wide oscillation |
| điều khiển dự báo theo mô hình | model predictive control (MPC) |
| tối ưu hoá thời gian thực | real-time optimization |
| trạng thái an toàn | fail-safe state |
| khoá liên động phần cứng | hardwired interlock |
| chính sách học được | learned policy |
| lớp an toàn bao quanh | safety shield / runtime assurance |

---

## S4 · Security engineering

**Nguồn cấp 1:** NIST publications, OWASP, spec crypto, hướng dẫn IEC 62443.
**Truy vấn mở đầu:** `<term> NIST` · `<term> OWASP` · `<term> threat model`

| Roadmap (VI) | Gõ cái này |
|---|---|
| mô hình hoá mối đe doạ | threat modeling |
| bề mặt tấn công | attack surface |
| ranh giới tin cậy | trust boundary |
| cây tấn công | attack tree |
| đặc quyền tối thiểu | principle of least privilege |
| danh tính và xác thực | identity and authentication |
| uỷ quyền | authorization |
| xác thực đa yếu tố | multi-factor authentication |
| quản lý bí mật | secrets management |
| xoay vòng khoá | key rotation |
| dẫn xuất khoá | key derivation |
| mã hoá có xác thực | authenticated encryption (AEAD) |
| chữ ký số | digital signature |
| số dùng một lần | nonce |
| khởi động an toàn, chuỗi tin cậy | secure boot, chain of trust |
| cầu chì một lần ghi | OTP fuse |
| bảo mật chuỗi cung ứng phần mềm | software supply chain security |
| bảng kê vật liệu phần mềm | software bill of materials (SBOM) |
| bản dựng tái lập | reproducible build |
| đảo ngược model | model inversion |
| suy luận thành viên | membership inference |
| trích xuất model | model extraction |
| ngộ độc dữ liệu | data poisoning |
| tiêm lời nhắc | prompt injection |
| ẩn danh hoá, giả danh hoá | anonymization, pseudonymization |
| riêng tư vi phân | differential privacy |
| tối thiểu hoá dữ liệu | data minimization |
| phân vùng và ống dẫn (OT) | zones and conduits (IEC 62443) |
| mức bảo mật | security level (SL) |
| vùng phi quân sự công nghiệp | industrial DMZ |
| truy cập từ xa của nhà cung cấp | vendor remote access |
| giám sát an ninh OT | OT network monitoring |

---

## S5 · Testing & verification

**Nguồn cấp 1:** docs của framework test + paper về property-based testing + sách testing.
**Truy vấn mở đầu:** `<term> testing` · `property based testing <language>` · `<term> flaky test`

| Roadmap (VI) | Gõ cái này |
|---|---|
| kim tự tháp kiểm thử | test pyramid |
| nhân đôi thử nghiệm | test double (mock, stub, fake, spy) |
| kiểm thử bất ổn | flaky test |
| độ phủ | code coverage |
| kiểm thử đột biến | mutation testing |
| kiểm thử dựa trên thuộc tính | property-based testing |
| thu nhỏ phản ví dụ | shrinking |
| bộ sinh dữ liệu | generator |
| kiểm thử hợp đồng | contract testing |
| kiểm thử trên máy chủ (firmware) | host-based testing |
| mô phỏng phần cứng | hardware emulation |
| kiểm thử bất biến biến hình | metamorphic testing |
| kiểm thử hồi quy | regression testing |
| bộ khung đánh giá | evaluation harness |
| tập vàng | golden set |
| kiểm thử mờ | fuzzing |
| bộ khử trùng | sanitizer (ASan, UBSan, TSan) |
| phương pháp hình thức | formal methods |
| kiểm tra mô hình | model checking |

---

## S6 · Reliability & safety

**Nguồn cấp 1:** sách độ tin cậy, hướng dẫn FMEA, tiêu chuẩn IEC 61508 (bản tóm tắt của nhà cung cấp).
**Truy vấn mở đầu:** `<term> reliability engineering` · `FMEA <domain> example` · `<term> IEC 61508`

| Roadmap (VI) | Gõ cái này |
|---|---|
| lỗi, sai, hỏng | fault, error, failure |
| thời gian trung bình giữa các lần hỏng | mean time between failures (MTBF) |
| thời gian trung bình để sửa | mean time to repair (MTTR) |
| tỷ lệ hỏng, đường cong bồn tắm | failure rate, bathtub curve |
| phân tích chế độ hỏng và tác động | FMEA |
| số ưu tiên rủi ro | risk priority number (RPN) |
| cây lỗi | fault tree |
| dự phòng | redundancy |
| chuyển đổi dự phòng | failover |
| lỗi nguyên nhân chung | common-cause failure |
| đa dạng hoá | diversity (design diversity) |
| bỏ phiếu đa số | majority voting (TMR) |
| lỗi tiềm ẩn | latent fault |
| độ phủ chẩn đoán | diagnostic coverage |
| kiểm tra định kỳ | proof test |
| mức toàn vẹn an toàn | safety integrity level (SIL) |
| vòng đời an toàn | safety lifecycle |
| người trong vòng lặp | human-in-the-loop |

---

## S7 · Queueing, capacity & economics

**Nguồn cấp 1:** sách hàng đợi + bài viết capacity planning của các công ty vận hành hệ lớn.
**Truy vấn mở đầu:** `<term> capacity planning` · `cost per <unit>` · `<term> unit economics`

| Roadmap (VI) | Gõ cái này |
|---|---|
| định luật Little | Little's law |
| mức sử dụng | utilization |
| đường cong mức sử dụng–độ trễ | utilization-latency curve |
| biến thiên thời gian phục vụ | service time variability |
| hàng đợi có giới hạn | bounded queue |
| kỷ luật hàng đợi | queueing discipline |
| lập kế hoạch capacity | capacity planning |
| chi phí cố định / biến đổi | fixed / variable cost |
| tổng chi phí sở hữu | total cost of ownership |
| chi phí mỗi suy luận | cost per inference |
| điểm hoà vốn | break-even point |
| mua hay tự xây | build vs buy |
| chi phí thoát | exit cost |
| kinh tế học đơn vị | unit economics |

---

## S8 · Technical communication

**Nguồn cấp 1:** ADR/RFC công khai của các dự án mã nguồn mở, sách viết kỹ thuật.
**Truy vấn mở đầu:** `architecture decision record template` · `design doc template engineering` · `postmortem example`

| Roadmap (VI) | Gõ cái này |
|---|---|
| tài liệu thiết kế | design doc |
| đề xuất kỹ thuật | RFC (request for comments) |
| bản ghi quyết định kiến trúc | architecture decision record (ADR) |
| phương án đã cân nhắc | considered alternatives |
| mô hình C4 | C4 model |
| sơ đồ tuần tự | sequence diagram |
| sơ đồ luồng dữ liệu | data flow diagram |
| khám nghiệm sau sự cố | postmortem |
| hạng mục hành động | action item |
| giải thích đánh đổi | explaining tradeoffs |
| sổ tay vận hành | runbook |
| tài liệu bàn giao | handover documentation |

---

## A1–A6 · Adjacent

### A1 · Robotics
| Roadmap (VI) | Gõ cái này |
|---|---|
| nút, chủ đề, dịch vụ, hành động | node, topic, service, action |
| chất lượng dịch vụ (DDS) | QoS policy |
| hệ toạ độ, phép biến đổi | coordinate frame, transform |
| ghi và phát lại | record and replay (rosbag) |
| pipeline nhận thức | perception pipeline |
| hiệu chuẩn ngoại | extrinsic calibration |
| đo đường đi | odometry |
| trôi tích luỹ | accumulated drift |
| đóng vòng | loop closure |
| bản đồ lưới chiếm dụng | occupancy grid map |
| không gian cấu hình | configuration space |
| lập kế hoạch dựa trên lấy mẫu | sampling-based planning |
| làm mượt quỹ đạo | trajectory smoothing |
| dừng khẩn cấp | emergency stop |
| giám sát tốc độ an toàn | safe speed monitoring |
| kiến trúc hai kênh | dual-channel architecture |

### A2 · Simulation
| Roadmap (VI) | Gõ cái này |
|---|---|
| mô phỏng sự kiện rời rạc | discrete-event simulation |
| độ trung thực | simulation fidelity |
| xác thực mô phỏng | simulation validation |
| phần cứng trong vòng lặp | hardware-in-the-loop (HIL) |
| dữ liệu tổng hợp | synthetic data |
| ngẫu nhiên hoá miền | domain randomization |
| khoảng cách mô phỏng–thực tế | sim-to-real gap |
| bản sao số | digital twin |

### A3 · Human factors
| Roadmap (VI) | Gõ cái này |
|---|---|
| mức độ tự chủ | levels of automation / autonomy |
| nhầm lẫn chế độ | mode confusion |
| bất ngờ do tự động hoá | automation surprise |
| thiên lệch tự động hoá | automation bias |
| ra khỏi vòng lặp | out-of-the-loop performance problem |
| mất kỹ năng | skill degradation |
| trình bày độ không chắc chắn | uncertainty visualization |
| hiệu chuẩn niềm tin | trust calibration |
| bàn giao ngữ cảnh | context handover |
| mù thay đổi | change blindness |
| nhận thức tình huống | situation awareness |

### A4 · Business & operations
| Roadmap (VI) | Gõ cái này |
|---|---|
| sơ đồ quy trình | process map |
| lý thuyết ràng buộc | theory of constraints |
| nút cổ chai | bottleneck |
| thời gian chu kỳ / thời gian chờ | cycle time / lead time |
| biến thiên trong quy trình | process variability |
| tự động hoá một phần | partial automation |
| chi phí của lỗi | cost of errors |
| dương tính giả / âm tính giả | false positive / false negative |
| quản lý thay đổi | change management |

### A5 · Standards & regulation
| Roadmap (VI) | Gõ cái này |
|---|---|
| phân tầng rủi ro | risk tiering / risk classification |
| hệ thống AI mục đích chung | general-purpose AI system |
| giám sát của con người | human oversight |
| phạm vi ngoài lãnh thổ | extraterritorial scope |
| cơ sở pháp lý xử lý dữ liệu | lawful basis for processing |
| quyền của chủ thể dữ liệu | data subject rights |
| chuyển dữ liệu xuyên biên giới | cross-border data transfer |
| đánh giá tác động | impact assessment (DPIA) |
| tương thích điện từ | electromagnetic compatibility (EMC) |
| phát xạ / miễn nhiễm | emissions / immunity |
| chứng nhận radio | radio type approval |
| an toàn chức năng | functional safety |

### A6 · Licensing & IP
| Roadmap (VI) | Gõ cái này |
|---|---|
| giấy phép dễ dãi | permissive license |
| giấy phép lây lan | copyleft license |
| phạm vi lây lan | copyleft scope |
| nghĩa vụ ghi công | attribution requirement |
| tương thích giấy phép | license compatibility |
| nguồn sẵn có (không phải mã nguồn mở) | source-available |
| liên kết tĩnh vs động | static vs dynamic linking (license implications) |
| giấy phép có hạn chế sử dụng | use-restricted license (RAIL) |
| điều khoản về đầu ra của model | model output terms |
| nguồn gốc dữ liệu | data provenance |
| sự đồng ý và phạm vi | consent and its scope |
| bí mật kinh doanh | trade secret |

---

## P · Peripheral

| Roadmap (VI) | Gõ cái này |
|---|---|
| sinh mã, tối ưu hoá của trình biên dịch | code generation, compiler optimization passes |
| thiết kế mạch số tuỳ biến | custom digital design (RTL) |
| thiết kế ăng-ten | antenna design |
| thiết kế cơ khí | mechanical design / CAD |
| trợ lý chứng minh | proof assistant |
| thiết kế để sản xuất | design for manufacturing (DFM) |
| hệ sinh thái framework giao diện | frontend framework ecosystem |
| tính toán lượng tử | quantum computing |
| sổ cái phân tán | distributed ledger |

---

## ✎ Từ của tôi

Thêm vào đây mỗi khi bạn mất >5 phút chỉ để tìm ra nên gõ chữ gì.

| Roadmap / công việc (VI) | Thuật ngữ tiếng Anh | Leaf | Ngày |
|---|---|---|---|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
