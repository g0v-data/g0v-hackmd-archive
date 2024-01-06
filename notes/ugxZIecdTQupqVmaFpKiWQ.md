# C# 泛型List<T>
宣告物件
```
public class ClassName {
            public string Name { get; set; }
            public int count { get; set; }
        }
```
宣告全域變數
```
static class config{
public static List<ClassName> aa = new List<ClassName>();
}
```
使用
```
void main()
config.aa.Add(new ClassName{Name="Mark",count=123});

```