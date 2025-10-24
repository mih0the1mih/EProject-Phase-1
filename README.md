# 🛍️ E-Commerce Microservices System

## 📖 Giới thiệu
Dự án mô phỏng **hệ thống bán hàng online** được xây dựng theo kiến trúc **Microservices**, triển khai bằng **Docker Compose**.

Chức năng chính:
- Đăng ký, đăng nhập tài khoản.
- Quản lý sản phẩm.
- Đặt hàng và xem danh sách đơn hàng.

Mục tiêu là **phân tách hệ thống thành các dịch vụ nhỏ** giúp dễ mở rộng, bảo trì và triển khai độc lập.

---

## 🧩 Kiến trúc hệ thống

Hệ thống gồm **4 dịch vụ chính** và **2 thành phần hỗ trợ**:

| Thành phần | Chức năng chính |
|-------------|----------------|
| **API Gateway** | Tiếp nhận request từ client, định tuyến đến các service khác |
| **Auth Service** | Đăng ký, đăng nhập, xác thực JWT |
| **Product Service** | Thêm sản phẩm, xem sản phẩm |
| **Order Service** | Tạo và xử lý đơn hàng |
| **RabbitMQ** | Truyền thông điệp giữa các service (Order ↔ Product) |
| **MongoDB** | Lưu trữ dữ liệu riêng cho từng service |

---

## ⚙️ Công nghệ sử dụng
- **Node.js / Express.js**
- **MongoDB**
- **RabbitMQ**
- **JWT (JSON Web Token)**
- **Docker & Docker Compose**
- **Postman** (dùng để kiểm thử API)

 ###Các mẫu thiết kế được dùng
- Microservices: Tách nhỏ hệ thống để dễ bảo trì.
- API Gateway: Gom các service về một cổng gọi chung.
- Message Queue (RabbitMQ): Truyền dữ liệu giữa các service.
- Repository: Tách phần làm việc với database.

## 🔗 Cách các service giao tiếp

- Client → API Gateway (HTTP)

- API Gateway → Auth/Product/Order (HTTP nội bộ Docker)

- Order ↔ Product (qua RabbitMQ)

- Mỗi service có MongoDB riêng, không dùng chung database.


## 🚀 Cách chạy dự án

### 1.Tại thư mục gốc dự án, chạy lệnh:
docker-compose up --build

### 2. Kiểm thử nhanh (Postman)

Đăng ký: POST http://localhost:3003/auth/register

Đăng nhập: POST http://localhost:3003/auth/login

Thêm sản phẩm: POST http://localhost:3003/products/api/products

Đặt hàng: POST http://localhost:3003/products/api/products/buy

Lấy sản phẩm theo id: GET http://localhost:3003/products/api/products/<id>

Trần Phú Vinh --- 22684291
