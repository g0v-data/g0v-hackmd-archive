以下是以 Laravel 框架實作討論區專案的關鍵程式碼與說明：

---

## 一、資料庫設計與遷移
```php
// database/migrations/xxxx_create_users_table.php
Schema::create('users', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->string('email')->unique();
    $table->string('password');
    $table->string('avatar')->nullable();
    $table->enum('role', ['admin', 'forum_admin', 'user'])->default('user');
    $table->text('bio')->nullable();
    $table->timestamps();
});

// database/migrations/xxxx_create_forums_table.php
Schema::create('forums', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->text('description');
    $table->timestamps();
});

// database/migrations/xxxx_create_posts_table.php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->text('content');
    $table->foreignId('forum_id')->constrained();
    $table->foreignId('user_id')->constrained();
    $table->string('image')->nullable();
    $table->timestamps();
});
```

**關聯說明**：
- `User` 與 `Post`: 一對多 (`hasMany()`)
- `Forum` 與 `Post`: 一對多 (`hasMany()`)
- `Post` 與 `User/Forum`: 反向關聯 (`belongsTo()`)

---

## 二、模型與關聯
```php
// app/Models/User.php
class User extends Authenticatable
{
    public function posts()
    {
        return $this->hasMany(Post::class);
    }
}

// app/Models/Forum.php
class Forum extends Model
{
    public function posts()
    {
        return $this->hasMany(Post::class);
    }
}

// app/Models/Post.php
class Post extends Model
{
    public function user()
    {
        return $this->belongsTo(User::class);
    }

    public function forum()
    {
        return $this->belongsTo(Forum::class);
    }
}
```

---

## 三、中介層權限檢查
```php
// app/Http/Middleware/CheckAdmin.php
public function handle($request, Closure $next)
{
    if (!auth()->check() || !in_array(auth()->user()->role, ['admin', 'forum_admin'])) {
        return redirect('/')->with('error', '權限不足');
    }
    return $next($request);
}
```

註冊中介層：
```php
// app/Http/Kernel.php
protected $routeMiddleware = [
    'admin' => \App\Http\Middleware\CheckAdmin::class,
];
```

---

## 四、控制器邏輯範例
### 會員註冊 (使用 Laravel Breeze 擴充)
```php
// app/Http/Controllers/Auth/RegisteredUserController.php
protected function validator(array $data)
{
    return Validator::make($data, [
        'name' => ['required', 'string', 'max:255'],
        'email' => ['required', 'string', 'email', 'max:255', 'unique:users'],
        'password' => ['required', 'string', 'min:8', 'confirmed'],
    ]);
}
```

### 文章發表邏輯
```php
// app/Http/Controllers/PostController.php
public function store(Request $request)
{
    $validated = $request->validate([
        'title' => 'required|max:255',
        'content' => 'required',
        'forum_id' => 'required|exists:forums,id',
        'image' => 'nullable|image|mimes:jpeg,png,jpg,gif|max:2048'
    ]);

    if ($request->hasFile('image')) {
        $path = $request->file('image')->store('posts', 'public');
        $validated['image'] = $path;
    }

    $post = auth()->user()->posts()->create($validated);

    return redirect()->route('posts.show', $post);
}
```

---

## 五、路由設定
```php
// routes/web.php
// 會員功能
Route::middleware('guest')->group(function () {
    Route::get('register', [RegisteredUserController::class, 'create']);
    Route::post('register', [RegisteredUserController::class, 'store']);
    // 登入路由...
});

// 文章功能
Route::resource('posts', PostController::class)->except(['index']);

// 管理後台路由組
Route::middleware(['auth', 'admin'])->prefix('admin')->group(function () {
    Route::resource('forums', ForumAdminController::class);
});
```

---

## 六、Blade 模板範例
### 文章列表分頁
```php
// resources/views/posts/index.blade.php
@foreach ($posts as $post)
    <div class="post">
        <h2>{{ $post->title }}</h2>
        <p>{{ Str::limit($post->content, 100) }}</p>
    </div>
@endforeach

{{ $posts->links() }} // 分頁連結
```

### 圖片上傳表單
```html
<form method="POST" enctype="multipart/form-data">
    @csrf
    <input type="file" name="image">
    <!-- 其他表單欄位 -->
</form>
```

---

## 七、圖片儲存設定
```php
// config/filesystems.php
'disks' => [
    'public' => [
        'driver' => 'local',
        'root' => storage_path('app/public'),
        'url' => env('APP_URL').'/storage',
        'visibility' => 'public',
    ],
]
```

執行指令建立符號連結：
```bash
php artisan storage:link
```

---

## 補充說明
1. 權限系統可透過 Policy 進一步細化控制
2. 圖片上傳建議使用雲端儲存服務（如 S3）時需修改 filesystems 設定
3. 前端樣式可使用 Tailwind CSS 或 Bootstrap 快速搭建
4. API 開發可使用 Laravel Sanctum 進行認證

以上程式碼展示了主要功能模組的實作方式，實際開發時需根據需求補充驗證邏輯、錯誤處理與安全性措施。