# Project Status — Huong-Dan / E2E-SYSTEM

**State:** ĐANG VIẾT C3 (C3.1 → C3.14)
**Updated:** 2026-10-02
**Last session:** claude-code (Opus 5.5), 2026-10-02, hoàn tất C3.4, tiếp C3.5 →

## NEXT ACTION

Viết C3.5 Pipelining&BranchPrediction (roadmap §C3.5; checkpoint: hai phiên bản vòng lặp — nhánh khó đoán vs branchless — đo
chênh lệch, xác nhận nguyên nhân bằng `branch-misses`). Không có PMU trong WSL2 → `branch-misses` thật không đọc được; dùng
mô phỏng (cachegrind --branch-sim, bộ dự đoán tự viết) + đo thời gian, nói rõ giới hạn. Scratchpad phiên 2026-10-02 mới:
phải dựng lại môi trường C3 (apt download + dpkg -x, xem "Môi trường C3").

## Việc đang làm — viết nhánh C3 (C3.1 → C3.14)

Yêu cầu (người dùng, 2026-09-27): "Kiểm tra trạng thái Project. Sau đó thực hiện C3-ComputerArchitecture&DigitalLogic,
bám sát theo C1 và C2 đã làm vào roadmap.md đã ghi." → cùng quy ước với C2; **không** sửa `C3.0-INDEX.md`.

| File | Trạng thái |
|---|---|
| C3.1 BooleanLogic&CombinationalCircuits | ✅ 2026-09-27 (80 KB; checkpoint: 21/21 test chính thức trên mạch NAND tự mô phỏng + 20/20 trên HardwareSimulator chính thức qua .hdl phẳng; độ phủ stuck-at của ALU.tst 85,6%; SAT chứng minh tương đương 2³⁸ đầu vào) |
| C3.2 SequentialLogic&FSM | ✅ 2026-09-28 (142 KB; project 3: 8/8 test trên runner + 8/8 trên HardwareSimulator, 4/4 đột biến runner; checkpoint: FSM khung UART (SOF+LEN+CRC-16/MODBUS) bằng C trên QEMU Cortex-M3 khớp mô hình tham chiếu khai báo 2.295/2.295 sự kiện ×3 lần, 10⁶ khung thử 0 lệch, 760.428/760.438 khung tốt (10 mất đều giải thích được); lỗi thật tìm được: xóa cờ ngắt sau khi đọc, bộ thử gom byte, CRC lọt 1/256 với 0x7E chèn sau LEN=1) |
| C3.3 Datapath&BuildingACPU | ✅ 2026-09-29 (140 KB; máy Hack thuần NAND+DFF 3,27 triệu NAND: project 5 6/6 runner + 6/6 HardwareSimulator chính thức; assembler 7/7 + 1.000/1.000 ngẫu nhiên trùng từng bit với bản Java; CRC-16/XMODEM chạy trên CPU tự dựng = 0x31C3; CPU chứng minh SAT tương đương đặc tả 2⁸¹ đầu vào; 4 hiện thực ISA bất đồng ở 5 vùng; assembler Java sai im lặng 6/21 ca biên) |
| C3.4 ISA&Assembly | ✅ 2026-10-02 (215 KB; CoreMark trên 7 cấu hình tập lệnh cùng CRC, đếm lệnh/byte/truy cập bằng plugin QEMU + valgrind; bộ giải mã RV64IM 51.730/51.730 khớp binutils; ABI quan sát bằng thẻ vị trí trên 6 ABI; checkpoint filt.c: 9 biến thể cờ, mỗi biến đổi có -fopt-info + thí nghiệm tắt, kiểm vi sai 10⁶ khối 0 khác; -O2 nhanh 8,7× -O0) |
| C3.5 Pipelining&BranchPrediction | ⏳ tiếp theo |
| C3.6 → C3.14 | ☐ |

### Môi trường C3 (không cần sudo)

- `apt download` + `dpkg -x` vào `scratchpad/root`: qemu-user-static, qemu-system-arm/misc (8.2.2), iverilog 12, yosys 0.33,
  gcc-arm-none-eabi 13.2.1 + newlib, gcc-aarch64/riscv64-linux-gnu 13 (+ libc6-dev-*-cross), valgrind 3.22, openjdk-21-jdk.
  Cross gcc Linux cần `--sysroot=$R`; JDK: các symlink conf trỏ /etc → sửa trỏ `$R/etc`.
