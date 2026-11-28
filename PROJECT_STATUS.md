# Project Status — Huong-Dan / E2E-SYSTEM

**State:** C1–C5 hoàn tất. C6 · Embedded Systems & Firmware đang làm: **C6.1, C6.2 xong (2026-11-28)**; C6.3–C6.16 còn là file khung.
**Updated:** 2026-11-28 (phiên 18)
**Last session:** claude-code (Opus 5.5), 2026-11-28 (phiên 18): viết **C6.2 · GPIO, timer, PWM, ngắt** (222 KB, 53 dự đoán: ✓27 ½17 ✗7, 2 không chấm). Nền tảng: simavr ATmega328P với harness mới (kích thích chân, log sườn/vector, SP), logic analyzer mô phỏng `la.py` → sigrok `pwm`, ngspice 42 (mới thêm vào debs). Phát hiện: 14 chỗ simavr 1.6 khác datasheet (vào ngắt 0 chu kỳ, 2 lệnh sau SEI/RETI, mode 14 bỏ qua ghi OCR1A, phase-correct không chạy, ghi 1 vào EIFR đặt cờ…); Uno R3 chạy ATmega328P bằng bộ cộng hưởng gốm CSTCE16M0V53-R0 (±0,5 %+0,3 %+0,2 %) nên PWM không đạt 0,1 % nếu không hiệu chuẩn.

## NEXT ACTION

Bắt đầu **C6.3 · Bus & giao tiếp ngoại vi** (roadmap §5; checkpoint: debug một bus I²C "câm" bằng logic analyzer, ba nguyên nhân: sai địa chỉ, thiếu điện trở kéo lên, clock stretching không được hỗ trợ). Hướng: simavr ATmega328P có TWI/SPI/UART (kiểm trước mô hình của simavr: `avr_twi.c`, `avr_spi.c`, `avr_uart.c` — C6.2 tìm 14 chỗ simavr khác datasheet, đọc mã trước khi dự đoán); thiết bị I²C/SPI phía kia viết trong harness (C6.2 harness: `-s` kích thích, `-w` log sườn, `-I` vector, `-S` SP); "logic analyzer" = `la.py` (16/24 MS/s, ppm) → `sigrok-cli` với bộ giải mã `i2c`, `spi`, `uart` (có sẵn trong libsigrokdecode); điện của I²C (kéo lên, thời gian lên) bằng ngspice (đã có trong `.draft-tools/debs`). Đọc trước C3.11 §7 (UART/SPI/I²C tầng vật lý, đã đo thời gian lên I²C) để không lặp. Công cụ: `source .draft-tools/setup_env.sh`; chép `src/{rec.sh,dsq.sh,srcq.sh,gradecount.py,la.py,edges.py}` và `src/avr/{harness.c,build.sh,run.sh,uart.h,gen_stim.py}` từ `.draft-C6.2/`.
<!-- /NEXT -->

## Completed

| Nhánh | Kết quả | Kiểm chứng |
|---|---|---|
| C1 | ✅ trước 2026-09-24 (người dùng viết; trừ C1.0-INDEX.md) | — |
| C2 (C2.1–C2.13) | ✅ 2026-09-26 | mọi output chạy thật; doccheck 13/13 file 0 lỗi |
| C3 (C3.1–C3.14) | ✅ 2026-10-09 | doccheck 14/14 file 0/0; blockcheck C3.7–C3.14: 2.834 dòng, 0 lệch, trước khi xóa nháp |
| C4 (C4.1–C4.13) | ✅ 2026-11-10 | doccheck 13/13 leaf 0/0; blockcheck 611 khối ✅, 7.838 dòng, 0 lệch; 361 dẫn chiếu `C4.N §X`, 0 sai; trước khi xóa nháp |
| C5 (C5.1–C5.16) | ✅ 2026-11-27 | doccheck 16/16 leaf 0/0; blockcheck 428 khối ✅, 7.491 dòng, 0 lệch; 342 dẫn chiếu, 0 sai, chủ đề đích khớp (đối chứng âm 2/2); CRLF 16/16; 473 dự đoán chấm nghiêm: 292 ✓ 141 ½ 40 ✗; trước khi xóa nháp |
| C6.1 | ✅ 2026-11-28 | doccheck 0/0; blockcheck 83 khối ✅, 1.330 dòng, 0 lệch (đối chứng âm bắt được); xrefcheck 31 dẫn chiếu, 0 sai; errscan 12 điểm, đều là nội dung hợp lệ |
| C6.2 | ✅ 2026-11-28 | doccheck 0/0; blockcheck 69 khối ✅, 999 dòng, 0 lệch (đối chứng âm bắt được); xrefcheck 33 dẫn chiếu, 0 sai, chủ đề khớp; errscan 17 điểm, đều là nội dung hợp lệ (đối chứng âm 17→18); prosenums 35 số suy ra, đã soát; CRLF |

