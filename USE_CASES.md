📑 Use Case Description – Hệ thống Hub media bán lẻ đa kênh cho điện máy

Use Case 1: Quản lý nội dung số

Use Case ID: UC-01  
Actor: Admin, Content Editor  
Trigger: Actor chọn chức năng “Quản lý nội dung”.

Description:  
Cho phép người dùng tạo, chỉnh sửa, duyệt và phân loại nội dung số (bài viết, hình ảnh, video, clip ngắn) để phục vụ truyền thông đa kênh cho doanh nghiệp điện máy.

Preconditions:  
1. Actor đã đăng nhập hệ thống.  
2. Hệ thống hoạt động ổn định.

Postconditions:  
1. Nội dung được lưu và sẵn sàng xuất bản.
2. Nếu lỗi, hệ thống thông báo và không lưu thay đổi.       

Basic Flow:
1. Actor chọn “Tạo/Sửa nội dung”.
2. Nhập thông tin nội dung (tiêu đề, mô tả, media).
3. Hệ thống lưu nội dung vào CSDL.

Alternative Flow:
UC-01.AC.1: Actor gắn thẻ nội dung theo danh mục sản phẩm (TV, máy lạnh, tủ lạnh, v.v.) để hỗ trợ phân loại và tìm kiếm.   

Exception Flow:
UC-01.EX.1: Thiếu thông tin bắt buộc → hệ thống hiển thị cảnh báo.
UC-01.EX.2: Lỗi kết nối DB → lưu thất bại.

Use Case 2: Xuất bản đa kênh

Use Case ID: UC-02
Actor: Admin, Content Editor
Trigger: Actor chọn “Xuất bản nội dung”.

Description:
Cho phép người dùng xuất bản nội dung lên các nền tảng như Website, Facebook Page, Zalo OA, TikTok, YouTube.

Preconditions:
Nội dung đã được duyệt và hợp lệ.

Postconditions:
Nội dung hiển thị trên các kênh đã chọn.

Basic Flow:
1. Actor chọn kênh xuất bản.
2. Hệ thống gửi nội dung qua API tương ứng.
3. Ghi nhận trạng thái xuất bản.

Exception Flow:
UC-02.EX.1: Lỗi xác thực API → hệ thống thông báo lỗi.      
UC-02.EX.2: Kênh không phản hồi → đánh dấu thất bại.        

Use Case 3: Lên lịch nội dung 90 ngày

Use Case ID: UC-03
Actor: Admin, Marketing Planner
Trigger: Actor chọn “Lịch nội dung”.

Description:
Cho phép người dùng lên lịch đăng bài trong vòng 90 ngày cho
từng kênh truyền thông.

Preconditions:
Người dùng đã tạo nội dung.

Postconditions:
Lịch đăng bài được lưu và hiển thị trên dashboard.

Basic Flow:
1. Actor chọn ngày và kênh đăng bài.
2. Gắn nội dung tương ứng vào lịch.
3. Hệ thống lưu lịch và hiển thị trạng thái.

Exception Flow:
UC-03.EX.1: Trùng lịch đăng → hệ thống cảnh báo.
UC-03.EX.2: Không có nội dung tương ứng → yêu cầu tạo mới.  

Use Case 4: Tạo poster/thumbnail

Use Case ID: UC-04
Actor: Content Editor
Trigger: Actor chọn “Tạo poster”.

Description:
Cho phép người dùng tạo hình ảnh truyền thông (poster, thumbnail) từ nội dung có sẵn để phục vụ xuất bản.

Preconditions:
Nội dung đã được nhập đầy đủ.

Postconditions:
Poster được tạo và lưu vào hệ thống.

Basic Flow:
1. Actor chọn mẫu poster.
2. Nhập tiêu đề, hình ảnh, màu sắc.
3. Hệ thống render và lưu ảnh.

Exception Flow:
UC-04.EX.1: Lỗi render ảnh → hệ thống hiển thị lỗi.
UC-04.EX.2: Thiếu hình ảnh đầu vào → yêu cầu bổ sung.       

Use Case 5: Thông báo đẩy

Use Case ID: UC-05
Actor: Hệ thống
Trigger: Có nội dung mới hoặc lịch đăng đến hạn.

Description:
Hệ thống gửi thông báo đẩy đến người dùng để nhắc nhở hoặc cập nhật trạng thái nội dung.

Preconditions:
Người dùng đã bật thông báo.

Postconditions:
Thông báo được gửi và ghi nhận.

Basic Flow:
1. Hệ thống kiểm tra lịch đăng.
2. Gửi thông báo đến người dùng.
3. Ghi log thông báo.

Exception Flow:
UC-05.EX.1: Trình duyệt không hỗ trợ → hiển thị cảnh báo.   
UC-05.EX.2: Người dùng từ chối nhận thông báo → ghi nhận trạng thái.

Use Case 6: Tối ưu SEO & phân tích hiệu quả

Use Case ID: UC-06
Actor: Admin, Marketing Analyst
Trigger: Actor chọn “Phân tích & SEO”.

Description:
Hệ thống tạo sitemap, thẻ OG, Schema và hiển thị báo cáo hiệu quả truyền thông theo từng kênh.

Preconditions:
Nội dung đã được xuất bản.

Postconditions:
SEO được cập nhật, báo cáo hiển thị.

Basic Flow:
1. Actor chọn nội dung cần tối ưu.
2. Hệ thống tạo metadata SEO.
3. Actor chọn loại báo cáo → hệ thống hiển thị kết quả.     

Exception Flow:
UC-06.EX.1: Không có dữ liệu phù hợp → hiển thị “Không có dữ liệu”.
UC-06.EX.2: Lỗi tạo sitemap → hệ thống cảnh báo.

Use Case 7: Kiểm thử & bảo trì hệ thống

Use Case ID: UC-07
Actor: Developer, QA Tester
Trigger: Có phiên bản mới hoặc cập nhật nội dung.

Description:
Thực hiện kiểm thử đơn vị, tích hợp và end-to-end để đảm bảo
hệ thống hoạt động ổn định.

Preconditions:
Mã nguồn đã được cập nhật.

Postconditions:
Kết quả kiểm thử được ghi nhận.

Basic Flow:
1. Developer viết unit test cho module mới.
2. QA thực hiện integration test và E2E test.
3. Ghi nhận kết quả và báo cáo.

Exception Flow:
UC-07.EX.1: Test thất bại → rollback phiên bản.
UC-07.EX.2: Lỗi môi trường → chuyển sang staging.
