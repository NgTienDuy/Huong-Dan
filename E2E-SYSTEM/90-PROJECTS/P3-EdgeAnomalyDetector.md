---
loai: project
ma: P3
trang_thai: chua-bat-dau
gio_du_kien: "*realistic* — tháng 14–22 — ~180 h"
---
# P3 · EDGE ANOMALY DETECTOR

***realistic* — tháng 14–22 — ~180 h**

> *Đặc tả dưới đây trích nguyên văn roadmap §10. Đừng sửa đặc tả — ghi thay đổi vào mục ✎ ở cuối.*

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

