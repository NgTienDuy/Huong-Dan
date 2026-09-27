---
loai: meta
ma: M14
---
# 14 · Master checklist (Phụ lục C)

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# PHỤ LỤC C · MASTER CHECKLIST

Toàn bộ checkpoint từ §5, gom lại thành danh sách kiểm tra được. **Một nhánh chưa tick hết checkpoint thì chưa đạt mức mục tiêu, bất kể bạn đã đọc bao nhiêu.**

Ký hiệu: ★ = checkpoint quan trọng nhất của nhánh.

## C1 · Programming & Language Runtimes
- [ ] Ring buffer + state machine bằng C, không cấp phát động, sạch dưới valgrind và ASAN/UBSAN
- [ ] Giải thích padding mọi struct bạn định nghĩa mà không chạy `sizeof`
- [ ] Package Python: test ≥80% coverage, `mypy --strict` pass, `pip install .` từ repo sạch, có CLI và logging
- [ ] Port một service Python sang Go/Rust, đo chênh lệch p99 và bộ nhớ, giải thích nguyên nhân
- [ ] ★ Đọc core dump và giải thích nguyên nhân segfault
- [ ] Tính worst-case stack usage của một firmware và chứng minh không tràn
- [ ] Thiết kế API mà dùng sai thì compile fail — chứng minh bằng code sai cố ý không build được
- [ ] Bảng: mỗi dependency × cách hỏng × hành vi mong muốn × cơ chế hiện thực — bảo vệ được từng ô
- [ ] Cross-compile binary ARM từ x86, chạy trên board, giải thích từng dòng linker script
- [ ] Giải thích p99 tăng khi CPU chưa đầy 50% — chỉ ra do GC, do lock, hay do I/O bằng số liệu
- [ ] ★ Tìm bug chỉ xuất hiện dưới concurrency, sửa đúng nguyên nhân (không che bằng `sleep`)
- [ ] `git bisect` tìm commit gây regression trong repo ≥500 commit
- [ ] Rebase 10 commit lộn xộn thành 3 commit nguyên tử
- [ ] ★ Đọc một module của CPython/Linux/Redis/vLLM trong ≤6 h, vẽ lại data flow, viết một trang giải thích
- [ ] Thêm tính năng vào codebase của chính bạn từ 6 tháng trước, sửa ≤5 file
- [ ] Phát hiện output sai của AI và nói được sai ở đâu, vì sao

## C2 · Data Structures & Algorithms
- [ ] Phân tích amortized của một cấu trúc **bạn tự thiết kế**, chứng minh biên
- [ ] Hash table open addressing tự cài, đo hiệu năng vs thư viện chuẩn, giải thích chênh lệch
- [ ] Giải thích **bằng số** vì sao DB dùng B-tree không dùng BST (tính số lần đọc đĩa, n = 10⁹)
- [ ] Scheduler dùng heap cho RTOS đồ chơi, chạy đúng với 20 task khác chu kỳ
- [ ] Topological sort cho build system nhỏ, phát hiện chu trình và báo đúng chu trình nào
- [ ] Cài Dijkstra và nêu 2 trường hợp nó sai, có phản ví dụ
- [ ] Sắp xếp file 10 GB trên máy 8 GB RAM, đo số lần đọc/ghi đĩa, so với lý thuyết
- [ ] ★ Nhận ra cấu trúc DP trong bài toán **chưa từng gặp** trong ≤20 phút, viết hàm hồi quy
- [ ] Chứng minh hoặc bác bỏ tính tối ưu của một thuật toán tham lam bằng exchange argument
- [ ] Bloom filter giảm ≥80% truy vấn DB trong workload thật, đo FP rate thực tế vs lý thuyết
- [ ] ★ Tăng tốc vòng lặp ≥2× **chỉ bằng** đổi thứ tự truy cập hoặc bố cục dữ liệu
- [ ] Tính p99 trên stream 10⁸ mẫu không lưu toàn bộ, sai số < 1%
- [ ] Lock-free SPSC ring buffer, sạch dưới TSAN, lập luận bằng lời vì sao đúng
- [ ] Giải bài lạ mức trung bình-khó trong 45 phút

