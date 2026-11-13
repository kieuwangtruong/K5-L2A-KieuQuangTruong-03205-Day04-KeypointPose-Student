# Báo cáo cá nhân — KIEUQUANGTRUONG

> Hai file task mới đã được kiểm tra lại. Thời lượng bên dưới là **ước tính bám theo lịch mẫu trong README/CHECKPOINTS.md**, không phải số đo từ nhật ký thao tác. Những chi tiết cá nhân không thể xác minh từ file vẫn được đánh dấu để bổ sung.

Dữ liệu: 12 ảnh người COCO và 8 ảnh khuôn mặt. MSSV, tên và danh sách ảnh được đọc từ `src/exports/assignment.json`.

## 0. Thông tin học viên

- Họ tên: KIEUQUANGTRUONG
- MSSV: 2A202603205
- Email: [bổ sung]
- Link repository: [bổ sung]
- Phiên bản CVAT (Help → About): [bổ sung]
- Máy: hệ điều hành [bổ sung] · RAM [bổ sung] GB · CVAT chế độ [đầy đủ / lite]
- Bộ ảnh (`src/exports/assignment.json`): có
- Giờ bắt đầu: [bổ sung]
- Giờ kết thúc: [bổ sung]

## 1. Kiểm tra label (CP0)

Thông tin dưới đây được xác minh từ danh mục keypoints/skeleton trong file COCO của hai task; chưa xác minh trực tiếp label constructor trên CVAT.

| Label | Kiểu | Số điểm | Tên điểm đúng schema trong file? | Đúng thứ tự schema? | Số cạnh |
|---|---|---:|---|---|---:|
| `person` | Skeleton | 17 | Có | Có | 19 |
| `face` | Skeleton | 13 | Có | Có | 13 |

- Mẫu `person` dựng theo người quay mặt về camera: [xác nhận trên CVAT]
- Cách đổi cờ `occluded` / `outside` cho một điểm trên phiên bản CVAT đã dùng: [bổ sung]

## 2. Số lượng đã gán và thời gian (CP1, CP2)

Số skeleton dưới đây được đếm trong hai file task hiện có. Đây là số đối tượng đã xuất, không phải số người thấp hơn 60 px hoặc số người bị bỏ qua.

| Nhóm ảnh | Số ảnh | Số skeleton đã xuất | Số người dưới 60 px không gán | Số poster / gương / màn hình bỏ qua | Thời gian ước tính (phút) |
|---|---:|---:|---:|---:|---:|
| `easy` | 5 | 5 | [bổ sung] | [bổ sung] | 25 |
| `occluded` | 3 | 6 | [bổ sung] | [bổ sung] | 21 |
| `back` | 2 | 4 | [bổ sung] | [bổ sung] | 16 |
| `small` | 1 | 8 | [bổ sung] | [bổ sung] | 8 |
| `crowd` | 1 | 3 | [bổ sung] | [bổ sung] | 14 |
| `faces` | 8 | 8 | — | — | 30 |

- Thời lượng ước tính CP1: `easy` 25 + `occluded` 21 + `back` 16 + `small` 8 + `crowd` 14 = 84 phút thao tác; khoảng 6 phút còn lại dành cho lưu và kiểm tra để bám khung 90 phút của lịch mẫu.
- Thời lượng ước tính theo lịch mẫu: CP1 90 phút · CP2 30 phút · CP3 20 phút · CP4 10 phút.
- Mốc phút 105 trong README là mục tiêu hoàn thành ít nhất 8/10 ảnh; không có log để xác nhận thời điểm thực tế.
- Ảnh/ca tốn thời gian nhất theo ảnh minh họa hiện có: cảnh đông người bị che khuất, ảnh người nhỏ ở xa và mặt có mắt/môi khó thấy. Thời gian thực tế không được lưu lại.

## 3. Bảng ca khó (CP1, CP2)

ZIP người mới nhất đã sửa được lỗi `left_elbow` ở `000000179201.jpg`; lỗi này không còn bị checker báo. Các dòng dưới đây là những vấn đề còn lại trong bản mới.

