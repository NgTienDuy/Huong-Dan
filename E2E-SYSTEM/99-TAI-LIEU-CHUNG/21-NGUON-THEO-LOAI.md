---
loai: meta
ma: M21
tieu_de: "Nguồn theo loại — tìm ở đâu, lấy thế nào"
---

# 21 · Nguồn theo loại — tìm ở đâu, lấy thế nào

> Bổ sung cho [`19-CACH-TIM-TAI-LIEU.md`](19-CACH-TIM-TAI-LIEU.md) (phương pháp) và [`20-TU-DIEN-VI-EN.md`](20-TU-DIEN-VI-EN.md) (từ khoá).
> Danh sách tài nguyên **cụ thể theo nhánh** đã có sẵn trong file `*.0-INDEX.md` của từng nhánh — trích từ roadmap §5 và §13. File này nói về **loại nguồn** và **đường lấy**, thứ mà roadmap không nói.

---

## 1 · Nhánh nào dùng loại nguồn nào

Đây là bảng quan trọng nhất của file. Chọn sai loại nguồn là cách phí giờ nhanh nhất.

| Nhánh | Nguồn cấp 1 (T0) | Nguồn chính để học | Nguồn cho chế độ hỏng |
|---|---|---|---|
| **C1** Programming | Chuẩn ngôn ngữ, docs toolchain, source thư viện chuẩn | Sách + tự viết | Bug tracker, UB sanitizer |
| **C2** DSA | Paper gốc của thuật toán | **Sách + lecture notes** — nhánh mà sách thắng tuyệt đối | Tự phá: dữ liệu xấu nhất |
| **C3** Architecture | Optimization manual của Intel/ARM, tài liệu PMU | Sách kiến trúc + nand2tetris | Tự đo bằng `perf` |
| **C4** OS | **man page**, kernel documentation, POSIX | Sách OS + source | lwn.net, kernel mailing list |
| **C5** Networking | **RFC** | Sách + **packet capture của chính bạn** | Postmortem sự cố mạng công khai |
| **C6** Embedded | **Datasheet + reference manual + errata** | Application note của nhà sản xuất | Errata (đọc kỹ), forum của vendor |
| **C7** Sensing | Datasheet cảm biến, app note TI/ADI | Sách DSP | Tự gây lỗi cảm biến trong lab |
| **C8** ML | **Paper trên arXiv**, docs của engine | Khoá học + paper | Model card, báo cáo eval, incident của nhà cung cấp |
| **C9** Data | Docs của chính DB bạn chạy + paper gốc | Sách dữ liệu | Jepsen, postmortem về mất dữ liệu |
| **C10** Distributed | **Paper kinh điển** + docs hệ thật | Sách + paper | **Jepsen reports** — không có nguồn nào thay được |
| **C11** Observability | Spec OpenTelemetry, docs công cụ | SRE book, AWS Builders' Library | **Postmortem công khai** — đây *là* nội dung của nhánh |
| **C12** Architecture | ADR công khai, kiến trúc tham chiếu của vendor | Sách kiến trúc | Báo cáo dự án thất bại, postmortem |
| **S1** Math | — | **Sách + lecture notes**, không cần gì khác | Bài tập sai |
| **S2** Electronics | **Datasheet**, app note TI/ADI | Sách mạch | Tự làm cháy trong lab (có kiểm soát) |
| **S3** Control | Tài liệu tuning của vendor DCS/PLC | Sách điều khiển | **Hệ thật ở công ty bạn** |
| **S4** Security | NIST SP, OWASP, IEC 62443 | Sách + hướng dẫn cơ quan | CVE, advisory của CISA cho ICS |
| **S5** Testing | Docs framework | Sách + paper property-based testing | Test bất ổn của chính bạn |
| **S6** Reliability | IEC 61508 (qua bản tóm tắt vendor) | Sách độ tin cậy | **Báo cáo điều tra tai nạn** (hàng không, hạt nhân) |
| **S7** Economics | Bảng giá nhà cung cấp cloud | Sách hàng đợi + bài viết capacity | Hoá đơn cloud của chính bạn |
| **S8** Communication | ADR/RFC công khai của dự án mở | Sách viết kỹ thuật | Design doc bị hiểu sai |
| **A1** Robotics | Docs ROS 2 | Sách robotics | Báo cáo tai nạn robot công nghiệp |
| **A2** Simulation | Docs công cụ mô phỏng | Paper domain randomization | Chênh lệch sim–real của chính bạn |
| **A3** Human factors | Báo cáo điều tra tai nạn hàng không | Sách human factors | **Chính báo cáo tai nạn** |
| **A4** Business | — | Sách vận hành | Dự án tự động hoá thất bại quanh bạn |
| **A5** Standards | **Văn bản gốc của luật/tiêu chuẩn** | Hướng dẫn của cơ quan quản lý | Án phạt, quyết định xử lý công khai |
| **A6** Licensing | **Văn bản giấy phép gốc** | choosealicense, SPDX | Vụ kiện và tranh chấp giấy phép |

