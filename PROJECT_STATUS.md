# Project Status — Huong-Dan / E2E-SYSTEM

**State:** C1–C4 hoàn tất. C5 (Networking) đang làm: C5.1–C5.13 xong (C5.13 viết + commit 2026-11-24, phiên 13); C5.14–C5.16 chưa viết.
**Updated:** 2026-11-24
**Last session:** claude-code (Opus 5.5), 2026-11-24 (phiên 13, dừng ~18:45 UTC vì hết lượt dùng; Checkpoint C5.14 vẫn chạy nền): kiểm toán nháp C5.13 của phiên 12 (thí nghiệm lab có, run49 đã chạy nhưng Istio hỏng vì hub gcr.io không có 1.31.3, và phần xóa pod 'có delay' chưa từng có delay), chạy run49b/c/d trên runner (x86 rơi vào AWS ở run49b), thêm overlay/VPN/egress, viết và commit C5.13 (196 KB). Phát hiện: HAProxy redispatch ngay lần thử đầu (stream.h) và chu kỳ kiểm tra = chờ + nghỉ (DOWN +5,72 s); kube-proxy minSyncPeriod 1 s → cửa sổ lỗi khi xóa pod 0,1 hoặc 1,2 s (0–7 lỗi không delay, 0 có delay); topology spread + taint control-plane = rollout kẹt; router Linux không dùng PMTU đã học khi chuyển tiếp (ip_forward_use_pmtu) → underlay hẹp = mọi gói phân mảnh; NAT gateway tính phí cả chiều vào. 67 dự đoán 47 ✓ 13 ½ 7 ✗.

## NEXT ACTION

C5.14 (phiên 13, 2026-11-24) ĐANG LÀM. Checkpoint 6 giờ thật đang chạy nền: khởi chạy 17:44:46 UTC, mất mạng từ 17:54:47 tới ~00:00 UTC ngày 25, xả
hàng đợi xong ~00:45 UTC; kết quả tự chép vào `.draft-C5.14/out/ckpt-good/`, `ckpt-naive/` (verify.txt, load.csv, events.txt, server.db, status.log).
Nếu các tiến trình đã chết (WSL khởi động lại): chạy lại theo `out/ckpt_launch.txt`. Đã xong: thí nghiệm §1–§7 (`out/nat.txt`, `outbound-*.txt`,
`reconnect-*.txt`, `queue_*.txt`, `gaps-qos*.txt`, `detect*.txt`, `multipath.txt`, `clockref.txt`), dự đoán P1–P33 (P10–P33 chấm trong
`out/grades_partial.txt`), tài liệu `doc/00b-sec0.md`, `01-nat.md`…`07-multipath.md`. Còn lại sau Checkpoint: chạy `src/energy/energy.py out/ckpt-good
out/ckpt-naive > out/energy.txt` (§8), viết `08-energy.md`, `09-checkpoint.md` (verify.txt cả hai nhóm, chấm P1–P9), `00-head.md` (mục tiêu + phát hiện),
`11-appendix.md`, gộp grades → `out/grades.txt`, ghép bằng assemble.py, chạy các bộ kiểm, đọc lại, commit. Trong lúc chờ: bắt đầu C5.15 trong
`.draft-C5.15/` (Checkpoint của roadmap: retry storm → sụp đổ → jitter + circuit breaker, chứng minh bằng đồ thị). Sau đó C5.16, rồi rà soát cả nhánh C5.
C5.15 (phiên 13, dừng vì hết lượt dùng): `.draft-C5.15/` có lab + `src/ckpt/{srv,load,ckpt.sh,graph}.py` (retry storm: 150 yêu cầu/s, máy chủ ~200/s, đóng băng 3 s ở t=22 s) và dự đoán P1–P5 trong `out/predictions.txt` — CHƯA CHẠY lần nào (chạy: `bash src/lab/inlab.sh src/ckpt/ckpt.sh out naive400 naive 400`, `naive100 naive 100`, `good400 good 400`, `deadline400 naive 400 deadline`; tránh chạy nặng lúc Checkpoint C5.14 đang xả hàng đợi). Kế hoạch các mục khác của C5.15 (chưa viết): phân vùng một chiều + idempotency, lỗi xám (HAProxy observe layer7), đàn bò (hẹn giờ đồng bộ vs lệch theo băm), DNS chết khi kết nối cũ còn sống (dnsmasq), DROP vs REJECT, rò rỉ fd (CLOSE_WAIT, ulimit), cạn cổng tạm (port range hẹp, TIME_WAIT, tw_reuse), đồng hồ lệch hỏng TLS (`openssl s_client -attime`). Nợ cho C5.15: C5.7 §1.3 thử lại 503; C5.9 §3 đồng hồ lệch làm hỏng TLS; C5.11 §6.4/§8.2 đàn bò giẫm đạp/bão bắt tay. Rà soát nhánh: C5.12 B.4
(ACK đảo thứ tự trong lab veth có làm sai các leaf trước không); C5.13 B.4 (kube-proxy trễ 1 s: kiểm bằng log -v=4). Môi trường phiên này:
`SP=scratchpad`, `C5T=$SP/c5t TMPDIR=$SP PYQ=$SP/venv/bin/python` (venv: paho-mqtt 2.1.0, aioquic 1.7.2). WSL lần khởi động này: CLOCK_MONOTONIC
nhanh 8,34 % so với Windows (`out/clockref.txt` của C5.14) — mọi lịch trình dài phải lặp trên CLOCK_MONOTONIC_RAW.
<!-- /NEXT -->

