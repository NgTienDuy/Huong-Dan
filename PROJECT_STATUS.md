# Project Status — Huong-Dan / E2E-SYSTEM

**State:** ĐANG VIẾT C3 (C3.1 → C3.14)
**Updated:** 2026-09-27
**Last session:** claude-code (Opus 5.5), 2026-09-27, bắt đầu nhánh C3

## NEXT ACTION

Viết C3.2 (Logic tuần tự, FSM) theo quy ước C1/C2; checkpoint cần MCU → dùng QEMU Cortex-M3 (mps2-an385) + ghi rõ giới hạn. Sau đó C3.3 → C3.14, mỗi file một commit.
Công cụ dựng lại được theo mục "Môi trường C3" (scratchpad mất sau phiên).

## Việc đang làm — viết nhánh C3 (C3.1 → C3.14)

Yêu cầu (người dùng, 2026-09-27): "Kiểm tra trạng thái Project. Sau đó thực hiện C3-ComputerArchitecture&DigitalLogic,
bám sát theo C1 và C2 đã làm vào roadmap.md đã ghi." → cùng quy ước với C2; **không** sửa `C3.0-INDEX.md`.

| File | Trạng thái |
|---|---|
| C3.1 BooleanLogic&CombinationalCircuits | ✅ 2026-09-27 (80 KB; checkpoint: 21/21 test chính thức trên mạch NAND tự mô phỏng + 20/20 trên HardwareSimulator chính thức qua .hdl phẳng; độ phủ stuck-at của ALU.tst 85,6%; SAT chứng minh tương đương 2³⁸ đầu vào) |
| C3.2 SequentialLogic&FSM | ⏳ tiếp theo |
| C3.3 → C3.14 | ☐ |

### Môi trường C3 (không cần sudo)

- `apt download` + `dpkg -x` vào `scratchpad/root`: qemu-user-static, qemu-system-arm/misc (8.2.2), iverilog 12, yosys 0.33,
  gcc-arm-none-eabi 13.2.1 + newlib, gcc-aarch64/riscv64-linux-gnu 13 (+ libc6-dev-*-cross), valgrind 3.22, openjdk-21-jdk.
  Cross gcc Linux cần `--sysroot=$R`; JDK: các symlink conf trỏ /etc → sửa trỏ `$R/etc`.
- nand2tetris: mã nguồn bộ công cụ Java (Drive id 1stcWUSeAixCRHWOjc9sgBhq5voSLvun8) — biên dịch bằng javac 21 sau khi đổi
  định danh `enum`→`enumr` và bỏ `import Hack.*;`; file .tst/.cmp chính thức lấy từ repo `nand2tetris/web-ide`
  (projects/src/project_0x/*.ts) + script thêm `output-file` và định dạng `%B1.W.1` cho simulator cũ. Không đăng lời giải .hdl
  (tác giả khóa học đề nghị không công khai; repo này public) — dùng trình mô phỏng cổng tự viết + test chính thức.
- Phần cứng: không có PMU (perf_event HW → ENOENT), không RAPL; có GPU RTX 4060 Laptop (nvidia-smi: công suất/nhiệt/xung thật).

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
