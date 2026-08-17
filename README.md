# 23642711_VoThiTuyetNgan_CABSYSTEM
Bước 1: Hiểu nghiệp vụ
1. Vấn đề hiện tại:
- Việc phân công tài xế chủ yếu được thực hiện thủ công
- Khách hàng khó theo dõi trạng thái chuyến đi 
- Thông tin thanh toán chưa được quản lý tập trung 
- Bộ phận vận hành gặp khó khăn khi muốn mở rộng hệ thống
2. Lý do xây dựng hệ thống mới:
- Tự động hóa quá trình tìm kiếm và phân công tài xế.
- Giúp khách hàng đặt xe và theo dõi chuyến đi dễ dàng.
- Quản lý tập trung khách hàng, tài xế, chuyến đi và thanh toán.
- Nâng cao khả năng mở rộng hệ thống khi nhu cầu tăng.
- Tăng tính ổn định, bảo mật và khả năng kiểm soát.
- Cho phép doanh nghiệp dễ dàng bổ sung dịch vụ, phương thức thanh toán và kênh thông báo mới trong tương lai.
3. Mục tiêu của hệ thống
- Xây dựng nền tảng đặt xe phục vụ khách hàng, tài xế và nhân viên vận hành.
- Tự động hóa quy trình từ đặt xe → tìm tài xế → thực hiện chuyến → tính cước → thanh toán → đánh giá.
- Cải thiện tốc độ và hiệu quả phân công tài xế.
- Quản lý tập trung dữ liệu và hỗ trợ báo cáo hoạt động kinh doanh.
- Đảm bảo hệ thống ổn định, bảo mật và có khả năng mở rộng.
- Tạo nền tảng linh hoạt để phát triển thêm các tính năng trong tương lai.
4. Ai sẽ tham gia và sử dụng hệ thống?
- Khách hàng: đặt xe, theo dõi chuyến, thanh toán và đánh giá.
- Tài xế: nhận chuyến, cập nhật trạng thái và thông tin vị trí.
- Nhân viên vận hành: quản lý khách hàng, tài xế, phương tiện và chuyến đi.
- Ban lãnh đạo: theo dõi báo cáo, doanh thu và hiệu quả hoạt động.
5. Hệ thống mới mang lại giá trị kinh doanh gì?
- Giảm chi phí và thời gian vận hành nhờ tự động hóa.
- Tăng doanh thu nhờ phục vụ được nhiều khách hàng hơn.
- Nâng cao trải nghiệm khách hàng thông qua đặt xe và theo dõi chuyến theo thời gian thực.
- Tăng hiệu quả sử dụng tài xế nhờ cơ chế tìm và ưu tiên tài xế phù hợp.
- Giúp doanh nghiệp quản lý và ra quyết định tốt hơn nhờ dữ liệu và báo cáo.
- Tạo nền tảng có thể mở rộng quy mô và phát triển dịch vụ mới trong tương lai.

Bước 2: Xác định stakeholder trong hệ thống

|        Stakeholder      |                                                       Vai trò                                                                                |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Khách hàng              | Đăng ký/đăng nhập, quản lý thông tin cá nhân, đặt xe, theo dõi chuyến đi, thanh toán, xem lịch sử và đánh giá tài xế.                        |
| Tài xế                  | Quản lý hồ sơ và phương tiện, cập nhật trạng thái hoạt động, nhận/từ chối chuyến, cập nhật trạng thái chuyến và vị trí.                      | 
| Nhân viên vận hành      | Quản lý khách hàng, tài xế, phương tiện và chuyến đi; theo dõi chuyến đang diễn ra; xử lý các trường hợp chuyến bị lỗi và tra cứu giao dịch. | 
| Ban lãnh đạo            | Theo dõi báo cáo về số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế; đưa ra quyết định quản lý.     |
| Nhà cung cấp thanh toán | Xử lý các giao dịch thanh toán điện tử cho khách hàng thông qua hệ thống tích hợp.                                                           |
| Nhà cung cấp thông báo  | Cung cấp các kênh gửi thông báo đến khách hàng và tài xế, đồng thời hỗ trợ mở rộng thêm các kênh trong tương lai.                            |

Xác định tầm quan trọng của stakeholder
| Stakeholder                        | Mức độ quan trọng    | Lý do                                                                                                                                                                       |
| ---------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Khách hàng**                     | ⭐⭐⭐⭐⭐ Rất cao        | Là người trực tiếp sử dụng hệ thống để đặt xe, theo dõi chuyến, thanh toán và đánh giá. Sự hài lòng của khách hàng ảnh hưởng trực tiếp đến doanh thu và chất lượng dịch vụ. |
| **Tài xế**                         | ⭐⭐⭐⭐⭐ Rất cao        | Là người trực tiếp thực hiện chuyến đi. Tài xế ảnh hưởng đến khả năng đáp ứng yêu cầu, thời gian phục vụ và chất lượng chuyến đi.                                           |
| **Nhân viên vận hành**             | ⭐⭐⭐⭐⭐ Rất cao        | Quản lý và giám sát hoạt động của hệ thống, xử lý các trường hợp phát sinh và hỗ trợ khách hàng, tài xế.                                                                    |
| **Ban lãnh đạo**                   | ⭐⭐⭐⭐ Cao             | Đưa ra định hướng, phê duyệt yêu cầu và theo dõi các chỉ số kinh doanh như doanh thu, số chuyến, tỷ lệ hoàn thành và tỷ lệ hủy.                                             |
| **Nhà cung cấp thanh toán**        | ⭐⭐⭐ Trung bình – Cao | Đảm bảo các giao dịch thanh toán điện tử được thực hiện. Nếu dịch vụ gặp lỗi có thể ảnh hưởng đến quá trình thanh toán.                                                     |
| **Nhà cung cấp dịch vụ thông báo** | ⭐⭐⭐ Trung bình – Cao | Đảm bảo hệ thống gửi thông báo đến khách hàng và tài xế. Tuy nhiên đây là hệ thống bên ngoài nên mức độ ảnh hưởng thấp hơn các nhóm sử dụng trực tiếp.                      |