## C3 · Computer Architecture & Digital Logic
- [ ] ALU đầy đủ chức năng chỉ từ cổng NAND (nand2tetris 1–2)
- [ ] FSM cho một giao thức nối tiếp, cài bằng C, chạy trên MCU, xử lý trạng thái lỗi
- [ ] ★ nand2tetris phần 1 hoàn thành — CPU + assembler + chương trình chạy được
- [ ] Đọc disassembly `-O2` và giải thích mọi thay đổi so với `-O0`
- [ ] Hai phiên bản vòng lặp (có nhánh khó đoán / branchless), đo chênh lệch, xác nhận bằng `branch-misses`
- [ ] ★★ Workload thật: xác định memory-bound hay compute-bound bằng `perf`, blocking/tiling, speedup ≥3×, **giải thích bằng số liệu cache miss trước/sau**
- [ ] Code đồng bộ hóa chạy đúng trên x86 nhưng hỏng trên ARM — giải thích và sửa bằng barrier đúng
- [ ] Vector hóa một convolution 1-D, đo speedup, xác nhận lệnh SIMD trong disassembly
- [ ] Kernel GPU: xác định memory-bound hay compute-bound, giải thích bằng mô hình roofline
- [ ] Cùng model trên hai phần cứng khác nhau, đo latency + năng lượng, giải thích bằng đặc điểm kiến trúc
- [ ] DMA cho luồng ADC liên tục, đo mức giảm tải CPU, xử lý đúng mạch lạc cache
- [ ] ★★ Lượng tử hóa model sang int8, **định vị lớp nào gây mất chính xác nhiều nhất** bằng phân tích theo lớp
- [ ] Đo throttling trên SBC dưới tải 30 phút, đồ thị nhiệt–xung nhịp–thông lượng, đề xuất giảm thiểu có số
- [ ] `perf stat` phân biệt đúng nút thắt CPU / bộ nhớ / I/O ở cả ba trường hợp thử nghiệm

## C4 · Operating Systems & Concurrency
- [ ] Đo chi phí chuyển ngữ cảnh trên máy bạn, giải thích con số bằng những gì phải lưu/khôi phục
- [ ] Tái tạo priority inversion với 3 luồng, đo độ trễ, sửa bằng priority inheritance, số đo trước/sau
- [ ] Chẩn đoán thrashing từ số liệu (page fault, swap, latency), xác định nguyên nhân, sửa
- [ ] ★ Chứng minh mất dữ liệu khi thiếu `fsync` bằng thí nghiệm cắt điện; sửa và chứng minh không mất
- [ ] ★★ Tự viết event loop phục vụ 10.000 kết nối đồng thời trên một luồng
- [ ] ★ Bounded buffer producer-consumer bằng mutex + condvar, không busy-wait, xử lý spurious wakeup, sạch dưới TSAN với 8+8
- [ ] Pipeline 3 giai đoạn có backpressure, chứng minh bộ nhớ không tăng vô hạn khi nghẽn
- [ ] Từ stack dump toàn bộ luồng, xác định chu trình chờ và hai khóa gây deadlock
- [ ] Ba tình huống IPC khác nhau: chọn đúng cơ chế cho mỗi cái, bảo vệ bằng đo đạc
- [ ] Đo jitter tác vụ chu kỳ 1 ms trên MCU dưới tải, đưa xuống < 50 µs, giải thích từng nguồn đã loại
- [ ] ★ "Container" tối giản bằng `unshare` + `cgroup` + `chroot`, không dùng Docker
- [ ] Unit systemd có restart policy + device tree overlay cho cảm biến, chạy sau reboot không can thiệp
- [ ] eBPF/`bpftrace` trace một syscall path và tìm nguồn latency, không sửa code ứng dụng

