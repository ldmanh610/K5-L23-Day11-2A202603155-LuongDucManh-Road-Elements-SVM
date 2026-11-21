# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): nguyenbinhanh   Người kiểm (học viên): luongducmanh  
Ngày: 21/11/2026                         Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): nguyenbinhanh-front.zip, nguyenbinhanh-fisheye.zip (không kèm manifest)  
Số ảnh kiểm: 6 (A02, A06, A11, B02, B05, B06; ảnh không lỗi: B05) (+ 0 ảnh thêm)  
Số nhãn đã kiểm (shape + tag): 75 (51 shape + 24 tag)  

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 14 | 1 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 14 | 2 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 14 | 4 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 14 | 2 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 9 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 11 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 15 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 4 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 21 | 3 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-03 | B06 | lane#3@(935,509) | nặng | Camera hai bên (fisheye_left) bắt buộc đặt `position=other`, đang để `L1`. |
| 2 | QC1-04 | A06 | lane#1@(1130,548) | chính | Điểm đầu cao hơn điểm cuối (vẽ ngược từ xa về gần). |
| 3 | QC1-04 | A06 | lane#12@(541,389) | chính | Điểm đầu cao hơn điểm cuối (vẽ ngược từ xa về gần). |
| 4 | QC1-05 | A02 | lane#3@(2,501), lane#5@(511,567) | chính | Hai polyline cùng mang `position=L1` (trùng vị trí hoặc tách vạch). |
| 5 | QC1-05 | A02 | lane#1@(931,572), lane#2@(1152,720) | chính | Hai polyline cùng mang `position=R1` (tách vạch hoặc nhầm `R2` thành `R1`). |
| 6 | QC1-05 | A06 | lane#9@(441,415), lane#10@(452,416) | chính | Tách vạch đôi L1 thành 2 polyline riêng cùng mang `position=L1`. |
| 7 | QC1-05 | A11 | lane#0@(138,713), lane#1@(77,716) | chính | Tách vạch vàng đôi `L1` (`kind=double`) thành 2 polyline riêng thay vì 1 đường trên tâm. |
| 8 | QC1-06 | A06 | lane#9@(441,415), lane#10@(452,416) | chính | Vạch tim đường đôi là màu vàng (`yellow`), đang gán `color=white`. |
| 9 | QC1-06 | A06 | lane#12@(541,389) | chính | Vạch bên phải là vạch đứt (`dashed`), đang gán `style=solid`. |
| 10 | QC1-11 | B02 | road_curb#7@(1260,559) | chính | Chỉ đặt 3 điểm trên ảnh fisheye; cần thêm điểm uốn theo cung cong. |
| 11 | QC1-11 | B02 | traffic_light#3@(46,362) | chính | Tâm box nằm ngoài 80 % bán kính vòng ảnh nhưng chưa bật `edge_zone`. |
| 12 | QC1-11 | B02 | traffic_sign#5@(92,319) | chính | Tâm box nằm ngoài 80 % bán kính vòng ảnh nhưng chưa bật `edge_zone`. |

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| — | — | — |

## Quyết định

Lỗi nặng: 1   Lỗi chính: 11 / 75 nhãn = 14.67 %   Lỗi nhẹ: 0   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): Rework  
Lý do (theo luật của phiếu): Có 1 lỗi nặng (QC1-03 ở B06 đặt sai `position=L1` trên camera hai bên) và tỉ lệ lỗi chính 14.67 % > ngưỡng 5 %.
