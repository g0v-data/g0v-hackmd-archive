# C# 修改csv
```
var lines = File.ReadAllLines(AppDomain.CurrentDomain.BaseDirectory + @"\STKCconfig.csv").ToList();
for (int i = 0; i < lines.Count; i++) {
    if (i == 1) {
    lines[i] = string.Join(",", lines[i].Split(',').Select((x, j) => j == 3 ? "0" : x));
    //i為行,x(j)為列
    }
}
File.WriteAllLines(AppDomain.CurrentDomain.BaseDirectory + @"\STKCconfig.csv", lines);
```