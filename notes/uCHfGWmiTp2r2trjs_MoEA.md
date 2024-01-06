# EGS 新系統架構說明
## 使用工具

### PHP Laravel Framework
Laravel 是一個開源的 PHP 網頁應用程式框架，提供優雅且簡潔的語法來加速網頁開發

[官方文件](https://laravel.com/docs/10.x)

### Livewire
Livewire 是 Laravel 生態系統中的一個開源工具，可在不使用 JavaScript 的情況下，快速構建動態和互動性豐富的網頁應用程式

[官方文件](https://laravel-livewire.com/docs/2.x/quickstart)

### Laravel Livewire Forms
laravel-livewire-forms 是一個擴展 Livewire 的開源工具，專注於簡化表單處理，能夠更輕鬆地建立和管理複雜的表單功能

[官方文件](https://github.com/pkkbkraa/laravel-livewire-forms/blob/master/DOCS.md)

### Livewire PowerGrid
Livewire PowerGrid 是一個強大且靈活的開源工具，可快速建立可排序、篩選和分頁的動態資料表格，加速 Laravel Livewire 專案的開發

[官方文件](https://v4.livewire-powergrid.com/table/features-setup.html)

### Livewire Alert
Livewire Alert 是一個 Laravel Livewire 的擴展工具，方便地處理警示視窗和通知訊息的顯示，使得互動性的網頁應用程式開發更加便捷

[官方文件](https://github.com/jantinnerezo/livewire-alert)

### Laravel Modules With Livewire
Laravel Modules With Livewire 是一個整合 Laravel Modules 和 Livewire 的工具，協助更有效地組織和管理 Livewire 組件，讓專案更加模組化和可維護

[官方文件](https://docs.laravelmodules.com/v10/introduction)

### Laravel Permission
Laravel-permission 是一個用於 Laravel 框架的開源套件，提供簡單而強大的角色權限管理功能，協助在應用程式中實現細緻的訪問控制

[官方文件](https://spatie.be/docs/laravel-permission/v5/introduction)

## Laravel

### Laravel 的基本操作指令

1. **建立新的 Laravel 專案：**
   ```bash
   laravel new project-name
   ```

2. **建立新的 Controller：**
   ```bash
   php artisan make:controller MyController
   ```

3. **建立新的 Model：**
   ```bash
   php artisan make:model MyModel
   ```

4. **建立新的 Migration：**
   ```bash
   php artisan make:migration create_table_name
   ```
這個指令會在 database/migrations 目錄下建立一個新的 Migration 檔案，用於定義資料庫表格的結構和欄位。可以在這個檔案中使用 Laravel 的 Schema Builder 方法來定義資料庫表格

資料庫 Migration 是 Laravel 中管理資料庫結構變更的一個非常有用的工具，它可以讓您在多人開發的情況下，輕鬆地跟踪並應用資料庫結構的變更

5. **執行 Migration：**
   ```bash
   php artisan migrate
   ```

6. **建立新的 Seeder：**
   ```bash
   php artisan make:seeder MySeeder
   ```
Seeder 是 Laravel 中用於填充資料庫測試資料的工具。當需要在開發環境或測試環境中快速填充資料庫資料時，Seeder 提供了一個簡單的方式來實現這個需求

使用上述指令，可以建立一個新的 Seeder，並將其放置在 database/seeders 目錄下。Seeder 檔案中包含了填充資料的程式碼，可以在其中定義要填充的資料結構和資料內容

在建立了 Seeder 之後，可以使用 php artisan db:seed 指令來執行 Seeder，將指定的資料填充到資料庫中

Seeder 是 Laravel 中非常實用的功能，它讓您能夠輕鬆地填充測試資料，加快開發速度並確保應用程式在各種情況下運作正常。在測試和開發過程中，可以使用 Seeder 快速填充資料庫，並進行資料驗證和功能測試。這使得測試和開發變得更加高效和可靠

7. **執行 Seeder：**
   ```bash
   php artisan db:seed
   ```

8. **建立新的 Middleware：**
   ```bash
   php artisan make:middleware MyMiddleware
   ```
Middleware 是 Laravel 中處理 HTTP 請求的過濾器。可以使用 Middleware 來對進入應用程式的 HTTP 請求進行處理，例如驗證用戶身份、檢查權限、執行日誌紀錄等。

使用上述指令，可以建立一個新的 Middleware，並將其放置在 app/Http/Middleware 目錄下。Middleware 檔案中包含了處理請求的程式碼，可以在其中定義要進行的處理邏輯。

在建立了 Middleware 之後，需要將其註冊到應用程式的中介層（Middleware Stack）中。這樣，它將在指定的請求進入應用程式之前或之後執行，根據設定的順序來進行處理。

Middleware 是 Laravel 中非常強大且靈活的功能，它使得處理請求和應用程式中的共用邏輯變得更加簡單且可管理。可以使用 Middleware 來確保特定的請求遵循應用程式的安全和業務邏輯，同時減少重複程式碼和提高程式碼的可讀性和可維護性。

9. **建立新的 Livewire 組件：**
   ```bash
   php artisan make:livewire MyComponent
   ```

10. **建立新的 Test：**
    ```bash
    php artisan make:test MyTest
    ```

11. **啟動內建開發伺服器：**
    ```bash
    php artisan serve
    ```

12. **建立新的 Blade View：**
    ```bash
    php artisan make:view my-view
    ```


## Livewire 專案建立流程及說明

1. **建立新的 Model 和 Migration：**

   我們首先建立一個 `Post` Model 和相應的 Migration，用於儲存文章的資料。

   ```bash
   php artisan make:model Post -m
   ```

   上述指令將會建立 `Post` Model 和 `posts` 資料表的 Migration 檔案。

2. **編輯 Migration 檔案：**

   打開生成的 Migration 檔案 `database/migrations/xxxxxxxx_create_posts_table.php`，在 `up` 方法中定義資料表的欄位結構。

   ```php
   // database/migrations/xxxxxxxx_create_posts_table.php

   public function up()
   {
       Schema::create('posts', function (Blueprint $table) {
           $table->id();
           $table->string('title');
           $table->text('content');
           $table->timestamps();
       });
   }
   ```

   執行 Migration 來建立 `posts` 資料表：

   ```bash
   php artisan migrate
   ```

3. **建立新的 Livewire 組件：**

   建立一個 `Posts` Livewire 組件，用於顯示文章列表。

   ```bash
   php artisan make:livewire Posts
   ```

4. **編輯 Livewire 組件：**

   打開生成的 Livewire 組件檔案 `app/Http/Livewire/Posts.php`，在 `render` 方法中定義要顯示的資料。

   ```php
   // app/Http/Livewire/Posts.php

   namespace App\Http\Livewire;

   use Livewire\Component;
   use App\Models\Post;

   class Posts extends Component
   {
       public function render()
       {
           $posts = Post::all();
           return view('livewire.posts', compact('posts'));
       }
   }
   ```

   在上面的範例中，`Posts` Livewire 組件的 `render` 方法從資料庫中檢索所有文章並將其傳遞給 `livewire.posts` 視圖。
**小提示：傳遞資料給視圖的方式有很多，詳細用法可以前往官方網站查詢**

5. **建立 Livewire 視圖：**

   在 `resources/views/livewire` 目錄下建立名為 `posts.blade.php` 的 Livewire 視圖檔案。

   ```blade
   <!-- resources/views/livewire/posts.blade.php -->

   <h1>Blog Posts</h1>

   <ul>
       @foreach($posts as $post)
           <li>
               <h2>{{ $post->title }}</h2>
               <p>{{ $post->content }}</p>
           </li>
       @endforeach
   </ul>
   ```

   在這個 Livewire 視圖中，使用 Blade 語法迴圈顯示所有文章的標題和內容。

6. **定義 Livewire Route：**

   開啟 `routes/web.php` 檔案，定義用於顯示文章列表的 Livewire Route。

   ```php
   // routes/web.php

   use App\Http\Livewire\Posts;

   Route::get('/posts', Posts::class);
   ```

   上述 Route 定義了一個 GET 請求，當用戶訪問 `/posts` URL 時，會呼叫 `Posts` Livewire 組件的 `render` 方法並顯示 Livewire 視圖。

現在，當用戶訪問 `/posts` URL 時，將會呼叫 `Posts` Livewire 組件的 `render` 方法並顯示文章列表的 Livewire 視圖。這個例子演示了如何使用 Livewire 在 Laravel 中建立一個簡單的部落格應用程式。

## Laravel Livewire Forms


1. 使用 `make` 命令：

    ```php
    php artisan make:form UserCreateForm --model=User
    ```

    這將在 `app/Http/Livewire` 資料夾中建立新的表單元件。

2. 打開生成的檔案 `app/Http/Livewire/UserCreateForm.php`，在 `fields` 方法中定義要顯示的資料

    ```php
    class UserCreateForm extends FormComponent
    {
        public function fields()
        {
            return [
                Field::make('Name')->input()->rules('required'),
            ];
        }
    
        public function success()
        {
            User::create($this->form_data);
        }
    
        public function saveAndStayResponse()
        {
            return redirect()->route('users.create');
        }
    
        public function saveAndGoBackResponse()
        {
            return redirect()->route('users.index');
        }
    }
    ```

    無需在表單元件中使用 `render()` 方法，也不需要擔心元件視圖，因為該套件會自動處理。

**小提示：可以為 `Model` 添加 `FillsColumns` trait，以便通過數據庫列名自動填充 `$fillable`。**
