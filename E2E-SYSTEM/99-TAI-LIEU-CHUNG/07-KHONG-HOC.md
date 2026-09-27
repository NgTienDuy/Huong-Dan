---
loai: meta
ma: M07
---
# 07 · Chủ động bỏ qua — và mốc quay lại

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

# 12. CHỦ ĐỘNG BỎ QUA

Mọi giờ dành cho những thứ dưới đây là giờ **không** dành cho core. Danh sách này bắt buộc theo §1.5 của prompt, và là một trong những phần có giá trị nhất của tài liệu.

## 12.1 — Bỏ hẳn

| Thứ | Lý do | Nếu thấy mình đang làm |
|---|---|---|
| **Học một framework agent ở mức sâu** | Tầng biến động nhất trong stack; landscape đổi trong 5 tháng đầu 2026 nhiều hơn cả 2024+2025 cộng lại | Dừng ở 20 h. Quay lại học **mẫu**: state machine, durable execution, ranh giới tool |
| **Certification cloud (AWS SA, Azure, GCP) trong 2 năm đầu** | Dạy API của một vendor trước khi bạn hiểu khái niệm bên dưới — đảo ngược §1.1 | Cân nhắc lại ở Phase 4, và chỉ khi một nhà tuyển dụng cụ thể yêu cầu tên cụ thể |
| **Thi đấu competitive programming ở mức sâu** | Lợi ích giảm rất nhanh sau khi qua phỏng vấn; luyện đúng thứ bạn không dùng | Trần 80 h tổng, rải trong Phase 1–2 |
| **Blockchain, distributed ledger** | Phần hữu ích trùng với C10; phần còn lại lệch hướng | — |
| **Quantum computing** | Không nằm trên đường tới bất kỳ hệ thống nào bạn xây trong 5 năm | — |
| **Tự cài thuật toán mật mã** | Phản mẫu về an toàn, không phải bài tập học tập | Học **cách dùng đúng** (S4.4) thay vì cách cài |
| **Proof assistant (Coq, Isabelle, Lean)** | Chi phí rất cao; không áp dụng được cho hệ có thành phần phi tất định | Awareness là đủ (S5.8) |
| **Đọc arXiv hàng ngày** | Tiêu thụ thay cho xây dựng | Đọc paper **nền** (danh sách ở §13); đọc paper mới khi có bài toán cụ thể |
| **Chạy theo framework frontend** | Đủ để dựng dashboard là dừng | Học một cái (HTMX hoặc React tối thiểu), không so sánh |
| **Tối ưu hóa micro trước khi có bottleneck thật** | Tối ưu sai chỗ là lãng phí thuần | C11.6 trước C3.8 |
| **Xây "AI platform" trước khi có dữ liệu thật** | Phản mẫu phổ biến nhất trong domain này | P3 trước P4. Thiết bị và dữ liệu trước, hạ tầng sau |
| **Học nhiều hơn 3 ngôn ngữ lập trình trong 5 năm** | Ngôn ngữ thứ tư là chi phí cơ hội thuần | C + Python + (Go hoặc Rust). Dừng |

## 12.2 — Hoãn, có mốc quay lại rõ ràng

| Thứ | Hoãn tới | Vì sao | Tín hiệu đã đến lúc |
|---|---|---|---|
| **Kubernetes ở mức vận hành** | Sau C10 đạt Intermediate | Học trước biến nó thành ma thuật cần thuộc lòng | Bạn giải thích được reconciliation loop trước khi chạm YAML |
| **Rust** | Phase 3 | Chi phí học cao; C dạy bạn nhiều hơn về phần cứng ở giai đoạn đầu | Bạn đã viết ≥2.000 dòng C và hiểu ownership bằng trực giác |
| **Đại số tuyến tính nâng cao (SVD, phân rã)** | Phase 3 | Không chặn gì trong Phase 1–2 | Bạn gặp PCA hoặc low-rank approximation trong công việc thật |
| **Laplace và hàm truyền** | Phase 3–4, chỉ nếu có actuation | PID dùng được trước khi hiểu Laplace | Bạn tune PID mà không hiểu vì sao nó dao động |
| **Compiler và lý thuyết ngôn ngữ** | Phase 4+, hoặc không bao giờ | Supporting, không chặn | Bạn cần viết toolchain cho một accelerator |
| **ROS 2 sâu** | Phase 4+ | Chỉ nếu thực sự rẽ sang robotics | Bạn quyết định spine SC-C ở §11.4 |
| **Huấn luyện model quy mô lớn** | **Không bao giờ**, trừ khi đổi mục tiêu | Bạn không có compute và không có lợi thế cạnh tranh ở đây | Chỉ khi bạn vào một tổ chức có cluster |
| **Formal verification** | Không có mốc | ROI quá thấp | Bạn làm giao thức đồng thuận hoặc hệ safety-critical được chứng nhận |
| **Thiết kế PCB nhiều lớp** | Phase 5+, tùy chọn | Module có sẵn đủ cho mọi thứ trong roadmap | Bạn cần tối ưu BOM cho sản xuất số lượng |
| **Đa vùng (multi-region)** | Phase 5 | Phức tạp bậc cao hơn multi-AZ, và bạn chưa có bài toán cần nó | P7a |