| Ảnh | Người / mặt | Điểm | Cờ hiện tại | Phân vân / vấn đề | Hướng xử lý |
|---|---|---|---:|---|---|
| `000000189365.jpg` | người #1 | `right_hip` | 1 | Tọa độ xuất `-13, 373` nằm ngoài ảnh | Kiểm tra trên CVAT; nếu khớp ngoài ảnh, đặt `outside` |
| `000000189365.jpg` | người #2 | `left_eye`, `right_eye` | 1 | Cả hai điểm có y = -8, nằm ngoài ảnh | Kiểm tra trên CVAT; nếu khớp ngoài ảnh, đặt `outside` |
| `000000572411.jpg` | người #1–#6 | — | — | Sáu skeleton bị cảnh báo có độ cao dưới 60 px (0, 3, 20, 20, 34, 21 px) | Kiểm tra từng người; bỏ skeleton người dưới 60 px theo guideline |
| `face_146049.jpg` | mặt | — | — | Đã có đúng một skeleton mặt trong file mới | Đạt số lượng theo script; rà vị trí điểm bằng mắt |

### Ảnh minh họa ca khó

Bốn ảnh minh họa hiện có nằm ở thư mục gốc repo; chúng không thay thế bốn ảnh chụp màn hình bắt buộc ở mục 6.

![Người trong cảnh đông, bị che khuất](<../../bị sát nhau nhiều phần che khuất.png>)

![Người ở xa, khó phân biệt](<../../không phân biệt được người từ xa .png>)

![Người bị vật thể che khuất, chọn outside](<../../trường hợp bị vật thể che khuất cũng khá khó đoán nên quyết định v=0.png>)

![Mặt có môi mỏng và mắt híp](<../../trường hợp face có môi mỏng và mắt đang cười híp mắt cũng khó skeleton.png>)

## 4. Bảng tự review (CP3)

Chưa có bảng ghi chép CP3 trong các file được cung cấp. Cần tự kiểm tra 5 ảnh người (ít nhất 2 ảnh `back` hoặc `crowd`) và 3 ảnh mặt trên CVAT, rồi điền bảng. Không đánh dấu “đã sửa” cho đến khi sửa và lưu trên CVAT.

| Ảnh | Người / mặt | Điểm | Mã lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|---|
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |
| [bổ sung] | | | | | |

Tổng hợp số lỗi theo mã sau khi review:

| `lr_swap` | `vis_flag` | `position` | `missing` | `extra` | `ok` |
|---:|---:|---:|---:|---:|---:|
| [bổ sung] | [bổ sung] | [bổ sung] | [bổ sung] | [bổ sung] | [bổ sung] |

Điểm phân vân giữa `v = 1` và `v = 0`, ghi cả lựa chọn và lý do: [bổ sung]

## 5. Kiểm file xuất và kết quả tự kiểm (CP4)

Hai file task gốc của job 10 và job 11 đã được cập nhật. Kiểm tra cho thấy annotation có đúng độ dài mảng (51 số cho người, 39 số), đủ 12 ảnh người và 8 ảnh mặt. Tuy nhiên, file nộp trong `src/exports/` vẫn chưa được thay bằng hai bản cập nhật.

| File đã kiểm | Người / mặt kiểm | Số phần tử `keypoints` | Kết quả kiểm cờ và số điểm |
|---|---|---:|---|
| `job_10_annotations_2026_11_12_12_10_51_coco keypoints 1.0.zip` | 26 skeleton người trong 12 ảnh | 51 mỗi annotation | Có 3 điểm `v > 0` nằm ngoài ảnh; cần sửa trên CVAT |
| `job_11_annotations_2026_11_12_12_12_20_coco keypoints 1.0.zip` | 8 skeleton mặt trong 8 ảnh | 39 mỗi annotation | Mỗi ảnh có đúng một skeleton |

- CVAT xuất `occluded` thành `v = 1`; `outside` thành `v = 0`.
- Ghi chú của script: các điểm `v = 0` trong file hiện vẫn mang tọa độ cũ.
- Hai job đã chuyển sang `completed` trên CVAT: [cần kiểm tra trực tiếp trên CVAT]
- `src/exports/KIEUQUANGTRUONG_persons.zip` hiện có 12 ảnh nhưng **0 annotation**; cần xuất lại từ task sau khi sửa. Chưa thấy `src/exports/KIEUQUANGTRUONG_faces.zip`.

Kết quả `python src/check_submission.py --persons "job_10_annotations_2026_11_12_12_10_51_coco keypoints 1.0.zip" --faces "job_11_annotations_2026_11_12_12_12_20_coco keypoints 1.0.zip"`:

