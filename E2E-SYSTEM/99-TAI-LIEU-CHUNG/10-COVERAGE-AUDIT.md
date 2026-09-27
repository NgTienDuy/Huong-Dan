---
loai: meta
ma: M10
---
# 10 · Coverage audit

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

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
---

## ✎ Phần của tôi — theo dõi

**Chạy mỗi quý.**

| Ngày audit | Leaf ☐ | Leaf ◐ | Leaf ● | Leaf ★ | Lỗ hổng lớn nhất | Hành động |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

