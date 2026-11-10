# Project Status — Huong-Dan / E2E-SYSTEM

**State:** C1, C2, C3, C4 hoàn tất. Nhánh kế tiếp chưa được người dùng chỉ định.
**Updated:** 2026-11-10
**Last session:** claude-code (Opus 5.5), 2026-11-10 (phiên 6): viết xong C4.12 và C4.13; trả nợ của C4.1 (posix_spawn, XSAVE, EPYC, 215 ns), làm dày C4.9, sửa dẫn chiếu tới C4.12/C4.13 trong C4.2/C4.3/C4.5/C4.10/C4.11; rà soát toàn nhánh C4; xóa mọi nháp `.draft-*` của C4.

## NEXT ACTION

Rà soát nhánh C4 — đọc lại toàn văn đã ghép (phần còn nợ từ khi viết): C4.2, C4.3, C4.4, C4.5, C4.6, C4.7, C4.8, C4.9. Đã đọc: (cập nhật khi xong từng leaf).
Chỉ sửa văn xuôi (nháp và `out/` đã xóa — không sửa khối ✅). Sửa bằng Python đọc/ghi giữ CRLF, mỗi chuỗi cũ phải xuất hiện đúng một lần. Xong thì commit + push.
Sau đó: chờ người dùng chọn nhánh tiếp (C5 Networking là nhánh kế theo số thứ tự).

## Completed

| Nhánh | Kết quả | Kiểm chứng |
|---|---|---|
| C1 | ✅ trước 2026-09-24 (người dùng viết; trừ C1.0-INDEX.md) | — |
| C2 (C2.1–C2.13) | ✅ 2026-09-26 | mọi output chạy thật; doccheck 13/13 file 0 lỗi |
| C3 (C3.1–C3.14) | ✅ 2026-10-09 | doccheck 14/14 file 0/0; blockcheck C3.7–C3.14: 2.834 dòng, 0 lệch, trước khi xóa nháp |
| C4 (C4.1–C4.13) | ✅ 2026-11-10 | doccheck 13/13 leaf 0 lỗi 0 cảnh báo; blockcheck 13/13 leaf: 611 khối ✅, 7.838 dòng, 0 lệch; 361 dẫn chiếu `C4.N §X` giữa các leaf, 0 sai; trước khi xóa nháp |

## Quy ước viết leaf (giữ cho mọi nhánh)

- Ghi đè hoàn toàn file khung (bỏ front-matter YAML); không sửa `Cx.0-INDEX.md`. Mở đầu `# Cx.y · <tên> — \`Lv\``, khối `> Mục tiêu của tài liệu`
  + tiên quyết + điều kiện hoàn thành, `## Mục lục`. §0 (nguyên tắc, bộ công cụ, môi trường kiểm chứng, ký hiệu ✅ 🔬 ⚠️);
  mỗi sub-leaf của roadmap một mục; Checkpoint có lời giải + Tự chấm + Mở rộng; Phụ lục A–D; "Tổng kết: mười điều"; chân trang `*Môi trường đo: …*`.
- Mọi ✅ là output chạy thật, chép nguyên văn bằng công cụ ghép (`…` = dòng lược); dự đoán ghi vào `out/predictions.txt` TRƯỚC khi chạy, chấm nghiêm ở Phụ lục B.3
  (đúng cơ chế nhưng sai con số là ½) bằng `out/grades.txt` + script đếm.
- Tiếng Việt, code/identifier tiếng Anh; file CRLF. Nháp ở `<nhánh>/.draft-Cx.y/` (không commit), xóa khi xong nhánh.
- Công cụ kiểm (đã xóa cùng nháp C4; dựng lại cho nhánh sau): ghép `doc/*.md` + `{{out:FILE[:A-B][:cut=N]}}`; doccheck (cấu trúc, anchor, mọi §, chân trang);
  blockcheck (mỗi dòng của khối ✅ có trong `out/`); prosenums (số trong văn xuôi không có nguyên văn trong `out/`); kiểm dẫn chiếu giữa các leaf
  (phải thử với một dẫn chiếu sai trước khi tin "0 lỗi").
- Không đăng lời giải `.hdl` của nand2tetris (repo public).