## C5 · Networking
- [ ] Tính CRC bằng tay hoặc code từ đầu; giải thích vì sao CRC bắt lỗi burst mà checksum bỏ sót
- [ ] Đọc ARP table, dựng tình huống IP trùng, giải thích chính xác triệu chứng
- [ ] ★ Ba kịch bản radio (băng thông/tầm/pin): chọn đúng, tính link budget, **đo thực tế** xác nhận hoặc bác bỏ
- [ ] Chia subnet cho mạng 200 thiết bị 5 nhóm, viết bảng định tuyến, truy vết gói bằng lập luận rồi xác nhận bằng `traceroute`
- [ ] ★★ Từ packet capture, xác định đúng nguyên nhân thông lượng thấp ở ≥3 tình huống: giới hạn cửa sổ, mất gói, Nagle/delayed-ACK
- [ ] Chẩn đoán sự cố DNS cache bằng công cụ, chỉ ra tầng cache nào giữ bản ghi cũ
- [ ] Giải thích head-of-line blocking ở tầng nào trong HTTP/1.1, /2, /3; dựng thí nghiệm chứng minh
- [ ] ★ Bốn kịch bản messaging: chọn giao thức + QoS, bảo vệ bằng số (byte, số lần thức radio, năng lượng/thông điệp)
- [ ] mTLS giữa MCU và server, gồm cấp phát ban đầu và xoay vòng chứng chỉ; thiết bị vẫn kết nối sau khi cert cũ hết hạn
- [ ] ★ TCP server từ socket thuần, xử lý partial read/write, graceful shutdown, timeout, 10.000 kết nối
- [ ] Ngân sách độ trễ cho request xuyên 5 tầng: dự đoán p50/p99 **trước khi đo**, rồi đo và giải thích chênh lệch
- [ ] Wireshark tìm nguyên nhân kết nối treo, phân biệt mất gói / tường lửa im lặng / ứng dụng không đọc
- [ ] Vẽ đường đi gói tin từ Internet tới container, liệt kê mọi thành phần, xác định nơi mTLS bắt đầu/kết thúc
- [ ] ★★ Thiết bị mất mạng 6 h rồi khôi phục: 0 mất, 0 trùng, thứ tự đúng, không tăng đột biến tải (có đồ thị)
- [ ] Tái tạo retry storm trong lab, dập bằng jitter + circuit breaker, chứng minh bằng đồ thị
- [ ] **[v3]** Đọc dữ liệu từ thiết bị công nghiệp thật qua giao thức gốc, đưa lên hệ hiện đại, **viết ra chính xác cái gì mất trong lần dịch** (kiểu dữ liệu, timestamp, chất lượng, ngữ nghĩa)

## C6 · Embedded Systems & Firmware
- [ ] ★★ Cấu hình một peripheral chưa từng dùng **chỉ bằng reference manual và errata** — không ví dụ, không HAL vendor
- [ ] PWM đạt tần số + độ phân giải mục tiêu, đo bằng logic analyzer, sai số < 0,1%; độ trễ ngắt < 5 µs
- [ ] ★ Debug bus I²C câm bằng logic analyzer ở 3 tình huống: sai địa chỉ, thiếu pull-up, clock stretching
- [ ] Đo ENOB thực tế của ADC bằng thí nghiệm, so datasheet, giải thích chênh lệch
- [ ] Thu audio/ADC ≥16 kHz qua DMA vòng tròn đệm đôi, 1 giờ **không mất mẫu nào**, chứng minh bằng bộ đếm
- [ ] Chứng minh không tràn stack ở worst case bằng cả stack painting lẫn phân tích tĩnh, hai phương pháp đồng ý
- [ ] Chuyển firmware superloop 4 chức năng sang RTOS không tạo race mới; 24 h liên tục dưới tải, kiểm bằng trace
- [ ] Ba kịch bản: chọn bare-metal / RTOS / embedded Linux, bảo vệ bằng bảng định lượng (RAM, flash, boot time, jitter, chi phí)
- [ ] ★★ Node đạt tuổi thọ pin mục tiêu: **có phép tính ngân sách năng lượng chứng minh trước**, đo thực tế ≥2 tuần, so sánh
- [ ] ★★ OTA cắt điện ở 3 thời điểm khác nhau (tải / ghi / chuyển đổi), 20/20 lần thiết bị vẫn boot hợp lệ
- [ ] ★ Tìm bug chỉ xuất hiện ở tốc độ đầy đủ bằng SWO trace hoặc logic analyzer, không dùng breakpoint
- [ ] ★ ≥60% logic firmware chạy dưới unit test trên PC, trong CI
- [ ] Provision device identity + secure boot; firmware không ký **không boot**; khóa không đọc được qua debug
- [ ] ★★ Model chạy trên MCU trong ngân sách RAM cho trước, đo latency p99 + năng lượng/inference, độ chính xác trên eval set từ **thiết bị thật**
- [ ] Chứng minh tác vụ luôn hoàn thành trong deadline dưới tải xấu nhất (DMA chạy, mọi ngắt bắn, flash đang ghi)
- [ ] **[v3]** Cho một bài toán điều khiển: lập luận chọn PLC / MCU+RTOS / embedded Linux bằng bảng định lượng (tính xác định, chi phí, vòng đời, chứng nhận, nhân lực bảo trì)
- [ ] **[v3]** Viết cùng một logic điều khiển ở cả hai thế giới — ST trên PLC và C trên MCU — so sánh cái gì dễ hơn ở mỗi bên và vì sao

