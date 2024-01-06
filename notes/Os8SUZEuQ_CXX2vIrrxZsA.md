# C# 功能小筆記
判斷某字串是否包含某個字串陣列中
```
string[] myStrings = { "a", "b", "c" };
string checkThis = "abc";

if (myStrings.Any(checkThis.Contains))
{
    MessageBox.Show("checkThis contains a string from string array myStrings.");
}
or using Linq
```