## Quy ước viết leaf (giữ cho mọi nhánh)

- Ghi đè hoàn toàn file khung (bỏ front-matter YAML); không sửa `Cx.0-INDEX.md`. Mở đầu `# Cx.y · <tên> — \`Lv\``, khối `> Mục tiêu của tài liệu`
  + tiên quyết + điều kiện hoàn thành, `## Mục lục`. §0 (nguyên tắc, bộ công cụ, môi trường kiểm chứng, ký hiệu ✅ 🔬 ⚠️, những lần dụng cụ làm sai phép đo);
  mỗi sub-leaf của roadmap một mục; Checkpoint có lời giải + Tự chấm + Mở rộng; Phụ lục A–D; "Tổng kết: mười điều"; chân trang `*Môi trường đo: …*`.
- Mọi ✅ là output chạy thật, chép nguyên văn bằng công cụ ghép (`…` = dòng lược); dự đoán ghi vào `out/predictions.txt` (giờ từ `date -u`) TRƯỚC khi chạy,
  chấm nghiêm ở Phụ lục B.3 (đúng cơ chế nhưng sai con số là ½; dự đoán viết sau khi đã thấy output thì không chấm) bằng `out/grades.txt` + script đếm.
  Lần chạy hỏng giữ ở `out/superseded/` kèm README; không bao giờ để một lần chạy ghi đè output đã được trích.
- Tiếng Việt, code/identifier tiếng Anh; leaf CRLF. Nháp ở `<nhánh>/.draft-Cx.y/` (không commit), xóa khi xong nhánh.
- C6: `assemble.py` tự chèn `…` khi regex chọn các dòng không liền nhau; trích datasheet bằng `src/dsq.sh` (đầu đề ghi dòng + trang PDF) vào `out/ds_quotes/`, mã nguồn trình mô phỏng vào `out/src_quotes/`; `errscan.py` (traceback, `key=` rỗng, tiêu đề không nội dung) có đối chứng âm.
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

- **C6 (2026-11-28):** `.draft-tools/debs/` chứa mọi `.deb` (gcc-arm-none-eabi 13.2.1, qemu-system-arm 8.2.2, gdb-multiarch 15.1, gcc-avr 7.3.0, avr-libc 2.0.0, simavr/libsimavr 1.6, sigrok-cli 0.7.2, poppler 24.02.0 + thư viện phụ); `setup_env.sh` giải nén vào scratchpad. Tài liệu hãng trong `.draft-tools/docs/` (+ `txt/` = pdftotext): TI SPMS144I, SPMZ860, SPMZ092, SPMZ637, TM4C123+SPMZ849; Microchip DS40002061B (errata DS80000855C chỉ lấy được từ onlinedocs.microchip.com, `docs/mcerr/`; www.microchip.com trả Access Denied); Espressif ESP32 DS v5.3, TRM v5.9, errata v3.1, WROOM-32E v2.1. **ST chặn tải tự động — không vượt rào** (bộ phân loại an toàn từ chối đổi User-Agent). `pdftotext` mất dấu trừ trong PDF của Espressif (font CID Adobe-GB1) → kiểm số âm bằng pdfminer.six (venv scratchpad).
- **simavr 1.6 trong C6.2** (bảng §0.5 của leaf): vào ngắt 0 chu kỳ (DS 4); 2 lệnh sau SEI/RETI (DS 1); không bộ đồng bộ PIN; pull-up nội đè driver ngoài mỗi lần ghi PORT/DDR (→ không bật pull-up nội trong bài, kích thích tự giữ mức nghỉ = dòng `1 1`); sự kiện timer/capture ở cuối lệnh đang chạy (hạt 0–3 chu kỳ); mode 8/9/14/15 = loại `pwm`, ghi OCR bị bỏ qua; mode 1–3/10/11 không có; OCR=TOP → mức thấp; mode 5–7 không đệm kép + so giá trị cũ sau byte cao; không ICNC1; ghi 1 vào EIFR/PCIFR đặt cờ. ngspice: spinit cần sửa đường dẫn code model (setup_env.sh làm).
- **QEMU lm3s6965evb**: `ignore_memory_transaction_failures` (lỗi bus bị nuốt → dùng `mps2-an385` làm đối chứng), 8 bit ưu tiên (chip 3), RCC = 200/(SYSDIV+1), không gate RCGCn, CCR.STKALIGN bật sẵn (chip: 0), CPUID r0p1 (chip r1p1), GPIOLOCK so với 0x0ACCE551; 64 IRQ (chip 38). `-icount shift=3` = 8 ns/lệnh; SysTick đếm SYSCLK của model → đo được tần số firmware cấu hình. **simavr 1.6**: không CLKPR, không FOC, PRR không dừng timer, OC1A bị xóa mỗi lần tràn ở Normal mode, điện áp analog là mV nguyên (ngưỡng 1,1 V thành 1099,5 mV); SRAM giữ qua reset; WDRF→WDE đúng.

