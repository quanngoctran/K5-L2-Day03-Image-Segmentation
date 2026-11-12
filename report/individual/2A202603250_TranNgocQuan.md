# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603250
- Ngày / CVAT local: 12-11-2026 / CVAT local
- Công cụ đã dùng: brush/polygon

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

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

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000181542.jpg`, vị trí: người phụ nữ lớn tuổi mặc áo dài trắng đang băng qua vạch kẻ đường.
- Class và quy tắc tôi dùng để chọn biên: Class `person`. Tuân thủ nguyên tắc chỉ gán nhãn phần nhìn thấy (visible-only): đi nét biên ôm sát theo dáng người, phần tóc, toàn bộ hai tà áo dài trắng, quần, dép và phần quai túi xách đeo bên vai phải.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng.
- Nếu không dùng gợi ý: Tôi giữ nguyên cả phần tà áo dài đang bay rộng và dây đeo túi xách trong cùng một mask `person` thay vì cắt bớt theo phom dáng cơ thể, đồng thời xếp lớp (layer) của đối tượng này nằm trên chiếc xe máy ngay phía sau để phản ánh đúng thứ tự che khuất ngoài thực tế.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance` / `000000181542.jpg` / khu vực vỉa hè phía sau chiếc xe bán tải và góc dưới bên trái ảnh.
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: thiếu-thừa vật.
- Bằng chứng tôi nhìn thấy: Ở lượt vẽ đầu tiên, tôi đã bỏ sót một nhóm người đang đứng trên vỉa hè ở xa (đoạn sau xe bán tải, phía trước biển hiệu Chanel) cùng với phần bánh trước của một chiếc xe máy bị cắt ở mép dưới góc trái bức ảnh.
- Quy tắc và hành động sửa: Áp dụng quy tắc rà soát và gán nhãn không bỏ sót mọi đối tượng thuộc các class yêu cầu miễn là còn phần diện tích hiển thị trong khung hình.
- Sau sửa đã Save và export lại chưa? Đã sửa, bấm Save và export lại file ZIP mới.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): chưa có điểm.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `000000460147.jpg` — Khu vực giữa ảnh: Xe tải chuyên dụng đang chở nhiều ô tô trên 2 tầng sàn xe. | (1) Gộp toàn bộ thân xe tải và các xe con bên trên thành một mask `truck` duy nhất.<br>(2) Tách phần đầu kéo và khung sàn xe là `truck`, còn mỗi chiếc ô tô con nằm trên 2 tầng chở hàng được gán thành từng instance `car` riêng biệt. | Quan sát bằng mắt thường thấy rõ 3 chiếc xe con tách rời nhau nằm trên 2 tầng thùng xe. | Hỏi coach: Đối với loại xe tải chở ô tô, các xe nằm trên thùng luôn phải tách thành từng object `car` riêng hay được gộp chung vào `truck`? |
| `000000460147.jpg` — Khu vực bên trái: Cột biển hiệu ENEOS, tấm bảng quảng cáo lớn màu vàng và dãy nhà phía sau. | (1) Gộp chung cả trụ biển hiệu, khung bảng quảng cáo lớn và dãy nhà phía sau vào cùng class `building`.<br>(2) Bỏ qua (để trống) các trụ/bảng quảng cáo dựng độc lập, chỉ tô class `building` cho phần kiến trúc tường và mái nhà ở phía sau. | Qua quan sát thực tế, các biển quảng cáo này được dựng trên hệ cột thép độc lập, tách biệt với kết cấu nhà dân phía sau. | Hỏi coach: Những trụ hoặc bảng quảng cáo kích thước lớn đặt ven đường (như trụ ENEOS và biển màu vàng bên trái) có được tính vào lớp `building` không hay xếp vào phần nền bỏ qua? |
| `000000460147.jpg` — Khu vực phía dưới trung tâm: Phần mặt đường nhựa có vạch sơn trắng nằm giữa đuôi xe tải chở ô tô và dải cây phân cách. | (1) Gán vào lớp `road` do đây vẫn là phần mặt đường trải nhựa liên thông, chỉ được phân tách với làn xe bên trái bằng vạch kẻ sơn.<br>(2) Để trống (không gán nhãn `road`) vì khu vực này đóng vai trò như vùng lề đệm/đảo mềm ngăn cách làn xe chạy với dải phân cách cứng. | Bề mặt tại vị trí này là nhựa đường đồng chất với lòng đường và có kẻ vạch sơn chỉ dẫn giao thông. | Hỏi coach: Phần mặt đường có vạch sơn đệm nằm sát dải phân cách cứng ở giữa đường có được tính là `road` hay bỏ trống? |
