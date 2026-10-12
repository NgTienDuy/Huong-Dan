# Project Status — Huong-Dan / E2E-SYSTEM

**State:** IN PROGRESS — nhánh C1, C2, C3 hoàn tất; đang viết nhánh C4 (C4.1 xong; C4.2–C4.13 chưa bắt đầu)
**Updated:** 2026-10-12
**Last session:** claude-code (Opus 5.5), 2026-10-12: bắt đầu C4 theo yêu cầu người dùng (viết C4.1 → C4.13 theo cách của C1, bám `roadmap.md`,
rà soát toàn nhánh sau C4.13; điều chắc chắn đúng không buộc phải thử trước). Dựng lại công cụ ở `C4-…/.draft-tools/`.

## NEXT ACTION

C4.1 ĐÃ VIẾT XONG (2026-10-12): `E2E-SYSTEM/C4-…/C4.1-Processes&Threads.md`, 229,7 KB, 2.476 dòng, ghép từ 13 file `.draft-C4.1/doc/NN-*.md`.
Kiểm trên file thật, không nối ống: `doccheck.py` 0 lỗi 0 cảnh báo (mã thoát 0); `blockcheck.py` 87 khối ✅, 831 dòng, 0 lệch (mã thoát 0); mọi dòng CRLF; không đường dẫn cục bộ.
CHƯA làm cho C4.1: đọc lại TOÀN BỘ văn bản đã ghép từ đầu tới cuối như một người đọc (mới rà từng mục với file output + quét nhất quán 12 họ con số) — để dành cho lượt rà soát
toàn nhánh sau C4.13, hoặc làm ngay nếu người dùng muốn. Leaf dài hơn leaf lớn nhất trước đó (C3.4, 215,8 KB) khoảng 14 KB.
ĐÃ SỬA sau khi đẩy lần đầu (f3aedde): §1.2 viết "không đọc được `prio` thô từ không gian người dùng, 120 chỉ là quy ước" — SAI; `/proc/PID/sched` in `prio` (120; 130 ở nice 10)
và `stat` in `prio` − 100. Đã thay bằng số đo + khối `out/proc_sched_prio.txt`. Phát hiện khi khảo sát C4.2.
KẾ TIẾP: C4.2 (Lập lịch). Đọc file khung `C4.2-Scheduling.md` và mục C4.2 của `roadmap.md` (9 sub-leaf; checkpoint: tái tạo đảo ngược ưu tiên với 3 luồng, đo độ trễ, sửa bằng
kế thừa ưu tiên). Cần SCHED_FIFO → runner (sudo). Dùng lại: `.draft-tools/` (assemble.py, doccheck.py, blockcheck.py, setup_env.sh), cách viết theo file mục + chỉ thị `{{out:…}}`,
các file `src/common.h`, `ctxsw.c`, `hog.c` của C4.1 (giữ `.draft-C4.1/` cho tới khi rà soát xong cả nhánh). Món nợ C4.1 để lại cho C4.2: lượt chạy ≈ 1 tick 4 ms (§4.8),
43% lần chuyển trên đường pipe là không tự nguyện (§4.3), khoản phạt CPU nghỉ (§4.6), `sched_yield` được đếm là không tự nguyện.
C4.2 — khảo sát [i7] đã làm (`C4-…/.draft-C4.2/out/survey_i7.txt`, chỉ đọc; CHƯA có thí nghiệm nào):
- KHÔNG đặt được SCHED_FIFO / RR / DEADLINE (EPERM; RLIMIT_RTPRIO = 0) → checkpoint (đảo ngược ưu tiên + mutex PI) và mọi thứ thời gian thực làm trên runner, gộp trong MỘT lần chạy
  cùng `lscpu`, mitigations, `sched/features`, chế độ preempt. Được phép cục bộ: SCHED_BATCH, SCHED_IDLE, `nice` dương; controller `cpu` đã ủy quyền cho user manager
  (cpu.weight / cpu.max trong scope riêng — CHƯA thử chạy thật); `/proc/PID/sched` đọc được.
- ⚠️ `nice -n -5 CMD` in "Permission denied" nhưng vẫn chạy CMD và trả mã thoát 0 → phải đọc lại nice thật, không tin mã thoát.
- Lớp fair: BTF của `struct sched_entity` trên [i7] có `deadline`, `vlag`, `slice`, `min_slice`, `rel_deadline`… (`.draft-C4.2/out/btf_sched_entity.txt`) → trạng thái của EEVDF, không phải
  CFS của sách; hành vi chọn tác vụ CHƯA kiểm (cần `sched/features` trên runner). `/proc/PID/sched` (`out/proc_self_sched.txt`, `proc_sched_prio.txt`): `se.slice` = 2.800.000 ns;
  `se.load.weight` 1.048.576 (nice 0), 112.640 (nice 10), 3.072 (SCHED_IDLE). CHƯA biết: chế độ preempt đang dùng (kernel dựng PREEMPT_DYNAMIC).
