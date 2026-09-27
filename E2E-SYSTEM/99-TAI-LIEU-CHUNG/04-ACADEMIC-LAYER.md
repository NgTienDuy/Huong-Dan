---
loai: meta
ma: M04
---
# 04 · Academic layer — nền học thuật nào chạy song song

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# 7. ACADEMIC LAYER

Trục chính là engineering. Bảng này nói: nền học thuật nào **chạy song song**, nền nào **hoãn được và tới khi nào**, nền nào **chỉ cần biết tồn tại**.

## 7.1 — Bảng đầy đủ

| Nền tảng | Nhãn | Phase | Lý do | Chặn cái gì nếu thiếu |
|---|---|---|---|---|
| Số học nhị phân, logic Boolean | **Học ngay** | 0–1 | Không có thì computer architecture là ma thuật | C3 toàn bộ |
| Discrete math: tập hợp, quan hệ, tổ hợp, quy nạp | **Học ngay** | 1 | Ngôn ngữ để lập luận về tính đúng của thuật toán | C2.1, C2.9, S5.2 |
| Đại số tuyến tính tới eigenvalue | **Học ngay** | 1–2 | Dependency toán **chặn** duy nhất của ML | C8 toàn bộ, C7.8 |
| Xác suất: biến ngẫu nhiên, kỳ vọng, Bayes | **Học ngay** | 1–2 | Uncertainty là bản chất của hệ thông minh | C8.1, C8.3, C7.8 |
| Thống kê: ước lượng, kiểm định, lỗi nhiều so sánh | **Học ngay** | 2 | Thứ ngăn bạn tin vào một cải thiện không có thật | C8.3, C11.7 |
| Calculus tới gradient nhiều biến | **Học ngay** | 2 | Đủ cho backprop; tích phân nâng cao thì defer | C8.4 |
| Fourier & biến đổi | **Học ngay** | 3 | Chặn toàn bộ sensing | C7.3, C7.4, C7.10 |
| Vật lý: điện học, RC, năng lượng | **Học ngay** (tối thiểu) | 1–3 | Ohm, công suất, tụ — đủ để không đốt board | S2, C6 |
| Lý thuyết độ phức tạp: P/NP, reduction | **Defer** | 2–3 | Nhận ra "cái này NP-hard" là đủ; không cần chứng minh | Không chặn |
| Optimization: convexity, Lagrange, KKT | **Defer** | 3 | Cần khi đi sâu training hoặc control | C8.7 ở mức nâng cao |
| Numerical analysis: sai số, ổn định, điều kiện | **Defer** | 3 | Cần **đúng lúc** làm quantization | C8.9, C3.12 nâng cao |
| Information theory: entropy, mutual info, channel capacity | **Defer** | 3 | Làm sáng nhiều thứ nhưng không chặn | Không chặn |
| Queueing theory: M/M/1, Little's law | **Defer** (trực giác thì học ngay) | 3–4 | Little's law dùng được trước khi hiểu chứng minh | C11.5 ở mức định lượng |
| Lý thuyết điều khiển: Laplace, hàm truyền, ổn định | **Defer** | 3–4 | PID dùng được trước khi hiểu Laplace | S3.3, S3.4 |
| Lý thuyết phân tán: FLP, CAP, PACELC, chứng minh consensus | **Defer** (phát biểu học ngay) | 3–4 | Kết luận quan trọng hơn chứng minh ở giai đoạn này | C10.5 ở mức nâng cao |
| Lý thuyết tính toán: automata, Turing, decidability | **Defer** | 4–5 hoặc không | Đẹp nhưng không chặn gì | Không chặn |
| Lý thuyết độ tin cậy: Weibull, phân tích tồn tại | **Defer** | 4–5 | Cần khi định lượng tuổi thọ thiết bị | S6.1 ở mức định lượng |
| Điện từ, truyền sóng | **Chỉ awareness** | — | Đủ để biết vì sao tường chặn 2.4 GHz | Không chặn |
| Lý thuyết học thống kê: VC dimension, generalization bound | **Chỉ awareness** | — | Biết tồn tại giới hạn lý thuyết; không dùng hàng ngày | Không chặn |
| Lý thuyết ngôn ngữ lập trình: type theory, lambda calculus | **Chỉ awareness** | — | Type system dùng được mà không cần lý thuyết | Không chặn |
| Cryptography lý thuyết | **Chỉ awareness** | — | Dùng thư viện; tự cài là phản mẫu | Không chặn |
| Lý thuyết thông tin lượng tử | **Chỉ awareness** | — | Không nằm trên đường tới hệ nào bạn xây | Không chặn |

## 7.2 — Quy tắc vận hành

**[Recommendation]** Ba quy tắc, áp dụng nghiêm:

1. **Gặp toán chặn đường → học đúng phần chặn trong ≤2 buổi, rồi quay lại engineering.** Không mở một khóa 15 tuần vì một công thức. Ghi lại khái niệm đó vào danh sách "cần học có hệ thống sau".

2. **Dồn phần có hệ thống vào ba đợt tập trung**, mỗi đợt 4–6 tuần, chiếm ~60% thời gian trong đợt:
   - **Đợt 1 (đầu Phase 1):** discrete math + đại số tuyến tính nền
   - **Đợt 2 (đầu Phase 2):** xác suất + thống kê
   - **Đợt 3 (đầu Phase 3):** Fourier + optimization + numerical methods

3. **Mọi khái niệm toán phải được neo vào một thứ bạn đang xây.** Học eigenvalue khi đang làm PCA. Học Fourier khi đang phân tích rung động. Học Little's law khi đang tính capacity. Toán không neo sẽ bay hơi trong 3 tháng.

## 7.3 — Cái tôi cố ý không đưa vào

| Không đưa vào | Vì sao |
|---|---|
| Real analysis, topology, abstract algebra | Không chạm vòng; là nền cho nghiên cứu toán, không cho kỹ thuật hệ thống |
| Xác suất đo lường (measure-theoretic probability) | Xác suất "kỹ sư" đủ cho mọi thứ trong roadmap này |
| Lý thuyết tối ưu lồi đầy đủ | Cần cho research về optimizer, không cần cho người dùng optimizer |
| Lý thuyết đồ thị nâng cao (phổ, ngẫu nhiên) | Không chạm vòng |
| Lý thuyết trò chơi | Chỉ liên quan nếu làm hệ multi-agent có cạnh tranh |

---
---

## ✎ Phần của tôi — theo dõi

| Nền tảng | Đã học tới đâu | Chặn cái gì | Ngày |
|---|---|---|---|
|  |  |  |  |

