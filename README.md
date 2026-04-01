# Hệ Thống Bán Laptop Online - Dự Án Angular

Đây là một ứng dụng web bán hàng laptop được xây dựng bằng **Angular 20**, sử dụng dữ liệu giả (JSON Server) và các công nghệ hiện đại.

---

## Mục Lục

1. [Tính Năng Chính](tính-năng-chính)

2. [Công Nghệ Sử Dụng](công-nghệ-sử-dụng)

3. [Cấu Trúc Dự Án](cấu-trúc-dự-án)

4. [Yêu Cầu Hệ Thống](yêu-cầu-hệ-thống)

5. [Hướng Dẫn Setup Chi Tiết](hướng-dẫn-setup-chi-tiết)

6. [Cách Chạy Dự Án](cách-chạy-dự-án)

7. [Cấu Trúc Database](cấu-trúc-database)

8. [Hướng Dẫn Để Người Khác Clone & Chạy](hướng-dẫn-để-người-khác-clone--chạy)

---

## Tính Năng Chính

### Cho Người Dùng (User)

- **Duyệt Sản Phẩm**: Xem danh sách 28+ mẫu laptop từ các hãng (Lenovo, HP, Dell, ASUS, Acer, Apple, MSI)
- **Lọc & Tìm Kiếm**: Tìm kiếm theo tên, hãng sản xuất hoặc danh mục
- **Chi Tiết Sản Phẩm**: Xem thông tin chi tiết, giá, khuyến mãi của từng laptop
- **Giỏ Hàng**: Thêm/xóa sản phẩm, cập nhật số lượng, chọn multiple items
- **Đăng Ký & Đăng Nhập**: Tạo tài khoản mới, đăng nhập an toàn
- **Lịch Sử Mua Hàng**: Xem các đơn hàng đã tạo với trạng thái (Đang xử lý, Đã giao hàng, Đã hủy)
- **Đặt Hàng**: Tạo đơn hàng từ giỏ hàng với tổng tiền tự động tính
- **Trang Tin Tức & Giới Thiệu**: Xem thông tin về shop

### Cho Quản Trị Viên (Admin)

- **Đăng Nhập Admin**: Bảo vệ route dashboard bằng CanActivate guard
- **Quản Lý Sản Phẩm (EBook)**: Thêm, sửa, xóa laptop
- **Quản Lý Đơn Hàng**: Xem tất cả đơn hàng, thay đổi trạng thái
- **Quản Lý Người Dùng**: Khóa/mở khóa tài khoản, xem danh sách user

### Tính Năng Giao Diện

- **Header & Footer**: Thanh điều hướng chung cho tất cả trang
- **Slider**: Hiển thị ảnh quảng cáo tự động cuộn
- **Responsive**: Giao diện thích ứng với các thiết bị khác nhau
- **Một Trang Ứng Dụng (SPA)**: Chuyển đổi nhanh giữa các trang mà không reload

---

## Công Nghệ Sử Dụng

### Frontend

- **Angular 20.1.0** - Framework JavaScript hiện đại, component-based
- **TypeScript 5.8.2** - Ngôn ngữ lập trình an toàn kiểu
- **Bootstrap 5.3.8** - Framework CSS cho giao diện responsive
- **RxJS 7.8.0** - Xử lý bất đồng bộ và Observable
- **Angular Router** - Điều hướng giữa các trang (SPA)
- **Angular Forms** - Xử lý form đăng nhập, đăng ký, tìm kiếm
- **Angular HttpClient** - Gọi API REST

### Backend (Giả)

- **json-server** - Cung cấp REST API giả từ file `db.json`
- **Node.js & npm** - Quản lý dependencies

### Dev Tools

- **Angular CLI 20.1.6** - Công cụ phát triển Angular
- **Karma & Jasmine** - Framework test (đã được setup sẵn)

### Version Control

- **Git** - Quản lý mã nguồn

---

## Cấu Trúc Dự Án

