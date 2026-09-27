---
loai: project
ma: P7
trang_thai: chua-bat-dau
gio_du_kien: "tháng 48+ — ~200 h"
---
# P7 · LÀM CỨNG HOẶC ĐÓNG GÓP NGƯỢC

**tháng 48+ — ~200 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

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

