# 爬蟲 Crawler
## 參考影片

## 初始化
```
#初始化使用者名稱、email、密碼、頁面超時設定
def __init__(self, account_name, account_email, account_password, page_load_timeout):
        self.name = account_name
        self.email = account_email
        self.password = account_password
        self.page_load_timeout = page_load_timeout
```

## 進入帳戶
```
# 透過更改使用者代理程式繞過登入系統
def login(self, driver):
    driver.get("要進入的網站")

    # bypassing login system by changing user agent.
    driver.execute_cdp_cmd('Network.setUserAgentOverride', {
            "userAgent": "user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) "
                        "AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36'"
    })

    # writing email and password on the form
    driver.find_element(By.XPATH, '//*[@id="username"]').send_keys(self.email)
    driver.find_element(By.XPATH, '//*[@id="password"]').send_keys(self.password)

    # I don't like the xpath selector on this one, I will do it by text
    buttons = driver.find_elements(By.TAG_NAME, 'button')
    for button in buttons:
        if button.text == 'Sign in':
            button.click()
            break

    sleep(self.page_load_timeout)
    return driver
```

## 尋找標籤
```

```

## 初始化驅動(* )
```
#初始化驅動選項(針對額外開啟的頁面)
def initialize_driver_options():
    options = ChromeOptions()
    
    #瀏覽器的解析度
    options.add_argument('--window-size=1920,1080')
    #關閉擴充
    options.add_argument('--disable-extensions')
    #禁用gpu(以此來規避bug)
    options.add_argument('--disable-gpu')
    #禁用沙盒
    options.add_argument('--disable-setuid-sandbox')
    #禁用3D渲染
    options.add_argument('--disable-software-rasterizer')
    #停止log(?)
    options.add_argument('--log-level=3')
    
    options.add_argument('--silent')
    options.add_argument('--useAutomationExtension=false')

    return options
```