## C7 · Sensing, Signals & Physical Interface
- [ ] ★★ Tái tạo aliasing bằng thí nghiệm vật lý, **dự đoán chính xác tần số giả bằng công thức**, sửa bằng anti-alias filter, chứng minh biến mất
- [ ] Tính sàn nhiễu lý thuyết của chuỗi đo, đo thực tế, giải thích chênh lệch, chỉ ra nguồn nhiễu chiếm ưu thế
- [ ] Thiết kế filter đạt dải thông + độ suy giảm + độ trễ cho trước, cài trên MCU, đo đáp ứng tần số thực tế
- [ ] ★ Gắn IMU lên động cơ, tìm tần số cơ bản + harmonic, **phát hiện bất thường cố ý tạo ra** từ phổ
- [ ] Giảm nhiễu ≥10 dB bằng thay đổi phần cứng/đi dây, có số đo trước/sau
- [ ] Mỗi loại cảm biến dùng: ≥3 chế độ hỏng + cơ chế phát hiện; **tạo ra từng chế độ hỏng thật** và xác nhận phát hiện được
- [ ] ★★ Hiệu chuẩn một cảm biến, **chứng minh sai số RMS giảm** trên tập điểm độc lập
- [ ] Kalman 1-D tự cài (không thư viện), giải thích ý nghĩa vật lý từng ma trận, tốt hơn moving average trên dữ liệu thật
- [ ] ★★ Đo clock drift 48 h, tính ppm, dự đoán lệch sau 30 ngày; căn chỉnh chuỗi thời gian 2 thiết bị, **sự kiện đồng thời ghi nhận đồng thời** dưới ngưỡng
- [ ] Đặc trưng thủ công + model nhỏ đạt ≥ độ chính xác của model lớn trên dữ liệu thô; đo chênh lệch RAM/latency/năng lượng
- [ ] ★ Điều khiển tải thật với khóa liên động phần cứng; gây ra cả 3 loại lỗi phần mềm (treo, crash, giá trị điên rồ), không hư hại
- [ ] Tune PID trên hệ vật lý thật đạt overshoot + settling time mục tiêu, có đồ thị trước/sau

## C8 · Machine Learning & Inference Systems
- [ ] ★ Phát hiện rò rỉ dữ liệu trong pipeline do người khác viết, chỉ chính xác chỗ rò, ước lượng mức thổi phồng metric
- [ ] Đánh bại neural network bằng gradient boosting trên dữ liệu bảng, giải thích đặc điểm nào làm cây thắng
- [ ] ★★ Eval set bạn **tin tưởng**, viết ra bằng văn bản những gì nó **không** đo được, chứng minh bằng một ca điểm cao nhưng hỏng thật
- [ ] Tự cài backprop cho MLP bằng numpy thuần, khớp PyTorch tới 1e-6
- [ ] Vẽ luồng qua khối transformer, **tính bằng tay** bộ nhớ KV cache theo độ dài chuỗi + batch, xác nhận bằng đo
- [ ] Chẩn đoán retrieval trả kết quả vô nghĩa: xác định do model embedding / chuẩn hóa / chunking
- [ ] ★ Chạy lại thí nghiệm của chính bạn sau **3 tháng**, ra cùng kết quả trong sai số thống kê
- [ ] Fine-tune cho domain hẹp: cải thiện trên eval riêng **và** không tệ đi trên eval thứ hai
- [ ] ★★ Giảm ≥4× kích thước model dưới ngưỡng mất chính xác; **đường cong Pareto ≥4 cấu hình**; định vị lớp nhạy cảm nhất
- [ ] ★★ Tự deploy serving stack, **tăng throughput ≥2×** bằng cấu hình, có p50/p99 trước/sau, giải thích cơ chế mỗi cải thiện
- [ ] ★ Xây tính năng dùng LLM và **chứng minh bằng đo đạc** rằng một lời gọi structured output không đủ, trước khi thêm orchestration
- [ ] ★ Agent phục hồi đúng sau khi bị kill giữa chừng, tiếp tục từ đúng điểm dừng với trạng thái nhất quán
- [ ] ★★ Eval harness bắt được regression thật mà unit test bỏ lọt
- [ ] ★ Phát hiện drift **trước khi** ảnh hưởng người dùng: cảnh báo đúng lúc, không quá sớm (nhiễu), không quá muộn
- [ ] 3 phương án kiến trúc + bảng chi phí và độ trễ; bảo vệ được trước "vì sao không chọn cái rẻ hơn"
- [ ] ★ Liệt kê ≥5 cách hệ ML của bạn hỏng mà mọi dashboard vẫn xanh; thiết kế cơ chế phát hiện cho mỗi cái