## Completed

| Nhánh | Kết quả | Kiểm chứng |
|---|---|---|
| C1 | ✅ trước 2026-09-24 (người dùng viết; trừ C1.0-INDEX.md) | — |
| C2 (C2.1–C2.13) | ✅ 2026-09-26 | mọi output chạy thật; doccheck 13/13 file 0 lỗi |
| C3 (C3.1–C3.14) | ✅ 2026-10-09 | doccheck 14/14 file 0/0; blockcheck C3.7–C3.14: 2.834 dòng, 0 lệch, trước khi xóa nháp |
| C5.1 | ✅ 2026-11-12 | doccheck 0/0; blockcheck 60 khối ✅, 842 dòng, 0 lệch; xrefcheck 6/0; CRLF; nháp `.draft-C5.1/` giữ lại tới khi rà soát nhánh |
| C5.4 | ✅ 2026-11-12 | doccheck 0/0; blockcheck 14 khối ✅, 388 dòng, 0 lệch; xrefcheck 17/0; CRLF; 21 dự đoán 12 ✓ 6 ½ 3 ✗; nhà máy 4 router trong netns, nftables NAT, BIRD OSPF/BGP, radvd; câu hỏi mở: BIRD giữ route qua giao diện đã xóa (3/3 vs 0/4) |
| C5.5 | ✅ 2026-11-12 | doccheck 0/0; blockcheck 18 khối ✅, 217 dòng, 0 lệch; xrefcheck 17/0; CRLF; 12 dự đoán 7 ✓ 5 ½ 0 ✗; Checkpoint mù 4/4 ×3 lần xáo (thêm đối chứng khỏe); BBR trên runner; câu hỏi mở: phần dư 4,3 % của QUIC-1, đuôi độ trễ aioquic |
| C5.13 | ✅ 2026-11-24 | doccheck 0/0; blockcheck 32 khối ✅, 764 dòng, 0 lệch; xrefcheck 25/0 (đối chứng âm 2/2); prosenums 13/440 (phiên bản, năm, số suy ra ghi cạnh); CRLF 2067 dòng; 67 dự đoán 47 ✓ 13 ½ 7 ✗; runner run49/49b/49c/49d (Azure x86+arm, AWS x86): kind v0.33.0 + Istio 1.31.3; mã nguồn Linux v6.18, HAProxy 2.8.30, Kubernetes v1.37.0, agnhost trong `out/src_quotes/`; giá AWS Price List API trong `data/` |
| C5.12 | ✅ 2026-11-23 | doccheck 0/0; blockcheck 40 khối ✅, 538 dòng, 0 lệch; xrefcheck 32/0 (đối chứng âm 2/2); prosenums 39/602 đã đọc (suy ra ghi cạnh, phiên bản, năm); CRLF 1277 dòng; 34 dự đoán 21 ✓ 7 ½ 6 ✗; viết 2026-11-19 (phiên 11), kiểm toán 2026-11-23: ACK đảo thứ tự + RACK, mô hình bánh xe hẹn giờ, phép thử ghim CPU; mã nguồn libpcap 1.10.4, Wireshark 4.2.2, Linux v6.18 (RACK, veth backlog, probe0), aioquic 1.7.2 trong `out/src_quotes/` |
| C5.11 | ✅ 2026-11-19 | doccheck 0/0; blockcheck 23 khối ✅, 338 dòng, 0 lệch; xrefcheck 40/0; prosenums 24/631 đã đọc (bảng hiệu suất tính, phép chia ghi cạnh, phiên bản, năm); CRLF 1093 dòng; 29 dự đoán 11 ✓ 16 ½ 2 ✗; mã nguồn Linux v6.18 (cwnd restart, sndbuf wakeup, frag memory, TLP), nginx 1.24.0 (cache manager, cache lock) trong `out/src_quotes/`; output cũ trong `out/superseded/` |
| C5.10 | ✅ 2026-11-19 | doccheck 0/0; blockcheck 28 khối ✅, 278 dòng, 0 lệch; xrefcheck 34/0; CRLF 976 dòng; 23 dự đoán 12 ✓ 8 ½ 3 ✗; viết 2026-11-15, kiểm toán + chạy lại Checkpoint/drops/shutdown/dsorder 2026-11-19; output cũ trong `out/superseded/`; mã nguồn Linux v6.18 (timer.c, tick-sched.c, dev.c, veth.c, task_mmu.c), glibc 2.39 (nhãn + độ ưu tiên), OpenSSL 3.0.13 trong `out/src_quotes/` |
| C5.9 | ✅ 2026-11-15 | doccheck 0/0; blockcheck 18 khối ✅, 361 dòng, 0 lệch; xrefcheck 12/0 (đối chứng âm 2/2); prosenums 55/402 đã đọc (phiên bản, RFC, năm, phép tính ghi cạnh); CRLF 922 dòng; 13 dự đoán 10 ✓ 3 ½ 0 ✗; mã nguồn mbedTLS 2.28.8, Linux v6.18 (delayed ACK), lwIP 2.1.3 (Nagle) trong `out/src_quotes/`; thiết bị Checkpoint là Python/paho + thư viện mbedTLS, không phải MCU thật |
| C5.8 | ✅ 2026-11-15 | doccheck 0/0; blockcheck 17 khối ✅, 275 dòng, 0 lệch; xrefcheck 19/0; prosenums 23/366 đã đọc; CRLF 906 dòng; 12 dự đoán 7 ✓ 5 ½ 0 ✗; mã nguồn mosquitto 2.0.18, paho 2.1.0, grpc 1.85.1 trong `out/src_quotes/`; năng lượng là mô hình (datasheet ESP32 v5.3) |
| C5.7 | ✅ 2026-11-15 | doccheck 0/0; blockcheck 18 khối ✅, 291 dòng, 0 lệch; xrefcheck 15/0; prosenums 85/442 đã đọc (mã trạng thái, RFC, năm, phép tính ghi cạnh); CRLF 946 dòng; 10 dự đoán 6 ✓ 4 ½ 0 ✗; mã nguồn nginx 1.24 (HPACK, khóa cache) và CPython (Nagle) trong `out/src_quotes/` |
| C5.6 | ✅ 2026-11-15 | doccheck 0/0; blockcheck 25 khối ✅, 477 dòng, 0 lệch; xrefcheck 11/0 (đối chứng âm 2/2); prosenums 35/400 đã đọc; CRLF 1280 dòng; 21 dự đoán 13 ✓ 8 ½ 0 ✗; Checkpoint mù 4/4 ×2 lần xáo; mã nguồn glibc 2.39 (nscd, res_send) và Unbound 1.19.2 trích trong `out/src_quotes/` |
| C5.3 | ✅ 2026-11-12 | doccheck 0/0; blockcheck 15 khối ✅, 248 dòng, 0 lệch; xrefcheck 7/0; CRLF; 13 dự đoán 6 ✓ 4 ½ 3 ✗; Wi-Fi/BLE thật của [i7-host] (chỉ đọc), mac80211_hwsim trên runner (run47), modem LoRa tự viết, datasheet ESP32/SX1276/CC2640R2F; nháp giữ lại |
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
- C5.4: nft, conntrack, bird2, radvd, mtr chạy được trong userns (cache .deb ở `.draft-tools/debs`). tcpdump -r trong userns cần `-Z root`. `fwd` là từ khóa nft. rp_filter của netns mới = 2 trên mọi giao diện; hiệu lực = max(all, iface). IGMP snooping của bridge chỉ tỉa khi có querier (đợi > 10 s).
- C5.5: netem đặt `delay` và `rate … limit` trên cùng giao diện thì gói trong hàng trễ bị tính vào limit — tách ra hai giao diện. tcp_bbr không tự nạp được trong userns (`capable()` ở tcp_ca_find_autoload) → BBR chạy trên runner với `sudo modprobe tcp_bbr`. Runner: user namespace con không đọc được checkout → `rootlab.sh` (unshare không --user). Lệnh nền không có stdin riêng nhận /dev/null (here-doc cho hàm chạy nền → ghi ra file). tshark 4.2 in boolean là True/False. aioquic 1.7.2 trong `$SP/venv`; luồng QUIC hai chiều chỉ trả hạn mức khi đóng cả hai chiều (dùng luồng một chiều).
- C5.3: đo radio của [i7-host] qua PowerShell (`src/wifi/run_wifi.sh`, `src/ble/run_ble.sh` trong `.draft-C5.3`): KHÔNG BAO GIỜ ngắt Wi-Fi (ngắt = ngắt phiên). BLE WinRT cần C# biên dịch bằng csc.exe của .NET Framework với tham chiếu `System.Runtime.InteropServices.WindowsRuntime.dll`. `netsh wlan show networks` đọc bộ đệm — gọi `WlanScan` trước. Runner có `mac80211_hwsim` sẵn (gói modules-extra cài lỗi nhưng không cần). numpy: venv trong scratchpad. pdftotext: `apt download poppler-utils libpoppler134 libopenjp2-7 liblcms2-2 libnss3 libnspr4`. Nordic/SiLabs/u-blox chặn tải datasheet; TI, Espressif, Adafruit (Semtech) thì được.
- C5.11: lab C—R1(netem trễ)—R2(htb + qdisc lá)—S trong `.draft-C5.11/src/topo/topo.sh`; kernel WSL có htb/tbf/codel/fq_codel/fq/sfq/red, không có cake/pie. nginx 1.24 chạy được với master process trong userns (`user root root`; initgroups lỗi nhưng không chết) — cần cho cache manager. Biến môi trường: không `export A=x B=$A` trên một dòng. `openssl s_time -reuse` cần `-www /` để TLS 1.3 nối lại. `mtr` in tên máy ở dòng HOST — che trước khi ghi. venv: `VENV=… bash .draft-C5.11/src/setup_py.sh` (paho-mqtt 2.1.0, zstandard, brotli). fsync trên ext4 của WSL ~4,6 ms p50.
- C5.9: PKI bằng Python `cryptography` 50.0.2 (44 xung đột với service-identity); mbedTLS 2.28.8 + valgrind 3.22 từ .deb (`VALGRIND_LIB=$C5T/usr/libexec/valgrind`); `openssl s_server` không nhận `-early_data` cùng `-www` và thoát khi stdin EOF (dùng `sleep N |`); mosquitto chỉ nạp lại CRL/khóa khi SIGHUP; Python/paho: TLS 1.3 báo từ chối chứng chỉ client ở lần đọc đầu, không ở `connect()`; giờ ảnh bắt gói theo đồng hồ thực WSL có thể nhảy lùi giữa phiên — chạy lại nếu thấy thời gian âm.
- C5.8: mosquitto 2.0.18 (.deb) trong userns cần `user root`; `log_type all` cho thấy mọi gói kèm `rc`; `set_tcp_nodelay` mặc định false, paho-mqtt không bao giờ đặt TCP_NODELAY. pdftotext: `apt download poppler-utils libpoppler134 libopenjp2-7 liblcms2-2 libnss3 libnspr4`. Datasheet ESP32 tải lại được từ espressif.com (sha256 a7917e6b…).
- C5.7: nginx 1.24 trong userns cần `master_process off; user root root;` (chown thư mục tạm cho `nobody` không ánh xạ) và chờ file pid của chính nó; nghttp2 1.59 (`nghttp`, `nghttpd`, `h2load`) từ .deb. Edge headless trên Windows đọc được máy chủ WSL qua `localhost` (WSL NAT, localhostForwarding): `msedge.exe --headless=new --user-data-dir=%TEMP%\\c57edge --dump-dom` — xóa hồ sơ sau khi chạy. aioquic ghi khóa TLS bằng `secrets_log_file` → tshark giải mã QUIC. Một gói TCP chính xác bị mất: máy chủ đặt IP_TOS trước một lần ghi nhỏ (TCP_NODELAY) rồi xóa; nft trên R bỏ `ip dscp cs1`.
- C5.6: BIND 9.18.39/Unbound 1.19.2/dnsmasq 2.91/nscd chạy trong userns (dnsmasq `--no-daemon`, nscd không `server-user`; socket điều khiển Unbound ở `/run`). `dig` 9.18 ghi khóa TLS ra stderr khi có `SSLKEYLOGFILE` → tshark giải mã DoT/DoH. **Đồng hồ WSL** (`.draft-C5.6/src/clockcheck.py`): CLOCK_MONOTONIC chạy nhanh 4,1 % so với MONOTONIC_RAW, CLOCK_REALTIME bị lùi ~1,3 s mỗi ~32 s → khoảng đo bằng `date` có thể ngắn đi 1,3 s; `sleep N` ngắn hơn N giây thực. venv zeroconf/dnspython: `python3 -m venv` + pip trong scratchpad (`PYQ=`).
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
- 2026-11-12, C5.3: `doccheck` 0/0; `blockcheck` 15 khối ✅ / 248 dòng / 0 lệch; `xrefcheck` 7/0; `prosenums` 57/451 đã đọc (năm, kênh, số hiệu chuẩn; hai chỗ sửa); CRLF 790 dòng.
- 2026-11-12, C5.4: `doccheck` 0/0; `blockcheck` 14 khối ✅ / 388 dòng / 0 lệch; `xrefcheck` 17/0; `prosenums` 36/384 (phiên bản, mặt nạ, hằng số chuẩn); CRLF 953 dòng.
- 2026-11-12, C5.5: `doccheck` 0/0; `blockcheck` 18 khối ✅ / 217 dòng / 0 lệch; `xrefcheck` 17/0; `prosenums` 52/542 (phiên bản, năm, phép tính có ghi mô hình); CRLF 1343 dòng.
- 2026-11-15, C5.6: `doccheck` 0/0; `blockcheck` 25 khối ✅ / 477 dòng / 0 lệch; `xrefcheck` 11/0 (đối chứng âm: `C5.4 §8.9`, `C5.5 §29` đều bị bắt); `prosenums` 35/400 đã đọc (phiên bản, IP, năm, phép trừ ghi cạnh); CRLF 1280 dòng.
- 2026-11-15, C5.7: `doccheck` 0/0; `blockcheck` 18 khối ✅ / 291 dòng / 0 lệch; `xrefcheck` 15/0; `prosenums` 85/442 đã đọc; CRLF 946 dòng.
- 2026-11-15, C5.8: `doccheck` 0/0; `blockcheck` 17 khối ✅ / 275 dòng / 0 lệch; `xrefcheck` 19/0; `prosenums` 23/366 đã đọc; CRLF 906 dòng.
- 2026-11-15, C5.9: `doccheck` 0/0; `blockcheck` 18 khối ✅ / 361 dòng / 0 lệch; `xrefcheck` 12/0 (đối chứng âm: `C5.8 §42`, `C5.7 §1.9` bị bắt, `C5.6 §2` qua); `prosenums` 55/402 đã đọc; CRLF 922 dòng.
- 2026-11-19, C5.10 (sau kiểm toán): `doccheck` 0/0; `blockcheck` 28 khối ✅ / 278 dòng / 0 lệch; `xrefcheck` 34/0; `prosenums` 35/576 đã đọc (khoảng mô hình, phép chia MiB, tổng ghi cạnh); CRLF 976 dòng.
- 2026-11-19, C5.11: `doccheck` 0/0; `blockcheck` 23 khối ✅ / 338 dòng / 0 lệch; `xrefcheck` 40/0; `prosenums` 24/631 đã đọc; CRLF 1093 dòng.
- 2026-11-23, C5.12 (sau kiểm toán): `doccheck` 0/0; `blockcheck` 40 khối ✅ / 538 dòng / 0 lệch; `xrefcheck` 32/0 (đối chứng âm `C5.11 §42`, `C5.10 §5.9` bị bắt); `prosenums` 39/602 đã đọc; CRLF 1277 dòng.
- 2026-11-24, C5.13: `doccheck` 0/0; `blockcheck` 32 khối ✅ / 764 dòng / 0 lệch; `xrefcheck` 25/0 (đối chứng âm `C5.4 §42`, `C5.6 §5.9` bị bắt); `prosenums` 13/440 đã đọc; CRLF 2067 dòng.