- nand2tetris: mã nguồn bộ công cụ Java (Drive id 1stcWUSeAixCRHWOjc9sgBhq5voSLvun8) — biên dịch bằng javac 21 sau khi đổi
  định danh `enum`→`enumr` và bỏ `import Hack.*;`; file .tst/.cmp chính thức lấy từ repo `nand2tetris/web-ide`
  (projects/src/project_0x/*.ts) + script thêm `output-file` và định dạng `%B1.W.1` cho simulator cũ. Không đăng lời giải .hdl
  (tác giả khóa học đề nghị không công khai; repo này public) — dùng trình mô phỏng cổng tự viết + test chính thức.
- Phần cứng: không có PMU (dmesg: "unsupported CPU family 6 model 183 no PMU driver, software events only"; CPUID thiếu
  arch_perfmon), MSR PMU (tsc/pperf) → EINVAL; pin trong WSL là "Hyper-V Virtual Battery" (giả). CÓ số đo thật phía Windows qua
  interop: `powershell.exe Get-Counter '\Energy Meter(*)\Power'` (RAPL pkg/pp0/pp1, mW), `'\Processor Information(_Total)\Actual
  Frequency'`, `'\Thermal Zone Information(*)\High Precision Temperature'` (0,1 K) — không cần admin → dùng cho C3.10/C3.13.
  GPU RTX 4060 Laptop (driver 610.88, CUDA UMD 13.3; nvidia-smi: công suất/nhiệt/xung thật).
- nand2tetris bản mới: `git clone --depth 1 --filter=blob:none --sparse https://github.com/nand2tetris/web-ide` + `sparse-checkout set
  projects/src` (GitHub REST API bị giới hạn lượt khi chưa đăng nhập); tách hdl/tst/cmp từ các file .ts. Simulator Java chạy:
  `cd InstallDir && java -Djava.awt.headless=true -cp <classes> HardwareSimulatorMain X.tst` (tst cần thêm output-file + %B1.W.1).
- Plugin QEMU đếm lệnh: lấy include/qemu/qemu-plugin.h tag v8.2.2 (raw.githubusercontent.com), glib.h giả (typedef gboolean...),
  `gcc -shared -fPIC`; chạy `-plugin libicount.so,lo=..,hi=.. -d plugin`.
- pdftotext: apt download poppler-utils (+ libpoppler134) → dpkg -x.
- C3.3: file test/asm lấy theo bảng CHIPS trong `index.ts` từng project (đừng glob — `06_alu_all.ts` không phải test chính thức);
  project 6 ở `projects/src/samples/project_06/*.ts`. Assembler chính thức không có main: tự viết OfficialAsm.java gọi
  `new Hack.Assembler.HackAssembler(f, 32768, HackAssemblerTranslator.NOP, true)`. Test v2 cho simulator cũ: thêm output-file.
  Nhìn trộm `DRegister[]`, `PC[]`, `RAM16K[i]` chỉ tìm chip DỰNG SẴN (GatesManager) → bản xuất phải dùng ARegister/DRegister/PC/RAM16K.
  Web-ide (Node 22 có sẵn): simulator/src/cpu/{cpu,alu}.ts, languages/asm.ts (sparse-checkout add simulator/src/...).
- Web-ide chạy thật: `npm install esbuild ohm-js@17 @davidsouther/jiffies@2.2.5` trong scratchpad/webasm, `ln -s .../node_modules
  web-ide/simulator/node_modules`, entry.ts import `ASM` (languages/asm.ts) + lớp `CPU` (cpu.ts) + `ROM` (memory.ts) — PHẢI dùng
  RAM/ROM gốc (đọc ngoài vùng trả 0xFFFF), không tự viết bộ nhớ; esbuild --bundle --platform=node --format=esm.
- Memory.tst trên HardwareSimulator không giao diện: vá Keyboard.java (+pressVirtual) và HackController.doEchoCommand (echo "'K'" →
  nhấn phím) — chú thích Java chỉ dùng ASCII (javac -encoding ISO-8859-1). CPUEmulator headless: `CPUEmulatorMain script.tst`
  (tên file không có '_').
- apt download thêm: gcc-arm-none-eabi binutils-arm-none-eabi qemu-system-arm qemu-system-common qemu-system-data gcc-avr
  binutils-avr avr-libc + libfdt1 libpmem1 libnuma1 librdmacm1t64 libslirp0 liburing2 libaio1t64 libibverbs1 libndctl6
  libdaxctl1 (QEMU cần LD_LIBRARY_PATH=$R/usr/lib/x86_64-linux-gnu và -L $R/usr/share/qemu); poppler cần libopenjp2-7 liblcms2-2
  libnss3 libnspr4. avr-gcc: -B/-I/-L trỏ $R/usr/lib/avr/.
- doccheck.py (dựng lại 2026-09-29): slug GitHub = giữ ký tự loại L/M/N + ' -_'; bỏ qua §x.y.z (mục chuẩn C11) khi kiểm §-tham chiếu.

### C3.4 — số liệu đã đo (2026-09-30/10-01, trước khi viết văn bản)
- CoreMark (EEMBC, không sửa core_*.c, port bare-metal semihosting): mỗi vòng x86-64 338.524 lệnh (1,05 MB, TB 3,11 B),
  AArch64 303.203, RV64GC 358.929 (+Zba/Zbb/Zbs 318.370), Thumb-2 M3 294.565 (71,8% lệnh 16 bit), M0 389.090; x86 load-op 1,2% + RMW 1,0%,
  mov 24%, chép thanh ghi 13,5% (A64 7,3%); truy cập dữ liệu/vòng x86 74,0K vs A64 68,0K; .text -O2: x86 5775, A64 6228, RV64GC 5124,
  RV64G 7184, M3 4036, M0 4504. Plugin QEMU 8.2.2 Ubuntu: lọc MEM_R/MEM_W lệch một bậc (đã hiệu chỉnh).
- RV64IM decoder 51.730/51.730 khớp objdump trên Lua 5.4.7; x86 len15: 15 B chạy, 16 B → SIGSEGV si_code 128; split lock 2,55 µs vs 3,9 ns,
  làm luồng khác quét DRAM chậm 4×; ABI probe theo thẻ vị trí cho 6 ABI; checkpoint filt.c: -O0 202 ns/khối, -O2 23,3 ns, 8 biến thể
  khớp -O0 trên 10^6 khối.

### Tham chiếu tới trước mà C3.3 để lại (phải trả ở leaf sau; kiểm lại ở rà soát cuối C3)
- C3.4: x86 dài 1–15 byte cần bộ giải mã độ dài + CPU x86 giữ ROM vi mã cho lệnh hiếm/phức tạp (§3.3); đọc thanh ghi, chế độ địa
  chỉ, quy ước gọi hàm trên RISC-V/ARM/x86 (D.3); ARM phải tự đồng bộ I-cache/D-cache sau khi ghi mã (§5.5, cùng C3.7).
- C3.5: pipeline hai tầng Hack (Mở rộng 1 "điểm khởi đầu của C3.5"); tệp thanh ghi nhiều cổng → bank/bản sao (§2.2–2.3);
  xung đột cấu trúc/điều khiển (§4.4); chia đường dài bằng pipeline (§1.4).
- C3.6/C3.11: vùng thiết bị không cache (§6.5, C.3); C3.11: giao dịch AHB/APB, I²C cực máng hở (§2.5, §6.5).

## Nhánh C2 (C2.1 → C2.13) — HOÀN TẤT 2026-09-26

Yêu cầu (người dùng, 2026-09-24): "Đã viết xong C1 (trừ C1.0-INDEX.md). Tiếp theo là C2.
Bám theo roadmap.md và C1 đã viết để thực hiện tương tự." → **Không** sửa `C2.0-INDEX.md` (giống C1).

Quy ước rút từ C1 (giữ đúng khi viết tiếp):
- Ghi đè hoàn toàn file khung; không front-matter YAML. Mở đầu `# C2.x · <tên> — \`Lv\``, khối
  `> Mục tiêu của tài liệu` + tiên quyết + điều kiện hoàn thành, rồi `## Mục lục` (bảng, anchor).
- §0 Cách dùng tài liệu (nguyên tắc, bộ công cụ, môi trường kiểm chứng, ký hiệu ✅ 🔬 ⚠️).
- Mỗi sub-leaf của roadmap §5 → một mục; mục Checkpoint có lời giải mẫu + "Tự chấm" + "Mở rộng".
- Phụ lục A (bảng tra), B (triệu chứng → nguyên nhân), C (checklist), D (lộ trình đọc tiếp),
  rồi "Tổng kết: mười điều phải mang theo", dòng chân trang in nghiêng ghi môi trường đo.
- Mọi output/số đo phải chạy thật; không bịa. Tiếng Việt, code/identifier tiếng Anh.
- File lưu CRLF (như cây làm việc của Windows).

## Tiến độ

| File | Trạng thái |
|---|---|
| C2.1 ComplexityAnalysis | ✅ 2026-09-24 (93 KB; anchor mục lục đã kiểm) |
| C2.2 Arrays&HashTables | ✅ 2026-09-24 (95 KB; checkpoint oaht + kiểm thử vi sai) |
| C2.3 Trees&BalancedTrees | ✅ 2026-09-24 (67 KB; checkpoint đo trên SQLite + mô phỏng BST trên đĩa) |
| C2.4 Heaps&PriorityQueues | ✅ 2026-09-24 (58 KB; checkpoint scheduler RM/EDF khớp RTA) |
| C2.5 Graphs&Traversal | ✅ 2026-09-24 (60 KB; checkpoint mbuild.py, so với make/tsort/graphlib) |
| C2.6 ShortestPaths&Flow | ✅ 2026-09-25 (122 KB; checkpoint dijkstra.py + 2 trường hợp sai; dữ liệu thật DIMACS NY) |
| C2.7 Sorting&Selection | ✅ 2026-09-25 (85 KB; checkpoint sắp xếp ngoài 10 GiB: đo 40,00 GiB I/O = dự đoán C2.1 §6.4; khớp GNU sort từng byte) |
| C2.8 DynamicProgramming | ✅ 2026-09-25 (67 KB; checkpoint: quy trình 20 phút + 3 bài nghề (pin PV, cân bằng dây chuyền, điểm đổi chế độ), mỗi bài khớp vét cạn) |
| C2.9 Greedy&Correctness | ✅ 2026-09-25 (55 KB; checkpoint greedy_check.py: tìm + thu nhỏ phản ví dụ, 4 chứng minh exchange, 3 phản ví dụ giải thích) |
| C2.10 ProbabilisticDataStructures | ✅ 2026-09-26 (129 KB; checkpoint Bloom trước SQLite: Tranco 1M × blocklist StevenBlack, truy vấn DB −99,0%, FP 0,822% ± 0,011% vs lý thuyết 0,819% qua 20 hạt giống) |
| C2.11 CacheAwareAlgorithms | ✅ 2026-09-26 (87 KB; checkpoint: Jacobi trên mạng đường DIMACS E-USA 3,6 triệu nút, chỉ đánh số lại nút → ×2,8–3,2, kết quả trùng từng bit, mô hình dự đoán đúng số trượt cache) |
| C2.12 Online&StreamingAlgorithms | ✅ 2026-09-26 (134 KB; checkpoint: p99 của 10⁸ độ trễ `getppid` thật qua pipe — histogram log α=0,5% 8,3 KB, sai +0,031%, có chứng minh biên; 3 luồng đối nghịch ≤ 0,475%; đối chứng 783 MB) |
| C2.13 ConcurrentDataStructures | ✅ 2026-09-26 (88 KB; checkpoint: SPSC ring release/acquire, 0 sai/10⁸ + TSan sạch; 5 đột biến — 3 đột biến memory order đúng 100% trên x86 nhưng TSan bắt cả 3, đột biến logic bị kiểm thử bắt, chỉ số thường treo ở -O2; lập luận happens-before 6 bước) |

## Known problems

- Icarus: `@(d)` trên cổng nối vào một bit của vector kích hoạt khi BẤT KỲ bit nào của vector đổi → so với giá trị trước;
  biểu thức tổ hợp `cnt ^ (cnt >> 1)` sinh glitch độ rộng 0 (C3.2 §4 dùng làm bài học). `pkill -f "<mẫu>"` có thể giết chính
  shell đang chạy lệnh (mẫu nằm trong dòng lệnh) → dùng `pkill -x qemu-system-arm`.

- C3.1: iverilog giải nén cục bộ cần `-B$R/usr/lib/x86_64-linux-gnu/ivl` và `vvp -M$R/usr/lib/x86_64-linux-gnu/ivl`.

- TSan trên kernel WSL này báo `FATAL: ThreadSanitizer: unexpected memory mapping` → chạy
  binary qua `setarch $(uname -m) -R ./prog`.
- Không có perf/valgrind/gdb/clang (không cài hệ thống); đo bằng thời gian, `/proc/self/io`, mô phỏng.
- Windows git dùng `autocrlf=true`, git trong WSL thì không → mọi file hiện "modified" trong WSL.
  Xem thay đổi thật: `git -c core.autocrlf=true status`. Commit từ WSL: `git -c core.autocrlf=true add <file>`.
- Thay đổi C1 và các thư mục mới (`90-PROJECTS/`, `99-TAI-LIEU-CHUNG/`) là của người dùng, chưa
  commit — không đụng tới, chỉ commit file C2 + file này.
- Python hệ thống không có numpy/scipy/networkx (2026-09-25) — thí nghiệm dùng Python thuần hoặc C.
- WSL2: một luồng chỉ thấy ~5 MiB L3 (hệ báo 24 MiB); vùng < 2 MiB không được cấp huge page qua madvise (C2.11 §1.3–1.4).
  Có internet (curl): C2.6 tải dữ liệu DIMACS vào scratchpad; scratchpad mất sau phiên, muốn chạy lại thì tải lại
  từ http://www.diag.uniroma1.it/challenge9/data/ (USA-road-d/t.NY.gr.gz, USA-road-d.NY.co.gz).

## Last verification

- 2026-10-02: C3.4 — phiên trước (09-30 → 10-01) chạy mọi thí nghiệm và đọc lại §0–§4.6; phiên này sửa 17 lỗi đã ghi + đọc lại §5–hết,
  sửa thêm: §8.5 đọc rách là `lo` CŨ + `hi` MỚI (sai 2³¹ với bước 2³¹, không phải 2³²); §5.4 Win64↔SysV còn hỏng ở vùng bóng 32 B;
  tổng kết 5 + §3.4 khung 8 từ = r0–r3, r12, lr (thanh ghi được phá) + pc, xPSR; tham chiếu fuzz assembler C3.3 §7.3 → §7.2;
  khối mix.py tách dòng nguyên văn (`…` = lược). doccheck.py dựng lại (anchor, fence, cột bảng, CRLF, mọi § nội bộ + Cx.y §z tồn tại):
  0 lỗi, 31 bảng, 199 tham chiếu §; 15 tham chiếu chéo kiểm đúng chủ đề bằng tay. C3.1–C3.3 chạy lại doccheck: 0 lỗi.

- 2026-09-29: C3.3 — mọi output chạy thật: runtst p1–p3 30/30 (khớp số cổng C3.1/C3.2) + p5 6/6; HardwareSimulator 6/6 (+ bản thuần
  Nand/DFF qua CPU-external; đột biến bị bắt); trace1/critpath/bench/regfile/buscount/cpuparts/diverge(4 hiện thực)/udf(QEMU)/runmc/
  Pong-startup/avr/smc/diag/kbd/mmio(QEMU)/readfx/asmcheck/fuzzrun/edge/runcrc/mutcpu/lockstep 10⁶/satcpu/faultcpu+satfaults.
  Đọc lại toàn văn, sửa ~20 chỗ (đường tới hạn ROM đi qua bit a chứ không qua bit điều khiển ALU; 78% là của CPU không phải datapath;
  CRC-XMODEM khác đa thức MODBUS; bộ nhớ web-ide phải là lớp gốc — đọc ngoài vùng 0xFFFF; nhóm ca biên 9/5/7; chips.py có thêm
  name/words; "đọc là lấy ra" thay bằng số đo QEMU; §8.x đánh số lại...). Thêm ví dụ Max.asm chính thức sai với ±20000 (tràn).
  Nguồn đã đối chiếu văn bản gốc: ARM DDI 0479C bảng 4-7, AMBA IHI 0011A §3.2/§3.10/ch.4, Intel SDM 3A "Self-Modifying Code",
  RISC-V unpriv RV32I, Rixner HPCA 2000, mã nguồn Java 2.5 + web-ide 52611ad. doccheck 0 lỗi, 26 bảng, CRLF.
- Ghi chú rà soát cuối C3: "dòng so khớp" — C3.1 và C3.3 KHÔNG tính dòng tiêu đề, C3.2 CÓ tính (Bit 215, Register 149, PC 31, RAM8 173,
  RAM64…RAM16K 320) → sửa C3.2 thành 214/148/30/172/319 (đã chạy lại 2026-09-29: đúng các số đó).
- 2026-09-28: C3.2 — mọi output chạy thật (latch/latch2/race/setuphold/skew trên evsim; meta/mtbf; lfsr n=2..20 khớp φ(2^n−1)/n;
  counters/cdc/pulse/seqdet trên Icarus; yosys 4 biến thể + seu_tb trên netlist; fsm_sw x86 + Cortex-M3; runtst 8/8 + HardwareSimulator
  8/8 + phép thử ngược; checkpoint: diff.py 40k + 10⁶ khung, lost.py, vét cạn CRC 1/256, run_qemu ×3 + plugin icount, run_ovf, mutants.sh
  + khoảng nghỉ biên); đọc lại toàn văn so từng khối output, sửa 15 chỗ (độ sâu đọc/ghi RAM16K, B3→B5, §7.5→§7.4, "7 mẫu" → 4,
  kích thước cụm 838 byte, dự đoán COBS ghi rõ chưa đo...); doccheck 0 lỗi, 19 bảng, CRLF.
- 2026-09-26: RÀ SOÁT CUỐI C2 — (1) máy: doccheck 13/13 file 0 lỗi (anchor, fence, số cột bảng, CRLF); xref: mọi "C2.x §y" trỏ tới mục
  tồn tại và đúng chủ đề (7 cảnh báo còn lại là số mục của sách/C1.1 — dương tính giả); khung mẫu đồng đều (mục tiêu, tiên quyết,
  điều kiện hoàn thành, §0.1–0.3, Tự chấm, Mở rộng, Phụ lục A–D, 10 điều tổng kết, chân trang); mức Lv khớp INDEX. (2) đọc toàn văn,
  sửa: C2.4 §1.3 số so sánh dòng n = 16·10⁶ chép nhầm 19.95 → 21.95 (chạy lại xác nhận); C2.6 tham chiếu vector hóa (C2.11 → C3.8 +
  C2.11 §4.2); C2.3 tiêu đề `In → Ad` → `In→Ad`; C2.1/C2.7 "C2.11 đo trực tiếp" → nói rõ đo bằng thời gian + mô phỏng; C2.1/C2.7 ghi chú
  L3 hiệu dụng ~5 MiB (C2.11 §1.3); C2.1/C2.4 ghi rõ numpy 2.5.3 cài riêng (Python hệ thống không có); C2.3 ghi chú chênh 81 vs 70,5 ns
  giữa hai lần chạy LPM; mọi tham chiếu tới trước "(C2.12)", "(C2.13)" ở C2.1/2/4/7/8/10/11 trỏ về mục cụ thể; C2.9 §5.3 nối list
  scheduling với tỷ lệ cạnh tranh C2.12 §5.4.
- 2026-09-26: C2.13 — mọi output chạy thật (counter, queues, aba, reclaim [ASan], rcu/rcu_bug/rcu_nofence [ASan, TSan], litmus, orders -S,
  fencecost, spsc_test + mutants.sh [TSan qua setarch -R]); ánh xạ ARMv8 lấy từ bảng Sewell (không có máy ARM); kfifo, liburcu, P2530/P2545
  kiểm trên nguồn; doccheck 0 lỗi, 21 bảng, CRLF.
- 2026-09-26: C2.12 — mọi output chạy thật (consume/welford, onepass.py, slidesum/slidemax/oplat/slidemed, deadband.py, totalizer,
  variance.py, merge.py, qbench, cusum, nab.py/nab2.py, skirental.py, paging.py, morris.py, sdt.py, latsrc/gen2/p99/exact); dữ liệu thật:
  NAB machine_temperature + nhãn, War and Peace (Gutenberg #2600); khẳng định về PostgreSQL float.c, CPython statistics.py, DataSketches
  KLL kiểm trên mã nguồn/tài liệu; PI swinging door theo tài liệu AVEVA; doccheck 0 lỗi, 22 bảng, CRLF.
- 2026-09-26: C2.11 — mọi output chạy thật (latency/l3probe/tlb/spread/stride/padding/matmul/aos/veb/prefetch/batch/
  falseshare/graphorder, rowcol.py); dữ liệu DIMACS USA-road-d.E và NY tải lại vào scratchpad; phát hiện L3 hiệu dụng ~5 MiB
  (ghi rõ chưa rõ nguyên nhân); khẳng định về libstdc++/Folly kiểm trên mã nguồn, Khuong & Morin trên tóm tắt; doccheck 0 lỗi, 19 bảng, CRLF.
- 2026-09-26: C2.10 — mọi output chạy thật (bloom*.c, cbf.c, cuckoo.c, hll.c, pv.c, reservoir*, qbench.c, tdmerge.c, lsh.c,
  simhash.c, checkpoint.py, sqlitecfg.py); dữ liệu thật: Tranco L5PZ4, StevenBlack hosts 25/09/2026, Wikimedia pageviews
  2024-03-01 12h, stdlib CPython 3.12, 10⁷ độ trễ pread; khẳng định về LevelDB/RocksDB/Redis/coreutils shuf/t-digest/
  cuckoofilter kiểm trên mã nguồn hoặc tài liệu chính thức, trích dẫn bài báo đã kiểm; doccheck: 0 lỗi, 16 bảng, CRLF.
- 2026-09-25: C2.9 — mọi output chạy thật; ví dụ chặt của list scheduling/LPT đạt đúng cận; AGV dùng lại đúng bản đồ C2.8
  (tối ưu khớp); 11/11 anchor, 12 bảng, CRLF.
- 2026-09-25: C2.8 — mọi output chạy thật; mọi DP khớp vét cạn (400/1000/300/2000 bộ thử); lru_cache 3.331 tầng trên Python 3.12
  kiểm với ghi chú phát hành; 13/13 anchor, 16 bảng, CRLF.
- 2026-09-25: C2.7 — mọi output chạy thật; extsort 10 GiB (O_DIRECT) đo 20,00 + 20,00 GiB, M=256 MiB/k=8 đo 60 GiB, kết quả
  trùng từng byte với GNU sort 9.4; khẳng định về thư viện kiểm bằng mã nguồn đúng phiên bản; 14/14 anchor, 25 bảng, CRLF.
- 2026-09-25: C2.6 — mọi output chạy thật (road.c, bf.c, fw.c, flowbench.c và các script Python); dijkstra.py khớp
  Bellman-Ford + vét cạn trên 20.000 đồ thị, 2 đột biến bị bắt; 12/12 anchor mục lục OK, 20 bảng đủ cột, code fence chẵn, CRLF.
- 2026-09-24: C2.5 — mbuild.py chạy trên 4 bộ thử (hợp lệ, vòng, nhiều lỗi, 10⁵ đích); anchor OK.
- 2026-09-24: C2.4 — toysched.c: 960.000 quyết định khớp quét tuyến tính, max đáp ứng = RTA 20/20; ASan+UBSan sạch.
- 2026-09-24: C2.3 — số trang đọc/truy vấn SQLite đếm bằng /proc/self/io syscr; anchor OK.
- 2026-09-24: C2.2 — oaht.h qua kiểm thử vi sai 3×10⁶ thao tác vs std::unordered_map dưới ASan+UBSan; anchor OK.
- 2026-09-24: C2.1 — mọi output trong tài liệu chạy thật; assemble.py kiểm anchor mục lục (0 hỏng), code fence chẵn, CRLF.