## C9 · Data Engineering & Storage
- [ ] Schema cho hệ ≥100 thiết bị, ≥5 loại cảm biến, metadata thay đổi theo thời gian; bảo vệ **từng** lựa chọn phi chuẩn hóa
- [ ] ★ Tăng tốc truy vấn chậm **≥10×** bằng đọc query plan, ghi lại plan trước/sau
- [ ] Tái tạo write skew ở `repeatable read`, chứng minh gây kết quả sai, sửa bằng đúng công cụ
- [ ] Chọn storage engine cho workload ghi nặng, bảo vệ bằng phân tích khuếch đại ghi, xác nhận bằng benchmark
- [ ] ★★ 1 năm dữ liệu 100 thiết bị × 5 cảm biến × 1 Hz trong ngân sách; truy vấn "trung bình theo giờ, 30 ngày" < 1 giây
- [ ] Truy vấn 50 GB Parquet trên laptop 16 GB, < 60 giây, giải thích predicate pushdown loại bao nhiêu dữ liệu
- [ ] Chiến lược cache cho một tính năng + **chỉ ra tường minh kịch bản cache trả dữ liệu sai**, quyết định có chấp nhận được không
- [ ] Đường cong recall–latency cho ≥3 cấu hình ANN; **nêu trường hợp tìm kiếm từ khóa tốt hơn vector**
- [ ] ★ Giải thích bằng ví dụ cụ thể vì sao "exactly-once" phải làm ở tầng ứng dụng; chứng minh bằng test gửi trùng
- [ ] Ba yêu cầu nghiệp vụ: chọn batch/stream/micro-batch, bảo vệ bằng bảng (độ trễ, chi phí, số dòng code, số chế độ hỏng)
- [ ] ★★ 20 thiết bị offline 24 h cùng trở lại: 0 mất, 0 trùng, thứ tự đúng, **tải server không vượt 2×** (có đồ thị)
- [ ] Đổi schema (thêm trường, đổi kiểu), consumer cũ vẫn chạy, chứng minh bằng test tự động trong CI
- [ ] ★ Phát hiện cảm biến hỏng **từ tầng dữ liệu** trong ≤1 h, bằng cách gây hỏng thật (ngắt / che / làm nóng)
- [ ] ★ Khôi phục **thật** từ backup vào môi trường sạch, đo RTO và RPO thực tế, so với mục tiêu

## C10 · Distributed Systems & Cloud Infrastructure
- [ ] ★★ Liệt kê mọi điểm hỏng từng phần của một kiến trúc + hệ quả từ góc nhìn người dùng; kiểm chứng ≥5 cái bằng thử nghiệm
- [ ] Dựng tình huống sắp thứ tự theo timestamp cho kết quả **sai** với 2 máy đồng hồ lệch; sửa bằng đồng hồ logic
- [ ] Ba tính năng: chọn mô hình nhất quán, **mô tả chính xác người dùng thấy gì khi có sự cố**
- [ ] Tính cấu hình quorum cho mục tiêu chịu lỗi cho trước, chứng minh bằng thử nghiệm giết node
- [ ] Nêu 3 tình huống trong hệ của bạn mà đồng thuận là **sai** lời giải, chỉ ra lời giải đúng
- [ ] ★★ API idempotent, chứng minh bằng test tự động gửi mọi request 3 lần (kể cả ngắt giữa chừng), 0 tác dụng phụ trùng
- [ ] ★ Outbox pattern: 0 sự kiện mất khi kill ngay sau DB commit trước publish, lặp ≥50 lần
- [ ] Chọn partition key, chỉ ra kịch bản gây hot partition, ước lượng mức lệch tải, đề xuất giảm thiểu
- [ ] Chuyển luồng sync 3 bước sang event-driven, viết ra **chính xác bạn mất gì**
- [ ] ★★ Ở **3× tải thiết kế**: suy giảm có kiểm soát thay vì sập, có đồ thị throughput/latency/tỷ lệ lỗi
- [ ] Dựng hạ tầng từ zero với quyền tối thiểu; thử thao tác không được phép và thấy bị từ chối
- [ ] ★ Viết một controller tối giản điều hòa một CRD, chạy trong cluster, giải thích reconciliation loop bằng code của bạn
- [ ] ★ Phá hủy toàn bộ hạ tầng và dựng lại hoàn toàn từ code, 0 thao tác tay, dịch vụ hoạt động; đo thời gian
- [ ] 5 chức năng: quyết định vị trí tính toán, bảo vệ bằng số (băng thông, độ trễ, chi phí, hành vi offline)

