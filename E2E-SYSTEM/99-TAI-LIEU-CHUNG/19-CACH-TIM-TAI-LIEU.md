---
loai: meta
ma: M19
tieu_de: "Cách tìm hiểu theo roadmap"
---

# 19 · Cách tìm hiểu theo roadmap

> Đây là **phương pháp**, không phải danh sách link. Danh sách link hỏng sau 2 năm; phương pháp thì không.
> Nguồn cụ thể theo loại: [`21-NGUON-THEO-LOAI.md`](21-NGUON-THEO-LOAI.md).
> Từ khoá tiếng Anh để tra: [`20-TU-DIEN-VI-EN.md`](20-TU-DIEN-VI-EN.md).

---

## 0 · Ba quyết định chốt trước, không bàn lại

| Quyết định | Vì sao |
|---|---|
| **Đơn vị học là một sub-leaf**, không phải "một chủ đề" | Roadmap đã chia sẵn 2.128 sub-leaf. Mỗi cái vừa một buổi. "Học networking" là câu vô nghĩa; "học path MTU discovery" thì đo được |
| **Tra cứu bằng tiếng Anh, ghi chú bằng tiếng Việt + thuật ngữ Anh nguyên gốc** | Xem §1 |
| **Một sub-leaf đóng lại khi có bằng chứng**, không khi "đã đọc xong" | Ô *Bằng chứng · nguồn* trong template tồn tại vì lý do này |

---

## 1 · Quy tắc ngôn ngữ: tiếng Việt → tiếng Anh

### Vì sao phải chuyển

Ba lý do, xếp theo sức nặng:

1. **Khối lượng.** Với phần lớn sub-leaf trong roadmap này, tài liệu tiếng Việt đủ sâu **không tồn tại**. Không phải ít — là không có. Thử tra "coordinated omission", "write skew", "anti-rollback counter", "coordinated universal time vs monotonic clock" bằng tiếng Việt và bạn sẽ thấy.
2. **Nguồn gốc.** RFC, datasheet, errata, tiêu chuẩn IEC, paper — tất cả gốc tiếng Anh. Mọi bản tiếng Việt đều là bản dịch, tức là đã qua một lần mất mát.
3. **Đường ra.** Năng lực bạn đang xây được đo bằng việc bạn nói chuyện được với kỹ sư phần mềm và kỹ sư OT. Cả hai nhóm dùng thuật ngữ tiếng Anh. Nếu bạn chỉ biết bản dịch tiếng Việt, bạn hiểu mà không nói được — tệ hơn là không hiểu, vì bạn không biết mình không nói được.

### Năm quy tắc

**Quy tắc 1 — mỗi sub-leaf phải có đúng một *canonical English term*.**
Trước khi tìm bất cứ thứ gì, viết ra thuật ngữ tiếng Anh chuẩn của sub-leaf đó. Nếu không viết được, bạn **chưa biết mình đang học gì** — và mọi phút tìm kiếm sau đó sẽ lãng phí. Tra ở [`20-TU-DIEN-VI-EN.md`](20-TU-DIEN-VI-EN.md) trước.

**Quy tắc 2 — không dịch thuật ngữ khi ghi chú.**
Viết `cache coherence` rồi mở ngoặc `(mạch lạc cache)` nếu cần, **không bao giờ ngược lại**. Lý do rất thực dụng: 6 tháng sau bạn mở lại file và muốn tra sâu hơn — nếu trong file chỉ có chữ tiếng Việt, bạn phải dịch lại từ đầu.

> Tiêu đề sub-leaf trong file giữ nguyên tiếng Việt của roadmap (để đối chiếu được).
> Nhưng **dòng đầu tiên** của ô *"Là gì · cơ chế"* nên là thuật ngữ tiếng Anh.

**Quy tắc 3 — tiếng Việt chỉ dùng cho hai việc.**

