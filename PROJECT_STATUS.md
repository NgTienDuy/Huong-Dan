# Project Status — Huong-Dan / E2E-SYSTEM

**State:** IN PROGRESS — nhánh C1, C2, C3 hoàn tất; chưa bắt đầu nhánh kế tiếp
**Updated:** 2026-10-09
**Last session:** claude-code (Opus 5.5), 2026-10-09: xong C3.13 + C3.14, rà soát toàn bộ C3, xóa mọi `.draft-*`, gọn file này, commit + push. Dừng sạch.

## NEXT ACTION

Chờ yêu cầu của người dùng. Nếu được giao nhánh kế theo `E2E-SYSTEM/roadmap.md` (C4-OperatingSystems&Concurrency): đọc `C4.0-INDEX.md`
và các file khung C4.x, rồi viết C4.1 theo đúng "Quy ước viết leaf" dưới đây (không sửa `C4.0-INDEX.md`).

## Completed

| Nhánh | Kết quả | Kiểm chứng |
|---|---|---|
| C1 | ✅ trước 2026-09-24 (theo người dùng: "đã viết xong C1, trừ C1.0-INDEX.md") | — |
| C2 (C2.1–C2.13) | ✅ 2026-09-26 | mọi output chạy thật; doccheck 13/13 file 0 lỗi; rà soát cuối 2026-09-26 |
| C3 (C3.1–C3.14) | ✅ 2026-10-09 | doccheck 14/14 file: 0 lỗi, 0 cảnh báo (anchor, fence, cột bảng, CRLF, mọi § và mọi `Cx.y §z` tồn tại); blockcheck C3.7–C3.14: mọi dòng của mọi khối ✅ có trong file output (2.834 dòng, 0 lệch) trước khi xóa nháp |

Rà soát cuối C3 (2026-10-09) — các sửa nội dung đáng nhớ:
- C3.6 §3.4: "+56% 4K aliasing ở d ≡ 16" phần lớn là **lệnh ghi 32 B vắt dòng** (×1,28 ở mọi offset lệch 32 B); 4K aliasing thật chỉ thêm ~×1,10 khi
  b nằm ngay sau a (đo lại bằng tỉ số kẹp tham chiếu, `alias4`, C3.14 §7.3). `alias2`/`alias3` trước đó đo nhầm vòng vô hướng (đọc objdump mới thấy).
- C3.4 §9.7 / C3.14 §7.1: hai cụm thời gian của bản AVX2 KHÔNG do lõi P/E, anh em SMT hay xung (ghim + hiệu chuẩn từng lượt); cơ chế còn mở.
- Đồng hồ WSL2 lệch 2,5–3,3%, chiều đổi theo lần khởi động và trong một phiên (tick 9.715–9.749 rồi 10.271–10.331) → ghi chú ở C3.5–C3.12.
- C3.13 §8.6: Windows tự hạ QoS tiến trình tải không cửa sổ khởi từ WSL → −27% thông lượng ở cùng 55 W; tự khai HighQoS trả lại; biện pháp
  "một luồng mỗi lõi vật lý" +3,8% chỉ ở trạng thái QoS thấp, không phân biệt được khi HighQoS.

## Quy ước viết leaf (rút từ C1, giữ cho mọi nhánh)

- Ghi đè hoàn toàn file khung (bỏ front-matter YAML); không sửa `Cx.0-INDEX.md`. Mở đầu `# Cx.y · <tên> — \`Lv\``, khối `> Mục tiêu của tài liệu`
  + tiên quyết + điều kiện hoàn thành, `## Mục lục` (bảng, anchor). §0 (nguyên tắc, bộ công cụ, môi trường kiểm chứng, ký hiệu ✅ 🔬 ⚠️);
  mỗi sub-leaf của roadmap một mục; Checkpoint có lời giải + Tự chấm + Mở rộng; Phụ lục A–D; "Tổng kết: mười điều"; chân trang môi trường đo.
- Mọi ✅ là output chạy thật, chép nguyên văn (`…` = dòng lược); ghi mọi output sẽ trích ra file trước khi viết; kiểm bằng doccheck + blockcheck.
- Tiếng Việt, code/identifier tiếng Anh; file CRLF. Nháp ở `.draft-Cx.y/` (không commit), xóa khi xong nhánh.
- Không đăng lời giải `.hdl` của nand2tetris (repo public).

## Môi trường (chỉ những gì leaf sau cần)

- Không sudo: `apt download <gói>` + `dpkg -x` vào scratchpad (qemu, iverilog/yosys, cross gcc, valgrind `VALGRIND_LIB`, mingw-w64, opam/herdtools7).
- [i7] i7-13650HX lai P/E, WSL2 không PMU; số đo thật phía Windows qua interop không cần admin: `Get-Counter` (`\Energy Meter(*)`, xung từng CPU
  logic, nhiệt TZ0), chương trình mingw ghim lõi (`SetThreadAffinityMask`) và **tự khai HighQoS** (`SetProcessInformation`, ProcessPowerThrottling).
- ARM/x86 thật: runner GitHub qua scratch repo `NgTienDuy/c3-arm-lab` (commit với tác giả `Luca <215770720+NgTienDuy@users.noreply.github.com>`;
  email riêng bị chặn khi push). Runner x86 đổi CPU giữa các lần (EPYC 7763 / 9V45 / Xeon 8573C) — luôn in `lscpu`.
- GPU RTX 4060 Laptop, CUDA 13.3 redist; `ncu` bị chặn quyền bộ đếm (ERR_NVGPUCTRPERM). Đồng hồ trong WSL: dùng `CLOCK_MONOTONIC_RAW`.

## Known problems

- Git: Windows `autocrlf=true`, WSL thì không → mọi file hiện "modified". Xem thật: `git -c core.autocrlf=true status`; add: `git -c core.autocrlf=true add <file>`.
- Thay đổi C1, `90-PROJECTS/`, `99-TAI-LIEU-CHUNG/` là của người dùng — không đụng, chỉ commit file mình viết.
- Máy chủ dùng chung (game, Edge, tác vụ nền 7–25% CPU): in `hostload` cạnh mọi số đo, so sánh xen kẽ A/B trong cùng một chuỗi; đo năng lượng khi ≤ 8%.
- `pkill -f <mẫu>` có thể giết chính shell; tìm theo PID. WSL có tiến trình hmi-scada của người dùng (iedsim, hmikit) — không đụng.
- TSan trên kernel WSL này cần `setarch $(uname -m) -R`. Renode 1.17.0 STM32G0 có 4 chỗ sai mô hình (DMA HT/TC, ADC chia nguyên, quantum, NVIC 4 bit)
  — C3.11 §2.2 ghi cách vá. Edge TPU Compiler 14.1 không tất định — biên dịch lặp.

## Blockers

- Không có vi điều khiển nối vào máy (ESP32 DevKit, Arduino Uno có trong tay nhưng chưa nối), không Raspberry Pi/SBC, không NPU thật: các phép đo
  đó để ở mục "Mở rộng" của C3.x. Mở khóa: người dùng nối thiết bị (USB → `usbipd` cho WSL).

## Last verification

- 2026-10-09: `doccheck.py` trên C3.1–C3.14: 14 file, 0 lỗi, 0 cảnh báo. `blockcheck.py` C3.7–C3.14 với `out/` của từng nháp: 0 dòng lệch
  (C3.7 431, C3.8 209, C3.9 191, C3.10 286, C3.11 301, C3.12 618, C3.13 371, C3.14 427). Sau đó xóa `.draft-C3.7` … `.draft-C3.14`.
