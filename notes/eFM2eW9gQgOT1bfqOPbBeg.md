# 對Windows 服務進行除錯

**把 Windows Service 當成 Console Application 來執行**
1. 由於 Windows Service 與 Console Appliation 的程式進入點都一樣是 static void Main()，預設的 Main() 內容如下：
---
```
static void Main()
{
	ServiceBase[] ServicesToRun;
	ServicesToRun = new ServiceBase[] 
	{ 
		new Service1() 
	};
	ServiceBase.Run(ServicesToRun);
}
```
---
2. 在 Windows Service 專案中的啟動點是在 OnStart 方法，但這個方法是屬於 protected 存取層級，無法對外公開使用。


---
**修改程式了，共有 3 個步驟：**
### 1. 先修改 Service1.cs 程式 ( Windows Service 專案中的主要服務類別 )

    由於 OnStart 與 OnStop 方法被 protected 宣告保護著，無法讓使用此類別的程式直接呼叫，此時必須多寫兩個方法(method)讓使用此類別的程式可以呼叫 OnStart() 方法。
```
public void Start(string[] args)
{
    this.OnStart(args);
}

public void Stop()
{
    this.OnStop();
}
```
### 2. 接著修改 Program.cs 中的 Main() 方法 ( 也就是整個 Windows Service 專案的程式啟動點 )
 透過 Environment.UserInteractive 屬性即可得知該組件是執行於使用者互動模式中，若該組件是以 Windows Service 執行時，則此屬性將會回傳 false，將原本的 Main() 程式改成以下程式碼：
```
static void Main()
{
	if (Environment.UserInteractive)
	{
		Service1 s = new Service1();

		s.Start(null);

		Console.WriteLine("服務已啟動，請按下 Enter 鍵關閉服務...");
		// 必須要透過 Console.ReadLine(); 先停止程式執行
		// 因為 Windows Service 大多是利用多 Thread 或 Timer 執行長時間的工作
		// 所以雖然主執行緒停止執行了，但服務中的執行緒已經在運行了!
		Console.ReadLine();

		s.Stop();

		Console.WriteLine("服務已關閉");
	}
	else
	{
		ServiceBase[] ServicesToRun;
		ServicesToRun = new ServiceBase[] 
		{ 
			new Service1() 
		};
		ServiceBase.Run(ServicesToRun);
	}
}
```
### 3. 變更 Windows Service 專案的 輸出類型 ( Output Type )
開啟 Windows Service 專案屬性(Properties)視窗，將原本的 Windows Application 切換到 Console Application即可。

來源:https://blog.miniasp.com/post/2009/04/05/How-to-debugging-Windows-Service-and-Setup-Project-Custom-Action