| Dùng tiếng Việt | Dùng tiếng Anh |
|---|---|
| Lần tiếp xúc đầu để có trực giác (≤20% thời gian của sub-leaf) | Mọi tra cứu, mọi nguồn cấp 0–3 |
| Phần **giải thích của chính bạn** trong file | Mọi thuật ngữ, mọi tên riêng, mọi truy vấn tìm kiếm |
| Toán nền và điện tử cơ bản, nếu tiếng Việt nhanh hơn | Mọi thứ thuộc C1–C12 |
| Nói chuyện với đồng nghiệp ở công trường | Ghi chú kỹ thuật, ADR, postmortem |

**Quy tắc 4 — không đọc sách dịch.**
Bản dịch tiếng Việt của sách kỹ thuật thường trễ 5–10 năm, thuật ngữ lệch, và làm hỏng khả năng tra cứu tiếp của bạn. Ngoại lệ duy nhất: sách toán thuần (đại số tuyến tính, xác suất) — nội dung không đổi theo thời gian và ký hiệu là quốc tế.

**Quy tắc 5 — ba tháng đầu chấp nhận chậm gấp đôi.**
Đây là chi phí một lần. Sau ~200 giờ đọc kỹ thuật tiếng Anh, tốc độ của bạn vượt tốc độ đọc bản dịch, vĩnh viễn.

### Cách rút ngắn ba tháng đó

- **Đừng học từ vựng rời.** Học *cụm* của ngành: `by design`, `out of scope`, `at the cost of`, `unless otherwise specified`, `undefined behavior`, `is guaranteed to`, `SHOULD / MUST / MAY` (nghĩa chính xác trong RFC 2119 — đọc đúng 1 trang này, nó chi phối mọi spec bạn sẽ đọc).
- **Đọc mục lục trước, luôn luôn.** Mục lục một cuốn sách 600 trang dạy bạn cấu trúc của cả lĩnh vực trong 10 phút.
- **Dùng LLM để dịch *đoạn khó*, không dịch cả chương.** Xem §8.
- **Mỗi tuần đọc to 1 trang.** Nghe kỳ cục nhưng có tác dụng: nó ép bạn xử lý từng từ thay vì lướt.
- **Sổ dịch OT↔IT** ở [`12-SO-DICH-OT-IT.md`](12-SO-DICH-OT-IT.md) chính là bài tập ngôn ngữ chuyên ngành hiệu quả nhất bạn có — 2 dòng/tuần.

---

## 2 · Giao thức 6 bước cho một sub-leaf

Tổng ~90 phút. Nếu vượt 2× thì dừng — xem bước 6.

| Bước | Thời gian | Làm gì | Ra cái gì |
|---|---|---|---|
| **0 · Đặt tên** | 2' | Viết thuật ngữ tiếng Anh chuẩn | 1 dòng ở đầu ô *Là gì · cơ chế* |
| **1 · Định vị** | 3' | Wikipedia **tiếng Anh** — chỉ để lấy từ vựng, tên người, tên chuẩn, và bản đồ khái niệm lân cận. **Không học ở đây** | 3–5 từ khoá phụ để tra tiếp |
| **2 · Nguồn gốc** | 10' | Tìm nguồn cấp T0: RFC / spec / datasheet + errata / man page / paper gốc / source code | 1 link + số hiệu mục |
| **3 · Hiểu** | 45' | **Một** chương sách hoặc **một** bài giảng. Một, không phải ba | Ghi chú vào 4 ô của sub-leaf |
| **4 · Làm** | 30' | Chạy / đo / đấu nối / phá cho hỏng | Số đo, ảnh, commit |
| **5 · Đóng** | 10' | Điền đủ 4 ô, tick trạng thái, ghi nguồn theo cú pháp §3 | Sub-leaf đóng |