```
d:\...\myangular/
├── db.json                          # Database giả (JSON Server)
├── README.md                        # Tài liệu này
└── demo_final/                      # Thư mục Angular app
    ├── package.json                 # Dependencies & scripts
    ├── angular.json                 # Cấu hình Angular CLI
    ├── tsconfig.json                # Cấu hình TypeScript
    ├── src/
    │   ├── index.html               # HTML chính
    │   ├── main.ts                  # Entry point app
    │   ├── styles.css               # CSS global
    │   └── app/
    │       ├── app.ts               # Root component
    │       ├── app.routes.ts        # Định nghĩa routes
    │       ├── app.config.ts        # Cấu hình app
    │       ├── interfaces/          # Interface TypeScript
    │       │   ├── book.ts
    │       │   ├── order.ts
    │       │   └── users.ts
    │       ├── services/            # Services (logic gọi API, state management)
    │       │   ├── bookservice.ts
    │       │   ├── cart-service.ts
    │       │   ├── auth.ts
    │       │   ├── order-service.ts
    │       │   └── admin-auth.ts
    │       ├── components/
    │       │   ├── header/          # Header thanh điều hướng
    │       │   ├── footer/          # Footer
    │       │   ├── home/            # Trang chủ
    │       │   ├── product/         # Trang sản phẩm
    │       │   ├── bookdetail/      # Chi tiết sản phẩm
    │       │   ├── cart/            # Giỏ hàng
    │       │   ├── auth/
    │       │   │   ├── login/       # Đăng nhập user
    │       │   │   └── register/    # Đăng ký
    │       │   ├── admin-login/     # Đăng nhập admin
    │       │   ├── dashboard/       # Bảng điều khiển admin
    │       │   ├── ebook/           # Quản lý laptop
    │       │   ├── orders/          # Quản lý đơn hàng
    │       │   ├── users/           # Quản lý người dùng
    │       │   ├── history/         # Lịch sử mua hàng user
    │       │   ├── about/           # Trang giới thiệu
    │       │   └── news/            # Trang tin tức
    │       └── (các file .spec.ts = file test)
    └── public/
        └── image/                   # Ảnh sản phẩm
```

---

## Yêu Cầu Hệ Thống

- **Node.js >= 18.0.0** (khuyến nghị v20+)
- **npm >= 9.0.0**
- **Git** (để clone repo)
- **Chrome, Firefox, Edge hoặc Safari** (trình duyệt hiện đại)

### Kiểm tra

```bash
node --version    # Phải >= v18.0.0
npm --version     # Phải >= 9.0.0
git --version     # Phải cài sẵn
```

---

## Hướng Dẫn Setup Chi Tiết

### Bước 1: Clone Repository

```bash
git clone <repository-url>
cd myangular
```

Nếu bạn đã có folder, bạn có thể bỏ qua bước này.

### Bước 2: Cài Đặt Dependencies (NPM Packages)

Đi vào thư mục `demo_final`:

```bash
cd demo_final
npm install
```

Lệnh này sẽ:

- Tải tất cả dependencies từ `package.json`
- Tạo thư mục `node_modules/` chứa toàn bộ thư viện
- Thời gian: 2-5 phút tùy vào internet

**Nếu gặp lỗi:**

- Xóa `node_modules` & `package-lock.json`, rồi chạy `npm install` lại
- Hoặc chạy `npm cache clean --force` nếu cache bị hỏng

### Bước 3: Kiểm Tra Cấu Hình

Mở file `src/app/services/bookservice.ts` và xác nhận các endpoint:

```typescript
private apiUrl = 'http://localhost:3000/products';  // Phải là 3000
```

Tương tự kiểm tra các service khác:

- `cart-service.ts`: `http://localhost:3000/cart`
- `auth.ts`: `http://localhost:3000/customers`
- `order-service.ts`: `http://localhost:3000/orders`
- `admin-auth.ts`: `http://localhost:3000/adminUsers`

---

## Cách Chạy Dự Án

Bạn cần **2 terminal** chạy đồng thời:

### Terminal 1: Chạy JSON Server (Backend giả)

