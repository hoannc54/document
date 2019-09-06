1. Không code trực tiếp hàm `env()` trong code, mà phải dùng thông qua config

Config:
Thêm biến config theo nguyên tắc:
- Gom nhóm config theo nguyên tắc tree đi từ ngoài vào trong
- Tên biến env theo nguyên tắc là ký tự in hoa từ tên file đến tên biến trong config
Ví dụ: 
'name' => env('APP_NAME', 'CungHocVui'), trong file app.php

=> Đặt tên APP_NAME

## Naming conventions 

(Cách đặt tên file, tên class, tên biến trong Laravel)

### Quy tắc chung

 * Không bao giờ đặt tên Tiếng Việt

### Controllers
* PHẢI bắt đầu là danh từ số ít
* Không có khoảng trắng ở giữa, viết kiểu lạc đà, mỗi từ nên viết hoa chữ cái đầu tiên
* Kết thúc chữ "Controller"
Ví dụ: `BlogController, AuthController, UserController`

### Models

* PHẢI là danh từ số ít đúng chuẩn tiếng Anh, để tự động map tên Model với tên table
* Viết hoa chữ cái đầu tiên của từ

#### Model properties
* Viết chữ thường dạng snake_case (rắn)
* Trùng với tên tronng table nếu có

#### Model method
* Sử dụng camelCase, nhưng viết thường chữ đầu tiên

#### Relationships
##### hasOne or belongsTo relationship (one to many)
* PHẢI là danh từ số ít
* Tên hàm theo chuẩn bình thường

##### hasMany, belongsToMany, hasManyThrough (one to many)
* PHẢI là danh từ số nhiều : `public function comments(), public function roles()`



### Routes 
* Là danh từ số nhiều 
    - `Route::get('/users', 'UserController@index');`
    - `Route::resource('photos', 'PhotoController');`
* Viết thường

#### Name routes 
* Sử dụng dạng snake_case 
* Dùng dấu chấm phân cách giữa các phần

### Views
#### Tên file: 
* Sử dụng dạng snake_case

* Không thực hiện logic trong file view

### Migrate
#### Migrations
Tên file theo dạng sau :
- Create table: `yyyy_mm_dd_<timestamp>_create_<table name>_table`
- Add, change, ... column: 
    `yyyy_mm_dd_<timestamp>_<action_name>_<column_name>_<table name>_table`




# Tham khảo 

* https://webdevetc.com/blog/laravel-naming-conventions
* https://www.laravelbestpractices.com