## C11 · Observability, Reliability & Performance
- [ ] ★ 5 sự cố khác nhau: nói ngay tín hiệu nào nhìn trước + lý do; **dựng lại 5 sự cố đó thật** để kiểm chứng
- [ ] Trace một request xuyên ≥4 service + 1 thiết bị, xác định tầng gây chậm, có waterfall
- [ ] Định nghĩa SLO + error budget + cảnh báo burn-rate nhiều cửa sổ; **giải thích vì sao không chọn số 9 cao hơn** bằng chi phí
- [ ] ★★ Giải thích **bằng dữ liệu** vì sao p99 tệ trong khi p50 đẹp; phân rã latency theo tầng, xác định nguồn đuôi
- [ ] ★ **Dự đoán trước khi đo** độ trễ tăng bao nhiêu khi utilization 70% → 90%; đo và so, sai số < 2×
- [ ] ★ Tìm và sửa nút thắt thật bằng profiling; **chứng minh nút thắt bạn tưởng trước khi profile là sai**
- [ ] ★★ Lấy một benchmark công khai, chỉ ra **≥3 lỗi phương pháp**, chạy lại đúng cách, báo cáo khác biệt
- [ ] Load test tìm điểm gãy, mô tả **chính xác cách nó gãy** (thành phần, triệu chứng, có phục hồi không), kế hoạch mở rộng có số
- [ ] Postmortem blameless cho sự cố thật: timeline tới phút, ≥3 yếu tố góp phần, action item có tiêu chí hoàn thành
- [ ] ★★ Giết ngẫu nhiên một thành phần trong lúc phục vụ tải, hệ vẫn đạt SLO; lặp cho ≥5 thành phần (kể cả thiết bị vật lý)
- [ ] Giảm ≥50% số cảnh báo mà **không** giảm khả năng phát hiện; chứng minh bằng chạy lại sự cố lịch sử
- [ ] Mỗi dependency: định nghĩa hành vi khi nó chết, cài đặt, **chứng minh bằng thử nghiệm** (không bằng code review)
- [ ] Dashboard chi phí **theo tính năng**, xác định tính năng nào có tỷ lệ chi phí/giá trị tệ nhất
- [ ] ★ Tái hiện một lỗi production trong test bằng **replay** dữ liệu thật, xác định nguyên nhân, chứng minh bản sửa

## C12 · Systems Architecture & Integration
- [ ] ★ Từ một đoạn mô tả mơ hồ, rút ≥8 ràng buộc **định lượng** (có đơn vị và số), kiểm chứng với người đặt yêu cầu
- [ ] ★★ 3 kiến trúc cho cùng bài toán, mỗi cái tối ưu một thuộc tính, bảng so sánh định lượng, bảo vệ trước 3 phản biện khác nhau
- [ ] ★ Thay đổi cài đặt một service **không phá consumer nào**, chứng minh bằng contract test chạy consumer cũ
- [ ] Vẽ riêng data flow và control flow, xác định mọi điểm giao, **chứng minh control plane chết không làm data plane chết**
- [ ] ★★ FMEA đầy đủ ≥30 chế độ hỏng, tìm **≥3 chế độ hỏng chưa từng nghĩ tới**, thêm phát hiện/giảm thiểu cho mỗi cái
- [ ] ★★ 5 chức năng: quyết định vị trí tính toán với lập luận định lượng đầy đủ (byte, độ trễ, chi phí/tháng, hành vi offline); thực hiện và đo — sai bao nhiêu?
- [ ] Bản đồ **mọi nơi** một sự thật được lưu, chỉ ra nguồn sự thật, mô tả cơ chế hòa giải khi lệch
- [ ] ★ Đọc một hệ lạ (mã nguồn mở) trong ≤4 h: xác định mẫu kiến trúc chính, vi phạm phân tầng, 2 điểm yếu
- [ ] Vẽ lại 3 kiến trúc tham chiếu từ trí nhớ; mỗi cái nêu ≥2 điểm yếu cố hữu marketing không nhắc
- [ ] Phân tích build-vs-buy thật với **chi phí thoát tính bằng người-tháng**
- [ ] ★ Migration **không downtime** cho một thành phần, 0 request thất bại trong suốt quá trình
- [ ] ★★ ADR mà **một kỹ sư lạ đọc 6 tháng sau ra được cùng quyết định** — kiểm chứng với người thật
- [ ] Review thiết kế của người khác, nêu ≥3 rủi ro họ chưa thấy, xác nhận bằng phản hồi của họ
- [ ] ★ Threat model toàn vòng `sense→act`, tìm ≥3 vector chưa từng nghĩ tới, thiết kế giảm thiểu cho mỗi cái
- [ ] **[v3]** Lấy một hệ bạn biết, vẽ theo **ISA-95**, chỉ ra chính xác tầng nào phần `learn/infer/adapt` nên nằm và vì sao; vẽ lại theo unified namespace và so sánh được/mất

