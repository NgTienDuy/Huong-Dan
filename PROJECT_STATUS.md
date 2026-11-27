# Project Status — Huong-Dan / E2E-SYSTEM

**State:** C1–C5 hoàn tất. C5 (Networking, 16 leaf) đã rà soát cả nhánh và xóa nháp ngày 2026-11-27. Nhánh kế tiếp theo roadmap: C6 · Embedded Systems & Firmware (mọi leaf còn là file khung).
**Updated:** 2026-11-27 (phiên 16)
**Last session:** claude-code (Opus 5.5), 2026-11-27 (phiên 16): rà soát và đóng nhánh C5. Kiểm bằng script cả 16 leaf — ghép lại từ nháp trùng từng byte, cấu trúc, khối ✅ so với `out/`, dẫn chiếu giữa leaf *và* chủ đề của mục đích, phiên bản công cụ, số trong văn xuôi chỉ có ở file tự viết (grades/predictions), khối ✅ chứa traceback / mục rỗng / giá trị rỗng (mỗi phép quét có đối chứng âm) — rồi đọc kỹ C5.15 và C5.16 so với `out/`. Sửa: C5.2 §6.1 (khối ✅ là một lần chạy hỏng suốt hai tuần, lần chạy tốt đã bị ghi đè → chạy lại `mtu.sh speed`); C5.16 §5.3 (RTU IEC 104 đóng kết nối bởi t1 tính từ khung chưa xác nhận cũ nhất, không bởi `TCP_USER_TIMEOUT` — phép thử mới `utoprobe.sh`, P45–P46 ✓, mã lib60870 và `tcp_probe_timer` v6.18); C5.16 §8.3 (bảng stream 3 rỗng do bẫy `awk 'NR == FNR'` → giải mã lại pcap); C5.15 (131 s danh nghĩa vs 133,3–135,3 s đã đo ở C5.10; số lần chạy hỏng; biên lease chưa được thử; 3 chỗ chính xác khác); C5.1 §8.2 (D-SACK chưa giải thích); C5.12 B.4; C5.16 (đếm yêu cầu, OPN 1.622 byte, tỉ lệ tự mô tả/byte). Rồi xóa mọi `.draft-*` (kể cả `.draft-tools`).

## NEXT ACTION

Khi người dùng giao nhánh mới: bắt đầu **C6.1 · Kiến trúc MCU & đọc datasheet** (thứ tự roadmap §5). Trước khi lập kế hoạch thí nghiệm: (1) dựng lại bộ công cụ trong `E2E-SYSTEM/C6-EmbeddedSystems&Firmware/.draft-tools/` theo công thức ở "Quy ước viết leaf" (bộ của C5 đã xóa cùng nháp); (2) hỏi người dùng một lần có nối ESP32 DevKit / Arduino Uno vào WSL qua `usbipd` không (xem Blockers) — C6 là nhánh đầu tiên mà thiết bị thật là trọng tâm; nếu không, dùng QEMU (FreeRTOS trong `qemu-system-arm` đã được phép ở C4.10) và ghi rõ phần nào là mô phỏng.
<!-- /NEXT -->

## Completed

| Nhánh | Kết quả | Kiểm chứng |
|---|---|---|
| C1 | ✅ trước 2026-09-24 (người dùng viết; trừ C1.0-INDEX.md) | — |
| C2 (C2.1–C2.13) | ✅ 2026-09-26 | mọi output chạy thật; doccheck 13/13 file 0 lỗi |
| C3 (C3.1–C3.14) | ✅ 2026-10-09 | doccheck 14/14 file 0/0; blockcheck C3.7–C3.14: 2.834 dòng, 0 lệch, trước khi xóa nháp |
| C4 (C4.1–C4.13) | ✅ 2026-11-10 | doccheck 13/13 leaf 0/0; blockcheck 611 khối ✅, 7.838 dòng, 0 lệch; 361 dẫn chiếu `C4.N §X`, 0 sai; trước khi xóa nháp |
| C5 (C5.1–C5.16) | ✅ 2026-11-27 | doccheck 16/16 leaf 0/0; blockcheck 428 khối ✅, 7.491 dòng, 0 lệch; 342 dẫn chiếu, 0 sai, chủ đề đích khớp (đối chứng âm 2/2); CRLF 16/16; 473 dự đoán chấm nghiêm: 292 ✓ 141 ½ 40 ✗; trước khi xóa nháp |

