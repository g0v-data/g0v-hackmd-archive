# React
* component 必定為大寫英文字母開頭，網頁標籤必為小寫開頭
* className 等價於 HTML的 class
* 



```
https://react.dev/learn
```
> Notice that <MyButton /> starts with a capital letter. That’s how you know it’s a React component. React component names must always start with a capital letter, while HTML tags must be lowercase.

> In React, you specify a CSS class with className. It works the same way as the HTML class attribute:

> In React, there is no special syntax for writing conditions. Instead, you’ll use the same techniques as you use when writing regular JavaScript code. For example, you can use an if statement to conditionally include JSX:
> ```
> let content;
> if (isLoggedIn) {
>   content = <AdminPanel />;
> } else {
>   content = <LoginForm />;
> }
> return (
>   <div>
>     {content}
>   </div>
> );
> ```
> If you prefer more compact code, you can use the conditional ? operator. Unlike if, it works inside JSX:
> ```
> <div>
>   {isLoggedIn ? (
>     <AdminPanel />
>   ) : (
>     <LoginForm />
>   )}
> </div>
> ```
> When you don’t need the else branch, you can also use a shorter logical && syntax:
> ```
> <div>
>   {isLoggedIn && <AdminPanel />}
> </div>
> ```
> All of these approaches also work for conditionally specifying attributes. If you’re unfamiliar with some of this JavaScript syntax, you can start by always using if...else.

> Functions starting with use are called Hooks. useState is a built-in Hook provided by React