# Day 9 - 我都唸 Devise，你呢？（二）

## Devise 拉皮
### 登入
```
# app/views/devise/sessions/new.html.erb

<div class="w-full h-full flex items-center justify-center">
  <%= form_for resource, html: { class: 'flex flex-col items-center justify-center mx-auto p-4 w-1/3 bg-gray-400 rounded-lg text-center text-black gap-2' }, as: resource_name, url: session_path(resource_name) do |form| %>

    <%= form.label :email %>
    <%= form.text_field :email, class: 'w-2/3 rounded-md' %>

    <%= form.label :password %>
    <%= form.text_field :password, class: 'w-2/3 rounded-md' %>

    <%= form.submit '送出', class:'bg-gray-500 px-4 py-1 rounded-full text-green-300 w-1/2' %>

    <%= render "devise/shared/links" %>
  <% end %>
</div>
```

### 註冊
```
# app/views/devise/registrations/new.html.erb

<div class="w-full h-full flex items-center justify-center">
  <%= form_for resource, html: { class: 'flex flex-col items-center justify-center mx-auto p-4 w-1/3 bg-gray-400 rounded-lg text-center text-black gap-2' }, as: resource_name, url: registration_path(resource_name) do |form| %>

    <%= form.label :name %>
    <%= form.text_field :name, class: 'w-2/3 rounded-md' %>

    <%= form.label :email %>
    <%= form.text_field :email, class: 'w-2/3 rounded-md' %>

    <%= form.label :password %>
    <% if @minimum_password_length %>
      <div class="text-xs text-red-600">*<%= @minimum_password_length %> characters minimum</div>
    <% end %>
    <%= form.text_field :password, class: 'w-2/3 rounded-md' %>

    <%= form.label :password_confirmation %>
    <%= form.text_field :password_confirmation, class: 'w-2/3 rounded-md' %>

    <%= form.submit '送出', class:'bg-gray-500 px-4 py-1 rounded-full text-green-300 w-1/2' %>

    <%= render "devise/shared/links" %>
  <% end %>
</div>
```
打算控制在最低程度的刻頁面，所以使用者編輯頁就暫時不去改樣式（~~偷懶~~

## 導覽列
承上因為認證使用者的狀態了，也就是要有介面顯示現在是否已登入的狀態，以及登入前後在導覽列的不同顯示內容
所以至少導覽列的部分要先做出來，那就來小小補充一下這個部分

| 項目 | Before login | After logout|
| --- | --- | --- |
| 使用者狀態(User name) | X | O |
| 登出(Logout link) | X | O |
| 費用(Price) | O | X |
| 計畫狀態(Plan) | X | O |

按照這個條件去拼出畫面
```
# app/views/shared/_navigation.html.erb

<nav class="flex items-center justify-end h-16 w-full mb-8 p-4 gap-4 bg-gray-600">
  <% if user_signed_in? %>
    <div class="bg-gray-500 px-4 py-1 rounded-full text-blue-300">
      <%= link_to current_payment_info, plan_path %>
    </div>
    <div class="bg-gray-500 px-4 py-1 rounded-full text-yellow-300">
      <%= link_to current_user.name, root_path %>
    </div>
    <div class="bg-gray-500 px-4 py-1 rounded-full text-red-300">
      <%= link_to '登出', destroy_user_session_path, data: { turbo_method: :delete } %>
    </div>
  <% else %>
    <div class="bg-gray-500 px-4 py-1 rounded-full text-blue-300">
      <%= link_to '費用', price_path %>
    </div>
  <% end %>
</nav>
```

```
<!DOCTYPE html>
# app/views/layouts/application.html.erb

<html>
  <head>
    ...
  </head>

  <body>
    <main class="w-full h-full min-h-screen bg-gray-700 text-white">
      <%= render 'shared/navigation' %>
      <%= yield %>
    </main>
  </body>
</html>
```

```ruby
# app/controllers/application_controller.rb

class ApplicationController < ActionController::Base
  # 這樣就可以控制沒登入的人不能使用！
  before_action :authenticate_user!
end
```

```ruby
# config/routes.rb

Rails.application.routes.draw do
  ...

  get '/price', to: 'plans#price'
  get '/plan', to: 'plans#show'
end
```

```ruby
# app/controllers/plans_controller.rb

class PlansController < ApplicationController
  # 等之後做金流的時候再來補充
end
```

### 完工照
![https://ithelp.ithome.com.tw/upload/images/20230924/20142040kBSGfQBX8e.png](https://ithelp.ithome.com.tw/upload/images/20230924/20142040kBSGfQBX8e.png)
![https://ithelp.ithome.com.tw/upload/images/20230924/20142040DiclddWnMV.png](https://ithelp.ithome.com.tw/upload/images/20230924/20142040DiclddWnMV.png)

如此一來，整個應用已經能做最「基本」的個人記帳功能了 ~~(對，後面還有附加功能~~
但今天刻完之後發現，畫面有太多重複的地方，看起來需要一點「特殊」處理，明天就先來做這個部分
