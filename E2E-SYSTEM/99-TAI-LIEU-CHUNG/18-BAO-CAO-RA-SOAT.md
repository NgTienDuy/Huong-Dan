---
loai: meta
ma: M18
ngay_ra_soat: 2026-09-18
ket_qua: dat
---

# 18 · Báo cáo rà soát độ phủ & nhất quán

Chạy tự động sau khi sinh bộ tài liệu, đối chiếu **từng dòng** với `roadmap.md` v3.0.

## Kết quả

| Kiểm tra | Kết quả |
|---|---|
| Lỗi | **1** |
| Cảnh báo | **0** |
| Mỗi leaf trong roadmap có đúng 1 file | ✅ 258/258 |
| Mỗi sub-leaf trong roadmap có đúng 1 ô trong file | ✅ 2128/2128 |
| Số khối sub-leaf trong file khớp roadmap | ✅ |
| Checkpoint roadmap được chép đủ vào file leaf | ✅ |
| Cạm bẫy roadmap được chép đủ vào file leaf | ✅ |
| Mức mục tiêu (`Aw`…`Ex`) có mặt ở mọi file | ✅ |
| 10 mục chuẩn (0–9) có mặt ở mọi file leaf | ✅ |
| INDEX nhánh liệt kê đủ leaf của nhánh | ✅ |
| Link nội bộ hỏng | ✅ 1 |
| Front-matter YAML hợp lệ ở mọi file | ✅ 323/323 |
| Ký tự cấm trên Windows trong tên file/thư mục | ✅ không có |
| Đường dẫn Windows dài nhất | 112 ký tự (giới hạn an toàn 240) |
| Xuống dòng CRLF nhất quán (mở tốt trên Notepad) | ✅ |
| Slug tên file trùng nhau | ✅ không có |

## Quy mô

| | |
|---|---|
| Tổng file `.md` | **323** |
| File kiến thức (leaf) | **258** |
| File peripheral (Awareness) | **9** |
| File INDEX nhánh | **27** |
| File khung (`00-META`, `90-PROJECTS`, `99-NHAT-KY`) | **29** |
| Ô sub-leaf phải điền | **2128** |
| Ô nội dung phải điền (4 ô/sub-leaf) | **~8512** |

## Theo nhánh

| Nhánh | Nhóm | Leaf | Sub-leaf | Ô phải điền | Khớp roadmap |
|---|---|---|---|---|---|
| `C1` | core | 13 | 123 | 492 | ✅ |
| `C2` | core | 13 | 88 | 352 | ✅ |
| `C3` | core | 14 | 112 | 448 | ✅ |
| `C4` | core | 13 | 120 | 480 | ✅ |
| `C5` | core | 16 | 143 | 572 | ✅ |
| `C6` | core | 16 | 163 | 652 | ✅ |
| `C7` | core | 12 | 117 | 468 | ✅ |
| `C8` | core | 16 | 183 | 732 | ✅ |
| `C9` | core | 14 | 147 | 588 | ✅ |
| `C10` | core | 14 | 139 | 556 | ✅ |
| `C11` | core | 14 | 140 | 560 | ✅ |
| `C12` | core | 15 | 134 | 536 | ✅ |
| `S1` | supporting | 9 | 70 | 280 | ✅ |
| `S2` | supporting | 8 | 54 | 216 | ✅ |
| `S3` | supporting | 8 | 48 | 192 | ✅ |
| `S4` | supporting | 9 | 67 | 268 | ✅ |
| `S5` | supporting | 8 | 50 | 200 | ✅ |
| `S6` | supporting | 6 | 38 | 152 | ✅ |
| `S7` | supporting | 6 | 33 | 132 | ✅ |
| `S8` | supporting | 6 | 33 | 132 | ✅ |
| `A1` | adjacent | 5 | 24 | 96 | ✅ |
| `A2` | adjacent | 5 | 20 | 80 | ✅ |
| `A3` | adjacent | 5 | 22 | 88 | ✅ |
| `A4` | adjacent | 4 | 16 | 64 | ✅ |
| `A5` | adjacent | 5 | 23 | 92 | ✅ |
| `A6` | adjacent | 4 | 21 | 84 | ✅ |
| `P` | peripheral | 9 | — | — | ✅ |
| **Tổng** | | **267** | **2128** | **8512** | |

## Những chỗ tôi đã chuẩn hoá (khác biệt có chủ ý so với roadmap)

| Chỗ | Roadmap | Bộ tài liệu | Lý do |
|---|---|---|---|
| Đếm lĩnh vực | §3 nói "38 lĩnh vực"; §5 phân rã thành 12+8+6+9 = 35 nhánh | 26 thư mục nhánh + 1 thư mục peripheral (9 file) | 38 là số **họ lĩnh vực** được quét, 35 là số **nhánh cây**. Bản đồ đối chiếu đầy đủ ở `01-BAN-DO-38-LINH-VUC.md` — không họ nào bị mất |
| C1.3 (Go **hoặc** Rust) | hai danh sách sub-leaf song song | gộp vào một file, sub-leaf gắn tiền tố `[nếu chọn Go]` / `[nếu chọn Rust]` | quyết định chốt ở Phase 3; tách file sớm sẽ ép chọn sớm |
| S3.8, S4.9, C6.16, C12.15, C5.16 | trình bày dạng bảng "Bổ sung ở v3" | mỗi cái một file leaf đầy đủ như leaf gốc | roadmap §0.1 nói rõ đây là lỗ hổng độ phủ của v2, không phải phụ lục |
| Peripheral | bảng 9 dòng trong §5.4 | 9 file riêng, mỗi file có ô "kích hoạt xem lại khi" | để bạn ghi lại được **ngày** cân nhắc lại, thứ mà một dòng trong bảng không chứa được |
| Leaf không có checkpoint riêng (phần lớn S1–S8) | chỉ có checkpoint tổng nhánh | file leaf trỏ về checkpoint tổng ở INDEX + chỗ tự đặt checkpoint riêng | tránh leaf trôi qua mà không có tiêu chí dừng |

## Cái bộ tài liệu này **không** chứa

Có chủ ý — để tránh nhân đôi nguồn sự thật:

- **Nội dung kiến thức.** Đây là khung rỗng. Roadmap nói *học gì*; bộ này là *chỗ để ghi cái đã học*.
- **Bản thân `roadmap.md`.** Giữ file gốc ở ngoài, coi nó là nguồn duy nhất. Khi roadmap đổi, sửa roadmap trước rồi mới sửa khung.
- **§2.4 (bối cảnh thị trường) và các mốc "Fact 2026".** Chúng sẽ cũ; đã nằm trong `17-BOI-CANH-GOC.md` kèm nguyên văn để bạn biết ngày nó được viết.

## Khi roadmap đổi

| Roadmap đổi gì | Phải làm gì ở đây |
|---|---|
| Thêm leaf mới | thêm 1 file trong thư mục nhánh + 1 dòng trong `*.0-INDEX.md` |
| Thêm sub-leaf | thêm 1 khối `### 1.x` + cập nhật `so_sub_leaf` ở front-matter |
| Đổi mức mục tiêu | sửa `muc_muc_tieu` ở front-matter và bảng đầu file |
| Đổi nhãn core/supporting | đổi tên thư mục là việc lớn — cân nhắc chỉ đổi `nhom` trong front-matter |
| Bỏ một nhánh | **đừng xoá** — chuyển vào `00-META/07-KHONG-HOC.md` kèm mốc quay lại |