## 12.3 — Năm cạm bẫy đặc thù của chính domain này

### 1. Xây hạ tầng trước khi có dữ liệu
**Triệu chứng:** bạn có Kafka, có data lake, có dashboard — và ba hàng dữ liệu test.
**Vì sao nó hấp dẫn:** hạ tầng là phần bạn kiểm soát được hoàn toàn; dữ liệu thật thì lộn xộn và chậm.
**Sửa:** P3 (có thiết bị, có dữ liệu thật) trước P4 (hạ tầng). Thứ tự này trong §10 không phải ngẫu nhiên.

### 2. Bắt đầu bằng LLM
**Triệu chứng:** project đầu tiên của bạn là một chatbot có RAG.
**Vì sao nó hấp dẫn:** kết quả ấn tượng trong vài giờ.
**Vì sao nó nguy hiểm:** LLM ở tầng cao nhất của stack, nên nó **ngụy trang cho mọi lỗ hổng bên dưới**. Một hệ có LLM mà bạn không hiểu tầng mạng bên dưới là hệ bạn không debug được. Và khi nó hỏng ở production, nó hỏng ở tầng bạn không nhìn thấy.
**Sửa:** C8.11 nằm ở Phase 4 trong §5 vì lý do này.

### 3. Sưu tầm board
**Triệu chứng:** bạn có 8 board, mỗi cái chớp LED một lần.
**Vì sao nó hấp dẫn:** mua board rẻ và cho cảm giác tiến bộ.
**Sửa:** ba board dùng cạn giá trị tốt hơn mười board mỗi cái chạm một lần. Quy tắc: **không mua board mới cho tới khi board hiện tại đã chạy một project ≥30 ngày liên tục.**

### 4. Dashboard trước metric
**Triệu chứng:** Grafana đẹp, không trả lời được câu hỏi nào.
**Vì sao nó hấp dẫn:** dashboard là cách trì hoãn dễ chịu nhất trong nghề này — nó trông giống làm việc.
**Sửa:** thứ tự đúng là instrument → thu → **biết câu hỏi nào cần trả lời** → dashboard. Mỗi biểu đồ phải trả lời một câu hỏi cụ thể; nếu không, xóa.

### 5. Coi tutorial đã hoàn thành là kiến thức đã có
**Triệu chứng:** bạn "đã học" OS vì đã đọc hết OSTEP.
**Vì sao nó nguy hiểm:** cảm giác hiểu khi đọc rất khác năng lực làm. Bạn phát hiện ra khoảng cách này ở thời điểm tệ nhất — khi đang phỏng vấn hoặc khi hệ đang hỏng.
**Sửa:** **checkpoint ở §5 tồn tại chính xác vì lý do này.** Một nhánh chưa đạt checkpoint thì chưa xong, bất kể bạn đã đọc bao nhiêu.

## 12.3b — Ba cạm bẫy bổ sung cho người đang làm trong ngành công nghiệp

*Bổ sung ở v3. Ba cái này không có ở v2 vì chúng chỉ xuất hiện khi bạn đã ở trong một ngành.*

