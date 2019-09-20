# Danh mục

[Quy tắc về chuẩn đặt tên]()

[Quy tắc trong khi code]()

[Các quy tắc khác]()

## Quy tắc về chuẩn đặt tên

(Cách đặt tên file, tên class, tên biến trong Laravel)

### Quy tắc chung
* Không bao giờ đặt tên Tiếng Việt
### Configuration
* Thêm biến config theo nguyên tắc:

* Gom nhóm config theo nguyên tắc tree đi từ ngoài vào trong
* Tên biến env theo nguyên tắc là ký tự in hoa từ tên file đến tên biến trong config
Ví dụ: 
'name' => env('APP_NAME', 'CungHocVui'), trong file app.php

=> Đặt tên APP_NAME
#### Đặt tên file config theo dạng snake_case
Good: 
`config/my_config.php`

Bad: 
`config/MyConfig.php`

#### Cấu hình các key trong file config ở dạng snake_case
Good: 
```
// config/my_config.php
return [
    'my_api' => [
        'domain' => env('API_DOMAIN'),
        'secret' => env('API_SECRET'),
    ],
```
Bad: 
```
// config/my_config.php
return [
    'MyApi' => [
        'DOMAIN' => env('API_DOMAIN'),
        'SECRET' => env('API_SECRET'),
    ],
```
 
### Controllers

* PHẢI bắt đầu là danh từ số ít
* Không có khoảng trắng ở giữa, viết kiểu lạc đà, mỗi từ nên viết hoa chữ cái đầu tiên
* Kết thúc chữ "Controller"

**Good:**
```
class ArticleController extends Controller
{
```

**Bad:**
```
class ArticlesController extends Controller
{
```

```
class wp_articlesController extends Controller
{
```

```
class Article extends Controller
{
```

* Nên sử dụng các hàm trong Resource Controllers trong các trường hợp tương ứng, chỉ sử dụng hàm khác khi không tương ứng

**Good**
```
class DomainController extends Controller
{
    public function index(){} // list domains
    public function create(){} // show create form
    public function store(Request $request){ } // handle the form POST 
    public function show($id){} // show a single domain
    public function edit($id){} // show edit page
    public function update(Request $request, $id){} // handle show edit page POST
    public function destroy($id){} // delete a domain
}
```

**Bad**
```
class DomainController extends Controller
{
    public function list(){} // list domains
    public function create_or_save(){} // show create form then handle save
    public function show_edit($id){} // show a single domain then show edit page
    public function delete($id){} // delete a domain
}
```

### Models

* PHẢI là danh từ số ít đúng chuẩn tiếng Anh, để tự động map tên Model với tên table
* Viết hoa chữ cái đầu tiên của từ

**Good**
```
class Flight extends Model
{
...
```

**Bad**
```
class Flights extends Model
{
...
```

```
class flight extends Model
{
...
```

#### Model properties
* Viết chữ thường dạng snake_case (rắn)
* Trùng với tên tronng table nếu có

**Good**
```
$user->created_at
```
**Bad**
```
$user->createdAt
```
#### Model method
* Sử dụng camelCase, nhưng viết thường chữ đầu tiên

**Good**
```
class User extends Model
{
    public function scopePopular($query)
    {
        return $query->where('votes', '>', 100);
    }
```
**Bad**
```
class User extends Model
{
    public function scope_popular($query)
    {
        return $query->where('votes', '>', 100);
    }
```

#### Relationships
##### hasOne or belongsTo relationship (one to many)
* PHẢI là danh từ số ít
* Tên hàm theo chuẩn bình thường

**Good**
```
class User extends Model
{
    public function phone()
    {
        return $this->hasOne('App\Phone');
    }
}
```

**Bad**
```
class User extends Model
{
    public function phones()
    {
        return $this->hasOne('App\Phone');
    }
}
```
##### hasMany, belongsToMany, hasManyThrough (one to many)
* PHẢI là danh từ số nhiều : `public function comments(), public function roles()`

