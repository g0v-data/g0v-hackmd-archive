# Day 10 - 打造前端螺絲釘！
## ViewComponent 導入!

沒錯，又要來裝東西了！[文件](https://viewcomponent.org/guide/getting-started.html)底加

這次要使用的是 `ViewComponent`，可以很好的幫助我們從常規到特規做出各式各樣的小零件，提高複用程度增加工作效率

雖然說也是有 `partial` 可以用，但這邊的複雜度可能用 `Component` 比較好處理
這裡說的複雜度主要是可變化的程度，譬如顏色樣式，特殊功能，切版的方便度等等
除了透過傳入的參數，也可以在 `Component` 內部去變化很多條件渲染出不同的畫面，這些事情在 `partial` 上也做得到，只是相對不那麼易讀

```
rails generate component Button
```
安裝完幫忙自動生成一個預設的 Component 空殼

## 實作
這次主要的目標是先替換很常用的「按鈕」樣式
主要分為幾塊
1. 會有按鈕樣式但是要加上連結的狀況
2. 有基本樣式
3. 能夠有限度的自由調整 CSS

先預想出 HTML 結構，考慮是零件，先有一個包覆的隔離層，有 CSS 變動可針對此層

```
# app/components/button_component.html.erb

<div class="button_container <%= wrap_classes %>">
  ...
</div>
```


再來就是內部，這部分預計在 Component 內部組裝，所以內部的位置擺放給 `button` method

```
# app/components/button_component.html.erb

<div class="button_container <%= wrap_classes %>">
  <%= button %>
</div>
```


這樣接下來就回到 Component 內部造出 `button`，並處理會遇到有連結的情境，也就是說會有連結包住按鈕跟單純按鈕的狀況加入 `button` 內

```ruby
# app/components/button_component.rb

class ButtonComponent < ViewComponent::Base
  def initialize(...)
    ...
  end

  def button
    return base_button unless with_link?

    link_to link_path do
      base_button
    end
  end
  
  private
  
  def base_button
    content_tag(:button, content, class:"px-4 py-1 rounded-full")
  end
  
  def with_link?
    ...
  end
end
```

這裡的 `link_path` 是需要外部給的所以加入初始化

```ruby
# app/components/button_component.rb


class ButtonComponent < ViewComponent::Base
  attr_reader :link_path

  def initialize(link_path: nil)
    @link_path = link_path
  end

  def button
    return base_button unless with_link?

    link_to link_path do
      base_button
    end
  end
  
  private
  
  def base_button
    content_tag(:button, content, class:"px-4 py-1 rounded-full")
  end
  
  def with_link?
    link_path.present?
  end
end
```

另外考慮到 link 會帶 attribute，像是 `data`，所以也來處理

```ruby
# app/components/button_component.rb


class ButtonComponent < ViewComponent::Base
  attr_reader :link_path, :link_options

  def initialize(link_path: nil, link_options: {})
    @link_path = link_path
    @link_options = link_options
  end

  def button
    return base_button unless with_link?

    link_to link_path, **link_options do
      base_button
    end
  end
  
  private
  
  def base_button
    content_tag(:button, content, class:"px-4 py-1 rounded-full")
  end
  
  def with_link?
    link_path.present?
  end
end
```

至此第一個需求已經可以解決，接著第二個，因為只是單純的換色，那這邊就抽出一個 `display_type` 來幫忙切換換色

```ruby
# app/components/button_component.rb


class ButtonComponent < ViewComponent::Base
  attr_reader ..., :display_type
  
  MODIFIERS = {
    black: %w[bg-gray-500 text-black],
    blue: %w[bg-gray-500 text-blue-300],
    green: %w[bg-gray-500 text-green-300],
    red: %w[bg-gray-500 text-red-300],
    yellow: %w[bg-gray-500 text-yellow-300],
    orange: %w[bg-gray-500 text-orange-300],
  }.freeze

  def initialize(..., display_type: nil)
    ...
    @display_type = display_type || :black # 預設一個黑色按鈕
  end

  ...
  
  private
  
  def base_button
    content_tag(:button, content, class:"px-4 py-1 rounded-full #{modifiers}")
  end
  
  ...
  
  def modifiers
    MODIFIERS[display_type.to_sym]&.join(' ')
  end
end
```

最後最後，處理需求三給予一定限度的樣式控制

```ruby
# app/components/button_component.rb


class ButtonComponent < ViewComponent::Base
  attr_reader ..., :wrap_classes, :button_classes
  
  ...

  def initialize(..., wrap_classes: '', button_classes: '')
    ...
    @wrap_classes = wrap_classes
    @button_classes = button_classes
  end

  ...
  
  private
  
  def base_button
    content_tag(:button, content, class:"px-4 py-1 rounded-full #{modifiers} #{button_classes}")
  end
  
  ...
end
```

以上就完成一個萬用的小螺絲了

## 替換
接著就能快速的把畫面替換掉了！

```html
# app/views/shared/_navigation.html.erb

<nav class="...">
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

變成

```html
# app/views/shared/_navigation.html.erb

<nav class="...">
  <% if user_signed_in? %>
    <%= render ButtonComponent.new(display_type: :blue, link_path: plan_path).with_content(current_payment_info) %>
    <%= render ButtonComponent.new(display_type: :yellow, link_path: root_path).with_content(current_user.name) %>
    <%= render ButtonComponent.new(display_type: :red,
                                   link_path: destroy_user_session_path,
                                   link_options: { data: { turbo_method: :delete } }).with_content('登出') %>
  <% else %>
    <%= render ButtonComponent.new(display_type: :blue, link_path: price_path).with_content('費用') %>
  <% end %>
</nav>
```

就變得蠻清楚了吧！

還有 Form 也能一起處理

```html
# app/views/devise/sessions/new.html.erb

<div class="...">
  <%= form_for resource, html: { class: '...' }, as: resource_name, url: session_path(resource_name) do |form| %>

    ...

   # 可以替換原本的送出，並調整寬度顏色！ 
   <%= render ButtonComponent.new(display_type: :green, wrap_classes: 'w-1/2', button_classes:'w-full').with_content('送出') %>
    ...
  <% end %>
</div>
```

## 小插曲
這裡搞了小半天，忘記安裝完要去 `Tailwind` 設定加東西，不然 Tailwind 會跳過 Component 的內容不編譯

```javascript
# config/tailwind.config.js

const defaultTheme = require('tailwindcss/defaultTheme')

module.exports = {
  content: [
    ...,
    './app/components/**/*'
  ],
  ...
}
```

經過這整段處理，這樣在往前替換或是往後實作的時候就能簡單的做出按鈕又能方便的調整 (>_O)b
而如果同樣的事情在 `partial` 做的話可能就沒辦法這麼清晰了
