# Phân tích Mối Quan Hệ Giữa Các Subdomain Trong Hệ Thống CAB System

## 1. Xác định subdomain

### 1.1. **Authentication & Authorization Subdomain (Miền Xác thực & Phân quyền)**

* **Mô tả:** Quản lý toàn bộ vòng đời tài khoản người dùng và bảo mật hệ thống.

* **Các chức năng / Use Case đảm nhận:**

  * Đăng ký tài khoản (Khách hàng, Tài xế).

  * Đăng nhập / Đăng xuất hệ thống.

  * Xác thực và phân quyền người dùng theo vai trò (RBAC).

* **Thực thể dữ liệu chính:** Người dùng (`TaiKhoan`), Phiên đăng nhập.

### 1.2. **Customer Management Subdomain (Miền Quản lý Khách hàng)**

* **Mô tả:** Quản lý thông tin định danh cá nhân của khách hàng và lịch sử tương tác của họ với dịch vụ.

* **Các chức năng / Use Case đảm nhận:**

  * Xem và cập nhật thông tin cá nhân khách hàng.

  * Xem lịch sử chuyến đi và đánh giá tài xế.

* **Thực thể dữ liệu chính:** Khách hàng, Lịch sử chuyến đi, Đánh giá.

### 1.3. **Driver & Fleet Management Subdomain (Miền Quản lý Tài xế & Phương tiện)**

* **Mô tả:** Quản lý hồ sơ tài xế, phương tiện di chuyển và trạng thái hoạt động sẵn sàng nhận việc.

* **Các chức năng / Use Case đảm nhận:**

  * Xem và cập nhật hồ sơ tài xế (bởi tài xế hoặc nhân viên vận hành).

  * Quản lý thông tin phương tiện.

  * Cập nhật trạng thái sẵn sàng (Sẵn sàng / Không sẵn sàng).

* **Thực thể dữ liệu chính:** Tài xế (`TaiXe`), Phương tiện (`PhuongTien`), Trạng thái sẵn sàng.

### 1.4. **Trip & Dispatching Subdomain (Miền Quản lý Đặt xe & Phân công chuyến đi)** — *Core Subdomain*

* **Mô tả:** Đây là miền cốt lõi (Core Domain) xử lý toàn bộ luồng nghiệp vụ đặt xe, thuật toán tìm kiếm, phân công tài xế thông minh và theo dõi hành trình thời gian thực.

* **Các chức năng / Use Case đảm nhận:**

  * Tiếp nhận và xử lý yêu cầu đặt xe từ khách hàng.

  * Tìm kiếm và phân công tài xế phù hợp (dựa trên vị trí GPS và loại xe).

  * Xử lý trường hợp tài xế từ chối hoặc không phản hồi (tự động chuyển tiếp).

  * Nhận / Từ chối chuyến từ phía tài xế.

  * Cập nhật và theo dõi trạng thái, vị trí chuyến đi theo thời gian thực.

* **Thực thể dữ liệu chính:** Yêu cầu đặt xe (`YeuCauDatXe`), Chuyến đi (`ChuyenDi`), Vị trí (`VongLapGPS`).

### 1.5. **Billing & Payment Subdomain (Miền Tính cước & Thanh toán)**

* **Mô tả:** Xử lý logic nghiệp vụ tính cước phí di chuyển và tích hợp cổng thanh toán để thu phí an toàn.

* **Các chức năng / Use Case đảm nhận:**

  * Tính cước chuyến đi tự động dựa trên quãng đường/loại xe.

  * Lựa chọn phương thức thanh toán (Tiền mặt / Điện tử).

  * Xử lý và ghi nhận kết quả thanh toán (tích hợp nhà cung cấp thanh toán bên ngoài).

  * Xử lý giao dịch thất bại và hỗ trợ thanh toán lại.

* **Thực thể dữ liệu chính:** Cước chuyến đi (`Cuoc`), Giao dịch (`GiaoDich`).

### 1.6. **Operations Management Subdomain (Miền Quản lý Vận hành)**

* **Mô tả:** Hỗ trợ bộ phận vận hành giám sát hệ thống, theo dõi các chuyến xe đang diễn ra và xử lý sự cố.

* **Các chức năng / Use Case đảm nhận:**

  * Theo dõi và quản lý các chuyến đang diễn ra.

  * Hỗ trợ xử lý chuyến đi gặp sự cố.

  * Tra cứu thông tin giao dịch.

* **Thực thể dữ liệu chính:** Sự cố chuyến đi, Nhật ký hệ thống (Audit Logs).

### 1.7. **Notification Subdomain (Miền Thông báo)**

* **Mô tả:** Subdomain hỗ trợ chịu trách nhiệm gửi thông tin tương tác đa kênh đến người dùng.

* **Các chức năng / Use Case đảm nhận:**

  * Gửi thông báo tự động về trạng thái chuyến đi, phân công tài xế, kết quả thanh toán.

  * Tích hợp nhà cung cấp thông báo đa kênh (App Push, SMS, Email) và cơ chế chuyển đổi kênh dự phòng.

* **Thực thể dữ liệu chính:** Bản ghi thông báo (`ThongBao`).