## Supporting · checkpoint tổng
- [ ] **S1** Suy ra backprop cho MLP từ quy tắc chuỗi, không tra cứu
- [ ] **S1** Tính capacity cho một SLO độ trễ bằng định luật Little
- [ ] **S1** Giải thích `float32` mất chính xác ở một phép tính cụ thể trong code của bạn và sửa được
- [ ] **S2** Đọc datasheet lạ và đấu nối đúng ngay lần đầu, không cháy gì
- [ ] **S2** Debug bug do nguồn bằng oscilloscope, có ảnh waveform trước/sau
- [ ] **S2** Đo dòng ngủ ở mức µA, khớp với tính toán ngân sách năng lượng
- [ ] **S3** Tune PID trên hệ vật lý đạt chỉ tiêu, có đồ thị đáp ứng bước
- [ ] **S3** Thiết kế và chứng minh trạng thái fail-safe dưới 3 loại lỗi
- [ ] **S3** Cho một bài toán điều khiển, lập luận có nên dùng ML hay không, bằng tiêu chí
- [ ] **S3 [v3]** Thiết kế và tune một vòng **cascade** trên hệ thật, chứng minh tốt hơn vòng đơn bằng đồ thị đáp ứng nhiễu; nêu ≥2 tình huống cascade làm tệ hơn
- [ ] **S4** Threat model toàn vòng, ≥3 vector mới
- [ ] **S4** mTLS + provisioning + xoay vòng chứng chỉ, hoạt động sau khi cert cũ hết hạn
- [ ] **S4** Agent có tool không thực hiện được hành động ngoài phạm vi, kể cả khi input dẫn dụ
- [ ] **S4 [v3]** Vẽ mô hình **zone/conduit** (IEC 62443) cho hệ có cả tầng OT lẫn cloud; mỗi conduit vượt ranh giới tin cậy có biện pháp bảo vệ + **cái gì xảy ra với an toàn nếu biện pháp đó lỗi**
- [ ] **S5** Eval harness bắt regression mà unit test bỏ lọt
- [ ] **S5** ≥60% logic firmware test trên host trong CI
- [ ] **S5** Property-based test tìm ra ≥1 bug thật trong code của bạn
- [ ] **S6** FMEA ≥30 mục, ≥3 chế độ hỏng mới
- [ ] **S6** Chứng minh fail-safe dưới ≥3 loại lỗi
- [ ] **S6** Đo thời gian phát hiện cho mỗi cơ chế giám sát, dưới ngưỡng đặt ra
- [ ] **S7** Bảo vệ lựa chọn kiến trúc bằng bảng chi phí + độ trễ trước 3 phản biện
- [ ] **S7** Dự đoán độ trễ khi utilization tăng, đo xác nhận
- [ ] **S7** Tính điểm hòa vốn tự host vs API cho workload inference của bạn
- [ ] **S8** Design doc mà kỹ sư lạ **thực thi được không cần hỏi lại** — kiểm chứng với người thật
- [ ] **S8** ADR mà người đọc 6 tháng sau ra cùng quyết định
- [ ] **S8** README cho một dự án mà người mới chạy được trong ≤30 phút

