以下提供一個使用 Laravel (假設版本 8 以上) 所建立的「網路討論區」基礎範例程式碼，包含前端頁面(Blade)、後端程式(Controllers + Models)、以及資料庫(Migrations) 設計，並附上相關說明。此範例僅示範核心功能與程式架構，實際專案可再根據需求進行細部調整或增加更多功能。

一、資料庫 Migrations

1. 建立 users 資料表

Laravel 預設會在 database/migrations/2014_10_12_000000_create_users_table.php 裡建立 users 資料表，可自行修改或新增欄位。為了符合需求，我們需要以下欄位：
	•	name (會員名稱)
	•	email (會員帳號)
	•	password (會員密碼)
	•	role (會員權限：admin, moderator, user)
	•	avatar (會員圖片路徑)
	•	introduction (會員自我介紹)

可以在原有 migration 的基礎上進行調整，例如：

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateUsersTable extends Migration
{
    public function up()
    {
        Schema::create('users', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->string('password');
            $table->enum('role', ['admin', 'moderator', 'user'])->default('user');
            $table->string('avatar')->nullable();
            $table->text('introduction')->nullable();
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('users');
    }
}

2. 建立 forums 資料表

用於儲存各種討論區(例如：技術討論、閒聊區、公告區等)。可以在 database/migrations 目錄下建立新的 migration：2023_01_01_000000_create_forums_table.php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateForumsTable extends Migration
{
    public function up()
    {
        Schema::create('forums', function (Blueprint $table) {
            $table->id();
            $table->string('name'); // 討論區名稱
            $table->text('description')->nullable(); // 討論區描述
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('forums');
    }
}

3. 建立 posts 資料表

用於儲存各討論區中的文章。可以在 database/migrations 目錄下建立新的 migration：2023_01_01_000001_create_posts_table.php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreatePostsTable extends Migration
{
    public function up()
    {
        Schema::create('posts', function (Blueprint $table) {
            $table->id();
            $table->unsignedBigInteger('forum_id'); // 所屬討論區
            $table->unsignedBigInteger('user_id');  // 發文者
            $table->string('title'); // 文章標題
            $table->text('content'); // 文章內容
            $table->timestamps();

            // Foreign key constraints
            $table->foreign('forum_id')->references('id')->on('forums')->onDelete('cascade');
            $table->foreign('user_id')->references('id')->on('users')->onDelete('cascade');
        });
    }

    public function down()
    {
        Schema::dropIfExists('posts');
    }
}

二、Models

1. User Model

位於 app/Models/User.php (Laravel 8 以上版本是 App\Models\User; 若較舊版本則是在 App\User)。此處可放入與 users 資料表相關的欄位與關聯。

namespace App\Models;

use Illuminate\Contracts\Auth\MustVerifyEmail;
use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Foundation\Auth\User as Authenticatable;
use Illuminate\Notifications\Notifiable;

class User extends Authenticatable
{
    use HasFactory, Notifiable;

    protected $fillable = [
        'name',
        'email',
        'password',
        'role',
        'avatar',
        'introduction',
    ];

    protected $hidden = [
        'password',
        'remember_token',
    ];

    public function posts()
    {
        return $this->hasMany(Post::class);
    }
    
    // 判斷是否為網站管理員
    public function isAdmin()
    {
        return $this->role === 'admin';
    }

    // 判斷是否為討論區管理員
    public function isModerator()
    {
        return $this->role === 'moderator';
    }
}

2. Forum Model

位於 app/Models/Forum.php。此處可放入與 forums 資料表相關的欄位與關聯。

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Forum extends Model
{
    use HasFactory;

    protected $fillable = [
        'name',
        'description',
    ];

    public function posts()
    {
        return $this->hasMany(Post::class);
    }
}

3. Post Model

位於 app/Models/Post.php。此處可放入與 posts 資料表相關的欄位與關聯。

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Post extends Model
{
    use HasFactory;

    protected $fillable = [
        'forum_id',
        'user_id',
        'title',
        'content',
    ];

    public function forum()
    {
        return $this->belongsTo(Forum::class);
    }

    public function user()
    {
        return $this->belongsTo(User::class);
    }
}

三、Controllers

此處示範主要的功能 Controller，包括會員功能、討論區管理與文章管理。
另外可利用 Laravel 內建的 Auth scaffolding / Laravel Breeze / Laravel Jetstream 等方案加快開發，以下僅示範自訂程式碼核心架構。

1. Auth 相關 Controller

若使用 Laravel Breeze 或原生的 Auth scaffolding，可以省去手動撰寫的繁瑣。這裡示範自訂簡易的 AuthController。

	注意：實務上要確保密碼加密、驗證邏輯安全，以及處理信箱驗證等。這裡為簡化示範，不包含信箱驗證等完整邏輯。

app/Http/Controllers/AuthController.php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;
use Illuminate\Support\Facades\Hash;
use App\Models\User;

class AuthController extends Controller
{
    // 顯示註冊表單
    public function showRegisterForm()
    {
        return view('auth.register');
    }

    // 處理註冊請求
    public function register(Request $request)
    {
        // 驗證表單資料
        $request->validate([
            'name' => 'required|string|max:255',
            'email' => 'required|email|unique:users',
            'password' => 'required|string|min:6|confirmed',
        ]);

        // 建立使用者
        User::create([
            'name' => $request->name,
            'email' => $request->email,
            'password' => Hash::make($request->password),
        ]);

        return redirect()->route('login')->with('success', '註冊成功，請登入！');
    }

    // 顯示登入表單
    public function showLoginForm()
    {
        return view('auth.login');
    }

    // 處理登入請求
    public function login(Request $request)
    {
        // 驗證表單資料
        $request->validate([
            'email' => 'required|email',
            'password' => 'required|min:6',
        ]);

        // 嘗試登入
        if (Auth::attempt($request->only('email', 'password'))) {
            return redirect()->route('home')->with('success', '登入成功！');
        }

        return back()->withErrors(['email' => '帳號或密碼錯誤']);
    }

    // 處理登出
    public function logout()
    {
        Auth::logout();
        return redirect()->route('login')->with('success', '您已登出');
    }
}

2. User Profile 相關 Controller

app/Http/Controllers/UserController.php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;
use Illuminate\Support\Facades\Hash;

class UserController extends Controller
{
    // 會員中心頁
    public function profile()
    {
        $user = Auth::user();
        return view('user.profile', compact('user'));
    }

    // 編輯會員資料表單
    public function edit()
    {
        $user = Auth::user();
        return view('user.edit', compact('user'));
    }

    // 更新會員資料
    public function update(Request $request)
    {
        $user = Auth::user();

        // 驗證資料
        $request->validate([
            'name' => 'required|string|max:255',
            'introduction' => 'nullable|string',
            // 如果要改密碼就驗證，也可另外放到獨立方法
            // 'password' => 'nullable|string|min:6|confirmed',
            'avatar' => 'nullable|image|mimes:jpeg,png,jpg,gif|max:2048'
        ]);

        // 更新基本欄位
        $user->name = $request->name;
        $user->introduction = $request->introduction;

        // 如果有上傳大頭照
        if ($request->hasFile('avatar')) {
            $file = $request->file('avatar');
            $path = $file->store('avatars', 'public'); 
            $user->avatar = $path;
        }

        // 如果要改密碼
        // if ($request->filled('password')) {
        //     $user->password = Hash::make($request->password);
        // }

        $user->save();

        return redirect()->route('user.profile')->with('success', '會員資料已更新！');
    }
}

3. Forum 及 Post 相關 Controller

app/Http/Controllers/ForumController.php

namespace App\Http\Controllers;

use App\Models\Forum;
use Illuminate\Http\Request;

class ForumController extends Controller
{
    // 討論區列表
    public function index()
    {
        // 可以加上分頁或顯示方式
        $forums = Forum::all();
        return view('forums.index', compact('forums'));
    }

    // 顯示單一討論區下的文章列表
    public function show($id)
    {
        $forum = Forum::findOrFail($id);
        // 這裡文章分頁一次 20 筆
        $posts = $forum->posts()->orderBy('created_at','desc')->paginate(20);
        return view('forums.show', compact('forum', 'posts'));
    }
}

app/Http/Controllers/PostController.php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;
use App\Models\Post;
use App\Models\Forum;

class PostController extends Controller
{
    // 顯示單篇文章
    public function show($postId)
    {
        $post = Post::with('forum')->findOrFail($postId);
        return view('posts.show', compact('post'));
    }

    // 顯示建立文章表單
    public function create($forumId)
    {
        $forum = Forum::findOrFail($forumId);
        return view('posts.create', compact('forum'));
    }

    // 儲存新文章
    public function store(Request $request, $forumId)
    {
        $forum = Forum::findOrFail($forumId);

        // 驗證資料
        $request->validate([
            'title' => 'required|string|max:255',
            'content' => 'required',
        ]);

        $post = new Post();
        $post->forum_id = $forum->id;
        $post->user_id = Auth::id();
        $post->title = $request->title;
        $post->content = $request->content;
        $post->save();

        return redirect()->route('forums.show', $forum->id)->with('success', '文章已建立！');
    }

    // 顯示編輯文章表單
    public function edit($postId)
    {
        $post = Post::findOrFail($postId);
        // 只有作者本人或管理員才可編輯
        if (Auth::id() !== $post->user_id && !Auth::user()->isAdmin() && !Auth::user()->isModerator()) {
            abort(403, '您無權編輯此文章');
        }

        return view('posts.edit', compact('post'));
    }

    // 更新文章
    public function update(Request $request, $postId)
    {
        $post = Post::findOrFail($postId);

        if (Auth::id() !== $post->user_id && !Auth::user()->isAdmin() && !Auth::user()->isModerator()) {
            abort(403, '您無權編輯此文章');
        }

        $request->validate([
            'title' => 'required|string|max:255',
            'content' => 'required',
        ]);

        $post->title = $request->title;
        $post->content = $request->content;
        $post->save();

        return redirect()->route('posts.show', $post->id)->with('success', '文章已更新！');
    }
}

四、Routes 設定

在 routes/web.php 中設定所需路由。此處示範基本路由，實際可再調整命名或合併群組 Middleware 等。

use Illuminate\Support\Facades\Route;
use App\Http\Controllers\AuthController;
use App\Http\Controllers\UserController;
use App\Http\Controllers\ForumController;
use App\Http\Controllers\PostController;

// 首頁(可改成顯示討論區列表等)
Route::get('/', function () {
    return redirect()->route('forums.index');
})->name('home');

// 註冊、登入、登出
Route::get('/register', [AuthController::class, 'showRegisterForm'])->name('register');
Route::post('/register', [AuthController::class, 'register'])->name('register.post');
Route::get('/login', [AuthController::class, 'showLoginForm'])->name('login');
Route::post('/login', [AuthController::class, 'login'])->name('login.post');
Route::post('/logout', [AuthController::class, 'logout'])->name('logout');

// 會員中心(需登入)
Route::middleware('auth')->group(function () {
    Route::get('/user/profile', [UserController::class, 'profile'])->name('user.profile');
    Route::get('/user/edit', [UserController::class, 'edit'])->name('user.edit');
    Route::post('/user/update', [UserController::class, 'update'])->name('user.update');
});

// 討論區列表 & 顯示討論區文章列表
Route::get('/forums', [ForumController::class, 'index'])->name('forums.index');
Route::get('/forums/{id}', [ForumController::class, 'show'])->name('forums.show');

// 文章相關
Route::middleware('auth')->group(function () {
    // 在指定討論區建立文章
    Route::get('/forums/{forumId}/posts/create', [PostController::class, 'create'])->name('posts.create');
    Route::post('/forums/{forumId}/posts', [PostController::class, 'store'])->name('posts.store');

    // 編輯文章
    Route::get('/posts/{postId}/edit', [PostController::class, 'edit'])->name('posts.edit');
    Route::post('/posts/{postId}/update', [PostController::class, 'update'])->name('posts.update');
});

// 文章瀏覽
Route::get('/posts/{postId}', [PostController::class, 'show'])->name('posts.show');

五、Blade 前端頁面(範例)

以下僅示範核心頁面，可依需求增加樣式或使用前端框架(例如 Bootstrap, Tailwind CSS)美化。

1. resources/views/layouts/app.blade.php

一個簡易的主樣板，包含導覽列區域及可放置訊息顯示、主要內容區塊。

<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>我的討論區</title>
    <!-- 可以放 Bootstrap 或其他 CSS -->
</head>
<body>
    <nav>
        <a href="{{ route('home') }}">首頁</a>

        @guest
            <a href="{{ route('login') }}">登入</a>
            <a href="{{ route('register') }}">註冊</a>
        @else
            <a href="{{ route('user.profile') }}">{{ Auth::user()->name }}的會員中心</a>
            <form action="{{ route('logout') }}" method="POST" style="display:inline;">
                @csrf
                <button type="submit">登出</button>
            </form>
        @endguest
    </nav>

    <hr>
    @if(session('success'))
        <div style="color: green;">{{ session('success') }}</div>
    @endif
    @if($errors->any())
        <div style="color: red;">
            <ul>
                @foreach ($errors->all() as $error)
                    <li>{{ $error }}</li>
                @endforeach
            </ul>
        </div>
    @endif

    <div class="container">
        @yield('content')
    </div>

    <!-- 可放置 JS -->
</body>
</html>

2. 註冊頁 resources/views/auth/register.blade.php

@extends('layouts.app')

@section('content')
<h1>會員註冊</h1>
<form action="{{ route('register.post') }}" method="POST">
    @csrf
    <div>
        <label for="name">姓名：</label>
        <input type="text" name="name" id="name" value="{{ old('name') }}">
    </div>
    <div>
        <label for="email">信箱：</label>
        <input type="email" name="email" id="email" value="{{ old('email') }}">
    </div>
    <div>
        <label for="password">密碼：</label>
        <input type="password" name="password" id="password">
    </div>
    <div>
        <label for="password_confirmation">確認密碼：</label>
        <input type="password" name="password_confirmation" id="password_confirmation">
    </div>
    <button type="submit">註冊</button>
</form>
@endsection

3. 登入頁 resources/views/auth/login.blade.php

@extends('layouts.app')

@section('content')
<h1>會員登入</h1>
<form action="{{ route('login.post') }}" method="POST">
    @csrf
    <div>
        <label for="email">信箱：</label>
        <input type="email" name="email" id="email" value="{{ old('email') }}">
    </div>
    <div>
        <label for="password">密碼：</label>
        <input type="password" name="password" id="password">
    </div>
    <button type="submit">登入</button>
</form>
@endsection

4. 會員中心頁 resources/views/user/profile.blade.php

@extends('layouts.app')

@section('content')
<h2>會員中心</h2>
<div>
    <p>帳號：{{ $user->email }}</p>
    <p>會員名稱：{{ $user->name }}</p>
    <p>會員權限：{{ $user->role }}</p>
    <p>自我介紹：{{ $user->introduction }}</p>
    @if($user->avatar)
        <p>會員圖片：<img src="{{ asset('storage/'.$user->avatar) }}" alt="avatar" style="max-width:100px;"></p>
    @else
        <p>尚未上傳大頭照</p>
    @endif
</div>
<a href="{{ route('user.edit') }}">編輯資料</a>
@endsection

5. 會員資料修改頁 resources/views/user/edit.blade.php

@extends('layouts.app')

@section('content')
<h2>編輯會員資料</h2>
<form action="{{ route('user.update') }}" method="POST" enctype="multipart/form-data">
    @csrf
    <div>
        <label for="name">會員名稱：</label>
        <input type="text" name="name" value="{{ old('name', $user->name) }}">
    </div>
    <div>
        <label for="introduction">自我介紹：</label>
        <textarea name="introduction" id="introduction">{{ old('introduction', $user->introduction) }}</textarea>
    </div>
    <div>
        <label for="avatar">會員圖片：</label>
        <input type="file" name="avatar" id="avatar">
    </div>
    <!-- 如果要改密碼
    <div>
        <label for="password">新密碼：</label>
        <input type="password" name="password" id="password">
    </div>
    <div>
        <label for="password_confirmation">確認密碼：</label>
        <input type="password" name="password_confirmation" id="password_confirmation">
    </div>
    -->
    <button type="submit">更新資料</button>
</form>
@endsection

6. 討論區列表頁 resources/views/forums/index.blade.php

@extends('layouts.app')

@section('content')
<h1>討論區列表</h1>
<ul>
@foreach($forums as $forum)
    <li>
        <a href="{{ route('forums.show', $forum->id) }}">{{ $forum->name }}</a>
        @if($forum->description)
            - {{ $forum->description }}
        @endif
    </li>
@endforeach
</ul>
@endsection

7. 個別討論區文章列表頁 resources/views/forums/show.blade.php

@extends('layouts.app')

@section('content')
<h1>{{ $forum->name }}</h1>
<p>{{ $forum->description }}</p>

@auth
    <a href="{{ route('posts.create', $forum->id) }}">發表新文章</a>
@endauth

<hr>
<h2>文章列表</h2>
<ul>
@foreach($posts as $post)
    <li>
        <a href="{{ route('posts.show', $post->id) }}">{{ $post->title }}</a>
        <small>by {{ $post->user->name }} at {{ $post->created_at }}</small>
    </li>
@endforeach
</ul>

{{-- 分頁元件 --}}
{{ $posts->links() }}
@endsection

8. 文章內容頁 resources/views/posts/show.blade.php

@extends('layouts.app')

@section('content')
<h1>{{ $post->title }}</h1>
<p>{!! nl2br(e($post->content)) !!}</p>
<p>發表於 {{ $post->created_at }} by {{ $post->user->name }}</p>

@auth
    @if(Auth::id() === $post->user_id || Auth::user()->isAdmin() || Auth::user()->isModerator())
        <a href="{{ route('posts.edit', $post->id) }}">編輯文章</a>
    @endif
@endauth

<p><a href="{{ route('forums.show', $post->forum->id) }}">回到討論區</a></p>
@endsection

9. 文章編輯/新增頁 resources/views/posts/create.blade.php / resources/views/posts/edit.blade.php

(此處以建立文章頁為例，可依需求拆成兩個檔案)

建立文章 create.blade.php

@extends('layouts.app')

@section('content')
<h2>發表新文章於：{{ $forum->name }}</h2>
<form action="{{ route('posts.store', $forum->id) }}" method="POST">
    @csrf
    <div>
        <label for="title">標題：</label>
        <input type="text" name="title" id="title" value="{{ old('title') }}">
    </div>
    <div>
        <label for="content">內容：</label>
        <textarea name="content" id="content">{{ old('content') }}</textarea>
    </div>
    <button type="submit">發表文章</button>
</form>
@endsection

編輯文章 edit.blade.php

@extends('layouts.app')

@section('content')
<h2>編輯文章</h2>
<form action="{{ route('posts.update', $post->id) }}" method="POST">
    @csrf
    <div>
        <label for="title">標題：</label>
        <input type="text" name="title" id="title" value="{{ old('title', $post->title) }}">
    </div>
    <div>
        <label for="content">內容：</label>
        <textarea name="content" id="content">{{ old('content', $post->content) }}</textarea>
    </div>
    <button type="submit">更新文章</button>
</form>
@endsection

	插入圖片功能：若要在文章內容中插入圖片，較常見的做法是使用富文本編輯器(例如 Trix、TinyMCE、CKEditor…)，再搭配上傳圖片 API。這裡僅示範純文字 textarea，如需富文本可在 Blade 中引入外部編輯器套件並實作圖片上傳邏輯。

六、程式碼相關說明
	1.	資料庫設計
	•	users：存放會員資料(名稱、信箱、密碼、角色、頭像、簡介等)
	•	forums：存放不同討論區(名稱、簡介等)，方便將文章歸類
	•	posts：每篇文章的標題、內容、發文者、所屬討論區等
	2.	Models
	•	User 與 Post 是一對多關係(一個使用者可發多篇文章)
	•	Forum 與 Post 也是一對多關係(一個討論區可包含多篇文章)
	3.	Controllers
	•	AuthController 負責註冊、登入、登出等功能
	•	UserController 負責會員資料管理 (顯示會員中心、編輯資料…)
	•	ForumController 負責各討論區列表、顯示該討論區所有文章
	•	PostController 則負責發表文章、查看文章、編輯文章等
	4.	Routes
	•	分成「公開路由」(首頁、討論區列表、文章顯示) 與「需登入路由」(發文、編輯文章、編輯會員資料…)
	•	透過 auth 中介層保護需要登入的功能
	5.	Blade 前端頁面
	•	使用主樣板 app.blade.php 做為所有頁面的共用骨架
	•	各功能頁(註冊、登入、列表、詳細頁…)各自建立 Blade 檔
	•	可以整合前端框架 (Bootstrap、Tailwind CSS) 使版面更美觀
	•	若需插入圖片，可使用富文本編輯器

以上為一個基礎的 Laravel 網路討論區程式範例。在實際開發中，需考量更多安全性(例如 CSRF、XSS、權限控制)、使用者體驗(前端編輯器、上傳檔案大小限制)、以及功能(會員管理後台、文章排序、關鍵字搜尋…)。若要將此應用上線，請確保資料庫設定、檔案上傳、憑證(SSL)等均正確設定並符合資安需求。希望這份範例能協助您快速上手並完成所需的討論區功能。祝開發順利！