- Khách này KHÔNG có cpufreq, và cpuidle `current_driver` = none → sub-leaf "lập lịch và điện năng" không quan sát được từ trong máy ảo (chỉ còn RAPL phía Windows như C3.13).
  Cũng là dữ kiện mới cho câu còn mở ở C4.1 §4.6 (khoản phạt CPU nghỉ): khách không tự chọn trạng thái ngủ sâu → ghi nhận cho lượt rà soát nhánh, CHƯA đưa vào leaf.
Quy tắc làm việc rút từ C4.1 (áp dụng cho mọi leaf sau): (1) số trong văn xuôi phải rà với file — blockcheck không kiểm văn xuôi; mỗi mục của C4.1 có 2–8 chỗ sai kiểu này ở bản đầu;
(2) bảng tổng hợp do script sinh cũng phải đối chiếu với giá trị đã biết (hai script đã sai: gộp "unscoped" vào "scoped"; hoán đổi hai cột); (3) con số đếm ("ba lần", "bảy lệnh")
phải đếm bằng script; (4) nối build với chạy bằng `&&`, không nối ống ở lệnh làm cổng; (5) sửa file này bằng thay chuỗi chính xác trong khoảng tiêu đề … dấu `/NEXT`;
(6) trước khi viết thông điệp commit, grep nội dung đã stage; (7) thí nghiệm nặng chạy trong `systemd-run --user --scope`.

<!-- /NEXT : khi viết lại mục "việc kế tiếp" ở trên, chỉ thay đoạn từ tiêu đề của nó tới dấu này. Ngày 2026-10-12 một lần thay "tới tiêu đề kế" đã xóa mất
     DÀN Ý và mục run18 (chúng chưa từng được commit; thông điệp của commit 1a397d4 nói có là SAI). Hai mục dưới đây được KHÔI PHỤC CÓ BỔ SUNG (không phải nguyên văn):
     thêm file nào đã viết, cột objsize của slabinfo, và việc không runner nào đặt mitigations=. Trước khi viết thông điệp commit: grep nội dung đã stage. -->

DÀN Ý C4.1 ĐÃ CHỐT (viết từng file ở `.draft-C4.1/doc/NN-*.md`, ghép + sinh Mục lục + CRLF ở cuối; đã viết: `00-head.md`, `01-pcb.md`):
- §0 Cách dùng tài liệu: 0.1 nguyên tắc · 0.2 bộ công cụ · 0.3 môi trường ([i7], [N2], [EPYC]=7763 run17, [9V74]=run18)
- §1 Khối điều khiển tiến trình: 1.1 một tác vụ là gì (task_struct, BTF) · 1.2 đọc nó qua /proc (`pcb_proc`) · 1.3 cỡ thật trong slab (run18; x86 dư 2.576 B, ARM dư 0) ·
  1.4 mỗi cờ CLONE_* chia sẻ một thứ (`clone_share`, strace `thr_one`)
- §2 fork/exec/wait: 2.1 fork trả về hai lần (`fork_basic`) · 2.2 ⚠️ bộ đệm stdio bị nhân đôi (`fork_stdio`, bản lỗi `wait_status_run1_buggy`) · 2.3 exec giữ gì (`exec_inherit`) ·
  2.4 wait và mã trạng thái (`wait_status`, core_pattern) · 2.5 ⚠️ `1/z` không sinh SIGFPE (objdump) · 2.6 giá của fork theo cỡ bộ nhớ (`fork_cost` 4k/THP; cột "warm" sai nhãn;
  chỉ báo THP lấy mẫu sai lúc) · 2.7 fork trong tiến trình nhiều luồng (`fork_mt`)
- §3 Luồng: 3.1 luồng là tác vụ chung mm (`ids`) · 3.2 một luồng tốn gì (`thread_cost`) · 3.3 ⚠️ giới hạn thật là cgroup (9.391, pids.max; scope riêng) ·
  3.4 mô hình lai: Go nhìn từ /proc (`go_threads`) · 3.5 preempt bằng tín hiệu (`go_preempt2`; bản hỏng `go_preempt`)
- §4 Chi phí chuyển ngữ cảnh: 4.1 phải lưu gì (pt_regs, inactive_task_frame, FPU) · 4.2 ⚠️ thước đo: 19 GHz, và vì sao dùng ns · 4.3 cùng CPU trên ba máy + perf đếm lại ·
  4.4 tiến trình so với luồng · 4.5 tập làm việc: "chi phí gián tiếp" (`ctxsw_wset`) · 4.6 khác CPU, CPU nghỉ/bận · 4.7 ⚠️ trạng thái AVX (hai lượt vô hiệu, lượt thứ ba + đối chứng) ·
  4.8 chuyển không tự nguyện (`hog`)
