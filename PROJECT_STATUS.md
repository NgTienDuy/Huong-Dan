# Project Status — Huong-Dan / E2E-SYSTEM

**State:** C1–C4 hoàn tất. C5 (Networking) đang làm: C5.1, C5.2 xong (2026-11-12); C5.3–C5.16 chưa bắt đầu.
**Updated:** 2026-11-12
**Last session:** claude-code (Opus 5.5), 2026-11-12 (phiên 8): kiểm toán nháp C5.2 do một phiên trước bỏ dở (dự đoán có giờ mâu thuẫn mtime → viết lại dự đoán, chạy lại mọi thí nghiệm), thêm thí nghiệm mới (MSG_CONFIRM của ping, cuộc đua tự chữa sau giả mạo ARP, vòng lặp tích lũy broadcast, br_netfilter, hố đen TCP lặp 30+16+20 lần, Checkpoint IP trùng, mô hình PoE), runner run44/45b/46 (x86 đổi giữa AWS và Azure), viết xong C5.2 (182 KB, 29 khối ✅, 48 dự đoán: 35 ✓ 7 ½ 6 ✗).

## NEXT ACTION

Viết C5.3 (Tầng liên kết cho edge: Wi-Fi, BLE, LoRa, Zigbee, cellular — checkpoint: chọn radio cho ba kịch bản, tính link budget, **đo thực tế**). Không có radio nối vào WSL: đo được Wi-Fi thật của [i7-host] (`netsh wlan`, RSSI/tốc độ/kênh theo thời gian, quét kênh lân cận), BLE/LoRa/cellular bằng mô hình + số liệu datasheet có trích nguồn; phần cứng ESP32 để ở Mở rộng. Tạo `E2E-SYSTEM/C5-Networking/.draft-C5.3/{doc,src,out}`, ghi `out/predictions.txt` trước mọi phép đo. Người dùng muốn: làm tuần tự C5.3 → C5.16 theo `roadmap.md`, rồi rà soát toàn nhánh C5.
<!-- /NEXT -->

## Completed

| Nhánh | Kết quả | Kiểm chứng |
|---|---|---|
| C1 | ✅ trước 2026-09-24 (người dùng viết; trừ C1.0-INDEX.md) | — |
| C2 (C2.1–C2.13) | ✅ 2026-09-26 | mọi output chạy thật; doccheck 13/13 file 0 lỗi |
| C3 (C3.1–C3.14) | ✅ 2026-10-09 | doccheck 14/14 file 0/0; blockcheck C3.7–C3.14: 2.834 dòng, 0 lệch, trước khi xóa nháp |
| C5.1 | ✅ 2026-11-12 | doccheck 0/0; blockcheck 60 khối ✅, 842 dòng, 0 lệch; xrefcheck 6/0; CRLF; nháp `.draft-C5.1/` giữ lại tới khi rà soát nhánh |
| C5.2 | ✅ 2026-11-12 | doccheck 0/0; blockcheck 29 khối ✅, 866 dòng, 0 lệch; xrefcheck 17/0; CRLF; prosenums 67/629 đã đọc (dạng thập phân Việt của số trong `out/`, phép suy ra ghi cạnh); nháp `.draft-C5.2/` giữ lại |
| C4 (C4.1–C4.13) | ✅ 2026-11-10 | doccheck 13/13 leaf 0 lỗi 0 cảnh báo; blockcheck 13/13 leaf: 611 khối ✅, 7.838 dòng, 0 lệch; 361 dẫn chiếu `C4.N §X` giữa các leaf, 0 sai; trước khi xóa nháp |

## Quy ước viết leaf (giữ cho mọi nhánh)

- Ghi đè hoàn toàn file khung (bỏ front-matter YAML); không sửa `Cx.0-INDEX.md`. Mở đầu `# Cx.y · <tên> — \`Lv\``, khối `> Mục tiêu của tài liệu`
  + tiên quyết + điều kiện hoàn thành, `## Mục lục`. §0 (nguyên tắc, bộ công cụ, môi trường kiểm chứng, ký hiệu ✅ 🔬 ⚠️);
  mỗi sub-leaf của roadmap một mục; Checkpoint có lời giải + Tự chấm + Mở rộng; Phụ lục A–D; "Tổng kết: mười điều"; chân trang `*Môi trường đo: …*`.
