---
loai: meta
ma: M03
---
# 03 · Depth map — mức mục tiêu từng nhánh

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

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
---

## ✎ Phần của tôi — theo dõi

| Nhánh | Mức thật hiện tại | Ngày đánh giá | Chênh so với mục tiêu |
|---|---|---|---|
|  |  |  |  |