- §5 Coroutine và luồng xanh: 5.1 chuyển bằng 15 lệnh asm, khung 7 giá trị (`switch.S`, `uctx`, strace swapcontext) [trước ghi nhầm "bảy lệnh" — đếm từ file] · 5.2 thư viện N:1 (`green order`) · 5.3 100.000 luồng xanh · 5.4 ⚠️ một syscall chặn làm
  chết tất cả (`green block/nonblock`) · 5.5 coroutine không stack (`proto`)
- §6 Cây tiến trình: 6.1 zombie (`zombie`) · 6.2 mồ côi và subreaper (`orphan`, chuỗi cha ở WSL, runner) · 6.3 SIGCHLD không đếm (`reap`) · 6.4 PID 1 không thu dọn (`init_noreap`) ·
  6.5 PID bị dùng lại và pidfd (`pid_reuse`)
- §7 Nhóm tiến trình, phiên, điều khiển tác vụ: 7.1 nhóm và phiên (`job_groups`, `ids`) · 7.2 ^C (`job_ctrl_c`) · 7.3 đọc terminal từ nền (`job_ttin`) · 7.4 ^Z, bg (`job_ctrl_z`) ·
  7.5 mất terminal (`job_hangup`) · 7.6 bốn nghĩa vụ của shell (`fgjob`)
- §8 Tín hiệu: 8.1 bitmap và hàng đợi (`sig_queue`) · 8.2 khung trên stack và giá một lần giao (`sig_frame`, `sig_frame_align`, 3 máy) · 8.3 EINTR, SA_RESTART (`sig_eintr`) ·
  8.4 ⚠️ handler không an toàn: 4 chế độ + gdb (và lần đầu gcc xóa malloc) · 8.5 errno (`sig_errno`) · 8.6 mất lần đánh thức (`sig_race`) · 8.7 luồng nào nhận (`sig_threads`) ·
  8.8 mask và ignore qua exec (`sig_mask`) · 8.9 stack riêng cho handler (`sig_altstack`)
- §9 Checkpoint: 9.1 yêu cầu · 9.2 benchmark · 9.3 con số · 9.4 phân rã · 9.5 Tự chấm · 9.6 Mở rộng (máy không ảo hóa; run19; Windows gốc)
- Phụ lục A bảng tra · B triệu chứng → nguyên nhân (gồm bảng "thí nghiệm bị tầng dưới làm lệch": hiệu chuẩn add $1; vzeroupper; 1/z; malloc bị xóa ×2 (handler, zombie);
  cột warm; chỉ báo THP; vòng Go có lời gọi; stdio nhân đôi — ĐẾM LẠI khi viết, đừng ghi con số trước) · C checklist · D đọc tiếp · Tổng kết mười điều · chân trang

Runner run18 (commit 4818af5 của `c3-arm-lab`, artifact `out/runner18/`) — CHÚ Ý máy x86 lần này là EPYC 9V74, KHÁC máy 7763 của run17:
- cùng một máy, cùng lần khởi động: x86 (9V74, AVX-512) `sizeof(task_struct)` 9.664 B (BTF) nhưng `object_size` slab 12.240 B → dư 2.576 B mỗi tác vụ; `thread_struct` 184 B,
  `struct fpu` 4.224 B không nằm trong đó. ARM (N2) `sizeof` 8.960 = `object_size` 8.960 → dư 0; `thread_struct` 1.680 B. "2.576 B là trạng thái FPU" RẤT CÓ KHẢ NĂNG
  nhưng CHƯA khép: dòng dmesg "context size" bị `head -8` của tôi cắt mất.
  Cột `objsize` của `/proc/slabinfo` = `slab_size` (12.288 ở 9V74), KHÔNG phải `object_size` (12.240) → số 10.688 của 7763 ở run17 là cỡ ô slab; đừng lấy nó trừ `sizeof`.
- N2 có `sve`, `sve2` trong Features (run17 chưa biết); cả hai runner là khách Hyper-V (dmesg).
- mitigation của 9V74 (KHÔNG phải của 7763): spectre_v2 và retbleed "Not affected"; SRSO "Safe RET, no microcode"; tsa, SSB "Vulnerable"; không runner nào có `mitigations=`
  trên dòng lệnh kernel. Vì vậy câu hỏi "7763 chậm 3–5× có phải do mitigation" VẪN CHƯA được thử: có trạng thái của máy không có số đo, và số đo của máy không có trạng thái.
  `cpu MHz` (3.654 ở 9V74; 2.803 ở laptop trong khi chuỗi hiệu chuẩn đọc 4,4–4,8 GHz) là số danh nghĩa — KHÔNG dùng để kiểm hiệu chuẩn.
- run19 (tùy chọn, CHƯA làm): trong MỘT script trên MỘT máy: `ctxsw sys|pipe1|pipe-thr` + vulnerabilities + `dmesg | grep -i "x86/fpu"` đầy đủ (không `head`) + BTF sizeof + slab.