- Mọi ✅ là output chạy thật, chép nguyên văn bằng công cụ ghép (`…` = dòng lược); dự đoán ghi vào `out/predictions.txt` TRƯỚC khi chạy, chấm nghiêm ở Phụ lục B.3
  (đúng cơ chế nhưng sai con số là ½) bằng `out/grades.txt` + script đếm.
- Tiếng Việt, code/identifier tiếng Anh; file CRLF. Nháp ở `<nhánh>/.draft-Cx.y/` (không commit), xóa khi xong nhánh.
- Công cụ kiểm (C5: ở `C5-Networking/.draft-tools/`, không commit; nếu mất thì dựng lại): ghép `doc/*.md` + `{{out:FILE[:A-B][:cut=N]}}`; doccheck (cấu trúc, anchor, mọi §, chân trang);
  blockcheck (mỗi dòng của khối ✅ có trong `out/`); prosenums (số trong văn xuôi không có nguyên văn trong `out/`); kiểm dẫn chiếu giữa các leaf
  (phải thử với một dẫn chiếu sai trước khi tin "0 lỗi").
- Không đăng lời giải `.hdl` của nand2tetris (repo public).

## Môi trường (chỉ những gì leaf sau cần)

- **Phòng lab mạng không root trên [i7]** (C5): `unshare --user --map-root-user --net --mount --fork bash`, rồi `mount -t tmpfs none /run; mkdir /run/netns` để dùng `ip netns`; veth, bridge, vxlan/ipip/gre, netem, dummy đều tự nạp module. tcpdump phải có `-Z root --immediate-mode -B 65536` và đọc dòng `dropped`; `nstat` cần `NSTAT_HISTORY` riêng mỗi namespace; `netem corrupt` trên máy gửi TCP chỉ trúng siêu gói GSO — đặt trên router ở giữa. Không bao giờ `| tee FILE | head` (SIGPIPE cắt file).
- Runner (run41): VF `mlx5_core` của Azure nhận `ethtool -K rx-fcs on` → khung *nhận* mang FCS thật; `hv_netvsc` thì không.
- Runner x86 **đổi đám mây giữa các lần chạy** (run42/44: AWS EC2 m8id.large, Xeon 6975P-C, Linux 7.0.0-1014-aws, ENA, MTU 9001, gc_thresh 15360/16384; run43/45b/46: Azure EPYC 7763/9V45, 7.0.0-1017-azure, hv_netvsc, MTU 1500); arm luôn Azure. In `sys_vendor` ở dòng đầu. `/proc/net/stat/*` là theo CPU — cộng mọi dòng.
- Lab C5.2: `br_netfilter` có nạp trên kernel WSL → namespace mới có `bridge-nf-call-iptables=1` → bridge kiểm MTU kiểu IP và tự phân mảnh; tắt bằng sysctl trong namespace của bridge. tcpdump phải ghi vào tmpfs (`TMPDIR` = scratchpad), ghi vào /mnt/d mất 96 % khung. Không sửa script khi nó đang chạy. `ip tcp_metrics flush` bị cấm trong userns; dùng `tcp_no_metrics_save=1`.
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
- 2026-11-10, sau khi đọc lại và sửa C4.2–C4.9 (không còn nháp): dẫn chiếu giữa các leaf 361/0 sai; CRLF 13/13; số cột của mọi bảng nhất quán (bộ kiểm có đối chứng âm). Không khối ✅ nào bị sửa.
- 2026-11-12, C5.1: `doccheck` 0 lỗi 0 cảnh báo; `blockcheck` 60 khối ✅ / 842 dòng / 0 lệch; `xrefcheck` 6 dẫn chiếu / 0 sai (đối chứng âm: bắt đủ anchor hỏng, § không tồn tại, dẫn chiếu `C4.13 §29`, một chữ số sửa trong khối ✅); `prosenums` 43/695 số không có nguyên văn trong `out/` — đã đọc từng số: phép suy ra viết ngay cạnh, trích dẫn tài liệu, năm, phiên bản. Không có MAC/IP/tên VPN/hostname của máy trong leaf hay `out/`.
- 2026-11-12, C5.2: `doccheck` 0 lỗi 0 cảnh báo; `blockcheck` 29 khối ✅ / 866 dòng / 0 lệch (2 dấu ✅ còn lại là chú giải §0.4 và chân trang); `xrefcheck` 17 / 0 sai; `prosenums` 67/629 — đã đọc, một số sai thật đã sửa (khoảng thời gian bị lược ở §8.2), các số từ lần chạy bị ghi đè chép vào `out/overwritten_runs.txt`; CRLF 2066 dòng, 0 LF trần.
