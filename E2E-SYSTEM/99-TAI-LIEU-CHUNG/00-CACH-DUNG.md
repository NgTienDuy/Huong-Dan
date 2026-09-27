---
loai: meta
ma: M00
---
# 00 · Cách dùng bộ tài liệu này

## Nguyên tắc

1. **Không xoá đầu mục.** Ô trống là dữ liệu: nó nói bạn chưa học phần đó. Xoá đi là mất bản đồ độ phủ.
2. **Không chép định nghĩa.** Mỗi ô yêu cầu viết lại bằng chữ của bạn. Chép vào thì file dài ra mà đầu không đổi.
3. **Mỗi khẳng định về hiệu năng phải có số bạn tự đo.** Ô *"số liệu / lệnh / API cụ thể"* tồn tại vì lý do đó.
4. **Sổ lỗi quan trọng hơn phần lý thuyết.** Sau một năm, mục 4 của mỗi file là thứ bạn đọc lại nhiều nhất.
5. **Checkpoint là nhị phân.** Đạt hoặc không. Không có "gần đạt". Chưa có bằng chứng thì chưa đạt.

## Vòng lặp mỗi buổi học (≈90 phút)

| Bước | Thời gian | Làm gì |
|---|---|---|
| 1 | 5' | Mở file leaf, đọc lại mục 0 và mục 6 (câu hỏi mở) |
| 2 | 45' | Học **một** sub-leaf. Không nhảy. |
| 3 | 25' | Làm thật: code / đo / đấu nối. Ghi vào ô *bằng chứng* |
| 4 | 10' | Điền 4 ô của sub-leaf đó, tick trạng thái |
| 5 | 5' | Ghi nhật ký mục 9 + cập nhật `sub_leaf_da_dien` ở front-matter |

Nếu bước 3 không làm được → ghi vào mục 6 (câu hỏi mở) và **đừng** tick "đã hiểu".

## Vòng lặp mỗi tuần

- ≥2 dòng mới vào `12-SO-DICH-OT-IT.md` (bắt buộc — đây là năng lực liên ngành ở dạng cụ thể nhất).
- Cập nhật `99-NHAT-KY/` : giờ thực tế vs kế hoạch, tuần tốt hay tuần xấu.
- Xem lại các leaf đang ở trạng thái ◐ quá 3 tuần — hoặc đẩy lên ●, hoặc hạ xuống ☐ và thừa nhận đã bỏ.

## Vòng lặp mỗi quý

- Chạy `10-COVERAGE-AUDIT.md`.
- Đọc lại `11-STATE-BLOCK.md` và cập nhật ước lượng.
- Kiểm tra `06-PHASES.md`: phase hiện tại còn đúng không.

## Ghi bằng gì

Bất kỳ editor markdown nào. Gợi ý: Obsidian hoặc VS Code — cả hai đều đọc được front-matter YAML,
liên kết markdown tương đối giữa các file, và tìm kiếm toàn văn. Nếu dùng Obsidian, mở `E2E-SYSTEM` làm vault gốc.

## Cách đo tiến độ nhanh

```powershell
# Số leaf đã đạt trạng thái 'da-hieu' trở lên
Select-String -Path .\*\*.md -Pattern '^trang_thai: (da-hieu|da-dung-that|day-lai-duoc)' | Measure-Object

# Tổng giờ đã ghi
Select-String -Path .\*\*.md -Pattern '^gio_da_hoc: (\\d+)' | ForEach-Object { [int]$_.Matches.Groups[1].Value } | Measure-Object -Sum
```