Độ chắc của số liệu C4.1 (sau lượt lặp lại 2026-10-12) — SỬA các con số ghi ở dưới nếu mâu thuẫn:
- Chính xác/tất định: cờ clone; ma trận `clone_share`; thừa kế qua exec; mã trạng thái wait; SỐ lỗi trang (1/trang, 0, 1/trang); AnonHugePages 1024→0 qua lượt cow
  (3 lần); ánh xạ sp mod 64 → {976, 992, 1008, 1024} / khung 1440…1488 (2 lần, pha đổi theo ASLR, ánh xạ không đổi); che/bỏ qua qua exec; perf = getrusage ± 13;
  giới hạn luồng = `pids.max`.
- Lặp lại được, có dải: fork 1 GiB/4 KiB 5,0 / 5,5 / 5,6 ms; THP 0,17 / 0,27 / 0,20 ms; luồng: VmRSS 8,28–8,29 KiB, KernelStack 15,96–15,99 KiB (N = 2.000 và 9.391);
  luồng xanh 19,1–20,5 ns (6 lần), 4,03 KiB; `gt_switch` 7,2–7,4 ns; `swapcontext` 134–140 ns; lượt chạy 3,92–3,99 ms; bảng cùng CPU trên 3 máy; chiều nghỉ > bận 4/4 × 3 máy.
- Mềm / phụ thuộc điều kiện: mất đánh thức tự nhiên 5, 14, 16, 23 trên 200.000 (4 lần; KHÔNG phải "1/9.000–14.000"); nới 20 µs: 23% và 36% (2 lần);
  `sigsuspend` 0/804.000; slab mỗi luồng 8,6–11,4 KiB (tổng thường trú ~33–36 KiB); ảnh hưởng cỡ stack lên thời gian tạo CHƯA xác lập (1,5× rồi 1,1×);
  posix_spawn 226–387 µs ngoài scope nhưng 660–1.363 µs trong scope (chưa rõ vì sao; câu "phẳng, nhích ở 1 GiB" không gộp được); giá mỗi lỗi trang
  ~0,5 µs / ~2–3 µs (±50% theo điều kiện); AVX +13 ns; độ lớn khác-CPU theo từng máy.
- Còn mở: cụm chậm ~395 ns ở lượt hai tác vụ; chu kỳ preempt Go ~20 ms; số lỗi sau fork vùng THP (13.637 / 20.698 / 22.786 cho 512 trang lớn — không phải "8% ổn định");
  SigQ 1002; SigIgn của subshell `trap "" TERM` (lặp lại được, chưa giải thích); EPYC chậm 3–5×; posix_spawn chậm trong scope.

Điểm mà output nói ÍT HƠN lời giải thích — phải ghi rõ là suy luận/tài liệu khi viết, hoặc bổ sung thí nghiệm:
- `zombie.txt`: dòng "ls fd: Permission denied" KHÔNG chứng minh fd đã đóng. `job_ttin.txt`: đuôi file không cho thấy job chết sau `kill -9`.
- `init_noreap`: PID 1 tự gửi SIGTERM cho mình (chưa thử con gửi). `job_hangup`: thấy ai nhận SIGHUP, không thấy ai gửi (bash chuyển tiếp là theo tài liệu).
- `sig_queue`: thứ tự handler (USR1 chạy sau 1000 RT) là quan sát; cơ chế "khung lồng nhau" là đọc kernel. SigQ 1002 (gửi 1001) chưa giải thích.
- `sig_threads`: mọi tín hiệu tới một luồng là quan sát; `curr_target` là theo trí nhớ. `core_pattern`: "RLIMIT_CORE=1 là giá trị đặc biệt" CHƯA kiểm.
- `ids.txt` chạy từ script nên pgid = pid của script (không phải của chính nó) — đúng ý §7, đừng viết "pgid = pid".
- Dao động giữa các lần chạy (đã LƯU thêm: `out/reap_runs.txt` 5 lần, `out/sig_threads_runs.txt` 3 lần, `out/orphan_ancestors.txt`): `reap` naive thu được 78–122 trên 200,
  luôn còn zombie; handler vòng lặp chạy 15–122 lần cho 200 con, luôn thu đủ. `sig_unsafe` hỏng sau 1…487 vòng. `sig_threads`: mọi tín hiệu tới MỘT luồng ở cả 16 hàng
  đã lưu, nhưng số đếm được là 1.989–2.000 trên 2.000 (thiếu 0–11) — câu "thiếu nhiều nhất 1" trước đây SAI (nó dựa trên 2 lần chạy, một lần chỉ in màn hình).

