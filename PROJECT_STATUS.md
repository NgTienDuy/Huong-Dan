# Project Status — Huong-Dan / E2E-SYSTEM

**State:** ĐANG VIẾT C3 (C3.1 → C3.14) — C3.1–C3.10 xong; tiếp C3.11 (2026-10-08)
**Updated:** 2026-10-08
**Last session:** claude-code (Opus 5.5), 2026-10-08: viết xong C3.10 (yêu cầu người dùng: tiếp C3 tới C3.14, rồi rà soát toàn bộ C3)

## NEXT ACTION

Viết C3.11 IO-DMA&Interrupts (roadmap §C3.11; checkpoint: DMA cho luồng ADC liên tục, đo mức giảm tải CPU so với polling, xử lý
đúng mạch lạc cache). Chưa có file nào trong `.draft-C3.11/` (phiên 2026-10-08 dừng ở đây: chế độ auto chặn lệnh tạo khung firmware vì
một kiểm tra an toàn — cần người dùng chạy tiếp ngoài chế độ auto hoặc mở phiên mới). Đã khảo sát xong (2026-10-08):
- Renode 1.17.0 portable (github.com/renode/renode/releases v1.17.0, `renode-1.17.0.linux-portable.tar.gz`, chạy `./renode --console`,
  .NET 8 kèm sẵn) — nền tảng `platforms/cpus/stm32g0.repl` (cpuType cortex-m0, flash 128K @0x08000000, RAM 48K @0x20000000, USART2
  @0x40004400 mô hình STM32F7_USART, DMA1 @0x40020000 = DMA.STM32G0DMA 7 kênh (kênh 1 → nvic 9), ADC @0x40012400 = Analog.STM32G0_ADC
  → nvic 12, `externalEventFrequency: 1000`). ADC (STM32_ADC_Common.cs): EXTEN≠0 → lấy mẫu theo nhịp externalEventFrequency (thời gian ảo),
  có cờ OVR thật (EOC chưa đọc khi mẫu mới tới), đọc DR xóa EOC, yêu cầu DMA mỗi mẫu nếu DMAEN — NHƯNG repl gốc không truyền
  `dmaChannel/dmaPeripheral` → phải tự khai báo lại adc (dmaChannel: 1, dmaPeripheral: dma1, externalEventFrequency: 12000). Nguồn mẫu:
  `Analog.ADCChannelSource @ adc 0` + `FeedSamplesFromRESD @file` (RESD tạo bằng `tools/csv2resd/csv2resd.py`, cần `pip install construct`)
  → dùng dữ liệu rung CWRU làm tín hiệu ADC.
- ⚠️ Lỗi mô hình DMA.STM32G0DMA (đọc mã, chưa đo): `HalfTransfer = dataCount <= originalDataCount/2` gán ở MỖI lần chuyển → sau khi ISR
  xóa HTIF, mỗi mẫu của nửa sau lại bật HT (ngắt mỗi mẫu); TC tự xóa ở lần chuyển kế. Kế hoạch: đo số ngắt/bộ đệm để xác nhận, rồi nạp
  bản vá lúc chạy (`include @STM32G0DMA_fix.cs`, chỉ đặt HT khi count == N/2). DMA.STM32DMA (F4/F7) KHÔNG có CIRC/HTIE/DBM (tagged).
- Renode không mô hình cache → mạch lạc cache làm bằng: (a) GPU thật: L1 của GPU không mạch lạc với ghi của CPU vào bộ nhớ host-mapped
  (thử `ld.global.ca` vs `ld.global.cv` bằng PTX inline); (b) x86 mạch lạc DMA PCIe (cudaMemcpy D2H vào buffer CPU đã cache); (c) mô hình
  cache write-back + DMA cho Cortex-M7 (stale read, lỗi căn 32 B), kiểm ST AN4839 trước khi trích.
- Toolchain: `apt download gcc-arm-none-eabi binutils-arm-none-eabi libnewlib-arm-none-eabi libnewlib-dev` + dpkg -x → arm-none-eabi-gcc
  13.2.1 chạy được. Khung firmware dự kiến: g0.ld, g0.h (thanh ghi RM0444), startup.c, uart.h; MODE POLL/IRQ/DMA; đo tải CPU =
  `cpu ExecutedInstructions` / (PerformanceInMips × thời gian ảo) với WFI khi rảnh; mất mẫu = mẫu sinh ra theo thời gian − mẫu nhận.
- Mục khác: §1 x86 `inb` từ user → SIGSEGV; §4 jitter timer Linux/Windows thật; §7 I²C cực máng hở (ngspice hoặc RC), UART dung sai
  baud (mô phỏng bit), APB/AHB bằng Verilog (nợ của C3.3 §2.5/§6.5); §8 PCIe từ số đo C3.9/C3.10; §9 USB khái niệm (nguồn chuẩn).
