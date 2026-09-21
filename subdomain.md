# Phân rã Subdomain và Mối quan hệ trong Hệ thống CAB System

## 1. Danh sách các Subdomain

### 1.1. Subdomain: User Data (Quản lý dữ liệu người dùng)

* **Mô tả:** Đóng vai trò là miền lưu trữ và quản lý tập trung toàn bộ thông tin định danh của tất cả các bên tham gia hệ thống (Khách hàng, Tài xế, Quản trị viên).

* **Trách nhiệm nghiệp vụ:**

  * Lưu trữ thông tin cá nhân (Họ tên, số điện thoại, email, ảnh đại diện).

  * Quản lý trạng thái tài khoản (Đang hoạt động, bị khóa, chờ duyệt).

  * Lưu trữ thông tin phân quyền vai trò (Khách hàng, Tài xế, Nhân viên vận hành).

### 1.2. Subdomain: Booking (Đặt xe & Phân công chuyến đi)

* **Mô tả:** Miền cốt lõi (**Core Domain**) của toàn bộ hệ thống, chịu trách nhiệm xử lý toàn bộ luồng nghiệp vụ từ lúc khách hàng yêu cầu xe cho đến khi kết thúc chuyến đi.

* **Trách nhiệm nghiệp vụ:**

  * Tiếp nhận yêu cầu đặt xe với điểm đón, điểm đến và loại xe mong muốn.

  * Thực hiện thuật toán tìm kiếm và ghép nối tài xế phù hợp ở gần khu vực nhất.

  * Quản lý trạng thái vòng đời chuyến đi (Đang tìm tài xế $\rightarrow$ Tài xế đang đến $\rightarrow$ Đang di chuyển $\rightarrow$ Hoàn thành/Hủy).

  * Xử lý các tình huống hủy chuyến hoặc thay đổi lộ trình phát sinh.

### 1.3. Subdomain: Payment (Thanh toán & Cước phí)

* **Mô tả:** Miền hỗ trợ chuyên xử lý các bài toán về tài chính, tính toán chi phí và giao dịch tiền tệ.

* **Trách nhiệm nghiệp vụ:**

  * Tính toán tiền cước dựa trên quãng đường thực tế, thời gian và biểu giá của loại xe.

  * Tích hợp các cổng thanh toán điện tử hoặc ghi nhận thanh toán tiền mặt.

  * Quản lý lịch sử giao dịch và xử lý các sự cố hoàn tiền, thanh toán lại khi lỗi.

### 1.4. Subdomain: Fleet & Driver Management (Quản lý đội xe & Tài xế)

* **Mô tả:** Miền chuyên trách quản lý các tài nguyên đầu vào phía tài xế và phương tiện vận tải.

* **Trách nhiệm nghiệp vụ:**

  * Quản lý hồ sơ pháp lý của tài xế (Bằng lái xe, giấy tờ tùy thân, lý lịch).

  * Quản lý danh mục phương tiện (Biển số, dòng xe, kiểm định chất lượng).

  * Cập nhật trạng thái trực tuyến (`Online`/`Offline`) và vị trí thời gian thực của tài xế để phục vụ việc điều phối.

## 2. Mối quan hệ và Tương tác giữa các Subdomain

Hệ thống **Booking** đóng vai trò là trung tâm điều phối, kết nối trực tiếp với 3 subdomain còn lại.

### 2.1. Booking $\longleftrightarrow$ User Data

* **Loại quan hệ:** Phụ thuộc / Truy vấn thông tin.

* **Cách thức:** Khi thực hiện đặt xe hoặc nhận chuyến, hệ thống **Booking** truy vấn sang **User Data** để lấy thông tin định danh và hiển thị cho các bên liên quan.

### 2.2. Booking $\longleftrightarrow$ Fleet & Driver Management

* **Loại quan hệ:** Điều phối & Ghép nối trực tiếp (Core Integration).

* **Cách thức:**

  * **Booking** yêu cầu **Fleet & Driver** cung cấp danh sách tài xế trực tuyến, gần điểm đón nhất.

  * Sau khi ghép nối thành công, **Booking** yêu cầu cập nhật trạng thái tài xế từ `Sẵn sàng` thành `Đang bận`.

### 2.3. Booking $\longleftrightarrow$ Payment

* **Loại quan hệ:** Kích hoạt tài chính theo sự kiện (Event-driven).

* **Cách thức:** Khi sự kiện `TripCompleted` (Chuyến đi hoàn thành) phát sinh ở miền **Booking**, một Domain Event được bắn sang miền **Payment** để kích hoạt việc tính cước và thanh toán.

### 2.4. Fleet & Driver Management $\longleftrightarrow$ User Data

* **Loại quan hệ:** Kế thừa thông tin định danh.

* **Cách thức:** Hồ sơ tài xế trong miền **Fleet & Driver** liên kết chặt chẽ với dữ liệu tài khoản gốc nằm ở miền **User Data** để quản lý thông tin đăng nhập và bảo mật chung.