**Đọc bảng này thế nào:** nếu bạn đang học C5 mà nguồn duy nhất là một video YouTube, bạn đang làm sai. Nếu bạn đang học C11 mà chỉ đọc sách, bạn cũng đang làm sai — nhánh đó sống bằng postmortem.

---

## 2 · Nguồn gốc (T0) — sáu loại và đường lấy

### 2.1 · RFC và chuẩn Internet
- Toàn bộ RFC **miễn phí, không cần đăng ký**: `rfc-editor.org`, tra cứu theo tiến trình ở `datatracker.ietf.org`.
- Đọc **RFC 2119** trước tiên (1 trang): nó định nghĩa nghĩa chính xác của MUST / SHOULD / MAY, và chi phối cách đọc mọi spec sau đó.
- Mẹo: RFC mới thường **thay thế** RFC cũ. Kiểm tra mục "Obsoletes / Obsoleted by" trước khi đọc.

### 2.2 · Tiêu chuẩn công nghiệp — cái nào miễn phí, cái nào phải mua

Đây là chỗ nhiều người bỏ cuộc vì tưởng "phải mua hết". Thực tế:

| Miễn phí | Phải mua / hạn chế |
|---|---|
| **OPC UA**: OPC Foundation công bố công khai toàn bộ specification đã phát hành, kèm guideline và whitepaper, cả bản duyệt trực tuyến có liên kết chéo | IEC 61131-3 (ngôn ngữ PLC) |
| **Modbus**: spec công khai trên trang của tổ chức Modbus | IEC 61850 (tự động hoá trạm) |
| **NIST SP 800-82** — hướng dẫn bảo mật OT/ICS, rất chi tiết, miễn phí | IEC 62443 (bản đầy đủ) |
| Advisory ICS của CISA — chế độ hỏng và lỗ hổng thật, miễn phí | ISA standards |
| Whitepaper của Siemens / ABB / Rockwell giải thích chuẩn mà sản phẩm họ tuân theo | ISO 26262, IEC 61508 |
| Tài liệu PLCopen, tài liệu tổ chức EtherCAT (đăng ký miễn phí) | |

**Chiến lược khi tiêu chuẩn phải mua:** đừng mua trước. Thứ tự đúng là (1) whitepaper vendor → (2) hướng dẫn cơ quan/hiệp hội miễn phí → (3) sách giải thích chuẩn → (4) chính hệ thống ở công ty bạn → và chỉ mua bản gốc khi cần con số chính xác để viết spec hoặc để tranh luận. Công ty EPC của bạn nhiều khả năng **đã có** một số tiêu chuẩn — hỏi trước khi mua.

