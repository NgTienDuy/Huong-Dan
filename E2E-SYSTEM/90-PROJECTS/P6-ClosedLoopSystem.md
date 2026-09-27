---
loai: project
ma: P6
trang_thai: chua-bat-dau
gio_du_kien: "*end-to-end* — tháng 36–54 — ~500 h"
---
# P6 · CLOSED-LOOP INTELLIGENT SYSTEM

***end-to-end* — tháng 36–54 — ~500 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

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

---

## ✎ Nhật ký thực thi

| Ngày | Milestone | Giờ | Kết quả | Chặn ở đâu |
|---|---|---|---|---|
|  |  |  |  |  |

## ✎ ADR — quyết định không hiển nhiên

| # | Quyết định | Phương án bị loại | Lý do | Ngày |
|---|---|---|---|---|
|  |  |  |  |  |

## ✎ Nghiệm thu

| Tiêu chí | Đạt | Bằng chứng | Ngày |
|---|---|---|---|
|  | ☐ |  |  |

## ✎ Hậu kiểm

**Cái gì tôi sẽ làm khác lần sau:**

**Leaf nào project này chứng minh tôi CHƯA nắm:**