Trạng thái C4.1 (2026-10-12): mã ở `.draft-C4.1/src/` (31 chương trình C, `pty_job.py`, `ctxsw_paired.py`, `pcb.sh`) đã biên dịch và chạy thử.
Đã ghi `out/`: `pcb_*`, `wait_status_run1_buggy.txt`, `core_pattern.txt`, `sig_unsafe_elided.txt`, `calib_chains.txt`, `ctxsw_run1_badcalib.txt`,
`ctxsw_paired*.txt`. Các output khác mới in ra màn hình — CHƯA ghi file; phải chạy lại qua `run.sh`.
Kết quả đã có, kèm giới hạn:
- `core_ghz()` bản đầu dùng chuỗi `add $1` → 17–23 GHz (lặp lại đúng lỗi C3.5 §2.6 đã ghi); đã đổi sang `add %reg`; cột chu kỳ của lượt đầu vô hiệu.
- 15 vòng xen kẽ, hostload 11–12% (`out/ctxsw_paired_ns.txt`, tính lại từ `ctxsw_paired_raw.txt`). ĐƠN VỊ CHÍNH LÀ ns: quy đổi chu kỳ bằng hiệu chuẩn
  từng mẫu (3,86–4,84 GHz, trung vị 4,68) thêm nhiễu và đổi cả dấu ở cặp pipe; chỉ dùng "ns × 4,68 GHz" để định cỡ.
  Chuyển luồng cùng CPU so với cùng lời gọi không chuyển: +215 ns (yield, dải 210–272), +509 ns (pipe, 491–558) — 15/15.
  Tiến trình so với luồng: +99 ns (yield, 43–176, 15/15), +87 ns (futex, 45–150, 15/15), +53 ns (pipe, −8,5–99, 14/15).
  → không phải một con số (phụ thuộc đường đi, ±60 ns mỗi vòng); CHƯA tách được CR3/TLB; đuôi chậm của hai chế độ yield (18–23% theo ns) chưa rõ nguyên nhân.
  `out/ctxsw_paired.txt` (hiệu theo chu kỳ) giữ làm bằng chứng của cách tính kém, không trích làm kết quả.
- Quét tập làm việc (`out/ctxsw_wset.txt`, 7 vòng xen kẽ): phần riêng của lần chuyển (pipe-thr − base2) phẳng ~460–525 ns tới 256 KiB/tác vụ;
  ở 1 MiB/tác vụ lần chuyển tốn 22,5 µs nhưng MỘT tác vụ luân phiên hai vùng 1 MiB không chuyển gì cũng tốn 21,8 µs (pipe1 15,2 µs) → "chi phí gián
  tiếp" là hai tập làm việc chia một cache (2 MiB > L2 1,25 MiB), không phải cơ chế chuyển. Hàng 4 MiB và 16 MiB KHÔNG dùng được (nhiễu ≫ 0,5 µs).
  512 trang/tác vụ: proc 2.978 ns so với thr 3.212 ns → không có dấu vết xả TLB khi đổi tiến trình (hợp với PCID; cơ chế chưa chứng minh, không tắt được PCID).
  tiến trình − luồng: 49–65 ns tới 64 KiB, không phân biệt được ở trên đó. Cỡ cache/TLB đã kiểm: `out/cache_sizes.txt`, C3.6 §5.2 (dTLB 96, STLB ~2.048).
- Khác CPU (`out/ctxsw_cross_cpu.txt`, `ctxsw_cross_idle.txt`): mỗi lần trao tay ~12 µs (khứ hồi 23–26 µs, ba cặp CPU); futex chỉ ngủ 0,75–1,10 lần/vòng
  → chỉ dùng số khứ hồi. Thí nghiệm bác bỏ được: giữ hai CPU bận bằng `spin_idle` (SCHED_IDLE), xen kẽ 4 lần → 2,6 µs so với 12 µs, 4/4, không chồng lấn.
  → ~9,4 µs gắn với việc CPU đích đang nghỉ; CHƯA tách được hypervisor / idle của khách / C-state; 2,6 µs còn lại (3,4× cùng CPU) chưa phân rã.
- Chuyển ở mức người dùng (`out/uctx.txt`, `uctx_strace.txt`): gọi hàm 0,42 ns; `gt_switch` 7,2 ns; `swapcontext` 134–137 ns; `strace -c` đếm
  200.001 `rt_sigprocmask` cho 200.000 lần chuyển (đã kiểm). Dưới strace `swapcontext` thành 48,5 µs (chi phí tracer) còn `gt_switch` vẫn 7,23 ns.
- `hog` (`out/hog.txt`): hai luồng bận trên một CPU chạy 3,94–3,99 ms mỗi lượt ≈ một tick 250 Hz; không đọc được `sched/debug` → cơ chế để C4.2.
- Trạng thái AVX: `out/ctxsw_ymm.txt` và `ctxsw_ymm2.txt` VÔ HIỆU (đã ghi chú trong file): gcc tự thêm `vzeroupper` cuối `dirty_ymm()` nên `-f` không
  làm gì; lần 2 build hỏng nên chạy nhị phân cũ. Sửa: `dirty_ymm` viết bằng asm (`src/ymm.S`), `ctxsw` tự đọc XINUSE (XGETBV ECX=1) trước mỗi lần
  trao tay. Hợp lệ: `ctxsw_ymm3.txt` (0/11,2 triệu so với 11,2 triệu/11,2 triệu): +13,1 ns trên giá trị nhỏ nhất, 7/8 cặp, dải −37…+57;
  đối chứng không chuyển `ctxsw_ymm_noswitch.txt`: +0,2 ns (−0,2…+2,2). → hiệu ứng nhỏ (~4%), sát ngưỡng phân giải ±10 ns; cơ chế (XSAVES lưu thêm
  256 B) là suy luận. CÒN MỞ: cụm chậm ~395–400 ns (so với ~345) chỉ xuất hiện ở các lượt hai tác vụ, không liên quan cờ; chưa rõ nguyên nhân.