**Mở terminal ở thư mục gốc** (thư mục chứa `db.json`):

```bash
# Nếu đang ở demo_final, quay lại thư mục cha
cd ..

# Chạy json-server
npx json-server --watch db.json --port 3000
```

**Output mong đợi:**

```bash
  ✔ listening on port 3000
  ✔ Press CTRL-C to stop

  ⚊ http://localhost:3000 (CORS enabled ✓)

  Routes:
  /products
  /customers
  /cart
  /orders
  /adminUsers
```

**Kiểm tra**: Mở trình duyệt, truy cập `http://localhost:3000/products` — phải thấy JSON

---

### Terminal 2: Chạy Angular Dev Server

**Mở terminal khác** ở thư mục `demo_final`:

```bash
cd demo_final
ng serve --open
```

**Hoặc dùng npm script:**

```bash
npm start
```

**Output mong đợi:**

```bash
✔ Compiled successfully.

→ Local:       http://localhost:4200/
```

Trình duyệt sẽ tự động mở `http://localhost:4200/` — bạn sẽ thấy trang chủ với danh sách laptop.

---

## Kiểm Tra Ứng Dụng Hoạt Động

1. **Xem Danh Sách Laptop**: Trang chủ hiển thị ~28 sản phẩm
2. **Tìm Kiếm**: Nhập "Lenovo" trong ô tìm kiếm — lọc sản phẩm
3. **Thêm Vào Giỏ**: Bấm nút "Tất Cả Laptop" → chọn sản phẩm → "Thêm vào giỏ"
4. **Xem Giỏ Hàng**: Click icon giỏ hàng ở header — xem sản phẩm trong giỏ
5. **Đăng Nhập User**: Click "Đăng nhập" → Dùng:
   - Username: `123123` | Password: `123123`
   - Hoặc: Username: `longgg` | Password: `123123`
6. **Đăng Nhập Admin**: Click "Trang chủ" → URL thay đổi thành `/admin` → Dùng:
   - Username: `admin` | Password: `adminpassword123`
7. **Quản Lý Dashboard**: Sau đăng nhập admin, vào `/dashboard` → quản lý EBook/Orders/Users

---

## Cấu Trúc Database (`db.json`)

### 1. **Products** (Danh sách laptop)

```json
{
  "id": "1",
  "title": "Laptop Lenovo IdeaPad Slim 3",
  "image": "/image/Lenovo_ideaPad_slim_3.webp",
  "category": "new",
  "author": "Lenovo",
  "description": "...",
  "price": 18990000,
  "discount": 15,
  "stock": 50,
  "publishDate": "2020",
  "translator": "Chưa xác định"
}
```

### 2. **Customers** (Người dùng)

```json
{
  "id": "76f1",
  "username": "123123",
  "password": "123123",
  "fullname": "123123",
  "email": "123123@gmai.com",
  "phone": "0123123123",
  "address": "123123",
  "isLocked": false
}
```

### 3. **Cart** (Giỏ hàng)

```json
{
  "id": "...",
  "productId": "1",
  "title": "Laptop Lenovo IdeaPad Slim 3",
  "price": 18990000,
  "quantity": 1,
  "image": "/image/...",
  "discount": 15,
  "active": false
}
```

### 4. **Orders** (Đơn hàng)

```json
{
  "id": "...",
  "userId": "76f1",
  "date": "2024-11-20T10:30:00Z",
  "status": "Đang xử lý",
  "items": [...],
  "totalAmount": 18990000
}
```

### 5. **AdminUsers** (Quản trị viên)

```json
{
  "id": "1",
  "username": "admin",
  "password": "adminpassword123",
  "role": "admin",
  "name": "Ông Chủ"
}
```

---

## Khắc Phục Các Lỗi Thường Gặp

### Lỗi: `ERR_CONNECTION_REFUSED` (Port 3000)

**Nguyên nhân**: Json-server chưa chạy hoặc cổng 3000 đã bị chiếm

**Cách sửa**:

