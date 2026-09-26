# Project Status — Huong-Dan / E2E-SYSTEM

**State:** IN PROGRESS
**Updated:** 2026-09-26
**Last session:** claude-code (Opus 5.5), 2026-09-26, viết xong C2.10, C2.11; tiếp theo C2.12

## NEXT ACTION

Viết `E2E-SYSTEM/C2-DataStructures&Algorithms/C2.12-Online&StreamingAlgorithms.md` (thí nghiệm trong scratchpad, dán output thật;
checkpoint: p99 của luồng 10⁸ mẫu, sai số < 1%, không lưu toàn bộ — dùng lại t-digest/histogram log của C2.10 §6), rồi C2.13; sau C2.13 rà soát toàn bộ C2 lần cuối (yêu cầu người dùng 2026-09-26: nhất quán, chi tiết, chuyên sâu,
đầy đủ, khoa học). Công cụ kiểm cấu trúc: `doccheck.py` (anchor slug GitHub, code fence, số cột bảng, CRLF, liên kết file) —
nằm trong scratchpad, mất thì viết lại (~80 dòng Python).

## Việc đang làm — viết nhánh C2 (C2.1 → C2.13)

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
| C2.12 Online&StreamingAlgorithms | ☐ |
| C2.13 ConcurrentDataStructures | ☐ |

## Known problems

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
