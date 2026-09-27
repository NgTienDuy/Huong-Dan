---
loai: meta
ma: M11
---
# 11 · Reassessment + STATE block

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

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
---

## ✎ Phần của tôi — theo dõi

**Cập nhật khi:** ước lượng sai · đổi spine · đổi việc · tài nguyên biến mất · một điều ở §15.3 được chứng minh hoặc bác bỏ.

| Ngày | Cái gì đổi | Ảnh hưởng tới roadmap | Đã sửa file nào |
|---|---|---|---|
|  |  |  |  |