### 2.3 · Datasheet, reference manual, errata, application note
- Lấy trực tiếp từ trang nhà sản xuất chip (ST, TI, Analog Devices, NXP, Nordic, Microchip…), không lấy từ trang tổng hợp — trang tổng hợp hay giữ bản cũ.
- **Ba tài liệu khác nhau, đừng nhầm:** datasheet (đặc tính điện, chân) · reference manual (thanh ghi, peripheral) · **errata** (lỗi silicon đã biết).
- **Errata là tài liệu bị bỏ qua nhiều nhất và gây mất nhiều ngày nhất.** Quy tắc: mở errata **trước khi** viết dòng driver đầu tiên.
- **Application note của TI và Analog Devices** về nguồn, nhiễu, nối đất, đo lường thuộc hàng tài liệu kỹ thuật tốt nhất tồn tại, miễn phí, và gần như không ai đọc. Roadmap S2 nói đúng điều này.

### 2.4 · man page và tài liệu chính thức của dự án
- `man 2 <syscall>` và `man 7 <topic>` là T0 cho C4. Đọc mục **ERRORS** và **NOTES** — đó là chỗ chứa thông tin thật.
- Với mọi hệ bạn chạy trong production (PostgreSQL, Kubernetes, Redis, Kafka…): docs chính thức **của đúng phiên bản bạn chạy**, không phải phiên bản mới nhất.

### 2.5 · Paper
- `arxiv.org` cho ML và hệ thống hiện đại; Google Scholar / Semantic Scholar để lần theo trích dẫn.
- Cách đọc paper trong 20 phút: abstract → hình vẽ và bảng → phần đánh giá (evaluation) → giới hạn (limitations) → chỉ đọc phương pháp nếu vẫn cần.
- Với C10, **paper kinh điển đọc một lần là đủ cho 5 năm** — chúng thuộc tầng 1 của §8 roadmap.
- Nếu paper bị tường phí: tìm bản preprint trên trang cá nhân của tác giả, hoặc trang lab của họ. Gần như luôn có.

### 2.6 · Mã nguồn như một nguồn tài liệu
Roadmap có hẳn một leaf cho việc này (C1.11). Cách đọc: bắt đầu từ **test**, không từ `main()`. Test cho bạn biết tác giả nghĩ gì là quan trọng. Sau đó lần theo một đường dữ liệu duy nhất, từ đầu vào tới đầu ra, bỏ qua mọi thứ khác.

---

## 3 · Sách

### Cách chọn sách trong 15 phút
1. Tìm 3 ứng viên: `<topic> textbook "table of contents"`.
2. Đọc **mục lục** cả 3. Cuốn nào có chương đúng với sub-leaf bạn đang chặn thì thắng.
3. Đọc 2 trang bất kỳ ở giữa sách. Nếu phải đọc lại 3 lần mới hiểu một câu → sai trình độ, đổi cuốn.
4. Chọn, bắt đầu, **không tìm cuốn thứ tư**.

### Cách đọc
Không đọc tuần tự. Đọc **chương đang chặn**, theo thứ tự học ghi trong file `*.0-INDEX.md` của nhánh. Một cuốn sách 800 trang thường chỉ có 150 trang liên quan tới bạn trong năm nay.

### Sách miễn phí hợp pháp
Nhiều sách kinh điển được chính tác giả phát hành miễn phí. Ví dụ đã kiểm chứng: *Operating Systems: Three Easy Pieces* của Arpaci-Dusseau là sách hệ điều hành miễn phí trực tuyến, và tác giả cam kết bản PDF luôn miễn phí; bản in có bán riêng.

Roadmap §5 và §13 đã đánh dấu sẵn những cuốn **miễn phí** trong danh sách tài nguyên của từng nhánh — ví dụ *Mathematics for Machine Learning*, *Modern Robotics*, *Introduction to Probability* (Blitzstein), *Mathematics for Computer Science* (MIT 6.042). Mở file `*.0-INDEX.md` của nhánh và tìm chữ "miễn phí".

**Cách kiểm tra một cuốn có bản miễn phí hợp pháp không:** tìm `<tên sách> author site` hoặc `<tên sách> free pdf author` và chỉ nhận bản nằm trên **trang của tác giả hoặc trường đại học của họ**. Bản trên các trang tổng hợp lạ thường là bản lậu và thường là bản cũ.