## Môi trường (chỉ những gì leaf sau cần)

- Không sudo trên [i7]: `apt download <gói>` + `dpkg -x` vào scratchpad. Việc nặng chạy trong `systemd-run --user --scope` (cgroup riêng).
- [i7] i7-13650HX lai P/E, WSL2 (Linux 6.18, `CONFIG_HZ=250`), không root, không PMU; Windows counters qua interop (`Get-Counter`).
- Root, ARM/x86 thật: runner GitHub qua repo thử nghiệm riêng `NgTienDuy/c3-arm-lab` (private; commit với tác giả
  `Luca <215770720+NgTienDuy@users.noreply.github.com>`). Runner x86 đổi CPU giữa các lần (EPYC 7763/9V45/9V74, Xeon 8370C/8573C/6973P-C) — luôn in `lscpu`.
  Runner hiện chạy Linux 7.0.0-1017-azure (`PREEMPT_LAZY`, HZ 1000); tác tử `provjobd` có chương trình BPF trên `sys_enter_mmap`.
  Cài gói apt mỗi gói một lệnh. Mã nguồn kernel: `gh api -H "Accept: application/vnd.github.raw" repos/torvalds/linux/contents/PATH?ref=v6.18`.
- GPU RTX 4060 Laptop, CUDA 13.3 redist; `ncu` bị chặn quyền bộ đếm. Đồng hồ trong WSL: `CLOCK_MONOTONIC_RAW`.

## Known problems

- Git: Windows `autocrlf=true`, WSL thì không → mọi file hiện "modified". Xem thật: `git -c core.autocrlf=true status`; add: `git -c core.autocrlf=true add <file>`.
- Thay đổi C1, `90-PROJECTS/`, `99-TAI-LIEU-CHUNG/` là của người dùng — không đụng, chỉ commit file mình viết.
- Máy chủ dùng chung (game, Edge, tác vụ nền): in tải máy cạnh mọi số đo, so sánh xen kẽ A/B.
- `pkill -f <mẫu>` có thể giết chính shell; tìm theo PID. WSL có tiến trình hmi-scada của người dùng (iedsim, hmikit) — không đụng.
- TSan trên kernel WSL này cần `setarch $(uname -m) -R`. Chương trình cố ý sập phải gọi `prctl(PR_SET_DUMPABLE, 0)` (core_pattern của WSL là pipe).

## Việc cần báo người dùng (chưa làm, cần họ quyết)

- Thư mục crash dump của WSL phía Windows (`%LOCALAPPDATA%\Temp\wsl-crashes`) giữ ~5,7 GiB file `.dmp` từ các phiên trước. Nằm ngoài dự án → không tự xóa.
- C4.4 §10 dùng mô hình `mpsim.py` thay cho LittleFS v2.11.3 thật (biên dịch mã tải về bị bộ phân loại an toàn chặn). Nếu người dùng cho phép, tải lại,
  chạy LittleFS thật và thay §10.3 (ghi trong C4.4 §11.8 mục 3 và B.4). Bản tải về cũ đã bị xóa cùng nháp.

## Blockers

- Không có vi điều khiển nối vào máy (ESP32 DevKit, Arduino Uno có nhưng chưa nối), không SBC chạy Linux: phần cứng thật để ở "Mở rộng" và B.4 của các leaf.
  Mở khóa: người dùng nối thiết bị (USB → `usbipd` cho WSL).

## Last verification

- 2026-11-10, trước khi xóa nháp: `doccheck.py C4.*.md`: 13 leaf 0 lỗi 0 cảnh báo (17 lỗi chỉ ở `C4.0-INDEX.md` — file mục lục, không theo khuôn leaf).
  `blockcheck.py C4.N-*.md .draft-C4.N/out [src]` cho N = 1…13: 90/62/55/30/38/30/39/24/15/61/72/48/47 khối ✅, tổng 7.838 dòng, 0 lệch.
  Kiểm dẫn chiếu `C4.N §X` giữa các leaf: 361, 0 sai (đối chứng âm: bắt đúng 2/2 dẫn chiếu sai cài sẵn). Mọi leaf CRLF, 0 dòng LF trần.
