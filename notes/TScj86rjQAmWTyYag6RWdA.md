# 爬蟲 Crawler
## 參考影片

## 基本框架
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options

options = Options()
options.chrome_executable_path = "chromedriver路徑"

driver = webdriver.Chrome(options = options)
driver.get("要連接的網址")

driver.clos()

```

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
driver.find_element(s)(By.ID, “ ”) #使用id屬性值定位
driver.find_element(s)(By.NAME, “ ”) #使用name屬性值定位
driver.find_element(s)(By.LINK_TEXT, “ ”) #使用超連結文字定位
driver.find_element(s)(By.PARTIAL_LINK_TEXT, “ ”) #使用部分超連結文字定位
driver.find_element(s)(By.TAG_NAME, “ ”) #使用標籤名稱定位
driver.find_element(s)(By.CLASS_NAME, “ ”) #使用class屬性值定位
driver.find_element(s)(By.XPATH, “ ”) #使用XPath屬性定位
driver.find_element(s)(By.CSS_SELECTOR, “ ”) #使用CSS選擇器定位
```

## 對標籤的動作
```
.send_keys() #輸入值
.click() #點擊
.text #取得文字
.get_attribute('屬性名稱') #取得特定屬性
```

## 初始化驅動(* )
可參考:[https://www.cnblogs.com/gurenyumao/p/14721035.html](https://)
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
    #禁止自動化擴充
    options.add_argument('--useAutomationExtension=false')

    return options
```

## 主程式
```
if __name__ == '__main__':
    webdriver = Chrome(options=initialize_driver_options())

    # 
    crawler = class_name(
        account_name='Roy353',
        account_email='a9517532468000@gmail.com',
        account_password='dhf3771646',
        page_load_timeout=5,
        trading_timeout=2
    )

    webdriver = crawler.login(webdriver)
    
    webdriver.close()
```

## 捲動視窗
```
# 若是要爬取像是社群網站類的，就需要不斷滑動以加載內容更多


```
