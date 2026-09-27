---
loai: meta
ma: M17
---
# 17 · Bối cảnh gốc — giả định, domain, north star

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

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

---

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

---

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
---

## ✎ Phần của tôi — theo dõi

| Ngày | Giả định nào đã sai | Hệ quả | Đã sửa gì |
|---|---|---|---|
|  |  |  |  |