**Good**
```
class Post extends Model
{
    public function comments()
    {
        return $this->hasMany('App\Comment');
    }
}
```

**Bad**
```
class Post extends Model
{
    public function comment()
    {
        return $this->hasMany('App\Comment');
    }
}
```

### Functions (Helpers)
* Đặt trong thư mục app, không để ngoài thư mục project
**Good**
```
project_folder/app/helper.php
project_folder/app/Http/helper.php
```
**Bad**
```
project_folder/functions.php
```

* Sử dụng composer để autoload hàm trong helpers

**Good**
```
// file composer.json
...
"autoload": {
    "files": [
        "app/helpers.php"
    ],
...
```
**Bad**
```
// file app/Http/Controllers/HomeController.php

class HomeController.php
{
    function index(){
        require_once(app_path("helpers.php"));
    }
}
```

* Phải check tồn tại hàm

**Good**
```
if (! function_exists('my_custom_helper')) {
    function my_custom_helper($key, $default = null) {
        // ...
    }
}
```
**Bad**
```
function my_custom_helper($key, $default = null) {
    // ...
}
```
### Routes 

**Uri trong Route**
* Là danh từ số nhiều 
* Viết thường

**Good**
```
Route::get('/users', 'UserController@index');
Route::resource('photos', 'PhotoController');
```
**Bad**
```
Route::get('/user', 'UserController@index');
Route::get('/UsersList', 'UserController@index');
Route::resource('PHOTO', 'PhotoController');
```

**Name routes**

* Sử dụng dạng snake_case 
* Dùng dấu chấm phân cách giữa các phần

**Good**
```
Route::get('/user', 'UserController@active')->name('users.show_active');
```
**Bad**
```
Route::get('/user', 'UserController@active')->name('users.show-active');
Route::get('/user', 'UserController@active')->name('show-active-users');
```

### Variables
* Tên biến để dạng  camelCase

**Good**
```
$articlesWithAuthor
```
**Bad**
```
$articles_with_author
```
* Tên biến mô tả ý nghĩa của biến và ở dạng số nhiều hoặc số ít tương ứng 

**Good**
```
$activeUsers = User::active()->get();
$activeUser = User::active()->first();
```
**Bad**
```
$users = User::active()->get();
$user = User::active()->get();
$User = User::active()->get();
//
$users = User::active()->first();
```
### Views

**Tên file:** 

* Sử dụng dạng snake_case

**Good**
```
show_filtered.blade.php
```
**Bad**
```
showFiltered.blade.php
show-filtered.blade.php
```


**Cấu trúc thư mục**

Tổ chức thư mục phân cấp rõ ràng cho từng thành phần bên trong

```
views/
-- frontend
---- layouts
---- home
------ index.blade.php
---- posts
------- index.blade.php
------- show.blade.php
--- backend
```
### Migrate
* Đặt tên file migrations tương đương với file logs để khi đọc lại hiểu rõ ý nghĩa của file
- Create table: 
```
yyyy_mm_dd_<timestamp>_create_<table name>_table
```
- Add, change, ... column: 
```
yyyy_mm_dd_<timestamp>_<action_name>_<column_name>_<table name>_table
```

**Good**
```
2019_06_06_164210_create_domains_table.php
```
**Bad**
```
2019_06_06_164210_domains.php
```
* Tên bảng viết thường và ở dạng số nhiều

**Good**
```
class CreateFlightsTable extends Migration
{
    public function up()
    {
        Schema::create('flights', function (Blueprint $table) {
```

**Bad**
```
class CreateFlightsTable extends Migration
{
    public function up()
    {
        Schema::create('flight', function (Blueprint $table) {
```

```
class CreateUsersTable extends Migration
{
    public function up()
    {
        Schema::create('MyUsers', function (Blueprint $table) {
```

* Tên các bảng nối ở dạng số ít và sắp xếp theo thứ tự bảng chữ cái

**Good**
```
post_user
articles_user
photo_post
```