**Bước 6 — khi bế tắc.** Sau 90 phút vẫn mù mờ: ghi câu hỏi cụ thể vào mục *6 · Câu hỏi mở* của file, **không tick "đã hiểu"**, chuyển sang sub-leaf khác, quay lại trong ≤2 tuần. Phần lớn bế tắc là do thiếu một dependency — mục 5 · Liên kết chéo là nơi bạn phát hiện ra nó.

### Ngân sách theo mức mục tiêu

Mức mục tiêu của leaf (`Aw`…`Ex`) quyết định bạn được tiêu bao nhiêu, không phải độ hứng thú.

| Mức | Giờ / leaf | Số nguồn tối đa | Dừng khi |
|---|---|---|---|
| `Aw` awareness | 0,5–1 | 1 | Nói được 1 câu: nó giải quyết gì, vì sao chưa cần |
| `Ba` basic | 2–4 | 1–2 | Nhận ra nó khi gặp, biết tra ở đâu |
| `Wo` working | 6–12 | 2 | Dùng được theo hướng dẫn, gỡ được lỗi thường gặp |
| `In` intermediate | 15–25 | 2–3 | Chọn được giữa các phương án, giải thích được đánh đổi |
| `Ad` advanced | 30–60 | 3–4 | Thiết kế được, debug được lỗi lạ, biết giới hạn |
| `Ex` expert | 80+ | không giới hạn nhưng phải có T0 | Người khác hỏi bạn |

> Nếu bạn đang ở nguồn thứ 5 cho một leaf mức `Wo`, vấn đề không phải tài liệu — mà là bạn đang né bước 4 (làm thật).

---

## 3 · Bậc thang nguồn T0–T5

| Bậc | Loại | Ví dụ | Dùng để |
|---|---|---|---|
| **T0** | Nguồn gốc | RFC, IEC/ISA/IEEE spec, datasheet + reference manual + **errata**, man page, source code, paper gốc | Trả lời "chính xác nó là gì" · giải quyết mọi tranh cãi |
| **T1** | Sách giáo trình kinh điển | CS:APP, OSTEP, DDIA, Art of Electronics… | Xây mô hình tư duy |
| **T2** | Khoá đại học công khai + lecture notes | MIT OCW, Stanford, CMU, NPTEL | Trình tự và bài tập |
| **T3** | Tài liệu chính thức của dự án / nhà sản xuất | Linux kernel docs, PostgreSQL docs, Kubernetes docs, Siemens/ABB manual, TI/ADI application note | "Dùng thế nào" trong đúng phiên bản bạn đang chạy |
| **T4** | Blog kỹ sư của nơi vận hành hệ thật + postmortem công khai + Jepsen report | Cloudflare, Netflix, AWS Builders' Library, báo cáo sự cố | Chế độ hỏng thật, thứ sách không có |
| **T5** | Video, blog cá nhân, tutorial, LLM | YouTube, Medium, chatbot | **Phá băng** khi bạn tắc, tối đa 1 nguồn/leaf |

**Quy tắc cứng:** mọi khẳng định đi vào file phải truy được về **T0–T3**. T4 dùng để bổ sung chế độ hỏng. T5 không bao giờ là nguồn cuối cùng.

### Cú pháp ghi nguồn (ngắn, tra lại được)

Viết vào ô *Bằng chứng · nguồn* theo mẫu `[Bậc] Nguồn · vị trí chính xác`:

```
[T0] RFC 9293 §3.8.6.2      ← congestion window
[T0] STM32F411 RM0383 §13.4 + ES0287 rev9 mục 2.1.3 (errata I2C)
[T1] CS:APP 3rd ed. §6.4.2
[T2] MIT 6.1810 Lecture 5 notes, tr.3
[T3] PostgreSQL 17 docs, "Transaction Isolation" §13.2.3
[T4] Cloudflare blog 2024-03 "…" — mục chế độ hỏng
```

Không ghi `Google`, không ghi `một video trên YouTube`, không ghi `ChatGPT`.

