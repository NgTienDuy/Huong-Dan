---
loai: meta
ma: M02
---
# 02 · Dependency graph

> *Trích nguyên văn từ `roadmap.md` v3.0 — phần dưới cùng là ô của bạn.*

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
          Operating Systems & Concurrency               │
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
---

## ✎ Phần của tôi — theo dõi

**Của tôi:** vẽ lại graph này sau mỗi phase và đánh dấu nhánh đã đạt mức yêu cầu.

| Ngày | Nhánh đã đủ mức | Nhánh đang chặn tôi | Quyết định |
|---|---|---|---|
|  |  |  |  |