### 1.8. **Reporting & Analytics Subdomain (Miền Báo cáo & Thống kê)**

* **Mô tả:** Cung cấp thông tin tổng hợp phục vụ cho ban lãnh đạo ra quyết định kinh doanh.

* **Các chức năng / Use Case đảm nhận:**

  * Tổng hợp, thống kê dữ liệu chuyến đi, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy.

  * Xem báo cáo hiệu quả hoạt động của tài xế và doanh nghiệp.

* **Thực thể dữ liệu chính:** Báo cáo tổng hợp, Dữ liệu thống kê doanh thu.

## 2. Chi tiết các mối quan hệ giữa các Subdomain

### 2.1. Trip & Dispatching Subdomain (Core Domain) $\longleftrightarrow$ Driver & Fleet Management Subdomain

* **Loại quan hệ:** Phụ thuộc trực tiếp / Ghép nối điều phối (Upstream - Downstream)

* **Cách thức tương tác:**

  * Khi có yêu cầu đặt xe từ khách, **Trip & Dispatching** truy vấn sang **Driver & Fleet Management** để lấy danh sách các tài xế đang ở trạng thái `Sẵn sàng` kèm theo vị trí GPS gần nhất.

  * Sau khi hệ thống chọn được tài xế, **Trip & Dispatching** gửi lệnh cập nhật trạng thái tài xế thành `Bận / Đang có chuyến` sang **Driver & Fleet Management**.

### 2.2. Trip & Dispatching Subdomain $\longleftrightarrow$ Customer Management Subdomain

* **Loại quan hệ:** Truy vấn thông tin lịch sử & định danh

* **Cách thức tương tác:**

  * **Customer Management** quản lý hồ sơ chi tiết và lịch sử chuyến đi của khách hàng. Khi chuyến đi được tạo hoặc kết thúc tại **Trip & Dispatching**, dữ liệu lịch sử chuyến đi và điểm đánh giá sẽ được ghi nhận đồng bộ hoặc phát sinh sự kiện (`Domain Event`) để cập nhật vào miền Quản lý Khách hàng.

### 2.3. Trip & Dispatching Subdomain $\longleftrightarrow$ Billing & Payment Subdomain

* **Loại quan hệ:** Kích hoạt tài chính theo sự kiện (Event-driven Integration)

* **Cách thức tương tác:**

  * Khi **Trip & Dispatching** ghi nhận sự kiện chuyến đi chuyển sang trạng thái hoàn thành (`TripCompleted`), hệ thống sẽ phát một Domain Event chứa thông tin quãng đường và loại xe sang **Billing & Payment**.

  * **Billing & Payment** nhận sự kiện, tiến hành tính cước tự động, xử lý giao dịch thanh toán qua tiền mặt hoặc cổng điện tử.

### 2.4. Tất cả các Subdomain nghiệp vụ $\longleftrightarrow$ Authentication & Authorization Subdomain

* **Loại quan hệ:** Phụ thuộc nền tảng bảo mật (Shared Kernel / Customer-Supplier)

* **Cách thức tương tác:**

  * Mọi hành động thực hiện trong các miền như **Customer Management**, **Driver & Fleet Management**, **Trip & Dispatching**, và **Operations Management** đều phải thông qua việc xác thực token và kiểm tra quyền hạn (RBAC) do **Authentication & Authorization** cung cấp.

### 2.5. Các Subdomain nghiệp vụ $\longleftrightarrow$ Notification Subdomain

* **Loại quan hệ:** Tích hợp bất đồng bộ dựa trên sự kiện (Event-driven Notification)

* **Cách thức tương tác:**

  * Khi các sự kiện quan trọng xảy ra ở các miền khác (Ví dụ: Tìm thấy tài xế ở **Trip & Dispatching**, hoặc hoàn tất thanh toán ở **Billing & Payment**), các miền này sẽ phát sự kiện để **Notification Subdomain** tiếp nhận và gửi thông báo đa kênh (App Push, SMS, Email) đến người dùng.

### 2.6. Operations Management Subdomain $\longleftrightarrow$ Trip & Dispatching & Billing Subdomain

* **Loại quan hệ:** Giám sát và Quản lý tập trung (Monitoring / Read Model)

* **Cách thức tương tác:**

  * **Operations Management** thực hiện truy vấn trực tiếp hoặc đọc dữ liệu từ các bảng/event stream của **Trip & Dispatching** (để theo dõi xe đang chạy, xử lý sự cố) và **Billing & Payment** (để tra cứu giao dịch khi có khiếu nại).

### 2.7. Reporting & Analytics Subdomain $\longleftrightarrow$ Toàn bộ hệ thống

* **Loại quan hệ:** Tiêu thụ dữ liệu phân tích (Data Consumer / OLAP)

* **Cách thức tương tác:**

  * Miền này thu thập dữ liệu tổng hợp (qua Data Warehouse hoặc Event Sourcing) từ **Trip & Dispatching** (tỷ lệ hủy, doanh thu chuyến đi), **Billing & Payment** (doanh thu), và **Driver & Fleet Management** (hiệu suất tài xế) để phục vụ ban lãnh đạo lập báo cáo thống kê.