### Mua sách hợp pháp mà rẻ
- Nhà xuất bản kỹ thuật thường bán ebook DRM-free giảm sâu theo đợt (No Starch, Pragmatic Bookshelf, Manning).
- Bundle theo chủ đề (Humble Bundle) định kỳ có gói sách kỹ thuật với giá rất thấp.
- Thư viện đại học ở Hà Nội có quyền truy cập một số cơ sở dữ liệu sách và tạp chí kỹ thuật — đáng hỏi nếu bạn có quan hệ với một trường.
- Công ty EPC thường có ngân sách đào tạo và **có sẵn tiêu chuẩn đã mua**. Hỏi trước khi tự bỏ tiền.

> Đừng dùng nguồn lậu. Không phải vì đạo đức trừu tượng — mà vì A6 là một nhánh trong chính roadmap của bạn, và vì bản lậu thường là bản cũ, thiếu errata, thiếu chương sửa.

---

## 4 · Khoá học và bài giảng

| Nguồn | Dùng cho | Lưu ý |
|---|---|---|
| **MIT OpenCourseWare** | C2, C3, C4, S1 | Có problem set và solution — phần giá trị nhất, không phải video |
| Khoá công khai của Stanford, CMU, Berkeley | C8, C10 | Tìm `<trường> <mã môn> lecture notes` |
| **NPTEL** (Ấn Độ) | S3 điều khiển, C7 tín hiệu, điện tử | Rất mạnh ở mảng kỹ thuật điện/điều khiển |
| Coursera / edX chế độ audit | C8 | Xem miễn phí, chỉ trả tiền nếu cần chứng chỉ |
| Kênh YouTube của chính trường đại học | mọi nhánh | Khác với "video tutorial" — đây là T2 |

**Quy tắc:** với khoá học, **problem set quan trọng hơn video**. Nếu một khoá không có bài tập chấm được, nó là giải trí có cấu trúc.

---

## 5 · Nguồn chế độ hỏng thật (T4) — phần sách không có

Đây là loại nguồn mà người tự học hay bỏ qua, và là chỗ tạo khác biệt lớn nhất.

- **Postmortem công khai** của các công ty vận hành hệ thật. Tìm: `<công ty> postmortem <hiện tượng>`, `<công ty> incident report`.
- **AWS Builders' Library** — các bài viết về timeout, retry, backpressure, load shedding; ngắn, thực chiến, miễn phí.
- **Google SRE book** — bản đọc trực tuyến miễn phí.
- **Jepsen** — báo cáo kiểm chứng tính nhất quán của các hệ CSDL phân tán. Với C9 và C10, đây là nguồn không thứ gì thay được.
- **Báo cáo điều tra tai nạn** (hàng không, công nghiệp) cho S6 và A3. Roadmap A3 nói rõ: phần lớn tai nạn hệ tự động nằm ở giao diện người–máy.
- **Advisory ICS của CISA** cho S4.9 — lỗ hổng thật trên thiết bị công nghiệp thật, cập nhật liên tục.
- **CVE và security advisory** của chính các thiết bị bạn gặp ở công trường.

---

## 6 · Nguồn đặc thù cho hoàn cảnh của bạn

Bạn có một nguồn mà 99% người học roadmap này **không có**: một công ty EPC với hệ thống Siemens và ABB thật, và một chu kỳ dự án đầy đủ từ thiết kế tới chạy thử.