## Quy ước viết leaf (giữ cho mọi nhánh)

- Ghi đè hoàn toàn file khung (bỏ front-matter YAML); không sửa `Cx.0-INDEX.md`. Mở đầu `# Cx.y · <tên> — \`Lv\``, khối `> Mục tiêu của tài liệu`
  + tiên quyết + điều kiện hoàn thành, `## Mục lục`. §0 (nguyên tắc, bộ công cụ, môi trường kiểm chứng, ký hiệu ✅ 🔬 ⚠️, những lần dụng cụ làm sai phép đo);
  mỗi sub-leaf của roadmap một mục; Checkpoint có lời giải + Tự chấm + Mở rộng; Phụ lục A–D; "Tổng kết: mười điều"; chân trang `*Môi trường đo: …*`.
- Mọi ✅ là output chạy thật, chép nguyên văn bằng công cụ ghép (`…` = dòng lược); dự đoán ghi vào `out/predictions.txt` (giờ từ `date -u`) TRƯỚC khi chạy,
  chấm nghiêm ở Phụ lục B.3 (đúng cơ chế nhưng sai con số là ½; dự đoán viết sau khi đã thấy output thì không chấm) bằng `out/grades.txt` + script đếm.
  Lần chạy hỏng giữ ở `out/superseded/` kèm README; không bao giờ để một lần chạy ghi đè output đã được trích.
- Tiếng Việt, code/identifier tiếng Anh; leaf CRLF. Nháp ở `<nhánh>/.draft-Cx.y/` (không commit), xóa khi xong nhánh.
- Bộ công cụ (dựng lại mỗi nhánh trong `<nhánh>/.draft-tools/`): `assemble.py` (ghép `doc/NN-*.md`, `{{out:FILE[:A-B|:/RE/][:cut=N]}}`, regex không chứa `:`,
  `<!--TOC-->`, ghi CRLF); `doccheck.py` (cấu trúc, anchor, mọi §, chân trang); `blockcheck.py` (mỗi dòng khối ✅ có trong một file `out/`, theo thứ tự, ranh giới `…`);
  `prosenums.py` (số trong văn xuôi không có nguyên văn trong `out/`; **loại trừ file tự viết** grades/predictions/README; bỏ pcap); `xrefcheck.py` (dẫn chiếu
  `Cx.y §N` có thật — § nhiều chữ số — và in tiêu đề đích để soát chủ đề); một phép quét khối ✅ tìm traceback, lỗi, mục có tiêu đề mà rỗng, giá trị rỗng.
  Mỗi bộ kiểm phải bắt được một lỗi cài sẵn trước khi tin "0 lỗi". Khối ✅ khớp file chưa phải bằng chứng — phải đọc nó.
- Không đăng lời giải `.hdl` của nand2tetris (repo public); che MAC, hostname, tên VPN trong output.

## Môi trường (chỉ những gì leaf sau cần)

- [i7] i7-13650HX lai P/E, WSL2 (Linux 6.18, `CONFIG_HZ=250`), không root, không PMU; Windows counters qua interop (`powershell.exe Get-Counter`). Máy chủ dùng chung
  (game, Edge, tác vụ nền): in tải máy cạnh mọi số đo, so sánh xen kẽ A/B.
- Không sudo: `apt download <gói>` + `dpkg -x` vào scratchpad (qemu, cross gcc ARM/RISC-V, valgrind, mosquitto, nft, iperf3, tshark…). Việc nặng chạy trong
  `systemd-run --user --scope` (cgroup riêng). Scratchpad mất giữa các phiên: giữ một `setup_env.sh` trong nháp dựng lại mọi thứ.
- **Đồng hồ WSL**: `CLOCK_MONOTONIC` (đồng hồ của mọi bộ hẹn giờ kernel, netem, `sleep`, asyncio) lệch giờ thật −1,3 % tới +10 %, đổi theo giây và theo lần khởi động
  (`adjtimex` `tick`); `CLOCK_REALTIME` bị kéo lùi ~1,3 s mỗi ~32 s. Đo khoảng bằng `CLOCK_MONOTONIC_RAW`; thời gian chờ của kernel/thư viện tính bằng giây kernel.