---

## 4 · Chọn nguồn theo tầng công nghệ

Nối thẳng với [`05-TECHNOLOGY-LAYER.md`](05-TECHNOLOGY-LAYER.md). Tầng quyết định **loại nguồn** và **hạn dùng của nguồn**.

| Tầng roadmap §8 | Nguồn đúng | Hạn dùng | Sai lầm điển hình |
|---|---|---|---|
| 1 · Timeless | Sách kinh điển, paper gốc | Vô hạn — sách 1990 vẫn đúng | Tìm blog 2026 cho thứ Dijkstra đã giải xong |
| 2 · Long-lived (10–30 năm) | Sách + spec | 10+ năm | Bỏ qua vì "cũ" |
| 3 · Durable (5–15 năm) | Sách + docs chính thức | 5 năm | Học qua tutorial thay vì docs |
| 4 · Current mainstream | **Chỉ docs chính thức + changelog + release notes** | **18 tháng** | Mua sách về framework — sách in xong đã lỗi thời |
| 5 · Emerging | Paper + repo + issue tracker | 6 tháng | Đọc blog tổng hợp thay vì paper |
| 6 · Đang mất relevance | Không đầu tư | — | Học vì "công ty vẫn dùng" |

**Kiểm tra ngày, luôn luôn.** Với tầng 4–5, nguồn cũ hơn 18 tháng phải kiểm chứng lại bằng docs hiện hành trước khi ghi vào file.

---

## 5 · Sáu công thức theo *loại* sub-leaf

Không phải sub-leaf nào cũng tra giống nhau. Nhận ra loại rồi áp đúng công thức.

### A · Khái niệm CS / hệ thống
> *ví dụ: C4.3 bộ nhớ ảo · C10.3 mô hình nhất quán · C9.3 mức cô lập*