### 6. Để công việc định nghĩa phạm vi học
**Triệu chứng:** sau 2 năm, mọi thứ bạn học đều liên quan tới dự án được giao.
**Vì sao nguy hiểm:** công việc tối ưu cho *năng suất của công ty trong quý này*, không tối ưu cho *năng lực của bạn trong 10 năm*. Hai mục tiêu đó trùng nhau khoảng 40%, không phải 100%.
**Sửa:** ngân sách tự học phải đi vào nhánh **công việc không cho** (§9.2 quy tắc 2). Nếu tháng nào bạn thấy mình tự học đúng thứ đang làm ở công ty, tháng đó bạn mất ngân sách.

### 7. Nhầm kỹ năng vendor với kiến thức
**Triệu chứng:** bạn mô tả năng lực của mình bằng tên phần mềm.
**Vì sao nguy hiểm:** kỹ năng vendor mất giá khi bạn đổi ngành, và ngành công nghiệp đổi nền tảng khoảng 15–20 năm một lần — đủ chậm để bạn tưởng nó vĩnh viễn, đủ nhanh để nó xảy ra trong sự nghiệp bạn.
**Sửa:** bảng dịch ở §2.3d, làm hằng tuần. Kiểm tra: mô tả năng lực của bạn trong 3 câu **không dùng tên sản phẩm nào**. Nếu không làm được, bạn đang tích lũy kỹ năng chứ không tích lũy kiến thức.

### 8. Coi phía bên kia là ngu ngốc
**Triệu chứng đối xứng, cả hai đều phổ biến:**
- Phía OT nhìn phần mềm hiện đại: *"bọn nó deploy 10 lần một ngày, hệ thống nào chịu nổi"*
- Phía IT nhìn hệ công nghiệp: *"code này viết từ 2003, còn dùng Windows XP, sao chưa ai sửa"*

**Vì sao cả hai đều sai:** mỗi bên tối ưu cho ràng buộc bên kia chưa từng gặp. OT tối ưu cho vòng đời 20 năm, an toàn con người, và không được dừng. IT tối ưu cho tốc độ thay đổi, quy mô, và chi phí lỗi thấp. Cả hai đều đúng **trong ràng buộc của mình**.

**Vì sao nó quan trọng với riêng bạn:** giá trị của bạn nằm ở chỗ đứng giữa. Nếu bạn khinh một bên, bạn tự loại mình khỏi chính vị trí bạn đang xây. Và điều này khó hơn nó nghe — áp lực xã hội ở mỗi bên đều đẩy bạn về phía coi thường bên kia.

**Kiểm tra:** với mỗi thực hành bạn thấy vô lý ở một bên, tìm ra ràng buộc khiến nó hợp lý. Nếu không tìm được, bạn chưa hiểu bên đó đủ.

---


## 12.4 — Quy tắc quyết định khi gặp thứ mới không có trong roadmap

Bạn sẽ liên tục gặp công nghệ, framework, khái niệm mới. Dùng năm câu hỏi này, theo thứ tự:

```
1. Nó nằm ở tầng nào trong §8?
   → Tầng 1–3: đáng đầu tư
   → Tầng 4: học đủ dùng, trần 20 h
   → Tầng 5: đọc 2 giờ, ghi vào danh sách theo dõi
   → Tầng 6: đọc phần "cái còn lại có giá trị", bỏ phần còn lại

2. Nó thay thế hay bổ sung cho thứ tôi đã biết?
   → Thay thế: học nếu thứ cũ đang chặn tôi
   → Bổ sung: hoãn tới khi có bài toán cụ thể

3. Nếu nó biến mất sau 2 năm, tôi còn lại gì?
   → Còn nguyên lý: đáng học
   → Không còn gì: học đủ dùng, không hơn

4. Nó ở nhánh nào trong §5, và nhánh đó đang ở mức nào?
   → Nhánh đã đạt mức mục tiêu: bỏ qua
   → Nhánh chưa đạt: có thể là đường tắt

5. Tôi có bài toán thật cần nó không?
   → Có: học ngay, học đúng phần cần
   → Không: ghi vào danh sách, xem lại sau 3 tháng
```

Nếu một thứ không qua được cả 5 câu hỏi, câu trả lời là **không**. Đây là cơ chế bảo vệ chính của roadmap trước sự xao nhãng — và trong 5 năm, sự xao nhãng là kẻ thù lớn hơn sự khó khăn.

---
---

## ✎ Phần của tôi — theo dõi

| Thứ tôi quyết định bỏ | Ngày | Lý do | Mốc xem lại | Đã xem lại chưa |
|---|---|---|---|---|
|  |  |  |  | ☐ |

