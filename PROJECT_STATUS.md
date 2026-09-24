# Project Status — Huong-Dan / E2E-SYSTEM

**State:** IN PROGRESS
**Updated:** 2026-09-24
**Last session:** claude-code (Opus 5.5), 2026-09-24, đang viết nhánh C2

## NEXT ACTION

Viết `E2E-SYSTEM/C2-DataStructures&Algorithms/C2.4-Heaps&PriorityQueues.md` theo quy ước bên dưới
(thí nghiệm chạy trong scratchpad, dán output thật vào tài liệu), rồi lần lượt C2.5 → C2.13.

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
| C2.4 Heaps&PriorityQueues | ☐ |
| C2.5 Graphs&Traversal | ☐ |
| C2.6 ShortestPaths&Flow | ☐ |
| C2.7 Sorting&Selection | ☐ |
| C2.8 DynamicProgramming | ☐ |
| C2.9 Greedy&Correctness | ☐ |
| C2.10 ProbabilisticDataStructures | ☐ |
| C2.11 CacheAwareAlgorithms | ☐ |
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

## Last verification

- 2026-09-24: C2.3 — số trang đọc/truy vấn SQLite đếm bằng /proc/self/io syscr; anchor OK.
- 2026-09-24: C2.2 — oaht.h qua kiểm thử vi sai 3×10⁶ thao tác vs std::unordered_map dưới ASan+UBSan; anchor OK.
- 2026-09-24: C2.1 — mọi output trong tài liệu chạy thật; assemble.py kiểm anchor mục lục (0 hỏng), code fence chẵn, CRLF.