```bash
# Đảm bảo Terminal 1 chạy:
npx json-server --watch db.json --port 3000

# Nếu port 3000 bị chiếm, dùng port khác:
npx json-server --watch db.json --port 3001
# Rồi cập nhật URL trong services từ 3000 → 3001
```

### Lỗi: `Module not found` hoặc `npm install failed`

**Cách sửa**:

```bash
cd demo_final
rm -rf node_modules package-lock.json
npm cache clean --force
npm install
```

### Lỗi: `ng: command not found`

**Cách sửa**:

```bash
# Cài Angular CLI globally
npm install -g @angular/cli

# Hoặc chạy qua npx
npx ng serve
```

### Lỗi: PowerShell script execution policy (Windows)

**Cách sửa**:

```powershell
# Mở PowerShell as Administrator, chạy:
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

# Hoặc dùng lệnh bypass session:
powershell -NoProfile -ExecutionPolicy Bypass -Command "npx json-server --watch db.json --port 3000"
```

---

## Cấu Trúc Code Chính

### Services (Gọi API & Quản Lý State)

**BookService** (`src/app/services/bookservice.ts`)

- `getBook()` - Lấy tất cả sách
- `create()` - Tạo sách mới
- `update()` - Cập nhật sách
- `delete()` - Xóa sách
- `searchBooks()` - Tìm kiếm sách

**CartService** (`src/app/services/cart-service.ts`)

- `addToCart()` - Thêm vào giỏ
- `removeCart()` - Xóa khỏi giỏ
- `updateQuantity()` - Cập nhật số lượng
- `clearCart()` - Xóa hết giỏ

**AuthService** (`src/app/services/auth.ts`)

- `login()` - Đăng nhập user
- `register()` - Đăng ký tài khoản
- `getAllUsers()` - Lấy danh sách user
- `logout()` - Đăng xuất

**OrderService** (`src/app/services/order-service.ts`)

- `addOrder()` - Tạo đơn hàng
- `updateOrderStatus()` - Thay đổi trạng thái
- `deleteOrder()` - Xóa đơn hàng

**AdminAuthService** (`src/app/services/admin-auth.ts`)

- `login()` - Đăng nhập admin
- `canActivate()` - Guard route dashboard

### Routes (Điều hướng)

- `/` - Trang chủ
- `/product` - Danh sách sản phẩm
- `/book/:id` - Chi tiết sản phẩm
- `/cart` - Giỏ hàng
- `/login` - Đăng nhập user
- `/register` - Đăng ký
- `/history` - Lịch sử mua hàng
- `/admin` - Đăng nhập admin
- `/dashboard` - Bảng điều khiển admin (protected route)
  - `/dashboard/ebook` - Quản lý laptop
  - `/dashboard/orders` - Quản lý đơn hàng
  - `/dashboard/users` - Quản lý user

---

## Công Nghệ & Pattern Học Được

 **Angular 20 Standalone Components** - Cách xây dựng component mới không cần NgModule
 **Angular Signals** - Reactive state management thay thế Observable
 **RxJS Observables** - Xử lý bất đồng bộ, HTTP request
 **Route Guards** - Bảo vệ route admin với `CanActivate`
 **Typed Forms & Validation** - FormsModule với [(ngModel)]
 **HTTP Interceptor Pattern** - (có thể thêm trong tương lai)
 **Component Lifecycle** - OnInit, OnDestroy hooks
 **Responsive Design** - Bootstrap 5 + CSS custom
 **REST API** - Gọi endpoints CRUD từ JSON Server

---

## Support & Liên Hệ

Nếu gặp vấn đề:

1. Kiểm tra phần **Khắc Phục Các Lỗi Thường Gặp** ở trên
2. Mở DevTools (F12) → Console → xem lỗi chi tiết
3. Kiểm tra 2 terminal có chạy (port 3000 & 4200)
4. Tạo issue trên GitHub nếu là member

---

## License

Dự án này là bài tập học tập. Cảm ơn bạn đã quan tâm!

---

**Chúc bạn chạy dự án thành công!**
