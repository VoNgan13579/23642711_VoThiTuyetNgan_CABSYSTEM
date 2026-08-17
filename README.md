# 23642711_VoThiTuyetNgan_CABSYSTEM
**Bước 1: Hiểu nghiệp vụ**
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

**Bước 2: Xác định stakeholder trong hệ thống**

|        Stakeholder      |                                                       Vai trò                                                                                |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| Khách hàng              | Đăng ký/đăng nhập, quản lý thông tin cá nhân, đặt xe, theo dõi chuyến đi, thanh toán, xem lịch sử và đánh giá tài xế.                        |
| Tài xế                  | Quản lý hồ sơ và phương tiện, cập nhật trạng thái hoạt động, nhận/từ chối chuyến, cập nhật trạng thái chuyến và vị trí.                      | 
| Nhân viên vận hành      | Quản lý khách hàng, tài xế, phương tiện và chuyến đi; theo dõi chuyến đang diễn ra; xử lý các trường hợp chuyến bị lỗi và tra cứu giao dịch. | 
| Ban lãnh đạo            | Theo dõi báo cáo về số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế; đưa ra quyết định quản lý.     |
| Nhà cung cấp thanh toán | Xử lý các giao dịch thanh toán trực tuyến.                                                                                                   |
| Nhà cung cấp thông báo  | Cung cấp các kênh gửi thông báo đến khách hàng và tài xế, đồng thời hỗ trợ mở rộng thêm các kênh trong tương lai.                            |

``` mermaid
quadrantChart
    title Stakeholder Matrix - CAB System
    x-axis "Mức độ quan tâm thấp" --> "Mức độ quan tâm cao"
    y-axis "Quyền lực thấp" --> "Quyền lực cao"

    quadrant-1 "Quản lý chặt chẽ"
    quadrant-2 "Giữ hài lòng"
    quadrant-3 "Theo dõi"
    quadrant-4 "Giữ thông tin"

    "Ban lãnh đạo": [0.75, 0.90]
    "Nhân viên vận hành": [0.90, 0.80]
    "Khách hàng": [0.95, 0.55]
    "Tài xế": [0.90, 0.55]
    "Nhà cung cấp thanh toán": [0.55, 0.65]
    "Nhà cung cấp thông báo": [0.45, 0.45]
``` 

**Bước 3: Mục đích của nghiệp vụ**
1. Tối ưu hóa và tự động hóa quy trình vận hành

Tự động hóa luồng phân công: Loại bỏ việc phân công thủ công từ tổng đài bằng cơ chế tự động tìm và ưu tiên tài xế phù hợp dựa trên vị trí GPS, loại xe và trạng thái sẵn sàng.

Tự động chuyển tiếp yêu cầu: Tự động luôn chuyển chuyến đi sang tài xế tiếp theo nếu tài xế đầu tiên từ chối hoặc không phản hồi, giúp khách hàng không phải tạo lại yêu cầu.

Rút ngắn thời gian chờ: Giảm tối đa thời gian chờ xe (ETA) của khách hàng nhờ cơ chế ưu tiên tài xế gần nhất.

2. Nâng cao trải nghiệm người dùng và linh hoạt thanh toán

Theo dõi thời gian thực: Cho phép khách hàng theo dõi vị trí tài xế, hành trình di chuyển và thời gian dự kiến đến ngay trên ứng dụng.

Đa dạng phương thức thanh toán: Hỗ trợ linh hoạt cả Thanh toán tiền mặt (trả trực tiếp cho tài xế) và Thanh toán điện tử / Chuyển khoản (tích hợp cổng thanh toán bên ngoài an toàn, không lưu trữ dữ liệu thẻ nhạy cảm).

Thông báo tức thời: Cung cấp hệ thống thông báo đa kênh (App Push, SMS, Email) ở các mốc quan trọng: nhận chuyến, tài xế đến, hoàn thành và kết quả thanh toán.

Đánh giá dịch vụ: Thu thập phản hồi và đánh giá từ khách hàng sau mỗi chuyến đi để nâng cao chất lượng tài xế.

3. Đảm bảo hiệu năng cao và chịu tải thời điểm nhu cầu tăng cao

Chịu tải cao đồng thời: Đảm bảo hệ thống hoạt động ổn định, mượt mà ngay cả khi có số lượng lớn khách hàng và tài xế cùng truy cập vào các khung giờ cao điểm (giờ tan tầm, thời tiết xấu, lễ tết).

Kiến trúc độc lập (Decoupled Architecture): Cách ly rủi ro để khi xảy ra sự cố ở các chức năng phụ như thanh toán hay thông báo thì luồng đặt xe cốt lõi vẫn hoạt động bình thường.

Mở rộng linh hoạt trong tương lai: Tạo tiền đề kỹ thuật để dễ dàng bổ sung thêm loại hình dịch vụ mới, phương thức thanh toán mới hoặc nhà cung cấp thông báo mới mà không phải xây dựng lại toàn bộ hệ thống.

4. Quản lý tập trung và hỗ trợ ra quyết định kinh doanh

Tập trung dữ liệu master: Quản lý tập trung toàn bộ thông tin khách hàng, tài xế, phương tiện, chuyến đi và lịch sử giao dịch trên một giao diện quản trị duy nhất.

Báo cáo và đo lường: Cung cấp cho Ban lãnh đạo hệ thống báo cáo chuyên sâu về doanh thu, tổng số chuyến, tỷ lệ hoàn thành, tỷ lệ hủy chuyến và hiệu suất hoạt động của tài xế.

Bảo mật và truy vết: Phân quyền truy cập theo vai trò (RBAC) để kiểm soát các thao tác nhạy cảm của nhân viên vận hành, đồng thời ghi nhận vết hệ thống (Audit Logs) phục vụ tra cứu khi xảy ra sự cố.

**Bước 4: Xác định phạm vi cần làm cho dự án trong 7 tuần**

