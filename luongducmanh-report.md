# Báo cáo cá nhân — Ngày 11

Họ tên: Lương Đức Mạnh               Mã học viên: 2A202603155  
Phiên bản CVAT (Help → About): CVAT v2.82.0  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 21/11/2026 10:43 (bản đầu) / 12:10 (cập nhật A06, UTC+7)    Số lần nộp lại sau Rework: 0  

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | Nạp từ `configs/road_v1_labels.json` (`lane`, `road_curb`, `crosswalk`, `drivable`, `traffic_light`, `traffic_sign`) |
| Thuộc tính và giá trị | Đúng | Khớp 100% với output của `python -m road_lab.taxonomy` |
| 4 tag ảnh | Đúng | Đủ 4 tag `camera`, `timeofday`, `weather`, `source` với thuộc tính `value` |

Cách kết thúc polyline trên bản CVAT này: Bấm phím `N` sau khi chấm điểm cuối cùng.  
Cách đặt tag ảnh trên CVAT này: Chọn công cụ Tag ở thanh bên trái, thêm đủ 4 tag rồi mở `Details` ở bảng Objects để chọn đúng `value`.  

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 28 | 1 | 4 | 17 | 21 | 15 |
| front-extra | 4 | 10 | 0 | 2 | 6 | 5 | 6 |
| fisheye | 8 | 7 | 1 | 8 | 2 | 4 | 4 |
| fisheye-extra | 4 | 0 | 0 | 4 | 0 | 0 | 0 |
| **Tổng** | **28** | **45** | **2** | **18** | **25** | **30** | **25** |

## 3. Kết quả `road_check lint` & Ca khó

- `road_check selftest`: Đạt (`SELFTEST PASS`, `78.0/78`).
- `road_check lint`: **28 ảnh** (`16 front + 12 fisheye`), `contains_images: false`, `images_unlabelled: 0`, `images_all_tags: 28/28`, còn **5 cảnh báo `QC1-02`**:
  - **`A05` (2 cảnh báo `L1`, `R1`)**: Mặt đường thực tế không có vạch sơn phân làn → đề xuất coach miễn lỗi `QC1-02`.
  - **`A06` (1 cảnh báo `R1`)**: Đã vẽ `L1` sau ngã tư; bên phải là giao lộ và hàng cột sắt không có vạch sơn `R1` rõ ràng.
  - **`A08` (`L1`) & `A12` (`R1`)**: Còn thiếu `position` chuẩn (đã vẽ `lane` nhưng bị chọn nhầm `L2`), sẵn sàng cập nhật lại nếu có vòng Rework.
  - **`A04`, `A10`**: Điều kiện ánh sáng khó/nhiều biển và đèn ở xa; đã rà soát `edge_zone` và `facing`.
  - **`B05–B08`, `B10`, `B12` (`MVL/MVR`)**: Toàn bộ `lane` đều gán đúng `position = other`.
  - **`B11` (`0 shape`)**: Các vạch kẻ ô đỗ xe trong bãi không gán `lane` để tránh lỗi `QC1-03`.

## 4. Phiếu QC 1 trao đổi với bạn cùng lớp

- **Phiếu đã chấm cho bạn cùng lớp**: Đã kiểm 6 ảnh (`A02, A06, A11, B02, B05, B06` — 75 nhãn = 51 shape + 24 tag) trong file `luongducmanh-qc1-for-nguyenbinhanh.md` (1 lỗi nặng `QC1-03`, 11 lỗi chính → Quyết định: `Rework`).
- **Phiếu QC 1 nhận được từ `nguyenbinhanh`**: `[Điền kết quả sau khi nhận phiếu từ Bình Anh, hoặc ghi: Đang chờ phiếu QC 1 từ nguyenbinhanh]`

## 5. Tự đánh giá

- Điểm mạnh: Cấu trúc project, 4 tag ảnh trên 28/28 ảnh và quy cách đóng gói `CVAT for images 1.1` (không kèm ảnh) đạt chuẩn; các ảnh `MVL/MVR` gán đúng `position=other` và đèn `side/back` đặt đúng `color=unknown`.
- Điểm cần cải thiện: Chỉnh lại `position` của `lane` ở `A08` (`L1`), `A12` (`R1` + `drivable`), và bổ sung thêm `lane/drivable` chi tiết hơn ở một số ảnh `fisheye` (`B01, B02, B09, B10, B12`).

## 6. Ảnh minh họa (4 ảnh bắt buộc)

1. Tab `Labels` của project `d11-road-luongducmanh`: *(chèn/đính kèm ảnh 1)*
2. 1 ảnh `front` đã gán đầy đủ nhãn: *(chèn/đính kèm ảnh 2)*
3. 1 ảnh `fisheye` phóng to thấy rõ polyline uốn cong nhiều đỉnh: *(chèn/đính kèm ảnh 3)*
4. Đoạn XML `<polyline label="lane">` trích từ file zip đã export: *(chèn/đính kèm ảnh 4)*
