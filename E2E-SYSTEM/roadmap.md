# ROADMAP — INTELLIGENT SYSTEMS INTEGRATION ENGINEERING

**Bản đầy đủ · 14/09/2026 · hiệu chỉnh cho tình huống đã đi làm**
**Domain gốc:** End-to-End Intelligent Systems Engineering
**Trạng thái:** hoàn chỉnh — 38 lĩnh vực, không nhánh nào bị nén, không mục nào cần zoom thêm

---

## MỤC LỤC

| § | Nội dung |
|---|---|
| 0 | Giả định đã chốt + ngân sách |
| 1 | Domain normalization |
| 2 | North Star + hiệu chỉnh thực tế |
| 3 | Knowledge universe — sweep 38 lĩnh vực |
| 4 | Dependency graph (2 tầng) |
| 5 | Knowledge tree phân rã đầy đủ (12 core · 8 supporting · 6 adjacent · 9 peripheral) |
| 6 | Depth map |
| 7 | Academic layer |
| 8 | Technology layer (6 tầng) |
| 9 | Kiến trúc 5 năm theo phase |
| 10 | Project progression — đặc tả đầy đủ |
| 11 | Scenarios + recommended path |
| 12 | Chủ động bỏ qua |
| 13 | Tài nguyên theo thứ tự học + ước lượng giờ |
| 14 | 90 ngày đầu |
| 15 | Coverage audit |
| 16 | Reassessment + STATE block |
| A | Bill of materials — phần cứng theo phase |
| B | Ngân sách giờ chi tiết |
| C | Master checklist — toàn bộ checkpoint |
| D | Bản đồ công việc ↔ roadmap · giờ quy đổi |

---

# 0. GIẢ ĐỊNH ĐÃ CHỐT VÀ TÌNH HUỐNG THỰC TẾ

| Hạng mục | Giá trị | Trạng thái |
|---|---|---|
| **Nghề nghiệp** | Kỹ sư tự động hóa, **đang thử việc** — IPC E&C, tổng thầu EPC năng lượng và công nghiệp | **ĐÃ XÁC NHẬN** |
| **Nội dung công việc** | Giai đoạn tìm hiểu. Hệ sinh thái hỗn hợp, nhiều **Siemens và ABB** | **ĐÃ XÁC NHẬN** |
| **Mô hình công ty** | Tổng thầu EPC: thiết kế → mua sắm → thi công → chạy thử → bàn giao. **Không làm O&M dài hạn** | **ĐÃ XÁC NHẬN** |
| **Đích đến** | **Liên ngành** — không giới hạn ở năng lượng, không thuần một mảng nào | **ĐÃ XÁC NHẬN** |
| Điểm xuất phát | Zero ở nhánh phần mềm/CS; **mới bắt đầu** ở nhánh tự động hóa | Suy ra từ "đang thử việc" |
| Thời gian tự học | **12–18 h/tuần** ngoài công việc → ~720 h/năm → **~3.600 h / 5 năm** | Ước tính, cần xác nhận |
| Giờ công việc quy đổi | **~2.100 h / 5 năm** ở các nhánh cụ thể — xem **Phụ lục D** | Ước tính |
| Phần cứng | Có mua, ngân sách mở | **ĐÃ XÁC NHẬN** |
| Vị trí | Hà Nội | |

---

## 0.1 — Nguyên tắc biên tập của bản v3

Bản v3 giữ **nguyên vẹn phạm vi** của v2: 38 lĩnh vực, 12 nhánh core, 8 supporting, 6 adjacent, 9 peripheral.

**Tình huống nghề nghiệp đổi ba thứ, và chỉ ba thứ:**

| Đổi | Không đổi |
|---|---|
| **Trình tự** — học gì trước, học gì sau | **Phạm vi** — vẫn đủ 38 lĩnh vực |
| **Phân bổ giờ** — nhánh nào tốn giờ tự học, nhánh nào công việc trả hộ | **Nhãn** core/supporting/adjacent/peripheral |
| **Chi phí** — một số nhánh rẻ đi đáng kể | **Gradient độ sâu** theo khoảng cách tới root |

**Lý do giữ nguyên nhãn:** tiêu chí gán nhãn ở §1.3a là *khoảng cách tới vòng lặp*. Tiêu chí đó là thuộc tính của **domain**, không phải của **người học**. Việc bạn đi làm ở ngành năng lượng không làm cho control theory gần vòng lặp hơn — nó chỉ làm cho việc học control theory **rẻ hơn** với bạn. Hai thứ đó khác nhau, và lẫn lộn chúng là cách nhanh nhất để biến một roadmap liên ngành thành một roadmap chuyên ngành mà không ai để ý.

**Cái được thêm vào** là kiến thức trước đây bị thiếu chứ không phải kiến thức được ưu ái: giao thức công nghiệp (C5.16), PLC/DCS như mô hình tính toán (C6.16), điều khiển quá trình công nghiệp (S3.8), mô hình ISA-95/Purdue (C12.15), an toàn OT theo IEC 62443 (S4.9). Đây là **lỗ hổng độ phủ của v2**, và chúng đáng được thêm vào kể cả nếu bạn làm nghề khác.

---

## 0.2 — Điều gì đổi so với v2

### (1) Ngân sách tự học giảm 45%, nhưng ngân sách hiệu dụng chỉ giảm 13%

| | v2 (chưa đi làm) | v3 (đã đi làm) |
|---|---|---|
| Tự học | 6.600 h | **3.600 h** |
| Công việc quy đổi | 0 | **~2.100 h** |
| **Hiệu dụng** | **6.600 h** | **~5.700 h** |

Giờ công việc quy đổi tập trung vào đúng những nhánh **đắt nhất khi tự học**: C7 (cần thiết bị và hiện tượng vật lý thật), S2 (cần mạch và tải thật), S3 (cần đối tượng điều khiển thật), C12 (cần hệ thống thật và người khác phản biện). Nên phân bố thực tế tốt hơn con số tổng gợi ý.

### (2) Mức Expert tụt từ 2–3 nhánh xuống 1–2 nhánh

Và ứng viên đổi. Ở v2 tôi dự kiến C6 hoặc C8. Giờ:

| Ứng viên | Lập luận |
|---|---|
| **C8 · ML & inference systems** | Nhánh tốn giờ tự học lớn nhất, công việc không cho gì, và là cung `learn/infer` mà cả công việc lẫn ngành OT đều đang thiếu |
| **C12 · Systems architecture** | Nhánh tổng hợp; công việc cho **thực hành** (tích hợp đa nhà thầu, commissioning xuyên tầng), tự học cho **từ vựng và khung** |
| C1 · Programming | Khả thi nhưng ít khác biệt hóa hơn hai cái trên |

**[Recommendation]** Chưa chốt bây giờ. Điểm rẽ nhánh ở §11.4 dịch sang **tháng 24–30**, sau khi bạn đã qua ít nhất một chu kỳ dự án EPC đầy đủ.

### (3) Khuyến nghị mạnh nhất của v2 đã hết hiệu lực

§2.3 của v2 dành nhiều chỗ lập luận cho *"đi làm từ tháng 12–15, không đợi học xong"*. **Vô nghĩa với bạn.** §11.2 của v2 — *"vào bằng software/infra, khác biệt hóa bằng edge + AI systems"* — cũng vậy: chiến lược đó tồn tại để giải bài toán "làm sao có việc", và bài toán đó đã xong.

Thay bằng §2.3 mới: **cái gì công việc cho, cái gì công việc không cho, và cái không cho phải mua ở đâu.**

### (4) Cung `observe → adapt` trở thành lỗ hổng nghiêm trọng, và nguồn bù đắp duy nhất là project cá nhân

Đây là hệ quả của việc công ty **không làm O&M dài hạn**. Phân tích đầy đủ ở §2.3.

Hệ quả cụ thể: yêu cầu "**chạy 30 ngày ngoài thực địa**" của P3 và "**90 ngày vận hành**" của P6 chuyển từ *nên có* thành **không thương lượng**. Ở v2 chúng là bài tập; ở v3 chúng là nguồn kinh nghiệm vận hành dài hạn duy nhất bạn có.

### (5) Timeline giãn ra

3.600 h ở 15 h/tuần × 48 tuần = đúng 5 năm cho phần tự học. Nhưng vì phải chờ công việc cấp kinh nghiệm ở một số nhánh, và vì giai đoạn thi công EPC có thể ăn hết năng lượng theo đợt, **kỳ vọng thực tế là 5–6,5 năm** thay vì 5 năm.

---

## 0.3 — Ràng buộc còn lại

| Ràng buộc | Mức độ | Xử lý |
|---|---|---|
| **Năng lượng sau giờ làm** | **Cao nhất** | Ràng buộc thật sự của v3, không phải tiền cũng không phải thiết bị. Xem §14.6 về nhịp độ |
| **Đợt thi công công trường** | Cao, theo chu kỳ | Có giai đoạn tự học sẽ về gần 0. Thiết kế roadmap chịu được điều đó: dùng khối dài ngày nghỉ, và chấp nhận tháng mất |
| GPU | Trung bình | Thuê theo giờ suốt Phase 1–3 (~0,2–0,6 USD/h lớp T4/A10). Chỉ mua khi chi phí thuê tháng vượt 1/24 giá máy |
| Truy cập dữ liệu vận hành thật | **Cao** | Công ty không làm O&M. Xem §2.3 về cách bù |

**[Recommendation] về năng lượng:** đừng cố giữ 15 h/tuần đều đặn. Thiết kế theo **tuần tốt và tuần xấu**: tuần tốt 20–25 h, tuần xấu 5 h. Trung bình vẫn ra 15. Cố ép đều là cách bỏ cuộc phổ biến nhất của người vừa đi làm vừa tự học.

---

## 0.4 — Giả định còn lại có thể sai

| Giả định | Nếu sai thì đổi gì |
|---|---|
| 12–18 h/tuần bền được | Nếu thực tế dưới 8 h/tuần trong ≥3 tháng: **thu hẹp phạm vi** theo thứ tự ở Phụ lục B.7, đừng kéo dài timeline |
| Qua thử việc và ở lại ≥2 năm | Nếu đổi việc sớm, xem lại §11.6 — mô hình công ty mới quyết định nhánh nào được trả hộ |
| Công việc sẽ cấp kiến thức OT theo thời gian | Nếu 12 tháng đầu chỉ làm giấy tờ và giám sát nhà thầu phụ, giờ quy đổi ở Phụ lục D phải cắt mạnh, và ngân sách tự học phải gánh thêm C7/S2/S3 |
| Bạn thật sự muốn liên ngành, không phải chuyên sâu | Nếu sau 2 năm bạn thấy mình muốn chuyên sâu một mảng, roadmap này vẫn dùng được — chỉ cần đọc §11.5 và đổi trọng số |
| Sức khỏe đủ cho công trường + tự học | Nếu không: giảm project phần cứng, tăng nhánh làm được trên laptop (C1, C2, C8, C10) |


# 1. DOMAIN NORMALIZATION

## 1.1 — Chẩn đoán domain bạn đưa

*"End-to-End Intelligent Systems Engineering"*, bao software + hardware + AI + automation + networking + infrastructure, **không phải một domain**. Nó là hợp của 4–5 domain cấp-sự-nghiệp.

Vấn đề kỹ thuật cụ thể: nếu giữ nguyên phát biểu này làm main root, **mọi nhánh đều cách root đúng một bước**, và §1.2 của prompt (gradient độ sâu theo khoảng cách tới main root) không còn tính được. Kết quả sẽ là một danh mục 38 nhánh cùng độ sâu — tức là không có kiến trúc.

## 1.2 — Main root sau chuẩn hóa

> **Intelligent Systems Integration Engineering**
>
> Kỹ thuật thiết kế, xây dựng và vận hành hệ thống có **vòng khép kín**:
>
> ```
> sense → transport → store → learn → infer → decide → act → observe → adapt
>   ↑                                                                    │
>   └────────────────────────────────────────────────────────────────────┘
> ```
>
> chạy trên hạ tầng thật, dưới ràng buộc **latency / power / cost / reliability**.

## 1.3 — Ba thao tác chuẩn hóa đã thực hiện

**(a) Thu hẹp bằng một trục, không bằng một danh sách cấm.**
Trục là vòng dữ liệu–quyết định–hành động ở trên. Tiêu chí phân loại dùng xuyên suốt §3 và §5:

| Vị trí so với vòng | Nhãn |
|---|---|
| Nằm **trên** vòng — là một mắt xích | core |
| Nằm **dưới** vòng — cung cấp nền để mắt xích hoạt động | supporting |
| Chạm vòng ở **đúng một điểm** | adjacent |
| Không chạm, nhưng hay bị nhầm là liên quan | peripheral |

Đây là tiêu chí khách quan, thay cho trực giác. Bạn có thể kiểm tra lại mọi nhãn ở §3 bằng chính tiêu chí này.

**(b) Xác định năng lực phân biệt.**
Cái tách bạn khỏi một backend engineer hoặc một ML engineer **không phải độ sâu trong một tầng**, mà là năng lực ở các **mối nối**:

- Thiết kế interface contract giữa hai tầng có mô hình lỗi khác nhau
- Định vị một triệu chứng về đúng tầng gây ra nó (triệu chứng ở tầng 7, nguyên nhân ở tầng 2)
- Nhìn ra trade-off toàn cục khi mỗi tầng đang tối ưu cục bộ
- Biết một đảm bảo (guarantee) bị phá vỡ ở đâu khi đi xuyên nhiều tầng

Đây là một discipline có tên trong công nghiệp — *systems integration* — không phải cách nói hoa mỹ cho "biết nhiều thứ".

**(c) Neo vào role có thật.**
Main root này ánh xạ vào: AI/ML platform engineer · edge AI engineer · IoT platform engineer · robotics systems engineer · forward-deployed engineer · platform/infra engineer · solutions architect.

Nó **không** ánh xạ vào *AI researcher*. Nếu đó là đích thật của bạn, roadmap này sai ở tầng kiến trúc và cần viết lại, không phải điều chỉnh.

## 1.4 — Cái đã cắt khỏi root và lý do

| Đã cắt | Lý do |
|---|---|
| Mechanical design, kinematics, dynamics ở độ sâu robotics thật | Là một spine riêng; thêm vào sẽ làm loãng cả hai |
| VLSI / ASIC design | Bạn dùng chip, không làm chip. Khoảng cách tới vòng là 2+ bước |
| RF & antenna design | Chuyên ngành riêng với công cụ riêng; dùng module đã chứng nhận là quyết định kỹ thuật đúng |
| Frontend/product UI ở độ sâu chuyên môn | Chạm vòng ở đúng một điểm (observe), và điểm đó chỉ cần Working |
| Compiler backend & codegen | Bạn cần hiểu *output* của compiler; viết compiler là domain khác |

Cả năm đều xuất hiện trong bảng sweep §3 với nhãn và lý do — cắt khỏi *root* không có nghĩa là xóa khỏi *danh mục*.

---

# 2. NORTH STAR + HIỆU CHỈNH THỰC TẾ

## 2.1 — North Star

Tự mình đưa được một hệ thống từ ý tưởng tới vận hành, gồm **tối thiểu**:

| Thành phần | Tiêu chí không thể thương lượng |
|---|---|
| Thiết bị cảm biến | Phần cứng thật, chạy ngoài bàn làm việc, ≥30 ngày không can thiệp tay |
| Đường truyền | Mạng không tin cậy thật — mất gói, mất kết nối dài, độ trễ biến thiên |
| Lưu trữ | Mô hình dữ liệu được **thiết kế**, có schema contract, có retention policy |
| Học | Model được đánh giá bằng eval set bạn tự dựng, có regression suite |
| Quyết định | Vòng quyết định tác động ngược lại thế giới vật lý hoặc một hệ thống khác |
| Quan sát | Đủ để bạn giải thích **vì sao** hệ thống hành xử như nó đang hành xử, bằng dữ liệu chứ không bằng đọc code |
| Trách nhiệm | Bạn bảo vệ được trade-off latency/cost/reliability của nó trước người khác, bằng số |

Và điều kiện bao trùm: **khi một thành phần hỏng, bạn biết ngay nó hỏng, biết vì sao, và hệ thống không hỏng theo.**

**North Star này không đổi theo tình huống nghề nghiệp.** Nó mô tả một năng lực, không mô tả một ngành.

---

## 2.2 — Hiệu chỉnh với ngân sách ~5.700 h hiệu dụng

**[Inference]** Tham chiếu: chương trình kỹ sư 4 năm + 3 năm đi làm ≈ 11.000–13.000 h *có cấu trúc, có mentor, có hệ thống production thật*. Bạn có ~45–50% ngân sách đó — nhưng **có hai trong ba thứ vừa kể ngay từ đầu**: cấu trúc (dự án EPC có deadline và nghiệm thu) và hệ thống thật (nhà máy đang được xây và chạy thử). Thứ còn thiếu là mentor cho nhánh phần mềm, và hệ thống *vận hành dài hạn*.

### Khả năng cao ĐẠT được sau 5–6 năm

| Mức | Số nhánh | Nhánh nào (dự kiến — chốt ở §11.4, tháng 24–30) |
|---|---|---|
| **Expert** — tự implement lại core components, đánh giá được thiết kế người khác, dạy lại được | **1–2** | C8 (ML & inference systems) hoặc C12 (systems architecture) |
| **Advanced** | **6–8** | C1, C5, C7, C10, C12, S3 và 2–3 trong nhóm C3/C4/C6/C9/C11 |
| **Intermediate** | 8–10 | Phần còn lại của core, cộng S1, S2, S4, S5, S6 |
| **Working / Basic** | phần còn lại | S7, S8, adjacent |

Năng lực tổng hợp dự kiến:
- Thiết kế và vận hành được hệ end-to-end quy mô trung bình, một mình
- **Debug xuyên tầng** — và ở bạn là xuyên cả tầng OT lẫn tầng IT, điều rất ít người làm được
- Đọc, phê bình và cải thiện được thiết kế của người khác ở cả hai thế giới
- Ước lượng được chi phí và độ trễ của một kiến trúc **trước khi** xây
- Dịch được bài toán từ ngôn ngữ ngành này sang ngôn ngữ ngành kia — **đây là năng lực liên ngành thật sự, và nó hiếm**

### Khả năng cao CHƯA đạt được

| Chưa đạt | Vì sao |
|---|---|
| Expert ở >2 nhánh | Ngân sách tự học 3.600 h không đủ cho ba nhánh cùng lúc |
| Viết kernel/OS component dùng được trong production | Cần 3–5 năm toàn thời gian đúng việc đó |
| Thiết kế PCB nhiều lớp cho tín hiệu tốc độ cao | Cần thiết bị đo chuyên dụng và vòng lặp fab |
| Train foundation model từ đầu | Cần compute ở mức triệu đô |
| Vận hành hệ phân tán quy mô nghìn node | Không tự tạo ra được |
| **Chịu trách nhiệm cho hệ safety-critical được chứng nhận** | Cần quy trình tổ chức, chứng chỉ, bảo hiểm trách nhiệm — không phải kiến thức. Bạn sẽ **tiếp xúc** với nó ở công việc nhưng ở vai trò khác |
| Chuyên gia đầu ngành ở bất kỳ nhánh nào | 5 năm là nhiều với một người, ít với một lĩnh vực |

---

## 2.3 — Công việc cho gì và không cho gì

Đây là mục thay thế cho "tại sao nên đi làm sớm" của v2. Bài toán đó đã xong; bài toán mới là **dùng công việc đúng cách**.

### (a) Công việc cho — và cho ở chất lượng tự học không đạt được

| Cái được | Nhánh | Vì sao tự học không thay được |
|---|---|---|
| **Hiện tượng vật lý ở quy mô thật** | C7, S2 | Nhiễu điện từ từ inverter, sụt áp trên đường dây dài, trôi cảm biến sau 6 tháng ngoài trời — không tái tạo được trên bàn |
| **Đối tượng điều khiển thật** | S3 | Điều khiển một lò, một turbine, một hệ phát điện có quán tính và có hậu quả. PID trên mô phỏng không dạy được cảm giác này |
| **Tích hợp đa nhà thầu, đa vendor** | C12.3 | Interface contract giữa hai hệ do hai công ty khác nhau làm, mỗi bên hiểu spec một kiểu — đây là **bài học đắt nhất của systems integration** và chỉ có ở công việc |
| **Commissioning — debug xuyên tầng dưới áp lực** | C11, C12.5 | Triệu chứng ở tầng SCADA, nguyên nhân ở đấu dây. Tìm ra trong 4 giờ vì có người đang chờ |
| **An toàn như ràng buộc thật** | S6, A5 | Không phải chương sách. Là thứ có người ký tên chịu trách nhiệm |
| **Ràng buộc tổ chức** | S8, A4 | Deadline, ngân sách, nhà thầu phụ trễ, thay đổi thiết kế giữa chừng |
| **Bề rộng** | C12, A4 | **EPC là lợi thế ít người nhận ra:** bạn thấy 10 nhà máy khác nhau trong 3 năm, thay vì 1 nhà máy trong 10 năm. Với đích liên ngành, đây là mô hình phơi nhiễm gần như lý tưởng |

### (b) Công việc KHÔNG cho — và đây là toàn bộ ngân sách tự học của bạn

| Không được | Nhánh | Hệ quả |
|---|---|---|
| Lập trình ở mức kỹ sư phần mềm | C1 | ST/ladder/FBD **không** thay được C và Python ở mức Advanced. Mô hình tư duy khác hẳn |
| Thuật toán và cấu trúc dữ liệu | C2 | Không có gì |
| Kiến trúc máy tính | C3 | Không có gì |
| Hệ điều hành và concurrency | C4 | Khái niệm real-time có giao, phần còn lại không |
| Machine learning và inference systems | C8 | **Không có gì — và đây là cung `learn/infer` của vòng lặp** |
| Data engineering hiện đại | C9 | Historian SCADA ≠ Kafka/Parquet/time-series store hiện đại |
| Hệ phân tán và cloud | C10 | Gần như không có gì |
| Observability tầng phần mềm | C11 | **Bẫy:** alarm management trong SCADA giải quyết cùng vấn đề mệt mỏi cảnh báo nhưng bằng từ vựng và công cụ khác hoàn toàn. Đừng nhầm cái bạn biết với cái roadmap yêu cầu |
| Thực hành phần mềm hiện đại | C1.10, C1.12, S5 | Git, CI, test tự động, code review, packaging — văn hóa OT bảo thủ với những thứ này, và có lý do chính đáng (vòng đời 20 năm, an toàn) |

### (c) Lỗ hổng nghiêm trọng nhất: cung `observe → adapt`

Công ty là **tổng thầu EPC, không làm O&M dài hạn**. Chu trình là thiết kế → thi công → chạy thử → bàn giao → rời đi.

Hệ quả, nói thẳng:

```
CUNG CỦA VÒNG LẶP        CÔNG VIỆC CHO?
─────────────────────────────────────────
sense                    ✓ mạnh
transport                ✓ mạnh (giao thức OT)
store                    ~ một phần (historian)
learn                    ✗ không
infer                    ✗ không
decide                   ✓ nhưng dựa trên luật cứng
act                      ✓ mạnh
observe                  ~ chỉ tới lúc bàn giao
adapt                    ✗ không
```

Bạn sẽ có **kinh nghiệm commissioning xuất sắc** và **không có kinh nghiệm vận hành dài hạn**. Đó là hai thứ khác nhau: cái đầu dạy bạn làm cho hệ chạy được; cái sau dạy bạn điều gì xảy ra với một hệ sau 18 tháng khi cảm biến trôi, khi phân phối dữ liệu dịch chuyển, khi người vận hành bắt đầu bỏ qua cảnh báo.

**Ba nguồn bù đắp, xếp theo mức khả thi:**

| Nguồn | Khả thi | Cách làm |
|---|---|---|
| **Project cá nhân vận hành dài** | **Cao — và là nguồn chính** | P3 chạy 30 ngày, P6 chạy 90 ngày. Ở v2 đây là bài tập; ở v3 đây là **nguồn kinh nghiệm vận hành duy nhất của bạn**. Không thương lượng |
| Xin tham gia giai đoạn bảo hành/khắc phục sau bàn giao | Trung bình | Nhà thầu EPC thường có nghĩa vụ bảo hành. Đó là cửa sổ hẹp vào giai đoạn vận hành — xin vào |
| Đổi sang nơi có vận hành | Thấp bây giờ, cân nhắc ở năm 3–5 | Xem §11.6. Không phải quyết định của hôm nay |

**[Recommendation]** Đừng coi lỗ hổng này là lý do để rời công việc. EPC cho bạn bề rộng mà nơi vận hành không cho. Hãy coi nó là **đặc tả yêu cầu cho project cá nhân**: cái gì công việc không dạy, project phải dạy.

### (d) Hệ sinh thái Siemens/ABB — cách không bị khóa

Bạn sẽ học TIA Portal, STEP 7, có thể PCS 7, và phía ABB là 800xA hoặc AC500. Những thứ này **có giá trị trong ngành và gần như không chuyển nhượng ra ngoài ngành**.

Thói quen rẻ, giá trị cộng dồn rất lớn: **với mỗi tính năng vendor bạn học, hỏi "khái niệm trung lập bên dưới là gì?"**

| Bạn thấy ở công việc | Khái niệm bên dưới | Nhánh |
|---|---|---|
| Scan cycle của PLC | Vòng lặp tất định, WCET, jitter | C4.10, C6.16 |
| Organization Block / ngắt chu kỳ | ISR, lập lịch rate-monotonic | C4.2, C6.2 |
| Hardware config, GSD/GSDML | Mô tả thiết bị, device tree | C4.12, C6.1 |
| Profinet IRT | Mạng thời gian thực, đồng bộ đồng hồ | C5.3, C7.9 |
| Faceplate, alarm class trong SCADA | Thiết kế cảnh báo, triệu chứng vs nguyên nhân | C11.11, A3 |
| Redundancy S7-400H / 800xA | Dự phòng nóng, split-brain, fencing | S6.3, C10.4 |
| Historian và trend | Lưu trữ chuỗi thời gian, downsampling | C9.5 |

Đây chính là §1.1 của prompt gốc — *nguyên lý trước công cụ* — áp vào đời sống hằng ngày. Làm được điều này thì 5 năm ở Siemens/ABB trở thành 5 năm học systems engineering. Không làm được thì nó là 5 năm học một phần mềm.

---

## 2.4 — Bối cảnh thị trường (Fact, 9/2026 — sẽ cũ)

Bạn đã có việc nên phần này đổi vai trò: không còn là chiến lược vào cửa, mà là **bối cảnh cho quyết định ở năm 3–5**.

| Dữ kiện | Hàm ý cho bạn |
|---|---|
| Entry-level AI engineer: ~2,5% tin tuyển nhắm 0–2 năm | Bạn đã tránh được cửa hẹp này. Khi bạn quay lại thị trường, bạn sẽ có 3–5 năm kinh nghiệm kỹ thuật thật |
| Backend/infrastructure vẫn đông nhất theo số lượng thô | Vẫn là mạng lưới an toàn nếu bạn muốn chuyển hẳn sang phần mềm |
| Agentic systems và forward-deployed engineering tăng nhanh nhất | Cả hai thưởng cho năng lực **tích hợp** hơn **modeling** — trùng với cả main root lẫn nghề hiện tại của bạn |
| Python ~61% tin tuyển AI engineering; cloud ~55%; CI/CD ~34% | Đây chính xác là danh sách công việc **không** cho bạn. Xác nhận ngân sách tự học nên đổ vào đâu |
| "Prompt engineer" đang biến mất khỏi chức danh | Đừng đầu tư vào thứ đang là chức danh; đầu tư vào thứ đang là năng lực |

**[Inference, độ tin cậy trung bình]** Hội tụ IT/OT là chỗ khan hiếm người có thật, và nó không phải hiện tượng riêng của năng lượng — nó xuất hiện ở sản xuất, hạ tầng, giao thông, nước, tòa nhà. Với đích **liên ngành** của bạn, vị trí hiện tại là một điểm đứng tốt chứ không phải một cái hộp: người biết cả hai thế giới có thể đi sang bất kỳ ngành nào có tài sản vật lý. Người chỉ biết một thế giới thì không.


# 3. KNOWLEDGE UNIVERSE — SWEEP 38 LĨNH VỰC

Tiêu chí gán nhãn: **khoảng cách tới vòng** `sense → transport → store → learn → infer → decide → act → observe → adapt` (§1.3a).

## 3.1 — 26 họ lĩnh vực bắt buộc

| # | Lĩnh vực | Nhãn | Vị trí trên vòng | Lý do |
|---|---|---|---|---|
| 1 | **Mathematics** | core (chọn lọc) | learn, infer, decide | Linear algebra + probability là ngôn ngữ của ML và ước lượng; discrete math là nền thuật toán; calculus/optimization chỉ tới mức hiểu gradient và hội tụ. Phần analysis, topology, abstract algebra không chạm vòng |
| 2 | **Physics & natural science** | supporting | dưới sense, act | Điện học, sóng/tín hiệu, nhiệt, năng lượng để hiểu sensor và giới hạn vật lý. Sinh–hóa–vật liệu không chạm vòng |
| 3 | **Electronics & circuits** | **core** (nâng từ supporting sau khi xác nhận phần cứng) | sense, act | Không đọc được datasheet, không hiểu nguồn và nhiễu thì cả hai đầu của vòng là đoán mò |
| 4 | **Computer architecture & digital logic** | core | infer, decide | Memory hierarchy, cache, SIMD, accelerator quyết định inference nhanh hay chậm. Đây là nơi mọi câu hỏi "vì sao chậm" kết thúc |
| 5 | **Embedded systems & firmware** | **core — spine** | sense, act, transport | Là điểm tiếp xúc giữa thế giới vật lý và phần mềm. Bỏ nó thì "end-to-end" mất hẳn một đầu |
| 6 | **Control theory & signal processing** | **core** (DSP) / **supporting** (control) | sense, act, decide | Sampling/aliasing/filtering cần ngay từ cảm biến đầu tiên; control theory cần khi xuất hiện actuation và feedback |
| 7 | **Robotics / mechatronics** | adjacent → **supporting** (nâng sau xác nhận phần cứng) | toàn vòng, dạng case study | Tích hợp sensing+control+planning là case study tốt nhất của domain. Cơ khí và dynamics ở độ sâu thật vẫn nằm ngoài spine |
| 8 | **Programming languages, compilers, runtimes** | core (ngôn ngữ + runtime) / supporting (compiler internals) | toàn vòng | Runtime và memory model quyết định hành vi hệ thống dưới tải. Compiler internals chỉ cần tới mức giải thích được vì sao code này nhanh hơn code kia |
| 9 | **Data structures & algorithms** | core | toàn vòng | Nền không thể bỏ, và đồng thời là cửa qua vòng phỏng vấn kỹ thuật |
| 10 | **Software engineering & design patterns** | core | toàn vòng | Hệ end-to-end chết vì coupling và vì không ai sửa nổi, sớm hơn nhiều so với chết vì thuật toán sai |
| 11 | **Operating systems & concurrency** | core | toàn vòng | Scheduling, memory, I/O, đồng bộ hóa là nơi trú ngụ của mọi bug khó nhất bạn sẽ gặp |
| 12 | **Networking** | core | transport | Mọi hệ end-to-end là hệ phân tán qua mạng không tin cậy. Nhánh bị đánh giá thấp nhất so với giá trị thật |
| 13 | **Distributed systems** | core | transport, store, decide | Partition, timeout, retry, idempotency, consistency chính là ngữ pháp của chữ "end-to-end" |
| 14 | **Databases & storage systems** | core | store | Mô hình dữ liệu và đảm bảo lưu trữ quyết định thứ bạn *được phép hứa* với người dùng |
| 15 | **Data engineering & pipelines** | core | transport, store, learn | Phần "intelligent" chạy bằng dữ liệu. Pipeline hỏng âm thầm là chuẩn mực, không phải ngoại lệ |
| 16 | **AI / ML / statistical learning** | core | learn, infer | Là nguồn của chữ "intelligent". Trọng tâm: inference & systems, không phải research |
| 17 | **Cloud & infrastructure** | core | store, infer, observe | Là nơi hệ thống thực sự sống |
| 18 | **DevOps / SRE / observability** | core | observe, adapt | Không quan sát được thì không debug được, mà "debug được" nằm trong chính định nghĩa mục tiêu |
| 19 | **Security & cryptography** | supporting, 4 sub-part core | toàn vòng | TLS, identity, secrets, device provisioning là bắt buộc. Crypto lý thuyết chỉ awareness |
| 20 | **Performance engineering** | core | infer, decide, observe | Trade-off latency/throughput/cost là nội dung chính của thiết kế hệ AI, không phải bước tối ưu cuối |
| 21 | **Testing, verification, formal methods** | supporting (testing gần core; formal methods awareness) | toàn vòng | Hệ có ML là hệ phi tất định — kỹ thuật test phải khác, và bạn phải biết *khác ở đâu* |
| 22 | **Systems architecture & design** | **core — đỉnh** | toàn vòng | Đây chính là năng lực đích, không phải một môn học riêng biệt |
| 23 | **HCI / UX** | adjacent | observe, decide | Hệ tự động nào cũng có điểm giao với người: khi nào hỏi người, hiển thị uncertainty ra sao, escalation path là gì |
| 24 | **Business, process & operations engineering** | adjacent | decide | "Nên tự động hóa cái gì" là quyết định kỹ thuật bị ràng buộc bởi quy trình |
| 25 | **Standards, compliance, regulation** | adjacent | toàn vòng, dạng ràng buộc | EU AI Act, bảo vệ dữ liệu, RF/EMC, functional safety — ảnh hưởng tới kiến trúc chứ không chỉ giấy tờ |
| 26 | **Economics of engineering** | supporting | decide | Cost-per-inference, build-vs-buy, capacity planning — phần bị bỏ qua nhiều nhất và là phần khiến một thiết kế đúng kỹ thuật bị bác bỏ |

## 3.2 — 12 lĩnh vực bổ sung ngoài danh sách 26

Đây là phần §5 của prompt kỳ vọng tôi đưa ra thứ bạn chưa nghĩ tới.

| # | Lĩnh vực | Nhãn | Vì sao nó tồn tại riêng, không gộp vào họ nào ở trên |
|---|---|---|---|
| 27 | **Reliability & safety engineering** (FMEA, fault tree, redundancy, MTBF, dự phòng) | supporting | SRE (#18) nói về *vận hành*; cái này nói về *thiết kế để hỏng có kiểm soát*. Hệ có actuation bắt buộc phải có. Đây là hai body of knowledge khác nhau với lịch sử khác nhau (hàng không/hạt nhân vs web) |
| 28 | **Queueing theory & capacity planning** | supporting | Là cơ sở *toán* của tail latency — nằm dưới #20 nhưng không được dạy trong performance engineering thực hành. Trả lời "cần bao nhiêu máy" bằng mô hình thay vì cảm giác |
| 29 | **Information theory** | supporting | Entropy, channel capacity, rate–distortion nối liền **nén dữ liệu, truyền tin, và cross-entropy loss** — ba thứ trông rời nhau nhưng cùng một gốc. Không họ nào ở trên chứa cả ba |
| 30 | **Numerical methods & floating-point** | supporting | Quantization, ổn định số, mixed precision — nơi model ở edge sai một cách **âm thầm**. Toán (#1) không dạy, ML (#16) giả định bạn biết |
| 31 | **Metrology, sensor science & calibration** | supporting | Hầu như không giáo trình nào dạy. Là nguồn của lỗi "garbage in" mà không mô hình nào cứu được. Điện tử (#3) dạy mạch, DSP (#6) dạy xử lý — không ai dạy *làm sao biết số đo này đúng* |
| 32 | **Time & synchronization** (clock drift, NTP/PTP, căn chỉnh timestamp) | supporting | Hệ phân tán (#13) và sensor fusion (#6) **đều** chết vì đồng hồ, nhưng mỗi bên chỉ dạy nửa vấn đề. Đủ quan trọng để tách riêng |
| 33 | **Simulation & digital twins** | adjacent | Cách duy nhất để test hệ vật lý ở quy mô và test kịch bản không tạo lại được ngoài đời |
| 34 | **Human factors of automation** (autonomy levels, mode confusion, automation surprise) | adjacent | Failure mode **đặc thù của hệ thông minh**. Phần lớn tai nạn hệ tự động nằm ở giao diện người–máy, không ở thuật toán. HCI (#23) dạy giao diện, không dạy cái này |
| 35 | **Technical writing & design documentation** (RFC, ADR, postmortem) | supporting | Là công cụ **tư duy** kiến trúc, không phải kỹ năng mềm. Không viết được thì chưa thiết kế xong |
| 36 | **Licensing, IP & data rights** | adjacent | Quyết định bạn **được phép ship cái gì**. Sai thì phải viết lại, không phải xin lỗi. Đặc biệt gay gắt với model và dataset |
| 37 | **Energy & power engineering** (power budget, pin, nhiệt) | **core** (nâng sau xác nhận phần cứng) | Ràng buộc **cứng** của mọi thiết bị không cắm điện và của mọi compute ở edge. Quyết định kiến trúc duty-cycle của cả hệ |
| 38 | **Supply chain & component lifecycle** (DFM, EOL parts, lead time) | peripheral | Chỉ quan trọng khi sản xuất số lượng thật. Nhưng **EOL part** thì nên biết sớm: chọn con chip sắp ngừng sản xuất là lỗi đắt |

## 3.3 — Nhãn "không liên quan"

Với main root này, **không họ nào rơi vào "không liên quan" hoàn toàn**. Bản thân điều đó xác nhận chẩn đoán ở §1.1: domain gốc quá rộng. Nên tôi loại ở tầng **sub-part**:

| Bị loại | Thuộc họ | Lý do — nói rõ |
|---|---|---|
| Sinh học, hóa học, khoa học vật liệu | #2 | Không chạm vòng ở bất kỳ điểm nào. Ngoại lệ duy nhất: nếu bạn rẽ sang biomedical devices, lúc đó viết lại roadmap |
| VLSI/ASIC design, layout, timing closure | #4 | Khoảng cách tới vòng ≥2 bước. Bạn dùng chip |
| Analog/RF design, antenna, PCB tốc độ cao nhiều lớp | #3 | Cần thiết bị đo (VNA, scope ≥1GHz) và vòng lặp fab mà bạn không có. Dùng module đã chứng nhận |
| Kinematics, dynamics, mechanical CAD | #7 | Chỉ vào nếu đổi spine sang robotics. Hiện là chi phí cơ hội thuần |
| Formal verification bằng proof assistant (Coq, Isabelle, Lean) | #21 | ROI cực thấp với hệ chứa thành phần phi tất định. Bạn không chứng minh được tính đúng của một mạng neural |
| Compiler frontend/backend, codegen, optimization passes | #8 | Bạn cần hiểu *output*, không cần viết nó |
| Frontend framework ecosystem (React/Vue/Svelte ở độ sâu) | #23 | Đủ để dựng dashboard là dừng |
| Marketing, sales, tài chính doanh nghiệp | #24 | Ngoài phạm vi kỹ thuật; học khi cần, không học trước |
| Lý thuyết trò chơi, cơ chế đấu giá | #26 | Chỉ liên quan nếu làm hệ multi-agent có cạnh tranh — chưa phải bài toán của bạn |

## 3.4 — Bảng tổng hợp phân bổ

| Nhãn | Số nhánh | % ngân sách giờ | Mức mục tiêu trung bình |
|---|---|---|---|
| **Core** | 12 | ~64% (≈4.270 h) | Advanced, 2–3 nhánh chạm Expert |
| **Supporting** | 8 | ~14% (≈900 h) | Working–Intermediate |
| **Adjacent** | 6 | ~4,5% (≈300 h) | Basic–Working |
| **Peripheral** | 9 | ~0% | Awareness |
| **Project tích hợp** (vượt ngoài giờ nhánh) | — | ~15% (≈1.000 h) | — |
| **Slack, review, viết lách** | — | ~3% (≈200 h) | — |

Chi tiết từng nhánh ở **Phụ lục B**.

---

## 3.5 — Bản đồ: lĩnh vực nào công việc cấp, lĩnh vực nào phải tự mua

**Bảng này KHÔNG đổi nhãn ở §3.1 và §3.2.** Nhãn phản ánh khoảng cách tới vòng lặp — thuộc tính của domain. Bảng này phản ánh **chi phí thu nhận** — thuộc tính của hoàn cảnh bạn. Hai trục độc lập.

| Lĩnh vực | Nhãn (không đổi) | Công việc cấp | Phải tự mua |
|---|---|---|---|
| 1 Mathematics | core | — | **Toàn bộ** |
| 2 Physics & natural science | supporting | Điện, nhiệt, năng lượng ở mức ứng dụng | Sóng/tín hiệu ở mức toán |
| 3 Electronics & circuits | core | **Phần lớn** — mạch thật, tủ thật, đo thật | Điện tử số mức MCU |
| 4 Computer architecture | core | — | **Toàn bộ** |
| 5 Embedded & firmware | core | Tư duy thời gian thực, I/O, tất định (qua PLC) | Firmware MCU, bare-metal, RTOS, OTA |
| 6 Control & signal processing | core/supporting | **Control: phần lớn** | **DSP: toàn bộ** |
| 7 Robotics / mechatronics | supporting | Một phần (actuation, an toàn máy) | Perception, planning, SLAM |
| 8 Programming languages & runtimes | core | Rất ít (ST/ladder ≠ C/Python) | **Gần như toàn bộ** |
| 9 Data structures & algorithms | core | — | **Toàn bộ** |
| 10 Software engineering | core | — | **Toàn bộ** |
| 11 OS & concurrency | core | Khái niệm real-time | Phần còn lại |
| 12 Networking | core | **Giao thức công nghiệp** | TCP/IP, HTTP, mạng cloud |
| 13 Distributed systems | core | — | **Toàn bộ** |
| 14 Databases & storage | core | Historian ở mức người dùng | **Gần như toàn bộ** |
| 15 Data engineering | core | Rất ít | **Gần như toàn bộ** |
| 16 AI / ML | core | — | **Toàn bộ** |
| 17 Cloud & infrastructure | core | — | **Toàn bộ** |
| 18 DevOps / SRE / observability | core | Alarm management (từ vựng khác) | **Gần như toàn bộ** |
| 19 Security & cryptography | supporting | An ninh OT khi gặp | Phần IT, crypto, ML security |
| 20 Performance engineering | core | — | **Toàn bộ** |
| 21 Testing & verification | supporting | FAT/SAT, nghiệm thu | Test tự động, CI, test hệ phi tất định |
| 22 Systems architecture | core | **Thực hành** — tích hợp đa bên, commissioning | **Từ vựng và khung** — pattern, ADR, đánh đổi |
| 23 HCI / UX | adjacent | HMI, thiết kế màn hình vận hành | Human factors lý thuyết |
| 24 Business & operations | adjacent | **Phần lớn** — quy trình, tiến độ, nhà thầu | ROI kỹ thuật, tự động hóa cái gì |
| 25 Standards & regulation | adjacent | **Phần lớn** — grid code, tiêu chuẩn thiết bị | EU AI Act, bảo vệ dữ liệu |
| 26 Economics of engineering | supporting | Ngân sách dự án | Cost-per-inference, TCO phần mềm |
| 27 Reliability & safety | supporting | **Phần lớn** — bảo vệ, interlock, an toàn | FMEA có hệ thống, SRE |
| 28 Queueing & capacity | supporting | — | **Toàn bộ** |
| 29 Information theory | supporting | — | **Toàn bộ** |
| 30 Numerical & floating-point | supporting | — | **Toàn bộ** |
| 31 Metrology & calibration | supporting | **Phần lớn** — hiệu chuẩn thiết bị thật | Bất định đo ở mức toán |
| 32 Time & synchronization | supporting | Một phần (đồng bộ trong mạng công nghiệp) | NTP/PTP, thời gian phân tán |
| 33 Simulation & digital twins | adjacent | Một phần (mô phỏng trước commissioning) | Dữ liệu tổng hợp, sim-to-real |
| 34 Human factors of automation | adjacent | **Phần lớn** — quan sát người vận hành thật | Lý thuyết, autonomy levels |
| 35 Technical writing | supporting | **Phần lớn** — spec, báo cáo, nghiệm thu | ADR, RFC, postmortem |
| 36 Licensing & IP | adjacent | Rất ít | **Gần như toàn bộ** |
| 37 Energy & power | core | **Phần lớn** | Power budget cho thiết bị nhỏ |
| 38 Supply chain | peripheral | Một phần (mua sắm trong EPC) | — |

**Đọc bảng này thế nào:** cột "phải tự mua" là **đặc tả yêu cầu cho 3.600 h tự học**. Mọi ô ghi "toàn bộ" hoặc "gần như toàn bộ" đều thuộc nhóm ưu tiên cao nhất ở §9.2 quy tắc 2 — vì nếu bạn không tự học thì không có nguồn nào khác, mãi mãi.

**Cảnh báo về chữ "công việc cấp":** nó có nghĩa *có cơ hội học*, không có nghĩa *tự động học được*. Cơ hội chỉ thành kiến thức nếu bạn áp dụng thói quen dịch sang khái niệm trung lập ở §2.3d. Hai người cùng làm một dự án, một người ra với kiến thức chuyển nhượng được, người kia ra với kỹ năng bấm nút — khác biệt nằm ở thói quen đó.

---


# 4. DEPENDENCY GRAPH

## 4.1 — Tầng 1: graph cấp nhánh

Chỉ vẽ dependency **thực sự chặn**: thiếu node cha thì học node con là *lãng phí*, không phải chỉ là *khó hơn*.

```
                        Programming (C + Python)
                                  │
            ┌─────────────────────┼─────────────────────┐
            ↓                     ↓                     ↓
   Data Structures         Computer Arch.          Math nền
    & Algorithms          & Digital Logic     (Discrete, LA, Prob)
            │                     │                     │
            └──────────┬──────────┘                     │
                       ↓                                │
          Operating Systems & Concurrency                │
                       │                                │
     ┌─────────────────┼──────────────────┐             │
     ↓                 ↓                  ↓             ↓
Networking     Embedded/Firmware    Databases &    ML fundamentals
     │                 │              Storage            │
     │                 ↓                  │              ↓
     │      Sensing / DSP / Power         │      Inference systems
     │                 │                  │      (serving, quantize,
     │                 ↓                  │       batching, KV cache)
     │           Control & Actuation      │              │
     ↓                 │                  ↓              │
Distributed Systems ←──┴────→ Data Engineering ←─────────┘
     │                              │
     └──────────────┬───────────────┘
                    ↓
      Cloud & Infra + DevOps/Observability
                    ↓
    Performance  ·  Security  ·  Reliability
                    ↓
          Systems Architecture
                    ↓
   ╔════════════════════════════════════════╗
   ║   END-TO-END INTELLIGENT SYSTEM        ║
   ║   sense → transport → store → learn →  ║
   ║   infer → decide → act → observe →     ║
   ║   adapt                                ║
   ╚════════════════════════════════════════╝
```

## 4.2 — Tầng 2: dependency chi tiết ở các mối nối quan trọng

Ba mối nối hay bị làm sai nhất, vẽ riêng:

### Mối nối A — từ vật lý tới số

```
 Vật lý thật
     │
     ├─ Ohm's law, công suất, tụ điện ──────┐
     │                                      ↓
     ├─ Đọc datasheet ────────────→  Chọn cảm biến
     │                                      ↓
     │                              Mạch điều hòa tín hiệu
     │                                      ↓
     └─ Nhiễu, ground, EMI ────────→   ADC (bit, tần số,
                                        ENOB thực tế)
                                            ↓
                          Định lý lấy mẫu ← Aliasing
                                            ↓
                                     Lọc số (FIR/IIR)
                                            ↓
                                   Hiệu chuẩn (offset,
                                    gain, drift, nhiệt)
                                            ↓
                              ★ DỮ LIỆU ĐÁNG TIN ★
                                            ↓
                              (chỉ tới đây ML mới có nghĩa)
```

**[Quan trọng]** Mọi tầng ML phía trên đặt trần bởi chất lượng ở mối nối này. Một model tốt trên dữ liệu chưa hiệu chuẩn vẫn cho kết quả sai — và sai theo cách bạn không phát hiện được từ metric.

### Mối nối B — từ thiết bị tới đám mây

```
Thiết bị (có thể mất điện, mất mạng, sai giờ)
     │
     ├─ Bộ đệm cục bộ (store-and-forward) ─────┐
     ├─ Timestamp cục bộ + clock drift ────────┤
     ├─ Định danh thiết bị + khóa ─────────────┤
     └─ Chính sách retry + backoff ────────────┤
                                               ↓
                            Giao thức (MQTT/CoAP/HTTP/gRPC)
                                     + QoS level
                                               ↓
                                    Gateway / broker
                                               ↓
                            ★ RANH GIỚI IDEMPOTENCY ★
                              (dedup key, thứ tự, backfill)
                                               ↓
                                     Stream / hàng đợi
                                               ↓
                            Xử lý + schema contract
                                               ↓
                                   Lưu trữ (time-series,
                                    object, quan hệ)
```

**[Quan trọng]** "Exactly-once" là **hợp đồng end-to-end**, không phải tính năng của broker. Nếu bạn không thiết kế dedup key ở tầng ứng dụng, không cấu hình nào ở tầng broker cứu được bạn.

### Mối nối C — từ model tới hệ thống

```
Model đã train
     │
     ├─ Eval set (bạn tự dựng, biết nó KHÔNG đo được gì)
     ├─ Quantization (PTQ/QAT) → đo lại độ chính xác
     ├─ Format chuyển đổi (ONNX / TFLite / engine riêng)
     └─ Ngân sách: RAM, latency, năng lượng
                          ↓
              ★ RANH GIỚI TRIỂN KHAI ★
                          ↓
     ┌────────────────────┼────────────────────┐
     ↓                    ↓                    ↓
 Trên thiết bị      Serving cloud        Gọi API bên thứ 3
 (TFLite Micro,    (vLLM, batching,     (rate limit, chi phí,
  operator          KV cache, GPU)        thay đổi model)
  coverage)              │                     │
     └────────────────────┼────────────────────┘
                          ↓
              Tầng chính sách (policy layer)
        • giới hạn hành động  • ngưỡng tin cậy
        • fallback khi model im lặng  • human-in-the-loop
                          ↓
                  Hành động thật
                          ↓
              Quan sát + phát hiện drift
                          ↓
                   (quay lại train)
```

**[Quan trọng]** Tầng chính sách là thứ phân biệt một hệ thống với một demo. Đưa output của model trực tiếp tới actuator là phản mẫu phổ biến nhất trong edge AI.

## 4.3 — Dependency thật vs dependency tưởng tượng

### Chặn thật — đừng đảo thứ tự

| Trước | Sau | Vì sao chặn |
|---|---|---|
| C (con trỏ, bộ nhớ) | Computer architecture | Không biết con trỏ thì memory hierarchy chỉ là chữ |
| DSA + Computer arch | Operating systems | Scheduler là cấu trúc dữ liệu; virtual memory là ánh xạ |
| OS (process, I/O, syscall) | Networking | Socket, blocking I/O, event loop là khái niệm OS trước khi là khái niệm mạng |
| Networking | Distributed systems | Không có mạng thì partition và timeout không có nghĩa |
| Linear algebra + xác suất | Machine learning | Dependency toán **duy nhất** thực sự chặn |
| OS + Computer arch | Performance engineering | Không có hai cái này thì "tối ưu" là đoán |
| Điện tử cơ bản + datasheet | Embedded | Không đọc được datasheet thì mọi ví dụ là cargo cult |
| Định lý lấy mẫu | Mọi việc đọc cảm biến | Aliasing tạo dữ liệu sai mà nhìn vẫn hợp lý |
| Đồng hồ & đồng bộ | Sensor fusion + hệ phân tán | Cả hai sụp đổ nếu timestamp sai |
| Eval + metric | Bất kỳ quyết định nào về model | Không có eval thì "cải thiện" là cảm giác |

### Bị coi là chặn nhưng không phải — đừng để nó trì hoãn bạn

| Niềm tin sai | Thực tế |
|---|---|
| Học hết toán rồi mới làm ML | Chạy song song. Cần đúng 2 thứ trước khi bắt đầu: nhân ma trận, và xác suất có điều kiện |
| Compiler trước systems | Compiler là supporting, vào rất muộn hoặc không vào |
| Lý thuyết mạch trước embedded | Cần Ohm's law + đọc datasheet. Không cần phân tích mạch xoay chiều |
| Kubernetes trước distributed systems | **Đảo ngược và tai hại.** K8s là *một hiện thực* của control loop; học trước biến nó thành ma thuật cần thuộc lòng |
| Deep learning trước classical ML | Bạn sẽ không nhận ra khi nào bài toán không cần neural network — và phần lớn bài toán không cần |
| Học framework trước khi tự viết | Ngược §1.1 của chính bạn. Tự viết TCP server trước, rồi mới dùng framework |
| Cần GPU mới học được ML | Sai ở Phase 1–2. Toàn bộ classical ML và nền neural network chạy tốt trên CPU |
| Cần bằng cấp mới làm được | Sai với role tích hợp; đúng với research. Xem §11 |
| Phải học "AI" trước vì nó hot | Đảo ngược: AI là tầng cao nhất, nó ngụy trang cho mọi lỗ hổng bên dưới |

---

# 5. KNOWLEDGE TREE — PHÂN RÃ ĐẦY ĐỦ

**Ký hiệu mức:** `Aw` awareness · `Ba` basic · `Wo` working · `In` intermediate · `Ad` advanced · `Ex` expert

**Cách đọc:** mỗi nhánh core được phân rã 3 tầng — nhánh → leaf → sub-leaf. Checkpoint đặt ở tầng leaf (tầng sub-leaf quá mịn để kiểm chứng riêng lẻ). Mỗi leaf có thêm mục *Cạm bẫy* — đây là chỗ người tự học hay mất nhiều tháng nhất.

---

## 5.1 — CORE · 12 NHÁNH

---

# ◆ C1 · PROGRAMMING & LANGUAGE RUNTIMES

**Mức mục tiêu:** Advanced → **Expert** (một trong 2–3 nhánh chạm Expert)
**Ngân sách:** ~450 h · Phase 0–1: 260 h · Phase 2: 100 h · Phase 3–5: 90 h rải
**Vị trí:** gốc của dependency graph. Chặn mọi thứ.
**Vì sao mức này:** đây là công cụ bạn dùng mỗi ngày ở 11 nhánh còn lại. Dưới Advanced thì mọi nhánh khác bị chặn tốc độ; ở Expert thì mọi nhánh khác được tăng tốc.

## C1.1 · C như ngôn ngữ hệ thống — `Ad→Ex`

**Sub-leaves:**
- Cú pháp, kiểu, storage class, scope, linkage
- Con trỏ: số học con trỏ, con trỏ hàm, con trỏ nhiều cấp, `void*`
- Mảng vs con trỏ — sự khác nhau thật, array decay
- Struct: padding, alignment, packed struct, bit field
- Union và type punning (và vì sao nó là undefined behavior trong nhiều trường hợp)
- Quản lý bộ nhớ thủ công: `malloc`/`free`, arena allocator, pool allocator, cấp phát tĩnh
- Chuỗi trong C và lý do nó là nguồn lỗi bảo mật số một
- Preprocessor: macro, include guard, conditional compilation, `X-macro`
- `const`, `volatile`, `restrict`, `static` — ngữ nghĩa thật của từng cái
- Undefined behavior: danh sách các UB hay gặp và cách compiler khai thác chúng
- Chuẩn C99/C11/C17 — khác biệt thực tế
- Quy ước gọi hàm và ABI
- Inline assembly ở mức đọc được

**Dùng để xây:** toàn bộ C6 (firmware), phần lớn C4 (OS), công cụ đo trong C11.

**Checkpoint:** viết ring buffer + state machine **không dùng cấp phát động**, không leak, sạch dưới `valgrind` và `-fsanitize=address,undefined`; giải thích được padding của mọi struct bạn định nghĩa mà không cần chạy `sizeof`.

**Cạm bẫy:** học C bằng cách viết C++ có bớt tính năng. C có mô hình tư duy riêng (bộ nhớ là mảng byte phẳng, bạn chịu trách nhiệm cho mọi thứ). Nếu bạn thấy mình nhớ Python, bạn đang học sai.

## C1.2 · Python như ngôn ngữ dán và ngôn ngữ ML — `Ad`

**Sub-leaves:**
- Mô hình dữ liệu: `__dunder__`, protocol, duck typing, descriptor
- Iterator, generator, coroutine, `async`/`await`
- Context manager và quản lý tài nguyên
- Decorator và metaclass ở mức đọc được thư viện người khác
- Type hints, `typing`, `Protocol`, generic, và `mypy`/`pyright`
- Packaging hiện đại: `pyproject.toml`, virtualenv, `uv`/`pip`, versioning
- Testing: `pytest`, fixture, parametrize, mock, coverage
- Hiệu năng: vì sao Python chậm, khi nào nó không chậm, `numpy` vectorization
- C extension và FFI: `ctypes`, `cffi`, khái niệm `Cython`/`pybind11`
- GIL: ý nghĩa thật, tác động tới threading vs multiprocessing, và trạng thái free-threaded
- Logging, cấu hình, CLI (`argparse`/`click`)
- Chuẩn code: `ruff`, formatter, pre-commit hook

**Dùng để xây:** C8 (ML), C9 (pipeline), toàn bộ tooling và automation.

**Checkpoint:** ship một package có test ≥80% coverage, type hints đầy đủ pass `mypy --strict`, cài đặt được bằng `pip install .` từ repo sạch, có CLI, có logging cấu hình được. **Không dùng notebook trong toàn bộ package.**

**Cạm bẫy:** dừng ở mức "viết script chạy được". Khoảng cách giữa *script* và *package bảo trì được* lớn hơn khoảng cách giữa *không biết Python* và *viết được script*.

## C1.3 · Ngôn ngữ compiled thứ ba: Go **hoặc** Rust — `In→Ad`

**Sub-leaves nếu chọn Go:** goroutine và scheduler · channel và select · `context` và hủy bỏ · interface và composition · lỗi như giá trị · `net/http` và viết server thật · profiling built-in (`pprof`) · module và build · cross-compile

**Sub-leaves nếu chọn Rust:** ownership, borrow, lifetime · trait và generic · `Result`/`Option` và toán tử `?` · `unsafe` và khi nào chính đáng · `no_std` cho embedded · async và runtime · cargo và ecosystem · FFI với C

**Dùng để xây:** service backend hiệu năng cao (Go), hoặc firmware an toàn bộ nhớ (Rust).

**Checkpoint:** port một service từ Python sang, đo được chênh lệch p50/p99 latency và mức dùng bộ nhớ, và giải thích được chênh lệch đó đến từ đâu về mặt runtime.

**[Recommendation]** Chốt ở Phase 3, không sớm hơn: **Go** nếu spine nghiêng cloud (thời gian học ngắn, ecosystem hạ tầng mạnh), **Rust** nếu nghiêng edge (thay được C ở nơi an toàn bộ nhớ quan trọng). Không học cả hai trong 3 năm đầu — đó là chi phí cơ hội thuần.

## C1.4 · Mô hình bộ nhớ — `Ad→Ex`

**Sub-leaves:**
- Bố cục tiến trình: text, data, bss, heap, stack, mmap
- Stack frame, calling convention, stack overflow, đo stack usage
- Heap: allocator hoạt động thế nào, fragmentation, `mmap` vs `brk`
- Alignment và tại sao unaligned access hoặc chậm hoặc crash
- Lifetime: ai sở hữu, ai giải phóng, use-after-free, double-free
- Ownership model ở ba ngôn ngữ: thủ công (C), GC (Python/Go), compile-time (Rust)
- Cấp phát tĩnh cho hệ nhúng và vì sao production firmware tránh heap
- Memory-mapped I/O và `volatile`

**Dùng để xây:** mọi thứ. Đây là leaf có hệ số nhân cao nhất trong nhánh.

**Checkpoint:** đọc core dump và giải thích được nguyên nhân một segfault; tính được worst-case stack usage của một firmware và chứng minh nó không tràn.

**Cạm bẫy:** nghĩ rằng ngôn ngữ có GC miễn cho bạn khỏi việc hiểu bộ nhớ. Sai — nó chỉ dời vấn đề sang latency của GC và pattern giữ tham chiếu.

## C1.5 · Type system & thiết kế interface — `In→Ad`

**Sub-leaves:**
- Static vs dynamic, strong vs weak — bốn trục độc lập
- Kiểu tổng và kiểu tích (sum/product type), pattern matching
- Generic và parametric polymorphism
- Variance (covariant/contravariant) ở mức trực giác
- Interface tối thiểu: thiết kế API mà dùng sai thì compile fail
- Làm trạng thái không hợp lệ trở nên không biểu diễn được (*make illegal states unrepresentable*)
- Contract: precondition, postcondition, invariant
- Versioning API và tương thích ngược/tiến

**Dùng để xây:** C12 (architecture), mọi ranh giới giữa các component.

**Checkpoint:** thiết kế một API mà một người dùng sai sẽ bị compiler hoặc type checker chặn, chứ không phải bị lỗi runtime. Chứng minh bằng cách viết code sai cố ý và cho thấy nó không build.

## C1.6 · Error handling & ngữ nghĩa lỗi — `Ad`

**Sub-leaves:**
- Ba mô hình: mã trả về, exception, kiểu Result
- Phân loại lỗi: tạm thời vs vĩnh viễn, của mình vs của người khác, lập trình vs vận hành
- Chiến lược: retry, fail fast, degrade, escalate — chọn cái nào khi nào
- Retry với exponential backoff + jitter, và vì sao thiếu jitter gây retry storm
- Circuit breaker và bulkhead ở mức code
- Ngữ cảnh lỗi: bọc lỗi mà không mất nguyên nhân gốc
- Panic/abort vs xử lý được — ranh giới đặt ở đâu
- Lỗi ở ranh giới hệ thống: mã trạng thái, lỗi có cấu trúc, idempotency

**Dùng để xây:** C10, C11, mọi ranh giới trong hệ end-to-end.

**Checkpoint:** cho một hệ có 5 dependency ngoài, viết ra bảng: mỗi dependency × (hỏng cách nào) × (hành vi mong muốn) × (cơ chế hiện thực). Bảo vệ được từng ô.

**Cạm bẫy:** retry mọi thứ. Retry một lỗi vĩnh viễn là biến một lỗi thành một sự cố.

## C1.7 · Build system & toolchain — `In→Ad`

**Sub-leaves:**
- Chuỗi biên dịch: preprocess → compile → assemble → link
- `make` và `CMake` — viết được, không chỉ chạy được
- Linker: symbol, relocation, linker script, section
- Thư viện tĩnh vs động, `-fPIC`, `LD_PRELOAD`, `rpath`
- Cross-compilation: toolchain triple, sysroot, cho ARM từ x86
- Build tái lập được: khóa phiên bản, hash, hermetic build
- Cờ tối ưu và tác động thật của chúng (`-O0` → `-O3`, `-Os`, LTO)
- Cờ debug, symbol, stripping
- Quản lý dependency và xung đột phiên bản

**Dùng để xây:** C6 (firmware), C10 (deploy), toàn bộ CI.

**Checkpoint:** cross-compile một binary cho ARM từ máy x86, chạy được trên board, và giải thích được từng dòng trong linker script bạn dùng.

## C1.8 · Runtime internals — `In→Ad`

**Sub-leaves:**
- Allocator: `malloc` làm gì thật sự, `jemalloc`/`tcmalloc` khác gì
- Garbage collection: generational, mark-sweep, pause time, tác động lên p99
- GIL của CPython: cái gì bị khóa, cái gì không
- Async runtime: event loop, task, executor, và vì sao một task chặn làm chết tất cả
- Thread pool và work stealing
- Lazy vs eager evaluation
- JIT ở mức khái niệm
- Startup time, cold start, và ảnh hưởng tới serverless

**Dùng để xây:** C11 (performance), chẩn đoán latency trong C10.

**Checkpoint:** giải thích được vì sao p99 latency của một service tăng trong khi CPU chưa đầy 50% — và chỉ ra được bằng số liệu là do GC, do lock, hay do I/O.

## C1.9 · Debug & trace tooling — `Ad→Ex`

**Sub-leaves:**
- `gdb`: breakpoint, watchpoint, đọc thanh ghi, backtrace, debug lõi đa luồng
- Sanitizer: ASAN, UBSAN, TSAN, MSAN — mỗi cái bắt loại lỗi gì
- `valgrind` và `massif`
- `strace`/`ltrace` — theo dõi ranh giới syscall
- `perf`: `stat`, `record`, `top`, flamegraph
- `eBPF`/`bpftrace` ở mức viết được script đơn giản
- Logging có cấu trúc và correlation ID
- Debug từ xa và debug trên thiết bị nhúng (`gdbserver`, OpenOCD)
- Debug bằng in ấn — khi nào nó là công cụ đúng (có, đôi khi là vậy)
- Debug hồi quy bằng `git bisect`

**Dùng để xây:** toàn bộ roadmap. Đây là leaf làm bạn nhanh hơn ở mọi nhánh khác.

**Checkpoint:** tìm được một bug chỉ xuất hiện dưới concurrency (không tái tạo được bằng chạy tuần tự), dùng TSAN hoặc phân tích thủ công, và sửa đúng nguyên nhân chứ không che triệu chứng bằng `sleep`.

**Cạm bẫy:** đây là nhánh mà người tự học bỏ qua nhiều nhất và trả giá đắt nhất. Đầu tư 40 h vào tooling debug ở Phase 1 tiết kiệm hàng trăm giờ ở Phase 3–5.

## C1.10 · Git & quy trình cộng tác — `In`

**Sub-leaves:**
- Mô hình đối tượng: blob, tree, commit, ref — hiểu git như một DAG
- Branch, merge, rebase — và khi nào dùng cái nào
- `bisect` để tìm commit gây hồi quy
- `reflog` và phục hồi sau thảm họa
- Giải quyết xung đột mà không mất thay đổi
- Commit message tốt và commit nguyên tử
- Pull request, review, và cách nhận review khó
- Chiến lược branching: trunk-based vs git-flow, đánh đổi
- Hook và CI tích hợp

**Dùng để xây:** mọi dự án, mọi công việc.

**Checkpoint:** dùng `bisect` tìm được commit gây regression trong một repo ≥500 commit; rebase sạch một nhánh có 10 commit lộn xộn thành 3 commit nguyên tử.

## C1.11 · Đọc source code dự án lớn — `Ad→Ex`

**Sub-leaves:**
- Chiến lược điều hướng: từ entry point, từ test, từ symbol
- Công cụ: `ctags`/LSP, `ripgrep`, call graph, IDE navigation
- Đọc để trả lời một câu hỏi cụ thể, không đọc để "hiểu hết"
- Nhận ra pattern kiến trúc trong code lạ
- Dựng lại data flow và control flow từ code
- Đọc lịch sử git để hiểu *vì sao* code như vậy
- Đọc issue tracker và design doc kèm theo

**Dùng để xây:** năng lực học công nghệ mới nhanh — hệ số nhân lớn nhất trong toàn roadmap.

**Checkpoint:** chọn một module của CPython, Linux kernel, Redis, hoặc vLLM; trong ≤6 giờ, vẽ lại được data flow của module đó và viết một trang giải thích cho người khác.

**Cạm bẫy:** cố đọc tuần tự từ đầu. Codebase lớn không đọc tuần tự được — luôn đọc theo câu hỏi.

## C1.12 · Software engineering & design pattern — `Ad`

*(Đây là họ #10 của sweep, đặt trong C1 vì nó không tách rời khỏi việc viết code.)*

**Sub-leaves:**
- SOLID ở mức nguyên lý, không ở mức giáo điều
- Composition over inheritance
- Dependency injection và inversion of control
- Pattern thật hay dùng: strategy, adapter, observer, state machine, factory, repository
- Anti-pattern: god object, anemic model, premature abstraction, sự trừu tượng sai
- Coupling và cohesion — đo được bằng gì
- Refactoring có kỷ luật: có test trước, bước nhỏ, commit thường xuyên
- Nợ kỹ thuật: khi nào vay là đúng, khi nào phải trả
- Code review: cho và nhận
- Cấu trúc dự án và ranh giới module

**Dùng để xây:** C12, và khả năng bảo trì của mọi thứ bạn viết.

**Checkpoint:** nhận một codebase của chính bạn từ 6 tháng trước, thêm một tính năng mới, và đo được số file phải sửa. Nếu > 5 file cho một tính năng nhỏ, coupling của bạn quá cao — sửa nó.

## C1.13 · Phát triển có AI hỗ trợ — `Wo`

**Sub-leaves:**
- Khi nào AI tăng tốc thật và khi nào nó tạo nợ kỹ thuật
- Xác minh output: đọc, chạy, test — không chấp nhận vì "trông đúng"
- Dùng cho việc bạn đã làm được vs việc bạn chưa làm được (chỉ cái đầu là an toàn)
- Tác động lên việc học: nguy cơ mất cơ hội học chính cái bạn đang delegate

**Checkpoint:** phát hiện được output sai của AI **và nói được sai ở đâu, vì sao**. Điều kiện tiên quyết: bạn đã tự làm được việc đó ít nhất một lần.

**[Recommendation]** Ở Phase 0–2, giới hạn nghiêm ngặt: dùng AI để **giải thích** và **review**, không dùng để **viết thay**. Lý do: cơ chế học là vật lộn với vấn đề, và delegate chính là bỏ qua cơ chế đó. Từ Phase 3, khi nền đã vững, nới ra.

---

## ▸ Thứ tự học trong C1

```
1. C cơ bản + con trỏ + bộ nhớ          (Phase 0, ~80 h)
2. Python cơ bản + pytest                (Phase 0, ~50 h)  ← song song
3. gdb + valgrind + sanitizer            (Phase 0–1, ~30 h) ← sớm, không hoãn
4. C nâng cao + UB + struct layout       (Phase 1, ~60 h)
5. Git internals                         (Phase 1, ~20 h)
6. Build system + cross-compile          (Phase 1, ~30 h)
7. Python nâng cao + packaging + typing  (Phase 1–2, ~50 h)
8. Error handling + interface design     (Phase 2, ~40 h)
9. Runtime internals                     (Phase 2, ~30 h)
10. perf + eBPF                          (Phase 2–3, ~30 h)
11. Đọc source dự án lớn                 (Phase 2–5, ~40 h rải)
12. Go hoặc Rust                         (Phase 3, ~70 h)
13. Design pattern + refactoring         (Phase 2–4, ~40 h rải)
```

## ▸ Tài nguyên chính C1

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| *The C Programming Language* (K&R) | — | C1.1, nền | 40 |
| *Computer Systems: A Programmer's Perspective* + lab | CMU | C1.1, C1.4, C1.7 | 120 |
| *Modern C* (Jens Gustedt) — miễn phí | — | C1.1 chuẩn hiện đại | 30 |
| Python docs + *Fluent Python* | PSF / — | C1.2 | 50 |
| *The Rust Book* hoặc *A Tour of Go* — miễn phí | Rust/Go teams | C1.3 | 60 |
| GDB documentation + tutorial của Beej | GNU / — | C1.9 | 15 |
| *Pro Git* — miễn phí | — | C1.10 | 15 |
| *A Philosophy of Software Design* (Ousterhout) | — | C1.12 | 15 |
| Tài liệu công khai của Brendan Gregg | — | C1.9 phần perf/eBPF | 25 |

---

# ◆ C2 · DATA STRUCTURES & ALGORITHMS

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~280 h · Phase 1: 200 h · Phase 2–3: 80 h rải
**Vị trí:** con trực tiếp của Programming; chặn OS, Databases, và mọi tối ưu.
**Vì sao Advanced chứ không Expert:** bạn thiết kế hệ thống, không viết thư viện nền. Expert ở đây (tự cài B-tree tối ưu cache từ đầu) là chi phí cơ hội so với C8 hoặc C6.

## C2.1 · Phân tích độ phức tạp — `Ad`

**Sub-leaves:** big-O/Θ/Ω · phân tích amortized (aggregate, accounting, potential) · trường hợp trung bình vs xấu nhất · độ phức tạp không gian · hằng số ẩn và khi nào chúng quan trọng hơn bậc · độ phức tạp I/O và mô hình external-memory · độ phức tạp cache-oblivious

**Dùng để xây:** mọi quyết định thiết kế; đặc biệt là nhận ra khi nào O(n²) chấp nhận được.

**Checkpoint:** phân tích amortized của một cấu trúc **bạn tự thiết kế** (không phải dynamic array kinh điển), và chứng minh biên.

**Cạm bẫy:** thờ phượng big-O. Với n < 1000, hằng số và cache locality quan trọng hơn bậc.

## C2.2 · Mảng, chuỗi, bảng băm — `Ad`

**Sub-leaves:** dynamic array và chiến lược tăng trưởng · hàm băm: tính chất, phân phối, hàm băm tấn công được · giải quyết va chạm: chaining vs open addressing, robin hood, cuckoo · load factor và rehashing · thuật toán chuỗi: KMP, Rabin-Karp, Boyer-Moore · tìm kiếm con chuỗi và ứng dụng thực tế · trie và radix tree · biểu diễn chuỗi: UTF-8, độ dài vs kết thúc null, small-string optimization

**Dùng để xây:** C9 (index), C1 (chuỗi trong C), mọi thứ.

**Checkpoint:** tự cài hash table với open addressing, đo được hiệu năng so với thư viện chuẩn, và giải thích được chênh lệch.

## C2.3 · Cây và cây cân bằng — `In→Ad`

**Sub-leaves:** BST và suy biến · AVL và red-black — tính chất, không cần thuộc thao tác xoay · B-tree và B+tree: tại sao fanout cao, tại sao DB dùng · trie và compressed trie · segment tree và Fenwick tree · heap như một cây · cây như cấu trúc phân cấp (filesystem, DOM, AST)

**Dùng để xây:** C9 (index database), C4 (filesystem).

**Checkpoint:** giải thích được **bằng số** vì sao database dùng B-tree chứ không dùng BST — tính toán số lần đọc đĩa cho mỗi loại với n = 10⁹.

## C2.4 · Heap & hàng đợi ưu tiên — `In`

**Sub-leaves:** binary heap: sift-up/down, heapify · d-ary heap và cân bằng cache · pairing/Fibonacci heap ở mức awareness · hàng đợi ưu tiên trong scheduler · timer wheel như cấu trúc thay thế · top-k và selection

**Dùng để xây:** C4 (scheduler), C6 (RTOS), C11 (đo latency).

**Checkpoint:** cài scheduler dùng heap cho một RTOS đồ chơi, chạy đúng với 20 task có chu kỳ khác nhau.

## C2.5 · Đồ thị & duyệt — `Ad`

**Sub-leaves:** biểu diễn: danh sách kề, ma trận kề, CSR · BFS/DFS và ứng dụng · sắp xếp tô-pô và phát hiện chu trình · thành phần liên thông, thành phần liên thông mạnh · cây khung nhỏ nhất · đồ thị hai phía và ghép cặp · đồ thị như mô hình cho dependency, pipeline, mạng

**Dùng để xây:** C1.7 (build system), C9 (DAG pipeline), C12 (phân tích dependency).

**Checkpoint:** cài sắp xếp tô-pô cho một build system nhỏ, phát hiện được chu trình và báo lỗi có ích (nêu đúng chu trình nào).

## C2.6 · Đường đi ngắn nhất, luồng, tối ưu trên đồ thị — `In`

**Sub-leaves:** Dijkstra và điều kiện đúng · Bellman-Ford và trọng số âm · A* và heuristic chấp nhận được · Floyd-Warshall · luồng cực đại và lát cắt nhỏ nhất · ứng dụng thực tế: routing, phân bổ tài nguyên, lập lịch

**Dùng để xây:** C5 (routing), A1 (motion planning), phân bổ tài nguyên trong C10.

**Checkpoint:** cài Dijkstra và **nêu được 2 trường hợp nó cho kết quả sai**, chứng minh bằng ví dụ cụ thể.

## C2.7 · Sắp xếp, chọn, sắp xếp ngoài — `In→Ad`

**Sub-leaves:** quicksort và lựa chọn pivot · mergesort và tính ổn định · heapsort · introsort (cái thư viện chuẩn thực sự dùng) · radix/counting sort và khi nào tuyến tính được · quickselect và tìm phần tử thứ k · external merge sort · sắp xếp song song ở mức khái niệm

**Dùng để xây:** C9 (xử lý dữ liệu lớn hơn RAM).

**Checkpoint:** sắp xếp một file 10 GB trên máy 8 GB RAM, đo được số lần đọc/ghi đĩa và so với lý thuyết.

## C2.8 · Quy hoạch động — `In→Ad`

**Sub-leaves:** cấu trúc con tối ưu và bài toán con gối nhau · top-down memo vs bottom-up · tối ưu không gian (cuộn mảng) · DP trên chuỗi: LCS, edit distance, alignment · DP trên cây · DP bitmask · DP và cây quyết định của nó

**Dùng để xây:** C7 (alignment chuỗi thời gian), phân tích chuỗi trong C8.

**Checkpoint:** nhận ra cấu trúc DP trong một bài toán bạn **chưa từng gặp**, trong ≤20 phút, và viết được hàm hồi quy.

## C2.9 · Tham lam & chứng minh tính đúng — `In`

**Sub-leaves:** tính chất lựa chọn tham lam · lập luận exchange argument · matroid ở mức awareness · khi nào tham lam sai và làm sao biết · thuật toán xấp xỉ và tỷ lệ đảm bảo

**Checkpoint:** với một thuật toán tham lam cho trước, hoặc chứng minh nó tối ưu bằng exchange argument, hoặc đưa phản ví dụ.

## C2.10 · Cấu trúc dữ liệu xác suất — `Wo→In`

**Sub-leaves:** Bloom filter: toán học đằng sau, tính tỷ lệ dương tính giả · counting Bloom và cuckoo filter · HyperLogLog và ước lượng cardinality · Count-Min sketch · reservoir sampling · t-digest và ước lượng phân vị · locality-sensitive hashing (nối sang ANN ở C9)

**Dùng để xây:** C9 (dedup ở quy mô), C11 (đo phân vị trên stream).

**Checkpoint:** dùng Bloom filter giảm ≥80% truy vấn DB trong một workload thật, đo được tỷ lệ dương tính giả thực tế và so với tính toán lý thuyết.

## C2.11 · Thuật toán nhận biết cache & bộ nhớ ngoài — `In→Ad`

**Sub-leaves:** mô hình phân cấp bộ nhớ trong thiết kế thuật toán · duyệt theo hàng vs theo cột và ảnh hưởng · blocking/tiling · bố cục dữ liệu: AoS vs SoA · thuật toán cache-oblivious ở mức khái niệm · prefetching và pattern truy cập dự đoán được · false sharing trong code song song

**Dùng để xây:** C3, C11, tối ưu inference trong C8.

**Checkpoint:** tăng tốc một vòng lặp ≥2× **chỉ bằng** đổi thứ tự truy cập bộ nhớ hoặc bố cục dữ liệu — không đổi thuật toán, không đổi cờ compiler.

## C2.12 · Thuật toán trực tuyến & streaming — `Wo→In`

**Sub-leaves:** mô hình streaming và ràng buộc một lượt · cửa sổ trượt · thống kê chạy: trung bình, phương sai (Welford), phân vị · phát hiện thay đổi trên stream · phân tích cạnh tranh ở mức khái niệm · đánh đổi giữa chính xác và bộ nhớ

**Dùng để xây:** C7 (xử lý tín hiệu trực tiếp), C11 (metric), C9 (stream).

**Checkpoint:** tính p99 trên một stream 10⁸ mẫu **không lưu toàn bộ dữ liệu**, sai số dưới 1% so với giá trị chính xác.

## C2.13 · Cấu trúc dữ liệu an toàn concurrency — `In→Ad`

**Sub-leaves:** cấu trúc có khóa vs không khóa · SPSC/MPSC/MPMC queue · so sánh-và-hoán-đổi và vấn đề ABA · hazard pointer và epoch-based reclamation ở mức khái niệm · read-copy-update ở mức khái niệm · hàng rào bộ nhớ trong cấu trúc dữ liệu · khi nào lock-free là sai lựa chọn (thường xuyên)

**Dùng để xây:** C4, C6 (queue giữa ISR và task).

**Checkpoint:** cài lock-free SPSC ring buffer, chạy đúng dưới TSAN, và **lập luận bằng lời** vì sao nó đúng với mô hình bộ nhớ cụ thể.

**Cạm bẫy:** viết lock-free vì nó nghe hay. 95% trường hợp mutex đúng và nhanh hơn về tổng thể.

---

## ▸ Thứ tự học trong C2

```
1. Độ phức tạp + mảng/băm            (Phase 1, ~40 h)
2. Cây + heap                         (Phase 1, ~35 h)
3. Sắp xếp + chọn                     (Phase 1, ~25 h)
4. Đồ thị + duyệt                     (Phase 1, ~35 h)
5. DP + tham lam                      (Phase 1, ~40 h)
6. Đường đi ngắn nhất + luồng         (Phase 1–2, ~20 h)
7. Cấu trúc xác suất                  (Phase 2, ~20 h)
8. Cache-aware + external memory      (Phase 2, ~25 h)
9. Streaming/online                   (Phase 2–3, ~20 h)
10. Concurrency-safe                  (Phase 3, ~20 h)   ← sau C4
```

## ▸ Tài nguyên chính C2

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| 6.006 *Introduction to Algorithms* | MIT OCW | C2.1–C2.9 | 90 |
| *Algorithms* (Sedgewick) hoặc CLRS tra cứu | Princeton / MIT | tham chiếu | 30 |
| *Algorithm Design Manual* (Skiena) | — | phần "war stories" — nối lý thuyết với thực tế | 20 |
| LeetCode / Codeforces | — | luyện nhận dạng pattern, **giới hạn 80 h tổng** | 80 |
| *What Every Programmer Should Know About Memory* (Drepper) | — | C2.11 | 15 |
| Bài báo gốc về Bloom filter, HyperLogLog | — | C2.10 — đọc primary source | 10 |

---

# ◆ C3 · COMPUTER ARCHITECTURE & DIGITAL LOGIC

**Mức mục tiêu:** **Advanced** (Ad→Ex ở memory hierarchy và biểu diễn số)
**Ngân sách:** ~350 h · Phase 1: 180 h · Phase 2: 80 h · Phase 3–4: 90 h
**Vị trí:** con của Programming; chặn OS, Performance, và toàn bộ tối ưu inference.
**Vì sao mức này:** đây là nơi **mọi câu hỏi "vì sao chậm" kết thúc**. Không có nhánh này, tối ưu là mê tín.

## C3.1 · Logic Boolean & mạch tổ hợp — `Wo`

**Sub-leaves:** đại số Boolean, định lý De Morgan · cổng cơ bản và tập đầy đủ (NAND, NOR) · bảng chân lý, dạng chuẩn tắc, bản đồ Karnaugh · bộ cộng, bộ chọn kênh, bộ giải mã, bộ so sánh · ALU: xây từ các khối trên · độ trễ lan truyền và đường tới hạn

**Dùng để xây:** nền của tất cả phần còn lại trong C3.

**Checkpoint:** dựng ALU đầy đủ chức năng chỉ từ cổng NAND (nand2tetris project 1–2), pass toàn bộ test.

## C3.2 · Logic tuần tự, xung nhịp, máy trạng thái — `In`

**Sub-leaves:** latch và flip-flop · thanh ghi và thanh ghi dịch · bộ đếm · miền xung nhịp và vượt miền xung nhịp (CDC) · thiết lập/giữ và tại sao metastability tồn tại · máy trạng thái Moore vs Mealy · mã hóa trạng thái và trạng thái bất hợp lệ

**Dùng để xây:** C6 (firmware giao thức), hiểu peripheral trong MCU.

**Checkpoint:** thiết kế FSM cho một giao thức nối tiếp (ví dụ giải mã Manchester hoặc parse một khung UART tùy biến), cài bằng C, chạy đúng trên MCU, và xử lý được trạng thái lỗi.

## C3.3 · Datapath, control unit, tự dựng một CPU — `In`

**Sub-leaves:** chu trình fetch–decode–execute · tệp thanh ghi và bus · đường điều khiển và giải mã lệnh · thiết kế đơn chu kỳ vs đa chu kỳ · bộ nhớ lệnh và bộ nhớ dữ liệu · I/O ánh xạ bộ nhớ · assembler cho ISA của chính bạn

**Dùng để xây:** trực giác nền cho C3.4–C3.8; xóa bỏ toàn bộ "ma thuật" trong máy tính.

**Checkpoint:** hoàn thành nand2tetris phần 1 — CPU chạy được, assembler chạy được, chương trình assembly chạy trên CPU do bạn thiết kế.

**Cạm bẫy:** bỏ qua vì "không thực tế". Đây là khoản đầu tư 60 h có ROI cao nhất trong Phase 1 — nó biến 5 nhánh khác từ thuộc lòng thành hiểu.

## C3.4 · ISA & assembly — `In→Ad`

**Sub-leaves:** RISC vs CISC — khác biệt thật, không phải khẩu hiệu · RISC-V: tập lệnh cơ sở, thanh ghi, chế độ địa chỉ · ARM Cortex-M: Thumb-2, thanh ghi, ngoại lệ · x86-64 ở mức **đọc được** disassembly · quy ước gọi hàm cho mỗi kiến trúc · prologue/epilogue và stack frame · ánh xạ từ C sang assembly: compiler sinh gì cho vòng lặp, nhánh, gọi hàm · lệnh nguyên tử và ngữ nghĩa của chúng

**Dùng để xây:** C1.9 (debug), C6 (firmware), C11 (đọc profile).

**Checkpoint:** đọc disassembly của một hàm C do compiler sinh ở `-O2` và giải thích từng thay đổi so với `-O0`: inline gì, unroll gì, vectorize gì, loại bỏ gì.

## C3.5 · Pipeline, hazard, dự đoán nhánh — `In→Ad`

**Sub-leaves:** pipeline 5 tầng cổ điển · hazard dữ liệu, forwarding, stall · hazard điều khiển và bong bóng nhánh · dự đoán nhánh: static, 2-bit, tournament, TAGE ở mức khái niệm · thực thi suy đoán và hệ quả bảo mật (Spectre/Meltdown ở mức khái niệm) · superscalar và thực thi ngoài thứ tự · đa luồng đồng thời (SMT/hyperthreading) và khi nào nó hại

**Dùng để xây:** C11, tối ưu vòng lặp nóng trong C8.

**Checkpoint:** viết hai phiên bản của cùng một vòng lặp — một có nhánh khó đoán, một branchless — đo chênh lệch, và xác nhận nguyên nhân bằng bộ đếm `branch-misses` của `perf`.

## C3.6 · Phân cấp bộ nhớ — `Ad→Ex` ★ leaf quan trọng nhất của C3

**Sub-leaves:**
- Nguyên lý cục bộ: thời gian và không gian
- Cache L1/L2/L3: kích thước, độ liên kết, kích thước dòng, chính sách thay thế
- Ánh xạ cache và xung đột; tại sao stride xấu giết hiệu năng
- Write-through vs write-back, write-allocate
- TLB và ánh xạ địa chỉ ảo; huge page
- Prefetcher phần cứng và pattern nó nhận ra được
- Băng thông bộ nhớ vs độ trễ bộ nhớ — hai giới hạn khác nhau
- NUMA và vị trí bộ nhớ trên máy nhiều socket
- False sharing và cache line ping-pong
- Đo: cache miss, TLB miss, băng thông bão hòa
- Mô hình roofline: xác định compute-bound hay memory-bound

**Dùng để xây:** C11 (toàn bộ), C8 (tối ưu inference), C2.11.

**Checkpoint:** lấy một workload thật (nhân ma trận, hoặc một vòng lặp xử lý tín hiệu), đo bằng `perf` để xác định nó memory-bound hay compute-bound, áp dụng blocking/tiling, đạt speedup ≥3×, và **giải thích speedup bằng số liệu cache miss trước/sau**.

**Cạm bẫy:** tối ưu trước khi đo. Và: đo sai vì benchmark bị cache nóng sẵn hoặc bị compiler loại bỏ.

## C3.7 · Nhất quán & mạch lạc bộ nhớ — `In→Ad`

**Sub-leaves:** mạch lạc cache: MESI và các biến thể · mô hình nhất quán bộ nhớ: sequential consistency, TSO (x86), mô hình yếu (ARM) · hàng rào bộ nhớ và lệnh barrier · thứ tự acquire/release · mô hình bộ nhớ của ngôn ngữ (C11 atomics, mô hình của Java/Go/Rust) · tại sao code đúng trên x86 hỏng trên ARM

**Dùng để xây:** C2.13, C4.7, mọi code song song trên nhiều kiến trúc.

**Checkpoint:** viết một đoạn code đồng bộ hóa **chạy đúng trên x86 nhưng hỏng trên ARM**, giải thích vì sao, và sửa bằng barrier đúng.

## C3.8 · SIMD & tính toán vector — `Wo→In`

**Sub-leaves:** mô hình SIMD và độ rộng vector · SSE/AVX trên x86; NEON trên ARM; RVV trên RISC-V · tự động vector hóa của compiler: khi nào nó thành công, khi nào thất bại · intrinsics ở mức đọc và viết được cái đơn giản · alignment và tác động tới SIMD · pattern giảm (reduction) và giới hạn của chúng · SIMD trong DSP và inference

**Dùng để xây:** C7 (xử lý tín hiệu), C8 (kernel inference), C11.

**Checkpoint:** vector hóa một phép convolution 1-D, đo speedup so với bản vô hướng, và xác nhận bằng disassembly rằng lệnh SIMD thực sự được sinh ra.

## C3.9 · Kiến trúc GPU & mô hình bộ nhớ — `In→Ad`

**Sub-leaves:** SM, warp, block, grid · mô hình thực thi SIMT và phân kỳ warp · phân cấp bộ nhớ GPU: global, shared, register, constant · gộp truy cập bộ nhớ (coalescing) · occupancy và tác động thật của nó · băng thông bộ nhớ là nút thắt cho phần lớn kernel ML · kernel fusion và vì sao nó quan trọng · tensor core và phép nhân ma trận độ chính xác hỗn hợp · truyền host–device và chi phí PCIe · nhiều GPU: NVLink, chiến lược song song hóa

**Dùng để xây:** C8 (toàn bộ tầng serving và training).

**Checkpoint:** lấy một kernel GPU (viết hoặc có sẵn), xác định nó memory-bound hay compute-bound bằng công cụ profiling, và giải thích được kết quả bằng mô hình roofline.

## C3.10 · NPU, accelerator & kiến trúc dataflow — `In→Ad`

**Sub-leaves:** vì sao accelerator tồn tại: hiệu quả năng lượng, không phải tốc độ thuần · mảng tâm thu (systolic array) và tái sử dụng dữ liệu · kiến trúc dataflow vs von Neumann · độ phủ toán tử (operator coverage) và vì sao model của bạn không chạy · toolchain lượng tử hóa của từng họ NPU · phân mảnh toolchain: mỗi họ NPU có compiler riêng, pipeline lượng tử hóa riêng, độ phủ toán tử riêng · lập kế hoạch bộ nhớ cho NPU nhỏ · NPU cấp MCU đang trở thành mặc định [Fact 2026] · đo thực tế: TOPS trên tờ giấy vs latency thật

**Dùng để xây:** C6.14, C8.9, toàn bộ edge AI.

**Checkpoint:** chạy cùng một model trên hai phần cứng khác nhau (ví dụ CPU và một NPU/accelerator), đo latency và năng lượng, **và giải thích chênh lệch bằng đặc điểm kiến trúc**, không bằng "cái này nhanh hơn".

**Cạm bẫy [Fact 2026]:** phân mảnh toolchain là khó khăn số một ở tầng này — mỗi họ NPU có compiler riêng và độ phủ toán tử riêng. Hệ quả cho roadmap: học **quy trình** (lượng tử hóa → chuyển đổi → kiểm tra độ phủ toán tử → đo lại độ chính xác → đo latency), không học một toolchain cụ thể.

## C3.11 · I/O, DMA, ngắt, bus — `In→Ad`

**Sub-leaves:** I/O ánh xạ bộ nhớ vs I/O cổng · polling vs ngắt vs DMA — đánh đổi · bộ điều khiển ngắt, vector, độ ưu tiên, lồng nhau · độ trễ ngắt và jitter · DMA: scatter-gather, bộ đệm vòng, đệm đôi · mạch lạc cache với DMA (vấn đề kinh điển) · bus: I²C, SPI, UART ở tầng vật lý · PCIe ở mức khái niệm: lane, TLP, độ trễ · USB ở mức khái niệm

**Dùng để xây:** C6 (toàn bộ), C4.6.

**Checkpoint:** thiết lập DMA transfer cho một luồng ADC liên tục, đo mức giảm tải CPU so với polling, và xử lý đúng vấn đề mạch lạc cache nếu có.

## C3.12 · Biểu diễn số — `Ad→Ex` ★ leaf bị đánh giá thấp nhất

**Sub-leaves:**
- Bù hai, tràn số, dịch bit có dấu
- IEEE 754: float32, float64 — mantissa, exponent, denormal, NaN, Inf
- Định dạng nửa chính xác: float16, bfloat16 — khác nhau ở đâu và vì sao ML dùng bf16
- FP8 và các biến thể (E4M3, E5M2)
- Số nguyên lượng tử hóa: int8, int4, tỷ lệ đối xứng vs bất đối xứng
- Lượng tử hóa theo tensor vs theo kênh vs theo nhóm
- Số học điểm cố định (fixed-point) cho MCU không FPU
- Lỗi làm tròn, sai số tích lũy, catastrophic cancellation
- Thứ tự phép cộng ảnh hưởng kết quả — tính không tái lập trong tính toán song song
- Saturation vs wrap-around trong DSP
- Đo mất mát độ chính xác: chỉ số nào có nghĩa

**Dùng để xây:** C7 (DSP), C8.9 (nén model), C6.14 (inference trên thiết bị).

**Checkpoint:** lượng tử hóa một model sang int8, đo mất mát độ chính xác, **và định vị chính xác lớp nào gây mất mát nhiều nhất bằng phân tích theo lớp** — không đoán.

**Cạm bẫy:** coi lượng tử hóa là một nút bấm. Đây là leaf mà lỗi xảy ra âm thầm: model vẫn chạy, vẫn trả kết quả trông hợp lý, chỉ là sai ở một phân khúc dữ liệu bạn không test.

## C3.13 · Năng lượng & nhiệt ở mức chip — `Wo→In`

**Sub-leaves:** công suất động vs tĩnh · DVFS và điều chỉnh xung nhịp · giới hạn nhiệt và throttling · năng lượng mỗi phép toán và vì sao di chuyển dữ liệu tốn hơn tính toán · ngân sách năng lượng cho inference · race-to-sleep vs chạy chậm liên tục · đo công suất thật: shunt, INA219, đồng hồ đo năng lượng

**Dùng để xây:** C6.9 (quản lý năng lượng), S7 (kinh tế học).

**Checkpoint:** đo tụt hiệu năng do throttling trên một SBC dưới tải liên tục 30 phút, vẽ đồ thị nhiệt–xung nhịp–thông lượng, và đề xuất được một biện pháp giảm thiểu có số liệu.

## C3.14 · Bộ đếm hiệu năng & phương pháp đo — `Ad`

**Sub-leaves:** PMU và các sự kiện phần cứng có sẵn · `perf stat`: chỉ số nào đọc trước · IPC, cache miss rate, branch miss rate — diễn giải đúng · lấy mẫu vs đếm chính xác · quy kết sai do skid và cách xử lý · đo trên hệ có nhiều nhân và nhiễu · thiết lập môi trường đo ổn định: ghim CPU, tắt turbo, tắt ASLR khi cần

**Dùng để xây:** C11 (toàn bộ), mọi tuyên bố về hiệu năng bạn đưa ra.

**Checkpoint:** dùng `perf stat` trên một workload để phân biệt được ba khả năng — nút thắt ở CPU, ở bộ nhớ, hay ở I/O — và đưa ra kết luận đúng ở cả ba trường hợp thử nghiệm.

---

## ▸ Thứ tự học trong C3

```
1. Logic Boolean + tổ hợp              (Phase 1, ~25 h)
2. Logic tuần tự + FSM                 (Phase 1, ~25 h)
3. Tự dựng CPU (nand2tetris 1)         (Phase 1, ~60 h)  ← ROI cao nhất
4. ISA + assembly                      (Phase 1, ~40 h)
5. Pipeline + dự đoán nhánh            (Phase 1–2, ~30 h)
6. Phân cấp bộ nhớ ★                   (Phase 2, ~55 h)  ← đầu tư nặng
7. Bộ đếm hiệu năng + phương pháp đo   (Phase 2, ~25 h)  ← song song với trên
8. Biểu diễn số ★                      (Phase 2–3, ~40 h)
9. I/O, DMA, ngắt                      (Phase 3, ~25 h)  ← cùng lúc với C6
10. SIMD                               (Phase 3, ~20 h)
11. Nhất quán bộ nhớ                   (Phase 3, ~20 h)  ← cùng lúc với C4.7
12. Kiến trúc GPU                      (Phase 3–4, ~35 h)
13. NPU & accelerator                  (Phase 4, ~25 h)
14. Năng lượng & nhiệt                 (Phase 3–4, ~15 h)
```

## ▸ Tài nguyên chính C3

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| *Nand2Tetris* phần 1 (+ phần 2 tùy chọn) | Hebrew University of Jerusalem | C3.1–C3.3 | 70 |
| *Computer Systems: A Programmer's Perspective* + lab | CMU | C3.4–C3.6, C3.12 | 100 |
| *Computer Architecture: A Quantitative Approach* (Hennessy & Patterson) — tra cứu | — | C3.5, C3.6, C3.9 | 25 |
| *What Every Programmer Should Know About Memory* (Drepper) | — | C3.6 | 15 |
| RISC-V ISA specification | RISC-V International | C3.4 — primary source | 15 |
| ARM Cortex-M Technical Reference Manual | ARM | C3.4, C3.11 — primary source | 20 |
| CUDA Programming Guide | NVIDIA | C3.9 | 30 |
| *Programming Massively Parallel Processors* | — | C3.9 | 25 |
| `perf` documentation + tài liệu của Brendan Gregg | Linux / — | C3.14 | 20 |
| IEEE 754 standard + *What Every Computer Scientist Should Know About Floating-Point* (Goldberg) | IEEE / — | C3.12 | 15 |

---

# ◆ C4 · OPERATING SYSTEMS & CONCURRENCY

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~400 h · Phase 1–2: 260 h · Phase 3: 90 h · Phase 4–5: 50 h
**Vị trí:** con của DSA + Computer Arch; chặn Networking, Embedded, Cloud.
**Vì sao Advanced:** đây là nơi trú ngụ của **mọi bug khó nhất** trong hệ end-to-end. Expert (viết kernel production) không khả thi và không cần.

## C4.1 · Tiến trình, luồng, chuyển ngữ cảnh — `Ad`

**Sub-leaves:** khối điều khiển tiến trình và những gì trong đó · `fork`/`exec`/`wait` và mô hình tiến trình Unix · luồng kernel vs luồng người dùng vs mô hình lai · chi phí chuyển ngữ cảnh: lưu thanh ghi, xả TLB, ô nhiễm cache · coroutine và luồng xanh · cây tiến trình, tiến trình mồ côi, tiến trình zombie · nhóm tiến trình, phiên, và điều khiển tác vụ · tín hiệu: ngữ nghĩa, an toàn trong handler, mask

**Dùng để xây:** nền của toàn bộ C4; C10 (container).

**Checkpoint:** đo chi phí chuyển ngữ cảnh trên máy của bạn (viết benchmark riêng), ra con số hợp lý, và giải thích được tại sao nó ở mức đó bằng những gì phải lưu/khôi phục.

## C4.2 · Lập lịch — `In→Ad`

**Sub-leaves:** mục tiêu lập lịch và mâu thuẫn giữa chúng · round-robin, MLFQ, CFS · lượng tử thời gian và đánh đổi thông lượng/tương tác · lập lịch thời gian thực: rate-monotonic, earliest-deadline-first · phân tích khả năng lập lịch và giới hạn sử dụng · đảo ngược ưu tiên và kế thừa ưu tiên · độ ưu tiên và `nice`, chính sách `SCHED_FIFO`/`SCHED_RR`/`SCHED_DEADLINE` · lập lịch trên nhiều nhân, cân bằng tải, ái lực CPU · lập lịch và điện năng

**Dùng để xây:** C6.7 (RTOS), C11 (latency đuôi), C10 (đặt container).

**Checkpoint:** tái tạo được đảo ngược ưu tiên trong một chương trình có 3 luồng, đo được độ trễ gây ra, và sửa bằng kế thừa ưu tiên — chứng minh bằng số đo trước/sau.

## C4.3 · Bộ nhớ ảo & phân trang — `Ad`

**Sub-leaves:** không gian địa chỉ ảo và bảng trang · MMU, TLB, dạo bảng trang · lỗi trang: nhỏ, lớn, và lỗi thật · sao chép khi ghi và tối ưu `fork` · `mmap`, ánh xạ file, bộ nhớ chia sẻ · hoán đổi, thu hồi trang, thuật toán thay thế · huge page và khi nào chúng giúp · cấp phát bộ nhớ ở tầng kernel vs tầng người dùng · overcommit và OOM killer · thrashing: nhận diện và nguyên nhân · cách ly bộ nhớ cho container (cgroup)

**Dùng để xây:** C1.4, C10 (container), C11 (chẩn đoán bộ nhớ).

**Checkpoint:** chẩn đoán một sự cố thrashing từ số liệu (lỗi trang, hoạt động hoán đổi, độ trễ), xác định nguyên nhân, và sửa — trong một kịch bản bạn tự dựng ra.

## C4.4 · Hệ thống file & lưu trữ ở tầng OS — `In→Ad`

**Sub-leaves:** VFS và trừu tượng hóa hệ thống file · inode, dentry, mô tả file, bảng file mở · bố cục hệ thống file: ext4, XFS, và khái niệm của F2FS cho flash · nhật ký (journaling) và các chế độ · cache trang và cache ghi · `fsync`, `fdatasync`, và ngữ nghĩa độ bền thật · ghi đè tại chỗ vs ghi copy-on-write (btrfs, ZFS ở mức khái niệm) · lớp block, hàng đợi I/O, bộ lập lịch I/O · đặc điểm của SSD: ghi khuếch đại, thu gom rác, TRIM · hệ thống file cho nhúng: LittleFS, SPIFFS, và ma sát wear-leveling

**Dùng để xây:** C9 (storage engine), C6 (lưu trữ trên thiết bị).

**Checkpoint:** chứng minh mất dữ liệu khi thiếu `fsync` — viết chương trình ghi, cắt điện thật (hoặc mô phỏng bằng `dm-flakey`/VM), và cho thấy dữ liệu mất; sau đó sửa và chứng minh không mất.

**Cạm bẫy:** tin rằng `write()` thành công nghĩa là dữ liệu đã an toàn. Đây là giả định sai gây mất dữ liệu nhiều nhất trong hệ nhúng.

## C4.5 · Mô hình I/O — `Ad`

**Sub-leaves:** chặn, không chặn, ghép kênh I/O, không đồng bộ — bốn mô hình khác nhau · `select`/`poll`/`epoll`/`kqueue` · kích hoạt theo mức vs theo cạnh · `io_uring`: mô hình, vòng gửi/hoàn thành, khi nào nó thắng · vòng lặp sự kiện: cấu trúc, timer, tích hợp tín hiệu · vấn đề C10K và C10M · zero-copy: `sendfile`, `splice`, ánh xạ bộ nhớ · bộ đệm và tương tác với cache trang · backpressure ở tầng I/O

**Dùng để xây:** C5.10 (lập trình socket), C10, mọi service hiệu năng cao.

**Checkpoint:** tự viết một vòng lặp sự kiện phục vụ 10.000 kết nối đồng thời trên một luồng, đo được bộ nhớ và CPU, và giải thích được vì sao nó không sập khi số kết nối tăng.

## C4.6 · Nguyên thủy concurrency — `Ad`

**Sub-leaves:** loại trừ lẫn nhau: mutex, spinlock, khi nào dùng cái nào · biến điều kiện và thức dậy giả · semaphore đếm và nhị phân · khóa đọc-ghi và bỏ đói · biến nguyên tử và thao tác so sánh-hoán-đổi · thứ tự bộ nhớ trong API nguyên tử (relaxed, acquire, release, seq_cst) · futex và cách mutex thực sự hoạt động · rào chắn (barrier) và latch · lưu trữ cục bộ theo luồng · khởi tạo một lần và mẫu singleton an toàn

**Dùng để xây:** C2.13, C6.7, mọi code song song.

**Checkpoint:** cài đúng một bounded buffer producer-consumer bằng mutex + condition variable, **không busy-wait**, xử lý đúng thức dậy giả, chạy sạch dưới TSAN với 8 producer và 8 consumer.

## C4.7 · Mẫu concurrency ở tầng kiến trúc — `In→Ad`

**Sub-leaves:** mô hình actor và truyền thông điệp · CSP và channel · fork-join và work stealing · pipeline và giai đoạn · SEDA (kiến trúc theo giai đoạn hướng sự kiện) · backpressure: cơ chế và vì sao thiếu nó gây sập · giới hạn hàng đợi và chính sách loại bỏ · pool luồng: định cỡ, hàng đợi, bỏ đói · tránh chia sẻ trạng thái vs chia sẻ có kiểm soát · luồng đơn + không đồng bộ vs đa luồng — đánh đổi thật

**Dùng để xây:** C10 (thiết kế service), C8 (pipeline inference).

**Checkpoint:** thiết kế một pipeline 3 giai đoạn có backpressure, chứng minh bằng thử nghiệm rằng khi giai đoạn chậm nhất bị nghẽn, bộ nhớ **không** tăng vô hạn.

## C4.8 · Bế tắc, livelock, bỏ đói — `Ad`

**Sub-leaves:** bốn điều kiện Coffman · thứ tự khóa và phân cấp khóa · phát hiện bế tắc vs ngăn ngừa vs tránh · bế tắc phân tán và khác biệt so với cục bộ · livelock và vai trò của ngẫu nhiên hóa · bỏ đói và công bằng · convoy effect · chẩn đoán: stack dump toàn bộ luồng, phân tích đồ thị chờ

**Checkpoint:** cho một stack dump của tất cả luồng trong một tiến trình bị treo, xác định được chu trình chờ và chỉ ra hai khóa nào gây bế tắc.

## C4.9 · IPC — `In→Ad`

**Sub-leaves:** pipe và named pipe · socket Unix domain · bộ nhớ chia sẻ + đồng bộ hóa · hàng đợi thông điệp (POSIX, System V) · tín hiệu như IPC và giới hạn của nó · `eventfd`, `signalfd`, `timerfd` · truyền mô tả file qua socket · D-Bus ở mức khái niệm · đánh đổi: thông lượng, độ trễ, độ phức tạp, khả năng gỡ lỗi

**Checkpoint:** cho ba tình huống khác nhau (thông lượng cao/độ trễ thấp/nhiều tiến trình không tin nhau), chọn đúng cơ chế IPC cho mỗi cái và bảo vệ lựa chọn bằng đo đạc.

## C4.10 · RTOS & tính toán thời gian thực — `In→Ad`

**Sub-leaves:** khái niệm tác vụ, trạng thái, chuyển tiếp · tick timer và lập lịch không tick (tickless) · ISR: quy tắc, độ dài, cái gì được phép gọi · giao tiếp ISR ↔ tác vụ (queue, notification) · mutex với kế thừa ưu tiên trong RTOS · phân bổ stack cho mỗi tác vụ và phát hiện tràn · WCET: cách ước lượng, tại sao khó · jitter: nguồn gốc và đo đạc · FreeRTOS và Zephyr — mô hình khác nhau ở đâu · thời gian thực cứng vs mềm và hệ quả thiết kế

**Dùng để xây:** C6 (toàn bộ), S3 (control), S6 (reliability).

**Checkpoint:** đo jitter của một tác vụ chu kỳ 1 ms trên MCU dưới tải, đưa jitter xuống dưới 50 µs, và **giải thích từng nguồn jitter** bạn đã loại bỏ.

## C4.11 · Container & ảo hóa — `In→Ad`

**Sub-leaves:** namespace: PID, network, mount, user, IPC, UTS · cgroup v2: CPU, memory, I/O, pid · hệ thống file lớp và overlayfs · đặc tả image OCI và runtime · seccomp, capability, và giảm quyền · phá vỡ container và mô hình mối đe dọa · máy ảo vs container: ranh giới cách ly · microVM (Firecracker) ở mức khái niệm · chi phí hiệu năng của container — cái nào thật, cái nào huyền thoại

**Dùng để xây:** C10 (toàn bộ), triển khai trong mọi dự án.

**Checkpoint:** tự dựng một "container" tối giản bằng `unshare` + `cgroup` + `chroot` — không dùng Docker — chạy được một tiến trình bị cách ly về mạng, PID và bộ nhớ.

## C4.12 · Linux như một nền tảng — `In→Ad`

**Sub-leaves:** quá trình khởi động: firmware → bootloader → kernel → init · systemd: unit, target, chính sách khởi động lại, tạp chí · udev và quản lý thiết bị · device tree trên hệ nhúng · mô hình driver và sysfs · quản lý gói và bản dựng tùy chỉnh (Buildroot, Yocto ở mức khái niệm) · tham số kernel và điều chỉnh `sysctl` · giới hạn tài nguyên và `ulimit` · khởi động an toàn trên Linux nhúng

**Dùng để xây:** C6 (embedded Linux), C10 (vận hành).

**Checkpoint:** viết một unit systemd có chính sách khởi động lại đúng và một device tree overlay để kích hoạt một cảm biến trên SBC — cả hai chạy sau khi khởi động lại, không cần can thiệp tay.

## C4.13 · Quan sát kernel — `In→Ad`

**Sub-leaves:** `/proc` và `/sys` — đọc gì ở đâu · `ftrace` và tracepoint · `kprobe`/`uprobe` · eBPF: mô hình chương trình, verifier, map · `bpftrace` cho script nhanh · `bcc` tools và cái nào dùng khi nào · tổng phí của việc trace và cách giữ nó thấp · trace trên hệ production

**Dùng để xây:** C11 (toàn bộ), chẩn đoán trong C10.

**Checkpoint:** dùng eBPF/`bpftrace` để trace một đường syscall và tìm ra nguồn latency trong một tình huống bạn dựng sẵn — không sửa code ứng dụng.

---

## ▸ Thứ tự học trong C4

```
1. Tiến trình + luồng + tín hiệu        (Phase 1, ~40 h)
2. Bộ nhớ ảo + phân trang               (Phase 1–2, ~45 h)
3. Nguyên thủy concurrency              (Phase 2, ~50 h)
4. Bế tắc + chẩn đoán                   (Phase 2, ~25 h)
5. Mô hình I/O + vòng lặp sự kiện       (Phase 2, ~50 h)
6. Hệ thống file + độ bền               (Phase 2, ~40 h)
7. Lập lịch                             (Phase 2, ~30 h)
8. IPC                                  (Phase 2, ~25 h)
9. Mẫu concurrency kiến trúc            (Phase 3, ~30 h)
10. RTOS                                (Phase 3, ~45 h)  ← cùng lúc C6
11. Container + namespace/cgroup        (Phase 3, ~30 h)
12. Linux nền tảng                      (Phase 3, ~25 h)
13. Quan sát kernel (eBPF)              (Phase 4, ~25 h)
```

## ▸ Tài nguyên chính C4

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| *Operating Systems: Three Easy Pieces* (OSTEP) — **miễn phí toàn văn** | University of Wisconsin–Madison | C4.1–C4.6 | 120 |
| Project của CS 537 (đi kèm OSTEP) | UW–Madison | thực hành | 60 |
| *The Linux Programming Interface* (Kerrisk) — tra cứu | — | C4.9, C4.12 | 40 |
| Linux man pages (mục 2 và 7) | — | primary source, tra liên tục | — |
| *Linux Kernel Development* (Love) hoặc kernel docs | — | C4.12, C4.13 | 25 |
| FreeRTOS documentation + Zephyr documentation | FreeRTOS / Zephyr Project | C4.10 | 35 |
| Tài liệu và công cụ eBPF của Brendan Gregg | — | C4.13 | 25 |
| *Is Parallel Programming Hard* (McKenney) — miễn phí | — | C4.6, C4.7 nâng cao | 30 |
| xv6 (kernel giáo dục) + book | MIT | tùy chọn, đọc code kernel thật | 40 |

---

# ◆ C5 · NETWORKING

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~350 h · Phase 2: 200 h · Phase 3: 100 h · Phase 4: 50 h
**Vị trí:** con của OS; chặn Distributed Systems và toàn bộ tầng transport của vòng lặp.
**Vì sao Advanced:** hệ end-to-end **là** hệ mạng. Đây là nhánh có khoảng cách lớn nhất giữa *giá trị thật* và *mức đầu tư thông thường* — hầu hết engineer dừng ở mức Working và trả giá suốt sự nghiệp.

## C5.1 · Nền tảng: tín hiệu, khung, địa chỉ, phân tầng — `Wo→In`

**Sub-leaves:** mã hóa tín hiệu và tốc độ baud vs bit · đóng khung và phát hiện ranh giới · phát hiện lỗi: parity, checksum, CRC · địa chỉ: phẳng vs phân cấp · mô hình OSI và TCP/IP — cái nào mô tả thực tế · đóng gói và MTU · song công, bán song công, miền va chạm · vì sao phân tầng vừa giúp vừa che giấu lỗi

**Checkpoint:** tính được CRC của một khung bằng tay (hoặc code từ đầu), và giải thích được tại sao CRC bắt được lỗi burst mà checksum đơn giản bỏ sót.

## C5.2 · Tầng liên kết: Ethernet, ARP, chuyển mạch — `Wo→In`

**Sub-leaves:** khung Ethernet và địa chỉ MAC · ARP: hoạt động, cache, gratuitous ARP, ARP spoofing · chuyển mạch vs hub, học địa chỉ, bảng CAM · VLAN và tagging 802.1Q · spanning tree ở mức khái niệm · jumbo frame và MTU đường truyền · PoE ở mức khái niệm (liên quan tới triển khai thiết bị)

**Checkpoint:** đọc bảng ARP, dựng một tình huống IP trùng lặp trong lab, và giải thích chính xác triệu chứng quan sát được.

## C5.3 · Tầng liên kết cho edge: Wi-Fi, BLE, LoRa, Zigbee, cellular — `In→Ad`

**Sub-leaves:**
- Wi-Fi: 802.11 a/b/g/n/ac/ax, băng tần, kênh, nhiễu; chế độ tiết kiệm năng lượng; thời gian kết nối lại
- BLE: quảng bá vs kết nối, GATT, khoảng cách kết nối và ảnh hưởng tới pin, BLE mesh
- LoRa/LoRaWAN: điều chế chirp spread spectrum, hệ số trải, đánh đổi tầm–tốc độ, chu kỳ nhiệm vụ và giới hạn pháp lý
- Zigbee/Thread/Matter ở mức khái niệm
- Cellular: NB-IoT, LTE-M — khi nào đáng, chi phí, độ trễ
- Ngân sách liên kết (link budget): công suất phát, độ nhạy thu, suy hao đường truyền
- RSSI, SNR, tỷ lệ mất gói và đọc chúng đúng
- Nhiễu và chia sẻ phổ trong băng tần ISM

**Dùng để xây:** C6, mọi triển khai thiết bị ngoài thực địa.

**Checkpoint:** cho ba kịch bản (băng thông cao/tầm xa/pin năm), chọn được radio đúng cho mỗi cái, tính ngân sách liên kết, và **đo thực tế** để xác nhận hoặc bác bỏ tính toán.

**Cạm bẫy:** tin vào con số tầm xa trong datasheet. Tầm thật trong môi trường đô thị thường là 10–30% con số quảng cáo.

## C5.4 · Tầng mạng: IP, subnetting, NAT, routing — `In→Ad`

**Sub-leaves:** IPv4 và IPv6 — khác biệt thực tế, không chỉ độ dài địa chỉ · subnetting và CIDR, tính bằng tay · ICMP và vai trò thật của nó (không chỉ ping) · NAT: các loại, hệ quả cho kết nối vào, giữ trạng thái · phân mảnh và path MTU discovery · định tuyến tĩnh và bảng định tuyến · OSPF và BGP ở mức khái niệm — đủ để hiểu sự cố Internet · multicast và broadcast · IP nguồn giả mạo và lọc đường vào

**Checkpoint:** chia subnet cho một mạng 200 thiết bị chia 5 nhóm, viết bảng định tuyến, và **truy vết đường đi của một gói** qua toàn bộ topology bằng lập luận, rồi xác nhận bằng `traceroute`.

## C5.5 · Tầng transport: TCP, UDP, QUIC — `Ad→Ex`

**Sub-leaves:**
- Bắt tay ba bước, đóng bốn bước, TIME_WAIT và vì sao nó tồn tại
- Số thứ tự, xác nhận, truyền lại, RTO và ước lượng RTT
- Điều khiển luồng: cửa sổ nhận, zero-window, silly window syndrome
- Điều khiển tắc nghẽn: slow start, congestion avoidance, fast retransmit/recovery
- Các thuật toán: Reno, CUBIC, BBR — khác nhau ở mô hình gì
- Thuật toán Nagle và `TCP_NODELAY`; ACK trễ và tương tác xấu giữa hai cái
- Keepalive, nửa mở, và phát hiện kết nối chết
- UDP: khi nào đúng, mất gói, thứ tự, phân mảnh
- QUIC: sao chép gì của TCP, sửa gì, head-of-line blocking ở đâu
- Kích thước bộ đệm socket và tích băng thông–độ trễ
- Tấn công SYN flood và cookie

**Dùng để xây:** toàn bộ C10, mọi vấn đề hiệu năng mạng.

**Checkpoint:** nhìn một packet capture của một kết nối không đạt thông lượng kỳ vọng, và **xác định đúng nguyên nhân** trong ít nhất ba tình huống khác nhau: giới hạn cửa sổ, mất gói gây tắc nghẽn, và tương tác Nagle/delayed-ACK.

## C5.6 · DNS — `In→Ad`

**Sub-leaves:** phân giải đệ quy vs lặp · các loại bản ghi và ý nghĩa vận hành · TTL và hành vi cache ở nhiều tầng · negative caching · phân giải phía client và thứ tự `/etc/hosts`, `nsswitch` · DNS qua UDP vs TCP, và DoT/DoH · DNSSEC ở mức khái niệm · service discovery bằng DNS (SRV record) · mDNS/Bonjour cho mạng cục bộ thiết bị · các chế độ hỏng của DNS trong hệ phân tán

**Checkpoint:** chẩn đoán một sự cố do DNS cache (ví dụ deploy xong nhưng một phần traffic vẫn đi về IP cũ) **bằng công cụ**, không đoán — chỉ ra tầng cache nào đang giữ bản ghi cũ.

## C5.7 · HTTP 1.1 / 2 / 3 — `In→Ad`

**Sub-leaves:** phương thức, mã trạng thái, và ngữ nghĩa idempotency · header, content negotiation, và mã hóa chuyển giao · keep-alive và pipelining (và vì sao pipelining thất bại) · HTTP/2: khung, ghép kênh luồng, nén HPACK, server push (và vì sao nó bị bỏ) · HTTP/3 trên QUIC: head-of-line blocking được giải quyết ở đâu · cache: `Cache-Control`, ETag, validation · CORS và mô hình bảo mật trình duyệt · thiết kế REST và giới hạn của nó · so sánh với gRPC và khi nào chọn cái nào

**Checkpoint:** giải thích chính xác head-of-line blocking xảy ra ở **tầng nào** trong HTTP/1.1, HTTP/2 và HTTP/3, và dựng được thí nghiệm chứng minh sự khác biệt.

## C5.8 · Giao thức messaging cho hệ thiết bị — `Ad`

**Sub-leaves:**
- MQTT: publish/subscribe, chủ đề và ký tự đại diện, mức QoS 0/1/2 và ngữ nghĩa thật của chúng, phiên bền vững, thông điệp giữ lại, last-will-and-testament
- MQTT-SN cho mạng không TCP
- CoAP: mô hình REST trên UDP, observe, block-wise transfer
- AMQP ở mức khái niệm và khi nào nó hơn MQTT
- gRPC: protobuf, streaming, deadline, interceptor
- WebSocket: bắt tay, khung, và khi nào nó là lựa chọn sai
- Server-Sent Events
- Định dạng tuần tự hóa: JSON, protobuf, CBOR, MessagePack, FlatBuffers — đánh đổi kích thước/tốc độ/schema
- Tiến hóa schema trong giao thức nối dây
- Chọn giao thức theo ràng buộc: pin, băng thông, độ trễ, độ tin cậy

**Dùng để xây:** mối nối B ở §4.2 — xương sống edge↔cloud.

**Checkpoint:** cho bốn kịch bản (cảm biến chạy pin báo mỗi giờ / điều khiển thời gian thực / truyền tệp lớn / telemetry tần suất cao), chọn giao thức + mức QoS cho mỗi cái và **bảo vệ bằng số**: byte trên đường truyền, số lần thức dậy radio, năng lượng mỗi thông điệp.

**Cạm bẫy:** dùng MQTT QoS 2 vì nó "đảm bảo nhất". QoS 2 tốn 4 lượt đi-về; với thiết bị chạy pin đó thường là lựa chọn sai, và idempotency ở tầng ứng dụng rẻ hơn nhiều.

## C5.9 · TLS, PKI, chứng chỉ — `In→Ad`

**Sub-leaves:** bắt tay TLS 1.2 vs 1.3 và số lượt đi-về · bộ mã hóa, trao đổi khóa, bí mật chuyển tiếp hoàn hảo · chuỗi chứng chỉ, CA, và xác thực · mTLS: xác thực hai chiều cho thiết bị · vòng đời chứng chỉ: cấp phát, gia hạn, thu hồi (CRL, OCSP) · ghim chứng chỉ (pinning) và rủi ro của nó · TLS trên MCU: chi phí bộ nhớ và CPU, hỗ trợ phần cứng · PSK và khi nào nó hợp lý cho thiết bị nhỏ · xoay vòng khóa mà không làm gián đoạn dịch vụ

**Dùng để xây:** S4, mọi triển khai thật.

**Checkpoint:** dựng mTLS giữa một MCU và một server, **bao gồm** quy trình cấp phát ban đầu và xoay vòng chứng chỉ khi hết hạn — chứng minh thiết bị vẫn kết nối được sau khi chứng chỉ cũ hết hạn.

## C5.10 · Lập trình socket & vòng lặp sự kiện — `Ad`

**Sub-leaves:** API socket: `socket`, `bind`, `listen`, `accept`, `connect` · xử lý đọc/ghi một phần — nguồn lỗi phổ biến nhất · tùy chọn socket: `SO_REUSEADDR`, `TCP_NODELAY`, kích thước bộ đệm · socket không chặn + `epoll` · timeout ở mọi tầng · tắt duyên dáng và ngữ nghĩa half-close · quản lý kết nối: pool, giới hạn, thời gian sống · phân giải tên trong code · IPv4/IPv6 dual-stack và Happy Eyeballs

**Checkpoint:** tự viết một TCP server từ socket thuần (không dùng framework), xử lý đúng partial read/write, tắt duyên dáng, và timeout; chịu được 10.000 kết nối đồng thời.

## C5.11 · Hiệu năng mạng — `Ad`

**Sub-leaves:** độ trễ vs thông lượng — hai thứ khác nhau · tích băng thông–độ trễ và kích thước cửa sổ · MTU, phân mảnh, và MSS · bufferbloat: nguyên nhân, triệu chứng, AQM (CoDel, FQ-CoDel) · ngân sách độ trễ xuyên nhiều chặng · CDN và edge caching · nén: khi nào nó thắng, khi nào nó tốn CPU vô ích · gộp kết nối và chi phí bắt tay · đo: `iperf`, `ping`, `mtr`, phân tích packet capture

**Checkpoint:** dựng ngân sách độ trễ cho một request đi qua 5 tầng (thiết bị → gateway → broker → xử lý → lưu trữ), dự đoán p50 và p99 **trước khi đo**, rồi đo và giải thích chênh lệch.

## C5.12 · Bắt gói & phân tích — `Ad`

**Sub-leaves:** `tcpdump` và cú pháp bộ lọc BPF · Wireshark: theo dõi luồng, đồ thị I/O, biểu đồ thời gian chuỗi TCP · bắt gói ở đâu (client, server, giữa đường) và vì sao vị trí quan trọng · bắt gói trên hệ mã hóa: cái gì vẫn thấy được · bắt trên thiết bị nhúng · lấy mẫu và bắt gói vòng cho hệ production · phân tích lưu lượng không mã hóa của giao thức nhị phân

**Checkpoint:** dùng Wireshark tìm ra nguyên nhân của một kết nối bị treo — phân biệt được ba khả năng: mất gói, tường lửa im lặng, và ứng dụng không đọc.

## C5.13 · Mạng trên cloud — `In→Ad`

**Sub-leaves:** VPC, subnet, bảng định tuyến, gateway · security group vs network ACL · cân bằng tải: L4 vs L7, thuật toán, health check · kiểm tra sức khỏe và ngữ nghĩa loại bỏ · service mesh: sidecar, mTLS tự động, chính sách lưu lượng · mạng overlay cho container (CNI) · DNS trong cluster và service discovery · ingress, egress, và chi phí truyền dữ liệu · kết nối riêng (VPN, peering, direct connect)

**Checkpoint:** vẽ chính xác đường đi của một gói tin từ Internet công cộng tới một container trong cluster, liệt kê mọi thành phần nó đi qua, và xác định được nơi mTLS bắt đầu và kết thúc.

## C5.14 · Kết nối cho thiết bị ngoài thực địa — `In→Ad`

**Sub-leaves:** vượt NAT: STUN, TURN, ICE ở mức khái niệm · kết nối khởi tạo từ thiết bị (outbound-only) như mẫu thiết kế · chiến lược kết nối lại: backoff, jitter, ngưỡng từ bỏ · thiết kế offline-first: hàng đợi cục bộ, giới hạn, chính sách loại bỏ · đồng bộ sau khi trở lại trực tuyến: backfill, dedup, thứ tự · phát hiện mạng chất lượng kém vs mất mạng hoàn toàn · dự phòng nhiều đường truyền (Wi-Fi → cellular) · bảo tồn năng lượng khi kết nối kém

**Dùng để xây:** mối nối B, P3, P4, P6.

**Checkpoint:** thiết bị mất mạng **6 giờ liên tục** rồi khôi phục: không mất dữ liệu, không trùng dữ liệu, thứ tự đúng, và không gây tăng đột biến tải lên server khi đồng bộ (kiểm chứng bằng đồ thị tải).

## C5.15 · Chế độ hỏng của mạng — `Ad`

**Sub-leaves:** phân vùng mạng và phân vùng một chiều · lỗi xám (gray failure): chậm nhưng không chết · retry storm và sụp đổ do tắc nghẽn (congestion collapse) · thundering herd và cách phân tán · DNS hỏng nhưng kết nối hiện có vẫn sống · tường lửa im lặng thả gói vs từ chối rõ ràng · rò rỉ mô tả file do kết nối không đóng · lỗi cạn kiệt cổng ephemeral · đồng hồ lệch gây hỏng TLS

**Checkpoint:** tái tạo một retry storm trong lab (nhiều client retry đồng bộ), quan sát sụp đổ, rồi dập bằng jitter + circuit breaker và chứng minh bằng đồ thị.

---

## C5.16 · Giao thức công nghiệp (OT) — `In→Ad`

*Leaf bổ sung ở v3. Đây là lỗ hổng độ phủ của v2 — nó thuộc về nhánh này bất kể người học làm nghề gì, vì mọi hệ có tài sản vật lý đều gặp ít nhất một giao thức trong nhóm này.*

**Sub-leaves:**
- **Modbus** RTU và TCP: register map, function code, endianness, giới hạn cơ bản (không có schema, không có phát hiện thiết bị)
- **Profibus DP** và **Profinet**: RT vs IRT, mô hình nhà cung cấp/người tiêu dùng, GSD/GSDML
- **EtherCAT** và khái niệm distributed clock
- **IEC 61850** cho tự động hóa trạm: mô hình dữ liệu phân cấp, MMS, GOOSE, Sampled Values, file SCL
- **IEC 60870-5-104** và **DNP3** cho telemetry SCADA tới trung tâm điều độ
- **HART** và cảm biến thông minh trên vòng 4–20 mA
- **CAN/CANopen**, **BACnet** (tòa nhà), **M-Bus** (đo đếm)
- **OPC UA**: mô hình thông tin, client-server vs PubSub, companion specification, và vì sao nó là cầu nối IT/OT được chọn
- Gateway giao thức: dịch giữa các thế giới, và cái mất trong mỗi lần dịch
- Đánh đổi chung: xác định thời gian, chi phí, bề rộng hỗ trợ, khả năng mô tả dữ liệu
- So sánh với nhóm giao thức IT (MQTT, gRPC, HTTP) ở C5.8 — cái gì tương đương, cái gì không

**Dùng để xây:** mọi cầu nối giữa tầng thiết bị công nghiệp và tầng dữ liệu hiện đại; đây là đường dẫn dữ liệu của bất kỳ hệ IIoT nào.

**Checkpoint:** đọc dữ liệu từ một thiết bị công nghiệp thật qua giao thức gốc của nó, đưa lên một hệ hiện đại (MQTT hoặc time-series store), **và viết ra chính xác cái gì bị mất trong quá trình dịch** — kiểu dữ liệu, timestamp, chất lượng, ngữ nghĩa.

**Cạm bẫy:** coi mọi giao thức OT là "cũ và tệ". Nhiều thứ trong nhóm này giải quyết bài toán mà giao thức IT không giải quyết — tính xác định thời gian, hoạt động trên đường truyền cực hạn chế, và vòng đời 20 năm. Hiểu **vì sao** chúng được thiết kế như vậy có giá trị hơn nhiều so với chê chúng.


## ▸ Thứ tự học trong C5

```
1. Nền tảng + tầng liên kết            (Phase 2, ~25 h)
2. IP + subnetting + routing           (Phase 2, ~35 h)
3. TCP/UDP sâu ★                       (Phase 2, ~60 h)  ← đầu tư nặng nhất
4. Lập trình socket + vòng lặp sự kiện (Phase 2, ~50 h)  ← song song với C4.5
5. Bắt gói + phân tích                 (Phase 2, ~25 h)  ← sớm, dùng suốt
6. DNS                                 (Phase 2, ~20 h)
7. HTTP 1/2/3                          (Phase 2–3, ~25 h)
8. TLS + PKI                           (Phase 3, ~30 h)
9. Giao thức messaging (MQTT/CoAP/gRPC)(Phase 3, ~35 h)  ← cùng lúc C6
10. Radio cho edge                     (Phase 3, ~30 h)  ← cùng lúc C6
11. Hiệu năng mạng                     (Phase 3, ~25 h)
12. Kết nối thiết bị ngoài thực địa    (Phase 3, ~25 h)
13. Mạng cloud                         (Phase 4, ~25 h)
14. Chế độ hỏng                        (Phase 4, ~20 h)
```

## ▸ Tài nguyên chính C5

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| CS144 *Introduction to Computer Networking* + **lab tự viết TCP** | Stanford | C5.1–C5.5, C5.10 | 120 |
| *Computer Networking: A Top-Down Approach* (Kurose & Ross) | — | tham chiếu nền | 40 |
| *TCP/IP Illustrated Vol. 1* (Stevens) | — | C5.5 sâu | 35 |
| *Beej's Guide to Network Programming* — miễn phí | — | C5.10 khởi động | 10 |
| RFC 9293 (TCP), RFC 9110–9114 (HTTP), RFC 9000 (QUIC) | IETF | primary source | 25 |
| MQTT 5.0 specification | OASIS | C5.8 — primary source | 12 |
| *High Performance Browser Networking* (Grigorik) — miễn phí | — | C5.7, C5.11 | 25 |
| Wireshark documentation + sample capture | Wireshark Foundation | C5.12 | 20 |
| LoRa Alliance + Nordic/Espressif docs | LoRa Alliance / vendor | C5.3 | 25 |

---

# ◆ C6 · EMBEDDED SYSTEMS & FIRMWARE

**Mức mục tiêu:** **Advanced → Expert** (một trong 2–3 nhánh chạm Expert)
**Ngân sách:** ~460 h · Phase 1: 60 h · Phase 2: 80 h · Phase 3: 200 h · Phase 4–5: 120 h
**Vị trí:** con của OS + Computer Arch; là một đầu của "end-to-end".
**Vì sao Expert khả thi ở đây:** với phần cứng đã xác nhận và 6.600 h, nhánh này có vòng phản hồi chặt (bạn thấy ngay code sai) và phạm vi hữu hạn hơn ML. Expert nghĩa là: tự viết HAL và bootloader dùng được, chẩn đoán được lỗi phần cứng-phần mềm không điển hình, đánh giá được firmware của người khác.

## C6.1 · Kiến trúc MCU & đọc datasheet — `Ad→Ex` ★ nền của cả nhánh

**Sub-leaves:**
- Bản đồ bộ nhớ: flash, SRAM, peripheral, bit-banding
- Thanh ghi lõi và chế độ hoạt động (Cortex-M: Thread/Handler, MSP/PSP)
- Cây xung nhịp: nguồn dao động, PLL, bộ chia, và vì sao cấu hình sai làm chết mọi timing
- Miền nguồn và điều khiển xung nhịp peripheral
- NVIC: vector, độ ưu tiên, nhóm ưu tiên, ngắt lồng nhau
- Vector reset và mã khởi động (startup code)
- Cấu trúc datasheet vs reference manual vs errata — ba tài liệu khác nhau
- Đọc errata và vì sao nó quan trọng hơn bạn tưởng
- Bảng đặc tính điện: mức logic, dòng tối đa, thời gian thiết lập/giữ
- Sơ đồ chân, chức năng thay thế (alternate function), xung đột chân

**Dùng để xây:** toàn bộ C6.

**Checkpoint:** cấu hình một peripheral bạn chưa từng dùng (ví dụ bộ so sánh analog hoặc bộ mã hóa quay) **chỉ bằng reference manual và errata**, không dùng ví dụ có sẵn, không dùng thư viện HAL của nhà sản xuất.

**Cạm bẫy:** học embedded bằng cách copy ví dụ Arduino. Nó cho cảm giác tiến bộ nhanh và để lại lỗ hổng ở đúng chỗ quan trọng nhất.

## C6.2 · GPIO, timer, PWM, ngắt — `Ad`

**Sub-leaves:** cấu hình GPIO: kéo lên/xuống, open-drain, tốc độ slew, drive strength · chống dội (debounce) phần cứng và phần mềm · timer: chế độ đếm, prescaler, auto-reload, capture/compare · PWM: độ phân giải, tần số, dead-time cho half-bridge · input capture để đo tần số và độ rộng xung · encoder interface · ISR: viết đúng, giữ ngắn, biến `volatile`, phần cấp thấp vs cấp cao · độ trễ ngắt và jitter — đo được · ngắt lồng nhau và mức ưu tiên · vùng tới hạn và tắt ngắt — khi nào và bao lâu

**Checkpoint:** tạo tín hiệu PWM ở tần số và độ phân giải mục tiêu, đo bằng logic analyzer, xác nhận sai số dưới 0,1%; đồng thời đo độ trễ ngắt và giữ nó dưới 5 µs.

## C6.3 · Bus & giao tiếp ngoại vi — `Ad→Ex`

**Sub-leaves:**
- I²C: điều kiện start/stop, địa chỉ, ACK/NACK, clock stretching, arbitration, điện trở kéo lên và tính toán giá trị
- I²C khôi phục bus khi treo (bus recovery) — bài toán thực tế phổ biến
- SPI: chế độ CPOL/CPHA, chọn chip, full-duplex, tốc độ tối đa và signal integrity
- UART: baud rate, sai số xung nhịp, framing error, flow control, RS-485
- CAN: khung, arbitration, error frame, bus-off, terminator
- 1-Wire, I²S (cho audio), SDIO ở mức khái niệm
- Chọn bus theo ràng buộc: số dây, tốc độ, khoảng cách, nhiều thiết bị
- Debug bus bằng logic analyzer: đọc waveform thô

**Checkpoint:** debug một bus I²C "câm" (thiết bị không trả lời) **bằng logic analyzer**, xác định đúng nguyên nhân trong ba tình huống khác nhau: sai địa chỉ, thiếu điện trở kéo lên, và clock stretching không được hỗ trợ.

## C6.4 · ADC/DAC & giao diện analog — `In→Ad`

**Sub-leaves:** kiến trúc ADC: SAR, sigma-delta, flash — đánh đổi · độ phân giải danh nghĩa vs ENOB thực tế · thời gian lấy mẫu, trở kháng nguồn, và lỗi do sampling capacitor · điện áp tham chiếu: nội vs ngoại, độ trôi · kênh đa hợp và crosstalk · lấy mẫu đồng bộ với timer + DMA · oversampling và dithering để tăng độ phân giải hiệu dụng · DAC và PWM-as-DAC với bộ lọc RC · mạch điều hòa tín hiệu: bộ đệm, khuếch đại, chống aliasing · cảm biến nhiệt độ nội và bù

**Checkpoint:** đo ENOB thực tế của ADC trên board của bạn bằng thí nghiệm (histogram của tín hiệu DC, hoặc FFT của sóng sin), so với con số trong datasheet, và giải thích chênh lệch.

## C6.5 · DMA & đường dữ liệu không tải CPU — `In→Ad`

**Sub-leaves:** kênh DMA, luồng, ưu tiên · chế độ: memory-to-peripheral, peripheral-to-memory, memory-to-memory · scatter-gather và danh sách mô tả · chế độ vòng tròn (circular) cho luồng liên tục · ngắt nửa chừng và hoàn tất — đệm đôi · mạch lạc cache với DMA trên MCU có cache (Cortex-M7) · căn chỉnh bộ đệm DMA · lỗi DMA và phát hiện tràn · đo mức giảm tải CPU

**Checkpoint:** thu audio (hoặc luồng ADC) liên tục ở ≥16 kHz qua DMA vòng tròn với đệm đôi, chạy 1 giờ **không mất mẫu nào**, và chứng minh bằng bộ đếm mẫu.

## C6.6 · Ràng buộc bộ nhớ — `Ad→Ex`

**Sub-leaves:** phân vùng flash: code, hằng số, vùng dữ liệu, vùng OTA · bố cục SRAM: data, bss, heap, stack, vùng DMA · cấp phát tĩnh và vì sao firmware production tránh heap · phân mảnh heap trên hệ chạy lâu · đo stack usage: tô màu (painting), canary, phân tích tĩnh · nhiều stack (một cho mỗi tác vụ RTOS) và định cỡ · phần bộ nhớ tùy chỉnh trong linker script · lưu dữ liệu trong flash: emulated EEPROM, wear leveling · nén và lưu trữ hằng số · phân tích kích thước binary và cắt giảm

**Checkpoint:** chứng minh bằng đo đạc rằng firmware của bạn không tràn stack ở trường hợp xấu nhất — dùng cả stack painting lẫn phân tích tĩnh, và cho thấy hai phương pháp đồng ý với nhau.

## C6.7 · RTOS — `Ad`

**Sub-leaves:** tác vụ: tạo, độ ưu tiên, trạng thái, xóa · lập lịch: preemptive, cooperative, time-slicing · queue, semaphore, mutex, event group · thông báo tác vụ (task notification) — nhẹ hơn queue · kế thừa ưu tiên trong mutex của RTOS · giao tiếp ISR → tác vụ (API "FromISR") · timer phần mềm · phân bổ stack cho mỗi tác vụ · tick vs tickless idle · phân tích khả năng lập lịch với rate-monotonic · FreeRTOS vs Zephyr: mô hình driver, thiết bị cây, ecosystem · gỡ lỗi nhận biết RTOS (RTOS-aware debugging)

**Checkpoint:** chuyển một firmware superloop có 4 chức năng sang RTOS **mà không tạo ra race condition mới**; chứng minh bằng chạy 24 giờ liên tục dưới tải và kiểm tra bằng công cụ phân tích trace.

## C6.8 · Bare-metal vs RTOS vs Embedded Linux — `In→Ad`

**Sub-leaves:** superloop và máy trạng thái không chặn · khi nào bare-metal là lựa chọn đúng (và nó thường đúng hơn bạn nghĩ) · chi phí RTOS: RAM, flash, độ phức tạp, jitter · Embedded Linux: khi nào cần (kết nối phức tạp, hệ thống file, nhiều tiến trình) · MPU/MMU và ranh giới cách ly · thời gian khởi động ở ba mô hình · đánh đổi chi phí BOM · lộ trình nâng cấp và khả năng bảo trì

**Checkpoint:** cho ba kịch bản cụ thể, chọn đúng mô hình cho mỗi cái và bảo vệ bằng bảng so sánh định lượng: RAM, flash, thời gian khởi động, jitter, chi phí phát triển.

## C6.9 · Quản lý năng lượng — `Ad`

**Sub-leaves:** chế độ ngủ: sleep, stop, standby, shutdown — cái gì giữ lại, cái gì mất · nguồn đánh thức và độ trễ đánh thức · duty cycling và thiết kế xung quanh nó · dòng tiêu thụ ở mỗi chế độ — đo thật, không tin datasheet · dòng rò từ chân GPIO cấu hình sai · năng lượng của radio: thường chiếm 60–90% ngân sách · race-to-sleep vs chạy chậm · tính ngân sách năng lượng: dòng trung bình × thời gian · hóa học pin, đặc tính phóng điện, hiệu ứng nhiệt độ · đo năng lượng: shunt + ADC, hoặc máy phân tích năng lượng · thu hoạch năng lượng ở mức khái niệm

**Dùng để xây:** mọi thiết bị chạy pin; nối trực tiếp sang họ #37.

**Checkpoint:** thiết kế một node đạt mục tiêu tuổi thọ pin cho trước (ví dụ 1 năm với pin CR2032 hoặc 6 tháng với 18650), **có phép tính ngân sách năng lượng chứng minh trước**, sau đó đo thực tế trong ≥2 tuần và so sánh với dự đoán.

## C6.10 · Bootloader, OTA, rollback — `Ad→Ex` ★ leaf phân biệt sản phẩm với đồ chơi

**Sub-leaves:**
- Chuỗi khởi động: reset vector → bootloader → ứng dụng
- Phân vùng A/B và nhảy giữa các vùng
- Cập nhật giao hoán (swap) vs ghi đè trực tiếp
- Xác minh image: checksum, chữ ký, phiên bản
- Chống rollback (anti-rollback counter)
- Phục hồi khi mất điện giữa chừng cập nhật
- Chế độ phục hồi và cập nhật qua cổng vật lý
- Delta update để tiết kiệm băng thông
- Quản lý phiên bản và triển khai theo giai đoạn (staged rollout)
- Telemetry của quá trình cập nhật: bao nhiêu thiết bị thành công, bao nhiêu quay lui
- MCUboot và các bootloader mở khác

**Checkpoint:** thực hiện OTA và **cắt điện ở ba thời điểm khác nhau** trong quá trình cập nhật (đang tải, đang ghi, đang chuyển đổi); ở cả ba trường hợp thiết bị vẫn boot được và chạy được một phiên bản hợp lệ. Chứng minh bằng thử nghiệm lặp lại ≥20 lần.

**Cạm bẫy:** để leaf này tới cuối. OTA là thứ quyết định bạn có dám triển khai thiết bị ở nơi không với tới được hay không — thiết kế nó từ đầu, không bổ sung sau.

## C6.11 · Debug phần cứng — `Ad→Ex`

**Sub-leaves:** JTAG và SWD — giao thức và giới hạn · OpenOCD, probe (ST-Link, J-Link, DAPLink) · breakpoint phần cứng vs phần mềm, số lượng giới hạn · watchpoint trên truy cập bộ nhớ · ITM/SWO trace cho log không chặn · ETM trace ở mức khái niệm · logic analyzer: kích hoạt, giải mã giao thức, timing analysis · oscilloscope: đo sườn, nhiễu, glitch, ringing · debug trên hệ chạy tốc độ đầy đủ mà không dừng · phân tích crash: fault handler, đọc stack frame từ HardFault · postmortem: lưu thông tin crash vào flash và đọc lại sau

**Checkpoint:** tìm được một bug **chỉ xuất hiện khi chạy tốc độ đầy đủ** (biến mất khi step qua debugger) — dùng SWO trace hoặc logic analyzer, không dùng breakpoint.

## C6.12 · Kiến trúc firmware — `Ad`

**Sub-leaves:** phân tầng: driver → HAL → middleware → ứng dụng · viết HAL riêng vs dùng của nhà sản xuất — đánh đổi · tách logic khỏi phần cứng để test được trên PC · tiêm phụ thuộc trong C (con trỏ hàm, struct vtable) · máy trạng thái làm khung chính · mẫu lập lịch không chặn · xử lý lỗi trong firmware: mã lỗi, assert, fault handler · cấu hình và tham số có thể điều chỉnh · logging trên hệ hạn chế tài nguyên · unit test firmware trên máy host · tích hợp liên tục cho firmware

**Checkpoint:** chạy được **≥60% logic firmware** dưới unit test trên PC (không cần phần cứng), với phần cứng được giả lập qua giao diện HAL — và test này chạy trong CI.

## C6.13 · Bảo mật thiết bị — `In→Ad`

**Sub-leaves:** secure boot: chuỗi tin cậy từ ROM · lưu khóa: fuse, OTP, secure element (ATECC, SE050) · định danh thiết bị và cấp phát ban đầu (provisioning) tại nhà máy · mã hóa flash và bảo vệ đọc ngược (readout protection) · vô hiệu hóa giao diện debug trong sản phẩm · tấn công vật lý ở mức awareness: glitch, side-channel · cập nhật firmware có chữ ký · quản lý bí mật khi mã nguồn mở · mô hình mối đe dọa cho thiết bị ngoài tầm kiểm soát vật lý

**Checkpoint:** cấp phát định danh cho một thiết bị, kích hoạt secure boot, và chứng minh rằng firmware không được ký **không boot được** — và rằng bạn không thể đọc khóa ra khỏi thiết bị qua giao diện debug.

## C6.14 · Inference trên thiết bị — `Ad→Ex`

**Sub-leaves:**
- Đường ống từ model tới firmware: train → lượng tử hóa → chuyển đổi → tích hợp
- TFLite Micro: cấu trúc, arena bộ nhớ, giải quyết toán tử
- Độ phủ toán tử: model của bạn không chạy vì sao và làm gì
- Lập kế hoạch bộ nhớ tĩnh cho tensor arena
- Lượng tử hóa sau huấn luyện vs nhận biết lượng tử hóa trên MCU
- Đo latency inference và jitter của nó
- Ngân sách năng lượng cho mỗi lần inference
- NPU cấp MCU: toolchain, hạn chế, khi nào đáng dùng
- Edge Impulse và các nền tảng tương tự: dùng để học workflow, rồi tự dựng lại
- Đường ống trích xuất đặc trưng trên thiết bị (nối sang C7)
- Tầng chính sách: không đưa output model thẳng tới actuator
- Cập nhật model qua OTA tách biệt với cập nhật firmware

**Checkpoint:** chạy một model phát hiện bất thường trên MCU trong ngân sách RAM cho trước (ví dụ < 128 KB tensor arena), đo được latency p99 và năng lượng mỗi lần inference, và chứng minh độ chính xác trên một eval set bạn thu thập từ **thiết bị thật**, không từ dataset công khai.

## C6.15 · Ràng buộc thời gian thực — `In→Ad`

**Sub-leaves:** deadline cứng vs mềm vs vững (firm) · WCET: ước lượng bằng đo và bằng phân tích · nguồn của tính không tất định: cache, DMA, ngắt, DVFS · jitter: đo, ngân sách, giảm thiểu · phân tích thời gian đáp ứng cho tập tác vụ · vùng tới hạn và độ dài tối đa cho phép · watchdog: phần cứng, cửa sổ, đa tầng · trạng thái an toàn khi vi phạm deadline · ghi nhận vi phạm timing để phân tích sau

**Checkpoint:** chứng minh một tác vụ luôn hoàn thành trong deadline **dưới tải xấu nhất bạn có thể tạo ra** — bao gồm khi DMA đang chạy, khi mọi ngắt đang bắn, và khi flash đang được ghi.

---

## C6.16 · PLC và DCS như mô hình tính toán thứ tư — `In→Ad`

*Leaf bổ sung ở v3. C6.8 của v2 so sánh ba mô hình: bare-metal, RTOS, embedded Linux. Thiếu mô hình thứ tư, vốn đang điều khiển phần lớn hạ tầng vật lý của thế giới.*

**Sub-leaves:**
- Mô hình scan cycle: đọc ảnh vào → thực thi → ghi ảnh ra; và vì sao mô hình này cho tính xác định
- Process image và ngữ nghĩa của nó — khác với truy cập I/O trực tiếp thế nào
- **IEC 61131-3**: LD, FBD, ST, IL, SFC — mỗi ngôn ngữ cho loại bài toán nào
- Khối tổ chức và tác vụ chu kỳ; ngắt phần cứng trong thế giới PLC
- Thời gian chu kỳ, giám sát chu kỳ, và tương ứng với WCET ở C6.15
- Khối dữ liệu, biến giữ lại (retentive), và trạng thái sống sót qua mất điện
- **DCS vs PLC vs PAC**: khác biệt thật (kiến trúc điều khiển phân tán, kỹ thuật tập trung) chứ không phải khác biệt marketing
- Dự phòng trong PLC/DCS: CPU nóng dự phòng, I/O dự phòng, chuyển đổi không va đập
- Kỹ thuật an toàn: PLC an toàn, kênh kép, và vì sao logic an toàn tách khỏi logic điều khiển
- Vòng đời kỹ thuật: FAT → SAT → commissioning → bàn giao, và tài liệu đi kèm
- Vì sao PLC tồn tại thay vì dùng MCU: bảo hành, chứng nhận, vòng đời 20 năm, nhân lực thay thế được
- **Ánh xạ sang khái niệm trung lập** (bảng §2.3d) — đây là sub-leaf quan trọng nhất

**Dùng để xây:** hiểu tầng điều khiển của mọi hệ công nghiệp; và hiểu **ranh giới** giữa nó với tầng phần mềm hiện đại — nơi bạn sẽ làm việc.

**Checkpoint:** cho một bài toán điều khiển cụ thể, lập luận chọn PLC / MCU với RTOS / embedded Linux, bằng bảng định lượng (tính xác định, chi phí, vòng đời, chứng nhận, nhân lực bảo trì). Và: viết được cùng một logic điều khiển ở cả hai thế giới — ST trên PLC và C trên MCU — rồi so sánh cái gì dễ hơn ở mỗi bên và vì sao.

**Cạm bẫy đối xứng, cả hai đều phổ biến:**
- Kỹ sư phần mềm coi PLC là công nghệ lạc hậu → bỏ lỡ việc nó giải bài toán tính xác định và độ tin cậy mà họ chưa từng phải giải
- Kỹ sư tự động hóa coi phần mềm hiện đại là không đáng tin → bỏ lỡ 40 năm tiến bộ về kiểm soát phiên bản, test, và khả năng tiến hóa

Người đứng giữa hai bên có giá trị chính vì rất ít người chịu học cả hai.


## ▸ Thứ tự học trong C6

```
1. Blink + GPIO + toolchain              (Phase 1, ~25 h)  ← khởi động sớm
2. Đọc datasheet + kiến trúc MCU ★       (Phase 1–2, ~60 h)
3. Timer, PWM, ngắt                      (Phase 2, ~40 h)
4. Bus: I2C, SPI, UART                   (Phase 2, ~45 h)
5. Debug phần cứng (logic analyzer)      (Phase 2, ~30 h)  ← sớm, dùng suốt
6. ADC + giao diện analog                (Phase 3, ~35 h)  ← cùng lúc C7
7. DMA                                   (Phase 3, ~25 h)
8. Ràng buộc bộ nhớ                      (Phase 3, ~30 h)
9. RTOS                                  (Phase 3, ~45 h)  ← cùng lúc C4.10
10. Bare-metal vs RTOS vs Linux          (Phase 3, ~15 h)
11. Quản lý năng lượng                   (Phase 3, ~35 h)
12. Kiến trúc firmware + test trên host  (Phase 3, ~35 h)
13. Bootloader + OTA ★                   (Phase 3–4, ~50 h)
14. Inference trên thiết bị ★            (Phase 4, ~50 h)  ← sau C8
15. Bảo mật thiết bị                     (Phase 4, ~25 h)
16. Ràng buộc thời gian thực             (Phase 4, ~25 h)
```

## ▸ Tài nguyên chính C6

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| Reference manual + datasheet + errata của MCU bạn chọn | ST / Espressif / Nordic / NXP | C6.1–C6.5 — **primary source, đọc nhiều nhất** | 100 |
| ARM Cortex-M Generic User Guide | ARM | C6.1, C6.2 | 25 |
| FreeRTOS documentation + *Mastering the FreeRTOS Kernel* — miễn phí | FreeRTOS | C6.7 | 35 |
| Zephyr Project documentation | Zephyr Project / Linux Foundation | C6.7, C6.8, C6.12 | 35 |
| MCUboot documentation | MCUboot project | C6.10 | 20 |
| *Making Embedded Systems* (White) | — | C6.12 kiến trúc | 20 |
| *Test-Driven Development for Embedded C* (Grenning) | — | C6.12 test trên host | 25 |
| TensorFlow Lite Micro documentation + *TinyML* (Warden & Situnayake) | Google / — | C6.14 | 40 |
| Edge AI Foundation — tài liệu và talk công khai | Edge AI Foundation | C6.14 trạng thái hiện tại | 15 |
| Edge Impulse documentation | Edge Impulse | C6.14 — học workflow rồi tự dựng lại | 20 |
| Ứng dụng note của nhà sản xuất (AN/UM) | vendor | mọi leaf — thường tốt hơn sách | 40 |

---

# ◆ C7 · SENSING, SIGNALS & PHYSICAL INTERFACE

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~260 h · Phase 2: 40 h · Phase 3: 160 h · Phase 4: 60 h
**Vị trí:** con của Embedded; là đầu `sense` và đầu `act` của vòng lặp. Gom sub-part core từ họ #2, #3, #6, #31, #32, #37.
**Vì sao Advanced:** chất lượng ở đây **đặt trần cho mọi tầng phía trên**. Một model hoàn hảo trên dữ liệu chưa hiệu chuẩn vẫn cho kết quả sai, và sai theo cách metric không phát hiện được.

## C7.1 · Định lý lấy mẫu, aliasing, Nyquist — `Ad`

**Sub-leaves:** định lý Nyquist–Shannon và điều kiện của nó · aliasing: cơ chế, và vì sao dữ liệu bị alias trông hoàn toàn hợp lý · bộ lọc chống aliasing: tại sao phải là analog, đặt trước ADC · oversampling và giảm mẫu có lọc · undersampling có chủ đích (bandpass sampling) · jitter của xung nhịp lấy mẫu và ảnh hưởng tới SNR · lấy mẫu không đều và hệ quả · tần số lấy mẫu thực tế vs danh nghĩa

**Checkpoint:** tái tạo aliasing bằng thí nghiệm vật lý — lấy mẫu một tín hiệu có tần số cao hơn Nyquist, quan sát tần số giả xuất hiện, dự đoán chính xác tần số đó bằng công thức, rồi sửa bằng bộ lọc chống aliasing và chứng minh nó biến mất.

**Cạm bẫy:** đây là leaf mà sai lầm **không tạo ra lỗi**. Hệ thống vẫn chạy, dữ liệu vẫn trông hợp lý, model vẫn hội tụ — chỉ là kết quả sai. Không có cách nào phát hiện từ tầng trên.

## C7.2 · Lượng tử hóa, độ phân giải ADC, sàn nhiễu — `In→Ad`

**Sub-leaves:** nhiễu lượng tử hóa và SNR lý thuyết (6,02N + 1,76 dB) · ENOB và cách đo nó thật · nguồn nhiễu: nhiệt (Johnson), shot, flicker (1/f) · sàn nhiễu của toàn chuỗi đo · dải động và headroom · dithering để tăng độ phân giải hiệu dụng · trung bình hóa: giảm nhiễu theo √N và giới hạn của quy tắc đó · phi tuyến: INL, DNL · trôi theo nhiệt độ và thời gian

**Checkpoint:** tính sàn nhiễu lý thuyết của chuỗi đo của bạn, đo thực tế bằng thí nghiệm (histogram tín hiệu DC hoặc FFT), và giải thích chênh lệch — chỉ ra nguồn nhiễu nào chiếm ưu thế.

## C7.3 · Lọc số — `In→Ad`

**Sub-leaves:** FIR: đáp ứng xung, pha tuyến tính, thiết kế bằng cửa sổ · IIR: Butterworth, Chebyshev, biquad, và vấn đề ổn định · đánh đổi: bậc lọc ↔ độ trễ ↔ tài nguyên tính toán · trung bình trượt và trung bình trượt hàm mũ — lọc rẻ nhất · lọc trung vị cho nhiễu xung · đáp ứng tần số, đáp ứng pha, độ trễ nhóm · thực hiện điểm cố định và vấn đề tràn/làm tròn · lọc đa tốc độ: decimation, interpolation · lọc adaptive ở mức khái niệm

**Checkpoint:** thiết kế một bộ lọc đạt đồng thời ba yêu cầu cho trước: dải thông, độ suy giảm dải chặn, và độ trễ tối đa; cài trên MCU bằng số học phù hợp; đo đáp ứng tần số thực tế và so với thiết kế.

## C7.4 · FFT & phân tích phổ — `In→Ad`

**Sub-leaves:** DFT và FFT — thuật toán và độ phức tạp · rò rỉ phổ và hàm cửa sổ (Hann, Hamming, Blackman, flat-top) · độ phân giải tần số vs độ phân giải thời gian — nguyên lý bất định · STFT và spectrogram · mật độ phổ công suất và phương pháp Welch · nhận diện đỉnh và nội suy đỉnh · phân tích cepstrum ở mức khái niệm · FFT trên MCU: CMSIS-DSP, ràng buộc bộ nhớ · ứng dụng: phân tích rung động máy, âm thanh, phát hiện tần số lỗi

**Checkpoint:** gắn cảm biến gia tốc lên một động cơ (quạt, bơm), thu tín hiệu, tìm tần số quay cơ bản và các harmonic, và **phát hiện được một bất thường bạn cố ý tạo ra** (ví dụ thêm khối lượng lệch tâm) từ phổ.

## C7.5 · Nhiễu, nhiễu điện từ, và tính toàn vẹn tín hiệu — `Wo→In`

**Sub-leaves:** nguồn nhiễu: nguồn chuyển mạch, xung nhịp số, radio, động cơ · ghép nối: dẫn, cảm ứng, điện dung, bức xạ · vòng lặp đất (ground loop) và cách phá vỡ · nối đất một điểm vs mặt phẳng đất · tách nguồn: tụ decoupling, vị trí, giá trị · cặp vi sai và loại bỏ nhiễu chung · che chắn và bộ lọc ferrite · cách ly: opto, cách ly số, biến áp · đi dây cho tín hiệu analog nhạy · đo nhiễu: scope với đầu dò đúng cách

**Checkpoint:** giảm nhiễu trên một đường đo analog **≥10 dB** bằng thay đổi phần cứng hoặc đi dây, với số đo trước/sau bằng scope hoặc bằng độ lệch chuẩn của tín hiệu DC.

## C7.6 · Loại cảm biến & chế độ hỏng — `In→Ad`

**Sub-leaves:**
- IMU (gia tốc + con quay + từ kế): bias, scale factor, misalignment, trôi tích phân
- Nhiệt độ: NTC, RTD, cặp nhiệt, IC số — độ chính xác vs dải đo
- Dòng điện: shunt, Hall, biến dòng — cách ly và dải động
- Áp suất, độ ẩm, khí — phụ thuộc chéo và lão hóa
- Microphone: MEMS vs electret, I²S vs analog, hướng tính
- Camera: phơi sáng, gain, rolling shutter, băng thông
- Cảm biến quang: quang trở, photodiode, ToF
- Chế độ hỏng chung: bão hòa, đứt kết nối, trôi, kẹt giá trị, nhiễu tăng dần
- Phát hiện cảm biến hỏng **từ dữ liệu** (nối sang C9.13)
- Lão hóa và lịch bảo trì

**Checkpoint:** với mỗi loại cảm biến bạn dùng, viết ra ≥3 chế độ hỏng và **cơ chế phát hiện cụ thể từ dữ liệu**; sau đó tạo ra từng chế độ hỏng trong thực tế và xác nhận cơ chế phát hiện hoạt động.

## C7.7 · Hiệu chuẩn & metrology — `In→Ad` ★ leaf ít được dạy nhất

**Sub-leaves:**
- Khái niệm: độ chính xác vs độ chụm, sai số hệ thống vs ngẫu nhiên
- Truy xuất nguồn gốc (traceability) và chuẩn tham chiếu
- Hiệu chuẩn offset và gain — hai điểm, nhiều điểm
- Bù phi tuyến: đa thức, bảng tra, nội suy
- Bù nhiệt độ
- Trôi theo thời gian và chu kỳ hiệu chuẩn lại
- Hiệu chuẩn tại chỗ (in-situ) vs tại phòng thí nghiệm
- Hiệu chuẩn IMU: bias, scale, non-orthogonality; hiệu chuẩn từ kế (hard/soft iron)
- Lưu hệ số hiệu chuẩn trên thiết bị và quản lý phiên bản của chúng
- Bất định đo (measurement uncertainty) và truyền bất định qua tính toán
- Tài liệu hóa hiệu chuẩn — phần bị bỏ qua nhiều nhất

**Checkpoint:** hiệu chuẩn một cảm biến (ví dụ gia tốc kế 3 trục hoặc cảm biến nhiệt) và **chứng minh bằng số liệu** rằng sai số giảm: đo trước hiệu chuẩn, hiệu chuẩn, đo lại trên tập điểm độc lập, báo cáo sai số RMS trước/sau.

**Cạm bẫy:** bỏ qua vì "cảm biến có hiệu chuẩn nhà máy rồi". Hiệu chuẩn nhà máy không bù được: sai lệch lắp đặt, ảnh hưởng của mạch xung quanh, và trôi theo thời gian.

## C7.8 · Sensor fusion & ước lượng trạng thái — `In→Ad`

**Sub-leaves:** vì sao hợp nhất: mỗi cảm biến sai theo cách khác nhau · bộ lọc bổ sung (complementary filter) — đơn giản và hiệu quả bất ngờ · bộ lọc Kalman: mô hình trạng thái, dự đoán, cập nhật, ý nghĩa từng ma trận · điều chỉnh Q và R — phần khó thật sự · Kalman mở rộng (EKF) và Kalman không mùi (UKF) ở mức khái niệm · bộ lọc hạt (particle filter) ở mức khái niệm · hợp nhất tư thế: Madgwick, Mahony · phát hiện và loại bỏ ngoại lai trong hợp nhất · kiểm tra tính nhất quán (NIS/NEES) để biết bộ lọc có đang hoạt động đúng

**Checkpoint:** cài một bộ lọc Kalman 1-D từ đầu (không dùng thư viện), **giải thích được ý nghĩa vật lý của từng ma trận**, và chứng minh nó tốt hơn trung bình trượt trên một tập dữ liệu thật có nhiễu và có trôi.

## C7.9 · Thời gian & đồng bộ hóa — `Ad` ★ leaf bị đánh giá thấp nhất

**Sub-leaves:**
- Nguồn xung nhịp: RC nội, thạch anh, TCXO — độ chính xác ppm và giá
- Trôi xung nhịp: tính bằng ppm, ý nghĩa thực tế (10 ppm ≈ 0,86 s/ngày)
- RTC và pin dự phòng
- NTP: hoạt động, độ chính xác đạt được, hành vi step vs slew
- PTP (IEEE 1588) và độ chính xác sub-microsecond
- Đồng bộ bằng GPS/GNSS khi cần độ chính xác cao
- Timestamp ở đâu: tại cảm biến, tại MCU, tại gateway, tại server — mỗi chỗ sai khác nhau
- Đồng hồ đơn điệu (monotonic) vs đồng hồ tường (wall clock) — dùng cái nào khi nào
- Nhảy giây (leap second) và nhảy thời gian
- Căn chỉnh chuỗi thời gian từ nhiều nguồn có xung nhịp khác nhau
- Nội suy và tái lấy mẫu chuỗi thời gian khi đồng bộ
- Phát hiện lệch xung nhịp từ dữ liệu

**Dùng để xây:** C9.5, C10.2, C7.8 — cả hợp nhất cảm biến lẫn hệ phân tán đều sụp đổ nếu leaf này sai.

**Checkpoint:** đo trôi xung nhịp của một thiết bị trong 48 giờ, tính ppm, dự đoán độ lệch sau 30 ngày; sau đó căn chỉnh chuỗi thời gian từ hai thiết bị độc lập và **chứng minh sự kiện đồng thời thật sự được ghi nhận là đồng thời** với sai số dưới ngưỡng bạn đặt ra.

## C7.10 · Trích xuất đặc trưng cho edge ML — `In→Ad`

**Sub-leaves:** thống kê theo cửa sổ: mean, RMS, kurtosis, skewness, zero-crossing rate · đặc trưng miền tần số: năng lượng dải, tần số đỉnh, centroid phổ · MFCC cho âm thanh: từng bước và vì sao · spectrogram và mel-spectrogram · đặc trưng cho rung động: crest factor, kurtosis, đặc trưng envelope · chuẩn hóa và tỷ lệ hóa — và vì sao phải nhất quán giữa train và inference · kích thước cửa sổ và chồng lấn · trích xuất đặc trưng trên thiết bị vs gửi dữ liệu thô — đánh đổi băng thông/năng lượng/linh hoạt · kiểm tra rò rỉ trong trích xuất đặc trưng chuỗi thời gian

**Checkpoint:** đạt **cùng hoặc tốt hơn** độ chính xác so với một model lớn hơn chạy trên dữ liệu thô, bằng cách dùng đặc trưng thủ công được thiết kế tốt + model nhỏ — và đo chênh lệch về RAM, latency, năng lượng.

## C7.11 · Actuation — `In→Ad`

**Sub-leaves:** động cơ DC và driver H-bridge · động cơ bước: full/half/micro-stepping, mất bước · servo và điều khiển vị trí · động cơ BLDC và ESC ở mức khái niệm · relay và solid-state relay: dòng khởi động, hồ quang, tuổi thọ · điều khiển tải cảm: diode flyback, snubber · PWM cho điều khiển công suất: tần số, nhiễu nghe được, hiệu suất · phản hồi vị trí: encoder, hall, potentiometer · khóa liên động an toàn (interlock) phần cứng — không phụ thuộc phần mềm · công tắc hành trình và giới hạn cứng · nút dừng khẩn cấp và yêu cầu của nó

**Checkpoint:** điều khiển một tải thật (động cơ hoặc relay điều khiển thiết bị) với **khóa liên động phần cứng** sao cho bất kỳ lỗi phần mềm nào — treo, crash, hoặc giá trị điên rồ — không gây hư hại. Chứng minh bằng cách cố ý gây ra cả ba loại lỗi.

## C7.12 · Điều khiển vòng kín — `In`

**Sub-leaves:** vòng hở vs vòng kín và khi nào cần vòng kín · PID: vai trò từng thành phần · điều chỉnh: Ziegler-Nichols, thủ công, và tự động · bão hòa actuator và chống windup tích phân · lọc thành phần vi phân và nhiễu · tần số lấy mẫu của vòng điều khiển và quy tắc ngón tay cái · feedforward kết hợp feedback · giới hạn tốc độ thay đổi (slew rate limiting) · phát hiện dao động và chế độ an toàn · ghi log vòng điều khiển để phân tích sau

**Checkpoint:** điều chỉnh một PID trên hệ vật lý thật (nhiệt độ, tốc độ động cơ, hoặc vị trí) đạt chỉ tiêu cho trước về overshoot và thời gian ổn định, **có đồ thị** đáp ứng bước trước và sau khi điều chỉnh.

---

## ▸ Thứ tự học trong C7

```
1. Lấy mẫu + aliasing ★               (Phase 2, ~30 h)  ← trước mọi việc đọc cảm biến
2. Lượng tử hóa + sàn nhiễu           (Phase 3, ~25 h)
3. Loại cảm biến + chế độ hỏng        (Phase 3, ~30 h)
4. Nhiễu + EMI                        (Phase 3, ~20 h)
5. Lọc số                             (Phase 3, ~30 h)
6. FFT + phân tích phổ                (Phase 3, ~30 h)
7. Hiệu chuẩn ★                       (Phase 3, ~30 h)
8. Thời gian + đồng bộ ★              (Phase 3, ~25 h)
9. Trích xuất đặc trưng cho edge ML   (Phase 3–4, ~25 h)
10. Sensor fusion + Kalman            (Phase 4, ~25 h)
11. Actuation + an toàn               (Phase 4, ~20 h)
12. Điều khiển vòng kín               (Phase 4, ~20 h)  ← cùng lúc S3
```

## ▸ Tài nguyên chính C7

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| *The Scientist and Engineer's Guide to Digital Signal Processing* (Smith) — **miễn phí toàn văn** | — | C7.1–C7.4 | 50 |
| *Understanding Digital Signal Processing* (Lyons) | — | C7.3, C7.4 sâu hơn | 30 |
| CMSIS-DSP documentation | ARM | C7.3, C7.4 trên MCU | 15 |
| *Art of Electronics* chương về nhiễu và đo lường | — | C7.5 | 25 |
| Application note về nhiễu và nối đất (Analog Devices, TI) | ADI / TI | C7.5 — chất lượng rất cao, miễn phí | 20 |
| *Kalman and Bayesian Filters in Python* (Labbe) — **miễn phí** | — | C7.8 | 30 |
| Datasheet + application note của từng cảm biến bạn dùng | vendor | C7.6, C7.7 — primary source | 30 |
| NIST — tài liệu về bất định đo | NIST | C7.7 | 15 |
| *Feedback Systems* (Åström & Murray) — **miễn phí** | Caltech | C7.12, S3 | 30 |
| *TinyML* (Warden & Situnayake) — chương về đặc trưng | — | C7.10 | 15 |

---

# ◆ C8 · MACHINE LEARNING & INFERENCE SYSTEMS

**Mức mục tiêu:** **Advanced → Expert** ở inference/serving/eval · **Advanced** ở modeling ứng dụng · **Working** ở training quy mô lớn
**Ngân sách:** ~560 h — nhánh lớn nhất · Phase 2: 80 h · Phase 3: 200 h · Phase 4: 180 h · Phase 5: 100 h
**Vị trí:** con của Math + Programming; là `learn` và `infer` của vòng lặp.
**Vì sao phân bổ mức không đều:** giá trị của bạn nằm ở **đưa model vào hệ thống**, không ở **tạo model mới**. Training quy mô lớn cần compute bạn không có và không phải lợi thế cạnh tranh.

## C8.1 · Nền học thống kê — `Ad`

**Sub-leaves:** học có giám sát, không giám sát, tự giám sát, tăng cường — ranh giới thật · đánh đổi bias–variance và ý nghĩa thực tế · quá khớp, thiếu khớp, và khả năng của model · chính quy hóa: L1, L2, dropout, early stopping, augmentation · tách train/validation/test và vì sao ba chứ không hai · kiểm định chéo và các biến thể cho dữ liệu chuỗi thời gian · rò rỉ dữ liệu: các dạng, cách phát hiện, cách phòng · đường cong học và cách đọc chúng · lời nguyền chiều cao · định lý no-free-lunch và ý nghĩa thực tế

**Checkpoint:** phát hiện rò rỉ dữ liệu trong một pipeline **do người khác viết** (hoặc do bạn cố ý dựng), chỉ ra chính xác chỗ rò rỉ và ước lượng nó thổi phồng metric lên bao nhiêu.

## C8.2 · ML cổ điển — `In→Ad`

**Sub-leaves:** hồi quy tuyến tính và logistic — nền của mọi thứ · cây quyết định và tiêu chí chia · random forest và bagging · gradient boosting (XGBoost, LightGBM) — vẫn thắng trên dữ liệu bảng · SVM và kernel trick ở mức khái niệm · k-NN và vấn đề khoảng cách ở chiều cao · phân cụm: k-means, DBSCAN, phân cấp · giảm chiều: PCA, t-SNE, UMAP — và cách đọc sai chúng · phát hiện bất thường: isolation forest, one-class SVM, autoencoder · mô hình chuỗi thời gian cổ điển: ARIMA, phân rã mùa vụ · kỹ thuật đặc trưng cho dữ liệu bảng

**Checkpoint:** trên một dataset bảng thật, **đánh bại một neural network bằng gradient boosting** và giải thích vì sao — nêu đặc điểm nào của dữ liệu làm cho cây thắng.

**Cạm bẫy:** bỏ qua để nhảy sang deep learning. Kết quả: bạn sẽ dùng neural network cho bài toán mà một mô hình 50 tham số giải tốt hơn, rẻ hơn, và giải thích được.

## C8.3 · Đánh giá & metric — `Ad→Ex` ★ leaf quan trọng nhất của C8

**Sub-leaves:**
- Ma trận nhầm lẫn và mọi metric dẫn xuất từ nó
- Precision, recall, F1, và khi nào mỗi cái là metric sai
- ROC-AUC vs PR-AUC — và vì sao ROC gây hiểu lầm khi lớp mất cân bằng nặng
- Hiệu chuẩn xác suất: reliability diagram, Brier score, Platt scaling, isotonic
- Ngưỡng quyết định và tối ưu nó theo chi phí thật của lỗi
- Metric hồi quy: MAE, RMSE, MAPE — và khi nào mỗi cái nói dối
- Đánh giá theo lát cắt (slice-based): tổng thể tốt, một nhóm tệ
- Mất cân bằng lớp: lấy mẫu lại, trọng số, và vì sao cả hai đều có bẫy
- Ý nghĩa thống kê của chênh lệch giữa hai model
- Vấn đề nhiều so sánh khi bạn thử 50 cấu hình
- Đường cơ sở (baseline): luôn phải có, và phải ngớ ngẩn đủ để có ý nghĩa
- Xây dựng eval set: đại diện, đủ lớn, và **biết nó không đo được gì**
- Eval set từ dữ liệu thực địa vs dữ liệu công khai

**Checkpoint:** dựng một eval set cho bài toán của bạn mà **bạn tin tưởng**, viết ra bằng văn bản danh sách những gì nó **không** đo được, và chứng minh bằng một trường hợp cụ thể mà eval set cho điểm cao nhưng hệ thống hỏng trong thực tế.

## C8.4 · Nền mạng neural — `In→Ad`

**Sub-leaves:** perceptron, MLP, hàm kích hoạt và lựa chọn · lan truyền ngược: đạo hàm từng bước, không phải công thức thuộc lòng · đồ thị tính toán và vi phân tự động · optimizer: SGD, momentum, Adam, AdamW — khác nhau ở đâu · lịch trình tốc độ học và warmup · khởi tạo: Xavier, He, và vì sao khởi tạo quan trọng · chuẩn hóa: batch norm, layer norm, RMS norm — và vì sao transformer dùng layer norm · kết nối tắt (residual) và vì sao mạng sâu cần chúng · biến mất và bùng nổ gradient · cắt gradient · tích lũy gradient khi bộ nhớ hạn chế

**Checkpoint:** tự cài lan truyền ngược cho một MLP **bằng numpy thuần**, khớp kết quả với PyTorch tới 1e-6, và giải thích được từng bước đạo hàm.

## C8.5 · Kiến trúc — `In→Ad`

**Sub-leaves:** CNN: convolution, pooling, receptive field, tham số chia sẻ · kiến trúc CNN hiệu quả: MobileNet, EfficientNet — depthwise separable convolution · phát hiện đối tượng: một giai đoạn vs hai giai đoạn, họ YOLO · RNN/LSTM/GRU và giới hạn của chúng · Transformer: self-attention, multi-head, positional encoding, encoder vs decoder · chi phí bộ nhớ và tính toán của attention theo độ dài chuỗi (O(n²)) · attention hiệu quả: FlashAttention, sliding window, ở mức khái niệm · mixture-of-experts ở mức khái niệm · autoencoder và variational autoencoder · model chuỗi thời gian với deep learning — và khi nào nó thua cây

**Checkpoint:** vẽ được luồng dữ liệu qua một khối transformer, **tính bằng tay** bộ nhớ cần cho KV cache với độ dài chuỗi và kích thước batch cho trước, và xác nhận bằng đo thực tế.

## C8.6 · Biểu diễn & embedding — `In→Ad`

**Sub-leaves:** không gian embedding và ý nghĩa hình học của nó · độ đo tương đồng: cosine, dot product, Euclidean — khi nào khác nhau · học tương phản (contrastive learning) và triplet loss · embedding cho văn bản, ảnh, âm thanh, chuỗi thời gian · embedding đa phương thức · sụp đổ embedding và cách phát hiện · dịch chuyển phân phối trong không gian embedding · chuẩn hóa embedding và ảnh hưởng tới tìm kiếm · chiều embedding: đánh đổi chất lượng/chi phí · khi nào embedding search cho kết quả vô nghĩa

**Checkpoint:** chẩn đoán một hệ retrieval trả kết quả vô nghĩa và xác định nguyên nhân trong ba khả năng: model embedding không phù hợp domain, chuẩn hóa sai, hay chunking sai.

## C8.7 · Thực hành huấn luyện — `In→Ad`

**Sub-leaves:** đường ống dữ liệu: tải, augment, batch, prefetch · augmentation cho từng loại dữ liệu và cái nào phá hỏng nhãn · tìm kiếm siêu tham số: grid, random, Bayesian — và vì sao random thường đủ · theo dõi thí nghiệm: cái gì phải ghi lại · khả năng tái lập: seed, phiên bản, tính không tất định của cuDNN · huấn luyện độ chính xác hỗn hợp · điểm kiểm tra (checkpoint) và khôi phục · huấn luyện phân tán ở mức khái niệm: data parallel, model parallel · chẩn đoán huấn luyện: loss không giảm, loss NaN, overfit ngay lập tức · học chuyển tiếp và đóng băng lớp · huấn luyện trên dữ liệu mất cân bằng và dữ liệu nhiễu nhãn

**Checkpoint:** chạy lại một thí nghiệm của chính bạn sau **3 tháng** và ra cùng kết quả trong sai số thống kê — chứng minh bạn đã ghi đủ để tái lập.

## C8.8 · Tinh chỉnh & thích ứng — `In→Ad`

**Sub-leaves:** tinh chỉnh toàn phần vs một phần · LoRA và QLoRA: cơ chế, siêu tham số, khi nào đủ · adapter và prefix tuning · tinh chỉnh có giám sát cho hành vi cụ thể · chuẩn bị dữ liệu cho tinh chỉnh: chất lượng > số lượng · quên thảm họa (catastrophic forgetting) · đánh giá model đã tinh chỉnh trên eval riêng, không dùng benchmark chung · khi nào tinh chỉnh là sai lựa chọn (thường: prompt tốt hơn + retrieval đủ) · chi phí tinh chỉnh vs lợi ích thực tế

**Checkpoint:** tinh chỉnh một model cho một domain hẹp và chứng minh cải thiện trên **eval set của riêng bạn**; đồng thời chứng minh nó **không** làm tệ đi các năng lực khác (đo trên eval set thứ hai).

## C8.9 · Nén model — `Ad→Ex`

**Sub-leaves:**
- Lượng tử hóa sau huấn luyện (PTQ): tĩnh, động, và dữ liệu hiệu chuẩn
- Huấn luyện nhận biết lượng tử hóa (QAT): khi nào cần
- Lược đồ: đối xứng/bất đối xứng, theo tensor/theo kênh/theo nhóm
- Định dạng: int8, int4, FP8 (E4M3, E5M2), NF4
- Phương pháp cho LLM: AWQ, GPTQ, GGUF — khác nhau ở giả định gì
- Outlier trong activation và vì sao chúng phá lượng tử hóa
- Cắt tỉa (pruning): không cấu trúc, có cấu trúc, và vì sao chỉ cái sau tăng tốc thật
- Chưng cất tri thức: teacher-student, soft label
- Tìm kiếm kiến trúc neural ở mức awareness
- Đo mất mát chính xác đúng cách: không dùng một metric tổng hợp
- Định vị lớp nào gây mất mát nhiều nhất
- Đánh đổi độ chính xác ↔ kích thước ↔ latency ↔ năng lượng — vẽ thành đường cong

**Checkpoint:** giảm kích thước model ≥4× với mất chính xác dưới ngưỡng cho trước; vẽ được **đường cong Pareto** của ít nhất 4 cấu hình lượng tử hóa trên trục (kích thước, độ chính xác, latency); và định vị được lớp nhạy cảm nhất.

## C8.10 · Engine inference & serving — `Ad→Ex` ★

**Sub-leaves:**
- Vì sao serving khác training: batch nhỏ, latency quan trọng, throughput quan trọng
- Batching tĩnh vs batching động vs continuous batching
- KV cache: kích thước, quản lý, và vì sao nó là nút thắt bộ nhớ
- PagedAttention: quản lý KV cache theo khối, giống phân trang bộ nhớ ảo
- Prefill vs decode: hai giai đoạn có đặc tính hoàn toàn khác nhau
- Serving tách rời prefill/decode [Fact 2026: đang nổi lên]
- Song song tensor, song song pipeline, và khi nào cần mỗi cái
- Giải mã suy đoán (speculative decoding)
- Chia sẻ KV cache giữa các request có tiền tố chung
- vLLM: kiến trúc và cấu hình [Fact 2026: chuẩn thực tế cho throughput cao]
- TensorRT-LLM: hiệu năng cao hơn, chi phí thiết lập cao hơn nhiều
- Serving model nhỏ: ONNX Runtime, TorchServe, hoặc tự viết
- Autoscaling cho workload inference: scale-to-zero, cold start
- Định tuyến request và nhiều model trên cùng hạ tầng
- Đo: TTFT (time to first token), TPOT, throughput, độ sâu hàng đợi

**Checkpoint:** tự deploy một serving stack, và **tăng throughput ≥2×** bằng thay đổi cấu hình (batching, lượng tử hóa, song song hóa) — với số đo p50/p99 latency trước và sau, và giải thích được cơ chế của mỗi cải thiện.

## C8.11 · Hệ LLM — `Ad`

**Sub-leaves:**
- Tokenization: BPE, ảnh hưởng tới chi phí và tới ngôn ngữ không phải tiếng Anh
- Cửa sổ ngữ cảnh: chi phí, hiệu ứng "lost in the middle", quản lý ngữ cảnh
- Tham số lấy mẫu: temperature, top-p, top-k — ảnh hưởng thật
- Structured output: JSON mode, function calling, ràng buộc bằng grammar
- Tool calling: định nghĩa, ranh giới, xử lý lỗi của tool
- MCP như giao thức kết nối tool [Fact 2026: do Linux Foundation quản trị, các nhà cung cấp lớn hỗ trợ]
- RAG: chunking, embedding, retrieval, reranking, và các chế độ hỏng của từng bước
- Retrieval lai (từ khóa + vector) và vì sao nó thường thắng vector thuần
- Quản lý prompt như quản lý code: phiên bản, test, review
- Ước lượng và kiểm soát chi phí token
- Streaming và trải nghiệm độ trễ cảm nhận
- Caching: prompt cache, semantic cache và rủi ro của nó
- **Khi nào KHÔNG cần agent**: ~40% tác vụ "agent" trong production thực chất là một lời gọi có structured output [Fact 2026]

**Checkpoint:** xây một tính năng dùng LLM, và **chứng minh bằng đo đạc** rằng phiên bản đơn giản nhất (một lời gọi có structured output) không đủ, trước khi thêm bất kỳ lớp orchestration nào.

## C8.12 · Mẫu agentic — `Ad`

**Sub-leaves:**
- Agent như máy trạng thái, không phải như vòng lặp chat
- Thực thi bền vững (durable execution): tiếp tục đúng sau crash
- Quản lý trạng thái và checkpoint
- Ranh giới tool: cái gì agent được phép làm, cái gì không
- Human-in-the-loop như một primitive, không phải như một bổ sung
- Guardrail: trước khi gọi tool, sau khi gọi tool, trên output cuối
- Phân rã tác vụ và điều phối nhiều agent — và chi phí thật của nó
- Vòng lặp vô hạn và ngân sách token/bước
- Quan sát agent: trace từng bước, chi phí từng bước
- Xử lý lỗi: tool thất bại, model trả về rác, ngữ cảnh tràn
- LangGraph và các SDK vendor-native [Fact 2026: OpenAI Agents SDK, Claude Agent SDK, Google ADK đều ra khoảng tháng 3–4/2026]
- **[Cảnh báo]** Tầng này biến động nhất trong stack — landscape thay đổi trong 5 tháng đầu 2026 nhiều hơn cả 2024 và 2025 cộng lại. Học **mẫu**, không học framework. Trần cho bất kỳ framework nào: 20 h.

**Checkpoint:** thiết kế một agent **phục hồi đúng sau khi bị giết giữa chừng** — chạy, kill process ở một bước bất kỳ, khởi động lại, và agent tiếp tục từ đúng điểm dừng với trạng thái nhất quán.

## C8.13 · Đánh giá hệ phi tất định — `Ad→Ex`

**Sub-leaves:** vì sao pass/fail không áp dụng được · eval set và eval harness — hạ tầng, không phải script · đánh giá dựa trên rubric · LLM-as-judge: khi nào dùng được, thiên lệch của nó, và cách hiệu chuẩn nó · so sánh cặp và Elo · bộ test hồi quy cho hành vi model · eval theo lát cắt và phát hiện suy giảm ở nhóm nhỏ · golden set và cách bảo trì nó · đánh giá tự động vs người đánh giá · độ tin cậy giữa các người đánh giá · đánh giá hệ agentic: đúng kết quả vs đúng quá trình · red-teaming và eval đối kháng · chi phí của eval và cách giữ nó chạy được thường xuyên

**Checkpoint:** xây eval harness bắt được một **hồi quy thật** mà unit test bỏ lọt — dựng tình huống bằng cách đổi model hoặc đổi prompt, và chứng minh harness phát hiện được.

## C8.14 · Monitoring & drift — `Ad`

**Sub-leaves:** dịch chuyển dữ liệu (data drift) vs dịch chuyển khái niệm (concept drift) vs dịch chuyển nhãn · phát hiện drift: thống kê (KS test, PSI), dựa trên embedding, dựa trên hiệu năng · độ trễ nhãn: khi nào bạn mới biết dự đoán đúng hay sai · vòng phản hồi: khi hệ thống ảnh hưởng tới chính dữ liệu tương lai của nó · giám sát shadow và so sánh A/B cho model · phát hiện suy giảm âm thầm · giám sát chất lượng input: cảm biến hỏng nhìn giống drift · ngưỡng cảnh báo và mệt mỏi cảnh báo cho ML · nhật ký dự đoán: lưu gì, bao lâu, riêng tư ra sao · huấn luyện lại: kích hoạt, quy trình, kiểm soát

**Checkpoint:** phát hiện drift trong một hệ **trước khi** nó ảnh hưởng tới người dùng — dựng bằng cách đưa dữ liệu dịch chuyển dần vào và chứng minh cơ chế giám sát cảnh báo đúng lúc, không quá sớm (nhiễu) cũng không quá muộn.

## C8.15 · Chi phí, capacity & kinh tế học inference — `Ad`

**Sub-leaves:** chi phí mỗi token, mỗi request, mỗi thiết bị, mỗi ngày · chi phí training vs chi phí inference — hai đường cong khác nhau · tự host vs API: điểm hòa vốn và cách tính · mức sử dụng GPU và scale-to-zero · lựa chọn kích thước model theo chi phí, không theo benchmark · cascade: model nhỏ trước, model lớn khi cần · caching như giảm chi phí · ngân sách latency và ảnh hưởng tới lựa chọn kiến trúc · chi phí ẩn: lưu trữ, truyền dữ liệu, quan sát · dự báo chi phí khi tải tăng 10× · trình bày đánh đổi chi phí cho người ra quyết định

**Checkpoint:** trình bày **3 phương án kiến trúc** cho cùng một yêu cầu, mỗi phương án kèm bảng chi phí và độ trễ dự kiến, và bảo vệ được lựa chọn của bạn trước câu hỏi "vì sao không chọn cái rẻ hơn".

## C8.16 · Chế độ hỏng của hệ ML — `Ad→Ex`

**Sub-leaves:** suy giảm âm thầm: model tệ dần mà dashboard vẫn xanh · dịch chuyển phân phối giữa train và production · rò rỉ dữ liệu phát hiện muộn · hallucination và cách nó biểu hiện trong hệ có tool · tự tin sai: model chắc chắn nhưng sai · reward hacking và mục tiêu bị tối ưu sai · vòng phản hồi tự củng cố · ngộ độc dữ liệu (data poisoning) · tấn công đối kháng ở mức khái niệm · prompt injection qua dữ liệu không tin cậy · lỗi tầng: model đúng nhưng pipeline sai · thiếu đường lui (fallback) khi model không khả dụng

**Checkpoint:** cho một hệ ML cho trước (của bạn), liệt kê **≥5 cách nó hỏng mà mọi dashboard vẫn màu xanh**, và cho mỗi cách, thiết kế một cơ chế phát hiện.

---

## ▸ Thứ tự học trong C8

```
1. Nền học thống kê + đánh giá ★       (Phase 2, ~55 h)  ← trước mọi modeling
2. ML cổ điển                           (Phase 2–3, ~45 h)
3. Nền mạng neural (tự cài backprop)    (Phase 3, ~50 h)
4. Kiến trúc: CNN, Transformer          (Phase 3, ~50 h)
5. Thực hành huấn luyện                 (Phase 3, ~40 h)
6. Biểu diễn & embedding                (Phase 3, ~25 h)
7. Nén model ★                          (Phase 3–4, ~55 h)  ← nối C3.12, C6.14
8. Hệ LLM                               (Phase 4, ~50 h)
9. Engine inference & serving ★         (Phase 4, ~65 h)
10. Đánh giá hệ phi tất định ★          (Phase 4, ~40 h)
11. Tinh chỉnh & thích ứng              (Phase 4, ~30 h)
12. Mẫu agentic                         (Phase 4–5, ~35 h)
13. Monitoring & drift                  (Phase 5, ~35 h)
14. Chi phí & capacity                  (Phase 5, ~20 h)
15. Chế độ hỏng                         (Phase 5, ~25 h)
```

## ▸ Tài nguyên chính C8

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| Series "từ zero" của Andrej Karpathy (micrograd, makemore, nanoGPT) | — | C8.4, C8.5 — **đúng tinh thần nguyên lý trước framework** | 60 |
| *Practical Deep Learning for Coders* | fast.ai | C8.4, C8.7 vào nhanh | 50 |
| CS231n | Stanford | C8.5 phần thị giác | 45 |
| CS224n | Stanford | C8.5 phần ngôn ngữ | 45 |
| CS336 *Language Modeling from Scratch* | Stanford | C8.5, C8.10 sâu | 50 |
| *Machine Learning Crash Course* | Google | C8.1 nền nhanh | 15 |
| *An Introduction to Statistical Learning* — miễn phí | — | C8.1, C8.2 | 40 |
| *Designing Machine Learning Systems* (Chip Huyen) | — | C8.14, C8.15, C8.16 | 25 |
| PyTorch documentation + tutorial | Meta / PyTorch | xuyên suốt | 30 |
| vLLM documentation + blog kỹ thuật | vLLM project | C8.10 — primary source | 30 |
| Paper gốc: Attention Is All You Need, PagedAttention, LoRA, AWQ/GPTQ, FlashAttention | — | C8.5, C8.9, C8.10 | 35 |
| *TinyML* (Warden & Situnayake) | — | C8.9 phần edge, nối C6.14 | 25 |
| MCP specification | Linux Foundation | C8.11 — primary source | 10 |
| LangGraph documentation | LangChain | C8.12 — **trần 20 h** | 20 |

---

# ◆ C9 · DATA ENGINEERING & STORAGE

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~320 h · Phase 2: 120 h · Phase 3: 120 h · Phase 4: 80 h
**Vị trí:** con của OS + DSA; là `store` của vòng lặp, và là nhiên liệu của `learn`.
**Vì sao Advanced:** pipeline hỏng **âm thầm** là chuẩn mực, không phải ngoại lệ. Model tốt trên dữ liệu hỏng vẫn cho kết quả sai.

## C9.1 · Mô hình dữ liệu — `Ad`

**Sub-leaves:** đại số quan hệ và vì sao nó là nền · chuẩn hóa 1NF–3NF/BCNF và ý nghĩa thực tế của từng mức · phi chuẩn hóa có chủ đích và khi nào nó đúng · mô hình hóa chiều: star schema, snowflake · slowly changing dimension · mô hình hóa sự kiện vs mô hình hóa trạng thái · event sourcing ở mức khái niệm · mô hình cho dữ liệu chuỗi thời gian: wide vs narrow · khóa tự nhiên vs khóa thay thế · mô hình hóa quan hệ nhiều-nhiều và phân cấp · mô hình hóa cho hệ đa thiết bị đa tenant

**Checkpoint:** thiết kế schema cho hệ đa thiết bị (≥100 thiết bị, ≥5 loại cảm biến, có metadata thay đổi theo thời gian), và **bảo vệ từng lựa chọn phi chuẩn hóa** bằng truy vấn cụ thể mà nó tăng tốc và chi phí ghi mà nó thêm vào.

## C9.2 · SQL chuyên sâu — `Ad`

**Sub-leaves:** JOIN: các loại và cách engine thực hiện (nested loop, hash, merge) · hàm cửa sổ: partition, frame, và ứng dụng cho chuỗi thời gian · CTE và CTE đệ quy · truy vấn con tương quan và vì sao chúng chậm · tập hợp và GROUPING SETS, ROLLUP, CUBE · index: B-tree, hash, GIN/GiST, partial, covering, composite — và thứ tự cột · kế hoạch truy vấn: đọc EXPLAIN ANALYZE và hiểu từng node · thống kê và ước lượng cardinality — nguồn của kế hoạch tồi · index không được dùng: các nguyên nhân phổ biến · phân vùng bảng · CTE materialization và tối ưu hóa · viết truy vấn cho dữ liệu lớn: tránh N+1, batch

**Checkpoint:** tăng tốc một truy vấn chậm **≥10×** bằng cách đọc kế hoạch truy vấn và thay đổi index hoặc cách viết truy vấn — không bằng cách đoán. Ghi lại kế hoạch trước và sau.

## C9.3 · Transaction & tính đúng đắn — `Ad`

**Sub-leaves:** ACID — từng chữ nghĩa là gì chính xác · mức cô lập: read uncommitted, read committed, repeatable read, serializable · anomaly: dirty read, non-repeatable read, phantom, write skew, lost update · MVCC: cơ chế, snapshot, và chi phí (bloat, vacuum) · khóa: hàng, bảng, khoảng (gap lock), và leo thang khóa · khóa lạc quan vs bi quan · deadlock trong DB và cách xử lý · transaction dài và tác động của chúng · serializable snapshot isolation · giao dịch trong hệ phân tán (nối C10.7) · ngữ nghĩa transaction của từng engine khác nhau ra sao

**Checkpoint:** tái tạo **write skew** ở mức isolation `repeatable read`, chứng minh nó gây ra kết quả sai trong một tình huống nghiệp vụ cụ thể, và sửa bằng đúng công cụ (nâng isolation, hoặc khóa tường minh, hoặc ràng buộc).

## C9.4 · Storage engine — `In→Ad`

**Sub-leaves:** B-tree: cấu trúc, fanout, chia/gộp node, khuếch đại ghi · LSM-tree: memtable, SSTable, compaction, khuếch đại ghi/đọc/không gian · so sánh B-tree vs LSM theo workload · write-ahead log: cơ chế, checkpoint, phục hồi · buffer pool và chính sách thay thế · nén trong storage engine · lưu trữ theo hàng vs theo cột và ảnh hưởng tới truy vấn · bloom filter trong LSM · đo khuếch đại ghi thực tế · điều chỉnh compaction

**Checkpoint:** chọn storage engine cho một workload ghi nặng (ví dụ 10.000 điểm dữ liệu/giây từ thiết bị), bảo vệ lựa chọn bằng **phân tích khuếch đại ghi**, rồi chạy benchmark thật để xác nhận hoặc bác bỏ.

## C9.5 · Lưu trữ chuỗi thời gian — `Ad` ★

**Sub-leaves:** đặc điểm của workload chuỗi thời gian: ghi nhiều, ít cập nhật, truy vấn theo khoảng · mã hóa chuyên biệt: delta, delta-of-delta, XOR (Gorilla), RLE · nén và tỷ lệ đạt được thực tế · tổ chức theo chunk/partition theo thời gian · downsampling và rollup: khi nào tính trước, khi nào tính lúc truy vấn · chính sách lưu trữ (retention) theo tầng độ phân giải · dữ liệu đến muộn (out-of-order ingest) và xử lý · cardinality của tag/label và vụ nổ cardinality · TimescaleDB, InfluxDB, Prometheus TSDB, ClickHouse — mô hình khác nhau ở đâu · truy vấn chuỗi thời gian: nội suy, gap filling, hàm cửa sổ thời gian · so sánh chi phí lưu trữ giữa các chiến lược

**Checkpoint:** giữ **1 năm dữ liệu từ 100 thiết bị × 5 cảm biến × 1 Hz** trong ngân sách lưu trữ cho trước, với truy vấn "trung bình theo giờ trong 30 ngày qua" trả về dưới 1 giây. Trình bày chiến lược downsampling và tính toán dung lượng.

## C9.6 · Object storage & định dạng cột — `In→Ad`

**Sub-leaves:** mô hình object storage: nhất quán, chi phí, độ trễ · phân cấp lớp lưu trữ và chi phí truy xuất · Parquet: cấu trúc, row group, column chunk, thống kê, predicate pushdown · Arrow: định dạng trong bộ nhớ và zero-copy · ORC ở mức khái niệm · phân vùng thư mục và partition pruning · file nhỏ và vấn đề của chúng · định dạng bảng: Iceberg, Delta Lake ở mức khái niệm · nén: Snappy, ZSTD, và đánh đổi · truy vấn trực tiếp trên object storage (DuckDB, ClickHouse)

**Checkpoint:** truy vấn 50 GB dữ liệu Parquet trên laptop 16 GB RAM mà không sập, dưới 60 giây, và giải thích được predicate pushdown đã loại bỏ bao nhiêu dữ liệu.

## C9.7 · Key-value, cache & invalidation — `In→Ad`

**Sub-leaves:** Redis: cấu trúc dữ liệu, tính chất bền vững, mô hình một luồng · chiến lược cache: cache-aside, read-through, write-through, write-behind · chính sách hết hạn và thu hồi (LRU, LFU, TTL) · vấn đề invalidation và vì sao nó khó · cache stampede và cách chống (lock, probabilistic early expiration) · cache phân tầng: client, CDN, ứng dụng, DB · tính nhất quán của cache và cửa sổ không nhất quán · cache âm (negative caching) · đo tỷ lệ hit và diễn giải đúng · khi nào cache là sai lựa chọn

**Checkpoint:** thiết kế chiến lược cache cho một tính năng cụ thể, và **chỉ ra tường minh kịch bản mà cache trả về dữ liệu sai** — rồi quyết định có chấp nhận được không, có lý do.

## C9.8 · Vector storage & tìm kiếm tương đồng — `In→Ad`

**Sub-leaves:** bài toán tìm kiếm láng giềng gần nhất và độ phức tạp của nó · tìm kiếm chính xác vs xấp xỉ (ANN) · HNSW: cấu trúc đồ thị nhiều tầng, tham số M và efConstruction/efSearch · IVF và IVF-PQ: phân cụm và lượng tử hóa tích · lượng tử hóa tích (product quantization) và mất mát của nó · đánh đổi recall ↔ latency ↔ bộ nhớ · lọc metadata kết hợp tìm kiếm vector · cập nhật index và xóa · tìm kiếm lai: BM25 + vector, và reciprocal rank fusion · reranking sau retrieval · **khi nào không nên dùng vector DB**: dữ liệu nhỏ, filter mạnh, hoặc từ khóa đủ tốt

**Checkpoint:** đo đường cong recall–latency cho ít nhất 3 cấu hình index trên dữ liệu của bạn, chọn điểm vận hành có lý do, và **nêu được một trường hợp trong hệ của bạn mà tìm kiếm từ khóa đơn giản tốt hơn vector**.

## C9.9 · Streaming & log phân tán — `Ad`

**Sub-leaves:** log như trừu tượng cơ bản (append-only, có thứ tự trong partition) · Kafka: topic, partition, offset, consumer group, rebalance · đảm bảo thứ tự: trong partition có, giữa các partition không · lưu giữ và nén log (log compaction) · producer: ack, idempotent producer, batching · consumer: at-most-once, at-least-once, và cách đạt hiệu ứng exactly-once · **"exactly-once" là hợp đồng end-to-end**, không phải tính năng của broker · backpressure trong stream · xử lý stream: cửa sổ (tumbling, hopping, session), watermark, dữ liệu đến muộn · trạng thái trong xử lý stream và checkpoint · dead letter queue và xử lý thông điệp độc · thay thế nhẹ hơn: NATS, Redis Streams, và khi nào chúng đủ

**Checkpoint:** giải thích **bằng ví dụ cụ thể trong hệ của bạn** vì sao "exactly-once" phải được thực hiện ở tầng ứng dụng bằng dedup key, và chứng minh bằng thử nghiệm gửi trùng rằng hệ của bạn xử lý đúng.

## C9.10 · Batch, stream, micro-batch — `In→Ad`

**Sub-leaves:** kiến trúc lambda và kappa · thời gian sự kiện vs thời gian xử lý · độ trễ ↔ chi phí ↔ độ phức tạp — tam giác đánh đổi · tính toán tăng tiến (incremental) · điều phối batch: DAG, phụ thuộc, chạy lại · idempotency của job batch · backfill: thiết kế để chạy lại lịch sử được · so sánh chi phí thật: stream 24/7 vs batch mỗi giờ · khi nào batch đơn giản là câu trả lời đúng (thường xuyên hơn người ta nghĩ)

**Checkpoint:** cho ba yêu cầu nghiệp vụ khác nhau, chọn batch/stream/micro-batch cho mỗi cái và bảo vệ bằng bảng: độ trễ đạt được, chi phí hạ tầng, số dòng code, và số chế độ hỏng.

## C9.11 · Ingest từ edge không tin cậy — `Ad→Ex` ★

**Sub-leaves:**
- Store-and-forward trên thiết bị: hàng đợi cục bộ, giới hạn, chính sách loại bỏ
- Bộ đệm vòng trong flash và wear leveling
- Đánh số thứ tự và phát hiện khoảng trống
- Dedup key: thiết kế, tính duy nhất, thời gian sống
- Backfill: ingest dữ liệu lịch sử mà không phá thống kê
- Dữ liệu đến muộn: cửa sổ chấp nhận và xử lý sau cửa sổ
- Xung đột timestamp và đồng bộ hóa (nối C7.9)
- Điều tiết đồng bộ để không gây tăng đột biến tải khi nhiều thiết bị cùng trở lại
- Phiên bản schema từ thiết bị cũ vẫn đang chạy
- Xác thực và từ chối dữ liệu không hợp lệ ở biên
- Xác nhận (acknowledgement) đầu cuối: thiết bị chỉ xóa dữ liệu sau khi server xác nhận bền vững
- Đo: tỷ lệ mất, tỷ lệ trùng, độ trễ ingest p99

**Checkpoint:** 20 thiết bị offline **24 giờ đồng thời**, rồi cùng trở lại: không mất dữ liệu, không trùng, thứ tự đúng, và **tải lên server không vượt 2× tải bình thường** (chứng minh bằng đồ thị). Đây là checkpoint khó nhất của C9.

## C9.12 · Schema evolution & data contract — `In→Ad`

**Sub-leaves:** tương thích ngược, tương thích tiến, tương thích đầy đủ · schema registry và thực thi tương thích · thêm/xóa/đổi tên trường — cái nào an toàn · giá trị mặc định và trường tùy chọn · phiên bản hóa trong protobuf, Avro, JSON Schema · data contract: producer và consumer thỏa thuận gì · thử nghiệm tương thích trong CI · di trú dữ liệu cũ · xử lý thiết bị cũ không bao giờ cập nhật được

**Checkpoint:** đổi schema (thêm trường, đổi kiểu một trường) mà **consumer phiên bản cũ vẫn chạy đúng** — chứng minh bằng test tự động trong CI chạy consumer cũ trên dữ liệu mới.

## C9.13 · Chất lượng dữ liệu & data observability — `In→Ad`

**Sub-leaves:** chiều của chất lượng: đầy đủ, chính xác, nhất quán, kịp thời, duy nhất · kiểm tra tự động: ràng buộc, phạm vi, phân phối · phát hiện bất thường trong metric của pipeline (không phải trong dữ liệu nghiệp vụ) · lineage: theo dõi dữ liệu từ nguồn tới đích · freshness SLA cho dữ liệu · phát hiện cảm biến hỏng từ tầng dữ liệu (giá trị kẹt, ngoài phạm vi, nhiễu bất thường) · dữ liệu thiếu vs dữ liệu bằng 0 — phân biệt · kiểm thử dữ liệu trong CI · cảnh báo chất lượng dữ liệu và tránh mệt mỏi cảnh báo

**Checkpoint:** phát hiện một cảm biến hỏng **từ tầng dữ liệu** trước khi bất kỳ ai báo cáo — dựng bằng cách gây hỏng cảm biến thật (ngắt kết nối, che, làm nóng) và chứng minh cơ chế phát hiện hoạt động trong ≤1 giờ.

## C9.14 · Backup, khôi phục, lưu giữ, xóa — `In→Ad`

**Sub-leaves:** RPO và RTO — định nghĩa và đo · backup đầy đủ, tăng tiến, khác biệt · point-in-time recovery và WAL archiving · kiểm thử khôi phục — **backup chưa test không phải backup** · sao chép sang vùng khác · chính sách lưu giữ theo loại dữ liệu · xóa và quyền được xóa (nối A5) · xóa trong hệ có nhiều bản sao và cache · lưu trữ lạnh và chi phí truy xuất · mã hóa backup và quản lý khóa

**Checkpoint:** thực hiện **khôi phục thật** từ backup vào môi trường sạch, đo RTO thực tế và RPO thực tế, và so với mục tiêu bạn đặt ra. Nếu chưa từng khôi phục, bạn chưa có backup.

---

## ▸ Thứ tự học trong C9

```
1. Mô hình dữ liệu + SQL chuyên sâu   (Phase 2, ~70 h)
2. Transaction + isolation             (Phase 2, ~40 h)
3. Storage engine                      (Phase 2–3, ~30 h)
4. Chuỗi thời gian ★                   (Phase 3, ~45 h)
5. Key-value + cache                   (Phase 3, ~25 h)
6. Ingest từ edge ★                    (Phase 3, ~45 h)  ← cùng lúc C5.14
7. Schema evolution + contract         (Phase 3, ~20 h)
8. Streaming + log phân tán            (Phase 3–4, ~45 h)
9. Object storage + Parquet            (Phase 4, ~25 h)
10. Vector storage + ANN               (Phase 4, ~25 h)  ← sau C8.6
11. Batch/stream/micro-batch           (Phase 4, ~20 h)
12. Chất lượng dữ liệu                 (Phase 4, ~25 h)
13. Backup + khôi phục                 (Phase 4, ~20 h)
```

## ▸ Tài nguyên chính C9

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| 15-445 *Database Systems* | CMU Database Group | C9.1–C9.4 | 90 |
| 15-721 *Advanced Database Systems* | CMU Database Group | C9.4, C9.6 | 40 |
| *Designing Data-Intensive Applications* (Kleppmann) | — | C9.3, C9.9, C9.12 — **đáng mua** | 45 |
| PostgreSQL documentation | PostgreSQL Global Dev Group | C9.2, C9.3 — primary source | 30 |
| *Use The Index, Luke* — miễn phí | — | C9.2 phần index | 15 |
| Kafka documentation + *Kafka: The Definitive Guide* | Apache / — | C9.9 | 35 |
| Paper Gorilla (Facebook) về nén chuỗi thời gian | — | C9.5 — primary source | 8 |
| TimescaleDB / ClickHouse / Prometheus documentation | vendor | C9.5 | 25 |
| Parquet + Arrow specification | Apache | C9.6 — primary source | 15 |
| Paper HNSW | — | C9.8 — primary source | 8 |
| *Fundamentals of Data Engineering* (Reis & Housley) | — | C9.10, C9.13 | 25 |

---

# ◆ C10 · DISTRIBUTED SYSTEMS & CLOUD INFRASTRUCTURE

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~360 h · Phase 2: 60 h · Phase 3: 140 h · Phase 4: 120 h · Phase 5: 40 h
**Vị trí:** con của Networking + Databases; là ngữ pháp của chữ "end-to-end".

## C10.1 · Mô hình lỗi — `Ad→Ex` ★ nền tư duy của cả nhánh

**Sub-leaves:** lỗi từng phần (partial failure) — khác biệt cơ bản với hệ một máy · fail-stop vs fail-slow vs Byzantine · lỗi xám (gray failure): chậm nhưng không chết, và vì sao nó tệ hơn chết · timeout: không phân biệt được "chậm" với "chết" — hệ quả cơ bản · phân vùng mạng và phân vùng một chiều · hiệu ứng domino và lỗi lan truyền · lỗi tương quan (cùng rack, cùng vùng, cùng bản deploy) · giả định sai kinh điển: 8 ngộ nhận của tính toán phân tán · mô hình hóa lỗi trước khi thiết kế

**Checkpoint:** cho một kiến trúc cụ thể, liệt kê **mọi điểm hỏng từng phần** và hệ quả quan sát được của mỗi cái từ góc nhìn người dùng — rồi kiểm chứng ít nhất 5 cái bằng thử nghiệm thật.

## C10.2 · Thời gian trong hệ phân tán — `In→Ad`

**Sub-leaves:** vì sao đồng hồ vật lý không đủ để sắp thứ tự · quan hệ happens-before · đồng hồ Lamport và giới hạn của nó · vector clock và chi phí · đồng hồ lai (HLC) · TrueTime và đồng hồ có biên bất định · sự kiện đồng thời và ý nghĩa thật của nó · đồng hồ lệch gây lỗi ở đâu: TLS, cache, khóa, thứ tự sự kiện · đồng hồ đơn điệu cho đo khoảng thời gian

**Checkpoint:** dựng một tình huống mà sắp thứ tự theo timestamp cho kết quả **sai**, chứng minh bằng thử nghiệm với hai máy có đồng hồ lệch, và sửa bằng đồng hồ logic.

## C10.3 · Mô hình nhất quán — `Ad`

**Sub-leaves:** linearizability: định nghĩa và vì sao nó đắt · sequential consistency · causal consistency · eventual consistency và hội tụ · read-your-writes, monotonic reads, monotonic writes · nhất quán trong cache và bản sao đọc · CAP: phát biểu chính xác và những hiểu lầm phổ biến · PACELC: bổ sung quan trọng mà CAP thiếu · CRDT ở mức khái niệm và khi nào chúng giải quyết vấn đề thật · chọn mô hình nhất quán theo tính năng, không theo hệ thống

**Checkpoint:** cho ba tính năng trong hệ của bạn, chọn mô hình nhất quán cho mỗi cái và **mô tả chính xác người dùng sẽ thấy gì khi có sự cố** dưới mô hình đó.

## C10.4 · Sao chép & quorum — `In→Ad`

**Sub-leaves:** sao chép một-lãnh-đạo, nhiều-lãnh-đạo, không-lãnh-đạo · sao chép đồng bộ vs không đồng bộ và đánh đổi độ bền/độ trễ · độ trễ sao chép và đọc từ bản sao · chuyển đổi dự phòng (failover) và bầu lãnh đạo · split-brain và fencing token · quorum đọc/ghi: công thức R + W > N · sửa chữa khi đọc (read repair) và anti-entropy · giải quyết xung đột: last-write-wins và vì sao nó mất dữ liệu · hinted handoff

**Checkpoint:** tính được cấu hình quorum cho một mục tiêu chịu lỗi cho trước (ví dụ chịu được mất 1 node mà không mất dữ liệu và không mất khả năng ghi), và **chứng minh bằng thử nghiệm** giết node.

## C10.5 · Đồng thuận — `In→Ad`

**Sub-leaves:** bài toán đồng thuận và kết quả bất khả thi FLP · Paxos ở mức khái niệm · Raft: bầu lãnh đạo, sao chép log, an toàn — hiểu đủ để đọc log của etcd · nhóm thành viên và thay đổi cấu hình · khóa phân tán và vì sao nó khó đúng · leader lease và đồng hồ · khi nào bạn **không** cần đồng thuận (thường xuyên) · chi phí của đồng thuận: độ trễ, thông lượng, vận hành · etcd/ZooKeeper/Consul như dịch vụ điều phối

**Checkpoint:** nêu **3 tình huống cụ thể** trong hệ của bạn mà đồng thuận là lời giải sai, và chỉ ra lời giải đúng cho mỗi cái (thường: idempotency, hoặc một lãnh đạo tĩnh, hoặc chấp nhận eventual consistency).

## C10.6 · Idempotency & ngữ nghĩa giao hàng — `Ad→Ex` ★

**Sub-leaves:** at-most-once, at-least-once, exactly-once — và vì sao cái thứ ba không tồn tại ở tầng truyền tải · idempotency key: thiết kế, phạm vi, thời gian sống, lưu ở đâu · thao tác idempotent tự nhiên vs cần làm cho idempotent · dedup ở tầng nào: producer, broker, consumer, ứng dụng · cửa sổ dedup và đánh đổi bộ nhớ · retry an toàn và retry không an toàn · token yêu cầu và bảo vệ gửi trùng · idempotency trong API công khai · kiểm thử: gửi mọi request hai lần trong test

**Checkpoint:** thiết kế một API idempotent và **chứng minh bằng test tự động** rằng gửi mọi request 3 lần (kể cả khi bị ngắt giữa chừng) cho cùng kết quả và không tạo tác dụng phụ trùng lặp.

## C10.7 · Thay thế giao dịch phân tán — `In→Ad`

**Sub-leaves:** vì sao 2PC là vấn đề (blocking, coordinator là điểm hỏng đơn) · saga: choreography vs orchestration · hành động bù trừ (compensating action) và khi nào không bù được · mẫu outbox: đảm bảo sự kiện được phát khi DB commit · mẫu inbox ở phía consumer · nhất quán cuối cùng trong quy trình nghiệp vụ · trạng thái trung gian mà người dùng có thể nhìn thấy · hòa giải (reconciliation) như cơ chế an toàn cuối

**Checkpoint:** cài mẫu outbox và **chứng minh không mất sự kiện** khi tiến trình bị giết ngay sau khi DB commit nhưng trước khi publish — thử nghiệm lặp lại ≥50 lần.

## C10.8 · Phân mảnh & phân vùng — `In→Ad`

**Sub-leaves:** phân vùng theo khoảng vs theo băm · băm nhất quán và vành băm ảo · rebalancing và di chuyển dữ liệu · hot partition: nguyên nhân và giảm thiểu · chọn khóa phân vùng — quyết định khó đảo ngược nhất · truy vấn xuyên phân vùng và chi phí · index toàn cục vs index cục bộ · phân vùng theo tenant trong hệ đa tenant · phân vùng theo thời gian cho chuỗi thời gian

**Checkpoint:** chọn khóa phân vùng cho hệ của bạn, **chỉ ra kịch bản cụ thể gây hot partition**, ước lượng mức lệch tải, và đề xuất giảm thiểu.

## C10.9 · Giao tiếp giữa service — `Ad`

**Sub-leaves:** đồng bộ vs không đồng bộ — đánh đổi về coupling · request-response vs hướng sự kiện · coupling thời gian và cách phá vỡ nó · API gateway và mẫu backend-for-frontend · phiên bản hóa API và ngừng hỗ trợ · timeout theo tầng và ngân sách timeout tổng · lan truyền deadline · hủy bỏ và context · nội dung sự kiện: sự kiện mỏng vs sự kiện dày (notification vs event-carried state) · orchestration vs choreography cho quy trình

**Checkpoint:** chuyển một luồng đồng bộ 3 bước sang hướng sự kiện, và viết ra **chính xác bạn mất gì**: khả năng quan sát, tính đơn giản của debug, và đảm bảo nào không còn.

## C10.10 · Kiểm soát tải & sống sót — `Ad→Ex` ★

**Sub-leaves:** backpressure: cơ chế end-to-end, không phải cục bộ · giới hạn tốc độ: token bucket, leaky bucket, sliding window · giới hạn theo client vs toàn cục · loại bỏ tải (load shedding) và ưu tiên request · hàng đợi có giới hạn và chính sách loại bỏ · circuit breaker: trạng thái, ngưỡng, half-open · bulkhead: cách ly tài nguyên theo dependency · timeout + retry + jitter — và vì sao thiếu jitter gây đồng bộ hóa · retry budget và giới hạn khuếch đại · suy giảm duyên dáng: bỏ tính năng trước khi bỏ dịch vụ · thundering herd và cách phân tán · autoscaling: chỉ số nào, độ trễ phản ứng, dao động

**Checkpoint:** dưới tải **3× công suất thiết kế**, hệ của bạn suy giảm có kiểm soát (từ chối rõ ràng, latency giới hạn) thay vì sập — chứng minh bằng đồ thị throughput/latency/tỷ lệ lỗi khi tăng tải dần.

## C10.11 · Nguyên thủy cloud — `Ad`

**Sub-leaves:** mô hình compute: VM, container, serverless — đánh đổi thật · lớp lưu trữ: block, file, object, và chi phí từng loại · IAM: định danh, vai trò, chính sách, quyền tối thiểu · vai trò cho workload (không dùng khóa dài hạn) · quản lý bí mật trên cloud · mạng: VPC, subnet, security group (nối C5.13) · vùng và vùng khả dụng, và mô hình lỗi của chúng · hàng đợi và pub/sub được quản lý · chi phí: mô hình giá, dữ liệu ra, instance dự trữ vs spot · hạn ngạch và giới hạn dịch vụ — nguyên nhân sự cố bất ngờ · **học khái niệm, không học một vendor**

**Checkpoint:** dựng toàn bộ hạ tầng cho một dịch vụ từ zero với **quyền tối thiểu** — chứng minh bằng cách thử một thao tác không được phép và thấy nó bị từ chối.

## C10.12 · Kubernetes như một control loop — `In→Ad`

**Sub-leaves:** vòng lặp điều hòa (reconciliation loop) — mô hình cốt lõi · trạng thái mong muốn vs trạng thái thực tế · API server, etcd, scheduler, controller manager, kubelet · pod, deployment, statefulset, daemonset — khi nào dùng cái nào · service và cách kube-proxy thực hiện · yêu cầu và giới hạn tài nguyên; QoS class; OOMKill · probe: liveness, readiness, startup — và cấu hình sai gây gì · ConfigMap, Secret, và giới hạn của chúng · CRD và operator — mở rộng control loop · autoscaler: HPA, VPA, cluster autoscaler · **tự viết một controller tối giản** để hiểu mô hình · khi nào Kubernetes là quá mức cần thiết

**Checkpoint:** viết một controller tối giản (bằng Go hoặc Python) điều hòa một CRD đơn giản, chạy trong cluster, và **giải thích được vòng lặp điều hòa bằng chính code của bạn**.

**Cạm bẫy:** học Kubernetes bằng cách thuộc YAML. Mô hình quan trọng hơn cú pháp; cú pháp tra được.

## C10.13 · Hạ tầng dưới dạng mã — `In→Ad`

**Sub-leaves:** mô hình khai báo và tại sao nó khác script · state file: vai trò, khóa, lưu từ xa, và nguy hiểm khi mất · plan/apply và đọc plan cẩn thận · drift: phát hiện và hòa giải · module và tái sử dụng · biến, output, và quản lý bí mật trong IaC · phụ thuộc và thứ tự tạo tài nguyên · di trú tài nguyên: import, move, và đổi tên · Terraform vs OpenTofu: **cùng mô hình HCL, cùng protocol provider, cùng state model; khác biệt là giấy phép và quản trị** [Fact 2026] · thay thế: Pulumi (ngôn ngữ thật), Crossplane (control plane K8s) · kiểm thử IaC và quét chính sách · GitOps: Argo CD, Flux — điều hòa từ git

**Checkpoint:** **phá hủy toàn bộ hạ tầng và dựng lại hoàn toàn từ code**, không thao tác tay nào, và dịch vụ hoạt động trở lại — đo thời gian.

## C10.14 · Đa vùng, edge–cloud, data gravity — `In→Ad`

**Sub-leaves:** vì sao đa vùng khó hơn nhiều so với đa AZ · sao chép xuyên vùng và độ trễ · active-active vs active-passive · định tuyến lưu lượng theo địa lý · data gravity: dữ liệu nặng kéo tính toán về phía nó · chủ quyền dữ liệu và ràng buộc pháp lý (nối A5) · phân chia edge–cloud: quyết định cái gì tính ở đâu · tiêu chí: băng thông, độ trễ, quyền riêng tư, chi phí, khả năng offline · tính toán phân tầng: thiết bị → gateway → edge → cloud · triển khai model tới edge và quản lý phiên bản ở quy mô

**Checkpoint:** cho 5 chức năng trong hệ của bạn, quyết định vị trí tính toán cho mỗi cái và **bảo vệ bằng số**: băng thông tiết kiệm, độ trễ đạt được, chi phí, và hành vi khi mất kết nối.

---

## ▸ Thứ tự học trong C10

```
1. Mô hình lỗi ★                      (Phase 2, ~35 h)  ← trước mọi thứ khác
2. Idempotency + ngữ nghĩa giao hàng ★(Phase 3, ~40 h)
3. Thời gian trong hệ phân tán         (Phase 3, ~25 h)  ← cùng lúc C7.9
4. Mô hình nhất quán                   (Phase 3, ~30 h)
5. Sao chép + quorum                   (Phase 3, ~25 h)
6. Kiểm soát tải & sống sót ★          (Phase 3, ~40 h)
7. Giao tiếp giữa service              (Phase 3, ~25 h)
8. Nguyên thủy cloud                   (Phase 4, ~35 h)
9. Đồng thuận (Raft)                   (Phase 4, ~30 h)
10. Thay thế giao dịch phân tán        (Phase 4, ~25 h)
11. Phân mảnh + phân vùng              (Phase 4, ~20 h)
12. IaC                                (Phase 4, ~25 h)
13. Kubernetes control loop            (Phase 4, ~40 h)  ← SAU distributed systems
14. Đa vùng + edge-cloud               (Phase 5, ~25 h)
```

## ▸ Tài nguyên chính C10

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| 6.824 *Distributed Systems* + **lab Raft** | MIT | C10.1–C10.5 | 110 |
| *Distributed Systems* lecture series (Kleppmann) — miễn phí | University of Cambridge | C10.2, C10.3, C10.5 | 35 |
| *Designing Data-Intensive Applications* — phần II | — | C10.3, C10.4, C10.6 | 30 |
| Paper Raft (*In Search of an Understandable Consensus Algorithm*) | — | C10.5 — primary source | 10 |
| *Site Reliability Engineering* — miễn phí toàn văn | Google | C10.10, nối C11 | 30 |
| Kubernetes documentation — phần Concepts | CNCF | C10.12 | 35 |
| *Programming Kubernetes* hoặc kubebuilder book | — | C10.12 phần controller | 25 |
| OpenTofu / Terraform documentation | OpenTofu / HashiCorp | C10.13 | 25 |
| Bài viết về Jepsen (Kyle Kingsbury) | Jepsen | C10.3, C10.4 — kiểm chứng thực nghiệm | 20 |
| *Release It!* (Nygard) | — | C10.10 — mẫu ổn định | 20 |

---

# ◆ C11 · OBSERVABILITY, RELIABILITY & PERFORMANCE

**Mức mục tiêu:** **Advanced**
**Ngân sách:** ~260 h · Phase 2: 40 h · Phase 3: 60 h · Phase 4: 120 h · Phase 5: 40 h
**Vị trí:** con của OS + Distributed; là `observe` của vòng lặp.
**Vì sao Advanced:** "debug được" và "tối ưu được" nằm **trong chính định nghĩa mục tiêu** của bạn.

## C11.1 · Bốn tín hiệu và câu hỏi mỗi cái trả lời — `Ad→Ex`

**Sub-leaves:** metric: tổng hợp, rẻ, không có ngữ cảnh từng request · log: chi tiết, đắt, khó tổng hợp · trace: quan hệ nhân quả xuyên service, lấy mẫu · profile: phân bổ tài nguyên trong tiến trình · loại metric: counter, gauge, histogram, summary — và vì sao histogram cần thiết cho phân vị · cardinality của label và vụ nổ cardinality · log có cấu trúc vs log văn bản · mức độ log và cái gì đáng log · lấy mẫu: đầu đuôi (head/tail sampling) trong trace · chi phí của mỗi tín hiệu và ngân sách quan sát · continuous profiling · sự kiện (event) như tín hiệu thứ năm

**Checkpoint:** cho **5 sự cố khác nhau** (mô tả triệu chứng), nói ngay tín hiệu nào cần nhìn trước cho mỗi cái, và lý do — rồi kiểm chứng bằng cách dựng lại 5 sự cố đó thật.

## C11.2 · Instrumentation & OpenTelemetry — `Ad`

**Sub-leaves:** mô hình dữ liệu OTel: signal, resource, attribute · lan truyền ngữ cảnh (context propagation) và trace context W3C · span, span link, sự kiện trong span · instrumentation tự động vs thủ công · SDK, collector, exporter — kiến trúc · lấy mẫu ở đâu trong pipeline · quy ước ngữ nghĩa (semantic convention) và vì sao tuân thủ giúp · chi phí instrumentation và tác động tới latency · instrumentation cho firmware và thiết bị hạn chế · correlation ID xuyên toàn hệ, từ thiết bị tới DB

**Checkpoint:** trace một request đi qua **≥4 service + 1 thiết bị**, xác định tầng nào chiếm phần lớn latency, và chứng minh bằng waterfall của trace.

## C11.3 · SLI, SLO, error budget — `In→Ad`

**Sub-leaves:** chọn SLI đúng: đo trải nghiệm người dùng, không đo tài nguyên · SLI cho availability, latency, chất lượng, freshness · cửa sổ SLO và cửa sổ trượt · error budget và chính sách tiêu thụ · cảnh báo dựa trên tốc độ tiêu thụ (burn rate) nhiều cửa sổ · SLO cho hệ ML: chất lượng dự đoán như một SLI · SLO cho thiết bị: tỷ lệ thiết bị online, độ tươi của dữ liệu · đàm phán SLO với bên phụ thuộc · vì sao 99,99% thường là lựa chọn sai

**Checkpoint:** định nghĩa SLO cho hệ của bạn, tính error budget hàng tháng, thiết lập cảnh báo burn-rate nhiều cửa sổ, và **giải thích vì sao bạn không chọn một số 9 cao hơn** — bằng chi phí.

## C11.4 · Phân phối độ trễ — `Ad→Ex` ★

**Sub-leaves:** vì sao trung bình vô dụng · phân vị và cách tính chúng đúng (t-digest, HDR histogram) · **phân vị không cộng được** — lỗi phổ biến nhất trong đo latency · khuếch đại đuôi (tail amplification) trong fan-out · latency đuôi và số lượng dependency · coordinated omission trong công cụ đo tải · latency ở mỗi tầng và cách phân rã · hedged request và backup request · ảnh hưởng của GC, JIT, page fault lên đuôi · biểu đồ heatmap của latency theo thời gian

**Checkpoint:** giải thích được **bằng dữ liệu** vì sao p99 của một service tệ trong khi p50 đẹp — phân rã latency theo tầng và xác định nguồn của đuôi.

## C11.5 · Trực giác hàng đợi — `In→Ad`

**Sub-leaves:** định luật Little và ứng dụng thực tế · đường cong utilization–latency và tại sao nó phi tuyến · vì sao 80% utilization đã là nguy hiểm · M/M/1 và M/M/c ở mức trực giác · biến thiên của thời gian phục vụ và tác động lên hàng đợi · hàng đợi có giới hạn vs không giới hạn · kỷ luật hàng đợi: FIFO, LIFO, ưu tiên — và vì sao LIFO đôi khi tốt hơn khi quá tải · độ sâu hàng đợi như chỉ số cảnh báo sớm · hệ thống mở vs đóng trong mô hình tải

**Checkpoint:** **dự đoán trước khi đo** độ trễ sẽ tăng bao nhiêu khi utilization từ 70% lên 90%, rồi đo và so sánh — sai số dưới 2× là đạt.

## C11.6 · Profiling — `Ad`

**Sub-leaves:** profiling lấy mẫu vs instrumenting · CPU profiling và flamegraph — đọc đúng · off-CPU profiling: thời gian chờ ở đâu · memory profiling: heap, allocation rate, rò rỉ · I/O profiling · lock contention profiling · profiling trong production với chi phí thấp · differential flamegraph để so sánh trước/sau · profiling GPU và kernel ML · profiling firmware trên MCU (SWO, bộ đếm chu kỳ) · quy kết: hàm nào thật sự tốn, không phải hàm nào xuất hiện nhiều

**Checkpoint:** tìm và sửa một nút thắt **thật** trong hệ của bạn bằng profiling — và chứng minh rằng nút thắt bạn *tưởng* trước khi profile là sai.

## C11.7 · Phương pháp benchmark — `Ad→Ex` ★

**Sub-leaves:** benchmark nói dối như thế nào: warm-up, cache nóng, compiler loại bỏ code chết · biến thiên và ý nghĩa thống kê của chênh lệch · kiểm soát môi trường: tần số CPU, nhiễu từ tiến trình khác, thermal · microbenchmark vs macrobenchmark — khi nào cái nào lừa dối · coordinated omission trong công cụ đo tải · đo throughput ở latency cố định, không đo throughput tối đa · workload đại diện vs workload tiện lợi · báo cáo: phân phối, không phải một con số · tái lập và công bố phương pháp · đọc benchmark của người khác một cách hoài nghi

**Checkpoint:** lấy một benchmark công khai (của một công cụ bạn định dùng), chỉ ra **≥3 lỗi phương pháp** trong đó, và chạy lại theo cách bạn cho là đúng — kết quả khác biệt bao nhiêu?

## C11.8 · Capacity planning & load testing — `In→Ad`

**Sub-leaves:** mô hình hóa tải: đơn vị công việc, tỷ lệ đến, phân phối · headroom và vì sao 100% không bao giờ là mục tiêu · load test: ramp, soak, spike, breakpoint · tìm điểm gãy và mô tả nó (gãy như thế nào, không chỉ ở đâu) · test với dữ liệu và độ đồng thời thực tế · môi trường test vs production và chênh lệch · dự báo: tải tăng 10× thì cái gì gãy trước · kế hoạch mở rộng: dọc, ngang, và giới hạn của mỗi cái · capacity cho workload inference (GPU, bộ nhớ, KV cache)

**Checkpoint:** chạy load test tìm điểm gãy của hệ, mô tả **chính xác cách nó gãy** (thành phần nào, triệu chứng gì, có phục hồi được không), và đưa ra kế hoạch mở rộng có số.

## C11.9 · Incident response & postmortem — `In→Ad`

**Sub-leaves:** phát hiện, phân loại, giảm thiểu, giải quyết — bốn giai đoạn · vai trò trong sự cố: chỉ huy, liên lạc, vận hành · giảm thiểu trước, hiểu sau · runbook và khi nào nó hữu ích · timeline sự cố và cách dựng lại · postmortem blameless: nguyên tắc và cách viết · nguyên nhân gốc là số nhiều, không phải số ít · Five Whys và giới hạn của nó · action item có thể kiểm chứng vs mong muốn mơ hồ · theo dõi action item tới khi hoàn thành · học từ sự cố suýt xảy ra (near miss)

**Checkpoint:** viết một postmortem blameless cho một sự cố thật (trong dự án của bạn hoặc ở nơi làm việc), với timeline chính xác tới phút, ≥3 yếu tố góp phần, và action item **có tiêu chí hoàn thành kiểm chứng được**.

## C11.10 · Failure injection & chaos — `In→Ad`

**Sub-leaves:** giả thuyết trước, thí nghiệm sau — chaos là phương pháp khoa học · bắt đầu từ môi trường staging · loại lỗi tiêm: giết tiến trình, phân vùng mạng, độ trễ, mất gói, hết đĩa, đồng hồ lệch · tiêm lỗi ở tầng ứng dụng · game day và diễn tập · bán kính nổ (blast radius) và cách giới hạn · chaos cho hệ nhúng: cắt điện, ngắt mạng, nhiệt độ cực đoan · tự động hóa chaos trong CI · đo: hệ có đạt SLO trong lúc thí nghiệm không

**Checkpoint:** trong lúc hệ đang phục vụ tải, **giết một thành phần ngẫu nhiên** và chứng minh hệ vẫn đạt SLO — lặp lại cho ít nhất 5 thành phần khác nhau, kể cả thiết bị vật lý.

## C11.11 · Thiết kế cảnh báo — `In→Ad`

**Sub-leaves:** cảnh báo trên triệu chứng, không trên nguyên nhân · mọi cảnh báo phải có hành động — nếu không thì xóa · mệt mỏi cảnh báo và chi phí thật của nó · ngưỡng tĩnh vs động vs dựa trên SLO · cảnh báo burn-rate nhiều cửa sổ · gom nhóm và chống trùng lặp · định tuyến và leo thang · giờ làm việc vs trực đêm · cảnh báo cho hệ ML: chất lượng giảm, drift, dữ liệu không tới · cảnh báo cho đội thiết bị: bao nhiêu thiết bị offline là bất thường · kiểm thử cảnh báo

**Checkpoint:** giảm số cảnh báo trong hệ của bạn **≥50%** mà **không** giảm khả năng phát hiện sự cố — chứng minh bằng cách chạy lại các sự cố lịch sử và xác nhận bộ cảnh báo mới vẫn bắt được.

## C11.12 · Mẫu độ tin cậy ở tầng code — `Ad`

**Sub-leaves:** retry với backoff hàm mũ + jitter đầy đủ · idempotency là điều kiện tiên quyết của retry · circuit breaker: tham số và cách điều chỉnh · bulkhead: pool riêng cho mỗi dependency · timeout theo tầng và ngân sách tổng · fallback và giá trị mặc định an toàn · suy giảm duyên dáng: xác định trước tính năng nào bỏ trước · health check: nông vs sâu, và vì sao health check sâu nguy hiểm · graceful shutdown và drain kết nối · khởi động: warm-up, và vì sao cold start gây sự cố khi mở rộng

**Checkpoint:** với **mỗi dependency** trong hệ của bạn, định nghĩa hành vi khi nó chết, cài đặt, và **chứng minh bằng thử nghiệm** — không phải bằng code review.

## C11.13 · Quan sát chi phí — `In→Ad`

**Sub-leaves:** gán chi phí theo tính năng, không chỉ theo dịch vụ · chi phí mỗi request, mỗi inference, mỗi thiết bị · chi phí ẩn: truyền dữ liệu, lưu trữ log, chính hệ thống quan sát · tag và phân bổ chi phí trên cloud · phát hiện chi phí bất thường · đánh đổi chi phí–hiệu năng: đường cong Pareto · dự báo chi phí khi tải tăng · FinOps ở mức thực hành cá nhân · **chi phí của hệ quan sát có thể vượt chi phí của hệ được quan sát** — kiểm soát nó

**Checkpoint:** dựng dashboard chi phí **theo tính năng** (không theo dịch vụ), và xác định tính năng nào có tỷ lệ chi phí/giá trị tệ nhất.

## C11.14 · Debug hệ phân tán & hệ ML — `Ad→Ex`

**Sub-leaves:** correlation ID từ thiết bị tới cơ sở dữ liệu · lưu request/response để phát lại (replay) · shadow traffic và so sánh · debug bằng nhị phân tìm kiếm trên thời gian và trên cấu hình · khác biệt giữa môi trường và cách loại trừ · debug lỗi không tái tạo được: tăng quan sát trước, sửa sau · debug hệ ML: dự đoán sai vì input, vì model, hay vì pipeline · phân tích lỗi có hệ thống trên tập dự đoán sai · debug thiết bị ngoài thực địa: log từ xa, chế độ chẩn đoán, dump trạng thái · debug vấn đề chỉ xuất hiện ở quy mô

**Checkpoint:** tái hiện một lỗi production trong môi trường test **bằng replay** dữ liệu thật, xác định nguyên nhân, và chứng minh bản sửa bằng cách chạy lại cùng dữ liệu.

---

## ▸ Thứ tự học trong C11

```
1. Bốn tín hiệu + instrumentation      (Phase 2, ~40 h)  ← sớm, dùng suốt
2. Profiling                            (Phase 3, ~35 h)  ← cùng lúc C3.14
3. Phân phối độ trễ ★                   (Phase 3, ~25 h)
4. Phương pháp benchmark ★              (Phase 3–4, ~30 h)
5. SLI/SLO/error budget                 (Phase 4, ~25 h)
6. Trực giác hàng đợi                   (Phase 4, ~20 h)  ← cùng lúc S7
7. Mẫu độ tin cậy ở tầng code           (Phase 4, ~25 h)  ← cùng lúc C10.10
8. Capacity + load testing              (Phase 4, ~25 h)
9. Thiết kế cảnh báo                    (Phase 4, ~15 h)
10. Failure injection + chaos           (Phase 4, ~20 h)
11. Incident + postmortem               (Phase 4–5, ~15 h)
12. Debug phân tán + ML                 (Phase 5, ~25 h)
13. Quan sát chi phí                    (Phase 5, ~15 h)
```

## ▸ Tài nguyên chính C11

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| *Site Reliability Engineering* + *SRE Workbook* — **miễn phí toàn văn** | Google | C11.3, C11.9, C11.11 | 45 |
| *Systems Performance* (Brendan Gregg) | — | C11.1, C11.4, C11.6, C11.7 | 50 |
| *BPF Performance Tools* (Gregg) | — | C11.6 nâng cao | 25 |
| OpenTelemetry documentation + semantic conventions | CNCF | C11.2 — primary source | 25 |
| Prometheus documentation + PromQL | CNCF | C11.1, C11.3 | 20 |
| *Release It!* (Nygard) | — | C11.12 | 20 |
| Bài viết của Gil Tene về coordinated omission | — | C11.4, C11.7 | 8 |
| Tài liệu Principles of Chaos Engineering | — | C11.10 | 10 |
| Postmortem công khai (Google, Cloudflare, GitHub, AWS) | các công ty | C11.9 — đọc ≥20 cái | 25 |

---

# ◆ C12 · SYSTEMS ARCHITECTURE & INTEGRATION

**Mức mục tiêu:** **Advanced → Expert** — đỉnh của roadmap
**Ngân sách:** ~220 h · Phase 3: 40 h · Phase 4: 70 h · Phase 5: 110 h
**Vị trí:** hội tụ của toàn bộ graph. Không học được sớm — cần vật liệu từ 11 nhánh kia.
**Vì sao Expert khả thi:** không vì bạn dành nhiều giờ nhất, mà vì đây là nhánh **tổng hợp** — mỗi giờ ở 11 nhánh kia đều đóng góp vào đây.

## C12.1 · Từ yêu cầu tới ràng buộc tới kiến trúc — `Ad→Ex`

**Sub-leaves:** phân biệt yêu cầu chức năng và thuộc tính chất lượng · rút ràng buộc **định lượng** từ mô tả mơ hồ · kịch bản chất lượng: nguồn kích thích, môi trường, phản hồi, đo lường phản hồi · ràng buộc cứng vs ưu tiên mềm · giả định: nhận diện, ghi lại, và kiểm chứng · yêu cầu ngầm: pháp lý, vận hành, tổ chức · câu hỏi cần hỏi trước khi thiết kế · khi nào yêu cầu tự nó sai và cần đẩy lại

**Checkpoint:** từ một mô tả một đoạn văn mơ hồ ("chúng tôi muốn giám sát máy móc trong nhà xưởng"), rút ra **≥8 ràng buộc định lượng**, mỗi cái có đơn vị và con số, và kiểm chứng chúng với người đặt yêu cầu.

## C12.2 · Thuộc tính chất lượng & đánh đổi — `Ad→Ex` ★

**Sub-leaves:** danh mục: latency, throughput, availability, durability, consistency, security, privacy, cost, evolvability, operability, testability, portability · vì sao chúng xung đột và xung đột ở đâu cụ thể · chiến thuật kiến trúc cho từng thuộc tính · đánh đổi không thể tránh: CAP, latency vs durability, cost vs redundancy, đơn giản vs linh hoạt · làm cho đánh đổi **hiển thị** thay vì ẩn · phương pháp đánh giá kiến trúc (ATAM ở mức đơn giản hóa) · ma trận quyết định có trọng số và giới hạn của nó

**Checkpoint:** trình bày **3 kiến trúc** cho cùng một bài toán, mỗi cái tối ưu một thuộc tính khác nhau, với bảng so sánh định lượng, và bảo vệ được lựa chọn trước ba câu hỏi phản biện khác nhau.

## C12.3 · Thiết kế interface & contract — `Ad→Ex`

**Sub-leaves:** interface tối thiểu và nguyên tắc che giấu thông tin · thiết kế cho người gọi, không cho người cài đặt · ngữ nghĩa: idempotency, thứ tự, độ bền, tính nhất quán — nêu rõ trong contract · lỗi là một phần của interface · versioning: URL, header, content negotiation · tương thích ngược và chiến lược ngừng hỗ trợ · contract test giữa producer và consumer · interface giữa phần cứng và phần mềm (HAL) · interface giữa model ML và ứng dụng · tài liệu interface như một phần của code

**Checkpoint:** thay đổi cài đặt của một service **mà không phá bất kỳ consumer nào** — chứng minh bằng contract test tự động chạy consumer phiên bản cũ.

## C12.4 · Tách data flow khỏi control flow — `Ad`

**Sub-leaves:** hai sơ đồ cho cùng một hệ và vì sao cần cả hai · nơi chúng giao nhau là nơi nguy hiểm nhất · đường dữ liệu (data plane) vs đường điều khiển (control plane) · vì sao control plane hỏng không nên làm data plane hỏng · cấu hình như control plane · triển khai model như control plane · tách biệt trong hệ nhúng: luồng cảm biến vs lệnh điều khiển

**Checkpoint:** vẽ riêng data flow và control flow cho hệ của bạn, xác định mọi điểm giao, và **chứng minh bằng thử nghiệm** rằng control plane chết không làm data plane chết.

## C12.5 · Phân tích chế độ hỏng xuyên tầng — `Ad→Ex` ★

**Sub-leaves:** FMEA áp dụng cho hệ phần mềm + phần cứng · severity, occurrence, detection, và RPN · fault tree analysis: từ sự cố ngược về nguyên nhân · phân tích cây sự kiện: từ lỗi xuôi về hậu quả · lỗi lan truyền xuyên tầng: ví dụ cụ thể từ vòng lặp của bạn · lỗi tương quan và điểm hỏng đơn ẩn · lỗi im lặng và cơ chế phát hiện · chế độ hỏng của ML (nối C8.16) trong ngữ cảnh hệ thống · chế độ hỏng của phần cứng (nối C7.6) lan lên tầng ứng dụng · tài liệu hóa và duy trì phân tích

**Checkpoint:** chạy FMEA đầy đủ cho hệ của bạn (≥30 chế độ hỏng), tìm **≥3 chế độ hỏng bạn chưa từng nghĩ tới**, và thêm cơ chế phát hiện hoặc giảm thiểu cho mỗi cái.

## C12.6 · Phân chia edge–cloud — `Ad→Ex` ★ năng lực phân biệt

**Sub-leaves:** tiêu chí quyết định: băng thông, độ trễ, quyền riêng tư, chi phí, khả năng offline, khả năng cập nhật · tính toán phân tầng: cảm biến → MCU → gateway → edge server → cloud · dữ liệu thô vs đặc trưng vs quyết định — truyền cái nào · inference ở đâu và lý do định lượng · trạng thái ở đâu và nguồn sự thật là gì · hành vi khi mất kết nối ở mỗi tầng · cập nhật model và firmware tới hàng nghìn thiết bị · chi phí: băng thông cellular vs compute cloud vs BOM thiết bị · quyền riêng tư: xử lý tại chỗ như một quyết định kiến trúc · di chuyển ranh giới sau này: thiết kế để thay đổi được

**Checkpoint:** cho **5 chức năng** trong hệ của bạn, quyết định vị trí tính toán cho mỗi cái với **lập luận định lượng đầy đủ**: byte truyền, độ trễ, chi phí/tháng, hành vi offline. Sau đó thực hiện và đo — dự đoán sai bao nhiêu?

## C12.7 · Quản lý trạng thái & nguồn sự thật — `Ad→Ex`

**Sub-leaves:** trạng thái ở đâu: thiết bị, cache, DB, hàng đợi, model · nguồn sự thật duy nhất và vì sao nhiều nguồn luôn phân kỳ · trạng thái dẫn xuất và tái tạo được · trạng thái nhất thời vs bền vững · cấu hình như trạng thái và cách phân phối nó · trạng thái trong ML: model là trạng thái, đặc trưng là trạng thái · hòa giải khi các bản sao phân kỳ · migration trạng thái khi đổi schema hoặc đổi thiết kế · trạng thái trong hệ nhúng: cái gì sống sót qua reset, qua mất điện

**Checkpoint:** vẽ bản đồ **mọi nơi** một sự thật cụ thể được lưu trong hệ của bạn (ví dụ "ngưỡng cảnh báo của thiết bị X"), chỉ ra nguồn sự thật, và mô tả cơ chế hòa giải khi chúng lệch nhau.

## C12.8 · Mẫu kiến trúc — `Ad`

**Sub-leaves:** phân tầng và vi phạm phân tầng · hướng sự kiện: pub/sub, event sourcing, CQRS · pipeline và filter · vòng lặp điều khiển (control loop) như mẫu kiến trúc · microservice vs monolith module hóa — đánh đổi thật, không phải thời trang · kiến trúc hexagonal / ports-and-adapters · sidecar và ambassador · kiến trúc phân tầng cho edge · mẫu chống: distributed monolith, chatty interface, shared database · nhận diện mẫu trong hệ lạ

**Checkpoint:** đọc một hệ thống lạ (mã nguồn mở) trong **≤4 giờ** và xác định được mẫu kiến trúc chính, vi phạm phân tầng nếu có, và hai điểm yếu.

## C12.9 · Kiến trúc tham chiếu — `Ad`

**Sub-leaves:** IoT platform: thiết bị → gateway → ingest → xử lý → lưu trữ → API → UI, cộng device management, OTA, provisioning · ML platform: dữ liệu → feature → train → registry → serve → monitor → retrain · hệ agentic: orchestration, tool boundary, state store, eval, guardrail, quan sát · hệ điều khiển công nghiệp và mô hình an toàn của nó · so sánh: cái gì chung, cái gì khác · điểm yếu cố hữu của mỗi kiến trúc tham chiếu · khi nào lệch khỏi kiến trúc tham chiếu là đúng

**Checkpoint:** vẽ lại cả **3 kiến trúc tham chiếu** từ trí nhớ, và cho mỗi cái nêu ≥2 điểm yếu cố hữu mà các bài viết marketing không nhắc tới.

## C12.10 · Build-vs-buy & vendor lock-in — `In→Ad`

**Sub-leaves:** tổng chi phí sở hữu: license + vận hành + học + thoát · chi phí ẩn của tự xây: bảo trì, on-call, bus factor · chi phí ẩn của mua: giới hạn, lock-in, thay đổi giá, ngừng sản phẩm · đo mức lock-in: chi phí thoát tính bằng người-tháng · lock-in ở tầng nào: API, dữ liệu, vận hành, kỹ năng · chiến lược giảm lock-in: lớp trừu tượng, định dạng mở, thoát được · rủi ro nhà cung cấp: tài chính, giấy phép, thay đổi chiến lược — **ví dụ: thay đổi giấy phép Terraform năm 2023 sinh ra OpenTofu** · open-source như một lựa chọn có chi phí vận hành

**Checkpoint:** phân tích một quyết định build-vs-buy thật trong dự án của bạn, với **chi phí thoát tính bằng người-tháng** cho phương án "mua".

## C12.11 · Migration & tiến hóa — `In→Ad`

**Sub-leaves:** strangler fig: thay thế dần, không rewrite lớn · ghi kép (dual write) và rủi ro của nó · đọc bóng (shadow read) và so sánh · cờ tính năng và triển khai dần · backfill dữ liệu lịch sử · migration schema không downtime: expand–migrate–contract · migration hạ tầng: blue-green, canary · rollback: luôn phải có, và phải được test · migration firmware trên đội thiết bị đang chạy · đo tiến độ migration và biết khi nào xong

**Checkpoint:** lập kế hoạch migration **không downtime** cho một thành phần trong hệ của bạn (ví dụ đổi storage engine hoặc đổi giao thức thiết bị), thực hiện, và chứng minh không có request nào thất bại trong suốt quá trình.

## C12.12 · Tài liệu kiến trúc — `Ad→Ex`

**Sub-leaves:** ADR: cấu trúc, khi nào viết, cách giữ nó sống · design doc/RFC: vấn đề, ràng buộc, phương án đã cân nhắc, quyết định, rủi ro · **ghi lại phương án bị loại và lý do** — phần giá trị nhất · mô hình C4: context, container, component, code · sequence diagram cho luồng quan trọng · sơ đồ data flow và control flow riêng biệt · tài liệu vận hành: runbook, playbook · giữ tài liệu đồng bộ với code (diagram-as-code) · viết cho người đọc 6 tháng sau, không cho người review tuần này

**Checkpoint:** viết một ADR mà **một kỹ sư lạ đọc 6 tháng sau ra được cùng quyết định** — kiểm chứng bằng cách đưa cho một người thật đọc và hỏi họ quyết định gì.

## C12.13 · Design review — `Ad`

**Sub-leaves:** chuẩn bị: người review cần gì trước cuộc họp · đặt câu hỏi tìm rủi ro, không tìm lỗi chính tả · các câu hỏi luôn đáng hỏi: cái gì hỏng trước, dữ liệu ở đâu, ai gọi cái này, chi phí bao nhiêu, làm sao biết nó hỏng · phân biệt "tôi làm khác" với "cái này sai" · review thiết kế có ML: câu hỏi đặc thù · nhận review khó mà không phòng thủ · ghi lại quyết định từ review · review kiến trúc của chính mình sau 6 tháng

**Checkpoint:** review thiết kế của người khác và nêu được **≥3 rủi ro họ chưa thấy** — xác nhận bằng phản hồi của chính họ.

## C12.14 · Security & privacy by design — `Ad`

**Sub-leaves:** threat model cho **toàn vòng lặp**, không chỉ cho API · ranh giới tin cậy và nơi dữ liệu vượt qua chúng · định danh cho thiết bị, dịch vụ, người dùng, model · quyền tối thiểu ở mọi tầng · tối thiểu hóa dữ liệu như quyết định kiến trúc · xử lý tại chỗ để tránh truyền dữ liệu nhạy cảm · mã hóa khi truyền và khi lưu — và giới hạn của nó · ranh giới tool-use cho agent (nối C8.12) · nhật ký kiểm toán và khả năng truy vết quyết định · quyền được xóa trong hệ có nhiều bản sao · phản ứng khi lộ dữ liệu

**Checkpoint:** threat model cho toàn vòng `sense → act` của hệ bạn, tìm **≥3 vector tấn công** bạn chưa từng nghĩ tới, và thiết kế biện pháp giảm thiểu cho mỗi cái.

---

## C12.15 · Kiến trúc phân tầng công nghiệp: ISA-95 và Purdue — `In→Ad`

*Leaf bổ sung ở v3. C12.9 của v2 liệt kê ba kiến trúc tham chiếu (IoT platform, ML platform, hệ agentic) nhưng thiếu kiến trúc tham chiếu đã tồn tại lâu nhất và đang chi phối mọi tài sản vật lý công nghiệp.*

**Sub-leaves:**
- **ISA-95 / IEC 62264**: Level 0 (quá trình vật lý) → L1 (cảm biến & chấp hành) → L2 (điều khiển: PLC/DCS/SCADA) → L3 (MES: điều độ sản xuất) → L4 (ERP: kế hoạch kinh doanh)
- **Mô hình Purdue** cho phân tách mạng, và mối quan hệ với ISA-95
- Ngữ nghĩa dữ liệu đổi thế nào khi đi lên từng tầng: từ giá trị thô → đại lượng vật lý → sự kiện có nghĩa → chỉ số kinh doanh
- Thang thời gian đổi theo tầng: mili giây ở L1–L2, giây–phút ở L3, giờ–ngày ở L4
- Vì sao mô hình này **đang bị áp lực**: edge computing, kết nối trực tiếp lên cloud, và mô hình unified namespace
- **Unified Namespace** và kiến trúc hướng sự kiện trong công nghiệp — thay thế hay bổ sung cho ISA-95
- Đối chiếu ISA-95 với vòng lặp của roadmap này: `sense/act` ≈ L0–L1 · `decide` ≈ L2 · `store/observe` ≈ L2–L3 · `learn/infer/adapt` **không có chỗ trong ISA-95** — và đó chính là khoảng trống mà toàn bộ ngành đang tìm cách lấp
- Đưa ML vào kiến trúc phân tầng: chạy ở tầng nào, ai chịu trách nhiệm, và làm sao không phá tính xác định của L2
- Digital twin đặt ở đâu trong mô hình
- Cạm bẫy khi áp kiến trúc IT lên tài sản công nghiệp và ngược lại

**Dùng để xây:** từ vựng chung để nói chuyện với cả hai thế giới. Đây là **leaf có giá trị phiên dịch cao nhất** trong toàn bộ C12.

**Checkpoint:** lấy một hệ thống bạn biết, vẽ nó theo ISA-95, chỉ ra **chính xác** tầng nào phần `learn/infer/adapt` nên nằm và vì sao; sau đó vẽ lại theo unified namespace và so sánh cái gì được, cái gì mất.

**[Inference]** Đây là leaf mà giá trị của nó tăng theo thời gian: khoảng trống `learn/infer/adapt` trong ISA-95 là khoảng trống mà mọi nhà cung cấp công nghiệp đang cố lấp, và chưa ai lấp gọn. Người hiểu cả hai phía của khoảng trống đó ở vị thế hiếm.


## ▸ Thứ tự học trong C12

```
1. Tài liệu kiến trúc (ADR, RFC)      (Phase 3, ~25 h)  ← bắt đầu sớm, viết mọi quyết định
2. Mẫu kiến trúc                       (Phase 3, ~20 h)
3. Thiết kế interface & contract       (Phase 4, ~25 h)
4. Yêu cầu → ràng buộc → kiến trúc     (Phase 4, ~20 h)
5. Thuộc tính chất lượng & đánh đổi ★  (Phase 4, ~25 h)
6. Tách data/control flow              (Phase 4, ~10 h)
7. Kiến trúc tham chiếu                (Phase 4, ~20 h)
8. Phân tích chế độ hỏng (FMEA) ★      (Phase 5, ~25 h)  ← cùng lúc S6
9. Phân chia edge–cloud ★              (Phase 5, ~25 h)
10. Quản lý trạng thái                 (Phase 5, ~15 h)
11. Security & privacy by design       (Phase 5, ~20 h)
12. Migration & tiến hóa               (Phase 5, ~20 h)
13. Build-vs-buy                       (Phase 5, ~10 h)
14. Design review                      (Phase 5, ~10 h)  ← thực hành liên tục
```

## ▸ Tài nguyên chính C12

| Tài nguyên | Tổ chức | Dùng cho | Giờ |
|---|---|---|---|
| *Software Architecture in Practice* (Bass, Clements, Kazman) | SEI / Carnegie Mellon | C12.1, C12.2 | 35 |
| *Fundamentals of Software Architecture* (Richards & Ford) | — | C12.8, C12.2 | 25 |
| *Designing Data-Intensive Applications* — phần III | — | C12.9 | 20 |
| *A Philosophy of Software Design* (Ousterhout) | — | C12.3 | 15 |
| Mô hình C4 — tài liệu của Simon Brown | — | C12.12 | 10 |
| ADR — kho GitHub `joelparkerhenderson/architecture-decision-record` và bài gốc của Michael Nygard | — | C12.12 | 10 |
| Design doc và RFC công khai (Rust RFC, Kubernetes KEP, IETF) | — | C12.12 — đọc ≥15 cái | 25 |
| *The Site Reliability Workbook* — chương về thiết kế | Google | C12.2, C12.5 | 15 |
| *Building Secure and Reliable Systems* — miễn phí | Google | C12.14 | 25 |
| Tài liệu về FMEA (chuẩn IEC 60812 hoặc hướng dẫn công khai) | IEC / — | C12.5 | 15 |

---

## 5.2 — SUPPORTING · 8 NHÁNH

Phân rã tới tầng leaf, mỗi leaf có mức + lý do cần + checkpoint nhóm.

---

# ◇ S1 · MATHEMATICS FOR SYSTEMS & LEARNING — ~320 h

**Nguyên tắc vận hành:** khi gặp một khái niệm toán chặn đường, học **đúng phần chặn** trong ≤2 buổi rồi quay lại engineering. Dồn phần có hệ thống vào ba đợt tập trung: đầu Phase 1 (nền), đầu Phase 2 (thống kê), đầu Phase 3 (tối ưu + số học).

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S1.1 Discrete math & logic** | Wo | Tập hợp, quan hệ, hàm · logic mệnh đề và vị từ · chứng minh: trực tiếp, phản chứng, quy nạp · tổ hợp và đếm · quan hệ đệ quy · lý thuyết đồ thị cơ bản · bất biến (invariant) như công cụ chứng minh | Là ngôn ngữ để lập luận về tính đúng của thuật toán và của giao thức |
| **S1.2 Linear algebra** | In | Vector, không gian vector, cơ sở · nhân ma trận và ý nghĩa hình học · hạng, hạt nhân, không gian con · định thức và nghịch đảo · trị riêng, vector riêng · SVD và ý nghĩa · phân rã ma trận · chuẩn (norm) và khoảng cách · phép chiếu và bình phương tối thiểu | Dependency toán **chặn** duy nhất của ML; cũng là nền của ước lượng trạng thái và xử lý tín hiệu |
| **S1.3 Probability & statistics** | **In** | Không gian xác suất, biến ngẫu nhiên · phân phối rời rạc và liên tục · kỳ vọng, phương sai, hiệp phương sai · xác suất có điều kiện, Bayes · độc lập và tương quan (và khác biệt) · luật số lớn, định lý giới hạn trung tâm · ước lượng điểm và khoảng · kiểm định giả thuyết và p-value (và cách hiểu sai nó) · lỗi loại I/II và công suất · vấn đề nhiều so sánh · bootstrap và hoán vị · thống kê Bayes ở mức khái niệm | Uncertainty là bản chất của hệ "thông minh"; cũng là nền của mọi đánh giá model và mọi tuyên bố về hiệu năng |
| **S1.4 Calculus** | Wo | Đạo hàm và ý nghĩa · quy tắc chuỗi (nền của backprop) · gradient, Jacobian, Hessian · cực trị và điểm yên ngựa · khai triển Taylor · tích phân ở mức đủ hiểu kỳ vọng liên tục | Đủ cho backprop và optimization. Không cần calculus nâng cao |
| **S1.5 Optimization** | Wo | Hàm lồi và tập lồi · gradient descent và biến thể · tốc độ hội tụ · điều kiện dừng · tối ưu có ràng buộc và nhân tử Lagrange · KKT ở mức khái niệm · tối ưu rời rạc và độ khó · tối ưu đa mục tiêu và mặt Pareto | Hiểu vì sao training hội tụ hay không; và mặt Pareto là công cụ trình bày đánh đổi ở C12.2 |
| **S1.6 Numerical methods & floating-point** | Wo | Biểu diễn số thực và sai số làm tròn · số điều kiện (condition number) · ổn định số vs điều kiện tốt · catastrophic cancellation · tổng có bù (Kahan summation) · giải hệ tuyến tính: LU, QR, và vì sao không nghịch đảo ma trận · phương pháp lặp · tính không tất định trong tính toán song song | Quantization, ổn định số, và nguồn của lỗi "âm thầm" trong ML ở edge |
| **S1.7 Information theory** | Ba | Entropy và ý nghĩa · entropy có điều kiện, thông tin tương hỗ · KL divergence và cross-entropy · nguồn và mã hóa, định lý mã hóa nguồn · dung lượng kênh và định lý Shannon · rate–distortion ở mức khái niệm · ứng dụng: nén, lựa chọn đặc trưng, loss function | Nối liền nén dữ liệu, truyền tin và cross-entropy loss — ba thứ trông rời nhau nhưng cùng một gốc |
| **S1.8 Queueing theory** | Ba | Định luật Little · ký hiệu Kendall · M/M/1: độ dài hàng đợi và thời gian chờ · M/M/c và nhiều server · tác động của biến thiên · mạng hàng đợi ở mức khái niệm · ứng dụng vào capacity planning | Trả lời "cần bao nhiêu máy" bằng mô hình thay vì cảm giác; nền của C11.5 |
| **S1.9 Fourier & biến đổi** | Wo | Chuỗi Fourier và biến đổi Fourier · DFT và FFT · tính chất: tuyến tính, dịch, tích chập ↔ nhân · định lý Parseval · biến đổi Laplace và Z ở mức đủ cho control · wavelet ở mức awareness | Bắt buộc cho toàn bộ C7; không có thì DSP là công thức thuộc lòng |

**Checkpoint tổng S1:** (a) suy ra được backprop cho một MLP từ quy tắc chuỗi, không tra cứu; (b) tính được capacity cần thiết cho một SLO độ trễ bằng định luật Little; (c) giải thích được vì sao `float32` mất chính xác ở một phép tính cụ thể trong code của bạn và sửa được.

**Tài nguyên:** *Mathematics for Computer Science* (MIT 6.042, miễn phí) · 18.06 *Linear Algebra* của Strang (MIT OCW) · *Essence of Linear Algebra* và *Essence of Calculus* (3Blue1Brown) · 6.041 *Probabilistic Systems Analysis* (MIT OCW) · *Introduction to Probability* (Blitzstein, Harvard, miễn phí) · *Mathematics for Machine Learning* (Deisenroth, Faisal, Ong — miễn phí) · *Numerical Linear Algebra* (Trefethen & Bau) · *Elements of Information Theory* (Cover & Thomas — tra cứu) · StatQuest cho trực giác khi kẹt.

---

# ◇ S2 · ELECTRONICS & POWER — ~140 h

*(Nhánh này ở bản v1 là supporting mức Working; nâng lên sau khi xác nhận phần cứng.)*

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S2.1 Nền mạch** | Wo→In | Định luật Ohm, Kirchhoff · phân áp, phân dòng · tụ điện, cuộn cảm, hằng số thời gian RC · diode, transistor như khóa, MOSFET · trở kháng đầu vào/ra và phối hợp · mạch tương đương Thévenin | Đọc được schematic; không có thì mọi việc đấu nối là bắt chước |
| **S2.2 Đọc datasheet & chọn linh kiện** | **In** | Cấu trúc datasheet · bảng đặc tính tuyệt đối vs điều kiện hoạt động · điều kiện đo của mỗi thông số · đồ thị đặc tính và cách đọc · so sánh linh kiện theo tiêu chí thật · package và khả năng hàn tay · trạng thái vòng đời (EOL) và nguồn cung | Chọn sai linh kiện là hỏng cả dự án, và phát hiện rất muộn |
| **S2.3 Nguồn** | Wo→In | Regulator tuyến tính (LDO): dropout, tản nhiệt, hiệu suất · chuyển mạch (buck, boost): hiệu suất, nhiễu, layout · tụ decoupling: giá trị, vị trí, vì sao · khởi động và thứ tự cấp nguồn · dòng khởi động (inrush) · sụt áp và brownout · giám sát nguồn và reset | **Nguyên nhân số 1 của bug "ngẫu nhiên" trong embedded** |
| **S2.4 Pin & ngân sách năng lượng** | Wo→In | Hóa học pin: Li-ion, LiPo, LiFePO4, kiềm, CR2032 · dung lượng danh nghĩa vs dung lượng thực ở dòng cao · đường cong phóng điện và điện áp cắt · ảnh hưởng nhiệt độ · dòng rò và tự phóng · sạc và mạch bảo vệ · tính ngân sách năng lượng từ profile dòng · đo dòng ở mức µA | Quyết định kiến trúc duty-cycle của cả hệ; nối trực tiếp C6.9 |
| **S2.5 Tính toàn vẹn tín hiệu cơ bản** | Ba→Wo | Nối đất và mặt phẳng đất · vòng lặp đất · nhiễu xuyên âm (crosstalk) · phản xạ và kết thúc đường truyền ở mức khái niệm · độ dài dây và tần số · che chắn và ferrite · cách ly | Đủ để không tự tạo ra bug cho chính mình |
| **S2.6 Đo đạc** | **In** | Đồng hồ vạn năng: đo đúng, giới hạn, an toàn · logic analyzer: kích hoạt, giải mã giao thức, timing · oscilloscope: băng thông, tốc độ lấy mẫu, đầu dò, nối đất đầu dò · đo dòng: shunt, kẹp, INA219/INA226 · máy phân tích năng lượng cho thiết bị ngủ sâu · đo nhiệt: cặp nhiệt, camera hồng ngoại (nếu có) | **Không đo được thì không debug được phần cứng** — chỉ đoán |
| **S2.7 Prototyping** | Wo | Breadboard và giới hạn của nó (điện dung ký sinh) · perfboard và hàn · hàn SMD cơ bản · connector và độ tin cậy cơ khí · dây và tiết diện · in 3D vỏ cơ bản · lắp đặt cho thử nghiệm dài hạn | Thực thi; thiết bị chạy 30 ngày cần lắp đặt tốt hơn breadboard |
| **S2.8 Nhiệt** | Ba→Wo | Trở kháng nhiệt và tính nhiệt độ mối nối · tản nhiệt và đối lưu · giới hạn nhiệt của linh kiện · throttling và tuổi thọ · nhiệt trong vỏ kín · đo nhiệt độ trong hoạt động thật | Giới hạn thật của compute ở edge; nối C3.13 |

**Checkpoint tổng S2:** (a) đọc một datasheet lạ và đấu nối đúng ngay lần đầu, không cháy gì; (b) debug một bug do nguồn (sụt áp, thiếu decoupling, hoặc dòng khởi động) bằng oscilloscope, với ảnh chụp waveform trước/sau; (c) đo dòng ngủ của một thiết bị ở mức µA và khớp với tính toán ngân sách năng lượng.

**Tài nguyên:** *The Art of Electronics* (Horowitz & Hill — tra cứu, chương 1, 8, 9) · *Practical Electronics for Inventors* · Application note của Texas Instruments và Analog Devices về nguồn, nhiễu, nối đất (**chất lượng rất cao, miễn phí**) · EEVblog — video về đo đạc và debug · Datasheet và AN của linh kiện bạn dùng.

---

# ◇ S3 · CONTROL THEORY & FEEDBACK — ~90 h

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S3.1 Khái niệm feedback** | Wo | Vòng hở vs vòng kín · tín hiệu tham chiếu, sai số, tín hiệu điều khiển · nhiễu và nhiễu đo · độ nhạy và độ bền · feedback như khung tư duy cho cả hệ (autoscaling, rate limiting, retraining cũng là vòng feedback) | Là khung tư duy cho cả hệ thống, không chỉ cho động cơ |
| **S3.2 PID** | Wo→In | Vai trò P, I, D · điều chỉnh: Ziegler-Nichols, thủ công, tự động · chống windup tích phân · lọc thành phần D · dạng song song vs dạng chuẩn · bump-less transfer khi chuyển chế độ · tần số lấy mẫu vòng điều khiển · giới hạn tốc độ thay đổi | Bộ điều khiển bạn sẽ thực sự dùng trong 95% trường hợp |
| **S3.3 Ổn định** | Ba | Cực và không · biên độ lợi và biên pha (trực giác) · đáp ứng bước: overshoot, thời gian lên, thời gian ổn định · đáp ứng tần số và biểu đồ Bode ở mức đọc được · trễ vận chuyển (dead time) và tác động phá ổn định | Biết khi nào hệ sắp dao động, và vì sao |
| **S3.4 State-space & observer** | Ba | Biểu diễn không gian trạng thái · điều khiển được và quan sát được · phản hồi trạng thái · observer và Kalman như một observer (nối C7.8) · LQR ở mức khái niệm | Nối control với sensor fusion; giải thích vì sao Kalman hoạt động |
| **S3.5 Điều khiển rời rạc** | Ba | Lấy mẫu và giữ mẫu (ZOH) · ảnh hưởng của tần số lấy mẫu tới ổn định · rời rạc hóa bộ điều khiển liên tục · quy tắc ngón tay cái cho tần số vòng điều khiển · jitter trong vòng điều khiển và tác động | Lý do phần lớn bộ điều khiển số hoạt động kém hơn kỳ vọng |
| **S3.6 An toàn trong điều khiển** | **In** | Giới hạn mềm và giới hạn cứng · watchdog nhiều tầng · trạng thái an toàn (fail-safe) và định nghĩa nó · phát hiện dao động và thoát · khóa liên động phần cứng độc lập với phần mềm · giới hạn tốc độ thay đổi như biện pháp an toàn · ghi log vòng điều khiển để phân tích sau sự cố | **Bắt buộc** khi phần mềm điều khiển vật thể có thể gây hại |
| **S3.7 Control vs learned policy** | **In** | Khi nào bộ điều khiển cổ điển tốt hơn ML: hệ có mô hình, cần đảm bảo, cần giải thích · khi nào ML thắng: mô hình không biết, không gian trạng thái lớn · hệ lai: ML sinh tham chiếu, control theo dõi · learned policy và vấn đề đảm bảo an toàn · shield/safety layer bao quanh learned policy | **Phán đoán phân biệt bạn với người chỉ biết ML** |


**Bổ sung ở v3 — S3.8 · Điều khiển quá trình công nghiệp — `Wo→In`**

*Lỗ hổng độ phủ của v2: S3 mô tả control theory ở dạng học thuật (PID, ổn định, state-space) nhưng thiếu hình thái nó thực sự xuất hiện trong nhà máy.*

| Sub-leaf | Nội dung |
|---|---|
| Cấu trúc điều khiển | Vòng đơn · cascade (vòng trong nhanh, vòng ngoài chậm) · tỷ lệ (ratio) · split-range · override/chọn lựa |
| Feedforward trong quá trình | Bù nhiễu đo được trước khi nó ảnh hưởng — thường hiệu quả hơn tinh chỉnh PID |
| Nhận dạng đối tượng | Đáp ứng bước, mô hình bậc nhất có trễ (FOPDT), và vì sao trễ vận chuyển phá ổn định |
| Điều khiển bề mặt và chống dao động | Tương tác giữa các vòng, decoupling, và dao động lan truyền trong nhà máy |
| MPC ở mức khái niệm | Khi nào điều khiển dự báo đáng chi phí, và vì sao nó là cầu nối tự nhiên sang ML |
| Điều khiển cấp nhà máy | Setpoint từ tầng trên, tối ưu hóa thời gian thực, và ranh giới với tầng MES |
| Bump-less transfer và chuyển chế độ | Tự động ↔ tay ↔ tầng, và vì sao chuyển chế độ là nơi tai nạn xảy ra |
| Vòng điều khiển trong hệ điện | Điều khiển công suất tác dụng/phản kháng, đáp ứng tần số, tuân thủ grid code — vòng kín có ràng buộc pháp lý |

**Checkpoint:** thiết kế và điều chỉnh một vòng cascade trên hệ vật lý thật (hoặc mô phỏng đã hiệu chuẩn theo đối tượng thật), chứng minh nó tốt hơn vòng đơn bằng đồ thị đáp ứng nhiễu; và nêu được ≥2 tình huống cascade **làm tệ hơn**.


**Checkpoint tổng S3:** (a) điều chỉnh PID trên hệ vật lý thật đạt chỉ tiêu overshoot và thời gian ổn định, có đồ thị đáp ứng bước trước/sau; (b) thiết kế và chứng minh trạng thái fail-safe cho hệ đó dưới 3 loại lỗi; (c) cho một bài toán điều khiển cụ thể, lập luận có nên dùng ML hay không, bằng tiêu chí.

**Tài nguyên:** *Feedback Systems: An Introduction for Scientists and Engineers* (Åström & Murray — **miễn phí**, Caltech) · *PID Controllers: Theory, Design and Tuning* (Åström & Hägglund) · Brian Douglas — video về control theory (trực giác rất tốt) · MATLAB/Octave hoặc Python-control để mô phỏng.

---

# ◇ S4 · SECURITY ENGINEERING — ~110 h

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S4.1 Threat modeling** | In | STRIDE và cách áp dụng · ranh giới tin cậy và sơ đồ luồng dữ liệu · tài sản, tác nhân đe dọa, năng lực của họ · cây tấn công · xếp hạng rủi ro · threat model cho hệ vật lý (kẻ tấn công cầm được thiết bị) · threat model cho hệ ML | Bảo mật là hoạt động **thiết kế**, không phải bước kiểm tra cuối |
| **S4.2 Identity & xác thực** | In | Xác thực vs ủy quyền · OAuth2 và OIDC: các luồng và khi nào dùng cái nào · JWT: cấu trúc, xác minh, và các lỗi phổ biến · mTLS cho giao tiếp máy-máy · định danh thiết bị và chứng chỉ thiết bị · xoay vòng thông tin xác thực · định danh workload trên cloud (không dùng khóa dài hạn) · phiên và thu hồi | Mọi hệ đa thiết bị, đa dịch vụ |
| **S4.3 Quản lý bí mật** | In | Vòng đời khóa: tạo, phân phối, sử dụng, xoay vòng, thu hồi, hủy · nơi **không** để bí mật: mã nguồn, biến môi trường trong log, image · kho bí mật và truy cập theo workload · mã hóa phong bì (envelope encryption) và KMS · bí mật trên thiết bị nhúng: OTP, secure element · phát hiện bí mật bị lộ và quy trình xử lý | Nơi rò rỉ xảy ra nhiều nhất trong thực tế |
| **S4.4 Crypto như hộp đen** | Wo | Hàm băm và tính chất · mã hóa đối xứng: AES-GCM, ChaCha20-Poly1305 · mã hóa bất đối xứng và trao đổi khóa · chữ ký số · MAC và xác thực thông điệp · dẫn xuất khóa: PBKDF2, Argon2, HKDF · số ngẫu nhiên và entropy trên thiết bị nhúng · **không bao giờ tự cài** — chỉ dùng đúng | Dùng đúng; tự cài là phản mẫu về an toàn |
| **S4.5 Secure boot & firmware** | Wo→In | Chuỗi tin cậy từ ROM · ký firmware và xác minh · chống rollback · bảo vệ đọc ngược và vô hiệu hóa debug · mã hóa flash · cập nhật có xác thực (nối C6.10) · mô hình mối đe dọa khi kẻ tấn công có thiết bị trong tay | Thiết bị ngoài tầm kiểm soát vật lý |
| **S4.6 Bảo mật chuỗi cung ứng** | Wo | SBOM và vì sao nó quan trọng · khóa phiên bản dependency và xác minh hash · tấn công qua dependency và typosquatting · provenance của build và reproducible build · ký artifact · quét lỗ hổng và ưu tiên theo khả năng khai thác thật · dependency của model và dataset | Bề mặt tấn công lớn nhất của dự án hiện đại |
| **S4.7 Bảo mật đặc thù ML** | **In** | Prompt injection: trực tiếp và gián tiếp qua dữ liệu · ranh giới tool-use và quyền của agent · trích xuất model và trích xuất dữ liệu huấn luyện · ngộ độc dữ liệu và backdoor · ví dụ đối kháng · tấn công suy luận thành viên (membership inference) · rò rỉ qua output của model · phòng thủ: cách ly, xác thực output, quyền tối thiểu cho tool, human-in-the-loop cho hành động rủi ro | Lớp lỗ hổng mới mà kinh nghiệm bảo mật truyền thống không bao |
| **S4.8 Quyền riêng tư** | Wo | Tối thiểu hóa dữ liệu như quyết định kiến trúc · giới hạn của ẩn danh hóa và tái định danh · giả danh hóa (pseudonymization) · xử lý tại chỗ để tránh truyền · quyền riêng tư vi phân ở mức khái niệm · federated learning ở mức khái niệm · lưu giữ và xóa (nối A5) · riêng tư trong log và trace | Quyết định kiến trúc, không chỉ chính sách |


**Bổ sung ở v3 — S4.9 · An ninh OT / hệ thống điều khiển công nghiệp — `Wo→In`**

*Lỗ hổng độ phủ của v2: S4 bao bảo mật IT và bảo mật ML nhưng không bao bảo mật OT, vốn có mô hình mối đe dọa và thứ tự ưu tiên khác hẳn.*

| Sub-leaf | Nội dung |
|---|---|
| Đảo ngược thứ tự ưu tiên | IT ưu tiên bí mật → toàn vẹn → sẵn sàng. **OT đảo ngược: an toàn → sẵn sàng → toàn vẹn → bí mật.** Hiểu sai điều này là nguồn của mọi xung đột IT/OT |
| **IEC 62443** | Khái niệm zone và conduit · security level SL 1–4 · phân vai nhà sản xuất / nhà tích hợp / chủ sở hữu |
| Mô hình Purdue cho phân tách mạng | Tầng 0–5, DMZ công nghiệp, và vì sao "air gap" gần như không còn tồn tại thật |
| Truy cập từ xa vào hệ điều khiển | Jump host, ghi phiên, và rủi ro của kết nối nhà cung cấp |
| Bản vá trong môi trường không dừng được | Cửa sổ bảo trì, bù đắp bằng biện pháp bù trừ, và vì sao "cứ vá đi" là lời khuyên vô dụng ở đây |
| Mối đe dọa đặc thù | Thao túng logic điều khiển, giả mạo giá trị đo, tấn công vào hệ an toàn, ransomware làm dừng sản xuất |
| An toàn vs an ninh | Hai từ khác nhau, hai bộ tiêu chuẩn khác nhau, và nơi chúng mâu thuẫn — biện pháp an ninh không được làm giảm an toàn |
| Giám sát an ninh OT | Phát hiện bất thường trên lưu lượng công nghiệp; vì sao nó dễ hơn IT (lưu lượng rất tất định) và khó hơn IT (không được can thiệp) |

**Checkpoint:** vẽ mô hình zone/conduit cho một hệ có cả tầng OT lẫn tầng cloud, xác định mọi conduit vượt ranh giới tin cậy, và với mỗi cái nêu biện pháp bảo vệ + **cái gì xảy ra với an toàn nếu biện pháp đó lỗi**.


**Checkpoint tổng S4:** (a) threat model cho toàn vòng `sense→act` của hệ bạn, tìm ≥3 vector chưa nghĩ tới; (b) dựng mTLS + provisioning + xoay vòng chứng chỉ cho một thiết bị, chứng minh hoạt động sau khi chứng chỉ cũ hết hạn; (c) chứng minh một agent có tool không thể thực hiện một hành động ngoài phạm vi được cấp, kể cả khi input cố tình dẫn dụ.

**Tài nguyên:** *Building Secure and Reliable Systems* (Google — **miễn phí**) · OWASP Top 10 và OWASP LLM Top 10 · *Security Engineering* (Ross Anderson — **miễn phí bản 3**) · *Cryptography Engineering* (Ferguson, Schneier, Kohno) · NIST SP 800 series cho khuyến nghị cụ thể · Tài liệu về Microsoft Threat Modeling Tool / STRIDE.

---

# ◇ S5 · TESTING & VERIFICATION CHO HỆ PHI TẤT ĐỊNH — ~90 h

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S5.1 Nền testing** | In | Kim tự tháp test và các biến thể · test đơn vị: phạm vi, tốc độ, cách ly · test tích hợp: cái gì thật, cái gì giả · test đầu-cuối và chi phí bảo trì · test double: stub, mock, fake, spy — và khi nào dùng cái nào · độ phủ: dòng, nhánh, và vì sao 100% không phải mục tiêu · test dễ vỡ (flaky) và cách xử lý · tốc độ suite test như một ràng buộc thiết kế | Nền |
| **S5.2 Property-based testing** | Wo | Tính chất vs ví dụ · sinh dữ liệu và thu nhỏ (shrinking) · tính chất hữu ích: round-trip, invariant, oracle, metamorphic · stateful property testing · Hypothesis (Python), và tương đương ở ngôn ngữ khác | Tìm được lớp bug mà test theo ví dụ không tìm ra |
| **S5.3 Test cho firmware & phần cứng** | Wo→In | Test logic firmware trên host (nối C6.12) · giả lập HAL · hardware-in-the-loop: kiến trúc và chi phí · test tự động trên board thật trong CI · test dài hạn (soak test) và phát hiện rò rỉ · test môi trường: nhiệt độ, điện áp, nhiễu · test sau khi lắp ráp | Cách duy nhất test hệ vật lý ở quy mô và tần suất |
| **S5.4 Contract testing** | Wo | Contract giữa producer và consumer · consumer-driven contract · kiểm thử tương thích schema (nối C9.12) · contract cho giao thức thiết bị · chạy contract test trong CI của cả hai phía | Bảo vệ ranh giới tích hợp — nơi hệ end-to-end hỏng nhiều nhất |
| **S5.5 Test hệ phi tất định** | **In** | Vì sao pass/fail không áp dụng · assertion thống kê và dung sai · golden set và bảo trì nó · so sánh phân phối thay vì so sánh giá trị · seed và kiểm soát ngẫu nhiên · test với nhiều seed và báo cáo phân phối · phân biệt regression thật với nhiễu · test cho hệ có timeout và concurrency | Hệ có ML không pass/fail nhị phân được |
| **S5.6 Evaluation như testing** | **In** | Eval harness như hạ tầng CI (nối C8.13) · bộ test hồi quy cho hành vi model · eval theo lát cắt trong CI · ngưỡng chấp nhận và cổng triển khai · chi phí eval và tần suất chạy · eval cho hệ agentic: đúng kết quả vs đúng quá trình · theo dõi eval theo thời gian | Ngăn model mới tệ hơn model cũ ở nhóm người dùng cụ thể |
| **S5.7 Fuzzing & sanitizer** | Wo | Fuzzing có hướng dẫn độ phủ (AFL, libFuzzer) · fuzzing giao thức và parser · corpus và tối thiểu hóa · sanitizer trong CI · fuzzing firmware qua emulation · OSS-Fuzz ở mức awareness | Rẻ và hiệu quả bất thường với code C và với parser |
| **S5.8 Formal methods** | **Aw** | Model checking và TLA+ ở mức khái niệm · khi nào đáng dùng: giao thức phân tán, logic đồng thời quan trọng · kiểm chứng bằng proof assistant — biết tồn tại, biết chi phí · phân tích tĩnh như dạng nhẹ của formal method | Biết khi nào bạn đã bước sang lãnh địa cần chuyên gia |

**Checkpoint tổng S5:** (a) eval harness bắt được một regression thật mà unit test bỏ lọt; (b) ≥60% logic firmware chạy dưới test trên host trong CI; (c) property-based test tìm ra ≥1 bug thật trong code của bạn.

**Tài nguyên:** *Test-Driven Development for Embedded C* (Grenning) · Hypothesis documentation · *Software Testing* — tài liệu của Google (Testing Blog, và sách *Software Engineering at Google* chương test, miễn phí online) · Pact documentation cho contract testing · Tài liệu TLA+ của Leslie Lamport (chỉ đọc phần giới thiệu).

---

# ◇ S6 · RELIABILITY & SAFETY ENGINEERING — ~60 h

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S6.1 Phân loại lỗi & chỉ số** | Wo | Fault → error → failure: ba khái niệm khác nhau · lỗi thoáng qua, không liên tục, vĩnh viễn · MTBF, MTTF, MTTR, availability — và cách chúng liên hệ · phân phối lỗi và đường cong bồn tắm · lỗi độc lập vs tương quan | Ngôn ngữ chung để nói về độ tin cậy bằng số |
| **S6.2 FMEA & fault tree** | Wo→In | FMEA: quy trình, severity/occurrence/detection, RPN · FMECA · fault tree analysis: cổng logic, sự kiện cơ bản, cắt tối thiểu · event tree analysis · HAZOP ở mức khái niệm · áp dụng cho hệ phần mềm + phần cứng + ML · duy trì phân tích khi hệ tiến hóa | Tìm lỗi **có hệ thống** thay vì bằng trí tưởng tượng |
| **S6.3 Dự phòng & kiến trúc chịu lỗi** | **In** | Dự phòng: nóng, ấm, lạnh · N+1, 2N, và chi phí · bỏ phiếu (voting) và bộ ba module · lỗi chế độ chung (common mode) phá dự phòng như thế nào · đa dạng hóa (diversity) trong thiết kế · fail-safe vs fail-operational vs fail-secure — chọn cái nào · suy giảm duyên dáng có thiết kế · phân vùng lỗi và ngăn chặn lan truyền | Quyết định kiến trúc cốt lõi của hệ có actuation |
| **S6.4 Phát hiện & giám sát sức khỏe** | **In** | Watchdog: phần cứng, cửa sổ, nhiều tầng · heartbeat và thời gian phát hiện · health check nông vs sâu · tự kiểm tra khi khởi động (POST) · giám sát tính hợp lý (plausibility check) của dữ liệu · phát hiện "chết mà không báo" · thời gian phát hiện như một chỉ số thiết kế | Cơ chế phát hiện quyết định thời gian bạn chạy trong trạng thái sai |
| **S6.5 Mức an toàn & chứng nhận** | Aw | SIL (IEC 61508), ASIL (ISO 26262), DAL (DO-178C) — biết tồn tại và ý nghĩa · quy trình phát triển theo chuẩn và chi phí của nó · phân tích rủi ro và phân bổ mức an toàn · vì sao ML khó chứng nhận · khi nào bạn cần chuyên gia | Biết khi nào bạn đã bước qua ranh giới cần chuyên môn khác |
| **S6.6 Human-in-the-loop như cơ chế tin cậy** | Wo | Khi nào chèn người: rủi ro cao, không thể đảo ngược, độ tin cậy thấp · thiết kế điểm dừng và phê duyệt · trình bày thông tin để người quyết định đúng (nối A3) · tự động hóa với giám sát vs tự động hóa hoàn toàn · chi phí của người và cách giữ nó hợp lý · degradation sang chế độ thủ công | Cách rẻ nhất để chặn lỗi thảm họa của hệ tự động |

**Checkpoint tổng S6:** (a) FMEA đầy đủ cho hệ của bạn với ≥30 mục, tìm ≥3 chế độ hỏng mới; (b) thiết kế và chứng minh trạng thái fail-safe dưới ≥3 loại lỗi khác nhau; (c) đo thời gian phát hiện cho mỗi cơ chế giám sát và chứng minh nó dưới ngưỡng bạn đặt ra.

**Tài nguyên:** *Engineering a Safer World* (Leveson — tiếp cận STAMP, khác biệt và đáng đọc) · IEC 60812 (FMEA) và tài liệu hướng dẫn công khai · NASA Fault Tree Handbook (**miễn phí**) · *Normal Accidents* (Perrow — cho trực giác về lỗi hệ thống phức tạp) · Báo cáo điều tra tai nạn công khai (NTSB, hàng không) — nguồn học tập chất lượng cao.

---

# ◇ S7 · QUEUEING, CAPACITY & ENGINEERING ECONOMICS — ~50 h

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S7.1 Định luật Little & utilization** | Wo | L = λW và cách dùng thực tế · đường cong utilization–latency · vì sao 80% đã nguy hiểm · biến thiên làm đường cong tệ hơn · áp dụng cho thread pool, hàng đợi, GPU | Trực giác định lượng thay cho cảm tính |
| **S7.2 Mô hình capacity** | Wo | Đơn vị công việc và tỷ lệ đến · headroom và đệm cho tăng trưởng · capacity theo tài nguyên: CPU, bộ nhớ, băng thông, IOPS, VRAM · capacity cho workload inference: KV cache là ràng buộc chính · dự báo theo tăng trưởng · điểm gãy và kế hoạch mở rộng | Trả lời "chịu được bao nhiêu" bằng số |
| **S7.3 Mô hình chi phí** | **In** | Chi phí mỗi request, mỗi inference, mỗi thiết bị, mỗi tháng · chi phí cố định vs biến đổi · chi phí biên và điểm hòa vốn · chi phí ẩn: truyền dữ liệu, lưu trữ, quan sát, on-call · chi phí kỹ sư so với chi phí hạ tầng — thường lớn hơn · mô hình hóa trên bảng tính và phân tích độ nhạy | **Ngôn ngữ mà thiết kế của bạn được duyệt hay bị bác** |
| **S7.4 Build vs buy & TCO** | Wo | Tổng chi phí sở hữu qua 3 năm · chi phí học và chi phí vận hành · bus factor và rủi ro nhân sự · chi phí thoát (nối C12.10) · quyết định có thể đảo ngược vs không đảo ngược | Quyết định lặp lại suốt sự nghiệp |
| **S7.5 Unit economics của ML** | Wo | Chi phí training: một lần vs lặp lại · chi phí inference: theo request, và tăng tuyến tính với tải · điểm hòa vốn tự host vs API · chi phí dữ liệu: thu thập, gán nhãn, lưu trữ · chi phí đánh giá và giám sát · cascade model để giảm chi phí trung bình | Hai đường cong chi phí hoàn toàn khác nhau; nhầm chúng dẫn tới quyết định sai |
| **S7.6 Vendor lock-in & chi phí thoát** | Wo | Lock-in ở tầng nào: API, dữ liệu, vận hành, kỹ năng · đo chi phí thoát bằng người-tháng · chiến lược giảm: trừu tượng hóa, định dạng mở, đa nhà cung cấp · chi phí của việc giảm lock-in (nó không miễn phí) · rủi ro thay đổi giấy phép và thay đổi giá | Quyết định hôm nay, trả giá 3 năm sau |

**Checkpoint tổng S7:** (a) bảo vệ một lựa chọn kiến trúc bằng bảng chi phí + độ trễ trước ba câu hỏi phản biện; (b) dự đoán độ trễ khi utilization tăng và đo xác nhận; (c) tính điểm hòa vốn tự host vs API cho workload inference của bạn.

**Tài nguyên:** *The Art of Capacity Planning* (Allspaw) · *Quantitative System Performance* (Lazowska et al. — **miễn phí**) · *Systems Performance* (Gregg) chương về mô hình hóa · Bảng giá công khai của các nhà cung cấp cloud — dùng để tự dựng mô hình chi phí · FinOps Foundation — tài liệu công khai.

---

# ◇ S8 · TECHNICAL COMMUNICATION & DESIGN DOCUMENTATION — ~40 h

| Leaf | Mức | Sub-leaves | Vì sao cần |
|---|---|---|---|
| **S8.1 Design doc / RFC** | **In** | Cấu trúc: bối cảnh, vấn đề, ràng buộc, phương án, quyết định, rủi ro, kế hoạch · viết cho người đọc, không cho người viết · độ dài phù hợp với mức rủi ro của quyết định · nêu phương án bị loại và lý do · nêu rõ cái bạn không biết · vòng đời: nháp → review → chốt → cập nhật | **Viết không ra nghĩa là chưa thiết kế xong** |
| **S8.2 ADR** | **In** | Cấu trúc tối thiểu: bối cảnh, quyết định, trạng thái, hệ quả · một quyết định một ADR · ADR là bất biến, thay bằng ADR mới (superseded) · lưu cùng code · khi nào một quyết định xứng đáng một ADR | Lưu **lý do** — thứ mất nhanh nhất trong mọi dự án |
| **S8.3 Sơ đồ** | In | Mô hình C4: bốn mức và khi nào dùng mức nào · sequence diagram cho luồng quan trọng · sơ đồ data flow và control flow riêng · sơ đồ triển khai · diagram-as-code (Mermaid, PlantUML, Structurizr) để giữ đồng bộ · một sơ đồ trả lời một câu hỏi | Công cụ **tư duy**, không phải công cụ trình bày |
| **S8.4 Postmortem** | Wo | Nguyên tắc blameless và vì sao nó hiệu quả · timeline chính xác · yếu tố góp phần (số nhiều) · action item kiểm chứng được · chia sẻ và học ở quy mô tổ chức · postmortem cho near-miss | Biến sự cố thành kiến thức hệ thống |
| **S8.5 Giải thích đánh đổi** | Wo | Trình bày cho người không kỹ thuật · dịch chỉ số kỹ thuật sang hệ quả nghiệp vụ · trình bày uncertainty một cách trung thực · cấu trúc kết luận-trước (BLUF) · biết dừng: đủ chi tiết để quyết định, không hơn | Điều kiện để thiết kế của bạn được chọn |
| **S8.6 Tài liệu vận hành** | Wo | Runbook cho tình huống lặp lại · playbook cho sự cố · README mà người mới chạy được trong 30 phút · tài liệu API · ghi chú kiến trúc cho người kế nhiệm | Thứ quyết định hệ của bạn có sống sót khi bạn rời đi |

**Checkpoint tổng S8:** (a) viết một design doc mà một kỹ sư lạ **thực thi được không cần hỏi lại** — kiểm chứng với người thật; (b) một ADR mà người đọc 6 tháng sau ra được cùng quyết định; (c) README cho một dự án của bạn mà người mới chạy được trong ≤30 phút.

**Tài nguyên:** *Google Technical Writing Courses* (**miễn phí**) · Bài viết gốc của Michael Nygard về ADR · Mô hình C4 — tài liệu của Simon Brown · RFC công khai (IETF, Rust RFC, Kubernetes KEP) — đọc ≥15 cái để thấy cấu trúc tốt · Postmortem công khai của Google, Cloudflare, GitHub · *The Elements of Style* và *Style: Lessons in Clarity and Grace* cho văn phong.

---

## 5.3 — ADJACENT · 6 NHÁNH

Mục tiêu của tầng này: **nhận ra khi một bài toán thực chất thuộc lĩnh vực đó**, và biết tìm ở đâu. Không sâu hơn.

---

# ○ A1 · ROBOTICS & AUTONOMY — ~80 h · `Ba→Wo`

*(Nâng từ adjacent thuần lên ranh giới adjacent–supporting sau khi xác nhận phần cứng.)*

| Leaf | Mức | Nội dung | Checkpoint |
|---|---|---|---|
| A1.1 Mô hình ROS 2 | Wo | Node, topic, service, action · DDS và QoS · tf2 và hệ tọa độ · launch và cấu hình · rosbag để ghi và phát lại | Dựng một hệ ROS 2 với ≥3 node giao tiếp qua topic, ghi rosbag và phát lại được |
| A1.2 Pipeline nhận thức | Ba | Cảm biến → tiền xử lý → phát hiện → theo dõi · hợp nhất đa cảm biến · hệ tọa độ và hiệu chuẩn ngoại (extrinsic) · độ trễ trong pipeline nhận thức | Vẽ được pipeline nhận thức đầy đủ với ngân sách độ trễ từng bước |
| A1.3 Định vị & SLAM | Ba | Odometry và trôi tích lũy · định vị bằng đặc trưng · SLAM: bài toán và các họ giải pháp · đóng vòng (loop closure) · bản đồ lưới chiếm dụng | Giải thích được vì sao odometry trôi và loop closure sửa được gì |
| A1.4 Lập kế hoạch chuyển động | Ba | Không gian cấu hình · lập kế hoạch đồ thị (A*, D*) · lập kế hoạch lấy mẫu (RRT, PRM) · làm mượt quỹ đạo · tránh vật cản động | Cài A* trên bản đồ lưới và giải thích khi nào nó không đủ |
| A1.5 Kiến trúc an toàn cho máy chuyển động | **Wo** | Dừng khẩn cấp và yêu cầu · vùng an toàn và giám sát tốc độ · kiến trúc hai kênh · tiêu chuẩn liên quan ở mức awareness · kiểm thử an toàn | Thiết kế kiến trúc an toàn cho một máy chuyển động, với lớp phần cứng độc lập với phần mềm |

**Tài nguyên:** ROS 2 documentation · *Probabilistic Robotics* (Thrun et al. — đọc chương 1–4) · *Modern Robotics* (Lynch & Park — **miễn phí**, chỉ chương cần) · Gazebo/Isaac Sim documentation.

---

# ○ A2 · SIMULATION & DIGITAL TWINS — ~60 h · `Ba→Wo`

| Leaf | Mức | Nội dung | Checkpoint |
|---|---|---|---|
| A2.1 Khái niệm mô phỏng | Ba | Mô phỏng sự kiện rời rạc vs liên tục · độ trung thực và chi phí của nó · bước thời gian và ổn định số · xác thực mô phỏng (validation) | Nêu được mức độ trung thực cần thiết cho một mục đích test cụ thể |
| A2.2 Hardware-in-the-loop | **Wo** | Kiến trúc HIL · giả lập cảm biến và actuator · timing thời gian thực trong HIL · tự động hóa test qua HIL | Dựng một HIL tối giản: firmware thật + cảm biến giả lập, chạy test tự động |
| A2.3 Dữ liệu tổng hợp | Ba | Sinh dữ liệu tổng hợp cho ML · domain randomization · khi nào dữ liệu tổng hợp giúp và khi nào nó hại · trộn dữ liệu thật và tổng hợp | Sinh dữ liệu tổng hợp cho một lớp hiếm và đo tác động lên eval set thật |
| A2.4 Khoảng cách sim-to-real | **Ba** | Nguồn của khoảng cách · đo khoảng cách · thu hẹp: hiệu chuẩn mô phỏng, randomization, tinh chỉnh trên dữ liệu thật · **giới hạn cơ bản: mô phỏng không chứa cái bạn không biết** | Đo được chênh lệch hiệu năng giữa mô phỏng và thực tế, và giải thích nguồn |
| A2.5 Digital twin | Ba | Định nghĩa thực dụng vs marketing · đồng bộ trạng thái giữa twin và vật thật · dùng twin để dự đoán và để chẩn đoán · chi phí duy trì twin | Nêu được khi nào digital twin xứng đáng chi phí và khi nào nó là phô trương |

**Tài nguyên:** Gazebo documentation · Renode (mô phỏng embedded) · QEMU cho mô phỏng MCU · Bài báo về domain randomization.

---

# ○ A3 · HCI & HUMAN FACTORS OF AUTOMATION — ~50 h · `Ba→Wo`

| Leaf | Mức | Nội dung | Checkpoint |
|---|---|---|---|
| A3.1 Mức độ tự chủ | Ba | Thang mức tự chủ · ai quyết định, ai thực hiện, ai giám sát · chuyển đổi giữa các mức · tự chủ thích ứng | Xếp hệ của bạn vào một mức tự chủ cụ thể và nêu hệ quả thiết kế |
| A3.2 Mode confusion & automation surprise | **Wo** | Chế độ ẩn và vì sao người dùng mất dấu · "nó đang làm gì vậy?" — triệu chứng kinh điển · thiên lệch tự động hóa (automation bias) · ra khỏi vòng lặp (out-of-the-loop) và mất kỹ năng · nghiên cứu tình huống từ hàng không | Với hệ của bạn, liệt kê mọi chế độ và kiểm tra người dùng luôn biết đang ở chế độ nào |
| A3.3 Trình bày uncertainty | Wo | Hiển thị độ tin cậy mà không gây hiểu lầm · hiệu chỉnh niềm tin của người dùng · khi nào che giấu uncertainty là đúng · trình bày cho quyết định, không để trang trí | Thiết kế cách hiển thị độ tin cậy của model và kiểm tra với người dùng thật |
| A3.4 Escalation & bàn giao | Wo | Khi nào chuyển cho người · bàn giao ngữ cảnh: người cần biết gì để quyết định · thời gian phản ứng của người và thiết kế quanh nó · mệt mỏi cảnh báo ở phía người · quy trình leo thang | Thiết kế một luồng escalation đầy đủ với ngữ cảnh bàn giao, và đo thời gian quyết định của người |
| A3.5 Thiết kế giao diện vận hành | Ba | Dashboard cho quyết định, không cho trưng bày · phân cấp thông tin · mù thay đổi và cách chống · thiết kế cho tình huống căng thẳng | Dashboard của bạn cho phép trả lời "hệ có khỏe không" trong ≤10 giây |

**Tài nguyên:** *The Design of Everyday Things* (Norman) · *Engineering a Safer World* (Leveson) — phần human factors · Bài viết của Lisanne Bainbridge *Ironies of Automation* (kinh điển, ngắn) · Báo cáo điều tra tai nạn hàng không liên quan tới tự động hóa.

---

# ○ A4 · BUSINESS & OPERATIONS ENGINEERING — ~40 h · `Ba→Wo`

| Leaf | Mức | Nội dung | Checkpoint |
|---|---|---|---|
| A4.1 Vẽ và phân tích quy trình | Ba | Sơ đồ quy trình và ký hiệu cơ bản · nút cổ chai và lý thuyết ràng buộc · thời gian chu kỳ và thời gian chờ · biến thiên trong quy trình | Vẽ quy trình hiện tại của một công việc thật và tìm nút cổ chai |
| A4.2 Cái gì nên tự động hóa | **Wo** | Tiêu chí: tần suất, độ ổn định, chi phí lỗi, khả năng đảo ngược · tự động hóa một phần vs toàn phần · chi phí bảo trì tự động hóa · khi tự động hóa làm hệ giòn hơn | Với 5 công việc cụ thể, quyết định tự động hóa hay không, có tiêu chí |
| A4.3 ROI & chi phí của lỗi | Wo | Tính ROI của một dự án kỹ thuật · chi phí của false positive vs false negative — thường rất bất đối xứng · đưa chi phí lỗi vào ngưỡng quyết định của model (nối C8.3) · giá trị của thời gian tiết kiệm | Tính chi phí thật của mỗi loại lỗi trong hệ của bạn và chỉnh ngưỡng theo đó |
| A4.4 Quản lý thay đổi | Aw | Vì sao hệ kỹ thuật đúng vẫn thất bại khi triển khai · người dùng và sự kháng cự · đào tạo và tài liệu · triển khai theo giai đoạn | Nêu được ≥3 lý do phi kỹ thuật khiến một hệ tốt thất bại |

**Tài nguyên:** *The Goal* (Goldratt — tiểu thuyết về lý thuyết ràng buộc) · *Accelerate* (Forsgren, Humble, Kim) · Tài liệu công khai về process mapping.

---

# ○ A5 · STANDARDS, COMPLIANCE & REGULATION — ~40 h · `Aw→Ba`

| Leaf | Mức | Nội dung | Checkpoint |
|---|---|---|---|
| A5.1 EU AI Act | **Ba** | Phân tầng rủi ro: không chấp nhận được, cao, hạn chế, tối thiểu · nghĩa vụ theo tầng · hệ thống AI mục đích chung · ảnh hưởng tới kiến trúc: tài liệu hóa, truy vết, giám sát của con người · phạm vi ngoài lãnh thổ | Xếp hệ của bạn vào một tầng rủi ro và liệt kê nghĩa vụ tương ứng |
| A5.2 Bảo vệ dữ liệu | **Ba** | GDPR: cơ sở pháp lý, quyền của chủ thể, chuyển dữ liệu xuyên biên giới · Nghị định bảo vệ dữ liệu cá nhân của Việt Nam · quyền được xóa và hệ quả kỹ thuật · lưu giữ và tối thiểu hóa · đánh giá tác động | Thiết kế quy trình xóa dữ liệu hoạt động xuyên mọi bản sao và cache |
| A5.3 Tiêu chuẩn thiết bị | Aw | CE, FCC — phạm vi và ý nghĩa · EMC: phát xạ và miễn nhiễm · an toàn điện · chứng nhận radio và vì sao dùng module đã chứng nhận là quyết định đúng · RoHS, WEEE ở mức awareness | Biết được thiết bị của bạn cần chứng nhận gì nếu thương mại hóa |
| A5.4 Functional safety | Aw | IEC 61508 và các chuẩn dẫn xuất theo ngành · vòng đời an toàn · vì sao ML khó chứng nhận · khi nào cần chuyên gia | Nhận ra khi dự án bước vào lãnh địa functional safety |
| A5.5 Tiêu chuẩn ngành cụ thể | Aw | Công nghiệp: OPC UA, Modbus · y tế: IEC 62304 ở mức tồn tại · ô tô: ISO 26262, AUTOSAR ở mức tồn tại · năng lượng: IEC 61850 ở mức tồn tại | Biết tra ở đâu khi bước vào một ngành mới |

**Tài nguyên:** Văn bản chính thức của EU AI Act và GDPR · Cổng thông tin pháp luật Việt Nam cho nghị định bảo vệ dữ liệu cá nhân · Hướng dẫn công khai của cơ quan quản lý · Tài liệu của nhà sản xuất module radio về chứng nhận.

---

# ○ A6 · LICENSING, IP & DATA RIGHTS — ~30 h · `Ba→Wo`

| Leaf | Mức | Nội dung | Checkpoint |
|---|---|---|---|
| A6.1 Giấy phép mã nguồn mở | **Wo** | Nhóm dễ dãi (MIT, BSD, Apache 2.0) · nhóm copyleft (GPL, LGPL, AGPL) và phạm vi lây lan · nghĩa vụ ghi công và cung cấp mã nguồn · tương thích giữa các giấy phép · giấy phép source-available (BSL) và vì sao nó không phải open source — **ví dụ: Terraform 2023, dẫn tới OpenTofu** · liên kết tĩnh vs động và hệ quả giấy phép | Kiểm tra toàn bộ dependency của một dự án và xác định nghĩa vụ giấy phép của bạn |
| A6.2 Giấy phép model & dataset | **Wo** | Giấy phép model không phải giấy phép phần mềm · giấy phép có hạn chế sử dụng (RAIL và tương tự) · giới hạn thương mại · điều khoản về output của model · dataset và nguồn gốc dữ liệu huấn luyện · giấy phép của trọng số vs của mã | Với mỗi model bạn dùng, xác định bạn được phép làm gì với output |
| A6.3 Quyền dữ liệu & provenance | Ba | Ai sở hữu dữ liệu cảm biến · dữ liệu khách hàng và quyền sử dụng để huấn luyện · theo dõi nguồn gốc dữ liệu · sự đồng ý và phạm vi của nó · dữ liệu thu thập từ web và rủi ro | Theo dõi được nguồn gốc của mọi dataset trong hệ của bạn |
| A6.4 IP trong công việc | Ba | Quyền sở hữu mã bạn viết ở nơi làm việc · đóng góp open source khi đang đi làm · sáng chế ở mức awareness · bí mật kinh doanh | Biết mình được phép công khai cái gì |

**Tài nguyên:** choosealicense.com · SPDX license list · Tài liệu của Open Source Initiative · Giấy phép cụ thể của model bạn dùng (đọc trực tiếp, không đọc tóm tắt).

---

## 5.4 — PERIPHERAL · 9 NHÁNH · `Awareness`

| Nhánh | Nó giải quyết gì | Vì sao bạn chưa cần | Kích hoạt xem lại khi |
|---|---|---|---|
| Compiler backend & codegen | Dịch IR sang mã máy tối ưu | Bạn cần hiểu *output* của compiler (đã có ở C3.4), không cần viết nó | Bạn làm toolchain cho một accelerator |
| VLSI / ASIC / FPGA RTL | Thiết kế mạch số tùy biến | Khoảng cách tới vòng ≥2 bước; FPGA chỉ đáng khi gặp ràng buộc latency cứng mà CPU/NPU không đạt | Bạn cần latency dưới micro giây tất định |
| RF & antenna design | Thiết kế đường truyền vô tuyến | Cần VNA và buồng đo; dùng module đã chứng nhận là quyết định kỹ thuật đúng | Bạn làm sản phẩm số lượng lớn cần tối ưu BOM |
| Mechanical design & CAD | Vỏ, kết cấu, cơ cấu | In 3D theo mẫu có sẵn đủ cho prototype | Bạn làm sản phẩm vật lý thương mại |
| Formal methods với proof assistant | Chứng minh tính đúng bằng máy | ROI cực thấp với hệ chứa thành phần phi tất định | Bạn làm giao thức đồng thuận hoặc hệ safety-critical |
| Supply chain & DFM | Sản xuất được ở số lượng | Chỉ quan trọng khi sản xuất thật; nhưng **EOL part** nên biết sớm (đã ở S2.2) | Bạn chuyển từ prototype sang sản xuất |
| Frontend framework ecosystem | Giao diện người dùng phong phú | Đủ để dựng dashboard là dừng; đừng vào cuộc đua framework | Bạn làm sản phẩm hướng người dùng cuối |
| Quantum computing | Tính toán trên nguyên lý lượng tử | Không nằm trên đường tới bất kỳ hệ thống nào bạn xây trong 5 năm | Không có mốc dự kiến |
| Blockchain / distributed ledger | Đồng thuận không tin cậy lẫn nhau | Phần hữu ích trùng với C10; phần còn lại lệch hướng | Bài toán của bạn thật sự có nhiều bên không tin nhau |

---

# 6. DEPTH MAP

| Nhánh | Mức mục tiêu | Giờ | Vì sao đúng mức đó | Checkpoint tổng |
|---|---|---|---|---|
| **C1** Programming & runtimes | **Ad→Ex** | 450 | Công cụ dùng mỗi ngày ở 11 nhánh khác; Expert ở đây tăng tốc mọi nhánh còn lại | Viết và bảo trì service C + Python có test, CI, profiling; tìm được bug concurrency; đọc source dự án lớn trong 6 h |
| **C2** DSA | **Ad** | 280 | Đủ để thiết kế; Expert (viết thư viện nền) là chi phí cơ hội so với C6/C8 | Giải bài lạ mức trung bình-khó trong 45 phút; phân tích amortized cấu trúc tự thiết kế; tăng tốc vòng lặp 2× bằng bố cục bộ nhớ |
| **C3** Computer architecture | **Ad** (Ex ở C3.6, C3.12) | 350 | Nơi mọi câu hỏi "vì sao chậm" kết thúc | Tăng tốc workload thật ≥3× dựa trên đo đạc; lượng tử hóa model và định vị lớp nhạy cảm nhất |
| **C4** OS & concurrency | **Ad** | 400 | Nơi trú ngụ của mọi bug khó nhất; Expert (kernel production) không khả thi và không cần | Tự viết event loop 10k kết nối + container tối giản; chẩn đoán deadlock từ dump |
| **C5** Networking | **Ad** (Ex ở C5.5) | 350 | Hệ end-to-end **là** hệ mạng; nhánh có khoảng cách lớn nhất giữa giá trị và mức đầu tư thông thường | Từ packet capture giải thích 3 loại sự cố thông lượng khác nhau; thiết bị offline 6h đồng bộ lại không mất không trùng |
| **C6** Embedded & firmware | **Ad→Ex** | 460 | Một đầu của "end-to-end"; vòng phản hồi chặt và phạm vi hữu hạn làm Expert khả thi | Thiết bị chạy ≥30 ngày ngoài thực địa có OTA chịu được mất điện giữa chừng; cấu hình peripheral lạ chỉ bằng datasheet |
| **C7** Sensing & signals | **Ad** | 260 | Đặt **trần** cho mọi tầng phía trên | Hiệu chuẩn chuỗi đo với số liệu sai số trước/sau; phát hiện bất thường thật từ phổ; căn chỉnh thời gian giữa 2 thiết bị |
| **C8** ML & inference systems | **Ad→Ex** ở serving/eval · **Ad** modeling · **Wo** training lớn | 560 | Giá trị nằm ở đưa model vào hệ thống, không ở tạo model mới | Deploy serving stack tăng throughput 2×; eval harness bắt regression thật; giảm 4× kích thước model dưới ngưỡng mất chính xác |
| **C9** Data engineering & storage | **Ad** | 320 | Pipeline hỏng âm thầm là chuẩn mực | 20 thiết bị offline 24h cùng trở lại: không mất, không trùng, tải không vượt 2×; 1 năm dữ liệu 100 thiết bị trong ngân sách |
| **C10** Distributed & cloud | **Ad** | 360 | Ngữ pháp của "end-to-end" | Hệ đạt SLO khi giết ngẫu nhiên 5 thành phần khác nhau; API idempotent chứng minh bằng test gửi trùng |
| **C11** Observability & performance | **Ad** | 260 | "Debug được" nằm trong định nghĩa mục tiêu | Giải thích hành vi hệ bằng dữ liệu quan sát, không bằng đọc code; chỉ ra 3 lỗi phương pháp trong một benchmark công khai |
| **C12** Systems architecture | **Ad→Ex** | 220 | Năng lực đích; là nhánh tổng hợp nên mỗi giờ ở nhánh khác đều đóng góp | FMEA tìm ≥3 chế độ hỏng mới; phân chia edge-cloud cho 5 chức năng có lập luận định lượng; ADR người lạ đọc 6 tháng sau ra cùng quyết định |
| **S1** Mathematics | Wo–**In** | 320 | Đủ để hiểu và debug; không đủ để chứng minh định lý mới — đúng mức cần | Suy ra backprop không tra cứu; tính capacity bằng Little's law; giải thích mất chính xác float32 trong code cụ thể |
| **S2** Electronics & power | Wo–**In** | 140 | Đủ để không bị chặn bởi phần cứng; không đủ để thiết kế mạch phức tạp | Đọc datasheet lạ và đấu đúng lần đầu; debug bug nguồn bằng scope; đo dòng ngủ µA khớp tính toán |
| **S3** Control theory | Wo (**In** ở an toàn) | 90 | Cần khi có actuation; sâu hơn là chi phí cơ hội | Tune PID đạt chỉ tiêu có đồ thị; chứng minh fail-safe dưới 3 loại lỗi |
| **S4** Security | Wo–**In** | 110 | Đủ để thiết kế đúng và biết khi nào cần chuyên gia | Threat model toàn vòng tìm ≥3 vector mới; mTLS + xoay vòng chứng chỉ hoạt động |
| **S5** Testing & verification | **In** (Aw ở formal) | 90 | Hệ phi tất định cần kỹ thuật khác; formal methods không đáng thời gian | Eval harness bắt regression unit test bỏ lọt; ≥60% logic firmware test trên host trong CI |
| **S6** Reliability & safety | Wo–**In** | 60 | Bắt buộc khi phần mềm điều khiển vật thể; không cần mức chứng nhận | FMEA ≥30 mục tìm ≥3 chế độ hỏng mới; đo thời gian phát hiện của mỗi cơ chế giám sát |
| **S7** Queueing & economics | **Wo** | 50 | Đủ để thiết kế được duyệt; sâu hơn thuộc chuyên gia capacity | Bảo vệ lựa chọn kiến trúc bằng bảng chi phí + độ trễ trước 3 phản biện |
| **S8** Technical communication | **In** | 40 | Công cụ tư duy; dưới mức này kiến trúc của bạn không tồn tại ngoài đầu bạn | Design doc mà kỹ sư lạ thực thi được không hỏi lại |
| **A1** Robotics | Ba–**Wo** | 80 | Case study tích hợp tốt nhất; chiều sâu thật là spine khác | Hệ ROS 2 ≥3 node; kiến trúc an toàn cho máy chuyển động |
| **A2** Simulation | Ba–**Wo** | 60 | Cách duy nhất test hệ vật lý ở quy mô | HIL tối giản chạy test tự động |
| **A3** Human factors | Ba–**Wo** | 50 | Failure mode đặc thù của hệ thông minh | Kiểm tra người dùng luôn biết hệ đang ở chế độ nào |
| **A4** Business & ops | Ba–**Wo** | 40 | "Nên tự động hóa cái gì" là quyết định kỹ thuật bị ràng buộc bởi quy trình | Tính chi phí thật của mỗi loại lỗi và chỉnh ngưỡng theo đó |
| **A5** Standards & regulation | **Aw–Ba** | 40 | Ảnh hưởng tới kiến trúc, không chỉ tới giấy tờ | Xếp hệ vào tầng rủi ro EU AI Act; quy trình xóa dữ liệu xuyên mọi bản sao |
| **A6** Licensing & IP | Ba–**Wo** | 30 | Quyết định bạn được phép ship cái gì | Kiểm tra toàn bộ dependency và xác định nghĩa vụ giấy phép |
| **Peripheral** (9 nhánh) | **Aw** | ~0 | Biết tồn tại, biết khi nào cần tìm tới | Nói được trong một câu: nó giải quyết gì và vì sao bạn chưa cần |

---

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

# 8. TECHNOLOGY LAYER

Sáu tầng, từ thứ không hết hạn tới thứ đang chết. **Quy tắc phân bổ: càng xuống dưới, càng ít giờ cho mỗi đơn vị.**

## Tầng 1 — Timeless principles *(không hết hạn)*

| Nguyên lý | Xuất hiện ở đâu trong roadmap |
|---|---|
| Phân tầng và trừu tượng hóa | C5.1, C6.12, C12.8 |
| Indirection ("mọi vấn đề giải được bằng một tầng gián tiếp nữa") | C1.5, C12.3 |
| Locality (thời gian và không gian) | C3.6, C2.11 |
| Caching và tính nhất quán của nó | C9.7, C3.6, C5.11 |
| Hàng đợi và backpressure | C4.7, C10.10, C11.5 |
| Feedback control | S3.1, C10.12, C8.14 |
| Dự phòng và cô lập lỗi | S6.3, C10.10 |
| Idempotency | C10.6, C5.14, C9.11 |
| End-to-end argument | C9.9, C10.6, C5.8 |
| Tách mechanism khỏi policy | C4, C6.14, C8.12 |
| Đánh đổi nhất quán–sẵn sàng (CAP/PACELC) | C10.3 |
| Định luật Little | C11.5, S7.1 |
| Định luật Amdahl | C3.8, C11.6 |
| Giới hạn Shannon | S1.7, C7.1 |
| "Mọi trừu tượng đều rò rỉ" | C1.8, C10.12, C12.8 |
| Ranh giới tin cậy | S4.1, C12.14 |
| Mọi thứ hỏng; câu hỏi là hỏng ra sao | C10.1, S6 |

**Đây là phần còn giá trị nếu mọi công cụ ở tầng 3–5 biến mất ngày mai.** Theo §1.1 của prompt, tầng này được ưu tiên trong mọi quyết định phân bổ thời gian.

## Tầng 2 — Long-lived fundamentals *(10–30 năm)*

Mô hình process của Unix · TCP/IP · ngữ nghĩa HTTP · mô hình quan hệ và SQL · C ABI và POSIX · hệ thống file và journaling · bộ nhớ ảo · mật mã khóa công khai · học dựa trên gradient · khái niệm RISC ISA · IEEE 754 · publish/subscribe · write-ahead log · cơ chế attention (**[Inference]** có khả năng long-lived; chưa chắc sau 10 năm).

## Tầng 3 — Durable technologies *(5–15 năm — đáng đầu tư sâu)*

| Công nghệ | Nhánh | Lý do tin là bền |
|---|---|---|
| Linux | C4, C10 | Nền tảng của gần như mọi thứ; 30+ năm và vẫn tăng |
| C | C1, C6 | ABI chuẩn của thế giới; mọi ngôn ngữ khác nói chuyện qua nó |
| Python | C1, C8, C9 | Vị trí ngôn ngữ dán đã ổn định hơn 15 năm |
| Git | C1.10 | Không có đối thủ khả tín |
| PostgreSQL | C9 | Mô hình quan hệ + hệ sinh thái mở rộng |
| Log phân tán kiểu Kafka | C9.9 | Trừu tượng, không phải sản phẩm — trừu tượng sẽ sống |
| Redis | C9.7 | Mô hình đơn giản, đúng việc |
| Container / OCI | C4.11, C10 | Đã thành chuẩn công nghiệp |
| Mô hình control-loop của Kubernetes | C10.12 | **Mô hình** bền hơn API cụ thể |
| Mô hình metric của Prometheus, mô hình trace của OpenTelemetry | C11.1, C11.2 | Đã thành chuẩn de facto |
| IaC khai báo (Terraform/OpenTofu) | C10.13 | Mô hình bền; nhà cung cấp có thể đổi |
| ARM Cortex-M | C3.4, C6 | Kiến trúc thống trị MCU |
| FreeRTOS / Zephyr | C6.7 | Hai mô hình khác nhau, cả hai đều có nền tảng thể chế |
| MQTT | C5.8 | Chuẩn OASIS; thiết kế phù hợp với ràng buộc thiết bị |
| gRPC / protobuf | C5.8 | Schema-first và tương thích ngược tốt |
| ONNX | C8.9 | Định dạng trung gian giữa framework |
| PyTorch | C8 | Đã thành mặc định trong nghiên cứu và phần lớn production |

## Tầng 4 — Current mainstream *(2026 — học để dùng, không học để thuộc)*

**[Fact, tháng 9/2026 — kiểm tra lại mỗi 6 tháng]**

| Hạng mục | Trạng thái |
|---|---|
| **LLM serving** | vLLM là chuẩn thực tế cho throughput cao, nhờ PagedAttention và continuous batching. TensorRT-LLM cho hiệu năng tối đa với chi phí thiết lập cao hơn nhiều |
| **Quantization** | AWQ, GPTQ, GGUF, FP8. FP8 trên H100/Blackwell cho ~1,5–2× throughput và giảm ~50% VRAM, mất chính xác thường dưới 1–2% trên benchmark chuẩn |
| **Tool protocol** | MCP đã thành mặc định, hiện do **Linux Foundation** quản trị, được các nhà cung cấp lớn hỗ trợ. Đây là tầng hiếm hoi trong AI stack có dấu hiệu sẽ bền |
| **Agent orchestration** | LangGraph cho workflow có trạng thái và durable execution. SDK vendor-native: OpenAI Agents SDK (3/2026), Google ADK và Claude Agent SDK (4/2026). Pydantic AI khi hợp đồng kiểu dữ liệu quan trọng hơn độ rộng orchestration |
| **RAG** | Đã thành **quyết định tầng**, không còn là quyết định framework: tầng retrieval và tầng orchestration thường dùng công cụ khác nhau |
| **Platform baseline** | Kubernetes + Terraform/OpenTofu là table stakes. Argo CD hoặc Flux cho GitOps |
| **Edge hardware** | ESP32-S3, STM32 (kể cả dòng có NPU như STM32N6), nRF, RP2350. NPU cấp MCU đang thành mặc định: TI đưa TinyEngine NPU vào toàn bộ danh mục MCU (3/2026), NXP i.MX RT, Renesas RZ/V |
| **Edge ML toolchain** | TFLite Micro và Edge Impulse. Họ YOLO nhỏ và MobileNet cho thị giác trên phần cứng có tăng tốc; biến thể chưng cất của Whisper cho speech-to-text trên SBC |

## Tầng 5 — Emerging *(theo dõi, chưa đặt cược)*

| Xu hướng | Vì sao đáng theo dõi | Vì sao chưa đặt cược |
|---|---|---|
| NPU tích hợp trong MCU thành mặc định | Đổi hoàn toàn cái gì chạy được ở edge | Toolchain còn phân mảnh nặng |
| Serving tách rời prefill/decode | Tăng đáng kể mức sử dụng GPU | Còn phức tạp vận hành |
| Tầng orchestration cho inference phân tán (llm-d, NVIDIA Dynamo) | Giải quyết bài toán thật | Chưa ổn định |
| Training và cá nhân hóa on-device | Mở ra lớp sản phẩm mới | Ràng buộc năng lượng và bộ nhớ còn gắt |
| Federated learning trên phần cứng phổ thông | Giải quyết quyền riêng tư ở gốc | Hạ tầng và công cụ chưa chín |
| Language model nhỏ trên SBC | Đưa khả năng ngôn ngữ ra edge | Chất lượng còn cách biệt lớn |
| Observability và evaluation cho agent như hạng mục riêng | Nhu cầu thật và cấp bách | Chưa hội tụ về mô hình chung |

## Tầng 6 — Đang mất dần relevance

| Thứ | Tình trạng | **Cái còn lại có giá trị** |
|---|---|---|
| AutoGen | Microsoft chuyển sang chế độ bảo trì, thay bằng Microsoft Agent Framework | Mẫu multi-agent conversation |
| "Prompt engineer" như chức danh | Đang biến mất khỏi tin tuyển dụng | Kỹ năng đặc tả yêu cầu chính xác — vẫn giá trị, nhưng như một phần của kỹ thuật |
| Thiết kế ứng dụng LLM "framework-first" | ~40% tác vụ gọi là "agent" trong production thực chất chỉ cần một lời gọi có structured output | Biết **khi nào không cần** framework |
| Terraform như "open source" không điều kiện | Đổi sang BSL từ 2023, sinh ra fork OpenTofu; nay là quyết định **quản trị**, không phải quyết định kỹ thuật | Mô hình khai báo + state + plan/apply — giống hệt nhau ở cả hai |
| "TinyML" như thương hiệu | TinyML Foundation đổi tên thành Edge AI Foundation cuối 2024 | Toàn bộ kỹ thuật bên dưới, không đổi |
| Benchmark tổng hợp làm tiêu chí chọn model | Thứ hạng benchmark không dự đoán được hiệu năng production | Phương pháp đánh giá — nhưng trên eval set của **bạn** |

## 8.1 — Cảnh báo về tầng agentic

**[Inference, độ tin cậy cao]** Tầng agent framework là tầng **biến động nhất và kém bền nhất** trong toàn bộ stack. Một phân tích ngành ghi nhận landscape này thay đổi trong 5 tháng đầu 2026 nhiều hơn cả 2024 và 2025 cộng lại: ba nhà cung cấp lớn ra SDK riêng trong vòng 8 tuần, và một framework phổ biến bị chuyển sang chế độ bảo trì.

**Hệ quả cho roadmap, áp dụng nghiêm:**

| Quy tắc | Cụ thể |
|---|---|
| Học **mẫu**, không học framework | State machine · durable execution · ranh giới tool · checkpoint human-in-the-loop · guardrail · ngân sách bước/token |
| Trần giờ cho bất kỳ framework nào | **20 h**. Vượt quá là dấu hiệu bạn đang học sai tầng |
| Thứ tự | Framework luôn học **sau cùng** trong mỗi khối, sau khi đã tự dựng phiên bản thô |
| Kiểm tra | Nếu framework bạn dùng biến mất, bạn phải dựng lại được chức năng tương đương trong ≤2 tuần |

## 8.2 — Quy tắc phân bổ giờ theo tầng

| Tầng | % giờ của nhánh liên quan | Lý do |
|---|---|---|
| 1 — Nguyên lý | ~15% | Ít nội dung, giá trị vĩnh viễn; học qua việc áp dụng |
| 2 — Nền tảng lâu dài | ~35% | Nhiều nội dung, giá trị rất lâu |
| 3 — Công nghệ bền | ~35% | Nơi công việc thực tế xảy ra |
| 4 — Mainstream hiện tại | ~12% | Đủ để dùng thành thạo, không hơn |
| 5 — Emerging | ~3% | Đọc để biết, thử một cái mỗi 6 tháng |
| 6 — Đang mất | ~0% | Chỉ đọc phần "cái còn lại có giá trị" |

---

# 9. KIẾN TRÚC 5–6 NĂM THEO PHASE

**Thay đổi cấu trúc so với v2:** giờ có **hai track chạy song song**, không phải một.

| Track | Nguồn | Điều khiển bởi | Nhánh chính |
|---|---|---|---|
| **Track OT** | Công việc | Dự án được giao — bạn không kiểm soát | C7, S2, S3, S6, A4, A5, phần OT của C5/C6/C12 |
| **Track IT** | Tự học | Roadmap này — bạn kiểm soát hoàn toàn | C1, C2, C3, C4, C8, C9, C10, C11, S1, S4, S5, phần IT của C5/C6/C12 |
| **Cầu nối** | Project cá nhân | Bạn thiết kế | Nơi hai track gặp nhau, và nguồn cung `observe→adapt` duy nhất |

Track OT **không lập lịch được** — nó phụ thuộc dự án công ty giao. Nên roadmap chỉ lập lịch cho Track IT, và coi Track OT là đầu vào ngẫu nhiên có xu hướng tích cực.

## Bản đồ tổng

```
Tháng:  0    6    12   18   24   30   36   42   48   54   60   66   72
        |----|----|----|----|----|----|----|----|----|----|----|----|

TRACK OT (công việc — không lập lịch được)
 Thử việc ██
 Định hướng, theo dõi, đọc bản vẽ  ████████████
 Tham gia commissioning có giám sát     ████████████████
 Commissioning độc lập, đóng góp thiết kế     ██████████████████████
 Trách nhiệm cấp hệ thống                            ████████████████████████

TRACK IT (tự học — lập lịch được)
P0 ██████
P1   ████████████████████
P2          ████████████████████████
P3                    ████████████████████████
P4                              ████████████████████████
P5                                        ████████████████████████

CẦU NỐI (project)
 P1 ████
 P2      ██████████
 P3              ████████████
 P4                      ████████████
 P5                              ████████████
 P6                                    ████████████████████████
                    ▲                          ▲
                    │                          └─ điểm rẽ nhánh (§11.4)
                    └─ hết thử việc + P2 xong
```

---

## ◆ PHASE 0 · BOOTSTRAP — tháng 0–6 · ~350 h tự học

**Giãn từ 3 tháng lên 6** vì thử việc và định hướng công việc ăn phần lớn năng lượng.

| Hạng mục | Giờ | Nội dung |
|---|---|---|
| C1 — C và Python cơ bản | 150 | Con trỏ, bộ nhớ, cấu trúc; Python + pytest |
| C1.9 — Tooling debug | 30 | gdb, valgrind, sanitizer — **sớm, không hoãn** |
| C4.12 + môi trường | 30 | Linux như môi trường sống, shell, dotfiles |
| C1.10 — Git | 20 | Mô hình đối tượng, workflow |
| C6 — Blink + toolchain | 40 | Board đầu tiên, cross-compile |
| S1.1 — Discrete math | 40 | Logic, tập hợp, quy nạp |
| **P1** — Sensor node + logger | 40 | Project đầu tiên |

**Song song ở Track OT:** ghi lại **mọi khái niệm vendor bạn gặp** và khái niệm trung lập bên dưới nó (bảng ở §2.3d). Đây là thói quen rẻ nhất có ROI cao nhất trong toàn bộ 6 năm — bắt đầu từ tuần đầu tiên.

**Tín hiệu sang Phase 1:** dựng lại P1 từ đầu trong một buổi, không copy-paste. Và: bạn có một file ghi chú ≥30 cặp *khái niệm vendor ↔ khái niệm trung lập*.

---

## ◆ PHASE 1 · NỀN TÍNH TOÁN — tháng 3–24 · ~800 h tự học

**Giãn từ 12 lên 21 tháng.** Đây là phase dài nhất và khó nhất khi vừa đi làm — vì nó cho cảm giác chậm và không nối trực tiếp với công việc.

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C1 Programming | 180 | C nâng cao, UB, build system, Python packaging |
| C2 DSA | 140 | Độ phức tạp → DP |
| C3 Computer architecture | 130 | **nand2tetris phần 1** (70 h) + ISA + assembly |
| C4 OS | 70 | Tiến trình, luồng, bộ nhớ ảo |
| S1 Mathematics | 140 | **Đợt 1**: discrete + đại số tuyến tính |
| C6 Embedded | 50 | Đọc datasheet, GPIO, timer |
| Project | 90 | **P2a + P2b** |

**Cạm bẫy đặc thù của người vừa đi làm:** phase này không cho bạn thứ gì dùng được ở công ty ngay, nên nó dễ bị bỏ. Chống bằng hai cách: giữ P2 chạy để luôn có thứ hữu hình, và dùng bảng §2.3d để thấy nand2tetris đang giải thích chính cái PLC bạn dùng hằng ngày.

**Tín hiệu sang Phase 2:** bạn debug bằng lập luận về bộ nhớ, không bằng thêm `print`. Và bạn giải thích được scan cycle của PLC bằng từ vựng của C4.2 và C6.15.

---

## ◆ PHASE 2 · NỀN HỆ THỐNG — tháng 18–38 · ~800 h tự học

**Mục tiêu:** mạng, dữ liệu, OS ở mức Advanced. Đây là phase bắt đầu **giao với công việc** — bạn sẽ hiểu tầng dưới của Profinet, của historian, của mạng nhà máy.

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C4 OS & concurrency | 170 | Concurrency, I/O model, filesystem, scheduling |
| C5 Networking | 160 | TCP sâu, socket, packet capture, DNS, HTTP |
| C9 Data engineering | 130 | Mô hình dữ liệu, SQL sâu, transaction, chuỗi thời gian |
| C10 Distributed | 60 | **Mô hình lỗi** — nền tư duy |
| C8 ML | 70 | Nền học thống kê + **đánh giá** (trước mọi modeling) |
| C11 Observability | 40 | Bốn tín hiệu + instrumentation |
| C1 + C2 tiếp | 80 | Error handling, runtime internals |
| C3 tiếp | 50 | **Phân cấp bộ nhớ** + phương pháp đo |
| S1 Mathematics | 60 | **Đợt 2**: xác suất + thống kê |
| S8 Communication | 20 | Design doc, ADR |
| Project | 160 | **P2c** xong, **P3** khởi động |

**Giao thoa với Track OT:** khi bạn học C5.5 (TCP sâu) và C5.16 (giao thức công nghiệp), lần đầu bạn sẽ thấy Profinet, Modbus TCP và IEC 61850 không phải ba thứ ma thuật riêng biệt mà là ba điểm khác nhau trên cùng một phổ đánh đổi.

**Tín hiệu sang Phase 3:** từ packet capture giải thích được một sự cố mạng nhà máy — và giải thích được cho cả kỹ sư OT lẫn kỹ sư IT, bằng từ vựng của mỗi bên.

---

## ◆ PHASE 3 · VÒNG LẶP KHÉP LẠI — tháng 30–50 · ~850 h tự học

**Mục tiêu:** mua ba cung `learn`, `infer`, `adapt` mà cả công việc lẫn ngành OT đều không cho.

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C8 ML & inference | 230 | Neural net từ đầu, kiến trúc, **nén model**, eval |
| C6 Embedded | 150 | RTOS, DMA, năng lượng, kiến trúc firmware, **bootloader/OTA** |
| C7 Sensing — **phần công việc không cho** | 80 | DSP, FFT, sensor fusion, trích đặc trưng cho ML |
| C10 Distributed | 140 | **Idempotency**, nhất quán, **kiểm soát tải** |
| C9 Data | 90 | **Ingest từ edge**, streaming, schema contract |
| C5 Networking | 80 | TLS, MQTT/gRPC, kết nối thực địa |
| C11 Observability | 40 | Profiling, phân phối độ trễ |
| C12 Architecture | 40 | ADR, mẫu kiến trúc, **ISA-95** |
| S4 Security | 40 | Threat modeling, **IEC 62443** |
| Project | 160 | **P3** hoàn thành (30 ngày thực địa), **P4** khởi động |

**Lưu ý phân bổ C7:** ở v2 nhánh này là 260 h tự học. Ở v3 chỉ còn 80 h vì công việc cấp phần lớn — nhưng **chỉ phần instrumentation công nghiệp**. Phần DSP, FFT, sensor fusion và trích xuất đặc trưng cho ML thì công việc không cho, và đó chính là 80 h này.

**Tín hiệu sang Phase 4:** P3 chạy 30 ngày ngoài thực địa. Và bạn chẩn đoán được một lỗi mà nguyên nhân nằm ở tầng khác với tầng triệu chứng, ≥3 lần, với 3 cặp tầng khác nhau.

---

## ◆ PHASE 4 · QUY MÔ, ĐỘ TIN CẬY, PRODUCTION — tháng 42–62 · ~750 h tự học

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C8 ML | 150 | **Serving**, LLM systems, **eval harness**, drift |
| C11 Observability | 90 | SLO, hàng đợi, capacity, chaos, incident |
| C10 Distributed & cloud | 100 | Cloud, IaC, **Kubernetes** (sau distributed) |
| C9 Data | 60 | Object storage, vector, chất lượng dữ liệu, backup |
| C6 Embedded | 80 | **Inference trên thiết bị**, bảo mật, real-time |
| C3 Architecture | 50 | GPU, **NPU & accelerator** |
| C12 Architecture | 40 | Interface, đánh đổi, kiến trúc tham chiếu |
| S5 Testing | 50 | Test hệ phi tất định, eval như testing, HIL |
| S7 Economics | 20 | Mô hình chi phí, capacity |
| A1–A3 Adjacent | 60 | Robotics, simulation, human factors |
| Project | 190 | **P4** hoàn thành, **P5** hoàn thành |

**Tín hiệu sang Phase 5:** dự đoán được hành vi hệ thống dưới tải trước khi đo, đúng thường xuyên hơn sai. Ghi 10 dự đoán, đo, đếm.

---

## ◆ PHASE 5 · KIẾN TRÚC & CHIỀU SÂU — tháng 54–78 · ~700 h tự học

| Nhánh | Giờ | Trọng tâm |
|---|---|---|
| C12 Architecture | 60 | **FMEA xuyên tầng**, **phân chia edge–cloud**, migration, security by design |
| Nhánh Expert đã chọn | 180 | Đẩy tới mức tự implement lại core components |
| C8 ML | 80 | Mẫu agentic, monitoring, chi phí, chế độ hỏng |
| A4–A6 Adjacent | 80 | Business, standards, licensing |
| **P6** — hệ end-to-end | 250 | **North Star ở dạng sản phẩm — 90 ngày vận hành** |
| Slack | 50 | |

**P7** (làm cứng hoặc đóng góp mã nguồn mở) chuyển sang tùy chọn sau tháng 72.

**Tín hiệu hoàn thành:** người khác đến hỏi bạn *nên thiết kế thế nào*, và bạn trả lời bằng đánh đổi có số liệu. Và bạn nêu được rõ ràng cái bạn **không** biết.

---

## 9.1 — Bảng tổng giờ theo phase (chỉ Track IT)

| Phase | Tháng | Giờ tự học | % |
|---|---|---|---|
| P0 Bootstrap | 0–6 | 350 | 10% |
| P1 Nền tính toán | 3–24 | 800 | 22% |
| P2 Nền hệ thống | 18–38 | 800 | 22% |
| P3 Vòng lặp khép lại | 30–50 | 850 | 24% |
| P4 Quy mô & production | 42–62 | 750 | 21% |
| P5 Kiến trúc & chuyên sâu | 54–78 | 700 | 19% |
| | | **~3.600 h** (có chồng lấn) | |

*Tổng vượt 100% vì phase chồng lấn về thời gian; tổng giờ thực là ~3.600 h.*

Cộng **~2.100 h** quy đổi từ công việc (Phụ lục D) → **~5.700 h hiệu dụng**.

## 9.2 — Ba quy tắc cho người vừa đi làm vừa tự học

1. **Nhánh nào công việc đang dạy thì đừng tự học song song.** Chờ. Nếu tháng này bạn đang commissioning một hệ điều khiển, đừng dành tối để đọc control theory — dành tối cho C1 hoặc C8. Học cùng lúc cùng chủ đề từ hai nguồn nghe có vẻ tăng tốc nhưng thực tế là trùng lặp.

2. **Ưu tiên nhánh công việc không bao giờ cho.** Thứ tự bất biến: C8 > C10 > C2/C3/C4 > C1 > phần còn lại. Lý do: đây là những thứ mà nếu bạn không tự học thì **không có nguồn nào khác**, mãi mãi.

3. **Chuyển đổi mỗi thứ học được ở công ty thành khái niệm trung lập trong vòng 1 tuần.** Nếu sau một tháng bạn chỉ nói được "tôi cấu hình OB35 chu kỳ 100ms", bạn chưa học gì chuyển nhượng được. Nếu bạn nói được "tôi cấu hình một tác vụ chu kỳ với ngân sách WCET 100ms, và tôi biết cách đo jitter của nó" — đó là kiến thức đi theo bạn suốt đời.


# 10. PROJECT PROGRESSION — ĐẶC TẢ ĐẦY ĐỦ

**Nguyên tắc:** một project tốt **tích hợp nhiều nhánh**. Bảy project, mỗi cái là tiền đề của cái sau. Tổng ~1.000 h ngoài giờ học nhánh.

**Quy tắc chung áp dụng cho mọi project:**
- Viết ADR cho mọi quyết định không hiển nhiên, **từ P2 trở đi**
- Mọi project phải có README mà người lạ chạy được trong ≤30 phút
- Mọi project phải có tiêu chí nghiệm thu **đo được**, viết ra **trước khi** bắt đầu
- Nếu một project vượt 2× thời gian dự kiến: dừng, viết ra vì sao, rồi quyết định thu hẹp phạm vi hay tiếp tục

---

## ◆ P1 · SENSOR NODE + LOGGER — *toy* — tháng 2–4 — ~40 h

### Mục tiêu
Nối được thế giới vật lý với phần mềm, đầu-cuối, một lần, dù xấu.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | MCU đọc ≥1 cảm biến (nhiệt độ hoặc IMU) ở tần số cố định |
| F2 | Truyền dữ liệu về máy tính qua UART hoặc Wi-Fi |
| F3 | Script trên máy nhận, parse, và lưu vào SQLite |
| F4 | Script thứ hai đọc SQLite và vẽ đồ thị theo thời gian |
| F5 | Timestamp gắn ở phía máy tính (chưa cần đồng bộ) |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Chạy liên tục không crash | ≥ 6 giờ |
| N2 | Tần số lấy mẫu ổn định | sai lệch < 5% |
| N3 | Không mất mẫu khi đường truyền tốt | 0 mẫu mất trong 1 giờ |

### BOM
ESP32-S3 hoặc Pico 2 · một cảm biến I²C (BME280, MPU6050, hoặc DS18B20) · breadboard + dây · cáp USB.

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Blink + toolchain | Nạp được firmware tự build, không dùng IDE có sẵn |
| M2 | Đọc cảm biến qua I²C | Giá trị hợp lý, xác nhận bằng cách thay đổi môi trường vật lý |
| M3 | Truyền và parse | Máy tính nhận đúng 1000 mẫu liên tiếp |
| M4 | Lưu trữ | SQLite có schema, không phải CSV dump |
| M5 | Trực quan hóa | Đồ thị đọc được, có nhãn trục và đơn vị |

### Tiêu chí nghiệm thu
- [ ] Chạy 6 giờ liên tục, dữ liệu đầy đủ
- [ ] Bạn giải thích được **từng dòng** firmware, kể cả phần khởi tạo peripheral
- [ ] Bạn giải thích được vì sao chọn tần số lấy mẫu đó
- [ ] Dựng lại toàn bộ từ đầu trong một buổi, không copy-paste

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C1.1, C1.2, C6.1, C6.3, C7.6, C9.1 | Bạn nối được hai thế giới | firmware ↔ phần mềm ↔ lưu trữ |

**Mở đường cho:** tất cả. Đây là bộ xương của mọi project sau.

### Cạm bẫy
Dùng thư viện Arduino cho mọi thứ. Cho phép ở M1–M2 để có động lực, nhưng **phải quay lại viết bằng register hoặc HAL thật** trước khi tuyên bố P1 xong — nếu không, C6.1 sẽ không bao giờ đạt.

---

## ◆ P2 · TỰ VIẾT LẠI HẠ TẦNG — *small* — tháng 6–12 — ~120 h

### Mục tiêu
Hiểu các trừu tượng bạn dùng hàng ngày, bằng cách tự dựng lại chúng. **Đây là project khiến hồ sơ của bạn khác phần lớn ứng viên.**

Ba thành phần, làm tuần tự:

### P2a · TCP server từ socket thuần — ~45 h

| # | Yêu cầu |
|---|---|
| F1 | Server nhận kết nối TCP, xử lý giao thức dòng đơn giản (hoặc HTTP/1.1 tối giản) |
| F2 | Không dùng framework; chỉ dùng API socket của OS |
| F3 | Xử lý đúng partial read và partial write |
| F4 | Event loop dùng `epoll` (Linux), single-threaded |
| F5 | Timeout cho kết nối nhàn rỗi; graceful shutdown drain kết nối đang xử lý |
| N1 | ≥10.000 kết nối đồng thời, bộ nhớ < 500 MB |
| N2 | p99 latency < 10 ms ở 1.000 req/s trên localhost |
| N3 | Không rò rỉ mô tả file sau 1 triệu kết nối |

**Nghiệm thu:** chạy load test, đồ thị kết nối/bộ nhớ/latency; `lsof` xác nhận không rò rỉ fd; giải thích được vì sao `epoll` edge-triggered cần đọc tới `EAGAIN`.

### P2b · Key-value store có write-ahead log — ~50 h

| # | Yêu cầu |
|---|---|
| F1 | `get`, `put`, `delete` qua giao thức mạng (dùng lại P2a) |
| F2 | Write-ahead log ghi trước khi cập nhật memtable |
| F3 | Phục hồi đầy đủ sau crash bằng cách replay WAL |
| F4 | Checkpoint định kỳ và cắt WAL |
| F5 | Tùy chọn: LSM tree với SSTable và compaction cơ bản |
| N1 | **Không mất dữ liệu đã ack** khi kill -9 hoặc cắt điện |
| N2 | Throughput ghi ≥ 20.000 op/s với `fsync` mỗi N op (nêu rõ N và đánh đổi) |
| N3 | Thời gian phục hồi < 10 giây với WAL 1 GB |

**Nghiệm thu:** script tự động kill process ngẫu nhiên ≥200 lần trong lúc ghi; sau mỗi lần, xác nhận mọi giá trị đã ack vẫn đọc được. Đây là tiêu chí khó nhất của P2.

### P2c · Shell tối giản — ~25 h

| # | Yêu cầu |
|---|---|
| F1 | Parse dòng lệnh, `fork`/`exec`, `wait` |
| F2 | Pipe giữa các lệnh, redirect vào/ra |
| F3 | Job control cơ bản: chạy nền, `jobs`, `fg` |
| F4 | Xử lý tín hiệu đúng: Ctrl-C tới foreground job, không tới shell |
| F5 | Biến môi trường và built-in `cd`, `export` |

**Nghiệm thu:** chạy được `cat file | grep x | wc -l > out.txt`; Ctrl-C giết đúng tiến trình; không tạo zombie.

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C1 (Ad), C2, C4.1, C4.5, C4.6, C4.9, C5.10, C9.4 | Bạn hiểu trừu tượng bạn dùng, không chỉ gọi được chúng | OS ↔ mạng ↔ lưu trữ bền vững |

**Mở đường cho:** P4, và toàn bộ năng lực debug ở tầng hệ thống.

### Cạm bẫy
Làm cả ba cùng lúc. Làm tuần tự; P2b dùng lại P2a là một phần của bài học (interface design).

---

## ◆ P3 · EDGE ANOMALY DETECTOR — *realistic* — tháng 14–22 — ~180 h

> **[Ghi chú v3 — P3 đổi vai trò]** Ở v2, P3 là bài tập tích hợp. Ở v3 nó là **nguồn kinh nghiệm vận hành dài hạn duy nhất của bạn**, vì công ty là tổng thầu EPC không làm O&M (§2.3c). Yêu cầu "30 ngày ngoài thực địa" chuyển từ *nên có* sang **không thương lượng**.
>
> **Chọn đối tượng giám sát:** hoàn toàn tự do, và **không nên** mặc định chọn thiết bị ngành năng lượng chỉ vì bạn làm ở đó. Một máy bơm, một tủ lạnh, một máy giặt, một quạt công nghiệp đều dạy cùng bài học kỹ thuật. Chọn theo tiêu chí: (a) bạn tiếp cận được 30 ngày liên tục, (b) bạn tạo được bất thường có kiểm soát, (c) nó **không** thuộc tài sản công ty — để tránh vướng quy định và để bạn tự do thử nghiệm.

### Mục tiêu
ML trong ràng buộc thật, không trong notebook. **Đây là project khác biệt hóa lớn nhất của bạn.**

Phát hiện bất thường rung động hoặc âm thanh chạy **trên MCU**, triển khai ngoài thực địa.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | Thu tín hiệu rung (IMU) hoặc âm thanh (mic I²S) ở ≥1 kHz qua DMA, không mất mẫu |
| F2 | Trích xuất đặc trưng trên thiết bị (RMS, băng tần, hoặc MFCC) |
| F3 | Model phát hiện bất thường (autoencoder hoặc one-class) quantize int8, chạy trên MCU |
| F4 | Cảnh báo qua MQTT khi phát hiện bất thường; heartbeat định kỳ |
| F5 | Store-and-forward khi mất mạng; đồng bộ lại khi có mạng |
| F6 | OTA update firmware **và** model, có rollback |
| F7 | Hiệu chuẩn cảm biến lưu trên thiết bị, có phiên bản |
| F8 | Chế độ chẩn đoán: dump raw signal khi có lệnh từ xa |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Tuổi thọ pin | ≥ 30 ngày với nguồn đã chọn — **có phép tính ngân sách năng lượng chứng minh trước** |
| N2 | Latency inference | p99 < ngưỡng bạn đặt, đo trên thiết bị |
| N3 | RAM cho tensor arena | < 128 KB (hoặc ngưỡng phù hợp với MCU bạn chọn) |
| N4 | Không mất dữ liệu | offline 24 h rồi đồng bộ: 0 mất, 0 trùng |
| N5 | OTA an toàn | cắt điện ở ≥3 thời điểm khác nhau trong cập nhật, thiết bị vẫn boot |
| N6 | Độ chính xác | đo trên eval set từ **thiết bị thật**, không từ dataset công khai |
| N7 | Chạy liên tục | ≥ 30 ngày không can thiệp tay |

### BOM bổ sung
IMU chất lượng tốt (ICM-42688 hoặc tương đương) hoặc mic I²S (INMP441) · nguồn pin phù hợp (18650 + mạch bảo vệ, hoặc LiPo) · INA219 để đo dòng · vỏ in 3D hoặc hộp nhựa · nam châm hoặc kẹp để gắn lên thiết bị cần giám sát.

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Thu tín hiệu qua DMA | 1 giờ liên tục, bộ đếm xác nhận 0 mẫu mất |
| M2 | Hiệu chuẩn | Sai số RMS giảm, có số liệu trước/sau trên tập điểm độc lập |
| M3 | Thu dữ liệu huấn luyện | ≥20 giờ dữ liệu bình thường + ≥10 kịch bản bất thường tạo được |
| M4 | Trích xuất đặc trưng | Chạy trên MCU, khớp với bản Python trong sai số 1e-3 |
| M5 | Model + eval set | Eval set có ≥3 lát cắt; bạn viết ra nó **không** đo được gì |
| M6 | Quantize + deploy | Đường cong Pareto ≥4 cấu hình: (kích thước, độ chính xác, latency) |
| M7 | Kết nối + store-and-forward | Test offline 24 h |
| M8 | OTA + rollback | Cắt điện 20 lần ở các thời điểm ngẫu nhiên, 20/20 boot được |
| M9 | Ngân sách năng lượng | Đo dòng thật, so với tính toán, giải thích chênh lệch |
| M10 | Triển khai thực địa | 30 ngày trên một thiết bị thật (quạt, máy bơm, máy giặt, tủ lạnh) |

### Tiêu chí nghiệm thu
- [ ] Chạy 30 ngày ngoài bàn làm việc, không cắm lại, không sửa
- [ ] Phát hiện đúng một bất thường bạn cố ý tạo ra, ≥3 lần độc lập
- [ ] Tỷ lệ báo động giả dưới ngưỡng bạn đặt ra **trước khi** triển khai
- [ ] OTA thành công một lần trong lúc đang triển khai thực địa
- [ ] Bạn giải thích được tại sao model sai ở những trường hợp nó sai

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C6 (Ad), C7 (Ad), C8.3, C8.9, C5.8, C5.14, C9.11, S2, S6 | ML trong ràng buộc thật | vật lý ↔ tín hiệu ↔ ML ↔ mạng ↔ vận hành |

**Mở đường cho:** P6, và toàn bộ luận điểm khác biệt hóa ở §11.

### Cạm bẫy
| Cạm bẫy | Phòng tránh |
|---|---|
| Dùng dataset công khai thay vì dữ liệu thật | Dữ liệu công khai không có chế độ hỏng của **cảm biến của bạn** |
| Bỏ qua hiệu chuẩn | Model sẽ học sai lệch của cảm biến thay vì học hiện tượng |
| Để OTA tới cuối | Thiết kế OTA từ M1; nó ảnh hưởng tới bố cục flash |
| Đo pin bằng "nó vẫn chạy" | Đo dòng thật bằng INA219 và tích phân theo thời gian |
| Tuyên bố xong khi nó chạy trên bàn | 30 ngày ngoài thực địa là tiêu chí, không thương lượng |

---

## ◆ P4 · INGESTION & SERVING PLATFORM — *realistic-complex* — tháng 20–30 — ~180 h

### Mục tiêu
Vận hành dữ liệu ở quy mô và dưới điều kiện xấu.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | Nhận dữ liệu từ ≥10 thiết bị (thật hoặc giả lập từ dữ liệu thật của P3) |
| F2 | Gateway/broker MQTT, xác thực bằng mTLS, mỗi thiết bị có định danh riêng |
| F3 | Ingest vào stream có thứ tự trong partition |
| F4 | Xử lý: validation, dedup theo idempotency key, enrichment |
| F5 | Lưu vào time-series store với retention policy nhiều tầng |
| F6 | API truy vấn: theo thiết bị, theo khoảng thời gian, theo mức tổng hợp |
| F7 | Dashboard: trạng thái đội thiết bị, dữ liệu mới nhất, cảnh báo |
| F8 | Device management: đăng ký, provisioning, trạng thái online/offline |
| F9 | Schema registry với kiểm tra tương thích trong CI |
| F10 | Backfill: nạp dữ liệu lịch sử mà không phá thống kê |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Ingest throughput | ≥ 10.000 điểm/giây, đo được |
| N2 | Độ trễ ingest | p99 từ thiết bị tới truy vấn được < 10 giây |
| N3 | Đồng bộ hàng loạt | 20 thiết bị offline 24 h cùng trở lại: tải server **không vượt 2×** bình thường |
| N4 | Truy vấn | "trung bình theo giờ, 30 ngày" trả về < 1 giây |
| N5 | Dung lượng | 1 năm dữ liệu 100 thiết bị × 5 cảm biến × 1 Hz trong ngân sách bạn đặt |
| N6 | SLO | định nghĩa ≥3 SLI với mục tiêu, có dashboard |
| N7 | Observability | trace từ thiết bị tới DB với correlation ID |
| N8 | Khôi phục | thực hiện restore thật, đo RTO/RPO |

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Hạ tầng bằng IaC | Phá hủy và dựng lại hoàn toàn từ code, dịch vụ hoạt động |
| M2 | Broker + mTLS + provisioning | Thiết bị mới tự đăng ký và nhận chứng chỉ |
| M3 | Pipeline ingest + dedup | Test gửi trùng 3× cho kết quả giống hệt |
| M4 | Time-series store + retention | Tính toán dung lượng khớp với thực tế trong 20% |
| M5 | API + dashboard | Trả lời "hệ có khỏe không" trong ≤10 giây |
| M6 | Observability | Trace đi qua ≥4 thành phần |
| M7 | SLO + cảnh báo | Cảnh báo burn-rate nhiều cửa sổ |
| M8 | Test đồng bộ hàng loạt | Đồ thị tải chứng minh N3 |
| M9 | Backup + restore thật | RTO/RPO đo được |
| M10 | Schema evolution | Đổi schema, consumer cũ vẫn chạy, chứng minh trong CI |

### Tiêu chí nghiệm thu
- [ ] Toàn bộ hạ tầng dựng lại từ zero bằng một lệnh
- [ ] 10 thiết bị chạy liên tục 7 ngày, dashboard phản ánh đúng
- [ ] Test đồng bộ hàng loạt pass với đồ thị chứng minh
- [ ] Restore thật thành công, RTO đo được
- [ ] Bạn tìm được một sự cố (tự dựng) chỉ bằng trace và metric, không đọc code

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C9 (Ad), C10 (In→Ad), C11 (In), C5.9, C5.13, C10.13, S7 | Vận hành dữ liệu ở quy mô, dưới điều kiện xấu | edge ↔ streaming ↔ storage ↔ API ↔ observability |

**Mở đường cho:** P5, P6.

### Cạm bẫy
Dựng dashboard trước khi có metric đáng nhìn. Thứ tự đúng: instrument → thu metric → biết câu hỏi nào cần trả lời → dashboard.

---

## ◆ P5 · INFERENCE SERVICE — *complex* — tháng 28–38 — ~180 h

### Mục tiêu
Hiểu **kinh tế học và vật lý** của inference, không chỉ API của nó.

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | Tự host một model (LLM nhỏ, hoặc model thị giác, hoặc model từ P3 ở quy mô lớn hơn) |
| F2 | API tương thích chuẩn (OpenAI-compatible hoặc gRPC có schema) |
| F3 | Continuous batching hoặc dynamic batching |
| F4 | Hỗ trợ ≥2 cấu hình quantization, chuyển đổi được |
| F5 | Autoscaling theo độ sâu hàng đợi hoặc theo latency, có scale-to-zero |
| F6 | Kiểm soát tải: rate limit theo client, load shedding, circuit breaker |
| F7 | Đo và ghi nhận: TTFT, TPOT, throughput, độ sâu hàng đợi, cost-per-inference |
| F8 | Eval harness chạy trong CI trước mỗi lần đổi cấu hình |
| F9 | Fallback khi model không khả dụng |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Cải thiện throughput | **≥2×** so với cấu hình ngây thơ, bằng thay đổi cấu hình, có số đo |
| N2 | Latency budget | p50 và p99 dưới ngưỡng bạn đặt ở tải mục tiêu |
| N3 | Sống sót quá tải | ở **3× tải thiết kế**, suy giảm có kiểm soát thay vì sập |
| N4 | Cost-per-inference | tính được, và so sánh với chi phí gọi API bên thứ ba |
| N5 | Mất chính xác do quantization | dưới ngưỡng đặt trước, đo trên eval set riêng |
| N6 | Khởi động lạnh | đo được, và có chiến lược giảm thiểu |

### Milestone
| # | Nội dung | Xong khi |
|---|---|---|
| M1 | Serving cơ bản chạy | Model trả về kết quả đúng qua API |
| M2 | Đo baseline | Throughput, TTFT, TPOT, mức dùng VRAM |
| M3 | Batching | Throughput tăng, đồ thị theo kích thước batch |
| M4 | Quantization | Đường cong Pareto ≥4 điểm |
| M5 | Kiểm soát tải | Đồ thị hành vi ở 1×, 2×, 3×, 5× tải |
| M6 | Autoscaling | Phản ứng với spike, đo thời gian phản ứng |
| M7 | Eval harness trong CI | Bắt được một regression bạn cố ý tạo ra |
| M8 | Mô hình chi phí | Bảng tính có phân tích độ nhạy |
| M9 | Load test tới điểm gãy | Mô tả **chính xác cách nó gãy** |

### Tiêu chí nghiệm thu
- [ ] Throughput ≥2× baseline, với giải thích **cơ chế** của mỗi cải thiện
- [ ] Ở 3× tải, hệ từ chối rõ ràng thay vì treo hoặc sập
- [ ] Bảng so sánh tự host vs API bên thứ ba với điểm hòa vốn tính được
- [ ] Bạn chỉ ra được kernel/giai đoạn nào là nút thắt và vì sao (memory-bound hay compute-bound)

### Bản đồ nhánh
| Luyện | Chứng minh | Nối domain |
|---|---|---|
| C8.10 (Ad→Ex), C8.9, C3.9, C3.6, C10.10, C11 (Ad), S7 | Kinh tế học và vật lý của inference | kiến trúc máy tính ↔ ML ↔ hạ tầng ↔ chi phí |

**Mở đường cho:** P6.

### Cạm bẫy
Đo throughput tối đa thay vì throughput ở latency cố định. Con số "10.000 token/giây" vô nghĩa nếu p99 latency là 30 giây.

---

## ◆ P6 · CLOSED-LOOP INTELLIGENT SYSTEM — *end-to-end* — tháng 36–54 — ~500 h

### Mục tiêu
**North Star ở dạng sản phẩm.** Đây là project chứng minh toàn bộ roadmap.

### Kiến trúc yêu cầu

```
Thiết bị (≥5, ngoài thực địa)
   │ cảm nhận
   ↓
Tiền xử lý + inference cục bộ (từ P3)
   │ truyền qua mạng không tin cậy
   ↓
Ingestion platform (từ P4)
   │
   ├─→ Lưu trữ + huấn luyện lại định kỳ
   │
   ↓
Tầng suy luận
   • model học được (phát hiện, phân loại, dự đoán)
   • tầng LLM với tool calling trong ranh giới có kiểm soát
   • kết hợp thành quyết định
   ↓
★ TẦNG CHÍNH SÁCH ★
   • giới hạn hành động cứng
   • ngưỡng tin cậy
   • human-in-the-loop cho hành động rủi ro cao
   • fallback khi model im lặng hoặc trả rác
   ↓
Hành động
   • tác động lên thiết bị (điều chỉnh tham số, kích hoạt actuator)
   • hoặc tác động lên hệ thống khác (ticket, thông báo, API)
   ↓
Quan sát kết quả → phát hiện drift → huấn luyện lại → (quay lại)
```

### Đặc tả chức năng
| # | Yêu cầu |
|---|---|
| F1 | ≥5 thiết bị vật lý chạy ngoài thực địa, ≥2 loại cảm biến khác nhau |
| F2 | Inference cục bộ trên thiết bị + inference tập trung ở cloud, phân chia có lập luận |
| F3 | Tầng LLM có tool calling; tool có schema, có validation, có quyền tối thiểu |
| F4 | Tầng chính sách độc lập với model, không thể bị model bỏ qua |
| F5 | Human-in-the-loop: hành động rủi ro cao cần phê duyệt, có giao diện và ngữ cảnh đầy đủ |
| F6 | Vòng hành động: quyết định thực sự thay đổi trạng thái thiết bị hoặc hệ thống khác |
| F7 | Eval harness cho toàn hệ, không chỉ cho model |
| F8 | Phát hiện drift và quy trình huấn luyện lại có kiểm soát |
| F9 | Audit log: mọi quyết định truy vết được về input, model version, và policy version |
| F10 | Chế độ suy giảm: hệ hoạt động ở mức tối thiểu khi cloud không khả dụng |

### Đặc tả phi chức năng
| # | Yêu cầu | Ngưỡng |
|---|---|---|
| N1 | Vận hành liên tục | ≥ 90 ngày |
| N2 | SLO | ≥5 SLI định nghĩa, đạt trong ≥95% thời gian |
| N3 | Chaos | giết ngẫu nhiên ≥5 thành phần (kể cả thiết bị vật lý), hệ vẫn đạt SLO |
| N4 | An toàn | không hành động nguy hiểm nào thực hiện được, kể cả khi model trả về giá trị điên rồ |
| N5 | Chi phí | dashboard chi phí theo tính năng; cost-per-decision tính được |
| N6 | FMEA | ≥30 chế độ hỏng phân tích, mỗi cái có phát hiện hoặc giảm thiểu |
| N7 | Tài liệu | ≥10 ADR, 1 design doc, 1 runbook, 1 threat model |
| N8 | Người lạ vận hành được | một người khác chạy runbook và xử lý được một sự cố mô phỏng |

### Milestone
| # | Nội dung | Thời điểm | Xong khi |
|---|---|---|---|
| M1 | Design doc + kiến trúc | tháng 36 | Có ADR cho ≥8 quyết định lớn, bao gồm phân chia edge–cloud |
| M2 | Threat model + FMEA sơ bộ | tháng 37 | ≥20 mục, tìm ≥3 điều bạn chưa nghĩ tới |
| M3 | Đội thiết bị triển khai | tháng 39 | 5 thiết bị chạy 2 tuần ổn định |
| M4 | Pipeline dữ liệu + eval set nền | tháng 41 | Eval set có ≥5 lát cắt, viết ra nó không đo được gì |
| M5 | Tầng suy luận v1 | tháng 43 | Quyết định sinh ra nhưng **chưa** tác động (shadow mode) |
| M6 | So sánh shadow vs người | tháng 45 | ≥100 quyết định so sánh, phân tích lỗi có hệ thống |
| M7 | Tầng chính sách + HITL | tháng 46 | Chứng minh hành động nguy hiểm bị chặn ở ≥5 kịch bản tấn công |
| M8 | Bật vòng hành động | tháng 47 | Hành động thật, bắt đầu từ phạm vi hẹp nhất |
| M9 | Observability + SLO + chi phí | tháng 49 | Dashboard trả lời được 5 câu hỏi vận hành |
| M10 | Chaos + failure injection | tháng 51 | ≥5 thành phần, mỗi cái ≥3 lần |
| M11 | Drift + huấn luyện lại | tháng 52 | Một chu kỳ huấn luyện lại hoàn chỉnh, có cổng chất lượng |
| M12 | 90 ngày vận hành | tháng 54 | Báo cáo vận hành với số liệu thật |

### Tiêu chí nghiệm thu
- [ ] 90 ngày vận hành, ≥5 SLI đạt mục tiêu ≥95% thời gian
- [ ] Chaos test pass với ≥5 thành phần
- [ ] Bạn giải thích được **mọi quyết định** hệ đưa ra trong một ngày bất kỳ, bằng audit log
- [ ] ≥1 sự cố thật xảy ra, bạn viết postmortem, action item đã hoàn thành
- [ ] Một kỹ sư lạ đọc tài liệu và vận hành được hệ trong 1 ngày
- [ ] Bạn trình bày được kiến trúc trong 20 phút với đánh đổi có số, và trả lời được phản biện

### Bản đồ nhánh
**Luyện:** toàn bộ 12 nhánh core + S4, S5, S6, S8 + A3.
**Chứng minh:** chính xác North Star ở §2.1.
**Nối:** tất cả.

### Cạm bẫy — quan trọng nhất trong toàn bộ §10
| Cạm bẫy | Phòng tránh |
|---|---|
| **Bật vòng hành động quá sớm** | Shadow mode ≥2 tháng trước khi cho phép hành động thật. M5→M8 là 4 tháng, có lý do |
| **Tầng chính sách nằm trong prompt** | Chính sách phải là code, ở ngoài model, không thể bị prompt bỏ qua |
| **Phạm vi quá rộng** | Bắt đầu bằng **một** loại quyết định trên **một** loại thiết bị. Mở rộng sau khi ổn định |
| **Bỏ qua audit log** | Nếu không truy vết được quyết định, bạn không debug được và không chịu trách nhiệm được |
| **Coi LLM là bộ não** | LLM là một thành phần trong tầng suy luận, không phải kiến trúc |
| **Không có chế độ suy giảm** | Thiết kế "cloud chết thì sao" từ ngày đầu, không bổ sung sau |

---

## ◆ P7 · LÀM CỨNG HOẶC ĐÓNG GÓP NGƯỢC — tháng 48+ — ~200 h

Chọn **một**:

### P7a · Làm cứng P6

| Yêu cầu |
|---|
| Multi-tenant: ≥3 tenant cách ly về dữ liệu và về tài nguyên |
| Multi-region hoặc edge-cloud phân tầng đầy đủ |
| Migration không downtime cho ≥1 thành phần lớn (đổi storage engine, đổi giao thức, hoặc đổi model serving) |
| Quy trình vận hành: on-call rotation (dù chỉ một người), runbook đầy đủ, escalation |
| Tài liệu đủ để bàn giao cho người khác hoàn toàn |

**Nghiệm thu:** thực hiện migration trong lúc hệ đang phục vụ, 0 request thất bại, có đồ thị chứng minh.

### P7b · Đóng góp mã nguồn mở

| Yêu cầu |
|---|
| Chọn một dự án **trong stack của bạn**: serving engine, RTOS, observability, IaC, hoặc thư viện DSP |
| Bắt đầu: đọc code, sửa bug nhỏ, cải thiện tài liệu |
| Tiến tới: ≥1 đóng góp có ý nghĩa (tính năng, sửa bug khó, hoặc cải thiện hiệu năng đo được) |
| Vượt qua review của maintainer, kể cả khi review khó |

**Nghiệm thu:** ≥1 PR có ý nghĩa được merge, và bạn giải thích được kiến trúc của dự án đó.

### [Recommendation]
| Chọn | Khi nào |
|---|---|
| **P7b** (open source) | Bạn còn đang tìm đòn bẩy nghề nghiệp. Code của bạn đứng được trước review của người lạ khó tính là tín hiệu mạnh hơn mọi certification |
| **P7a** (làm cứng) | Bạn đã có việc tốt và cần chiều sâu vận hành. Migration không downtime là năng lực hiếm |

---

## 10.1 — Bảng tổng project

| # | Tên | Mức | Tháng | Giờ | Nhánh chính | Chứng minh gì |
|---|---|---|---|---|---|---|
| P1 | Sensor node + logger | toy | 2–4 | 40 | C1, C6, C7, C9 | Nối được hai thế giới |
| P2 | Tự viết lại hạ tầng | small | 6–12 | 120 | C1, C2, C4, C5, C9 | Hiểu trừu tượng bạn dùng |
| P3 | Edge anomaly detector | realistic | 14–22 | 180 | C6, C7, C8, C5, S2, S6 | ML trong ràng buộc thật |
| P4 | Ingestion & serving platform | realistic-complex | 20–30 | 180 | C9, C10, C11, C5 | Dữ liệu ở quy mô, điều kiện xấu |
| P5 | Inference service | complex | 28–38 | 180 | C8, C3, C10, C11, S7 | Kinh tế học và vật lý của inference |
| P6 | Closed-loop intelligent system | end-to-end | 36–54 | 500 | tất cả | North Star |
| P7 | Làm cứng / open source | — | 48+ | 200 | tùy chọn | Tiến hóa hệ thống / code đứng trước người lạ |
| | | | | **~1.400 h** | | |

*Phần vượt 1.000 h được bù bằng giờ nhánh (project **là** cách học nhánh ở Phase 3–5).*

---

# 11. SCENARIOS + RECOMMENDED PATH

## 11.0 — Đích đã xác nhận: liên ngành, không chuyên ngành

Bạn đã nói rõ: *đích đến không chỉ ở ngành năng lượng, cũng không thuần một mảng nào cả*.

Đây là một vị thế **hợp lệ và mạch lạc**, không phải sự thiếu quyết đoán — và nó chính là main root đã chuẩn hóa ở §1.2. Nhưng nó có một chế độ hỏng cụ thể cần gọi tên: **nông ở mọi nơi**.

Ba cơ chế phòng vệ, đã có sẵn trong kiến trúc tài liệu:

| Cơ chế | Ở đâu | Tác dụng |
|---|---|---|
| **Gradient độ sâu theo khoảng cách tới root** | §1.2, §6 | "Liên ngành" không có nghĩa là mọi nhánh cùng mức. Core Advanced, supporting Working–Intermediate, adjacent Basic–Working. Đây là cấu trúc, không phải thỏa hiệp |
| **Chiều sâu chứng minh qua project** | §10 | 7 project thay vì 20. Mỗi cái tích hợp nhiều nhánh và có tiêu chí nghiệm thu đo được |
| **1–2 nhánh Expert** | §2.2, §11.4 | Người liên ngành không có nhánh nào sâu thì không ai tin. Phải có ít nhất một chỗ bạn sâu hơn chuyên gia trung bình |

**Nói thẳng:** "đi trên nền của tất cả các mảng" chỉ có giá trị nếu *cái nền* đủ dày. Nền dày = core ở Advanced, không phải core ở Working. Đó là lý do §6 không hạ mục tiêu dù ngân sách giảm.

---

## 11.1 — Bốn hướng khả thi

| | **SC-A · Cloud AI Platform** | **SC-B · Edge-to-Cloud Systems** | **SC-C · Robotics / Autonomy** | **SC-D · ML Systems research-leaning** |
|---|---|---|---|---|
| **Main root thu hẹp thành** | Xây và vận hành hạ tầng cho sản phẩm AI | Xây hệ có vòng khép kín từ vật lý tới cloud | Xây máy tự hành an toàn | Nghiên cứu và cải thiện chính hệ ML |
| **Nhánh lên Expert** | C8, C10 | C8 hoặc C12 | C6, C7, S3 | C8, C3 |
| **Nhánh lên Advanced** | C9, C11, C1, C5 | C1, C5, C7, C10, C12, S3 | C4, C10, A1, S6 | C1, S1, C11 |
| **Gần như bỏ** | C6, C7, S2, S3 | Chiều sâu robotics, chiều sâu research | Chiều sâu cloud, chiều sâu data | C6, C7, C9, C10, S2 |
| **Khớp với vị trí hiện tại của bạn** | Thấp — phải bỏ toàn bộ vốn OT | **Rất cao — vị trí hiện tại phủ nửa khó nhất** | Trung bình | Không |
| **Khớp với đích liên ngành** | Một phần | **Đầy đủ** | Một phần | Không |
| **Mức độ đông đúc** | Cao | **Thấp** | Trung bình | Rất cao ở đỉnh |
| **Độ bền trước thay đổi công nghệ** | Trung bình | **Cao** — phần vật lý đổi chậm | Cao | Thấp |

---

## 11.2 — Khuyến nghị: SC-B, và bạn đã đứng ở nửa khó của nó

**[Recommendation — độ tin cậy cao]**

**SC-B · Edge-to-Cloud Intelligent Systems** vẫn là khuyến nghị. Nhưng lập luận đổi hoàn toàn so với v2.

Ở v2, SC-B được khuyến nghị **dù** nó chậm hơn SC-A tới việc làm, và tôi phải thiết kế một chiến lược sắp xếp lại thứ tự để bù. Bây giờ điều đó không còn cần:

> ### Bạn đang đứng ở nửa khó hơn của SC-B.
>
> SC-B có hai nửa. Nửa **IT** (phần mềm, cloud, ML, dữ liệu) tự học được — chậm nhưng có đầy đủ tài liệu, không cần thiết bị, không cần ai cho phép. Nửa **OT/vật lý** (cảm biến thật, điều khiển thật, an toàn thật, tích hợp đa bên thật) **gần như không tự học được** — nó cần hệ thống thật, hậu quả thật, và người chịu trách nhiệm thật.
>
> Bạn đang được trả tiền để học nửa thứ hai.
>
> Chiến lược v3 vì vậy đơn giản hơn v2 rất nhiều: **để công việc lo nửa OT, dồn toàn bộ ngân sách tự học vào nửa IT.**

Ba lý do phụ:

| Lý do | Lập luận |
|---|---|
| **Khớp với đích liên ngành** | SC-B là hướng duy nhất trong bốn hướng mà **cả hai thế giới đều nằm trong phạm vi**. Ba hướng kia đều yêu cầu bỏ một nửa |
| **EPC cho bề rộng** | Bạn thấy nhiều nhà máy, nhiều vendor, nhiều loại hệ trong vài năm — thay vì một hệ trong mười năm. Với đích liên ngành, đây là mô hình phơi nhiễm gần lý tưởng |
| **Vốn OT chuyển ngành được** | Hội tụ IT/OT không phải hiện tượng riêng của năng lượng. Nó xuất hiện ở sản xuất, hạ tầng, giao thông, nước, tòa nhà, logistics. Người biết cả hai thế giới đi sang ngành nào cũng được; người biết một thế giới thì không |

---

## 11.3 — Chọn SC-B thì mất gì — nói rõ

| Đánh đổi | Mức độ | Phòng ngừa |
|---|---|---|
| **Không sâu bằng chuyên gia từng tầng** | Chắc chắn xảy ra | Đây là **thiết kế**, không phải lỗi. Giá trị của bạn ở mối nối. Nếu bạn không tin luận điểm đó, đừng chọn SC-B |
| **Rủi ro "biết rộng mà nông"** | Thật, và là rủi ro chính của đích liên ngành | Ba cơ chế phòng vệ ở §11.0. Kiểm tra định kỳ: bạn có **ít nhất một nhánh** mà bạn sâu hơn chuyên gia trung bình không? |
| **Ngân sách tự học chỉ còn 3.600 h** | Thật | Expert 1–2 nhánh thay vì 2–3. Chấp nhận, hoặc tăng giờ, hoặc kéo dài timeline |
| **Thiếu cung `observe→adapt`** | Nghiêm trọng | Project cá nhân là nguồn duy nhất (§2.3c). P3 và P6 thành bắt buộc |
| **Vốn vendor Siemens/ABB không chuyển nhượng** | Thật | Thói quen dịch sang khái niệm trung lập (§2.3d). Làm hằng tuần, không để dồn |
| **Khó giải thích profile khi phỏng vấn** | Thật, và sẽ kéo dài | Chuẩn bị một câu: *"Tôi xây hệ thống nối thiết bị vật lý với hạ tầng phần mềm và mô hình học máy — và tôi debug được xuyên cả ba tầng."* Rồi chứng minh bằng P3 hoặc P6 |

---

## 11.4 — Điểm rẽ nhánh: tháng 24–30

**Dịch từ tháng 18–24 của v2** — vì bạn cần qua ít nhất một chu kỳ dự án EPC đầy đủ (thiết kế → thi công → chạy thử → bàn giao) trước khi có đủ bằng chứng.

Quyết định ở đây: **nhánh nào lên Expert.**

| Bằng chứng quan sát được | Chọn Expert ở | Hành động cụ thể |
|---|---|---|
| Bạn thấy phần thú vị nhất là *làm cho hệ thông minh hơn*; P3 hấp dẫn hơn P4; bạn thích eval và đo đạc | **C8 · ML & inference systems** | Tăng C8 lên ~500 h, giảm C10 và C11 xuống Intermediate–Advanced |
| Bạn thấy phần thú vị nhất là *làm cho nhiều hệ ghép được với nhau*; bạn hay là người giải thích giữa hai bên; bạn thích viết design doc | **C12 · Systems architecture** | Tăng C12 lên ~350 h, giữ C8 ở Advanced, tăng S8 và A4 |
| Bạn thấy công việc dạy bạn nhiều hơn tự học | **Để công việc quyết định** | Nhánh nào công ty dùng bạn nhiều nhất → đẩy lên Expert. Ít người dám chọn cách này và nó thường tối ưu |
| Không nhánh nào hấp dẫn sau 30 tháng | **Tín hiệu nghiêm trọng** | Không phải vấn đề kỷ luật. Xem lại §11.1 — có thể domain này không phải của bạn, và biết ở tháng 30 tốt hơn ở tháng 70 |

**Không chọn Expert ở C6, C7, S2, S3.** Lý do: công việc đang cấp chúng ở mức Advanced miễn phí. Dùng ngân sách tự học khan hiếm để đẩy chúng lên Expert là phân bổ sai — đó là mua thứ bạn đang được cho.

---

## 11.5 — Nếu bạn muốn chọn hướng khác

### Chọn SC-A · Cloud AI Platform
**Đổi gì:** bỏ C6, C7 xuống Awareness; bỏ S2, S3; C8 và C10 lên Expert; P3 thay bằng "feature store + training pipeline".
**Chi phí thật:** bạn vứt bỏ toàn bộ vốn OT đang được trả tiền để tích lũy. Chỉ hợp lý nếu bạn quyết định rời hẳn ngành công nghiệp.

### Chọn SC-C · Robotics
**Đổi gì:** A1 lên core Advanced; thêm kinematics, dynamics, motion planning ở Intermediate; S3 lên Advanced; C9, C10 xuống Working.
**Lưu ý:** vốn OT của bạn chuyển sang đây **tốt hơn** sang SC-A — điều khiển, an toàn, cảm biến, thời gian thực đều dùng lại được.

### Chọn SC-D · Research
**Roadmap này không phù hợp**, và vốn OT của bạn gần như không dùng được. Cần bằng cấp. Nếu đây là đích thật, nói ngay và tôi viết roadmap khác.

---

## 11.6 — Quyết định năm 3–5: ở lại EPC, hay chuyển sang nơi có vận hành

**[Không phải quyết định của hôm nay.** Bạn đang thử việc. Đưa vào đây để bạn biết nó tồn tại và thu thập bằng chứng dần.]

Ba mô hình công ty cho ba thứ khác nhau:

| Mô hình | Cho gì | Không cho gì |
|---|---|---|
| **Tổng thầu EPC** (hiện tại) | Bề rộng, tích hợp đa bên, commissioning, nhiều vendor, nhiều loại nhà máy | Vận hành dài hạn, `observe→adapt`, dữ liệu lịch sử nhiều năm |
| **Chủ đầu tư / IPP / nhà vận hành** | Vận hành dài hạn, dữ liệu nhiều năm, hậu quả của quyết định thiết kế, bài toán tối ưu thật | Bề rộng — thường chỉ một loại tài sản |
| **Công ty sản phẩm / nhà cung cấp giải pháp** | Chu kỳ phát triển phần mềm, thực hành kỹ thuật hiện đại, quy mô người dùng | Tiếp xúc trực tiếp với hiện tượng vật lý |

**Tín hiệu để cân nhắc chuyển** (không phải mệnh lệnh):
- Bạn đã qua ≥3 chu kỳ dự án EPC và bắt đầu thấy lặp lại
- P3 và P6 vẫn là nguồn kinh nghiệm vận hành **duy nhất** của bạn sau 3 năm
- Bạn đã đạt Advanced ở ≥4 nhánh core và cần môi trường dùng chúng
- Công ty không có đường cho bạn làm phần `learn/infer/adapt` dù bạn đã chứng minh được

**Tín hiệu để ở lại:**
- Công ty mở rộng sang O&M hoặc sang sản phẩm số (theo dõi chiến lược công ty)
- Bạn được giao phần hệ thống có quyền quyết định kiến trúc
- Bề rộng vẫn đang tăng — mỗi dự án vẫn dạy bạn thứ mới

**[Recommendation]** Đừng quyết định trước tháng 30. Trước đó, dữ liệu bạn có về chính mình còn quá ít.


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

# 13. TÀI NGUYÊN THEO THỨ TỰ HỌC

Ghi **tên tổ chức + tên tài nguyên**, không ghi URL (URL thay đổi; tên thì không). Một số thứ có thể đã đổi kể từ khi tôi kiểm tra (9/2026) — kiểm tra lại trước khi cam kết thời gian.

**Cách đọc bảng:** cột "Giờ" là ước lượng cho **mức độ sử dụng trong roadmap này**, không phải thời lượng đầy đủ của tài nguyên. Nhiều tài nguyên bạn chỉ dùng vài chương.

## 13.1 — Phase 0 · Bootstrap (~350 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | *The Missing Semester of Your CS Education* | MIT | môi trường | 15 | Shell, git, debugging — bắt đầu bằng cái này |
| 2 | *The C Programming Language* (K&R) | — | C1.1 | 40 | Làm hết bài tập, không đọc lướt |
| 3 | Python official tutorial + *Automate the Boring Stuff* | PSF / — | C1.2 | 30 | Đủ để viết script có test |
| 4 | *Beej's Guide to C* — miễn phí | — | C1.1 | 15 | Bổ sung cho K&R, hiện đại hơn |
| 5 | GDB tutorial + valgrind quickstart | GNU / — | C1.9 | 15 | **Không hoãn phần này** |
| 6 | *Pro Git* chương 1–3, 7 — miễn phí | — | C1.10 | 15 | Mô hình đối tượng ở chương 10 |
| 7 | Datasheet + getting-started của board bạn chọn | Espressif / ST / RPi | C6 | 40 | Primary source từ ngày đầu |
| 8 | *Mathematics for Computer Science* (6.042) chương 1–5 | MIT OCW | S1.1 | 40 | Logic, chứng minh, quy nạp |
| 9 | pytest documentation | — | C1.2 | 10 | |

## 13.2 — Phase 1 · Nền tính toán (~1.200 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | ***Nand2Tetris* phần 1** | Hebrew University of Jerusalem | C3.1–C3.3 | 70 | **ROI cao nhất của Phase 1.** Miễn phí trên trang chính thức và trên Coursera (audit) |
| 2 | *Computer Systems: A Programmer's Perspective* (CS:APP) + lab | CMU | C1.1, C1.4, C3.4–C3.6, C3.12 | 120 | Sách **đáng mua**; lab miễn phí và là phần giá trị nhất (Bomb, Attack, Cache, Malloc) |
| 3 | *Introduction to Algorithms* 6.006 | MIT OCW | C2.1–C2.9 | 90 | Làm problem set, không chỉ xem lecture |
| 4 | *Linear Algebra* 18.06 (Strang) | MIT OCW | S1.2 | 60 | Xem kèm *Essence of Linear Algebra* (3Blue1Brown) để có trực giác trước |
| 5 | *Essence of Linear Algebra* + *Essence of Calculus* | 3Blue1Brown | S1.2, S1.4 | 20 | Trực giác, không thay thế bài tập |
| 6 | *Mathematics for Computer Science* (6.042) phần còn lại | MIT OCW | S1.1 | 50 | Tổ hợp, đồ thị, xác suất rời rạc |
| 7 | *Modern C* (Jens Gustedt) — miễn phí | — | C1.1 | 30 | Chuẩn C hiện đại, UB, và cách viết C an toàn |
| 8 | *Operating Systems: Three Easy Pieces* (OSTEP) chương 1–20 — **miễn phí toàn văn** | University of Wisconsin–Madison | C4.1–C4.3 | 60 | Bắt đầu phần virtualization |
| 9 | *Algorithm Design Manual* (Skiena) — phần "war stories" | — | C2 | 20 | Nối lý thuyết với thực tế |
| 10 | *What Every Programmer Should Know About Memory* (Drepper) | — | C3.6, C2.11 | 15 | Dài nhưng đáng; đọc phần 1–5 |
| 11 | CMake tutorial + linker documentation | Kitware / GNU | C1.7 | 25 | Đủ để cross-compile |
| 12 | ARM Cortex-M Generic User Guide | ARM | C3.4, C6.1 | 25 | Primary source |
| 13 | RISC-V ISA specification (unprivileged) | RISC-V International | C3.4 | 15 | Đọc để so sánh với ARM |
| 14 | LeetCode / Codeforces | — | C2 | 60 | **Trần 80 h tổng cho cả roadmap** |

## 13.3 — Phase 2 · Nền hệ thống (~1.500 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | **OSTEP** chương 25–47 + project CS 537 | UW–Madison | C4.4–C4.9 | 120 | Concurrency và persistence; làm project |
| 2 | **CS144 + lab tự viết TCP** | Stanford | C5.1–C5.5, C5.10 | 120 | **Lab mạng giá trị nhất tồn tại công khai** |
| 3 | *Beej's Guide to Network Programming* — miễn phí | — | C5.10 | 10 | Đọc trước CS144 lab để khởi động |
| 4 | *Computer Networking: A Top-Down Approach* (Kurose & Ross) | — | C5 | 40 | Tham chiếu nền |
| 5 | *Database Systems* 15-445 | CMU Database Group | C9.1–C9.4 | 90 | Chất lượng cao bất thường; làm project |
| 6 | *The Linux Programming Interface* (Kerrisk) | — | C4.9, C4.12 | 40 | Tra cứu, không đọc tuần tự |
| 7 | *Probabilistic Systems Analysis* 6.041 | MIT OCW | S1.3 | 60 | Hoặc *Introduction to Probability* (Blitzstein, Harvard — miễn phí) |
| 8 | *An Introduction to Statistical Learning* — miễn phí | — | C8.1, C8.2 | 40 | Nền thống kê học; đọc trước mọi deep learning |
| 9 | *Designing Data-Intensive Applications* phần I | — | C9.1, C9.3 | 25 | **Đáng mua** |
| 10 | PostgreSQL documentation | PostgreSQL Global Dev Group | C9.2, C9.3 | 30 | Primary source |
| 11 | *Use The Index, Luke* — miễn phí | — | C9.2 | 15 | Index và query plan |
| 12 | *Fluent Python* | — | C1.2 | 30 | Python ở mức Advanced |
| 13 | RFC 9293 (TCP), RFC 9110–9114 (HTTP) | IETF | C5.5, C5.7 | 25 | Primary source; đọc khi cần chi tiết |
| 14 | Wireshark documentation + sample capture | Wireshark Foundation | C5.12 | 20 | |
| 15 | OpenTelemetry documentation | CNCF | C11.2 | 25 | Mô hình quan trọng hơn công cụ |
| 16 | *A Philosophy of Software Design* (Ousterhout) | — | C1.12, C12.3 | 15 | Ngắn, mật độ cao |
| 17 | Google *Technical Writing* courses — miễn phí | Google | S8 | 15 | |
| 18 | Reference manual của MCU bạn chọn | ST / Espressif / Nordic | C6.1–C6.3 | 60 | **Đọc nhiều nhất trong Phase 2 cho C6** |
| 19 | *The Scientist and Engineer's Guide to DSP* (Smith) chương 1–9 — **miễn phí** | — | C7.1, C7.2 | 30 | Lấy mẫu và aliasing trước mọi việc đọc cảm biến |

## 13.4 — Phase 3 · Vòng lặp khép lại (~1.600 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | FreeRTOS documentation + *Mastering the FreeRTOS Kernel* — miễn phí | FreeRTOS | C4.10, C6.7 | 35 | |
| 2 | Zephyr Project documentation | Zephyr Project / Linux Foundation | C6.7, C6.8, C6.12 | 35 | Mô hình khác FreeRTOS; đáng biết cả hai |
| 3 | *Making Embedded Systems* (White) | — | C6.12 | 20 | Kiến trúc firmware |
| 4 | *Test-Driven Development for Embedded C* (Grenning) | — | C6.12, S5.3 | 25 | Cách test firmware trên host |
| 5 | MCUboot documentation | MCUboot project | C6.10 | 20 | Bootloader và OTA |
| 6 | *The Scientist and Engineer's Guide to DSP* phần còn lại | — | C7.3, C7.4 | 20 | Lọc và FFT |
| 7 | *Understanding Digital Signal Processing* (Lyons) | — | C7.3, C7.4 | 30 | Sâu hơn Smith |
| 8 | CMSIS-DSP documentation | ARM | C7.3, C7.4 | 15 | DSP trên Cortex-M |
| 9 | Application note về nhiễu, nối đất, nguồn | Texas Instruments, Analog Devices | S2.3, S2.5, C7.5 | 30 | **Chất lượng rất cao, miễn phí** |
| 10 | *The Art of Electronics* chương 1, 8, 9 | — | S2.1, S2.6 | 25 | Tra cứu |
| 11 | *Kalman and Bayesian Filters in Python* (Labbe) — **miễn phí** | — | C7.8 | 30 | Notebook chạy được |
| 12 | *Feedback Systems* (Åström & Murray) — **miễn phí** | Caltech | S3, C7.12 | 30 | |
| 13 | Series "từ zero" của Andrej Karpathy | — | C8.4, C8.5 | 60 | **Đúng tinh thần §1.1**: micrograd → makemore → nanoGPT |
| 14 | *Practical Deep Learning for Coders* | fast.ai | C8.4, C8.7 | 50 | Vào nhanh, engineering-first |
| 15 | CS231n | Stanford | C8.5 | 45 | Thị giác |
| 16 | *Designing Data-Intensive Applications* phần II | — | C10.3, C10.4, C10.6 | 30 | |
| 17 | *Distributed Systems* lecture series (Kleppmann) — miễn phí | University of Cambridge | C10.2, C10.3 | 35 | |
| 18 | MQTT 5.0 specification | OASIS | C5.8 | 12 | Primary source |
| 19 | Paper Gorilla (nén chuỗi thời gian) | — | C9.5 | 8 | Primary source |
| 20 | TimescaleDB / ClickHouse / Prometheus TSDB docs | vendor | C9.5 | 25 | So sánh ba mô hình |
| 21 | Kafka documentation + *Kafka: The Definitive Guide* | Apache / — | C9.9 | 35 | |
| 22 | *Systems Performance* (Gregg) chương 1–6 | — | C11.1, C11.4, C11.6 | 30 | |
| 23 | *TinyML* (Warden & Situnayake) | — | C6.14, C7.10, C8.9 | 40 | |
| 24 | TensorFlow Lite Micro documentation | Google | C6.14 | 20 | |
| 25 | Edge Impulse documentation | Edge Impulse | C6.14 | 20 | Học workflow, rồi **tự dựng lại bằng tay** |
| 26 | Edge AI Foundation — tài liệu và talk công khai | Edge AI Foundation | C6.14 | 15 | Trạng thái hiện tại của lĩnh vực |
| 27 | *The Rust Book* **hoặc** *A Tour of Go* + *Effective Go* | Rust / Go teams | C1.3 | 60 | Chọn một |
| 28 | Datasheet + AN của mọi cảm biến bạn dùng | vendor | C7.6, C7.7 | 30 | Primary source |
| 29 | NIST — tài liệu về bất định đo | NIST | C7.7 | 15 | |

## 13.5 — Phase 4 · Quy mô & production (~1.500 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | ***Distributed Systems* 6.824 + lab Raft** | MIT | C10.1–C10.5 | 110 | Lab Raft là chuẩn vàng |
| 2 | Paper Raft (*In Search of an Understandable Consensus Algorithm*) | — | C10.5 | 10 | Primary source |
| 3 | *Site Reliability Engineering* + *SRE Workbook* — **miễn phí toàn văn** | Google | C11.3, C11.9, C11.11, C10.10 | 45 | Đọc chương SLO trước |
| 4 | *Systems Performance* (Gregg) phần còn lại | — | C11.6, C11.7 | 25 | |
| 5 | *BPF Performance Tools* (Gregg) | — | C4.13, C11.6 | 25 | |
| 6 | *Release It!* (Nygard) | — | C10.10, C11.12 | 20 | Mẫu ổn định |
| 7 | Kubernetes documentation — phần Concepts | CNCF | C10.12 | 35 | **Bỏ qua tutorial cho tới khi hiểu Concepts** |
| 8 | *Programming Kubernetes* hoặc kubebuilder book | — | C10.12 | 25 | Viết controller |
| 9 | OpenTofu / Terraform documentation | OpenTofu / HashiCorp | C10.13 | 25 | Mô hình giống nhau ở cả hai |
| 10 | vLLM documentation + blog kỹ thuật | vLLM project | C8.10 | 30 | **Primary source cho serving** |
| 11 | Paper PagedAttention | — | C8.10 | 8 | |
| 12 | Paper FlashAttention | — | C8.5, C8.10 | 8 | |
| 13 | Paper LoRA, AWQ, GPTQ | — | C8.8, C8.9 | 15 | |
| 14 | CUDA Programming Guide | NVIDIA | C3.9 | 30 | |
| 15 | *Programming Massively Parallel Processors* | — | C3.9 | 25 | |
| 16 | CS336 *Language Modeling from Scratch* | Stanford | C8.5, C8.10 | 50 | |
| 17 | CS224n | Stanford | C8.5 | 45 | Ngôn ngữ |
| 18 | *Designing Machine Learning Systems* (Chip Huyen) | — | C8.14, C8.15, C8.16 | 25 | |
| 19 | MCP specification | Linux Foundation | C8.11 | 10 | Primary source |
| 20 | LangGraph documentation | LangChain | C8.12 | 20 | **Trần cứng 20 h** |
| 21 | *Building Secure and Reliable Systems* — miễn phí | Google | S4, C12.14 | 25 | |
| 22 | OWASP Top 10 + OWASP LLM Top 10 | OWASP | S4.7 | 15 | |
| 23 | *Security Engineering* (Ross Anderson) — **miễn phí bản 3** | — | S4 | 25 | Chọn chương |
| 24 | NASA Fault Tree Handbook — miễn phí | NASA | S6.2 | 15 | |
| 25 | *Quantitative System Performance* — miễn phí | — | S7, C11.5 | 20 | |
| 26 | Bài viết Jepsen (Kyle Kingsbury) | Jepsen | C10.3, C10.4 | 20 | Kiểm chứng thực nghiệm các tuyên bố về nhất quán |
| 27 | Postmortem công khai (Google, Cloudflare, GitHub, AWS) | các công ty | C11.9 | 25 | **Đọc ≥20 cái** |
| 28 | Parquet + Arrow specification | Apache | C9.6 | 15 | |
| 29 | Paper HNSW | — | C9.8 | 8 | |
| 30 | ROS 2 documentation | Open Robotics | A1.1 | 30 | |
| 31 | *Ironies of Automation* (Bainbridge) | — | A3.2 | 3 | Ngắn, kinh điển, đọc được trong một buổi |

## 13.6 — Phase 5 · Kiến trúc & chuyên sâu (~1.450 h)

| Thứ tự | Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|---|
| 1 | *Software Architecture in Practice* (Bass, Clements, Kazman) | SEI / Carnegie Mellon | C12.1, C12.2 | 35 | |
| 2 | *Fundamentals of Software Architecture* (Richards & Ford) | — | C12.8 | 25 | |
| 3 | *Designing Data-Intensive Applications* phần III | — | C12.9 | 20 | |
| 4 | Mô hình C4 — tài liệu Simon Brown | — | C12.12, S8.3 | 10 | |
| 5 | Bài gốc về ADR (Michael Nygard) + kho mẫu ADR | — | C12.12, S8.2 | 10 | |
| 6 | Design doc và RFC công khai (Rust RFC, Kubernetes KEP, IETF) | — | S8.1 | 25 | **Đọc ≥15 cái** để thấy cấu trúc tốt |
| 7 | *Engineering a Safer World* (Leveson) | MIT | S6, A3 | 30 | STAMP — tiếp cận khác biệt và đáng đọc |
| 8 | IEC 60812 (FMEA) hoặc hướng dẫn công khai tương đương | IEC / — | C12.5, S6.2 | 15 | |
| 9 | *Normal Accidents* (Perrow) | — | S6 | 20 | Trực giác về lỗi trong hệ phức tạp |
| 10 | Báo cáo điều tra tai nạn (NTSB, hàng không) | NTSB | S6, A3.2 | 20 | Nguồn học tập chất lượng rất cao về failure analysis |
| 11 | *Is Parallel Programming Hard* (McKenney) — miễn phí | — | C4.6, C4.7 | 30 | Nâng cao |
| 12 | Văn bản EU AI Act + GDPR (phần liên quan) | EU | A5.1, A5.2 | 20 | Primary source |
| 13 | Nghị định bảo vệ dữ liệu cá nhân của Việt Nam | Chính phủ VN | A5.2 | 10 | |
| 14 | choosealicense.com + SPDX license list + OSI | — | A6.1 | 10 | |
| 15 | Source code của một dự án bạn chọn để đóng góp | — | P7b, C1.11 | 100+ | Đây là "tài nguyên" chính của Phase 5 |
| 16 | *The Art of Capacity Planning* (Allspaw) | — | S7.2 | 15 | |
| 17 | *Accelerate* (Forsgren, Humble, Kim) | — | A4 | 12 | |
| 18 | *The Goal* (Goldratt) | — | A4.1 | 12 | Tiểu thuyết về lý thuyết ràng buộc |

## 13.6b — Tài nguyên cho tầng công nghiệp (OT)

*Bổ sung ở v3, phục vụ các leaf mới C5.16, C6.16, S3.8, S4.9, C12.15. Phần lớn học được **tại công việc**; danh sách này để bạn học có hệ thống thay vì học ngẫu nhiên theo dự án được giao.*

| Tài nguyên | Tổ chức | Nhánh | Giờ | Ghi chú |
|---|---|---|---|---|
| Tài liệu chính thức TIA Portal / STEP 7 | Siemens | C6.16 | 40 | **Primary source.** Đọc phần kiến trúc hệ thống, không chỉ phần thao tác |
| Tài liệu ABB 800xA hoặc AC500 | ABB | C6.16 | 30 | Tùy hệ bạn gặp |
| IEC 61131-3 — chuẩn hoặc tài liệu diễn giải | IEC / PLCopen | C6.16 | 20 | Ngôn ngữ lập trình PLC, vendor-neutral |
| PLCopen — tài liệu công khai | PLCopen | C6.16 | 15 | Khối chức năng chuẩn hóa, motion control |
| Modbus Application Protocol Specification | Modbus Organization | C5.16 | 8 | Ngắn, đọc hết được. Primary source |
| IEC 61850 — tài liệu giới thiệu và SCL | IEC / vendor | C5.16 | 30 | Mô hình dữ liệu phân cấp là phần đáng học nhất |
| IEC 60870-5-104 / DNP3 — tài liệu kỹ thuật | IEC / DNP Users Group | C5.16 | 15 | Telemetry SCADA |
| OPC UA specification + companion spec | OPC Foundation | C5.16, C12.15 | 30 | **Cầu nối IT/OT quan trọng nhất.** Đọc phần information model |
| Profinet / Profibus — tài liệu kỹ thuật | PI (Profibus & Profinet International) | C5.16 | 20 | |
| *Process Dynamics and Control* (Seborg et al.) | — | S3.8 | 35 | Sách chuẩn cho điều khiển quá trình công nghiệp |
| *Practical Process Control* (Blevins/Nixon) hoặc tương đương | — | S3.8 | 20 | Thực hành hơn Seborg |
| ISA-95 / IEC 62264 — tài liệu giới thiệu | ISA / IEC | C12.15 | 20 | |
| IEC 62443 — tài liệu giới thiệu và hướng dẫn | IEC / ISA | S4.9 | 25 | An ninh hệ điều khiển công nghiệp |
| CISA — hướng dẫn công khai về ICS security | CISA | S4.9 | 15 | Miễn phí, chất lượng cao |
| Grid code Việt Nam và thông tư đấu nối | Bộ Công Thương / EVN | S3.8, A5 | 15 | Ràng buộc pháp lý định hình kiến trúc điều khiển |
| Tài liệu inverter / turbine của nhà sản xuất | vendor | C7, S3.8 | 30 | Primary source cho hệ bạn thực sự gặp |
| *The Unified Namespace* — tài liệu và thảo luận công khai | cộng đồng IIoT | C12.15 | 10 | Xu hướng đang định hình lại ISA-95 |

**[Recommendation] về cách dùng danh mục này:** đừng đọc trước. Đọc **ngay sau** khi gặp thứ đó ở công việc — đó là lúc bạn có ngữ cảnh để hiểu, và là lúc kiến thức dính lại. Với mỗi tài nguyên, viết ra bảng ánh xạ sang khái niệm trung lập (§2.3d). Ngân sách: ~380 h, rải đều 5 năm, **phần lớn trong giờ làm việc**.

---


## 13.7 — Tài nguyên tra cứu suốt 5 năm

| Tài nguyên | Dùng cho |
|---|---|
| Linux man pages (mục 2, 3, 7) | C1, C4 — tra hàng ngày |
| Datasheet, reference manual, errata, application note của vendor | C6, C7, S2 — **primary source quan trọng nhất của nhánh phần cứng** |
| RFC (IETF) | C5 — khi cần chi tiết chính xác |
| Documentation chính thức của mọi công cụ bạn dùng | Luôn đọc trước blog post |
| CLRS (*Introduction to Algorithms*) | C2 — tra cứu, không đọc tuần tự |
| *Computer Architecture: A Quantitative Approach* (Hennessy & Patterson) | C3 — tra cứu |

## 13.8 — Về tài nguyên trả phí

Chỉ **ba** thứ tôi cho là đáng trả tiền, và không thứ nào bắt buộc:

| # | Thứ | Vì sao | Chi phí ước tính |
|---|---|---|---|
| 1 | *Designing Data-Intensive Applications* | Khó thay thế bằng nguồn miễn phí; mật độ kiến thức cao nhất trong danh mục | ~1tr VND |
| 2 | *Computer Systems: A Programmer's Perspective* | Lab miễn phí nhưng sách làm chúng dễ tiêu hóa hơn nhiều | ~1,5tr VND |
| 3 | **Phần cứng** (Phụ lục A) | ROI cao nhất trong toàn bộ roadmap | 8–15tr VND rải 5 năm |

Cộng thêm, tùy tình huống: **thuê GPU theo giờ** (§0.2), ước tính 3–8tr VND tổng cho Phase 1–4 nếu có kỷ luật bật/tắt.

**Certification:** [Recommendation] không mua trong 2 năm đầu. Cân nhắc lại ở Phase 4, và **chỉ khi** một nhà tuyển dụng cụ thể yêu cầu tên cụ thể.

**Khóa học trả phí trên các nền tảng thương mại:** [Recommendation] không. Mọi thứ trong danh mục trên đều có chất lượng cao hơn, và phần lớn miễn phí. Ngoại lệ duy nhất đáng cân nhắc: một khóa có **phòng lab phần cứng thật** mà bạn không tự dựng được.

## 13.9 — Cách dùng tài nguyên — ba quy tắc

1. **Primary source trước blog post.** Datasheet, RFC, specification, documentation chính thức. Blog post để hiểu nhanh; primary source để hiểu đúng. Với nhánh phần cứng, tỷ lệ này nghiêng hẳn về primary source.

2. **Một tài nguyên một lúc cho mỗi nhánh.** Đọc song song ba cuốn về cùng một chủ đề cho cảm giác bận rộn và kết quả nông. Chọn một, làm hết bài tập, rồi chuyển.

3. **Tài nguyên không có bài tập thì không tính là đã học.** Với mọi tài nguyên trong danh mục, tìm bài tập — có sẵn, hoặc bạn tự đặt ra bằng cách lấy checkpoint ở §5 làm đề.

---

# 14. 90 NGÀY ĐẦU

Việc cụ thể, không phải "đọc về X". Mục tiêu của 90 ngày: **hoàn thành Phase 0 và bước vào Phase 1 với đà**.

Ngân sách: 25–30 h/tuần ≈ **330–390 h** trong 90 ngày.

## 14.1 — Tuần 1 (ngày 1–7)

| Ngày | Việc | Giờ | Xong khi |
|---|---|---|---|
| **1** | Cài Linux (dual boot hoặc WSL2). Dựng dotfiles, terminal, editor. Học 20 lệnh shell **bằng cách dùng chúng**. Xem *The Missing Semester* bài 1–2. | 5 | Bạn điều hướng và sửa file mà không rời terminal |
| **2** | Chương trình C đầu tiên: đọc file text, đếm tần suất từ, in top 10. Không thư viện ngoài. Chạy qua `gdb` một lần, `valgrind` một lần. | 5 | Chạy đúng và valgrind báo sạch |
| **3** | **Đặt mua phần cứng** (Phụ lục A, gói khởi động). Trong lúc chờ: cài toolchain cho MCU, build và chạy blink trên simulator hoặc QEMU. | 5 | Đơn đã đặt; toolchain build được binary |
| **4** | Git: mô hình đối tượng, tạo repo public, commit công việc ngày 2. Viết README mô tả **bạn học được gì**, không phải bạn làm gì. | 4 | Repo có ≥3 commit với message nghĩa lý |
| **5** | **Nand2Tetris project 1** — cổng logic cơ bản từ NAND. | 6 | Toàn bộ test project 1 pass |
| **6** | Python: script đọc CSV, tính thống kê, vẽ biểu đồ, lưu SQLite. Có `pytest` với ≥3 test. | 5 | Test pass; script chạy từ dòng lệnh với tham số |
| **7** | Viết **một trang**: mục tiêu 90 ngày, giờ cam kết mỗi tuần, và checkpoint bạn dùng để tự kiểm ở ngày 90. Mở file STATE ở §16 và điền lần đầu. | 3 | Một trang tồn tại, có số, có ngày, **không có từ "sẽ cố gắng"** |

## 14.2 — Tuần 2–4 (ngày 8–30) — ~90 h

| Khối | Nội dung | Giờ | Xong khi |
|---|---|---|---|
| C — con trỏ và bộ nhớ | K&R chương 5–6. Tự cài: dynamic array, linked list, hash table đơn giản. Mỗi cái có test và chạy sạch dưới sanitizer. | 30 | Ba cấu trúc chạy sạch dưới ASAN + valgrind; bạn giải thích được padding của mỗi struct |
| Nand2Tetris project 2–3 | ALU, thanh ghi, bộ nhớ | 18 | Test pass |
| Phần cứng về → blink thật | Nạp firmware **tự build**, không dùng IDE. Đọc GPIO section của reference manual. | 12 | LED chớp bằng code bạn hiểu từng dòng, cấu hình bằng register hoặc HAL thật |
| Đọc cảm biến I²C | Đọc datasheet cảm biến, viết driver tối giản, in giá trị qua UART | 15 | Giá trị hợp lý, xác nhận bằng thay đổi môi trường vật lý |
| Toán — logic và chứng minh | 6.042 chương 1–3: logic, chứng minh, quy nạp | 12 | Giải được bài tập cuối chương, viết chứng minh đầy đủ |
| Shell + tooling | *Missing Semester* bài 3–6: scripting, công cụ, debugging, metaprogramming | 8 | Bạn viết được script tự động hóa một việc bạn làm lặp lại |

**Checkpoint ngày 30:**
- [ ] Ba cấu trúc dữ liệu tự cài, sạch dưới sanitizer
- [ ] Nand2Tetris project 1–3 pass
- [ ] Cảm biến đọc được, giá trị hợp lý, driver do bạn viết
- [ ] Bạn dùng `gdb` để tìm một bug mà không cần thêm `printf`

## 14.3 — Tháng 2 (ngày 31–60) — ~120 h

| Khối | Nội dung | Giờ | Xong khi |
|---|---|---|---|
| **P1 — xây thật** | Sensor node → UART/Wi-Fi → script → SQLite → đồ thị. Theo đặc tả §10 P1. | 40 | M1–M5 của P1 hoàn thành |
| Nand2Tetris project 4–5 | Assembly, kiến trúc máy tính, CPU hoàn chỉnh | 25 | CPU chạy được chương trình assembly |
| C nâng cao | *Modern C*: UB, `const`/`volatile`/`restrict`, struct layout, preprocessor | 20 | Bạn liệt kê được 10 loại UB hay gặp và giải thích compiler khai thác chúng thế nào |
| Python lên mức package | Chuyển script của P1 thành package có `pyproject.toml`, test, type hints, CLI | 15 | `pip install .` chạy được từ repo sạch; `mypy` pass |
| Toán — tổ hợp và đồ thị | 6.042 chương 4–5 | 12 | Bài tập |
| Build system | `make`/`CMake`, cross-compile cho ARM từ x86 | 8 | Cross-compile thành công, binary chạy trên board |

**Checkpoint ngày 60:**
- [ ] P1 chạy 6 giờ liên tục, dữ liệu đầy đủ
- [ ] Nand2Tetris phần 1 hoàn thành (project 1–5)
- [ ] Package Python cài được và pass `mypy --strict`
- [ ] Cross-compile hoạt động, bạn giải thích được linker script

## 14.4 — Tháng 3 (ngày 61–90) — ~120 h

| Khối | Nội dung | Giờ | Xong khi |
|---|---|---|---|
| **P1 — hoàn thiện và nghiệm thu** | Chạy 6 h, viết README, dựng lại từ đầu trong một buổi | 20 | Toàn bộ tiêu chí nghiệm thu P1 tick |
| Nand2Tetris project 6 | Assembler | 15 | Assembler chạy được, dịch đúng chương trình test |
| CS:APP khởi động | Chương 1–3: biểu diễn thông tin, biểu diễn số, assembly cơ bản | 30 | Làm Data Lab và Bomb Lab (hoặc ít nhất một trong hai) |
| DSA khởi động | 6.006 bài 1–6: độ phức tạp, mảng, sắp xếp, cây | 25 | Problem set 1–2 |
| Đại số tuyến tính khởi động | *Essence of Linear Algebra* (toàn bộ) + 18.06 bài 1–5 | 20 | Bạn giải thích được nhân ma trận bằng cả hai cách: hàng-cột và tổ hợp tuyến tính |
| Đọc datasheet có hệ thống | Chọn một peripheral bạn **chưa dùng** (bộ so sánh, RTC, watchdog), cấu hình chỉ bằng reference manual | 10 | Peripheral hoạt động, không copy ví dụ |

## 14.5 — Nghiệm thu ngày 90 — tiêu chí chuyển sang Phase 1 đầy đủ

**Bắt buộc (không đạt thì lặp lại tháng 3, không đi tiếp):**
- [ ] **P1 hoàn thành** theo toàn bộ tiêu chí nghiệm thu ở §10
- [ ] Bạn **dựng lại P1 từ đầu trong một buổi**, không copy-paste
- [ ] Nand2Tetris phần 1 hoàn thành (project 1–6)
- [ ] Ba cấu trúc dữ liệu tự cài bằng C, sạch dưới sanitizer
- [ ] Bạn cấu hình được một peripheral lạ **chỉ bằng datasheet**
- [ ] Bạn dùng `gdb` như công cụ đầu tiên khi có bug, không phải `printf`

**Nên có:**
- [ ] Repo public với ≥4 commit mỗi tuần, message có nghĩa
- [ ] File STATE (§16) được cập nhật hàng tuần
- [ ] Bạn đã viết ≥1 ghi chú kỹ thuật giải thích một thứ bạn học cho người khác

**Tín hiệu cảnh báo — nếu thấy, dừng và đọc lại §0.3:**
- Giờ thực tế dưới 15 h/tuần trong ≥4 tuần liên tiếp
- Bạn tránh né nhánh phần cứng và chỉ làm phần mềm (hoặc ngược lại)
- Bạn học nhiều mà không xây gì trong 3 tuần liền
- Bạn thấy chán chứ không thấy khó — **hai thứ này khác nhau, và cái đầu nghiêm trọng hơn**

## 14.6 — Nhịp hàng tuần, áp dụng suốt 5 năm

| Ngày | Việc | Giờ điển hình |
|---|---|---|
| Thứ 2–6 | 2 khối sâu × 2 h, hoặc 1 khối × 4 h | 3–4 h/ngày |
| Thứ 7 | Khối dài cho project (phần cứng cần thời gian liên tục) | 6–8 h |
| Chủ nhật | Ôn, viết ghi chú, cập nhật STATE, lập kế hoạch tuần | 2–3 h |

**Ba quy tắc nhịp độ:**
1. **Khối sâu tối thiểu 90 phút** cho việc học khái niệm mới. Dưới mức đó là đọc, không phải học.
2. **Luôn có một project đang chạy song song** với việc học nhánh. Học thuần lý thuyết quá 3 tuần là dấu hiệu sắp bỏ cuộc.
3. **Chủ nhật viết lại một thứ bạn học trong tuần bằng lời của bạn.** Nếu không viết ra được, bạn chưa hiểu.

---

# 15. COVERAGE AUDIT

## 15.1 — Xác nhận độ phủ

| Kiểm tra | Trạng thái |
|---|---|
| 26 họ lĩnh vực bắt buộc ở §5 của prompt được gán nhãn | ✓ Đầy đủ, §3.1 |
| Lĩnh vực bổ sung ngoài 26 | ✓ 12 lĩnh vực, §3.2 |
| Nhãn "không liên quan" có lý do | ✓ §3.3, xử lý ở tầng sub-part vì không họ nào hoàn toàn không liên quan |
| Mỗi nhánh core có ≥8 leaf | ✓ Thực tế 12–16 leaf mỗi nhánh |
| Mỗi leaf core có mức + mục đích + checkpoint | ✓ |
| Sub-leaf ở chỗ cần | ✓ Mọi leaf core có sub-leaves |
| Nhánh supporting 5–10 leaf | ✓ 5–9 leaf mỗi nhánh |
| Nhánh adjacent 3–6 leaf | ✓ 4–5 leaf mỗi nhánh |
| Peripheral chỉ tên + 1 dòng lý do | ✓ §5.4, cộng thêm cột "kích hoạt xem lại khi nào" |
| Mục 1–6, 9, 12 đầy đủ, không nén | ✓ |
| **Không nhánh nào còn nhãn `[đã nén]`** | ✓ — khác với bản v1 |
| Không nhánh nào mở đầu bằng tên framework | ✓ |
| Dependency graph chỉ vẽ dependency chặn thật | ✓ §4.1, cộng 3 mối nối chi tiết ở §4.2 và bảng "dependency tưởng tượng" ở §4.3 |
| Tài nguyên ghi tên tổ chức + tên, không bịa URL | ✓ §13 |
| Có mục "chủ động bỏ qua" | ✓ §12, cộng quy tắc quyết định cho thứ mới |
| Nhãn Fact / Inference / Recommendation / Không chắc | ✓ Dùng xuyên suốt |
| STATE block dán lại được | ✓ §16.3 |
| **v3: giữ nguyên 38 lĩnh vực sau khi hiệu chỉnh tình huống** | ✓ §0.1 — nhãn không đổi, chỉ đổi trình tự và giờ |
| **v3: lấp lỗ hổng độ phủ tầng công nghiệp** | ✓ C5.16, C6.16, S3.8, S4.9, C12.15 — 5 leaf mới |
| **v3: phân tách giờ tự học và giờ công việc** | ✓ §3.5, Phụ lục B, Phụ lục D |

## 15.2 — Những gì tôi đã cân nhắc rồi cố ý loại

| Đã loại | Lý do |
|---|---|
| **Tầng robotics thật** (kinematics, dynamics, motion planning, SLAM ở độ sâu implement) | Là một spine riêng, không phải phần mở rộng. Thêm vào sẽ làm loãng cả hai. §11.5 nêu cách chuyển nếu bạn đổi ý |
| **MLOps như một hạng mục riêng** | Đã tách vào C9 (pipeline), C8.13–C8.14 (eval, drift), C11 (observability), C10.13 (IaC). Nhãn "MLOps" đóng gói và **che mất các dependency thật** — đó là lý do tôi từ chối dùng nó làm nhánh |
| **"Platform engineering" như một nhánh** | Cùng lý do: nó là tổ hợp của C10 + C11 + C1.7, không phải một body of knowledge riêng |
| **Product management, thiết kế sản phẩm** | Có liên quan thật nhưng chi phí cơ hội cao trong 5 năm đầu. A4 đã bao phần giao với kỹ thuật |
| **Một cloud vendor cụ thể theo chiều sâu** | Cố ý giữ ở mức khái niệm để tránh vi phạm nguyên tắc "không phụ thuộc mạnh vào một vendor" |
| **Kỹ năng phỏng vấn như một nhánh** | Đã nhúng vào C2 (thuật toán), C12 (system design), S8 (trình bày). Tách ra thành nhánh riêng sẽ khuyến khích học để thi thay vì học để làm |
| **Soft skills, networking nghề nghiệp** | Ngoài phạm vi của một roadmap kiến thức. S8 bao phần giao với kỹ thuật (viết, trình bày đánh đổi, design review) |

## 15.3 — Những chỗ tôi không chắc

**[Không chắc]** — liệt kê theo mức độ ảnh hưởng tới quyết định của bạn:

| # | Điều không chắc | Mức ảnh hưởng | Cách bạn tự kiểm |
|---|---|---|---|
| 1 | **Mốc "đi làm từ tháng 12–15"** | **Cao nhất** | Đây là khuyến nghị mạnh nhất trong tài liệu và cũng là khuyến nghị tôi có ít bằng chứng trực tiếp nhất. Nó dựa trên lập luận về *loại* kiến thức không tự học được, không dựa trên nghiên cứu về người tự học. Tự kiểm: ở tháng 10, thử phỏng vấn 3 nơi và xem phản hồi |
| 2 | **Luận điểm thị trường Việt Nam ở §11.2** | Cao | Là inference từ cơ cấu công nghiệp, **không phải** từ dữ liệu tuyển dụng Việt Nam mà tôi đã kiểm chứng. Tự kiểm: khảo sát tin tuyển dụng thật trong 2 tuần, đếm số vị trí yêu cầu cả embedded lẫn cloud |
| 3 | **Ngân sách giờ cho từng phase** | Trung bình | Ước lượng từ cấu trúc kiến thức, không từ dữ liệu người học thật. Khả năng cao Phase 1 tốn nhiều hơn tôi ghi (lời nguyền kiến thức: tôi ước lượng thấp cái tôi đã biết) và Phase 4 tốn ít hơn |
| 4 | **Mức Expert khả thi ở 2–3 nhánh** | Trung bình | Dựa trên ngân sách 6.600 h và giả định bạn đi làm đúng nhánh. Nếu công việc lệch khỏi spine, con số này có thể là 1–2 |
| 5 | **Độ bền của tầng agentic/LLM tooling (§8, tầng 4)** | Trung bình, nhưng **chắc chắn sẽ cũ** | Mọi thứ ở tầng 4 và 5 nên được coi là **ảnh chụp tháng 9/2026**, không phải kết luận. Kiểm tra lại mỗi 6 tháng |
| 6 | **C6 đạt được Expert** | Trung bình | Embedded có vòng phản hồi chặt nên tôi tin là khả thi, nhưng nó cũng có bề rộng lớn (mỗi họ MCU là một hệ sinh thái). Có thể thực tế là "Expert trên một họ MCU, Advanced trên phần còn lại" |
| 7 | **Tỷ lệ 75–80% software/infra trong 20 tháng đầu** | Thấp–trung bình | Con số này là phán đoán, không phải tính toán. Nếu bạn thấy nó làm nhánh edge chết yểu, tăng lên 30–35% |
| 8 | **Thời gian cho từng project ở §10** | Thấp | Con số này là phán đoán. P6 ở mức 250 h tự học có thể thiếu 1,5–2× |
| 9 | **[v3] Giờ công việc quy đổi ~2.100 h** | **Cao** | Đây là ước lượng yếu nhất trong bản v3. Nó giả định công việc cho kỹ thuật thật chứ không chủ yếu giấy tờ và giám sát nhà thầu. **Tự kiểm ở tháng 12:** đối chiếu cột "công việc" ở Phụ lục D với nhật ký thực tế |
| 10 | **[v3] Tự học 12–18 h/tuần bền được trong 5–6 năm** | **Cao** | Vừa đi làm vừa tự học ở cường độ này trong 6 năm là yêu cầu lớn. Đợt thi công công trường có thể làm nó về 0 trong nhiều tuần |
| 11 | **[v3] Công việc sẽ cấp C7/S2/S3 ở mức Advanced** | Trung bình | Phụ thuộc bạn được giao việc kỹ thuật hay việc quản lý. Nếu lệch sang quản lý, ba nhánh này phải quay lại ngân sách tự học |

## 15.4 — Mâu thuẫn cố ý trong tài liệu

Có **hai mâu thuẫn** tôi để lại có chủ đích. Nêu ra để bạn không nghĩ đó là lỗi:

**(1) §2.2 nói "Advanced ở 7–9 nhánh", §6 đặt mục tiêu Advanced ở 12 nhánh core.**
§6 là **mục tiêu để nhắm**. §2.2 là **kỳ vọng để không thất vọng**. Nhắm 12 và đạt 8 tốt hơn nhắm 8 và đạt 6. Nhưng nếu ở tháng 40 bạn mới đạt Advanced ở 5 nhánh, đó là bình thường chứ không phải thất bại.

**(2) §12 nói "bỏ hẳn học framework agent sâu", §13 vẫn liệt kê LangGraph documentation với 20 h.**
20 h là **đủ để dùng thành thạo một framework**, không phải đủ để "học sâu". Ranh giới nằm ở chỗ: bạn dùng nó, hay bạn thuộc nó. Nếu framework biến mất và bạn dựng lại được chức năng tương đương trong 2 tuần, bạn đang ở đúng phía của ranh giới.

## 15.5 — Kiểm tra tự nhất quán

| Kiểm tra | Kết quả |
|---|---|
| Tổng giờ theo nhánh (Phụ lục B) khớp 6.600 h | ✓ 6.600 h |
| Tổng giờ theo phase (§9.1) khớp tổng theo nhánh | ✓ có chồng lấn thời gian nhưng tổng giờ khớp |
| Mọi nhánh trong §5 xuất hiện trong depth map §6 | ✓ 26 dòng |
| Mọi nhánh trong depth map có trong Phụ lục B | ✓ |
| Mọi project ở §10 ánh xạ vào nhánh cụ thể | ✓ bảng "bản đồ nhánh" mỗi project |
| Thứ tự học trong nhánh không mâu thuẫn với dependency graph §4 | ✓ kiểm tra: Kubernetes (C10.12) ở Phase 4 sau distributed (C10.1–C10.6) Phase 2–3 ✓; Rust (C1.3) Phase 3 sau C ✓; C8.11 LLM Phase 4 sau C8.1 eval Phase 2 ✓ |
| Mọi checkpoint đều quan sát được (không có "hiểu X") | ✓ |
| Không tài nguyên nào có URL bịa | ✓ chỉ tên tổ chức + tên tài nguyên |
| Nhãn độ tin cậy có mặt ở mọi tuyên bố nhạy thời điểm | ✓ |

---

# 16. REASSESSMENT + STATE BLOCK

## 16.1 — Xem lại định kỳ

| Chu kỳ | Xem lại cái gì | Thời gian |
|---|---|---|
| **Hàng tuần** (chủ nhật) | Giờ thực tế vs cam kết · checkpoint nào đạt trong tuần · có nhánh nào bị bỏ rơi im lặng không · cập nhật STATE | 30 phút |
| **Hàng tháng** | Tiến độ so với phase hiện tại · project có đang tích hợp nhiều nhánh hay biến thành tutorial dài · có cạm bẫy nào ở §12.3 đang xảy ra không | 1 giờ |
| **Mỗi quý** | Phân bổ core/supporting/adjacent còn đúng tỷ lệ (Phụ lục B) · tín hiệu chuyển phase (§9) đã đạt chưa · danh sách "thứ mới cần đánh giá" bằng quy tắc §12.4 | 2 giờ |
| **Mỗi 6 tháng** | **Tầng 4 và 5 của §8 — gần như chắc chắn đã lỗi thời.** Tầng 1–3 thì không cần xem lại · kiểm tra tài nguyên ở §13 còn tồn tại không · đọc lại §15.3 xem điều nào đã được chứng minh hoặc bác bỏ | 4 giờ |
| **Hàng năm** | **Toàn bộ kiến trúc.** Spine (§11) còn đúng? Depth map (§6) cần đổi? Nhánh nào nên thăng hoặc tụt hạng? North Star (§2.1) còn là thứ bạn muốn? | 1 ngày |

## 16.2 — Tín hiệu kích hoạt xem lại ngay, không đợi chu kỳ

| Tín hiệu | Hành động |
|---|---|
| **Bạn nhận được một công việc** | Xem lại **toàn bộ depth map**. Công việc thật nên quyết định nhánh nào lên Expert. Đây là tín hiệu quan trọng nhất trong bảng |
| Bạn kẹt ở một nhánh >6 tuần không tiến bộ đo được | Dependency phía trên có thể còn thiếu. Quay lại §4.1 và kiểm tra node cha |
| Một project vượt 2× thời gian dự kiến | Hoặc phạm vi sai, hoặc nền còn lỗ hổng. **Cả hai đều là thông tin.** Dừng, viết ra, rồi quyết định |
| Một công nghệ ở tầng 4 (§8) biến mất hoặc bị thay | Kiểm tra: bạn đã học phần **nguyên lý** hay chỉ học phần API? Nếu là cái sau, đó là bài học về phân bổ giờ |
| Bạn thấy **chán** một nhánh core >2 tháng liên tục | Tín hiệu thật về spine, không phải về kỷ luật. Cân nhắc lại §11.4. Chán khác khó |
| Giờ thực tế dưới 15 h/tuần trong ≥2 tháng | Kích hoạt kịch bản §0.3: **thu hẹp phạm vi**, không kéo dài timeline |
| Bạn phát hiện §15.3 mục nào đó sai | Cập nhật tài liệu. Roadmap là tài liệu sống |
| Bạn đạt mọi checkpoint của một phase sớm hơn 30% | Bạn đang ước lượng thấp bản thân. Nâng mục tiêu, hoặc rút ngắn timeline |
| Một sự cố thật trong project của bạn | Viết postmortem (C11.9). Sự cố là nguồn học tập đắt nhất bạn có — đừng lãng phí nó |

## 16.3 — STATE BLOCK — dán lại ở phiên sau

```
STATE · Intelligent Systems Integration Engineering
════════════════════════════════════════════════════════

DOMAIN
  gốc:        End-to-End Intelligent Systems Engineering
  chuẩn hóa:  Intelligent Systems Integration Engineering
  trục:       sense → transport → store → learn → infer →
              decide → act → observe → adapt
  đích:       LIÊN NGÀNH — không chuyên một mảng, nền dày
              ở tất cả, sâu theo khoảng cách tới root
  spine:      SC-B (Edge-to-Cloud)
              → công việc lo nửa OT, tự học lo nửa IT

TÌNH HUỐNG NGHỀ NGHIỆP
  vị trí:     Kỹ sư tự động hóa — IPC E&C (tổng thầu EPC)
  giai đoạn:  thử việc, đang tìm hiểu
  stack:      hỗn hợp, nhiều Siemens và ABB
  mô hình cty: EPC, KHÔNG làm O&M dài hạn
              → cung observe→adapt phải mua bằng project

NGÂN SÁCH
  tự học:     12–18 h/tuần → ~3.600 h / 5–6 năm
  công việc:  ~2.100 h quy đổi (Phụ lục D)
  hiệu dụng:  ~5.700 h
  phần cứng:  8–15tr VND rải 5 năm         [ĐÃ XÁC NHẬN]
  GPU:        thuê theo giờ Phase 1–3
  ràng buộc lớn nhất: NĂNG LƯỢNG sau giờ làm

PHASE HIỆN TẠI
  Track IT:   Phase 0 — Bootstrap (tháng 0–6)
  Track OT:   thử việc / định hướng
  tuần thứ:   ___
  giờ tuần này: ___ / mục tiêu 12–18

ĐÃ ĐẠT (checkpoint — xem Phụ lục C)
  (chưa có)

ĐANG LÀM
  §14.1 — tuần 1 của 90 ngày đầu
  Sổ "khái niệm vendor ↔ khái niệm trung lập": ___ cặp
  P1 — chưa khởi động

QUYẾT ĐỊNH ĐÃ CHỐT
  ✓ giữ nguyên phạm vi 38 lĩnh vực — tình huống đổi
    trình tự và giờ, KHÔNG đổi phạm vi
  ✓ công việc lo nửa OT, tự học lo nửa IT
  ✓ ưu tiên tự học: C8 > C10 > C2/C3/C4 > C1 > còn lại
  ✓ KHÔNG tự học song song nhánh công việc đang dạy
  ✓ P3 (30 ngày) và P6 (90 ngày) là BẮT BUỘC —
    nguồn kinh nghiệm vận hành dài hạn duy nhất
  ✓ không chọn Expert ở C6/C7/S2/S3 (công việc đã cho)
  ✓ 3 ngôn ngữ: C, Python, + Go hoặc Rust (chốt Phase 3)
  ✓ Kubernetes học SAU distributed systems
  ✓ trần 20 h cho bất kỳ agent framework nào
  ✓ không certification trong 2 năm đầu
  ✓ dịch mọi khái niệm vendor sang trung lập trong ≤1 tuần

ĐIỂM RẼ NHÁNH SẮP TỚI
  tháng 24–30: chọn C8 hay C12 lên Expert (§11.4)
  tháng 30+:   cân nhắc EPC vs nơi có vận hành (§11.6)

CÂU HỎI ĐANG MỞ
  1. giờ tự học thực tế bền được bao nhiêu? (giả định 12–18)
  2. 12 tháng đầu công việc có cho kỹ thuật thật, hay chủ yếu
     giấy tờ và giám sát? → quyết định Phụ lục D có đúng không
  3. trình độ hiện có ở từng nhánh — để đánh dấu phần skip được

CẦN KIỂM TRA LẠI
  [ ] §8 tầng 4–5: mỗi 6 tháng (lần gần nhất: 09/2026)
  [ ] §13 tài nguyên còn tồn tại: mỗi 6 tháng
  [ ] §15.3 điều không chắc: mỗi quý
  [ ] Phụ lục D giờ quy đổi: mỗi 6 tháng, đối chiếu thực tế

TÀI LIỆU
  phiên bản: v3.0 · 14/09/2026
  trạng thái: hoàn chỉnh, 38 lĩnh vực, không nhánh nào bị nén
════════════════════════════════════════════════════════
```


## 16.4 — Cách dùng roadmap này

**Đây là tài liệu tham chiếu, không phải tài liệu đọc một lần.**

| Khi nào | Mở mục nào |
|---|---|
| Lập kế hoạch tuần | §9 (phase hiện tại) + §13 (tài nguyên của phase) |
| Không biết học gì tiếp | §5 (thứ tự học trong nhánh) + §4 (dependency) |
| Gặp công nghệ mới | §12.4 (quy tắc quyết định 5 câu hỏi) |
| Không biết đã học đủ chưa | Phụ lục C (master checklist) |
| Muốn biết mình đang ở đâu | §6 (depth map) + §16.3 (STATE) |
| Cảm thấy lạc hướng | §1 (main root) + §2.1 (North Star) |
| Cân nhắc đổi hướng | §11 (scenarios) |
| Muốn mua gì đó | Phụ lục A (BOM) + §13.8 (tài nguyên trả phí) |
| Nghi ngờ một khuyến nghị | §15.3 (những chỗ tôi không chắc) |

**Cập nhật tài liệu khi:** bạn phát hiện một ước lượng sai · bạn đổi spine · một tài nguyên biến mất · một điều ở §15.3 được chứng minh hoặc bác bỏ. Ghi ngày và lý do vào cuối file.

---

# PHỤ LỤC A · BILL OF MATERIALS

Giá tham chiếu VND, mua được ở Hà Nội (chợ Nhật Tảo / Trời Đất / Điện Tử Việt Nam, hoặc Shopee/Lazada, hoặc đặt từ LCSC/AliExpress nếu chờ được). Giá dao động; dùng để lập ngân sách, không để so giá.

## A.1 — Phase 0 · Gói khởi động — mua ngay ngày 3

| Món | Số lượng | Giá ước tính | Vì sao cần ngay |
|---|---|---|---|
| ESP32-S3 DevKit (hoặc Raspberry Pi Pico 2) | 2 | 150–250k/cái | Board chính; mua 2 để có cái dự phòng khi làm cháy |
| Breadboard 830 điểm | 2 | 40k/cái | |
| Bộ dây jumper (M-M, M-F, F-F) | 1 bộ | 60k | |
| Cảm biến nhiệt/ẩm/áp I²C (BME280) | 1 | 80k | Cảm biến đầu tiên — I²C, có datasheet tốt |
| IMU 6 trục (MPU6050) hoặc 9 trục | 1 | 50–150k | Cho P1 và sau này P3 |
| **Logic analyzer 8 kênh** | 1 | 200–350k | **ROI cao nhất trong toàn bộ BOM.** Không có nó, debug bus là đoán |
| Đồng hồ vạn năng số | 1 | 300–600k | Chọn loại có đo dòng và đo tụ |
| Cáp USB chất lượng (data, không chỉ sạc) | 2 | 50k/cái | Nguyên nhân phổ biến của "board không nhận" |
| **Tổng Phase 0** | | **~1,3–2,2tr** | |

## A.2 — Phase 1–2 · Mở rộng — tháng 4–18

| Món | Số lượng | Giá ước tính | Dùng cho |
|---|---|---|---|
| STM32 DevKit (Nucleo hoặc Blue Pill + ST-Link) | 1–2 | 150–400k | Họ MCU thứ hai — hệ sinh thái khác ESP32, học được nhiều |
| Probe SWD/JTAG (ST-Link V2 clone hoặc DAPLink) | 1 | 100–200k | Debug thật, không chỉ printf |
| Mỏ hàn + thiếc + flux + hút thiếc | 1 bộ | 400–800k | Perfboard và sửa board |
| Nguồn DC điều chỉnh được (0–30V, 0–5A) | 1 | 800k–1,5tr | Cấp nguồn ổn định, giới hạn dòng để không cháy board |
| Perfboard + header + connector | 1 bộ | 150k | Chuyển từ breadboard sang lắp đặt bền |
| Mic I²S (INMP441) | 1–2 | 60k/cái | Cho P3 nếu chọn hướng âm thanh |
| Module INA219 / INA226 đo dòng | 2 | 50k/cái | **Bắt buộc cho C6.9** — đo ngân sách năng lượng |
| Cảm biến nhiệt độ chính xác (RTD hoặc DS18B20) | 2 | 40k/cái | Cho C7.7 hiệu chuẩn — cần ≥2 để so sánh |
| Điện trở, tụ, diode, MOSFET, LED bộ tổng hợp | 1 bộ | 200k | |
| Pin 18650 + mạch sạc/bảo vệ + holder | 2 bộ | 150k/bộ | Cho P3 chạy pin |
| **Tổng Phase 1–2** | | **~2,5–4,5tr** | |

## A.3 — Phase 3 · Triển khai thực địa — tháng 18–36

| Món | Số lượng | Giá ước tính | Dùng cho |
|---|---|---|---|
| Raspberry Pi 5 (4GB hoặc 8GB) + nguồn + thẻ nhớ | 1 | 1,8–2,8tr | Gateway, embedded Linux, edge compute |
| SSD NVMe + adapter cho Pi | 1 | 800k–1,5tr | Thẻ nhớ SD chết sau vài tháng ghi liên tục — bài học thật |
| Vỏ hộp kín (IP54 trở lên) | 2–3 | 100–250k/cái | Triển khai 30 ngày ngoài môi trường thật |
| Nguồn 5V/12V ổn định có cách ly | 2 | 150k/cái | |
| Cáp và connector chống rung | 1 bộ | 200k | Lắp đặt lên máy đang chạy |
| Module LoRa (SX1276/SX1262) | 2 | 150–250k/cái | Nếu thử nghiệm truyền xa, C5.3 |
| **Oscilloscope** 2 kênh (rẻ: DSO138/FNIRSI; tốt: Rigol DS1054Z) | 1 | 700k–8tr | Tùy ngân sách. Rẻ vẫn hơn không có. C7.5, S2.6 |
| Cảm biến bổ sung tùy bài toán P3 | — | 300–800k | Rung, dòng, áp suất, khí |
| **Tổng Phase 3** | | **~4–14tr** | Biến động lớn nhất ở oscilloscope |

## A.4 — Phase 4–5 · Tùy chọn — tháng 36+

| Món | Giá ước tính | Khi nào mua |
|---|---|---|
| MCU có NPU (STM32N6, hoặc board NXP/Renesas tương đương) | 1–3tr | Khi C6.14 cần so sánh NPU vs CPU thật |
| Thêm 3–5 thiết bị cho đội P6 | 1–2tr | Khi P6 cần ≥5 thiết bị |
| GPU rời ≥24GB VRAM | 40–70tr | **Chỉ khi** chi phí thuê hàng tháng > 1/24 giá máy (§0.2) |
| Máy phân tích năng lượng (Nordic PPK2 hoặc tương đương) | 2–3tr | Khi đo dòng ngủ µA bằng INA219 không đủ chính xác |
| Bàn hàn khí nóng + kính lúp | 1,5–3tr | Chỉ nếu làm SMD |
| In 3D (thuê dịch vụ, không mua máy) | 50–200k/lần | Vỏ tùy chỉnh cho P3, P6 |

## A.5 — Tổng ngân sách 5 năm

| Phase | Thấp | Cao |
|---|---|---|
| Phase 0 | 1,3tr | 2,2tr |
| Phase 1–2 | 2,5tr | 4,5tr |
| Phase 3 | 4,0tr | 14,0tr |
| Phase 4–5 (không tính GPU) | 2,0tr | 8,0tr |
| **Tổng (không GPU)** | **~10tr** | **~29tr** |
| Thuê GPU Phase 1–4 | 3tr | 8tr |
| Sách (3 cuốn ở §13.8) | 2tr | 3tr |
| **Tổng cộng** | **~15tr** | **~40tr** |

**[Recommendation] Thứ tự ưu tiên nếu phải cắt:**
1. **Không cắt:** logic analyzer, đồng hồ vạn năng, 2 board, INA219. Đây là bộ tối thiểu để **đo được** — và không đo được thì không học được C6/C7.
2. **Hoãn được:** oscilloscope (tới Phase 3), nguồn DC điều chỉnh (dùng USB trước), Raspberry Pi 5 (tới Phase 3).
3. **Bỏ được:** MCU có NPU (dùng CPU và mô phỏng để hiểu nguyên lý), máy phân tích năng lượng, bàn hàn khí nóng.
4. **Không mua GPU** cho tới khi có số liệu chứng minh (§0.2).

## A.6 — Quy tắc mua sắm

| Quy tắc | Lý do |
|---|---|
| **Không mua board mới cho tới khi board hiện tại đã chạy một project ≥30 ngày** | Chống cạm bẫy "sưu tầm board" (§12.3) |
| Mua 2 cái cho mọi thứ rẻ dễ hỏng | Bạn **sẽ** làm cháy board. Chờ hàng 1 tuần giữa chừng project là cách giết động lực |
| Ưu tiên linh kiện có datasheet tốt hơn linh kiện rẻ hơn | Datasheet kém = hàng chục giờ đoán mò |
| Kiểm tra trạng thái vòng đời (EOL) trước khi chọn MCU cho P3/P6 | Chọn con sắp ngừng sản xuất là lỗi đắt (S2.2) |
| Thiết bị đo: mua tốt hơn khả năng hiện tại của bạn | Bạn sẽ lớn lên vừa nó; đồng hồ rẻ nói dối và bạn không biết |
| Với cảm biến: mua ≥2 cái cùng loại | Hiệu chuẩn (C7.7) cần so sánh; một cái không nói lên gì |

---

# PHỤ LỤC B · NGÂN SÁCH GIỜ CHI TIẾT

**v3:** hai nguồn giờ, không phải một.

| Nguồn | Giờ / 5 năm | Kiểm soát được? |
|---|---|---|
| Tự học | **3.600** | Có, hoàn toàn |
| Công việc quy đổi | **~2.100** | Không — phụ thuộc dự án được giao |
| **Hiệu dụng** | **~5.700** | |

## B.1 — Phân bổ giờ tự học theo nhãn

| Nhãn | Giờ tự học | % |
|---|---|---|
| Core (12 nhánh) | 2.250 | 62,5% |
| Supporting (8 nhánh) | 450 | 12,5% |
| Adjacent (6 nhánh) | 150 | 4,2% |
| Project tích hợp | 700 | 19,4% |
| Slack, review, viết lách | 50 | 1,4% |
| **Tổng** | **3.600** | **100%** |

## B.2 — Core · giờ tự học × giờ công việc quy đổi

| Nhánh | Tự học | Công việc | **Hiệu dụng** | Mức đạt được |
|---|---|---|---|---|
| C1 Programming & runtimes | 280 | 20 | **300** | Advanced |
| C2 DSA | 180 | 0 | **180** | Intermediate–Advanced |
| C3 Computer architecture | 200 | 0 | **200** | Intermediate–Advanced |
| C4 OS & concurrency | 240 | 30 | **270** | Advanced |
| C5 Networking | 160 | 250 | **410** | Advanced |
| C6 Embedded & firmware | 200 | 300 | **500** | Advanced |
| C7 Sensing & signals | 80 | 350 | **430** | Advanced |
| C8 ML & inference systems | 320 | 0 | **320** | Advanced → **Expert nếu chọn** |
| C9 Data engineering & storage | 190 | 40 | **230** | Intermediate–Advanced |
| C10 Distributed & cloud | 200 | 0 | **200** | Intermediate–Advanced |
| C11 Observability & performance | 130 | 100 | **230** | Intermediate–Advanced |
| C12 Systems architecture | 80 | 300 | **380** | Advanced → **Expert nếu chọn** |
| **Core tổng** | **2.260** | **1.390** | **3.650** | |

## B.3 — Supporting

| Nhánh | Tự học | Công việc | **Hiệu dụng** |
|---|---|---|---|
| S1 Mathematics | 220 | 0 | **220** |
| S2 Electronics & power | 30 | 250 | **280** |
| S3 Control theory | 30 | 250 | **280** |
| S4 Security | 60 | 40 | **100** |
| S5 Testing & verification | 50 | 30 | **80** |
| S6 Reliability & safety | 20 | 150 | **170** |
| S7 Queueing & economics | 20 | 10 | **30** |
| S8 Technical communication | 20 | 60 | **80** |
| **Supporting tổng** | **450** | **790** | **1.240** |

## B.4 — Adjacent

| Nhánh | Tự học | Công việc | **Hiệu dụng** |
|---|---|---|---|
| A1 Robotics & autonomy | 40 | 20 | **60** |
| A2 Simulation & digital twins | 30 | 20 | **50** |
| A3 HCI & human factors | 25 | 40 | **65** |
| A4 Business & operations | 10 | 80 | **90** |
| A5 Standards & regulation | 15 | 120 | **135** |
| A6 Licensing & IP | 30 | 0 | **30** |
| **Adjacent tổng** | **150** | **280** | **430** |

*Tổng công việc quy đổi: 1.390 + 790 + 280 = **2.460 h**. Tôi ghi ~2.100 ở §0 để dự phòng — giờ công việc trùng lặp giữa các nhánh (một buổi commissioning đóng góp vào C11 và C12 cùng lúc), nên tổng thực tế thấp hơn tổng cộng dồn.*

## B.5 — Project · giờ tự học

| Project | Giờ | Ghi chú |
|---|---|---|
| P1 Sensor node + logger | 40 | Phase 0 |
| P2 Tự viết lại hạ tầng | 110 | Phase 1–2 |
| P3 Edge anomaly detector | 150 | Phase 2–3. **30 ngày thực địa — bắt buộc** |
| P4 Ingestion platform | 130 | Phase 3–4 |
| P5 Inference service | 120 | Phase 4 |
| P6 Closed-loop system | 250 | Phase 5. **90 ngày vận hành — bắt buộc** |
| P7 Làm cứng / open source | tùy chọn | Sau tháng 72 |
| **Tổng** | **~800** | 700 h ròng sau khi trừ phần chồng với giờ nhánh |

## B.6 — Tổng theo phase (chỉ tự học)

| Phase | Tháng | Core | Supporting | Adjacent | Project | Slack | **Tổng** |
|---|---|---|---|---|---|---|---|
| P0 Bootstrap | 0–6 | 250 | 50 | — | 40 | 10 | **350** |
| P1 Nền tính toán | 3–24 | 560 | 140 | — | 90 | 10 | **800** |
| P2 Nền hệ thống | 18–38 | 600 | 80 | — | 110 | 10 | **800** |
| P3 Vòng lặp khép lại | 30–50 | 610 | 70 | — | 160 | 10 | **850** |
| P4 Quy mô & production | 42–62 | 490 | 70 | 60 | 120 | 10 | **750** |
| P5 Kiến trúc & chuyên sâu | 54–78 | 340 | 40 | 90 | 180 | 50 | **700** |
| **Tổng** | | **2.850** | **450** | **150** | **700** | **100** | **3.600** |

*Core cộng dồn 2.850 > 2.260 ở B.2 vì phần chênh là giờ ôn và giờ project tính vào nhánh. Tổng ròng vẫn 3.600.*

## B.7 — Cách dùng bảng này

| Tình huống | Làm gì |
|---|---|
| Giờ tự học thực tế thấp hơn 20% (≈12 h/tuần) | Bình thường. Cắt theo thứ tự: Adjacent → Supporting mức thấp → P7 |
| Thấp hơn 40% (≈9 h/tuần) | Cắt sâu hơn: giữ C8, C10, C1, C2 và P3; hoãn C3, C9, C11 sang sau tháng 60 |
| Thấp hơn 60% (≈6 h/tuần) trong ≥6 tháng | **Đổi kiến trúc:** giữ đúng một nhánh Advanced (C8), phần còn lại Working. Kéo timeline lên 8 năm. Thà đạt sâu một chỗ còn hơn nông khắp nơi |
| Công việc **không** cấp như bảng dự kiến | Sau 12 tháng, đối chiếu cột "công việc" với thực tế. Chênh lệch phải được bù bằng giờ tự học — hoặc bằng việc đổi vị trí trong công ty |
| Công việc cấp **nhiều hơn** dự kiến | Dồn giờ tự học tiết kiệm được vào C8 và C10 — hai nhánh không bao giờ có nguồn nào khác |
| Một nhánh tốn nhiều hơn dự kiến | Lấy từ Slack trước, rồi từ Adjacent. Đừng lấy từ nhánh core khác |
| Bạn đã biết một nhánh | Trừ giờ, nhưng **giữ lại checkpoint**. Không pass checkpoint nghĩa là chưa biết ở mức roadmap yêu cầu |


# PHỤ LỤC C · MASTER CHECKLIST

Toàn bộ checkpoint từ §5, gom lại thành danh sách kiểm tra được. **Một nhánh chưa tick hết checkpoint thì chưa đạt mức mục tiêu, bất kể bạn đã đọc bao nhiêu.**

Ký hiệu: ★ = checkpoint quan trọng nhất của nhánh.

## C1 · Programming & Language Runtimes
- [ ] Ring buffer + state machine bằng C, không cấp phát động, sạch dưới valgrind và ASAN/UBSAN
- [ ] Giải thích padding mọi struct bạn định nghĩa mà không chạy `sizeof`
- [ ] Package Python: test ≥80% coverage, `mypy --strict` pass, `pip install .` từ repo sạch, có CLI và logging
- [ ] Port một service Python sang Go/Rust, đo chênh lệch p99 và bộ nhớ, giải thích nguyên nhân
- [ ] ★ Đọc core dump và giải thích nguyên nhân segfault
- [ ] Tính worst-case stack usage của một firmware và chứng minh không tràn
- [ ] Thiết kế API mà dùng sai thì compile fail — chứng minh bằng code sai cố ý không build được
- [ ] Bảng: mỗi dependency × cách hỏng × hành vi mong muốn × cơ chế hiện thực — bảo vệ được từng ô
- [ ] Cross-compile binary ARM từ x86, chạy trên board, giải thích từng dòng linker script
- [ ] Giải thích p99 tăng khi CPU chưa đầy 50% — chỉ ra do GC, do lock, hay do I/O bằng số liệu
- [ ] ★ Tìm bug chỉ xuất hiện dưới concurrency, sửa đúng nguyên nhân (không che bằng `sleep`)
- [ ] `git bisect` tìm commit gây regression trong repo ≥500 commit
- [ ] Rebase 10 commit lộn xộn thành 3 commit nguyên tử
- [ ] ★ Đọc một module của CPython/Linux/Redis/vLLM trong ≤6 h, vẽ lại data flow, viết một trang giải thích
- [ ] Thêm tính năng vào codebase của chính bạn từ 6 tháng trước, sửa ≤5 file
- [ ] Phát hiện output sai của AI và nói được sai ở đâu, vì sao

## C2 · Data Structures & Algorithms
- [ ] Phân tích amortized của một cấu trúc **bạn tự thiết kế**, chứng minh biên
- [ ] Hash table open addressing tự cài, đo hiệu năng vs thư viện chuẩn, giải thích chênh lệch
- [ ] Giải thích **bằng số** vì sao DB dùng B-tree không dùng BST (tính số lần đọc đĩa, n = 10⁹)
- [ ] Scheduler dùng heap cho RTOS đồ chơi, chạy đúng với 20 task khác chu kỳ
- [ ] Topological sort cho build system nhỏ, phát hiện chu trình và báo đúng chu trình nào
- [ ] Cài Dijkstra và nêu 2 trường hợp nó sai, có phản ví dụ
- [ ] Sắp xếp file 10 GB trên máy 8 GB RAM, đo số lần đọc/ghi đĩa, so với lý thuyết
- [ ] ★ Nhận ra cấu trúc DP trong bài toán **chưa từng gặp** trong ≤20 phút, viết hàm hồi quy
- [ ] Chứng minh hoặc bác bỏ tính tối ưu của một thuật toán tham lam bằng exchange argument
- [ ] Bloom filter giảm ≥80% truy vấn DB trong workload thật, đo FP rate thực tế vs lý thuyết
- [ ] ★ Tăng tốc vòng lặp ≥2× **chỉ bằng** đổi thứ tự truy cập hoặc bố cục dữ liệu
- [ ] Tính p99 trên stream 10⁸ mẫu không lưu toàn bộ, sai số < 1%
- [ ] Lock-free SPSC ring buffer, sạch dưới TSAN, lập luận bằng lời vì sao đúng
- [ ] Giải bài lạ mức trung bình-khó trong 45 phút

## C3 · Computer Architecture & Digital Logic
- [ ] ALU đầy đủ chức năng chỉ từ cổng NAND (nand2tetris 1–2)
- [ ] FSM cho một giao thức nối tiếp, cài bằng C, chạy trên MCU, xử lý trạng thái lỗi
- [ ] ★ nand2tetris phần 1 hoàn thành — CPU + assembler + chương trình chạy được
- [ ] Đọc disassembly `-O2` và giải thích mọi thay đổi so với `-O0`
- [ ] Hai phiên bản vòng lặp (có nhánh khó đoán / branchless), đo chênh lệch, xác nhận bằng `branch-misses`
- [ ] ★★ Workload thật: xác định memory-bound hay compute-bound bằng `perf`, blocking/tiling, speedup ≥3×, **giải thích bằng số liệu cache miss trước/sau**
- [ ] Code đồng bộ hóa chạy đúng trên x86 nhưng hỏng trên ARM — giải thích và sửa bằng barrier đúng
- [ ] Vector hóa một convolution 1-D, đo speedup, xác nhận lệnh SIMD trong disassembly
- [ ] Kernel GPU: xác định memory-bound hay compute-bound, giải thích bằng mô hình roofline
- [ ] Cùng model trên hai phần cứng khác nhau, đo latency + năng lượng, giải thích bằng đặc điểm kiến trúc
- [ ] DMA cho luồng ADC liên tục, đo mức giảm tải CPU, xử lý đúng mạch lạc cache
- [ ] ★★ Lượng tử hóa model sang int8, **định vị lớp nào gây mất chính xác nhiều nhất** bằng phân tích theo lớp
- [ ] Đo throttling trên SBC dưới tải 30 phút, đồ thị nhiệt–xung nhịp–thông lượng, đề xuất giảm thiểu có số
- [ ] `perf stat` phân biệt đúng nút thắt CPU / bộ nhớ / I/O ở cả ba trường hợp thử nghiệm

## C4 · Operating Systems & Concurrency
- [ ] Đo chi phí chuyển ngữ cảnh trên máy bạn, giải thích con số bằng những gì phải lưu/khôi phục
- [ ] Tái tạo priority inversion với 3 luồng, đo độ trễ, sửa bằng priority inheritance, số đo trước/sau
- [ ] Chẩn đoán thrashing từ số liệu (page fault, swap, latency), xác định nguyên nhân, sửa
- [ ] ★ Chứng minh mất dữ liệu khi thiếu `fsync` bằng thí nghiệm cắt điện; sửa và chứng minh không mất
- [ ] ★★ Tự viết event loop phục vụ 10.000 kết nối đồng thời trên một luồng
- [ ] ★ Bounded buffer producer-consumer bằng mutex + condvar, không busy-wait, xử lý spurious wakeup, sạch dưới TSAN với 8+8
- [ ] Pipeline 3 giai đoạn có backpressure, chứng minh bộ nhớ không tăng vô hạn khi nghẽn
- [ ] Từ stack dump toàn bộ luồng, xác định chu trình chờ và hai khóa gây deadlock
- [ ] Ba tình huống IPC khác nhau: chọn đúng cơ chế cho mỗi cái, bảo vệ bằng đo đạc
- [ ] Đo jitter tác vụ chu kỳ 1 ms trên MCU dưới tải, đưa xuống < 50 µs, giải thích từng nguồn đã loại
- [ ] ★ "Container" tối giản bằng `unshare` + `cgroup` + `chroot`, không dùng Docker
- [ ] Unit systemd có restart policy + device tree overlay cho cảm biến, chạy sau reboot không can thiệp
- [ ] eBPF/`bpftrace` trace một syscall path và tìm nguồn latency, không sửa code ứng dụng

## C5 · Networking
- [ ] Tính CRC bằng tay hoặc code từ đầu; giải thích vì sao CRC bắt lỗi burst mà checksum bỏ sót
- [ ] Đọc ARP table, dựng tình huống IP trùng, giải thích chính xác triệu chứng
- [ ] ★ Ba kịch bản radio (băng thông/tầm/pin): chọn đúng, tính link budget, **đo thực tế** xác nhận hoặc bác bỏ
- [ ] Chia subnet cho mạng 200 thiết bị 5 nhóm, viết bảng định tuyến, truy vết gói bằng lập luận rồi xác nhận bằng `traceroute`
- [ ] ★★ Từ packet capture, xác định đúng nguyên nhân thông lượng thấp ở ≥3 tình huống: giới hạn cửa sổ, mất gói, Nagle/delayed-ACK
- [ ] Chẩn đoán sự cố DNS cache bằng công cụ, chỉ ra tầng cache nào giữ bản ghi cũ
- [ ] Giải thích head-of-line blocking ở tầng nào trong HTTP/1.1, /2, /3; dựng thí nghiệm chứng minh
- [ ] ★ Bốn kịch bản messaging: chọn giao thức + QoS, bảo vệ bằng số (byte, số lần thức radio, năng lượng/thông điệp)
- [ ] mTLS giữa MCU và server, gồm cấp phát ban đầu và xoay vòng chứng chỉ; thiết bị vẫn kết nối sau khi cert cũ hết hạn
- [ ] ★ TCP server từ socket thuần, xử lý partial read/write, graceful shutdown, timeout, 10.000 kết nối
- [ ] Ngân sách độ trễ cho request xuyên 5 tầng: dự đoán p50/p99 **trước khi đo**, rồi đo và giải thích chênh lệch
- [ ] Wireshark tìm nguyên nhân kết nối treo, phân biệt mất gói / tường lửa im lặng / ứng dụng không đọc
- [ ] Vẽ đường đi gói tin từ Internet tới container, liệt kê mọi thành phần, xác định nơi mTLS bắt đầu/kết thúc
- [ ] ★★ Thiết bị mất mạng 6 h rồi khôi phục: 0 mất, 0 trùng, thứ tự đúng, không tăng đột biến tải (có đồ thị)
- [ ] Tái tạo retry storm trong lab, dập bằng jitter + circuit breaker, chứng minh bằng đồ thị
- [ ] **[v3]** Đọc dữ liệu từ thiết bị công nghiệp thật qua giao thức gốc, đưa lên hệ hiện đại, **viết ra chính xác cái gì mất trong lần dịch** (kiểu dữ liệu, timestamp, chất lượng, ngữ nghĩa)

## C6 · Embedded Systems & Firmware
- [ ] ★★ Cấu hình một peripheral chưa từng dùng **chỉ bằng reference manual và errata** — không ví dụ, không HAL vendor
- [ ] PWM đạt tần số + độ phân giải mục tiêu, đo bằng logic analyzer, sai số < 0,1%; độ trễ ngắt < 5 µs
- [ ] ★ Debug bus I²C câm bằng logic analyzer ở 3 tình huống: sai địa chỉ, thiếu pull-up, clock stretching
- [ ] Đo ENOB thực tế của ADC bằng thí nghiệm, so datasheet, giải thích chênh lệch
- [ ] Thu audio/ADC ≥16 kHz qua DMA vòng tròn đệm đôi, 1 giờ **không mất mẫu nào**, chứng minh bằng bộ đếm
- [ ] Chứng minh không tràn stack ở worst case bằng cả stack painting lẫn phân tích tĩnh, hai phương pháp đồng ý
- [ ] Chuyển firmware superloop 4 chức năng sang RTOS không tạo race mới; 24 h liên tục dưới tải, kiểm bằng trace
- [ ] Ba kịch bản: chọn bare-metal / RTOS / embedded Linux, bảo vệ bằng bảng định lượng (RAM, flash, boot time, jitter, chi phí)
- [ ] ★★ Node đạt tuổi thọ pin mục tiêu: **có phép tính ngân sách năng lượng chứng minh trước**, đo thực tế ≥2 tuần, so sánh
- [ ] ★★ OTA cắt điện ở 3 thời điểm khác nhau (tải / ghi / chuyển đổi), 20/20 lần thiết bị vẫn boot hợp lệ
- [ ] ★ Tìm bug chỉ xuất hiện ở tốc độ đầy đủ bằng SWO trace hoặc logic analyzer, không dùng breakpoint
- [ ] ★ ≥60% logic firmware chạy dưới unit test trên PC, trong CI
- [ ] Provision device identity + secure boot; firmware không ký **không boot**; khóa không đọc được qua debug
- [ ] ★★ Model chạy trên MCU trong ngân sách RAM cho trước, đo latency p99 + năng lượng/inference, độ chính xác trên eval set từ **thiết bị thật**
- [ ] Chứng minh tác vụ luôn hoàn thành trong deadline dưới tải xấu nhất (DMA chạy, mọi ngắt bắn, flash đang ghi)
- [ ] **[v3]** Cho một bài toán điều khiển: lập luận chọn PLC / MCU+RTOS / embedded Linux bằng bảng định lượng (tính xác định, chi phí, vòng đời, chứng nhận, nhân lực bảo trì)
- [ ] **[v3]** Viết cùng một logic điều khiển ở cả hai thế giới — ST trên PLC và C trên MCU — so sánh cái gì dễ hơn ở mỗi bên và vì sao

## C7 · Sensing, Signals & Physical Interface
- [ ] ★★ Tái tạo aliasing bằng thí nghiệm vật lý, **dự đoán chính xác tần số giả bằng công thức**, sửa bằng anti-alias filter, chứng minh biến mất
- [ ] Tính sàn nhiễu lý thuyết của chuỗi đo, đo thực tế, giải thích chênh lệch, chỉ ra nguồn nhiễu chiếm ưu thế
- [ ] Thiết kế filter đạt dải thông + độ suy giảm + độ trễ cho trước, cài trên MCU, đo đáp ứng tần số thực tế
- [ ] ★ Gắn IMU lên động cơ, tìm tần số cơ bản + harmonic, **phát hiện bất thường cố ý tạo ra** từ phổ
- [ ] Giảm nhiễu ≥10 dB bằng thay đổi phần cứng/đi dây, có số đo trước/sau
- [ ] Mỗi loại cảm biến dùng: ≥3 chế độ hỏng + cơ chế phát hiện; **tạo ra từng chế độ hỏng thật** và xác nhận phát hiện được
- [ ] ★★ Hiệu chuẩn một cảm biến, **chứng minh sai số RMS giảm** trên tập điểm độc lập
- [ ] Kalman 1-D tự cài (không thư viện), giải thích ý nghĩa vật lý từng ma trận, tốt hơn moving average trên dữ liệu thật
- [ ] ★★ Đo clock drift 48 h, tính ppm, dự đoán lệch sau 30 ngày; căn chỉnh chuỗi thời gian 2 thiết bị, **sự kiện đồng thời ghi nhận đồng thời** dưới ngưỡng
- [ ] Đặc trưng thủ công + model nhỏ đạt ≥ độ chính xác của model lớn trên dữ liệu thô; đo chênh lệch RAM/latency/năng lượng
- [ ] ★ Điều khiển tải thật với khóa liên động phần cứng; gây ra cả 3 loại lỗi phần mềm (treo, crash, giá trị điên rồ), không hư hại
- [ ] Tune PID trên hệ vật lý thật đạt overshoot + settling time mục tiêu, có đồ thị trước/sau

## C8 · Machine Learning & Inference Systems
- [ ] ★ Phát hiện rò rỉ dữ liệu trong pipeline do người khác viết, chỉ chính xác chỗ rò, ước lượng mức thổi phồng metric
- [ ] Đánh bại neural network bằng gradient boosting trên dữ liệu bảng, giải thích đặc điểm nào làm cây thắng
- [ ] ★★ Eval set bạn **tin tưởng**, viết ra bằng văn bản những gì nó **không** đo được, chứng minh bằng một ca điểm cao nhưng hỏng thật
- [ ] Tự cài backprop cho MLP bằng numpy thuần, khớp PyTorch tới 1e-6
- [ ] Vẽ luồng qua khối transformer, **tính bằng tay** bộ nhớ KV cache theo độ dài chuỗi + batch, xác nhận bằng đo
- [ ] Chẩn đoán retrieval trả kết quả vô nghĩa: xác định do model embedding / chuẩn hóa / chunking
- [ ] ★ Chạy lại thí nghiệm của chính bạn sau **3 tháng**, ra cùng kết quả trong sai số thống kê
- [ ] Fine-tune cho domain hẹp: cải thiện trên eval riêng **và** không tệ đi trên eval thứ hai
- [ ] ★★ Giảm ≥4× kích thước model dưới ngưỡng mất chính xác; **đường cong Pareto ≥4 cấu hình**; định vị lớp nhạy cảm nhất
- [ ] ★★ Tự deploy serving stack, **tăng throughput ≥2×** bằng cấu hình, có p50/p99 trước/sau, giải thích cơ chế mỗi cải thiện
- [ ] ★ Xây tính năng dùng LLM và **chứng minh bằng đo đạc** rằng một lời gọi structured output không đủ, trước khi thêm orchestration
- [ ] ★ Agent phục hồi đúng sau khi bị kill giữa chừng, tiếp tục từ đúng điểm dừng với trạng thái nhất quán
- [ ] ★★ Eval harness bắt được regression thật mà unit test bỏ lọt
- [ ] ★ Phát hiện drift **trước khi** ảnh hưởng người dùng: cảnh báo đúng lúc, không quá sớm (nhiễu), không quá muộn
- [ ] 3 phương án kiến trúc + bảng chi phí và độ trễ; bảo vệ được trước "vì sao không chọn cái rẻ hơn"
- [ ] ★ Liệt kê ≥5 cách hệ ML của bạn hỏng mà mọi dashboard vẫn xanh; thiết kế cơ chế phát hiện cho mỗi cái

## C9 · Data Engineering & Storage
- [ ] Schema cho hệ ≥100 thiết bị, ≥5 loại cảm biến, metadata thay đổi theo thời gian; bảo vệ **từng** lựa chọn phi chuẩn hóa
- [ ] ★ Tăng tốc truy vấn chậm **≥10×** bằng đọc query plan, ghi lại plan trước/sau
- [ ] Tái tạo write skew ở `repeatable read`, chứng minh gây kết quả sai, sửa bằng đúng công cụ
- [ ] Chọn storage engine cho workload ghi nặng, bảo vệ bằng phân tích khuếch đại ghi, xác nhận bằng benchmark
- [ ] ★★ 1 năm dữ liệu 100 thiết bị × 5 cảm biến × 1 Hz trong ngân sách; truy vấn "trung bình theo giờ, 30 ngày" < 1 giây
- [ ] Truy vấn 50 GB Parquet trên laptop 16 GB, < 60 giây, giải thích predicate pushdown loại bao nhiêu dữ liệu
- [ ] Chiến lược cache cho một tính năng + **chỉ ra tường minh kịch bản cache trả dữ liệu sai**, quyết định có chấp nhận được không
- [ ] Đường cong recall–latency cho ≥3 cấu hình ANN; **nêu trường hợp tìm kiếm từ khóa tốt hơn vector**
- [ ] ★ Giải thích bằng ví dụ cụ thể vì sao "exactly-once" phải làm ở tầng ứng dụng; chứng minh bằng test gửi trùng
- [ ] Ba yêu cầu nghiệp vụ: chọn batch/stream/micro-batch, bảo vệ bằng bảng (độ trễ, chi phí, số dòng code, số chế độ hỏng)
- [ ] ★★ 20 thiết bị offline 24 h cùng trở lại: 0 mất, 0 trùng, thứ tự đúng, **tải server không vượt 2×** (có đồ thị)
- [ ] Đổi schema (thêm trường, đổi kiểu), consumer cũ vẫn chạy, chứng minh bằng test tự động trong CI
- [ ] ★ Phát hiện cảm biến hỏng **từ tầng dữ liệu** trong ≤1 h, bằng cách gây hỏng thật (ngắt / che / làm nóng)
- [ ] ★ Khôi phục **thật** từ backup vào môi trường sạch, đo RTO và RPO thực tế, so với mục tiêu

## C10 · Distributed Systems & Cloud Infrastructure
- [ ] ★★ Liệt kê mọi điểm hỏng từng phần của một kiến trúc + hệ quả từ góc nhìn người dùng; kiểm chứng ≥5 cái bằng thử nghiệm
- [ ] Dựng tình huống sắp thứ tự theo timestamp cho kết quả **sai** với 2 máy đồng hồ lệch; sửa bằng đồng hồ logic
- [ ] Ba tính năng: chọn mô hình nhất quán, **mô tả chính xác người dùng thấy gì khi có sự cố**
- [ ] Tính cấu hình quorum cho mục tiêu chịu lỗi cho trước, chứng minh bằng thử nghiệm giết node
- [ ] Nêu 3 tình huống trong hệ của bạn mà đồng thuận là **sai** lời giải, chỉ ra lời giải đúng
- [ ] ★★ API idempotent, chứng minh bằng test tự động gửi mọi request 3 lần (kể cả ngắt giữa chừng), 0 tác dụng phụ trùng
- [ ] ★ Outbox pattern: 0 sự kiện mất khi kill ngay sau DB commit trước publish, lặp ≥50 lần
- [ ] Chọn partition key, chỉ ra kịch bản gây hot partition, ước lượng mức lệch tải, đề xuất giảm thiểu
- [ ] Chuyển luồng sync 3 bước sang event-driven, viết ra **chính xác bạn mất gì**
- [ ] ★★ Ở **3× tải thiết kế**: suy giảm có kiểm soát thay vì sập, có đồ thị throughput/latency/tỷ lệ lỗi
- [ ] Dựng hạ tầng từ zero với quyền tối thiểu; thử thao tác không được phép và thấy bị từ chối
- [ ] ★ Viết một controller tối giản điều hòa một CRD, chạy trong cluster, giải thích reconciliation loop bằng code của bạn
- [ ] ★ Phá hủy toàn bộ hạ tầng và dựng lại hoàn toàn từ code, 0 thao tác tay, dịch vụ hoạt động; đo thời gian
- [ ] 5 chức năng: quyết định vị trí tính toán, bảo vệ bằng số (băng thông, độ trễ, chi phí, hành vi offline)

## C11 · Observability, Reliability & Performance
- [ ] ★ 5 sự cố khác nhau: nói ngay tín hiệu nào nhìn trước + lý do; **dựng lại 5 sự cố đó thật** để kiểm chứng
- [ ] Trace một request xuyên ≥4 service + 1 thiết bị, xác định tầng gây chậm, có waterfall
- [ ] Định nghĩa SLO + error budget + cảnh báo burn-rate nhiều cửa sổ; **giải thích vì sao không chọn số 9 cao hơn** bằng chi phí
- [ ] ★★ Giải thích **bằng dữ liệu** vì sao p99 tệ trong khi p50 đẹp; phân rã latency theo tầng, xác định nguồn đuôi
- [ ] ★ **Dự đoán trước khi đo** độ trễ tăng bao nhiêu khi utilization 70% → 90%; đo và so, sai số < 2×
- [ ] ★ Tìm và sửa nút thắt thật bằng profiling; **chứng minh nút thắt bạn tưởng trước khi profile là sai**
- [ ] ★★ Lấy một benchmark công khai, chỉ ra **≥3 lỗi phương pháp**, chạy lại đúng cách, báo cáo khác biệt
- [ ] Load test tìm điểm gãy, mô tả **chính xác cách nó gãy** (thành phần, triệu chứng, có phục hồi không), kế hoạch mở rộng có số
- [ ] Postmortem blameless cho sự cố thật: timeline tới phút, ≥3 yếu tố góp phần, action item có tiêu chí hoàn thành
- [ ] ★★ Giết ngẫu nhiên một thành phần trong lúc phục vụ tải, hệ vẫn đạt SLO; lặp cho ≥5 thành phần (kể cả thiết bị vật lý)
- [ ] Giảm ≥50% số cảnh báo mà **không** giảm khả năng phát hiện; chứng minh bằng chạy lại sự cố lịch sử
- [ ] Mỗi dependency: định nghĩa hành vi khi nó chết, cài đặt, **chứng minh bằng thử nghiệm** (không bằng code review)
- [ ] Dashboard chi phí **theo tính năng**, xác định tính năng nào có tỷ lệ chi phí/giá trị tệ nhất
- [ ] ★ Tái hiện một lỗi production trong test bằng **replay** dữ liệu thật, xác định nguyên nhân, chứng minh bản sửa

## C12 · Systems Architecture & Integration
- [ ] ★ Từ một đoạn mô tả mơ hồ, rút ≥8 ràng buộc **định lượng** (có đơn vị và số), kiểm chứng với người đặt yêu cầu
- [ ] ★★ 3 kiến trúc cho cùng bài toán, mỗi cái tối ưu một thuộc tính, bảng so sánh định lượng, bảo vệ trước 3 phản biện khác nhau
- [ ] ★ Thay đổi cài đặt một service **không phá consumer nào**, chứng minh bằng contract test chạy consumer cũ
- [ ] Vẽ riêng data flow và control flow, xác định mọi điểm giao, **chứng minh control plane chết không làm data plane chết**
- [ ] ★★ FMEA đầy đủ ≥30 chế độ hỏng, tìm **≥3 chế độ hỏng chưa từng nghĩ tới**, thêm phát hiện/giảm thiểu cho mỗi cái
- [ ] ★★ 5 chức năng: quyết định vị trí tính toán với lập luận định lượng đầy đủ (byte, độ trễ, chi phí/tháng, hành vi offline); thực hiện và đo — sai bao nhiêu?
- [ ] Bản đồ **mọi nơi** một sự thật được lưu, chỉ ra nguồn sự thật, mô tả cơ chế hòa giải khi lệch
- [ ] ★ Đọc một hệ lạ (mã nguồn mở) trong ≤4 h: xác định mẫu kiến trúc chính, vi phạm phân tầng, 2 điểm yếu
- [ ] Vẽ lại 3 kiến trúc tham chiếu từ trí nhớ; mỗi cái nêu ≥2 điểm yếu cố hữu marketing không nhắc
- [ ] Phân tích build-vs-buy thật với **chi phí thoát tính bằng người-tháng**
- [ ] ★ Migration **không downtime** cho một thành phần, 0 request thất bại trong suốt quá trình
- [ ] ★★ ADR mà **một kỹ sư lạ đọc 6 tháng sau ra được cùng quyết định** — kiểm chứng với người thật
- [ ] Review thiết kế của người khác, nêu ≥3 rủi ro họ chưa thấy, xác nhận bằng phản hồi của họ
- [ ] ★ Threat model toàn vòng `sense→act`, tìm ≥3 vector chưa từng nghĩ tới, thiết kế giảm thiểu cho mỗi cái
- [ ] **[v3]** Lấy một hệ bạn biết, vẽ theo **ISA-95**, chỉ ra chính xác tầng nào phần `learn/infer/adapt` nên nằm và vì sao; vẽ lại theo unified namespace và so sánh được/mất

## Supporting · checkpoint tổng
- [ ] **S1** Suy ra backprop cho MLP từ quy tắc chuỗi, không tra cứu
- [ ] **S1** Tính capacity cho một SLO độ trễ bằng định luật Little
- [ ] **S1** Giải thích `float32` mất chính xác ở một phép tính cụ thể trong code của bạn và sửa được
- [ ] **S2** Đọc datasheet lạ và đấu nối đúng ngay lần đầu, không cháy gì
- [ ] **S2** Debug bug do nguồn bằng oscilloscope, có ảnh waveform trước/sau
- [ ] **S2** Đo dòng ngủ ở mức µA, khớp với tính toán ngân sách năng lượng
- [ ] **S3** Tune PID trên hệ vật lý đạt chỉ tiêu, có đồ thị đáp ứng bước
- [ ] **S3** Thiết kế và chứng minh trạng thái fail-safe dưới 3 loại lỗi
- [ ] **S3** Cho một bài toán điều khiển, lập luận có nên dùng ML hay không, bằng tiêu chí
- [ ] **S3 [v3]** Thiết kế và tune một vòng **cascade** trên hệ thật, chứng minh tốt hơn vòng đơn bằng đồ thị đáp ứng nhiễu; nêu ≥2 tình huống cascade làm tệ hơn
- [ ] **S4** Threat model toàn vòng, ≥3 vector mới
- [ ] **S4** mTLS + provisioning + xoay vòng chứng chỉ, hoạt động sau khi cert cũ hết hạn
- [ ] **S4** Agent có tool không thực hiện được hành động ngoài phạm vi, kể cả khi input dẫn dụ
- [ ] **S4 [v3]** Vẽ mô hình **zone/conduit** (IEC 62443) cho hệ có cả tầng OT lẫn cloud; mỗi conduit vượt ranh giới tin cậy có biện pháp bảo vệ + **cái gì xảy ra với an toàn nếu biện pháp đó lỗi**
- [ ] **S5** Eval harness bắt regression mà unit test bỏ lọt
- [ ] **S5** ≥60% logic firmware test trên host trong CI
- [ ] **S5** Property-based test tìm ra ≥1 bug thật trong code của bạn
- [ ] **S6** FMEA ≥30 mục, ≥3 chế độ hỏng mới
- [ ] **S6** Chứng minh fail-safe dưới ≥3 loại lỗi
- [ ] **S6** Đo thời gian phát hiện cho mỗi cơ chế giám sát, dưới ngưỡng đặt ra
- [ ] **S7** Bảo vệ lựa chọn kiến trúc bằng bảng chi phí + độ trễ trước 3 phản biện
- [ ] **S7** Dự đoán độ trễ khi utilization tăng, đo xác nhận
- [ ] **S7** Tính điểm hòa vốn tự host vs API cho workload inference của bạn
- [ ] **S8** Design doc mà kỹ sư lạ **thực thi được không cần hỏi lại** — kiểm chứng với người thật
- [ ] **S8** ADR mà người đọc 6 tháng sau ra cùng quyết định
- [ ] **S8** README cho một dự án mà người mới chạy được trong ≤30 phút

## Adjacent · checkpoint tổng
- [ ] **A1** Hệ ROS 2 ≥3 node giao tiếp qua topic, ghi và phát lại rosbag
- [ ] **A1** Kiến trúc an toàn cho máy chuyển động, lớp phần cứng độc lập với phần mềm
- [ ] **A2** HIL tối giản: firmware thật + cảm biến giả lập, test tự động
- [ ] **A2** Đo chênh lệch hiệu năng mô phỏng vs thực tế, giải thích nguồn
- [ ] **A3** Liệt kê mọi chế độ của hệ, kiểm tra người dùng luôn biết đang ở chế độ nào
- [ ] **A3** Luồng escalation đầy đủ với ngữ cảnh bàn giao, đo thời gian quyết định của người
- [ ] **A3** Dashboard trả lời "hệ có khỏe không" trong ≤10 giây
- [ ] **A4** 5 công việc: quyết định tự động hóa hay không, có tiêu chí
- [ ] **A4** Tính chi phí thật của mỗi loại lỗi, chỉnh ngưỡng model theo đó
- [ ] **A5** Xếp hệ vào tầng rủi ro EU AI Act, liệt kê nghĩa vụ
- [ ] **A5** Quy trình xóa dữ liệu hoạt động xuyên mọi bản sao và cache
- [ ] **A6** Kiểm tra toàn bộ dependency, xác định nghĩa vụ giấy phép của bạn
- [ ] **A6** Với mỗi model dùng: xác định được phép làm gì với output

## Project · nghiệm thu
- [ ] **P1** Chạy 6 h liên tục; dựng lại từ đầu trong một buổi không copy-paste; giải thích từng dòng firmware
- [ ] **P2a** 10.000 kết nối đồng thời, không rò rỉ fd sau 1 triệu kết nối
- [ ] **P2b** Kill ngẫu nhiên ≥200 lần trong lúc ghi, mọi giá trị đã ack vẫn đọc được
- [ ] **P2c** `cat | grep | wc > out` chạy đúng; Ctrl-C giết đúng tiến trình; không zombie
- [ ] **P3** 30 ngày ngoài bàn làm việc không can thiệp; phát hiện đúng bất thường ≥3 lần độc lập; OTA thành công trong lúc triển khai
- [ ] **P4** Hạ tầng dựng lại từ zero bằng một lệnh; test đồng bộ hàng loạt pass có đồ thị; restore thật thành công
- [ ] **P5** Throughput ≥2× baseline có giải thích cơ chế; ở 3× tải từ chối rõ ràng thay vì sập; bảng so sánh tự host vs API có điểm hòa vốn
- [ ] **P6** 90 ngày vận hành, ≥5 SLI đạt ≥95%; chaos ≥5 thành phần; giải thích mọi quyết định bằng audit log; ≥1 postmortem action item hoàn thành; kỹ sư lạ vận hành được trong 1 ngày
- [ ] **P7** Migration không downtime 0 request thất bại **hoặc** ≥1 PR có ý nghĩa được merge

---

## Cách dùng master checklist

**Đây là tài liệu công tác chính của bạn**, không phải phụ lục trang trí.

| Nhịp | Việc |
|---|---|
| Hàng tuần | Tick những gì đạt được; ghi ngày bên cạnh |
| Hàng tháng | Đếm % đã tick theo nhánh; so với mức mục tiêu ở §6 |
| Khi tuyên bố một nhánh "xong" | **Mọi** checkpoint của nhánh đó phải tick. Không có ngoại lệ |
| Khi chuẩn bị phỏng vấn | Mỗi checkpoint đã tick là một câu chuyện cụ thể bạn kể được |
| Khi nghi ngờ bản thân | Đếm số đã tick. Đó là bằng chứng, cảm giác thì không |

## Thói quen liên tục — kiểm hằng tuần, không phải checkpoint một lần

- [ ] Sổ **"khái niệm vendor ↔ khái niệm trung lập"** (§2.3d, Phụ lục D.4) — thêm ≥2 cặp mỗi tuần
- [ ] Giờ tự học tuần này: ___ / mục tiêu 12–18
- [ ] Tuần này tôi có tự học đúng thứ công việc đang dạy không? (nếu có → **mất ngân sách**, xem §9.2 quy tắc 1)
- [ ] Mô tả năng lực của tôi trong 3 câu **không dùng tên sản phẩm nào** — làm được không?

**Kiểm tra mốc tháng 12:** làm bài 5 câu ở **Phụ lục D.5** để xác minh giả định "công việc cấp kỹ thuật thật".

---

**Tổng số checkpoint:**

---

# PHỤ LỤC D · BẢN ĐỒ CÔNG VIỆC ↔ ROADMAP

**Mục đích:** trả lời một câu hỏi duy nhất — *giờ tự học khan hiếm của tôi nên đi vào đâu?*

**Nguyên tắc:** nhãn core/supporting/adjacent ở §3 **không đổi** theo bảng này. Bảng này nói về **chi phí thu nhận**, không nói về **tầm quan trọng**. Một nhánh adjacent mà công việc cấp miễn phí vẫn là adjacent — bạn chỉ may mắn được nó rẻ.

## D.1 — Bốn nhóm nhánh

| Nhóm | Đặc điểm | Chiến lược |
|---|---|---|
| **① Công việc không bao giờ cho** | Không có nguồn nào khác ngoài tự học | **Ưu tiên tuyệt đối.** Mất ngân sách ở đây là mất vĩnh viễn |
| **② Công việc cho một phần** | Cần bổ sung có mục tiêu | Xác định **chính xác** phần thiếu, chỉ học phần đó |
| **③ Công việc cho phần lớn** | Chỉ cần hệ thống hóa | Học **sau khi** gặp ở công việc, không học trước |
| **④ Công việc cho, nhưng cần dịch** | Có nguyên liệu, thiếu từ vựng chuyển nhượng | Thói quen dịch §2.3d, không cần giờ riêng |

## D.2 — Bảng đầy đủ 26 nhánh

| Nhánh | Nhãn | Nhóm | Công việc cấp gì | Tự học phải mua gì | Giờ tự học |
|---|---|---|---|---|---|
| **C1** Programming & runtimes | core | **①** | Gần như không (ST/ladder khác mô hình) | Toàn bộ C, Python, Go/Rust, debug, build, git, design | **280** |
| **C2** DSA | core | **①** | Không | Toàn bộ | **180** |
| **C3** Computer architecture | core | **①** | Không | Toàn bộ | **200** |
| **C4** OS & concurrency | core | **①②** | Khái niệm tất định, chu kỳ, ưu tiên (qua PLC) | Bộ nhớ ảo, I/O model, concurrency, container, eBPF | **240** |
| **C5** Networking | core | **②** | Giao thức công nghiệp (C5.16), mạng nhà máy | TCP/IP sâu, HTTP, TLS, socket, mạng cloud, chế độ hỏng | **160** |
| **C6** Embedded & firmware | core | **②④** | Mô hình PLC/DCS (C6.16), I/O, thời gian thực | Firmware MCU, bare-metal, RTOS, DMA, OTA, năng lượng, inference trên thiết bị | **200** |
| **C7** Sensing & signals | core | **③②** | Instrumentation, hiệu chuẩn, nhiễu, actuation thật | **DSP, FFT, lọc số, sensor fusion, trích đặc trưng cho ML** | **80** |
| **C8** ML & inference systems | core | **①** | **Không gì cả** | **Toàn bộ — và đây là cung `learn/infer` của vòng lặp** | **320** |
| **C9** Data engineering | core | **①②** | Historian ở mức người dùng | Mô hình dữ liệu, SQL sâu, transaction, time-series hiện đại, streaming, ingest từ edge | **190** |
| **C10** Distributed & cloud | core | **①** | Không | Toàn bộ | **200** |
| **C11** Observability & performance | core | **①②** | Commissioning debug, alarm (từ vựng khác) | Metric/log/trace/profile, SLO, benchmark, chaos, hàng đợi | **130** |
| **C12** Systems architecture | core | **②④** | **Thực hành**: tích hợp đa bên, commissioning xuyên tầng, ISA-95 trong thực tế | **Từ vựng và khung**: pattern, ADR, đánh đổi định lượng, FMEA có hệ thống, edge-cloud | **80** |
| **S1** Mathematics | supporting | **①** | Không | Toàn bộ | **220** |
| **S2** Electronics & power | supporting | **③** | Mạch thật, nguồn thật, đo thật, tải thật | Điện tử số mức MCU, power budget µA | **30** |
| **S3** Control theory | supporting | **③②** | Vòng kín thật, đối tượng thật, tuning thật, an toàn | Toán điều khiển, Kalman, control vs learned policy | **30** |
| **S4** Security | supporting | **②** | An ninh OT khi gặp (S4.9) | Threat modeling, identity, crypto, **bảo mật ML** | **60** |
| **S5** Testing & verification | supporting | **①②** | FAT/SAT, nghiệm thu | Test tự động, CI, property-based, **test hệ phi tất định** | **50** |
| **S6** Reliability & safety | supporting | **③④** | Bảo vệ, interlock, dự phòng, an toàn thật | FMEA có hệ thống, fault tree | **20** |
| **S7** Queueing & economics | supporting | **①** | Ngân sách dự án | Little's law, capacity, cost-per-inference, TCO phần mềm | **20** |
| **S8** Technical communication | supporting | **③②** | Spec, báo cáo, biên bản nghiệm thu | ADR, RFC, postmortem, C4 | **20** |
| **A1** Robotics | adjacent | **②** | Actuation, an toàn máy chuyển động | ROS 2, perception, SLAM, planning | **40** |
| **A2** Simulation | adjacent | **②** | Mô phỏng trước commissioning | HIL tự dựng, dữ liệu tổng hợp, sim-to-real | **30** |
| **A3** Human factors | adjacent | **③②** | HMI thật, người vận hành thật | Lý thuyết autonomy levels, mode confusion | **25** |
| **A4** Business & operations | adjacent | **③** | Quy trình, tiến độ, nhà thầu, ràng buộc thật | ROI kỹ thuật, tiêu chí tự động hóa | **10** |
| **A5** Standards & regulation | adjacent | **③②** | Grid code, tiêu chuẩn thiết bị, chứng nhận | EU AI Act, bảo vệ dữ liệu | **15** |
| **A6** Licensing & IP | adjacent | **①** | Rất ít | Toàn bộ | **30** |

## D.3 — Thứ tự ưu tiên tuyệt đối cho giờ tự học

Khi bạn chỉ có 6 giờ trong một tuần, dùng thứ tự này:

```
1. C8   ML & inference systems       ← cung learn/infer, KHÔNG có nguồn khác
2. C10  Distributed & cloud          ← KHÔNG có nguồn khác
3. C2   DSA        ┐
4. C3   Computer architecture  ├──── KHÔNG có nguồn khác, và là nền
5. C1   Programming            ┘
6. C4   OS & concurrency             ← phần lớn không có nguồn khác
7. S1   Mathematics                  ← chặn C8
8. C9   Data engineering
9. C11  Observability
10. C5  Networking (phần IT)
11. C6  Embedded (phần MCU)
12. phần còn lại
```

**Lý do C8 đứng đầu, không phải C1:** C1 chậm hơn nhưng bạn *sẽ* học được nó vì mọi project đều cần. C8 thì không có gì ép bạn — và nó là cung duy nhất mà cả công việc lẫn toàn bộ ngành OT quanh bạn đều đang thiếu. Bỏ C8 thì roadmap này biến thành "kỹ sư tự động hóa biết thêm ít phần mềm", không phải Intelligent Systems Integration Engineering.

## D.4 — Chín thứ ở công việc cần dịch ngay sang khái niệm trung lập

*Đây là bảng §2.3d mở rộng. Làm hằng tuần, mỗi lần gặp một cái mới. Ghi vào một file duy nhất.*

| Bạn thấy | Khái niệm trung lập | Nhánh | Vì sao quan trọng |
|---|---|---|---|
| Scan cycle, cycle time monitoring | Vòng lặp tất định, WCET, jitter, ngân sách thời gian | C4.10, C6.15, C6.16 | Mọi hệ real-time đều có khái niệm này |
| OB chu kỳ, OB ngắt | ISR, lập lịch rate-monotonic, phân tích khả năng lập lịch | C4.2, C6.2 | |
| Hardware config, GSD/GSDML | Mô tả thiết bị, device tree, khám phá thiết bị | C4.12, C6.1 | |
| Profinet IRT, distributed clock | Mạng thời gian thực, đồng bộ đồng hồ, PTP | C5.3, C7.9 | Nối thẳng sang hệ phân tán |
| Alarm class, alarm suppression | Thiết kế cảnh báo, triệu chứng vs nguyên nhân, mệt mỏi cảnh báo | C11.11, A3 | **Cùng bài toán, khác từ vựng hoàn toàn** |
| Redundancy H-system, hot standby | Dự phòng nóng, chuyển đổi dự phòng, split-brain, fencing | S6.3, C10.4 | |
| Historian, trend, compression | Lưu trữ chuỗi thời gian, downsampling, retention | C9.5 | |
| Interlock, permissive, trip | Fail-safe, giới hạn cứng, cô lập lỗi | S6.3, C7.11 | |
| FAT / SAT / punch list | Tiêu chí nghiệm thu, contract test, regression suite | S5.4, C12.3 | |

**Cách dùng:** mỗi tuần thêm ít nhất 2 dòng. Sau 1 năm bạn có ~100 cặp. Đó là lúc bạn nói được về công việc của mình bằng ngôn ngữ mà một kỹ sư phần mềm hiểu — và ngược lại. **Đó chính là năng lực liên ngành, ở dạng cụ thể nhất.**

## D.5 — Kiểm tra lại bảng này ở tháng 12

Toàn bộ Phụ lục D dựa trên một giả định chưa kiểm chứng: **công việc sẽ cấp kỹ thuật thật, không phải chủ yếu giấy tờ và giám sát nhà thầu.** Đây là điều không chắc số 9 ở §15.3.

Ở tháng 12, làm bài kiểm tra này:

| Câu hỏi | Nếu "có" | Nếu "không" |
|---|---|---|
| Tôi đã tự cấu hình/lập trình một hệ điều khiển chưa? | C6.16 đang được cấp | Chuyển C6 sang nhóm ① |
| Tôi đã đấu nối, hiệu chuẩn, hoặc debug cảm biến thật chưa? | C7, S2 đang được cấp | **Chuyển C7 và S2 sang nhóm ①: +200 h tự học** |
| Tôi đã tune hoặc sửa một vòng điều khiển chưa? | S3 đang được cấp | Chuyển S3 sang nhóm ①: +60 h |
| Tôi đã tham gia commissioning và tự tìm ra ≥1 lỗi chưa? | C11, C12 đang được cấp | Chuyển sang nhóm ①: +150 h |
| Sổ dịch khái niệm của tôi có ≥60 cặp chưa? | Thói quen §2.3d đang chạy | Thói quen chưa hình thành — sửa trước khi làm gì khác |

**Nếu ≥3 câu trả lời "không":** ngân sách tự học phải gánh thêm ~400 h, và điều đó có nghĩa timeline giãn thêm 1–1,5 năm, **hoặc** bạn cần đổi vị trí trong công ty sang vai trò kỹ thuật hơn. Cả hai đều là quyết định hợp lệ; điều không hợp lệ là không nhận ra và tiếp tục dùng bảng này như thể nó đúng.

---

*Kết thúc tài liệu · v3.0 · 14/09/2026*
*Cập nhật khi: ước lượng sai · đổi spine · đổi việc · tài nguyên biến mất · một điều ở §15.3 được chứng minh hoặc bác bỏ.*

## Nhật ký cập nhật

| Ngày | Thay đổi | Lý do |
|---|---|---|
| 14/09/2026 | v1.0 — bản đầu, nhiều nhánh nén | — |
| 14/09/2026 | v2.0 — mở rộng đầy đủ, không nhánh nào nén | Xác nhận ngân sách phần cứng và thời gian |
| 14/09/2026 | **v3.0** — hiệu chỉnh tình huống nghề nghiệp | Đã đi làm: kỹ sư tự động hóa, EPC không O&M, đích liên ngành. **Giữ nguyên 38 lĩnh vực**; đổi trình tự, ngân sách giờ, và bổ sung 5 leaf lấp lỗ hổng tầng công nghiệp (C5.16, C6.16, S3.8, S4.9, C12.15) |
| | | |