- Go 1.27.2 (`out/go_threads.txt`, `go_preempt2*.txt`): 10.000 goroutine đỗ → Threads 5→11; 200 goroutine trong `read(2)` chặn → 203; 200 đọc `os.Pipe`
  (netpoller) → 6. Preempt: `go_preempt.txt` VÔ HIỆU (vòng "không gọi hàm" có gọi hàm mỗi 2^20 vòng; 48 = 48). Bản đúng `preempt2` (objdump: 0 CALL):
  mặc định ticker chạy 71–73 lần/1,48 s, strace đếm 72 SIGURG; `asyncpreemptoff=1`: 1 lần (đúng lúc vòng lặp kết thúc), 0 SIGURG. CÒN MỞ: chu kỳ ~20 ms thay vì 10.
- Runner run17 (commit 4aa4e5c của `c3-arm-lab`, artifact ở `out/runner17/`): [N2] Neoverse-N2 4 lõi; [EPYC] 7763 2 lõi × 2 luồng (CPU 1,2 khác lõi; 2,3 cùng lõi).
  Hiệu chuẩn N2 3,358–3,390 GHz (C3.14: 3,39 → đã kiểm); EPYC 3,18–3,21 (chưa có đối chiếu). `ctxsw_paired_ns.py` tái tạo đúng bảng laptop rồi áp cho runner
  (`out/runner17/paired_ns_*.txt`). ns trung vị i7 / N2 / EPYC: syscall rỗng 62 / 173 / 211; chuyển−không chuyển yield +215 / +289 / +1.077, pipe +509 / +670 / +2.353;
  tiến trình−luồng yield +99 / +100 / +106, pipe +53 / +109 / +38, futex +87 / +148 / +91 (runner: 15/15, dải hẹp). KHÔNG khẳng định "100 ns phổ quát".
  perf đếm lại: 1.200.020 / 1.200.018 so với getrusage 1.200.007 / 1.200.005 (chỉ kiểm cho pipe-thr cùng CPU); gắn perf làm chậm 7–12,5%.
  Khác CPU, đích nghỉ / bận (µs mỗi lần trao tay): i7 11,6–12,1 / 2,6; N2 7,55 / 6,2–6,4; EPYC 12,8–13,4 / 6,2–6,4 → chiều lặp lại 4/4 trên cả ba máy,
  nhưng độ lớn riêng từng môi trường (phần "do nghỉ" 9,4 / 1,3 / 6,6 µs — tính bằng `ctxsw_cross_three.py`): câu "9,4 trên 12 µs" CHỈ đúng cho laptop. Cơ chế chưa tách trên máy nào.
- `fork_cost` (đã chạy lần đầu hôm nay; `out/fork_cost_4k.txt` có cột "warm" GHI NHÃN SAI — đã chú thích; dùng `_4k_v2`, `_thp_v2`):
  trang 4 KiB: `fork()` 40–67 µs ở 1 MiB → 5,0–5,5 ms ở 1 GiB (≈5 µs/MiB, hai lần chạy); fork+wait ≈ 2× ; vfork 17–44 µs không theo cỡ;
  posix_spawn 226–291 µs, riêng 1 GiB 361/387 µs (hai lần cùng chiều, chưa giải thích). Ghi một byte mỗi trang (kèm số lỗi trang, getrusage):
  sau fork, con đã chết: 1 lỗi/trang, 494–509 ns; lặp lại ngay: 0 lỗi, 14,5–15 ns; con còn sống: 1 lỗi/trang, 2,4–2,7 µs.
  → 1 GiB: lời gọi 5 ms nhưng phần trả sau 0,13 s (con đã chết) tới 0,7 s (con còn sống). "Không sao chép khi con đã chết" là suy từ giá thấp hơn 5×.
  THP (`-t`): AnonHugePages của tiến trình 1024 MiB sau lần chạm đầu, sau 30 fork, sau lượt ghi đầu; = 0 sau lượt cow (đo trực tiếp ở 3 cỡ) →
  fork 1 GiB chỉ 0,17–0,27 ms (hai lần); ghi khi con còn sống: 1 lỗi mỗi trang 4 KiB và trang lớn bị tách.
  SAI DỰ ĐOÁN: VmPTE vẫn 2.100 kB khi vùng đang là trang lớn → VmPTE KHÔNG phân biệt được THP với 4 KiB (lý do "bảng trang đặt sẵn" là trí nhớ, chưa kiểm).
  CÒN MỞ: lượt ghi sau fork với THP có 20.698/22.786 lỗi cho 512 trang lớn (~44 lỗi mỗi trang lớn) trong khi AnonHugePages không đổi.
