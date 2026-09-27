---
loai: meta
ma: M05
---
# 05 · Technology layer — 6 tầng theo tuổi thọ

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

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
---

## ✎ Phần của tôi — theo dõi

**Kiểm tra hằng quý:** công cụ nào tôi đang bỏ giờ vào mà thuộc tầng 4–5?

| Công nghệ | Tầng | Giờ đã bỏ | Còn đáng không |
|---|---|---|---|
|  |  |  |  |