## Known problems

- Git: Windows `autocrlf=true`, WSL thì không → mọi file hiện "modified". Xem thật: `git -c core.autocrlf=true status`; add: `git -c core.autocrlf=true add <file>`.
- Thay đổi C1, `90-PROJECTS/`, `99-TAI-LIEU-CHUNG/` là của người dùng — không đụng, chỉ commit file mình viết.
- `pkill -f <mẫu>` có thể giết chính shell; tìm theo PID. WSL có tiến trình hmi-scada của người dùng (iedsim, hmikit) — không đụng.
- TSan trên kernel WSL này cần `setarch $(uname -m) -R`. Chương trình cố ý sập phải gọi `prctl(PR_SET_DUMPABLE, 0)` (core_pattern của WSL là pipe).

## Việc cần báo người dùng (chưa làm, cần họ quyết)

- Thư mục crash dump của WSL phía Windows (`%LOCALAPPDATA%\Temp\wsl-crashes`) giữ ~5,7 GiB file `.dmp` từ các phiên trước. Nằm ngoài dự án → không tự xóa.
- Mã nguồn tải về không biên dịch được: LittleFS v2.11.3 (C4.4 §10 dùng mô hình `mpsim.py`, ghi ở §11.8 mục 3 và B.4), libiec61850 v1.6.2.1 và lib60870-C v2.4.1
  (C5.16 §4.4 không đo MMS; B.4 mục 2). Nếu người dùng cho phép, tải lại, chạy thật và thay phần mô hình.

- QEMU `hw/gpio/pl061.c` so khóa GPIOLOCK với `0xacce551` (datasheet TI: 0x1ACC.E551), vẫn còn ở master ngày 2026-11-28 — có thể báo cho dự án QEMU; chưa gửi (hành động ra ngoài cần người dùng quyết). Bằng chứng: `C6.1` §10.2.

## Blockers

- Không có vi điều khiển nối vào máy (ESP32 DevKit, Arduino Uno có nhưng chưa nối), không SBC chạy Linux: phần cứng thật để ở "Mở rộng" và B.4 của các leaf
  (C5.3, C5.8, C5.9, C5.14; Checkpoint "thiết bị thật" của C5.16 BLOCKED). Mở khóa: người dùng nối thiết bị (USB → `usbipd` cho WSL).

## Last verification

- 2026-11-27, C5, trước khi xóa nháp: mỗi leaf ghép lại từ `.draft-C5.N/` trùng từng byte với file đã viết; `doccheck` 16/16 leaf 0 lỗi 0 cảnh báo; `blockcheck`
  60/29/15/14/18/25/18/17/18/28/23/40/32/31/22/38 khối ✅ (C5.1…C5.16), tổng 428 khối, 7.491 dòng, 0 lệch (đối chứng âm: một chữ số sửa trong khối ✅ bị bắt);
  `xrefcheck` 342 dẫn chiếu, 0 sai, 0 treo (đối chứng âm 2/2), tiêu đề đích của cả 342 đã soát chủ đề; CRLF 16/16 leaf, 0 dòng LF trần.
- 2026-11-10, C4: doccheck 13/13 leaf 0/0; blockcheck 611 khối ✅, 7.838 dòng, 0 lệch; 361 dẫn chiếu, 0 sai; trước khi xóa nháp.
