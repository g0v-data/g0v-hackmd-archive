Focus 3 連線問題
===

:::info
- **topic :** 解決focus 3可以接收卻無法上傳的問題
- **所需知識 :** MQTT基礎概念、AWS連線方法
- **測試工具 :** AWS 的MQTT測試端、AIOT網頁
:::

## 問題描述
focus 3在使用跟meta & pico 一樣的方法去做接收及發送的時候，在IoTCore Pub出現打叉的符號
(正常可以的話，會是三個都顯示綠色圓圈)
![image](https://hackmd.io/_uploads/HJamaCBlJg.png)

## 可能原因分析
1. pico & meta 都是使用Mono編譯，但focus 3是使用IL2CPP編譯，這也導致meta的解決辦法無法用在它上面
![image](https://hackmd.io/_uploads/rkpOJkLx1e.png)
2. 使用原先連線方式(臨時性金鑰)會有其他的問題

## 嘗試解決問題
1. 將上傳的手法更改為跟接收一樣(使用certificate)
> 原先的方法可以參考之前筆記的 **通訊模組** 的章節
> [AIOT軟體開發手冊](https://hackmd.io/@lab31718/index/%2FV5helSfxR9qO5nwzq2nuhQ#AIOT%E7%B3%BB%E7%B5%B1%E8%BB%9F%E9%AB%94%E9%96%8B%E7%99%BC%E6%89%8B%E5%86%8A)
* 使用同一份證書會使publisher 或 client 先連線到的那端斷線

舉例來說 : 在ApiManager.cs中我們讓pushiler先連線再讓client連線，所以會UI顯示都是綠色的圈但publisher已經斷線了
```=csharp
public async void PasswordInput(string password)
    {
        Logger.Log("Now checking password...");
        if (await CheckPassword(password))//密碼對
        {
            Debug.Log("password true");
            File.WriteAllText(DevicePasswordUrl, password);
            ///下面那個
            IoTCorePublisher.IoTPublisher();
            IoTCoreConsumer.IoTConsumer();
            ///上面那個
        }
        else//密碼錯
        {
            //錯誤訊息在CheckPassword(DevicePasswordStr)裡印了
        }
    }
```
而後來嘗試的是讓斷線後馬上重連，但這樣會造成通訊成本大增
以下程式是在接收到訊息(也就是發送端斷線)馬上重連
```=csharp
private static void IotClient_MqttMsgPublishReceived(object sender, MqttMsgPublishEventArgs e)
    {
        if(client != null && client.IsConnected)
        {
            Debug.Log("客户端已连接。尝试接收消息。");
            try
            {
                string rawM = System.Text.RegularExpressions.Regex.Unescape(Encoding.UTF8.GetString(e.Message).Trim(new char[] { '"' }));;
                CommunicationManager.Receive(rawM, CommunicationType.IoTCore);
            }
            catch (Exception ex)
            {
                Debug.LogError($"處理消息時發生錯誤: {ex.Message}");
            }
        }
        //這行就是重新建立連線
        IoTCorePublisher.IoTPublisher();
    }
```
2. 使用java寫個library並以.jar的方式去添加到unity中，這方法比較low level但可行，最終沒有實做出來
 
## 最終解決辦法
更改clientID有助於AWS去辨識來連線的是不一樣的

原先的clientId並不是channel名稱(實驗室只有pico & meta，focus3就用pico)，所以可以更改

分別在M2MqttPublisher.cs 及 M2MqttClient.cs做更動
```=csharp
//從這個
private string clientId = "pico";
//更改為
private string clientId = "publisher";
```
## 根本原因
AWS並未支援cpp的套件，所以在原本透過打api得到憑證的方法就會失效
而在使用同一份證書時因為原先使用同個clientID會讓AWS認為是同一個裝置連線兩次而導致第一個成功建立連線的被斷線了

![image](https://hackmd.io/_uploads/rkFUnbUe1x.png)