**Bad**
```
posts_users
user_articles
post_photos
```

* Tên cột ở dạng snake_case và không chứa tên bảng hoặc model

**Good**

```
username
title
thumb_url
```
**Bad**

```
UserName
_title
ThumbUrl
post_title
```

* Các thay đổi về cột hoặc về bảng trong cơ sở dữ liệu 

**Good**

Phải sử dụng migration để ghi các thay đổi và chạy `php artisan migrate` để thay đổi 

**Bad**

* Sử dụng phpMyAdmin để sửa trực tiếp các thay đổi 
* Import các file sql mẫu để lấy thay đổi

### Tổng kết

What | How | Good | Bad
------------ | ------------- | ------------- | -------------
Controller | singular | ArticleController | ~~ArticlesController~~
Route | plural | articles/1 | ~~article/1~~
Named route | snake_case with dot notation | users.show_active | ~~users.show-active, show-active-users~~
Model | singular | User | ~~Users~~
hasOne or belongsTo relationship | singular | articleComment | ~~articleComments, article_comment~~
All other relationships | plural | articleComments | ~~articleComment, article_comments~~
Table | plural | article_comments | ~~article_comment, articleComments~~
Pivot table | singular model names in alphabetical order | article_user | ~~user_article, articles_users~~
Table column | snake_case without model name | meta_title | ~~MetaTitle; article_meta_title~~
Model property | snake_case | $model->created_at | ~~$model->createdAt~~
Foreign key | singular model name with _id suffix | article_id | ~~ArticleId, id_article, articles_id~~
Primary key | - | id | ~~custom_id~~
Migration | - | 2017_01_01_000000_create_articles_table | ~~2017_01_01_000000_articles~~
Method | camelCase | getAll | ~~get_all~~
Method in resource controller | [table](https://laravel.com/docs/master/controllers#resource-controllers) | store | ~~saveArticle~~
Method in test class | camelCase | testGuestCannotSeeArticle | ~~test_guest_cannot_see_article~~
Variable | camelCase | $articlesWithAuthor | ~~$articles_with_author~~
Collection | descriptive, plural | $activeUsers = User::active()->get() | ~~$active, $data~~
Object | descriptive, singular | $activeUser = User::active()->first() | ~~$users, $obj~~
Config and language files index | snake_case | articles_enabled | ~~ArticlesEnabled; articles-enabled~~
View | snake_case | show_filtered.blade.php | ~~showFiltered.blade.php, show-filtered.blade.php~~
Config | snake_case | google_calendar.php | ~~googleCalendar.php, google-calendar.php~~
Contract (interface) | adjective or noun | Authenticatable | ~~AuthenticationInterface, IAuthentication~~
Trait | adjective | Notifiable | ~~NotificationTrait~~

## Quy tắc trong khi code
### Không lấy dữ liệu trực tiếp hàm `env()` trong code, mà phải dùng thông qua hàm `config()`

**Good**
```
// config/api.php
'key' => env('API_KEY'),

// Use the data
$apiKey = config('api.key');
```
**Bad**
```
$apiKey = env('API_KEY');
```

### Không thực hiện logic hoặc cách hành động không liên quan đến giao diện trong file view

**Good**
```
// $api_results is passed by controller
<ul>  
    @foreach($api_results as $result)
        <li>{{ $result->name }}</li>
    @endforeach
</ul>
```
**Bad**
```
@php
   $api_results = json_decode(file_get_contents("https://api.example.com"));
@endphp
<ul>
    @foreach($api_results as $result)
        <li>{{ $result->name }}</li>
    @endforeach
</ul>
```

### Validation
Không đặt validation trong controllers mà ta sẽ để trong class Request

**Bad**
```
public function store(Request $request)
{
    $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
        'publish_at' => 'nullable|date',
    ]);

    ....
}
```
**Good**
```
public function store(PostRequest $request)
{    
    ....
}

class PostRequest extends Request
{
    public function rules()
    {
        return [
            'title' => 'required|unique:posts|max:255',
            'body' => 'required',
            'publish_at' => 'nullable|date',
        ];
    }
}
```

### Đặt tất cả logic của DB trong Eloquent Models hoặc Repository nếu sử dụng query Builder hoặc raw SQL

**Good**
```
public function index()
{
    return view('index', ['clients' => $this->client->getWithNewOrders()]);
}

class Client extends Model
{
    public function getWithNewOrders()
    {
        return $this->verified()
            ->with(['orders' => function ($q) {
                $q->where('created_at', '>', Carbon::today()->subWeek());
            }])
            ->get();
    }
}
```
**Bad**
```
public function index()
{
    $clients = Client::verified()
        ->with(['orders' => function ($q) {
            $q->where('created_at', '>', Carbon::today()->subWeek());
        }])
        ->get();

    return view('index', ['clients' => $clients]);
}
```


## Quy tắc khác 
### Sử dụng cú pháp ngắn hơn khi có thể 
Bad:

```php
$request->session()->get('cart');
$request->input('name');
```

Good:

```php
session('cart');
$request->name;
```

Common syntax | Shorter and more readable syntax
------------ | -------------
`Session::get('cart')` | `session('cart')`
`$request->session()->get('cart')` | `session('cart')`
`Session::put('cart', $data)` | `session(['cart' => $data])`
`$request->input('name'), Request::get('name')` | `$request->name, request('name')`
`return Redirect::back()` | `return back()`
`is_null($object->relation) ? null : $object->relation->id` | `optional($object->relation)->id`
`return view('index')->with('title', $title)->with('client', $client)` | `return view('index', compact('title', 'client'))`
`$request->has('value') ? $request->value : 'default';` | `$request->get('value', 'default')`
`Carbon::now(), Carbon::today()` | `now(), today()`
`App::make('Class')` | `app('Class')`
`->where('column', '=', 1)` | `->where('column', 1)`
`->orderBy('created_at', 'desc')` | `->latest()`
`->orderBy('age', 'desc')` | `->latest('age')`
`->orderBy('created_at', 'asc')` | `->oldest()`
`->select('id', 'name')->get()` | `->get(['id', 'name'])`
`->first()->name` | `->value('name')`

### Don't repeat yourself (DRY)
Hãy tái sử dụng code khi có thể. 

Bad:

```php
public function getActive()
{
    return $this->where('verified', 1)->whereNotNull('deleted_at')->get();
}

public function getArticles()
{
    return $this->whereHas('user', function ($q) {
            $q->where('verified', 1)->whereNotNull('deleted_at');
        })->get();
}
```

Good:

```php
public function scopeActive($q)
{
    return $q->where('verified', 1)->whereNotNull('deleted_at');
}

public function getActive()
{
    return $this->active()->get();
}

public function getArticles()
{
    return $this->whereHas('user', function ($q) {
            $q->active();
        })->get();
}
```
### Business logic nên để trong các class 

Bad
```php
public function store(Request $request)
{
    if ($request->hasFile('image')) {
        $request->file('image')->move(public_path('images') . 'temp');
    }
    
    ....
}
```

Good
```php
public function store(Request $request)
{
    $this->articleService->handleUploadedImage($request->file('image'));

    ....
}

class ArticleService
{
    public function handleUploadedImage($image)
    {
        if (!is_null($image)) {
            $image->move(public_path('images') . 'temp');
        }
    }
}
```

Lợi ích:
- Giúp các controller mỏng hơn về code
- Tái sử dụng code khi cùng logic đó được sử dụng ở nhiều nơi
- Dễ dàng maintain khi logic code thay đổi, chỉ cần sửa trong class Services
# Tham khảo 

* https://webdevetc.com/blog/laravel-naming-conventions
* https://www.laravelbestpractices.com
* https://github.com/alexeymezenin/laravel-best-practices
* https://chungnguyen.xyz/posts/code-laravel-lam-sao-cho-chuan