- `thread_cost` (`out/thread_cost.txt`, bản nhị phân trước khi thêm in errno nên dòng lỗi ghi "create failed at 9391"): tạo luồng DỪNG ở 9.391, không tới
  10.000, cả với stack 8 MiB lẫn 64 KiB. Nguyên nhân đã kiểm (`out/thread_limit_cgroup.txt`): shell của phiên nằm trong `init.scope`, `pids.max` = 9516
  (DefaultTasksMax), KHÔNG phải `ulimit -u` 31.721 — câu "dư chỗ" trước đó sai. Cơ chế đo trong scope riêng TasksMax=300 (`thread_limit_scope.txt`):
  hỏng sau 297 luồng, EAGAIN, `pids.events max` 0→1, nhóm chung không đổi. Số đo cho 9.391 luồng: tạo+join 46,0 µs (8 MiB) / 30,8 µs (64 KiB);
  fork+exit+wait ~100 µs; mỗi luồng: VmSize +8.196 / +68 KiB, VmRSS +8,29 KiB, KernelStack +15,98–15,99 KiB (đo trực tiếp), SUnreclaim ~11,3 KiB.
  Cột PageTables VÔ HIỆU (+3,22 rồi −1,29 KiB: số toàn hệ thống).
  QUY TẮC TỪ NAY: thí nghiệm tạo nhiều tác vụ / dùng nhiều bộ nhớ chạy trong `systemd-run --user --scope -q -p TasksMax=… [-p MemoryMax=…]`;
  không chạy lại 10.000 luồng trong nhóm chung (nhóm này chung với tiến trình của người dùng).
- `sig_race` (`out/sig_race.txt`, chạy lần đầu): kiểm-rồi-`pause()` mất 23 và 14 lần đánh thức trên 200.000 vòng (cửa sổ tự nhiên, không ghim CPU);
  `sigsuspend` 0/200.000 hai lần (đồng thời là đối chứng: watchdog không báo giả); nới cửa sổ 20 µs: 721/2.000 (36%, một lần chạy) so với 0/2.000.
