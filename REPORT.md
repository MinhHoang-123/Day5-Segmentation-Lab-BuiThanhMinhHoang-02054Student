# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 02054
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Polygon, Brush, Gợi ý tự động (AI tools)

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh 1, chiếc xe ô tô nằm ở góc phải bên dưới.
- Class và quy tắc tôi dùng để chọn biên: Class `car`. Tôi dùng Polygon bám sát viền xe, không bao gồm bóng đổ dưới gầm xe vì bóng đổ không thuộc phần cứng của ô tô.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: Gợi ý AI thỉnh thoảng bị lan ra phần bóng đổ (shadow); tôi đã giữ lại mask nhưng dùng Brush (giữ Alt) để xóa phần bị tràn.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `cp2_slice`, chiếc xe nằm ngang bị cột đèn che ngang giữa thân.
- Lỗi thuộc loại: gộp-tách
- Bằng chứng tôi nhìn thấy: Tôi lỡ vẽ thành 2 object (2 instance khác nhau) ở 2 bên cột đèn.
- Quy tắc và hành động sửa: Quy tắc là một vật thể dù bị che khuất một phần vẫn phải là 1 object. Tôi đã gộp 2 object đó lại thành 1 (cùng ID).
- Sau sửa đã Save và export lại chưa? Đã Save và export đè lên `cp2_slice.zip`.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): Điểm số cho `cp2_slice` đã tăng sau khi gộp thành công 2 nửa của chiếc xe. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `easy_semantic`, Ảnh 1, vỉa hè góc trái | Bó vỉa đường: `road` hay `sidewalk`? | Bó vỉa nhô lên khỏi đường và cùng chất liệu với phần đi bộ. | Tôi chọn gán vào `sidewalk` thay vì `road`. |
| `hard_panoptic`, Ảnh 2, người đi bộ xa | Đốm mờ là `person` hay `background`? | Có hình dáng thẳng đứng, ở vị trí lối đi bộ nhưng rất nhỏ. | Tôi quyết định vẽ mask class `person` dù hơi mờ. |
| `cp5_occlusion`, Xe đạp bị xe tải che | Phần nhô ra là xe đạp hay không? | Khung kim loại lộ ra có hình dạng đuôi xe đạp. | Tôi thêm mask xe đạp đè bên dưới xe tải. |