Draft ở `.draft-C3.11/`; công cụ kiểm: `.draft-C3.7/src/{doccheck,blockcheck}.py`. Ghi ESP32 là bước phần cứng thật tiếp theo.
Môi trường C3.10 dựng lại bằng `.draft-C3.10/src/setup_env.sh S` (scratchpad mất sau mỗi phiên).
Môi trường GPU: `. scratchpad/tools/cuda.sh` (CUDA 13.3 redist ở scratchpad/cuda/root; tái tạo bằng `.draft-C3.9/src/cuda_setup.sh DIR`).
⚠️ GPU tự tăng xung 2100 → ~2650 MHz: mọi phép đo warmup() + in MHz. ncu bị chặn (ERR_NVGPUCTRPERM) — người dùng chọn làm tiếp không
bộ đếm; nếu họ bật quyền: chạy C3.9 §11.7 trong lần rà soát cuối và sửa §11.4 theo số đo.
Repo scratch ARM: https://github.com/NgTienDuy/c3-arm-lab (public; workflow chạy run.sh trên ubuntu-24.04-arm + ubuntu-24.04).
⚠️ Runner x86 KHÔNG cố định CPU → luôn in `lscpu | grep "Model name"` cùng output. GitHub từng trả 500 ~7 phút (2026-10-07) rồi tự hết.
Phần cứng người dùng có (2026-10-07): ESP32 DevKit + Arduino Uno (chưa nối vào máy này); sẽ mua STM32, Raspberry Pi sau → C3.11/C3.13 dùng
mô phỏng + chính laptop, ghi ESP32 là bước phần cứng thật tiếp theo.

## Việc đang làm — viết nhánh C3 (C3.1 → C3.14)

Yêu cầu (người dùng, 2026-09-27): "Kiểm tra trạng thái Project. Sau đó thực hiện C3-ComputerArchitecture&DigitalLogic,
bám sát theo C1 và C2 đã làm vào roadmap.md đã ghi." → cùng quy ước với C2; **không** sửa `C3.0-INDEX.md`.