## Adjacent · checkpoint tổng
- [ ] **A1** Hệ ROS 2 ≥3 node giao tiếp qua topic, ghi và phát lại rosbag
- [ ] **A1** Kiến trúc an toàn cho máy chuyển động, lớp phần cứng độc lập với phần mềm
- [ ] **A2** HIL tối giản: firmware thật + cảm biến giả lập, test tự động
- [ ] **A2** Đo chênh lệch hiệu năng mô phỏng vs thực tế, giải thích nguồn
- [ ] **A3** Liệt kê mọi chế độ của hệ, kiểm tra người dùng luôn biết đang ở chế độ nào
- [ ] **A3** Luồng escalation đầy đủ với ngữ cảnh bàn giao, đo thời gian quyết định của người
- [ ] **A3** Dashboard trả lời "hệ có khỏe không" trong ≤10 giây
- [ ] **A4** 5 công việc: quyết định tự động hóa hay không, có tiêu chí
- [ ] **A4** Tính chi phí thật của mỗi loại lỗi, chỉnh ngưỡng model theo đó
- [ ] **A5** Xếp hệ vào tầng rủi ro EU AI Act, liệt kê nghĩa vụ
- [ ] **A5** Quy trình xóa dữ liệu hoạt động xuyên mọi bản sao và cache
- [ ] **A6** Kiểm tra toàn bộ dependency, xác định nghĩa vụ giấy phép của bạn
- [ ] **A6** Với mỗi model dùng: xác định được phép làm gì với output

## Project · nghiệm thu
- [ ] **P1** Chạy 6 h liên tục; dựng lại từ đầu trong một buổi không copy-paste; giải thích từng dòng firmware
- [ ] **P2a** 10.000 kết nối đồng thời, không rò rỉ fd sau 1 triệu kết nối
- [ ] **P2b** Kill ngẫu nhiên ≥200 lần trong lúc ghi, mọi giá trị đã ack vẫn đọc được
- [ ] **P2c** `cat | grep | wc > out` chạy đúng; Ctrl-C giết đúng tiến trình; không zombie
- [ ] **P3** 30 ngày ngoài bàn làm việc không can thiệp; phát hiện đúng bất thường ≥3 lần độc lập; OTA thành công trong lúc triển khai
- [ ] **P4** Hạ tầng dựng lại từ zero bằng một lệnh; test đồng bộ hàng loạt pass có đồ thị; restore thật thành công
- [ ] **P5** Throughput ≥2× baseline có giải thích cơ chế; ở 3× tải từ chối rõ ràng thay vì sập; bảng so sánh tự host vs API có điểm hòa vốn
- [ ] **P6** 90 ngày vận hành, ≥5 SLI đạt ≥95%; chaos ≥5 thành phần; giải thích mọi quyết định bằng audit log; ≥1 postmortem action item hoàn thành; kỹ sư lạ vận hành được trong 1 ngày
- [ ] **P7** Migration không downtime 0 request thất bại **hoặc** ≥1 PR có ý nghĩa được merge

---

## Cách dùng master checklist

**Đây là tài liệu công tác chính của bạn**, không phải phụ lục trang trí.

| Nhịp | Việc |
|---|---|
| Hàng tuần | Tick những gì đạt được; ghi ngày bên cạnh |
| Hàng tháng | Đếm % đã tick theo nhánh; so với mức mục tiêu ở §6 |
| Khi tuyên bố một nhánh "xong" | **Mọi** checkpoint của nhánh đó phải tick. Không có ngoại lệ |
| Khi chuẩn bị phỏng vấn | Mỗi checkpoint đã tick là một câu chuyện cụ thể bạn kể được |
| Khi nghi ngờ bản thân | Đếm số đã tick. Đó là bằng chứng, cảm giác thì không |

## Thói quen liên tục — kiểm hằng tuần, không phải checkpoint một lần

- [ ] Sổ **"khái niệm vendor ↔ khái niệm trung lập"** (§2.3d, Phụ lục D.4) — thêm ≥2 cặp mỗi tuần
- [ ] Giờ tự học tuần này: ___ / mục tiêu 12–18
- [ ] Tuần này tôi có tự học đúng thứ công việc đang dạy không? (nếu có → **mất ngân sách**, xem §9.2 quy tắc 1)
- [ ] Mô tả năng lực của tôi trong 3 câu **không dùng tên sản phẩm nào** — làm được không?

**Kiểm tra mốc tháng 12:** làm bài 5 câu ở **Phụ lục D.5** để xác minh giả định "công việc cấp kỹ thuật thật".

---

**Tổng số checkpoint:**

---
---

## ✎ Phần của tôi — theo dõi

Tick trực tiếp lên các ô `- [ ]` ở trên. Tổng kết:

| Ngày | Số checkpoint đạt | Tổng | % |
|---|---|---|---|
|  |  |  |  |