- `sig_unsafe threaded hold` + gdb (`out/sig_unsafe_gdb.txt`, `sig_unsafe_gdb2.txt` không lọc): main → malloc → <signal handler called> → bad_handler → malloc →
  `__lll_lock_wait_private`, hai lần chạy. ĐÃ THẤY tự khóa chết trên một khóa trong malloc (là mutex của arena: suy từ thiết kế glibc, khung #4 không có ký hiệu).
  SỬA MÔ TẢ: lúc treo tiến trình chỉ còn MỘT luồng (`/proc/PID/task` có 1 mục, `Threads: 1`, gdb không cảnh báo) — luồng "idle" đã thoát.
  Vậy cặp đối lập là "chưa từng tạo luồng → hỏng heap" và "đã tạo luồng (nay đã thoát) → khóa chết", KHÔNG phải "có luồng thứ hai đang chạy".
  ĐÃ KIỂM bằng hai biến thể (`out/sig_unsafe_modes.txt`, 3 lần mỗi chế độ): `masked` (luồng phụ che SIGALRM) → treo, Threads: 2 (3/3); `joined` (tạo rồi join
  trước vòng lặp) → treo, Threads: 1 (3/3); `threaded` → treo, Threads: 1 (3/3); `single` → abort (3/3; hai thông điệp khác nhau: "corrupted double-linked list"
  và assertion `sysmalloc`; hỏng sau 1…487 vòng). → điều quyết định là "đã từng tạo luồng", không phải "đang có luồng thứ hai".
  Còn là suy luận: masked/joined treo trên CÙNG khóa (chưa có backtrace cho hai chế độ này); luồng nào chạy handler nào (0 handler xong ở masked/joined, 1–3 ở threaded).
- Bốn kết quả cuối (2026-10-12): `sig_unsafe_gdb_joined.txt` — chế độ `joined` cũng main→malloc→<signal>→bad_handler→malloc→`__lll_lock_wait_private`, 1 task
  (chỉ còn `masked` chưa có backtrace). `sig_mask.txt` — `sleep` exec với SIGTERM bị che / bị bỏ qua sống sót `kill -TERM` (SigBlk 0x4000 → ShdPnd 0x4000), chết với
  SIGKILL; ba tiến trình có ba tập SigIgn khác nhau (0x6; 0x1001006; 0x4000) — hàng subshell `trap "" TERM` thiếu INT/QUIT CHƯA giải thích, đừng phát biểu quy tắc
  "job nền bỏ qua INT/QUIT" khi chưa đọc manual bash. `sig_frame_align.txt` — fpregs luôn chia hết 64; sp−fpregs ∈ {976, 992, 1008, 1024} theo sp mod 64, chu kỳ 64;
  khung = 1440…1488 B (khớp mọi mẫu lẻ trước đó; 128 red zone + 836 = 964 nằm trong khoảng (960, 976] mà số liệu ép ra). `green_many.txt` (scope riêng, 3 lần) —
  19,4–19,5 ns/lần chuyển trên 100.000 ngữ cảnh (2 ngữ cảnh: 7,2 ns), 4,03 KiB RSS mỗi luồng xanh, spawn 0,9–1,5 µs (dao động; "do lỗi trang đầu" là suy luận).
- Bài học đưa vào leaf: BỐN lần trình biên dịch gỡ mất/vô hiệu chính thứ đang thử (trước đây tôi ghi "ba", quên vụ zombie) — gcc -O2 xóa cặp `malloc/free`
  không dùng trong handler (handler "không an toàn" hóa rỗng), xóa `malloc`+`memset` của tiến trình con trong `zombie.c` (con chỉ có 292 kB), gấp `1/z` thành so sánh
  (không SIGFPE), thêm `vzeroupper` (trạng thái AVX "bẩn" hóa sạch);
  `printf(..., syscall(), strerror(errno))` sai vì thứ tự tính đối số; stdio chưa flush trước `fork` in lặp.

## Kế hoạch C4 (máy nào cho việc gì)

- Công cụ: `source C4-…/.draft-tools/setup_env.sh` (đặt `C4ROOT`, `C4BUILD` trong scratchpad; giải nén `.draft-tools/debs/*.deb`: strace, gdb, perf 6.17,
  bpftool, pahole). `doccheck.py FILE…`, `blockcheck.py LEAF.md OUTDIR [SRCDIR]` ở cùng thư mục. Biên dịch vào `$C4BUILD` (ext4), không chạy trên `/mnt/d`.
- [i7] WSL2 không root: user namespace (`unshare -Ur`), cgroup v2 ủy quyền qua `systemd-run --user` (cpu, memory, pids), swap 8 GiB, io_uring, BTF đọc được.
  KHÔNG có: SCHED_FIFO (rtprio 0), eBPF/ftrace/tracepoint (cần root), dm-flakey, Docker (chưa bật WSL integration), /dev/kvm.
- Việc cần root → runner GitHub (`NgTienDuy/c3-arm-lab`, sudo, systemd, Docker, KVM trên x86): C4.2 (FIFO/DEADLINE, đảo ưu tiên), C4.4 (dm-flakey,
  mkfs), C4.11 (cgroup/veth/seccomp thật), C4.12 (QEMU khởi động + DT overlay), C4.13 (ftrace, bpftrace, bcc).
- C4.4 trên runner: rootfs của runner gắn `nobarrier,data=writeback,journal_async_commit,commit=30` (đọc từ /proc/cmdline, run18) → KHÔNG đo fsync/độ bền trên
  rootfs của runner; tự tạo loop device + mkfs + tùy chọn mount riêng.
- C4.10: không có MCU nối máy → FreeRTOS/Zephyr trên QEMU/Renode (thời gian mô phỏng) + đo jitter thật trên Linux; phần MCU thật để "Mở rộng".

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

## Việc cần báo người dùng (chưa làm, cần họ quyết)

- Thư mục crash dump của WSL phía Windows (`%LOCALAPPDATA%\Temp\wsl-crashes`, đọc từ WSL là `/mnt/c/Users/<tài khoản>/AppData/Local/Temp/wsl-crashes`) đang giữ
  ~5,7 GiB file `.dmp` do chương trình thử của các phiên trước sinh ra (hai file edgetpu 4,6 GiB + 1,0 GiB ngày 2026-10-08, v.v.) và 2 file 450 kB của phiên 2026-10-12
  (`wait_status`, trước khi tôi cho tiến trình con tự khai không dump). `core_pattern` của WSL là một pipe nên `ulimit -c 0` KHÔNG chặn được. Nằm NGOÀI dự án →
  không tự xóa; hỏi người dùng. Từ nay chương trình cố ý sập phải gọi `prctl(PR_SET_DUMPABLE, 0)` trước.

## Blockers

- Không có vi điều khiển nối vào máy (ESP32 DevKit, Arduino Uno có trong tay nhưng chưa nối), không Raspberry Pi/SBC, không NPU thật: các phép đo
  đó để ở mục "Mở rộng" của C3.x. Mở khóa: người dùng nối thiết bị (USB → `usbipd` cho WSL).

## Last verification

- 2026-10-09: `doccheck.py` trên C3.1–C3.14: 14 file, 0 lỗi, 0 cảnh báo. `blockcheck.py` C3.7–C3.14 với `out/` của từng nháp: 0 dòng lệch
  (C3.7 431, C3.8 209, C3.9 191, C3.10 286, C3.11 301, C3.12 618, C3.13 371, C3.14 427). Sau đó xóa `.draft-C3.7` … `.draft-C3.14`.