| Nguồn | Lấy thế nào | Nhánh nó phục vụ |
|---|---|---|
| **Tài liệu kỹ thuật của Siemens / ABB** | Cổng tài liệu công khai của hãng — manual, function manual, application example. Miễn phí, rất chi tiết | C6.16, S3.8, C5.16, C12.15 |
| **Hồ sơ dự án ở công ty** | P&ID, I/O list, network diagram, FAT/SAT protocol, punch list | C12, S5.4, S6 |
| **Chính thiết bị trong giai đoạn chạy thử** | Xin vào commissioning, mang laptop và Wireshark | C5.16, C7, S3 |
| **Kỹ sư kỳ cựu ở công trường** | Hỏi *"cái này hỏng kiểu gì?"* thay vì *"cái này là gì?"* | S6, A3, C11 |
| **Biên bản sự cố / báo cáo bất thường của dự án** | Đây là postmortem, chỉ là không ai gọi nó như vậy | C11.9 |

**Cách biến nguồn này thành kiến thức chuyển nhượng được:** mỗi lần gặp một thứ ở công trường, viết ngay 1 dòng vào [`12-SO-DICH-OT-IT.md`](12-SO-DICH-OT-IT.md). Không dịch sang khái niệm trung lập thì kinh nghiệm đó chỉ dùng được ở đúng công ty này.

> ⚠ Kiểm tra quy định của công ty trước khi mang tài liệu dự án ra ngoài hoặc đưa lên kho công khai. Ghi chú **khái niệm** thì an toàn; sao chép **hồ sơ** thì không. Nhánh A6.4 nói về chính chuyện này.

---

## 7 · Tiếng Việt: dùng khi nào

| Dùng | Không dùng |
|---|---|
| Lần tiếp xúc đầu với một khái niệm hoàn toàn lạ, để có trực giác (≤20% thời gian) | Làm nguồn chính cho bất kỳ leaf nào từ mức `Wo` trở lên |
| Toán nền và điện tử cơ bản, nếu bạn học nhanh hơn bằng tiếng Việt | Bất kỳ thứ gì thuộc C1–C12 ở mức `In` trở lên |
| Trao đổi với đồng nghiệp, biên bản nội bộ, đào tạo người khác | Thuật ngữ trong ghi chú của bạn (xem §1 quy tắc 2 của file 19) |
| Cộng đồng tự động hoá / PLC trong nước để hỏi về thiết bị và thực tiễn Việt Nam | Sách dịch của sách kỹ thuật tiếng Anh |

Thực tế cần chấp nhận: ở các mức `Ad`/`Ex` mà roadmap đặt ra cho C1–C12, tài liệu tiếng Việt tương đương **không tồn tại**. Đây không phải vấn đề của bạn để giải — chỉ là điều kiện biên cần chấp nhận sớm.

---

## 8 · Quản lý nguồn

Không cần công cụ phức tạp. Ba quy tắc là đủ:

1. **Nguồn sống trong file leaf, không trong trình duyệt.** Mục *7 · Tài nguyên đã dùng thật* của mỗi leaf. Bookmark không tính là đã đọc.
2. **Ghi vị trí chính xác, không ghi link trần.** `[T1] CS:APP §6.4.2` tra lại được sau 3 năm; một URL thì không chắc.
3. **Lưu bản PDF của mọi thứ T0.** Spec, datasheet, errata, RFC — chúng bị thay thế, rút xuống, đổi số hiệu. Cất vào [`98-TAI-LIEU-GOC/`](../98-TAI-LIEU-GOC/00-DOC-TRUOC.md), đặt tên `<mã>-<phiên bản>-<ngày tải>.pdf`. Quy ước đầy đủ nằm trong file đó.

---

## ✎ Nguồn của tôi theo loại

| Loại | Nguồn cụ thể tôi đã dùng và thấy tốt | Nhánh | Đánh giá 1–5 |
|---|---|---|---|
| Spec / tiêu chuẩn |  |  |  |
| Datasheet / app note |  |  |  |
| Sách |  |  |  |
| Khoá học |  |  |  |
| Postmortem / T4 |  |  |  |
| Nguồn từ công việc |  |  |  |

## ✎ Tiêu chuẩn tôi cần mà chưa có

| Tiêu chuẩn | Cần cho leaf | Công ty có sẵn? | Đường thay thế miễn phí | Ngày |
|---|---|---|---|---|
|  |  | ☐ |  |  |