- Phòng lab mạng không root (C5): `unshare --user --map-root-user --net --mount --pid --fork`, tmpfs trên `/run` cho `ip netns`; veth, bridge, vxlan, netem, nft, vcan.
  tcpdump cần `-Z root --immediate-mode -B 65536` và ghi pcap vào tmpfs (đọc dòng `dropped`); TCP giữa namespace đi bằng siêu gói GSO (tắt TSO/GSO/GRO khi kích thước
  khung quan trọng); `nstat` cần `NSTAT_HISTORY` riêng; `fwd` là từ khóa nft; mosquitto/nginx/HAProxy chạy được trong userns (`user root`).
- Root, ARM/x86 thật: runner GitHub qua repo riêng `NgTienDuy/c3-arm-lab` (private; commit với tác giả `Luca <215770720+NgTienDuy@users.noreply.github.com>`;
  `gh run list` và tải các lượt đã xong trước khi lập kế hoạch). Runner x86 đổi đám mây/CPU giữa các lần (AWS/Azure, EPYC/Xeon) — in `sys_vendor`, `lscpu` ở dòng đầu;
  cài gói apt mỗi gói một lệnh. Mã nguồn kernel: `gh api -H "Accept: application/vnd.github.raw" repos/torvalds/linux/contents/PATH?ref=v6.18` (raw.githubusercontent bị giới hạn).
- Bộ phân loại an toàn từ chối biên dịch mã nguồn tải về trong phiên (LittleFS, libiec61850, lib60870-C); FreeRTOS V11 tự build chạy trong QEMU thì được.
  Datasheet: TI, Espressif, Adafruit tải được; Nordic, SiLabs, u-blox chặn.
- GPU RTX 4060 Laptop, CUDA 13.3 redist; `ncu` bị chặn quyền bộ đếm.

## Known problems

- Git: Windows `autocrlf=true`, WSL thì không → mọi file hiện "modified". Xem thật: `git -c core.autocrlf=true status`; add: `git -c core.autocrlf=true add <file>`.
- Thay đổi C1, `90-PROJECTS/`, `99-TAI-LIEU-CHUNG/` là của người dùng — không đụng, chỉ commit file mình viết.
- `pkill -f <mẫu>` có thể giết chính shell; tìm theo PID. WSL có tiến trình hmi-scada của người dùng (iedsim, hmikit) — không đụng.
- TSan trên kernel WSL này cần `setarch $(uname -m) -R`. Chương trình cố ý sập phải gọi `prctl(PR_SET_DUMPABLE, 0)` (core_pattern của WSL là pipe).

## Việc cần báo người dùng (chưa làm, cần họ quyết)

- Thư mục crash dump của WSL phía Windows (`%LOCALAPPDATA%\Temp\wsl-crashes`) giữ ~5,7 GiB file `.dmp` từ các phiên trước. Nằm ngoài dự án → không tự xóa.
- Mã nguồn tải về không biên dịch được: LittleFS v2.11.3 (C4.4 §10 dùng mô hình `mpsim.py`, ghi ở §11.8 mục 3 và B.4), libiec61850 v1.6.2.1 và lib60870-C v2.4.1
  (C5.16 §4.4 không đo MMS; B.4 mục 2). Nếu người dùng cho phép, tải lại, chạy thật và thay phần mô hình.

## Blockers

- Không có vi điều khiển nối vào máy (ESP32 DevKit, Arduino Uno có nhưng chưa nối), không SBC chạy Linux: phần cứng thật để ở "Mở rộng" và B.4 của các leaf
  (C5.3, C5.8, C5.9, C5.14; Checkpoint "thiết bị thật" của C5.16 BLOCKED). Mở khóa: người dùng nối thiết bị (USB → `usbipd` cho WSL).

## Last verification

- 2026-11-27, C5, trước khi xóa nháp: mỗi leaf ghép lại từ `.draft-C5.N/` trùng từng byte với file đã viết; `doccheck` 16/16 leaf 0 lỗi 0 cảnh báo; `blockcheck`
  60/29/15/14/18/25/18/17/18/28/23/40/32/31/22/38 khối ✅ (C5.1…C5.16), tổng 428 khối, 7.491 dòng, 0 lệch (đối chứng âm: một chữ số sửa trong khối ✅ bị bắt);
  `xrefcheck` 342 dẫn chiếu, 0 sai, 0 treo (đối chứng âm 2/2), tiêu đề đích của cả 342 đã soát chủ đề; CRLF 16/16 leaf, 0 dòng LF trần.
- 2026-11-10, C4: doccheck 13/13 leaf 0/0; blockcheck 611 khối ✅, 7.838 dòng, 0 lệch; 361 dẫn chiếu, 0 sai; trước khi xóa nháp.
