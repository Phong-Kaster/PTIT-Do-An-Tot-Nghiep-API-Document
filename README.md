<h1 align="center">Đồ án tốt nghiệp - Học viện Công nghệ Bưu chính viễn thông <br/>
    Tài liệu mô tả API của Ứng dụng Android hỗ trợ bệnh nhân đăng ký khám và điều trị bệnh 
</h1>

<p align="center">
    <img src="./photo/umbrella-banner.jpg" />
</p>

# [**Table Of Content**](#table-of-content)
- [**Table Of Content**](#table-of-content)
- [**Introduction**](#introduction)
- [**Rules**](#rules)
  - [**1. Method**](#1-method)
  - [**2. Direction**](#2-direction)
  - [**3. Code**](#3-code)
- [**Document**](#document)
  - [**1. Authentication**](#1-authentication)
    - [**🟡 1.1. Login Patient**](#-11-login-patient)
    - [**🟡 1.2. Login Doctor**](#-12-login-doctor)
    - [**🟡 1.3. Sign Up**](#-13-sign-up)
    - [**🟡 1.4. Recovery**](#-14-recovery)
    - [**🟡 1.5. Password Reset**](#-15-password-reset)
  - [**2. Patients**](#2-patients)
    - [**🟢 2.1. Read All**](#-21-read-all)
    - [**🟢 2.2. Read By ID**](#-22-read-by-id)
    - [**🔵 2.3. Update**](#-23-update)
    - [**🟡 2.4. Delete**](#-24-delete)
  - [**3. Patient Profile**](#3-patient-profile)
    - [**🟢 3.1. Read Personal Information**](#-31-read-personal-information)
    - [**🟡 3.2. Change Personal Information**](#-32-change-personal-information)
    - [**🟡 3.3. Change Avatar**](#-33-change-avatar)
    - [**🟡 3.4. Change Password**](#-34-change-password)
  - [**4. Patient Booking**](#4-patient-booking)
    - [**🟢 4.1. Read All**](#-41-read-all)
    - [**🟢 4.2. Read By ID**](#-42-read-by-id)
    - [**🟡 4.3. Create**](#-43-create)
    - [**🔴 4.4. Cancel**](#-44-cancel)
  - [**5. Doctors**](#5-doctors)
    - [**🟢 5.1. Read All**](#-51-read-all)
    - [**🟢 5.2. Read By ID**](#-52-read-by-id)
    - [**🟡 5.3. Create**](#-53-create)
    - [**🔵 5.4. Update**](#-54-update)
    - [**🔴 5.5. Delete**](#-55-delete)
    - [**🟡 5.6. Update Avatar**](#-56-update-avatar)
  - [**6. Doctor Profile**](#6-doctor-profile)
    - [**🟢 6.1. Read Personal Information**](#-61-read-personal-information)
    - [**🟡 6.2. Change Personal Information**](#-62-change-personal-information)
    - [**🟡 6.3. Change Avatar**](#-63-change-avatar)
    - [**🟡 6.4. Change Password**](#-64-change-password)
  - [**7. Speciality**](#7-speciality)
    - [**🟢 7.1. Read All**](#-71-read-all)
    - [**🟢 7.2. Read By ID**](#-72-read-by-id)
    - [**🟡 7.3. Create**](#-73-create)
    - [**🔵 7.4. Update**](#-74-update)
    - [**🔴 7.5. Delete**](#-75-delete)
  - [**8. Services**](#8-services)
    - [**🟢 8.1. Read All**](#-81-read-all)
    - [**🟢 8.2. Read By ID**](#-82-read-by-id)
    - [**🟡 8.3. Create**](#-83-create)
    - [**🔵 8.4. Update**](#-84-update)
    - [**🔴 8.5. Delete**](#-85-delete)
  - [**9. Rooms**](#9-rooms)
    - [**🟢 9.1. Read All**](#-91-read-all)
    - [**🟢 9.2. Read By ID**](#-92-read-by-id)
    - [**🟡 9.3. Create**](#-93-create)
    - [**🔵 9.4. Update**](#-94-update)
    - [**🔴 9.5. Delete**](#-95-delete)

# [**Introduction**](#introduction)

Đây là tài liệu mô tả chi tiết từng API được mình - Nguyễn Thành Phong - viết và chuẩn bị trong đồ án.
Mình làm cái này để lưu lại cho mục đích liệt kê các chức năng mình đã làm. Đồng thời, đây là đồ án 
tốt nghiệp của mình nên mình muốn hoàn thiện ở mức đồ tốt nhất có thể.

# [**Rules**](#Rules)

Để dễ đọc & nhanh chóng hiểu cách dùng API này mình sẽ viết theo thứ tự 
[**Controller Timeline**](https://github.com/Phong-Kaster/PTIT-Do-An-Tot-Nghiep#controller-timeline) 
ở bên tài liệu [**Đồ án thực tập**](https://github.com/Phong-Kaster/PTIT-Do-An-Tot-Nghiep)

## [**1. Method**](#1-method)

API của mình viết theo chuẩn Restful API, trong đồ án của mình thì mình chỉ sử dụng 5 dạng phương thức quen thuộc 
sau để xây dựng đồ án:

- 🟢 **GET** - Để truy xuất một tài nguyên. Ví dụ: lấy thông tin 1 giao dịch thì dùng phương thức GET

- 🟡 **POST** - Để tạo một tài nguyên trên máy chủ. Ví dụ: tạo mới một tài khoản

- 🔵 **PUT** - Để thay đổi trạng thái toàn bộ một tài nguyên hoặc để cập nhật nó. Ví dụ: thay đổi mật khẩu, tên hiển thị

- 🟠 **PATCH** - Giống PUT nhưng PATCH thường dùng trong trường hợp sửa 1 phần của tài nguyên.

- 🔴 **DELETE** - Để huỷ bỏ hoặc xoá một tài nguyên. Ví dụ: xóa hoàn toàn một thể loại, bài viết,...

Hãy để ý một chút tới màu sắc mà mình quy ước bên trên. Mình sẽ sử dụng màu sắc kết hợp với các thông tin khác
để mô tả API.

## [**2. Direction**](#2-direction)

Để xem toàn bộ các điều hướng khi một API được gọi. Hãy mở `app/int/routes.inc.php` - đây là tệp tin chứa 
điều hướng & xử lý khi một API được gọi.

<p align="center">
    <img src="./photo/document01.png" width=800 />
</p>
<h3 align="center">

***Hình ảnh các API được khai báo trong tệp tin routes.inc.php***
</h3>

Giả sử, mình lấy ví dụ một dòng cho dễ hiểu nha 😅

> App::addRoute( "GET|POST", "/api/doctors", "Doctors");

Trong này, cấu trúc mặc định câu lệnh là 

> App::addRoute( "các phương thức hỗ trợ", "tên đường dẫn", "Controller sẽ xử lý yêu cầu");

Vậy thì với ví dụ trên thì 

- `GET|POST` là các phương thức hỗ trợ

- `/api/doctors` là tên đường dẫn của API. Ví dụ như: GET - http://192.168.1.221:8080/PTIT-Do-An-Tot-Nghiep/api/doctors sẽ là một yêu cầu hợp lệ

- `Doctors` là controller xử lý yêu cầu này.

## [**3. Code**](#3-code)

Các mình viết hàm xử lý là đồng nhất và xuyên suốt toàn bộ các controller nên mình sẽ mô tả tóm gọn 
như sau:

<p align="center">
    <img src="./photo/document02.png" width=800 />
</p>
<h3 align="center">

***Cấu trúc mặc định của một Controller***
</h3>
Từ hình minh họa bên trên, chúng ta có thể hiểu được cấu trúc một Controller trong đồ án này. 

Hàm `process` đóng vai trò như một Contructor của Controller này. Mọi yêu cầu khi được gọi tới 
`Patient Profile Controller` thì hàm `process` này luôn luôn chạy đầu tiên.

Nhờ vào quy ước đặc biệt này, chúng ta sẽ tiến hành điều hướng tới các hàm xử lý bên dưới.

<p align="center">
    <img src="./photo/document03.png" width=800 />
</p>
<h3 align="center">

***Dòng 34 lấy ra giá trị Action - giá trị này dùng để gọi tới hàm xử lý tương ứng bên dưới***
</h3>

Rất đơn giản phải không ?😎😋. Để lấy tên phương thức được gọi tới chúng ta dùng
hàm `Input::method()`. Nếu muốn lấy giá trị được gửi lên API này. 
Trong hình dòng 34, muốn lấy giá trị **action** thì ta gọi 

> Input::post("action")

Trong đó: 

- **Input** là tên của class chứa phương thức 

- **post** là tên phương thức POST được gọi tới 

- **action** là key của giá trị được gửi lên 

Ví dụ: nếu bạn gửi một biến với key là password lên server với phương thức PUT 
thì câu lệnh để lấy được giá trị sẽ là 

> $password = Input::put("password")


# [**Document**](#document)

Phần này mình sẽ mô tả chi tiết từng API, header cần có những gì, đối số truyền vào là gì và kết quả trả về.

Trong API mình có sử dụng chức năng Variable của POSTMAN để tiết kiệm thời gian viết code. Tên & ý nghĩa của chúng như sau:

| Tên                   | Chức năng                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|
| ENDPOINT_URL          | Tên đường dẫn chung của đồ án - http://192.168.1.221:8080/PTIT-Do-An-Tot-Nghiep   |
| ACCESS_TOKEN          | JWT token của bác sĩ với vai trò ADMIN                                            |
| ACCESS_TOKEN_MEMBER   | JWT token của bác sĩ với vai trò MEMBER                                           |
| ACCESS_TOKEN_SUPPORTER| JWT token của bác sĩ với vai trò SUPPORTER                                        |
| ACCESS_TOKEN_PATIENT  | JWT token của bệnh nhân                                                           |

## [**1. Authentication**](#1-authentication)

Mục đích chung là phục vụ chức năng đăng nhập & xác thực danh tính người dùng. Bất kì ai cũng có thể sử dụng API này.

<p align="center">
    <img src="./photo/document04.png" />
</p>
<h3 align="center">

***Các API trong mục Authentication***

</h3>

### [**🟡 1.1. Login Patient**](#11-login-patient)

- **Purpose**: Xử lý yêu cầu đăng nhập của bệnh nhân từ Android gửi tới.

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/login

- **Headers**: bỏ trống

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Type                  | Bắt buộc | chỉ đích danh đối tưởng đang đăng nhập là Bệnh nhân. Điều này giúp phân biệt với yêu cầu đăng nhập từ bác sĩ. Nếu `type = null` thì yêu cầu đăng nhập là từ bác sĩ.                                                          |
    | Email                 | Bắt buộc | Email đăng ký tài khoản                                                            |
    | Password              | Bắt buộc | Mật khẩu tài khoản                                                                 |

- **Respone**:

<p align="center">
    <img src="./photo/document05.png"/>
</p>
<h3 align="center">

### [**🟡 1.2. Login Doctor**](#12-login-doctor)

- **Purpose**: Xử lý yêu cầu đăng nhập của bác sĩ 

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/login

- **Headers**: bỏ trống

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Type                  | Bắt buộc | chỉ đích danh đối tưởng đang đăng nhập là Bệnh nhân. Điều này giúp phân biệt với yêu cầu đăng nhập từ bác sĩ. Nếu `type = null` thì yêu cầu đăng nhập là từ bác sĩ.                                                          |
    | Email                 | Bắt buộc | Email đăng ký tài khoản                                                            |
    | Password              | Bắt buộc | Mật khẩu tài khoản                                                                 |

- **Respone**:

<p align="center">
    <img src="./photo/document06.png"/>
</p>
<h3 align="center">

### [**🟡 1.3. Sign Up**](#13-sign-up)

- **Purpose**: đăng ký tài khoản mới

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/signup

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Email                 | Bắt buộc | Email đăng ký tài khoản                                                           |
    | Phone                 | Bắt buộc | Số điện thoại liên lạc                                                            |
    | Password              | Bắt buộc | Mật khẩu tài khoản        |
    | Password-confirm      | Bắt buộc | Mật khẩu xác nhận         |
    | Name                  | Bắt buộc | Họ tên đầy đủ của bác sĩ  |
    | Description           | Tùy chọn | Mô tả về quá trình công tác  |
    | Price                 | Tùy chọn | Chi phí đặt lịch khám bệnh  |
    | Role                  | Tùy chọn | Quyền truy cập của bác sĩ này. Có 3 quyền chính: admin, member & supporter  |
    | Avatar                | Tùy chọn | Ảnh đại diện  |

- **Respone**:
  
<p align="center">
    <img src="./photo/document07.png"/>
</p>

- **Email**:

<p align="center">
    <img src="../photo/image1.png"/>
</p>

### [**🟡 1.4. Recovery**](#14-recovery)

- **Purpose**: Gửi email để lấy mã xác thực nhằm khôi phục mật khẩu

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/recovery

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Email                 | Bắt buộc | Email đăng ký tài khoản                                                           |

- **Respone**:

<p align="center">
    <img src="./photo/document08.png"/>
</p>

### [**🟡 1.5. Password Reset**](#15-password-reset)

- **Purpose**: Đặt lại mật khẩu mới với mã xác thực nhận từ Email

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/password-reset/12

> 12 là ID của tài khoản

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Recovery Token        | Bắt buộc | Mã xác thực để đặt lại mật khẩu                                          |
    | Password              | Bắt buộc | Mật khẩu mới                                                             |
    | PasswordConfirm        | Bắt buộc | Mật khẩu xác thực lại                                                   |

- **Respone**:

<p align="center">
    <img src="./photo/document09.png"/>
</p>

## [**2. Patients**](#2-patients)

Đây là các API dành cho bác sĩ phải có vai trò ADMIN mới có quyền sử dụng

### [**🟢 2.1. Read All**](#21-read-all)

- **Purpose**: Đọc thông tin của tất cả bệnh nhân

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/patients

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authorization         | ACCESS_TOKEN                                                              |
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**:
  
- **Params**:

    | Tên                   |  Ý nghĩa                                                                          |
    |-----------------------|-----------------------------------------------------------------------------------|
    |search                |Từ khóa tìm kiếm                                                                  |           
    |order[dir]            |Chiều sắp xếp kết quả. Nhận 2 giá trị asc(tăng dần) & desc(giảm dần)              |
    |order[column]         |Cột được sử dụng để sắp xếp kết quả. Mặc định là ID                               |
    |length                |Số lượng kết quả trả về. Mặc định là không giới hạn                               |
    |start                 |Kết quả tìm kiếm bắt đầu từ vị trí thứ mấy. Ví dụ nhập 1 thì kết quả đầu tiên bị bỏ qua| 
- **Respone**:

<p align="center">
    <img src="./photo/document10.png"/>
</p>

### [**🟢 2.2. Read By ID**](#22-read-all)

- **Purpose**: Đọc thông tin của một bệnh nhân cụ thể

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/patients/1

> 1 là ID của bệnh nhân

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authorization         | ACCESS_TOKEN                                                              |
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**: bỏ trống 

- **Respone**:

<p align="center">
    <img src="./photo/document11.png" />
</p>

### [**🔵 2.3. Update**](#23-read-all)

- **Purpose**: Cập nhật thông tin của một bệnh nhân

- **Permission**: ADMIN

- **Method**: 🔵 **PUT**

- **URL**: {{ENDPOINT_URL}}/api/patients/1

> 1 là ID của bệnh nhân

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authorization         | ACCESS_TOKEN                                                              |
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Name        |Bắt buộc  |Họ tên bệnh nhân                                           |
    |Phone       |Bắt buộc  |Số điện thoại                                              |
    |Birthday    |Bắt buộc  |Ngày sinh                                                  |
    |Gender      |Bắt buộc  |Giới tính. Có 2 giá trị được chấp nhận: 0 là nữ & 1 là nam |
    |Address     |Tùy chọn  |Địa chỉ                                                    |

- **Respone**:

<p align="center">
    <img src="./photo/document12.png"/>
</p>

### [**🟡 2.4. Delete**](#24-read-all)

- **Purpose**: Xóa một người bệnh. Tuy nhiên, xóa thông tin của bệnh nhân là điều không nên làm bởi chúng ta có thể
đem thông tin của bệnh nhân để bán cho các bên khác có nhu cầu sử dụng.

- **Permission**: ADMIN

- **Method**: 🔴 **DELETE**
> 1 là ID của bệnh nhân

- **URL**: {{ENDPOINT_URL}}/api/patients/1

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authorization         | ACCESS_TOKEN                                                              |
    |Content-Type          | application/x-www-form-urlencoded                                         |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document13.png" />
</p>

## [**3. Patient Profile**](#3-patient-profile)

Mục đích chung là giúp bệnh nhân cập nhật thông tin cá nhân, thay đổi hình đại diện và thay đổi mật khẩu.
Không có chức năng khôi phục mật khẩu vì bệnh nhân sẽ đăng nhập bằng 1 trong 2 cách sau:

1. Đăng nhập bằng số điện thoại với mã OTP.

2. Đăng nhập bằng tài khoản Google.

<p align="center">
    <img src="./photo/document14.png" />
</p>

<h3 align="center">

***Các API trong mục Patient Profile***

</h3>

### [**🟢 3.1. Read Personal Information**](#31-read-personal-information)

- **Purpose**: Giúp bệnh nhân xem thông tin cá nhân của mình 

- **Permission**: PATIENT

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/patient/profile

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Type                  |Patient                                                                    |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document15.png" />
</p>

### [**🟡 3.2. Change Personal Information**](#32-change-personal-information)

- **Purpose**: Hỗ trợ bệnh nhân cập nhật thông tin cá nhân

- **Permission**: PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/patient/profile

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Action                 |Bắt buộc  |Thể hiện yêu cầu gửi tới api này làm gì. Có 3 trạng thái hợp lệ: personal, password & avatar. API sử dụng **PERSONAL**|
    |Name                   |Bắt buộc  |Họ tên bệnh nhân                                                                   |
    |Gender                 |Tùy chọn  |Giới tính. Có 2 giá trị: 0 là nữ & 1 là nam                                        |
    |Birthday               |Bắt buộc  |Ngày tháng năm sinh bệnh nhân                                                      |
    |Address                |Bắt buộc  |Địa chỉ bệnh nhân                                                                  |

- **Respone**:

<p align="center">
    <img src="./photo/document16.png" />
</p>

### [**🟡 3.3. Change Avatar**](#33-change-avatar)

- **Purpose**: Hỗ trợ bệnh nhân cập nhật ảnh đại diện

- **Permission**: PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/patient/profile

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Action                 |Bắt buộc  |Thể hiện yêu cầu gửi tới api này làm gì. Có 3 trạng thái hợp lệ: personal, password & avatar. API sử dụng **AVATAR**|
    |File                   |Bắt buộc  |Ảnh đại diện mà người dùng muốn đăng lên                                           |

- **Respone**:

<p align="center">
    <img src="./photo/document17.png" />
</p>

### [**🟡 3.4. Change Password**](#34-change-password)

- **Purpose**: Hỗ trợ bệnh nhân thay đổi mật khẩu

- **Permission**: PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/patient/profile

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Action                 |Bắt buộc  |Thể hiện yêu cầu gửi tới api này làm gì. Có 3 trạng thái hợp lệ: personal, password & avatar. API sử dụng **PASSWORD**|
    |Current Password       |Bắt buộc  |Mật khẩu hiện tại                                                                  |
    |New Password           |Bắt buộc  |Mật khẩu mới                                                                       |
    |Confirm Password       |Bắt buộc  |Mật khẩu xác nhận                                                                  |

- **Respone**:


<p align="center">
    <img src="./photo/document18.png" />
</p>

## [**4. Patient Booking**](#4-patient-booking)

Mục đích chính là chức năng đặt lịch khám bệnh cho bệnh nhân

### [**🟢 4.1. Read All**](#41-read-all)

- **Purpose**: Hỗ trợ bệnh nhân xem lại lịch sử lịch hẹn của mình

- **Permission**: PATIENT

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/patient/booking

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**: bỏ trống

- **Params**:

    | Tên                   |  Ý nghĩa                                                                          |
    |-----------------------|-----------------------------------------------------------------------------------|
    |search                |Từ khóa tìm kiếm                                                                    |           
    |order[dir]            |Chiều sắp xếp kết quả. Nhận 2 giá trị asc(tăng dần) & desc(giảm dần)                |
    |order[column]         |Cột được sử dụng để sắp xếp kết quả. Mặc định là ID                                 |
    |length                |Số lượng kết quả trả về. Mặc định là không giới hạn                                 |
    |start                 |Kết quả tìm kiếm bắt đầu từ vị trí thứ mấy. Ví dụ nhập 1 thì kết quả đầu tiên bị bỏ qua| 

- **Respone**:

<p align="center">
    <img src="./photo/document19.png" />
</p>

### [**🟢 4.2. Read By ID**](#42-read-by-id)

- **Purpose**: Xem chi tiết một lịch hẹn khám bệnh 

- **Permission**: PATIENT

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/patient/booking/19

> 19 là ID của lịch hẹn

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document20.png" />
</p>

### [**🟡 4.3. Create**](#43-create)

- **Purpose**: Hỗ trợ bệnh nhân tạo mới một lịch hẹn khám bệnh

- **Permission**: PATIENT

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/patient/booking

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Service_id             |Bắt buộc  |ID của loại dịch vụ mà lịch hẹn đăng ký                                            |
    |Booking_name           |Bắt buộc  |Họ tên người đặt lịch hẹn khám bệnh                                                |
    |Booking_phone          |Bắt buộc  |Số điện thoại người đặt lịch hẹn khám bệnh                                         |
    |Name                   |Bắt buộc  |Họ tên bệnh nhân                                                                   |
    |Gender                 |Tùy chọn  |Giới tính bệnh nhân                                                                |
    |Birthday               |Tùy chọn  |Ngày sinh bệnh nhân                                                                |
    |Address                |Tùy chọn  |Địa chỉ bệnh nhân                                                                  |
    |Reason                 |Tùy chọn  |Lý do khám bệnh, mô tả triệu chứng                                                 |
    |Appointment Time       |Bắt buộc  |Thời gian hẹn khám                                                                 |
    |Status                 |Tùy chọn  |Trạng thái lịch hẹn. Có 3 trạng thái hợp lệ: processing, verified, cancel. Mặc định lịch hẹn của bệnh nhân là **PROCESSING**|
    |Create At              |Tùy chọn  |Thời gian tạo ra ra lịch hẹn. Thông tin này do hệ thống tự động tạo                |
    |Update At              |Tùy chọn  |Thời gian lần cập nhật gần nhất của lịch hẹn. Thông tin này do hệ thống tự động tạo|

- **Respone**:

<p align="center">
    <img src="./photo/document21.png" />
</p>

### [**🔴 4.4. Cancel**](#44-cancel)

- **Purpose**: Hỗ trợ bệnh nhân hủy bỏ lịch hẹn đã tạo trước đó

- **Permission**: PATIENT

- **Method**: 🔴 **DELETE**

- **URL**: {{ENDPOINT_URL}}/api/patient/booking/19

> 19 là ID của lịch hẹn

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN_PATIENT}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |
    |Type                  |Patient                                                                    |

- **Body**: bỏ trống

- **Respone**:

Nếu lịch hẹn này đã **ở trạng thái HỦY BỎ**

<p align="center">
    <img src="./photo/document22.png" />
</p>

Nếu lịch hẹn này đang **ở trạng thái ĐANG XỬ LÝ**

<p align="center">
    <img src="./photo/document23.png" />
</p>



## [**5. Doctors**](#5-doctor)

Mục đích là để quản lý thông tin của các bác sĩ.

### [**🟢 5.1. Read All**](#51-read-all)

- **Purpose**: Xem danh sách bác sĩ với các điều kiện lọc khi cần thiết

- **Method**: 🟢 **GET**

- **Permission**: ADMIN - SUPPORTER - DOCTOR

- **URL**: {{ENDPOINT_URL}}/api/doctors/

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Params**:

    | Tên                   |  Ý nghĩa                                                                          |
    |-----------------------|-----------------------------------------------------------------------------------|
    |search                |Từ khóa tìm kiếm                                                                    |           
    |order[dir]            |Chiều sắp xếp kết quả. Nhận 2 giá trị asc(tăng dần) & desc(giảm dần)                |
    |order[column]         |Cột được sử dụng để sắp xếp kết quả. Mặc định là ID                                 |
    |length                |Số lượng kết quả trả về. Mặc định là không giới hạn                                 |
    |start                 |Kết quả tìm kiếm bắt đầu từ vị trí thứ mấy. Ví dụ nhập 1 thì kết quả đầu tiên bị bỏ qua|
    |room_id               |Mã phòng khám mà bác sĩ làm việc                                                    |
    |speciality_id         |Mã chuyên khoa của bác sĩ                                                           |
    |active                |Trạng thái tài khoản: 0 là vô hiệu hóa và 1 là đang hoạt động                       |

- **Respone**:

<p align="center">
    <img src="./photo/document24.png" />
</p>

<p align="center">
    <img src="./photo/document25.png" />
</p>

### [**🟢 5.2. Read By ID**](#52-read-by-id)

- **Purpose**: Xem thông tin một bác sĩ

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/doctors/19

> 19 là ID của bác sĩ

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document26.png" />
</p>

### [**🟡 5.3. Create**](#53-create)

- **Purpose**: Tạo tài khoản cho một bác sĩ với mật khẩu là ngẫu nhiên và được gửi tới email
được dùng để đăng kí tài khoản

- **Permission**: ADMIN

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/doctors

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Email                 | Bắt buộc | Email đăng ký tài khoản                                                           |
    | Phone                 | Bắt buộc | Số điện thoại liên lạc                                                            |
    | Name                  | Bắt buộc | Họ tên đầy đủ của bác sĩ                                                          |
    | Description           | Tùy chọn | Mô tả về quá trình công tác                                                       |     
    | Price                 | Tùy chọn | Chi phí đặt lịch khám bệnh                                                        |
    | Role                  | Bắt buộc | Quyền truy cập của bác sĩ này. Có 3 quyền chính: admin, member & supporter        |
    | Speciality_id         | Tùy chọn | Mã chuyên khoa                                                                    |
    | Room_id               | Bắt buộc | Mã phòng nơi bác sĩ sẽ làm việc                                                   |

- **Respone**:

<p align="center">
    <img src="./photo/document28.png" />
</p>

### [**🔵 5.4. Update**](#54-update)

- **Purpose**: Cập nhật thông tin cá nhân của bác sĩ

- **Permission**: ADMIN

- **Method**: 🔵 **PUT**

- **URL**: {{ENDPOINT_URL}}/api/doctors/1

> 1 là ID của bác sĩ

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Phone                 | Bắt buộc | Số điện thoại liên lạc                                                            |
    | Name                  | Bắt buộc | Họ tên đầy đủ của bác sĩ                                                          |
    | Description           | Tùy chọn | Mô tả về quá trình công tác                                                       |     
    | Price                 | Tùy chọn | Chi phí đặt lịch khám bệnh                                                        |
    | Role                  | Bắt buộc | Quyền truy cập của bác sĩ này. Có 3 quyền chính: admin, member & supporter        |
    | Speciality_id         | Tùy chọn | Mã chuyên khoa                                                                    |
    | Room_id               | Tùy chọn | Mã phòng nơi bác sĩ sẽ làm việc                                                   |

- **Respone**:

<p align="center">
    <img src="./photo/document29.png" />
</p>

### [**🔴 5.5. Delete**](#55-delete)

- **Purpose**: Xóa bác sĩ

- **Permission**: ADMIN

- **Method**: 🔴 **DELETE**

- **URL**: {{ENDPOINT_URL}}/api/doctors/1

> 1 là ID của bác sĩ

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
- **Respone**:

Trường hợp 1 - bác sĩ bị xóa hoàn toàn do không có dữ liệu gì trong cơ sở dữ liệu

<p align="center">
    <img src="./photo/document30.png" />
</p>

Trường hợp 2 - bác sĩ bị vô hiệu hóa do đã có các dữ liệu khác tồn tại như THỨ TỰ KHÁM,
 PHÁC ĐỒ ĐIỀU TRỊ hoặc BỆNH ÁN

 <p align="center">
    <img src="./photo/document31.png" />
</p>


### [**🟡 5.6. Update Avatar**](#56-update-avatar)

- **Purpose**: Xóa bác sĩ

- **Permission**: ADMIN

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/doctors/1

> 1 là ID của bác sĩ

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Action                |avatar - trường này dùng để phân biệt với yêu cầu cập nhật thông tin cá nhân|
    |File                  |ảnh đại diện được sử dụng                                         |
  
- **Respone**:

<p align="center">
    <img src="./photo/document32.png" />
</p>


## [**6. Doctor Profile**](#6-doctors)

Mục đích giúp bác sĩ cập nhật ảnh đại diện & thông tin cá nhân của mình.

### [**🟢 6.1. Read Personal Information**](#61-read-personal-information)

- **Purpose**: Giúp bác sĩ xem thông tin cá nhân của mình 

- **Permission**: ADMIN - SUPPORTER - MEMBER

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/doctor/profile

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document33.png" />
</p>


### [**🟡 6.2. Change Personal Information**](#62-change-personal-information)

- **Purpose**: Bác sĩ tự cập nhật thông tin cá nhân

- **Permission**: ADMIN - SUPPORTER - MEMBER

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/doctor/profile

- **Headers**: 

    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Action                 |Bắt buộc  |Thể hiện yêu cầu gửi tới api này làm gì. Có 3 trạng thái hợp lệ: personal, password & avatar. API sử dụng **PERSONAL**|
    |Name                   |Bắt buộc  |Họ tên bệnh nhân                                                                   |
    |Phone                  |Bắt buộc  |Số điện thoại                                                                      |
    |Description            |Tùy chọn  |Mô tả bản thân                                                                     |

- **Respone**:

<p align="center">
    <img src="./photo/document34.png" />
</p>


### [**🟡 6.3. Change Avatar**](#63-change-avatar)

- **Purpose**: Hỗ trợ bác sĩ cập nhật ảnh đại diện

- **Permission**: ADMIN - SUPPORTER - MEMBER

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/doctor/profile

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Action                 |Bắt buộc  |Thể hiện yêu cầu gửi tới api này làm gì. Có 3 trạng thái hợp lệ: personal, password & avatar. API sử dụng **AVATAR**|
    |File                   |Bắt buộc  |Ảnh đại diện mà người dùng muốn đăng lên                                           |

- **Respone**:

<p align="center">
    <img src="./photo/document35.png" />
</p>

### [**🟡 6.4. Change Password**](#64-change-password)

- **Purpose**: Hỗ trợ bác sĩ thay đổi mật khẩu

- **Permission**: ADMIN - SUPPORTER - MEMBER

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/doctor/profile

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    |Action                 |Bắt buộc  |Thể hiện yêu cầu gửi tới api này làm gì. Có 3 trạng thái hợp lệ: personal, password & avatar. API sử dụng **PASSWORD**|
    |Current Password       |Bắt buộc  |Mật khẩu hiện tại                                                                  |
    |New Password           |Bắt buộc  |Mật khẩu mới                                                                       |
    |Confirm Password       |Bắt buộc  |Mật khẩu xác nhận                                                                  |

- **Respone**:

<p align="center">
    <img src="./photo/document36.png" />
</p>


## [**7. Speciality**](#7-speciality)

Mục đính để quản lý các chuyên khoa của bác sĩ

### [**🟢 7.1. Read All**](#71-read-all)

- **Purpose**: Xem danh sách các chuyên khoa

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **Permission**: ADMIN - SUPPORTER - DOCTOR

- **URL**: {{ENDPOINT_URL}}/api/specialities/

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Params**:

    | Tên                   |  Ý nghĩa                                                                          |
    |-----------------------|-----------------------------------------------------------------------------------|
    |search                |Từ khóa tìm kiếm                                                                    |           
    |order[dir]            |Chiều sắp xếp kết quả. Nhận 2 giá trị asc(tăng dần) & desc(giảm dần)                |
    |order[column]         |Cột được sử dụng để sắp xếp kết quả. Mặc định là ID                                 |
    |length                |Số lượng kết quả trả về. Mặc định là không giới hạn                                 |
    |start                 |Kết quả tìm kiếm bắt đầu từ vị trí thứ mấy. Ví dụ nhập 1 thì kết quả đầu tiên bị bỏ qua|

- **Respone**:

<p align="center">
    <img src="./photo/document37.png" />
</p>

### [**🟢 7.2. Read By ID**](#72-read-by-id)

- **Purpose**: Xem thông tin một chuyên khoa

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/specialities/19

> 19 là ID của chuyên khoa

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document38.png" />
</p>

### [**🟡 7.3. Create**](#73-create)

- **Purpose**: Tạo mới chuyên khoa

- **Permission**: ADMIN

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/specialites

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Name                  | Bắt buộc | Tên chuyên khoa                                                                   |
    | Description           | Bắt buộc | Mô tả                                                                             |     

- **Respone**:

<p align="center">
    <img src="./photo/document39.png" />
</p>


### [**🔵 7.4. Update**](#74-update)

- **Purpose**: Cập nhật thông tin chuyên khoa

- **Permission**: ADMIN

- **Method**: 🔵 **PUT**

- **URL**: {{ENDPOINT_URL}}/api/specialites/10

10 là id của chuyên khoa

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Name                  | Bắt buộc | Tên chuyên khoa                                                                   |
    | Description           | Bắc buộc | Mô tả                                                                             |     

- **Respone**:

<p align="center">
    <img src="./photo/document40.png" />
</p>

### [**🔴 7.5. Delete**](#75-delete)

- **Purpose**: Xóa chuyên khoa. Nếu có bác sĩ đang thuộc chuyên khoa bị xóa thì sẽ hiển thị thông báo

- **Permission**: ADMIN

- **Method**: 🔴 **DELETE**

- **URL**: {{ENDPOINT_URL}}/api/specialites/10

10 là id của chuyên khoa

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: 

- **Respone**:

Trường hợp 1 - chuyên khoa tồn tại bác sĩ đang làm việc

<p align="center">
    <img src="./photo/document41.png" />
</p>

Trường hợp 2 - chuyên khoa không tồn tại bác sĩ nào

<p align="center">
    <img src="./photo/document42.png" />
</p>

## [**8. Services**](#8-service)

Mục đích để quản lý các dịch vụ mà bệnh nhân sẽ lựa chọn để đặt lịch khám.

### [**🟢 8.1. Read All**](#81-read-all)

- **Purpose**: Xem danh sách các dịch vụ

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/services/

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Params**:

    | Tên                   |  Ý nghĩa                                                                          |
    |-----------------------|-----------------------------------------------------------------------------------|
    |search                |Từ khóa tìm kiếm                                                                    |           
    |order[dir]            |Chiều sắp xếp kết quả. Nhận 2 giá trị asc(tăng dần) & desc(giảm dần)                |
    |order[column]         |Cột được sử dụng để sắp xếp kết quả. Mặc định là ID                                 |
    |length                |Số lượng kết quả trả về. Mặc định là không giới hạn                                 |
    |start                 |Kết quả tìm kiếm bắt đầu từ vị trí thứ mấy. Ví dụ nhập 1 thì kết quả đầu tiên bị bỏ qua|

- **Respone**:

<p align="center">
    <img src="./photo/document43.png" />
</p>

### [**🟢 8.2. Read By ID**](#82-read-by-id)

- **Purpose**: Xem thông tin một dịch vụ

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/services/19

> 19 là ID của dịch vụ

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document44.png" />
</p>

### [**🟡 8.3. Create**](#83-create)

- **Purpose**: Tạo mới dịch vụ. Nếu tên này đã được sử dụng sẽ hiển thị ra thông báo.

- **Permission**: ADMIN

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/services

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Name                  | Bắt buộc | Tên dịch vụ                                                                       |     

- **Respone**:

<p align="center">
    <img src="./photo/document45.png" />
</p>


### [**🔵 8.4. Update**](#84-update)

- **Purpose**: Cập nhật thông tin dịch vụ. Nếu tên này đã được sử dụng sẽ hiển thị ra thông báo.

- **Permission**: ADMIN

- **Method**: 🔵 **PUT**

- **URL**: {{ENDPOINT_URL}}/api/services/10

> 10 là ID của dịch vụ

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Name                  | Bắt buộc | Tên dịch vụ                                                                       |     

- **Respone**:

<p align="center">
    <img src="./photo/document46.png" />
</p>

### [**🔴 8.5. Delete**](#85-delete)

- **Purpose**: Xóa dịch vụ

- **Permission**: ADMIN

- **Method**: 🔴 **DELETE**

- **URL**: {{ENDPOINT_URL}}/api/services/10

10 là id của chuyên khoa

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: 

- **Respone**:

<p align="center">
    <img src="./photo/document47.png" />
</p>

## [**9. Rooms**](#9-room)

Mục đích để quản lý các dịch vụ mà bệnh nhân sẽ lựa chọn để đặt lịch khám.

### [**🟢 9.1. Read All**](#91-read-all)

- **Purpose**: Xem danh sách phòng khám nơi mà bác sĩ đang làm việc

- **Permission**: ADMIN - SUPPORTER - MEMBER - PATIENT

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/rooms/

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Params**:

    | Tên                   |  Ý nghĩa                                                                          |
    |-----------------------|-----------------------------------------------------------------------------------|
    |search                |Từ khóa tìm kiếm                                                                    |           
    |order[dir]            |Chiều sắp xếp kết quả. Nhận 2 giá trị asc(tăng dần) & desc(giảm dần)                |
    |order[column]         |Cột được sử dụng để sắp xếp kết quả. Mặc định là ID                                 |
    |length                |Số lượng kết quả trả về. Mặc định là không giới hạn                                 |
    |start                 |Kết quả tìm kiếm bắt đầu từ vị trí thứ mấy. Ví dụ nhập 1 thì kết quả đầu tiên bị bỏ qua|

- **Respone**:

<p align="center">
    <img src="./photo/document48.png" />
</p>

### [**🟢 9.2. Read By ID**](#92-read-by-id)

- **Purpose**: Xem thông tin một phòng khám cụ thể

- **Permission**: ADMIN

- **Method**: 🟢 **GET**

- **URL**: {{ENDPOINT_URL}}/api/rooms/19

> 19 là ID của phòng khám

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: bỏ trống

- **Respone**:

<p align="center">
    <img src="./photo/document49.png" />
</p>

### [**🟡 9.3. Create**](#93-create)

- **Purpose**: Tạo mới phòng khám. Nếu tên này đã được sử dụng sẽ hiển thị ra thông báo.

- **Permission**: ADMIN

- **Method**: 🟡 **POST**

- **URL**: {{ENDPOINT_URL}}/api/rooms

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Name                  | Bắt buộc | Tên phòng khám                                                                    |     
    | Location              | Bắt buộc | Vị trí phòng khám                                                                 |        

- **Respone**:

<p align="center">
    <img src="./photo/document49.png" />
</p>


### [**🔵 9.4. Update**](#94-update)

- **Purpose**: Cập nhật phòng khám

- **Permission**: ADMIN

- **Method**: 🔵 **PUT**

- **URL**: {{ENDPOINT_URL}}/api/rooms/10

> 10 là ID của phòng khám

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                           |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**:
  
    | Tên                   | Tùy chọn | Ý nghĩa                                                                           |
    |-----------------------|----------|-----------------------------------------------------------------------------------|
    | Name                  | Bắt buộc | Tên phòng khám                                                                       |   
    | Location              | Bắt buộc | Vị trí phòng khám                                                                 |       

- **Respone**:

<p align="center">
    <img src="./photo/document51.png" />
</p>

### [**🔴 9.5. Delete**](#95-delete)

- **Purpose**: Xóa phòng khám

- **Permission**: ADMIN

- **Method**: 🔴 **DELETE**

- **URL**: {{ENDPOINT_URL}}/api/rooms/10

10 là id của phòng khám

- **Headers**:
   
    | Tên                  | Giá Trị                                                                   |
    |----------------------|---------------------------------------------------------------------------|
    |Authentication        |{{ACCESS_TOKEN}}                                                   |
    |Content-Type          |application/x-www-form-urlencoded                                          |

- **Body**: 

- **Respone**:

Trường hợp đặc biệt: có bác sĩ đang làm việc ở phòng khám

<p align="center">
    <img src="./photo/document52.png" />
</p>