1. Wikipedia EN lấy từ vựng (3').
2. **Một chương sách T1** — đây là loại duy nhất mà sách thắng tuyệt đối mọi nguồn khác.
3. Lecture notes T2 của cùng chủ đề để lấy bài tập.
4. Làm: viết chương trình nhỏ nhất thể hiện hiện tượng đó.

**Bằng chứng cần có:** một chương trình ≤50 dòng tái hiện đúng hiện tượng, và bạn giải thích được vì sao nó xảy ra.

### B · Thuật toán / cấu trúc dữ liệu
> *ví dụ: C2.8 quy hoạch động · C2.10 Bloom filter*

1. Sách T1 hoặc lecture notes T2 → hiểu bất biến (invariant), không học thuộc code.
2. **Tự cài từ đầu**, không nhìn code mẫu.
3. So với thư viện chuẩn: đo chênh lệch, giải thích chênh lệch.

**Bằng chứng:** bản cài của bạn + một biểu đồ so sánh + một câu giải thích vì sao thư viện nhanh hơn.

### C · Giao thức
> *ví dụ: C5.5 TCP · C5.8 MQTT · C5.16 Modbus/OPC UA · C6.3 I²C*

1. **Spec gốc trước** (RFC / tài liệu OPC Foundation / Modbus spec / datasheet). Đọc mục "message format" và "state machine".
2. **Bắt gói thật** — Wireshark cho mạng, logic analyzer cho bus phần cứng.
3. Đối chiếu từng byte trên dây với từng trường trong spec.
4. Phá nó: rút dây, sai địa chỉ, sai baud, quá tải — xem nó hỏng thế nào.

**Bằng chứng:** một capture có chú thích, trong đó bạn chỉ ra được ≥1 trường mà spec nói một đằng và thiết bị làm một nẻo (luôn có).

> Đây là loại sub-leaf mà **đọc không bao giờ đủ**. Một giờ với Wireshark bằng mười giờ đọc.

### D · Phần cứng / thiết bị
> *ví dụ: C6.1 MCU · S2.2 datasheet · C7.6 cảm biến*

1. **Datasheet + reference manual + errata** — ba tài liệu khác nhau, errata quan trọng nhất và bị bỏ qua nhiều nhất.
2. **Application note của nhà sản xuất** (TI, Analog Devices, Nordic, ST) — chất lượng rất cao, miễn phí, và gần như không ai đọc.
3. Đo bằng thiết bị thật: đồng hồ, logic analyzer, oscilloscope.

**Bằng chứng:** một waveform hoặc một số đo, kèm dòng trong datasheet mà nó khớp (hoặc không khớp).

### E · Vận hành / production
> *ví dụ: C11.9 incident · C10.10 kiểm soát tải · C11.4 phân phối độ trễ*

Sách dạy được **cơ chế**, không dạy được **chế độ hỏng thật**. Loại này phải lấy từ T4:

1. Đọc **postmortem công khai** của các công ty lớn về đúng hiện tượng đó.
2. Đọc **AWS Builders' Library** / Google SRE book cho khung tư duy.
3. **Tự gây ra sự cố** trong lab: giết tiến trình, rút mạng, làm đầy đĩa, lệch đồng hồ.

**Bằng chứng:** một sự cố bạn tự gây ra, đồ thị trước/sau, và cơ chế phát hiện bạn thêm vào.

### F · Toán
> *ví dụ: S1.2 đại số tuyến tính · S1.3 xác suất*

1. Học **đúng phần đang chặn**, không học cả môn (roadmap S1 nói rõ điều này).
2. Trực giác trước (video ngắn), hình thức sau (sách), bài tập cuối.
3. Quay lại engineering ngay khi hết chặn.

**Bằng chứng:** dùng được nó trong một đoạn code hoặc một phép tính kỹ thuật thật, không phải giải xong bài tập.

### G · Tiêu chuẩn công nghiệp *(loại đặc thù với công việc của bạn)*
> *ví dụ: C6.16 IEC 61131-3 · C12.15 ISA-95 · S4.9 IEC 62443 · A5 chuẩn thiết bị*

Tiêu chuẩn thường phải mua, và đọc tiêu chuẩn thô là cách chậm nhất để hiểu nó. Thứ tự đúng:

1. **Tài liệu tóm tắt của nhà cung cấp** (Siemens, ABB, Rockwell đều có whitepaper miễn phí giải thích chuẩn mà sản phẩm họ tuân theo) — lấy bản đồ.
2. **Hướng dẫn công khai của cơ quan/hiệp hội** — ví dụ NIST SP 800-82 cho an ninh OT, tài liệu công khai của OPC Foundation, PLCopen.
3. **Bản thân tiêu chuẩn** chỉ khi cần con số chính xác để tranh luận hoặc để viết spec.
4. **Hệ thống thật ở công ty bạn** — đây là nguồn bạn có mà 99% người học không có. Tận dụng nó.

**Bằng chứng:** vẽ được một hệ thống thật ở công ty theo mô hình của chuẩn, và chỉ ra chỗ thực tế lệch khỏi chuẩn.

---

## 6 · Truy vấn: cú pháp và mẫu

### Toán tử đáng dùng

| Toán tử | Tác dụng | Ví dụ |
|---|---|---|
| `"..."` | khớp chính xác cụm | `"coordinated omission"` |
| `site:` | giới hạn miền | `site:ietf.org`, `site:ti.com`, `site:*.edu` |
| `filetype:pdf` | lấy lecture notes, app note, spec | `FMEA filetype:pdf lecture` |
| `intitle:` | tài liệu chuyên về nó, không nhắc qua | `intitle:"clock drift"` |
| `-` | loại nhiễu | `kalman filter -tutorial -medium` |
| `after:` | với công nghệ tầng 4–5 | `vllm continuous batching after:2026-01-01` |

### Mười hai mẫu truy vấn

| Bạn muốn | Truy vấn |
|---|---|
| Tài liệu học có hệ thống | `<term> lecture notes filetype:pdf site:*.edu` |
| Spec gốc | `<term> RFC` · `<term> specification site:opcfoundation.org` |
| Cách nó hỏng | `<term> failure mode` · `<term> postmortem` · `<term> incident` |
| Cạm bẫy | `<term> "common mistakes"` · `<term> pitfalls` · `<term> "why you should not"` |
| Đánh đổi | `<A> vs <B> tradeoff` · `<A> vs <B> when to use` |
| Số đo thật | `<term> benchmark methodology` · `<term> latency p99` |
| Phần cứng | `<part number> datasheet` · `<part number> errata` · `<vendor> application note <term>` |
| Bản đồ lĩnh vực | `awesome <term> github` *(chỉ để lấy bản đồ, không để học)* |
| Chọn sách | `<topic> textbook "table of contents"` → đọc mục lục 3 cuốn → chọn 1 |
| Paper gốc | `<term> original paper` · `<term> site:arxiv.org` |
| Bản chuẩn công nghiệp | `<standard number> overview whitepaper` |
| Cộng đồng đang tranh luận gì | `<term> site:news.ycombinator.com` · `<term> site:lobste.rs` |

### Quy tắc 3 truy vấn

Nếu **3 truy vấn khác nhau** không ra nguồn T0–T3 nào, vấn đề là **từ khoá sai**, không phải "không có tài liệu". Quay lại bước 0: bạn đang gọi sai tên khái niệm. Tra [`20-TU-DIEN-VI-EN.md`](20-TU-DIEN-VI-EN.md) hoặc hỏi LLM đúng theo §8.

---

## 7 · Đánh giá một nguồn trong 60 giây

| # | Câu hỏi | Trượt nếu |
|---|---|---|
| 1 | Tác giả có **vận hành** thứ họ viết không? | Chỉ tổng hợp lại từ nguồn khác |
| 2 | Có **số đo** không, hay chỉ có khẳng định? | "Nhanh hơn nhiều" mà không có con số |
| 3 | Có nói **điều kiện nó sai** không? | Chỉ có ưu điểm |
| 4 | **Ngày viết** so với tầng công nghệ? | Tầng 4–5 mà cũ hơn 18 tháng |
| 5 | Nó **dẫn về nguồn gốc** nào? | Không dẫn nguồn, hoặc dẫn vòng về blog khác |

Trượt ≥2 câu → đóng tab. Đừng bookmark "để đọc sau" — thư mục đó là nghĩa địa.

---

## 8 · Dùng LLM đúng cách

LLM là công cụ **tra cứu và dịch**, không phải nguồn.

### Bốn việc nên

| Việc | Prompt mẫu |
|---|---|
| Lấy thuật ngữ tiếng Anh chuẩn | *"Trong ngữ cảnh hệ nhúng, thuật ngữ tiếng Anh chuẩn cho 'biến giữ lại khi mất điện trong PLC' là gì? Cho 3 biến thể và nói rõ ngành nào dùng cái nào."* |
| Giải thích đoạn khó của tài liệu **bạn đang mở** | *"Đây là đoạn §13.4 của reference manual [dán]. Giải thích cơ chế clock stretching ở đây, và nói rõ đoạn nào tôi đang hiểu sai nếu tôi nghĩ X."* |
| Sinh câu hỏi kiểm tra bản thân | *"Tôi vừa học về write skew. Đặt 5 câu hỏi mà người hiểu thật trả lời được còn người học vẹt thì không."* |
| Chuyển ghi chú tiếng Việt sang thuật ngữ Anh chuẩn | *"Sửa ghi chú này: giữ nguyên ý, thay mọi khái niệm bằng thuật ngữ tiếng Anh chuẩn của ngành, để tôi tra cứu tiếp được."* |

### Bốn việc không

- **Không** dùng làm nguồn trích dẫn. Nếu nó nói một con số, đi tìm con số đó ở T0–T3 rồi mới ghi vào file.
- **Không** thay việc đọc spec. Nó tóm tắt spec khá tốt và sai ở đúng chỗ quan trọng.
- **Không** nhận code bạn chưa đọc từng dòng — roadmap C1.13 nói thẳng điều này.
- **Không** hỏi trước khi tự thử. Hỏi sau khi tắc là học; hỏi trước khi thử là thay thế việc học.

**Câu hỏi bắt buộc sau mỗi câu trả lời:** *"Nguồn gốc nào nói vậy — RFC nào, chương nào, datasheet nào?"* Rồi tự mở nguồn đó ra.

---

## 9 · Bảy cạm bẫy khi tìm tài liệu

| # | Cạm bẫy | Dấu hiệu | Chặn bằng |
|---|---|---|---|
| 1 | **Tutorial hell** | Làm xong tutorial thứ 3 mà chưa viết dòng nào của riêng mình | Trần **1 tutorial / leaf** |
| 2 | **Sưu tầm nguồn** | Thư mục bookmark dài hơn ghi chú | Trần **3 nguồn / leaf**; nguồn thứ 4 chỉ thêm khi 3 cái đầu đã tick "đã xong" |
| 3 | **Sách dịch** | Thuật ngữ trong ghi chú toàn tiếng Việt | Quy tắc 4, §1 |
| 4 | **YouTube-first** | Bắt đầu mọi chủ đề bằng video | Video là T5 — chỉ dùng khi đã tắc |
| 5 | **Đọc tuần tự** | Đọc sách 600 trang từ trang 1 | Đọc **chương đang chặn**, theo thứ tự học ở file INDEX của nhánh |
| 6 | **Chờ nguồn hoàn hảo** | "Tìm khoá học tốt nhất về X" kéo dài 2 tuần | Chọn nguồn đủ tốt trong 15 phút, bắt đầu; đổi nếu sau 3 giờ thấy sai |
| 7 | **Học theo dự án được giao** | Chỉ học thứ tuần này công việc cần | Roadmap §12.3b cạm bẫy 6 — giờ tự học phải đi vào nhóm ① của Phụ lục D |

---

## 10 · Nhịp tuần mẫu

Roadmap nói rõ: **đừng ép 15 h/tuần đều đặn**. Thiết kế theo tuần tốt / tuần xấu.

| Loại tuần | Giờ | Phân bổ |
|---|---|---|
| **Tuần tốt** (20–25 h) | 1 leaf mức `In`/`Ad` gần xong + 1 buổi project + 1 buổi đọc T0 | Dồn phần khó vào đây |
| **Tuần thường** (12–18 h) | 3–4 sub-leaf + 1 buổi làm thật | Nhịp mặc định |
| **Tuần xấu** (≤5 h) | 1 sub-leaf mức `Ba`/`Wo` + 2 dòng sổ dịch | **Không** bỏ hẳn — giữ chuỗi |
| **Tuần mất** (công trường) | 0 h học, nhưng **vẫn ghi sổ dịch** | Công trường là nguồn T0 mà người khác không có |

**Việc duy nhất không được bỏ ở bất kỳ loại tuần nào:** 2 dòng vào [`12-SO-DICH-OT-IT.md`](12-SO-DICH-OT-IT.md).

---

## 11 · ✎ Nguồn tôi đang mở

Giữ bảng này ngắn. Quá 5 dòng nghĩa là bạn đang mở quá nhiều mặt trận.

| Leaf | Nguồn | Bậc | Bắt đầu | Trang / chương đang ở | Đóng khi |
|---|---|---|---|---|---|
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

## ✎ Nguồn đã loại và lý do

*Ghi lại để không mở lại lần thứ hai.*

| Nguồn | Ngày | Loại vì |
|---|---|---|
|  |  |  |
