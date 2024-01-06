**虎科大AME0217電腦教室**

**SkyMars API 教育訓練**

GET_status：狀態資訊(程式號碼&行號)
```
//GET_status：狀態資訊
xd = _get_data(@"<CNC>
<API>GET_status</API>
<ConnKey>pmc</ConnKey>
<SendId>20110908</SendId>
</CNC>");
if (xd.HasChildNodes)
{
    var temp = xd.SelectNodes("CNC/MainProg");
    textBox26.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/CurSeq");
    textBox27.Text = "BC:"+temp[0].InnerText;
}

```

GET_feed_spindle：進給率/轉速
--------Example--------
```
//GET_feed_spindle：進給率/轉速
xd = _get_data(@"<CNC>
<API>GET_feed_spindle</API>
<ConnKey>pmc</ConnKey>
<SendId>20110908</SendId>
</CNC>");
if (xd.HasChildNodes)
{
    var temp = xd.SelectNodes("CNC/ActFeed");
    textBox25.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/ActSpindle");
    textBox28.Text = temp[0].InnerText;

    temp = xd.SelectNodes("CNC/OvFeed");
    textBox22.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/OvSpindle");
    textBox23.Text = temp[0].InnerText;
}

```

其他Code
--------Example--------
```
xd = _get_data(@"<CNC>
<API>GET_othercode</API>
<ConnKey>pmc</ConnKey>
<SendId>20110908</SendId>
</CNC>");
if (xd.HasChildNodes)
{
    var temp = xd.SelectNodes("CNC/HCode");
    textBox11.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/DCode");
    textBox19.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/TCode");
    textBox18.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/MCode");
    textBox21.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/FCode");
    textBox12.Text = temp[0].InnerText;
    temp = xd.SelectNodes("CNC/SCode");
    textBox20.Text = temp[0].InnerText;
}

```

相關時間
--------Example--------

```
//相關時間
            xd = _get_data(@"<CNC>
            <API>GET_time</API>
            <ConnKey>123</ConnKey>
            <SendId>20110908</SendId>
            </CNC>");
            if (xd.HasChildNodes)
            {
                var temp = xd.SelectNodes("CNC/Power");
                textBox14.Text = temp[0].SelectSingleNode("Hour").InnerText + ":" 
                    + temp[0].SelectSingleNode("Minuite").InnerText + ":" 
                    + temp[0].SelectSingleNode("Second").InnerText;
                temp = xd.SelectNodes("CNC/Cutting");
                textBox15.Text = temp[0].SelectSingleNode("Hour").InnerText + ":"
                    + temp[0].SelectSingleNode("Minuite").InnerText + ":"
                    + temp[0].Sele
                textBox16.Text = temp[0].SelectSingleNode("Hour").InnerText + ":"
                    + temp[0].SelectSingleNode("Minuite").InnerText + ":"
                    + temp[0].SelectSingleNode("Second").InnerText;
                temp = xd.SelectNodes("CNC/Operation");
                textBox17.Text = temp[0].SelectSingleNode("Hour").InnerText + ":"
                    + temp[0].SelectSingleNode("Minuite").InnerText + ":"
                    + temp[0].SelectSingleNode("Second").InnerText;ctSingleNode("Second").InnerText;
            }
```

Part Count
```
//Part Count
            xd = _get_data(@"<CNC>
            <API>GET_part_count</API>
            <ConnKey>123</ConnKey>
            <SendId>20110908</SendId>
            </CNC>");
            if (xd.HasChildNodes)
            {
                var temp = xd.SelectNodes("CNC/PartCount");
                textBox13.Text = temp[0].InnerText;
            }
```


```
XmlDocument xd = new XmlDocument();
            xd = _get_data(@"<CNC>
            <API>GET_position</API>
            <ConnKey>pmc</ConnKey>
            <SendId>20110908</SendId>
            </CNC>");
            if(xd.HasChildNodes)
            { 
            var temp = xd.SelectNodes("CNC/PosData");
            textBox10.Text = temp[0].SelectSingleNode("Abs").InnerText;//X
            textBox9.Text = temp[1].SelectSingleNode("Abs").InnerText;//Y
            textBox8.Text = temp[2].SelectSingleNode("Abs").InnerText;//Z

            textBox1.Text = temp[0].SelectSingleNode("Mach").InnerText;//X
            textBox2.Text = temp[1].SelectSingleNode("Mach").InnerText;//Y
            textBox3.Text = temp[2].SelectSingleNode("Mach").InnerText;//Z
            }
```

```
public XmlDocument _get_data(string xml_cmd)
        {
            XmlDocument doc = new XmlDocument();
            doc.LoadXml(xml_cmd);

            TcpClient tcpClient = new TcpClient();
            tcpClient.Connect(skymars_server_ip, skymars_server_port);

            NetworkStream ns = tcpClient.GetStream();
            byte[] command = Encoding.UTF8.GetBytes(doc.OuterXml);

            if (ns.CanWrite)
            {
                ns.Write(command, 0, command.Length);
            }

            Thread.Sleep(100);

            string receStr = string.Empty;

            byte[] rece = new byte[100];
            if (ns.CanRead)
            {
                while (ns.DataAvailable)
                {
                    Array.Clear(rece, 0, rece.Length);
                    ns.Read(rece, 0, rece.Length);
                    receStr += Encoding.UTF8.GetString(rece);
                }
            }

            XmlDocument xd = new XmlDocument();
            if (receStr != "")
            {                
                xd.LoadXml(receStr);                
            }

            return xd;
        }
```