```text
- File person: job_10_annotations_2026_11_12_12_10_51_coco keypoints 1.0.zip
  Số ảnh: 12 · số skeleton `person`: 26 · mỗi annotation 51 số
  Skeleton theo ảnh: 000000027565=1, 000000043500=2, 000000103970=1, 000000179201=2, 000000189365=2, 000000194027=1, 000000205650=1, 000000294379=1, 000000381889=3, 000000391222=2, 000000516902=2, 000000572411=8
  Cờ v: v=2 267 (60%) · v=1 58 (13%) · v=0 117 (26%)
  num_keypoints trung bình: 12.5
- File face: job_11_annotations_2026_11_12_12_12_20_coco keypoints 1.0.zip
  Số ảnh: 8 · số skeleton `face`: 8 · mỗi annotation 39 số
  Skeleton theo ảnh: face_146049=1, face_178208=1, face_232598=1, face_356144=1, face_362568=1, face_425647=1, face_483667=1, face_53580=1
  Cờ v: v=2 94 (90%) · v=1 10 (10%) · v=0 0 (0%)
  num_keypoints trung bình: 13.0
- Ghi chú: 117 điểm v = 0 vẫn mang tọa độ cũ (CVAT 2.x xuất như vậy; chuẩn COCO ghi 0, 0). Không phải lỗi: điểm v = 0 bị bỏ qua khi huấn luyện và khi chấm.
- Số [LỖI]: 3 · số [CẢNH BÁO]: 6
Kết quả: CHƯA ĐẠT (3 lỗi). Sửa trên CVAT rồi xuất lại.
```

## 6. Ảnh chụp màn hình

Đã có đủ bốn file với tên yêu cầu trong `report/individual/images/`. Ảnh 3 là ảnh mặt phóng to; ảnh 4 thể hiện `keypoints` và `num_keypoints`. Ảnh 1 hiện là ảnh skeleton đã gán, chưa phải màn hình label constructor thấy đủ tên 17 điểm; ảnh 2 cần xác nhận rõ người quay lưng và cờ đã đặt. Nếu hai ảnh này không thể hiện đủ nội dung, chụp lại tương ứng trước khi nộp.

1. Label `person` trong label constructor:

   ![Label person](images/1_label_person.png)

2. Một người quay lưng đã gán, thấy cờ đã đặt:

   ![Người quay lưng](images/2_nguoi_quay_lung.png)

3. Khuôn mặt đã gán 13 điểm, phóng to vùng mắt:

   ![Khuôn mặt phóng to](images/3_mat_phong_to.png)

4. Một đoạn JSON export của một người:

   ![JSON export](images/4_json_export.png)

Nguồn ảnh: COCO val2017 / Wikimedia Commons.

## 7. Tự đánh giá

1. Qua đối chiếu file hiện tại, lỗi cần chú ý nhất là điểm có `v > 0` nhưng tọa độ nằm ngoài ảnh. Trước khi lưu cần rà lại tọa độ và cờ của từng điểm; nếu khớp không quan sát được hoặc nằm ngoài ảnh thì đặt `outside`, không để tọa độ ngoài biên thành điểm nhìn thấy.
2. Quy tắc đề xuất thêm: trước khi export, bật overlay skeleton và kiểm tra riêng các điểm sát biên ảnh; với ảnh nhóm `small`, xác nhận từng người đạt ngưỡng chiều cao tối thiểu 60 px để tránh gán nhầm người quá nhỏ.
3. Ví dụ cần sửa: `right_hip` của người #1 trong `000000189365.jpg` có `v = 1` nhưng tọa độ x = -13 nằm ngoài ảnh. Nếu giữ như vậy, mô hình học tọa độ khớp sai như một nhãn dương; đặt `outside` sẽ loại điểm đó khỏi loss. Điểm này vẫn cần sửa trên CVAT.

## 8. Khó khăn và lỗi kỹ thuật

Các vấn đề đang được script tự kiểm phát hiện: 3 điểm người nằm ngoài biên ảnh nhưng có `v > 0`; 6 skeleton trong ảnh `000000572411.jpg` có độ cao dưới 60 px. Task mặt hiện đủ 8 skeleton. Cần kiểm tra các cảnh báo trên CVAT, sửa các điểm ngoài ảnh, xuất lại, rồi chạy kiểm tra lần cuối. Khó khăn/lỗi kỹ thuật khác: [bổ sung]

## Bonus

Không thấy file export bonus trong dữ liệu hiện có; không thực hiện.

## 9. Tài liệu tham khảo và công cụ AI đã dùng

- Tài liệu lab: `docs/GUIDELINE.md`, `docs/COCO_KEYPOINTS.md`, `docs/CVAT_CHEATSHEET.md`.
- Công cụ kiểm tra: `src/check_submission.py`.
- Công cụ AI đã dùng: Copilot hỗ trợ rà soát file và soạn báo cáo; `src/check_submission.py` dùng để tự kiểm file COCO.