| File | Trạng thái |
|---|---|
| C3.1 BooleanLogic&CombinationalCircuits | ✅ 2026-09-27 (80 KB; checkpoint: 21/21 test chính thức trên mạch NAND tự mô phỏng + 20/20 trên HardwareSimulator chính thức qua .hdl phẳng; độ phủ stuck-at của ALU.tst 85,6%; SAT chứng minh tương đương 2³⁸ đầu vào) |
| C3.2 SequentialLogic&FSM | ✅ 2026-09-28 (142 KB; project 3: 8/8 test trên runner + 8/8 trên HardwareSimulator, 4/4 đột biến runner; checkpoint: FSM khung UART (SOF+LEN+CRC-16/MODBUS) bằng C trên QEMU Cortex-M3 khớp mô hình tham chiếu khai báo 2.295/2.295 sự kiện ×3 lần, 10⁶ khung thử 0 lệch, 760.428/760.438 khung tốt (10 mất đều giải thích được); lỗi thật tìm được: xóa cờ ngắt sau khi đọc, bộ thử gom byte, CRC lọt 1/256 với 0x7E chèn sau LEN=1) |
| C3.3 Datapath&BuildingACPU | ✅ 2026-09-29 (140 KB; máy Hack thuần NAND+DFF 3,27 triệu NAND: project 5 6/6 runner + 6/6 HardwareSimulator chính thức; assembler 7/7 + 1.000/1.000 ngẫu nhiên trùng từng bit với bản Java; CRC-16/XMODEM chạy trên CPU tự dựng = 0x31C3; CPU chứng minh SAT tương đương đặc tả 2⁸¹ đầu vào; 4 hiện thực ISA bất đồng ở 5 vùng; assembler Java sai im lặng 6/21 ca biên) |
| C3.4 ISA&Assembly | ✅ 2026-10-02 (215 KB; CoreMark trên 7 cấu hình tập lệnh cùng CRC, đếm lệnh/byte/truy cập bằng plugin QEMU + valgrind; bộ giải mã RV64IM 51.730/51.730 khớp binutils; ABI quan sát bằng thẻ vị trí trên 6 ABI; checkpoint filt.c: 9 biến thể cờ, mỗi biến đổi có -fopt-info + thí nghiệm tắt, kiểm vi sai 10⁶ khối 0 khác; -O2 nhanh 8,7× -O0) |
| C3.5 Pipelining&BranchPrediction | ✅ 2026-10-04 (169 KB; rv5.v pipeline 5 tầng RV32IM tự viết: 111/111 vết retire trùng iss.py, 4 đột biến, lỗi `sra` thật chỉ CoreMark lộ; CPI × tầng NAND cho 8 cấu hình; x86 đo bằng thời gian quy đổi (không PMU): phạt đoán sai 21–27, RAS 16, ROB 512 → 256 khi anh em SMT hoạt động (robwin.exe trên Windows), SMT 0,77×–2,03×; checkpoint: có nhánh 14,25 vs mặt nạ 0,99 chu kỳ/pt ở p = 0,5, xác nhận bằng đối chứng + cachegrind + mô hình P đo độc lập + kế toán chính xác rv5 dư 0) |
| C3.6 MemoryHierarchy | ✅ 2026-10-06 (172 KB; khoảng cách dùng lại (rd.c, thuật toán Mattson) trên 9 tải thật khớp cache 12 đường ±0,28 điểm %; L1 12 đường — phép đo đầu cho 10 vì bộ tiền nạp theo bước chiếm 2 đường (pfprobe: 2 dòng phía trước, bước ≤ 8 KiB, qua trang, lúc bật lúc không); L2 10 đường + huge page khách liền nhau về vật lý; L3 hiệu dụng 10–12 MiB rảnh / 2–3 MiB khi hàng xóm quét 32 MiB; DTLB 16 set × 6 đường; huge page WSL không nới tầm TLB nhưng đi bảng trang 196 → 58 chu kỳ; RFO đo bằng thời gian (ghi thường = 2× lưu lượng); chuyển dòng lõi–lõi 16–95 ns; trần FMA 32 FLOP/chu kỳ, đợt ngắn ~75%; checkpoint: dàn lọc FIR 16 băng × 128 hệ số trên dữ liệu vòng bi CWRU, tile L1 ×3,26–3,46, tile thanh ghi ×5,2–5,5, số trượt L2 giảm 121 lần, v0 chạy đúng ở trần băng thông L3) |
| C3.7 MemoryConsistency&Coherence | ✅ 2026-10-07 (153 KB; ARM thật = runner GitHub Neoverse-N2, x86 = i7 + runner EPYC 7763; litmus.c 29 phép thử khớp herd7 7.58 (SC/TSO/ARMv8/RC11), đối chiếu litmus7; QEMU 8.2.2 sai cả hai chiều (MP 0; stlr/ldar SB 127/triệu — lỗi mã nguồn TCG); mesi.py 4 giao thức + bất biến + 3 đột biến; coh.c: E đắt như M, S rẻ 2,5×; smc.c: DIC=IDC=1 vẫn 999.998/10^6 mã cũ nếu thiếu dsb+isb; checkpoint ring.c: x86 0/10^9 ×2 máy, N2 0,12–47,5 lỗi/triệu, sửa bằng ishst+2×ishld+ctrl (herd7 cần & đủ), C11 ldapr nhanh 8,3× ldar; volatile-only hỏng ngay trên x86 vì gcc) |
| C3.8 SIMD&Vectorization | ✅ 2026-10-07 (94 KB; [i7] AVX2/FMA/AVX-VNNI + runner N2 NEON/SVE(VL 128) + runner x86 Xeon 8573C; RVV qua QEMU 3 VLEN; 12 vòng tự vector hóa + lý do gcc (vect-details); bẫy: "vectorized" = fold-left vaddss, _mm256_load_ps không chắc lỗi, SSE cũ addps lỗi căn lề, AVX2 pack trong nửa 128 bit (10006 sai), vpmaddubsw bão hòa (22/32 khối sai; reduce_range 7 bit — tài liệu ORT), OoO chồng lần gọi làm phép đo độ trễ 1,6 < 2,0; trả nợ C3.4 sat16 packssdw 2,8× compiler, C3.5 sum_ge AVX2 vpmovsxdq 1,4× vs intrinsics 32-bit theo khối 4,2×; checkpoint FIR 128 nhịp CWRU: intrinsics 17,1× [i7] (71% trần), 8,7× N2, SVE chậm hơn NEON trừ -mcpu=neoverse-n2) |
| C3.9 GPUArchitecture | ✅ 2026-10-07 (101 KB; RTX 4060 Laptop qua WSL, CUDA 13.3 redist; ncu bị chặn quyền → trần đo riêng + đếm lệnh SASS + biến thể có kiểm soát; xung 2100→2650 phải đo (bẫy §2.3), bẫy CSE 94 TFLOP/s; phân kỳ ×P trong warp; độ trễ shared 24/L1 40/L2 262/DRAM ~620 ck; DRAM 231, L2 1260, shared 7,78 TB/s; LSU ~1 lệnh nạp/2 ck; gộp kernel ×3,05 = 6:2; GEMM 0,86→31,2 TFLOP/s, sai số FP16/TF32 = làm tròn đầu vào (mô phỏng khớp); PCIe 12,4–13,0 GB/s; checkpoint FIR 0,30→10,7 TFLOP/s cùng bit: nhóm LSU, nhóm ULDC (cpath: không mở rộng theo occupancy), bản nhanh nhất bị chặn phía tính toán dù AI 60 < 66 (bound.cu)) |
| C3.10 NPU&Accelerators | ✅ 2026-10-08 (154 KB; pJ/phép & pJ/lệnh đo bằng RAPL (đơn vị pWh hiệu chuẩn) + NVML: CPU 1,4–2,2 nJ/lệnh dù 2 hay 64 phép, GPU INT8 tensor 0,54 pJ/phép (÷43 so với VNNI); mảng tâm thu Verilog 3 cỡ + 2 lỗi thật (x lan, ?: không dấu) + diện tích PE yosys; CNN CWRU 1-D 100% test → Vela U55/U65/U85 + Edge TPU 14.1: bước 4 tách 250 phép 0,4% đỉnh, viết lại tương đương từng bit ×11–17; Edge TPU không tất định (EXPAND_DIMS 2/10 vs 10/10, Fisher p 3,6e-4), GELU mã 150 → "builtin_code 127", cắt-một-lần; quant 9 kiểu: hiệu chuẩn chỉ lớp bình thường → 75% mà 4 trình biên dịch vẫn nhận; arena tham lam = cận dưới = Vela 1.470 KiB; checkpoint: CPU 8,56 µs/194 µJ vs GPU 96 µs/2.982 µJ batch 1 (chép 19,7 + khởi chạy 39,7 + tính 32,8 µs @1,26 GHz, 79% năng lượng ở CPU điều khiển), batch lớn GPU ×3,8–4,4 thông lượng, ×3,1–3,9 năng lượng (kernel 9% trần)) |
| C3.11 → C3.14 | ☐ |

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
  Kiểm: anchor mục lục, số dòng ``` chẵn, số cột mỗi bảng, CRLF, mọi '§x.y' nội bộ tồn tại, mọi 'Cx.y §z' tồn tại trong file Cx.y (file khung →
  cảnh báo 'tham chiếu tới trước'). ⚠️ 2026-10-06: `.draft-C3.5/` và `.draft-C3.6/` (mọi nguồn thí nghiệm, bench.h, doccheck.py) ĐÃ XÓA theo
  yêu cầu người dùng → leaf sau phải viết lại công cụ. Công thức dựng nhanh: `apt download valgrind gcc-mingw-w64-x86-64-win32 gcc-mingw-w64-base
  binutils-mingw-w64-x86-64 mingw-w64-x86-64-dev mingw-w64-common gcc-mingw-w64-x86-64-win32-runtime libisl23 libmpc3 libmpfr6` → dpkg -x vào
  $S/root; mingw: `x86_64-w64-mingw32-gcc-win32 -B$R/usr/lib/gcc/x86_64-w64-mingw32/13-win32/ -B$R/usr/x86_64-w64-mingw32/bin/
  -L$R/usr/x86_64-w64-mingw32/lib -isystem $R/usr/x86_64-w64-mingw32/include`; valgrind cần VALGRIND_LIB=$R/usr/libexec/valgrind.
  bench.h: hiệu chuẩn = 10^7 lệnh `add %reg,%reg` nối đuôi (KHÔNG `add $1`), kẹp mỗi phép đo giữa 2 lần, trung vị 9 tỉ số.

- C3.7 (2026-10-07): herdtools7 7.58 qua opam KHÔNG cần sudo: `apt download opam libglpk40 libamd3 libcolamd3 libsuitesparseconfig7 libltdl7
  libgmp-dev` → dpkg -x vào $R; `ln -sf /usr/lib/x86_64-linux-gnu/libgmp.so.10 $R/usr/lib/x86_64-linux-gnu/libgmp.so`; OPAMROOT=$S/opam
  `opam init --bare --disable-sandboxing -y -n && opam switch create herd ocaml-base-compiler.4.14.2 && C_INCLUDE_PATH=$R/usr/include:$R/usr/include/x86_64-linux-gnu
  LIBRARY_PATH=$R/usr/lib/x86_64-linux-gnu opam install --assume-depexts herdtools7` (~10 phút). Model: -I $OPAMROOT/herd/share/herdtools7/herd.
  litmus7 cho LDAPR cần GCCOPTS thêm -march=armv8.4-a. RISC-V cross: gcc-13-riscv64-linux-gnu cpp-13-riscv64-linux-gnu binutils-riscv64-linux-gnu
  libgcc-13-dev-riscv64-cross libc6-dev-riscv64-cross. Công cụ kiểm: `.draft-C3.7/src/doccheck.py` (cấu trúc + § + Cx.y §z) và `blockcheck.py`
  (mọi dòng khối ✅ phải có trong out/ — bắt được 1 dòng chép nhầm ở C3.7). Bài học: ghi ra out/ MỌI output sẽ trích (kể cả kết quả pipeline grep).

- C3.10 (2026-10-08): `setup_env.sh S` dựng venv (tensorflow-cpu 2.21.0, ethos-u-vela 5.2.0, numpy 2.5.3; thêm `pip install ai-edge-litert` cho đếm lệnh),
  Edge TPU Compiler 14.1 (sparse clone google-coral/edgetpu `compiler/x86_64`; apt repo Coral 403), iverilog/yosys/yosys-abc, CUDA 13.3, CWRU 16 bản ghi
  (engineering.case.edu/sites/default/files/N.mat). Valgrind: apt download valgrind, VALGRIND_LIB=$R/usr/libexec/valgrind; đếm lệnh CHỈ trong hàm
  (callgrind --toggle-collect='tflite::interpreter_wrapper::InterpreterWrapper::Invoke(int)') — khởi động Python dao động ±10⁸ lệnh. iverilog cục bộ:
  IVL=$R/usr/lib/x86_64-linux-gnu/ivl (run_systolic.sh). pdftotext cần thêm libopenjp2-7 liblcms2-2 libnss3 libnspr4. Năng lượng CPU: cpuwatt.py
  (Get-Counter '\Energy Meter(rapl_package0_pkg)\Energy', pWh, mẫu ~1,2 s; lệch đồng hồ WSL–Windows −1,5 ms); GPU: NVML dlopen.
  ⚠️ Máy chủ có lúc bận (java ~400% trên Windows ~1,5 h ngày 2026-10-08) → gói CPU "rảnh" 51 W; chờ máy rảnh (hostload ≤ 8%) mới đo năng lượng.
  ⚠️ Công suất nền GPU phụ thuộc lịch sử (7,9 W ở P8, 12,3 W ngay sau tải). WSL có tiến trình mô phỏng hmi-scada của người dùng (iedsim, hmikit) — không đụng.

### C3.6 — số đo đáng dùng lại cho leaf sau (2026-10-05/06; chi tiết trong chính tài liệu C3.6)
- Lõi P: L1 5 / L2 15–16 / L3 65–70 / DRAM 400–660 chu kỳ; băng thông 1 luồng L1 ~54, L2 ~38, L3 13–17, DRAM ~5,5 B/chu kỳ (21–24 GB/s);
  cả chip đọc ~61 GB/s (80% của 76,8). Trần FMA 4/16/32 FLOP/chu kỳ (vô hướng/AVX2 double/float), đợt AVX < ~10 µs chỉ ~75% (C3.8 dùng).
- Lõi E: L1 32 KiB 3 chu kỳ, L2 2 MiB/cụm ~20 chu kỳ, DRAM ~3 B/chu kỳ. Chuyển dòng E–E trong cùng cụm CHẬM hơn khác cụm (69–95 vs 57–82 ns),
  người đọc cùng cụm với người ghi 17–51 ns/lần đọc vs khác cụm 5,5 — chưa giải thích được (C3.7 có thể đào tiếp).
- Máy chủ: VBS + HVCI bật (Windows cũng là phân vùng gốc Hyper-V). Tải nền (backgrounddownload, memory compression, Edge, sqlservr) làm
  số đo DRAM/L3 dao động 20–90% → luôn in hostload.sh cạnh số đo; báo theo chu kỳ.
- Bẫy gặp trong C3.6: bộ tiền nạp theo bước (đo độ liên kết phải dùng thứ tự ngẫu nhiên); `pause` trong vòng chờ cộng ~5 ns vào c2c;
  malloc lớn ≡ 16 mod 64 (căn bằng aligned_alloc); gcc -O3 tự unroll-and-jam ×2, tắt nó thì gcc đổi chỗ vòng (interchange) → vô hướng;
  `long` của mingw 32 bit (bộ đếm > 2^31, tích độ dời); chia vùng cho T luồng phải căn 4 KiB (vmovdqa); đọc vùng mmap chưa ghi = trang 0.

### C3.5 — số liệu đã đo (2026-10-02/03)
- rv5 (Verilog, iverilog): 72+18+48+20 lần chạy khớp vết retire iss.py (Python, iss khớp qemu-riscv32 ở output 5 chương trình); lỗi thật:
  `alt ? $signed(x) >>> sh : x >> sh` → dịch logic (vế unsigned kéo cả biểu thức) — CoreMark bắt ở lệnh 60.804, 4 chương trình nhỏ không bắt.
- CPI CoreMark (FASTMIS=0): nofwd EX not-taken 1,831 … fwd EX BHT2+RAS 1,102; fwd ID BHT 1,168 (ID tệ hơn EX vì stall toán hạng 0,083);
  RAS không sửa khi đoán sai: sort jalr sai 879 (EX) vs 2 (ID).
- Độ sâu NAND (yosys 0.33 + abc -g NAND -fast; abc mặc định gập cộng Brent-Kung 18 tầng thành ripple 67): rv1 79; rv5 FASTMIS=0 80;
  FASTMIS=1 (+ đích JALR riêng) 64 = vòng ALU+bypass (kết thúc ở m_res); nofwd 54; BHT 72 (+RREG 67); ID 64 (+BHT 70).
- Checkpoint rv5 (Δ 4 lượt × 2048): nhánh p=0,5: 5,511 chu kỳ/pt (lệnh 4,504 + hủy 1,007), mặt nạ 7,009 mọi p; dư 0 tuyệt đối.
- bpsim (8 KiB): TAGE tốt nhất (CoreMark RV 0,88% vs gshare 4,27%); vết x86 btrace 4M nhánh python/gzip/sort, grep 1M.

- 2026-10-04 (đo lại khi máy rảnh, out2/): xung nhịp turbo trôi 4,2–4,8 GHz → bench.h mới: mỗi lần đo kẹp giữa 2 lần hiệu chuẩn chuỗi add,
  trung vị 9 tỉ số (nạp L1 5,04–5,10; imul 3,0/1,0). brpen2 21–22 chu kỳ, brpen 27; RAS gãy giữa D=16 và 18; ROB: rob2 gãy N=504–508;
  robwin.exe (Windows, LP 4): anh em rảnh → gãy N≈512, anh em chạy pause/add → gãy N≈248–256 (ROB chia đôi tĩnh). smtwin.exe (mingw,
  LP 2+3 thật): ALU 1,03×, imul 2,03×, đuổi 1 MiB 0,77× (L2 1,25 MB chung); ALU+add nối đuôi A 2,17×, ALU+pause A 1,13×. smt.c trong WSL:
  vCPU 2+3 KHÔNG phải anh em thật (mọi tỉ số ≈1). CoreMark x86 IPC 2,57–2,73 (338.520 lệnh/vòng cachegrind; ipc.sh). ck: nhánh p=0,5 14,25,
  cmov 2,0, mặt nạ 1,0, SIMD 1,0; ckfit.py: mô hình 2p(1−p) khớp nhất (RMS 0,39–0,45; a 0,84–0,94; P 25). Lõi: Raptor Cove B0 (CPUID 6/B7/1)
  nhưng L2 lõi P 1.280 KB 10 đường (Windows Win32_CacheMemory; Notebookcheck). k_* dựng lại: build.sh (cachegrind khớp từng số với lần cũ).
- Lỗi đo đã sửa: smt.c dùng `add $1` (bị gộp ở rename) cho tải ALU → đổi sang add thanh ghi; pkill -f "xout2" giết luôn shell (đã ghi Known problems).

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
- C3.5 để lại (kiểm ở rà soát cuối C3): C3.6 — độ trễ DRAM "hàng trăm chu kỳ" (§5.1), MLP/bộ đệm trượt L1/băng thông DRAM (§6.4),
  L2 dùng chung giữa hai luồng SMT (§7.3, D.3); C3.8 — AVX2 cho hàm checkpoint (§8.3, §8.9); C3.12 — đổi thứ tự cộng số thực (§6.6,
  C.1); C3.14 — top-down phân rã IPC (§6.5), luồng anh em SMT khi đo (§7.5).
- C3.1 §6.5 hứa "phép nhân chia 3 tầng pipeline (C3.5)" → đã trả ở C3.5 §2.6 (imul độ trễ 3, thông lượng 1).
- C3.9 để lại: C3.12 — FP16/BF16/FP8, chỗ chúng hỏng (§6.2, §8.3); C3.10 — mảng tâm thu / NPU (D.3). → C3.10 ĐÃ TRẢ (§2, §3).
- C3.10 để lại (kiểm ở rà soát cuối C3): C3.12 — định vị lớp gây mất chính xác, khi nào cần per-channel (§5.1, §5.2), cạm bẫy
  "phân khúc dữ liệu không test" (§5.3); C3.13 — giới hạn công suất/nhiệt của chip (§1.2), shunt + INA219 cho NPU thật (§10.7, §10.9);
  C3.11 — DMA đưa dữ liệu cảm biến tới NPU (D.3 bước 6). C3.9 đã trả: C3.1 §6.3 và
  C3.8 §3.2 (quét tiền tố Kogge-Stone trên GPU, §2.5), C3.8 §1.1 (SIMT, §2).


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

- Edge TPU Compiler 14.1 KHÔNG tất định (cùng file: lúc OK lúc "Internal compiler error"/std::length_error, lỗi có thể treo 2–5 phút) → luôn
  biên dịch lặp (etpu_repeat.sh) hoặc thử tới khi được (etpu_retry.sh), timeout 300 s. TF 2.21 converter SIGSEGV với LSTM batch tĩnh → chạy
  chuyển đổi trong tiến trình con.

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

- 2026-10-08: C3.10 — mọi output chạy thật (CPU [i7] + RTX 4060; Vela/Edge TPU là output trình biên dịch thật, chu kỳ NPU ghi rõ là ước lượng).
  blockcheck: 41 khối ✅, 286 dòng, 0 lệch (bắt được 1 dòng chép nhầm 96,62% → 87,48%); doccheck 0 lỗi, 15 bảng, 231 tham chiếu §, 31 chéo (kiểm đúng
  chủ đề, sửa C3.1 §6.1 → §6). Lỗi/giả thuyết sai tìm được khi làm: "EXPAND_DIMS là nguyên nhân" từ 1 lần chạy → lặp 10 lần mới thấy compiler không
  tất định (kết luận sửa thành: EXPAND_DIMS → 80% gãy); "GELU gộp miễn phí vào conv" sai — là một lượt LUT riêng 4.568 ck (vela_lut.txt), cũng chính
  là "phép thứ 250" của bản gốc; kernel `tuned` không nhanh hơn → đo trong kernel lộ xung 1,26 GHz + khởi chạy đơn lẻ 39,7 µs; K = N² (không phải 4N)
  ở mảng tâm thu; hiệu hai lần chạy cachegrind cho số âm → đếm theo hàm; blocking sync tốn năng lượng hơn quay vòng (lặp 3×2 xác nhận). Khẳng định
  ngoài đã kiểm: Horowitz ISSCC 2014 Fig 1.1.9 (giải mã PDF), whitepaper Ada (4090: 660,6/165,2), tài liệu Coral (8 MB, cắt một lần, ExpandDims ≥13),
  Vela SUPPORTED_OPS (stride>3), calc_blockdep trong mã Vela, trang hãng ST/Renesas/Infineon/TI/Arm (nguồn thứ cấp ghi rõ: Alif, Nordic, NXP qua tìm kiếm).
  Trả tham chiếu tới trước: C3.9 D.3 (mảng tâm thu/NPU). Để lại: C3.12 (định vị lớp gây mất chính xác, per-channel khi nào cần), C3.13 (shunt/INA219,
  giới hạn công suất), C3.11 (DMA đưa dữ liệu tới NPU).

- 2026-10-07: C3.9 — mọi output chạy thật trên RTX 4060 Laptop (run_gpu.sh + các lần chạy riêng cpath/bound/occ/inerr, kèm hostload và
  nvidia-smi trước/sau; 4 file "chép lại từ terminal" ghi rõ). blockcheck 30 khối ✅ / 191 dòng 0 lệch; doccheck 0 lỗi, 15 bảng, 159 tham
  chiếu §, 33 chéo (kiểm đúng chủ đề). run_gpu.sh ONLY_BUILD=1 dịch đủ 13 chương trình. Lỗi/giả thuyết sai tìm được khi làm: fuse.cu đếm
  thiếu một lượt DRAM (5 → 6, tỉ lệ đo ×2,97 lộ ra); giải thích §3.2 cũ "LDS chậm vì lệnh tính địa chỉ" bị bác bởi 3 kernel FIR cùng
  ~2 ck/lệnh nạp → sửa; tile32 trần 1/4 → 1/10 (tính lại theo nhịp LSU); fir_reg3 "~80 thanh ghi" → 94 (occ.cu); giả thuyết "8 KiB hằng
  tràn bộ đệm" bị bác (4/8/16 băng cùng tốc độ); "ghi float4 nhanh hơn" bị bác (chậm hơn 7%); ncu lệnh -c 8 sai (chỉ bắt fir_direct) →
  vòng theo tên. Chưa giải thích (ghi rõ trong tài liệu): ULDC ở F = 16, bản duỗi hết (icache vs IMC), float4 chậm hơn.
- 2026-10-07: C3.8 — mọi output chạy thật ([i7] run_i7.sh với hostload; runner run5/run6, log trong .draft-C3.8/out/run5|run6). blockcheck 37 khối
  ✅ / 209 dòng 0 lệch; doccheck 0 lỗi, 16 bảng, 125 tham chiếu §, 38 chéo (24 khác nhau, kiểm đúng chủ đề). Lỗi tìm được khi làm: tích lũy
  reduce trên stack (thiếu unroll) → K=4 chậm hơn K=2; OoO chồng lần gọi (giữ lại thành §6.2); align bản đầu: imul trong địa chỉ + 64 trang cùng
  set L1 → viết lại; dot8 khối kiểm 64 khi vòng bước 128; fplat ARM: mov #100000 không mã hóa được. Khẳng định ngoài đã kiểm: tài liệu ORT
  (VPMADDUBSW, reduce_range), C3.4 BLOCK=16.

- 2026-10-07: C3.7 — mọi output chạy thật: [i7] (WSL + Windows mingw), runner [N2] run1–run4 + [EPYC] run1–run3 (log trong .draft-C3.7/out/runN),
  QEMU, herd7 (63 test), litmus7 (29 test trên N2). blockcheck: 42 khối ✅, 431 dòng, 0 không khớp (một dòng chép nhầm ở §2.3 đã sửa trước khi
  kiểm). doccheck: 0 lỗi, 19 bảng, 226 tham chiếu §, 52 tham chiếu chéo — kiểm đúng chủ đề bằng tay (bảng trong phiên). Đọc lại: sửa
  sfence 9.585→9.583/triệu, ~15%→~16%, dải N2 M/E (6/7 lần 21–24, một lần 29–37), RMW 60–76, "mọi giao thức có E" → E/UC, đột biến thứ ba
  của mesi_mut, thêm ⚠️ K=512 (tập làm việc vượt L1 lõi E). Khẳng định ngoài đã kiểm: Go memory model 2022, Rustonomicon "inherits C++20",
  Linux x86 __smp_mb = lock addl, QEMU v8.2.2 + master trans_LDAR/STLR + tcg_out_mb, AMD MOESI (qua nguồn thứ cấp — ghi rõ).
  Trả tham chiếu: C2.13 §6.1/§8.5/§8.8 (ARM thật), C3.3 §5.5 + C3.4 §1.7 (mã cũ trên ARM thật), C3.6 §8.2/§9.4 (E–E cùng cụm: sạch 5,3 ns, bẩn 38,8).

- 2026-10-06: C3.6 — mọi output chạy thật (WSL + thẳng trên Windows qua mingw); script đối chiếu từng dòng của mọi khối ✅ với file output
  (mọi dòng khớp; các output chỉ có trong terminal được chép lại vào out/ trước khi xóa nháp). Đọc lại toàn văn, sửa: số tải 8 → 9 (7 chương
  trình); l1plru dùng trang 0..K−1 (không phải ngẫu nhiên) + ghi chú; lần đo L1 đầu: 3/5 set trượt hẳn ở K = 11 (không phải "cả năm set");
  L1 48K/12 đường có từ Sunny Cove; "4,5–5,0" → 4,5–4,9 (SMT); E-core L2 23,0–25,8; mái L1 cho v2/v3 (I tính theo byte đọc L1: 0,33/0,49);
  bản nojam là interchange chứ không phải "nhiều lưu lượng hơn" (cachegrind lộ ra: 25,8·10⁹ lệnh, trượt ÷43, vẫn chậm 3×); cgdemo phải căn
  64 B (malloc ≡ 16 mod 64 làm số trượt bản xáo trộn gấp đôi); `sum_unused` bị xóa cả lời gọi (không chỉ còn ret); C3.4 §8 → §9 (checkpoint).
  doccheck: 0 lỗi, 40 bảng, 307 tham chiếu §, CRLF; 25 tham chiếu chéo Cx.y §z kiểm đúng chủ đề bằng tay. Trả tham chiếu tới trước:
  C3.5 §5.1/§6.4 (DRAM hàng trăm chu kỳ, MLP, băng thông) → C3.6 §2.2, §7; C3.3 §6.5 (vùng thiết bị không cache) → §4.1; C3.2 §2.2 (bank/
  hàng/cột) → §7.5; C3.4 (bẫy đo roadmap C3.6) → §10.3.

- 2026-10-04: C3.5 — mọi output chạy thật; đo x86 lại khi máy rảnh với bench.h hiệu chuẩn kề bên (out2/). Đọc lại toàn văn, sửa: §1.3
  "bắt ở srai đầu tiên" → lệnh retire thứ 11.548 (241 phép dịch số học trước đó vô hại); 450 lệnh sai = 216 + 216 + 4 srai + 1 mv;
  §4.3 TAGE hòa tournament ở crc; §4.4 trỏ mô phỏng i.i.d. §4.5; §6.5 nguyên nhân IPC ghi là ứng viên; §8.4 cmov 8 lệnh vs mặt nạ 7;
  RAS khớp R = 15/16 → điểm gãy phân định 16; §0.3 tiên quyết ghi rõ C3.3 §4/§1.4, C3.4 §7.2. Kiểm lại bằng chạy mới: 24 đột biến
  (output + dòng vết đầu tiên khác khớp bảng §1.3), rv1 6/6, khối tổng hợp (cộng 22/346, slt 28/239, eq 14/127, sra 11/439),
  ck rv5 tái tạo đúng chu kỳ (89.346 / 104.677). doccheck.py (dựng lại, ở .draft-C3.5/src/): 0 lỗi, 35 bảng, 253 tham chiếu §, CRLF;
  17 tham chiếu chéo Cx.y §z kiểm đúng chủ đề bằng tay.
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
