# 撰寫 CGI

## 作業一：Hello World
在原本存放cgi的路徑上先創立一個`hello.c`其內容為簡單的
```c
#include <stdio.h>

int main(void) {
    printf("Content-type: text/html\n\n");
    printf("<html>\n");
    printf("  <head>\n");
    printf("    <title>CGI Response</title>\n");
    printf("  </head>\n");
    printf("  <body>\n");
    printf("    Hello World\n");
    printf("  </body>\n");
    printf("</html>\n");

    return 0;
}
```

之後編譯成`hello.cgi`，再透過`curl http://172.16.222.101/cgi-bin/hello.cgi` 來檢查cgi回傳的內容，也透過網頁檢查結果

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_028e5abc4dc44b097b2223f54c19c0db.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c33b0feb7f1eaf63df6cecaea9ffc0af.png)

## 作業二：登入

首先，先寫一個html格式，並放在伺服器的路徑上，並在html中設定要執行的cgi，並使用POST

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3c10656aeaeb3109ed548d4c49bd9f13.png)


完成後在瀏覽器輸入[`http://172.16.222.101/log_in.html`](http://172.16.222.101/log_in.html)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6fe492feaa4a9a88dffbf32d20e07b92.png)


接下來測試登入成功以及登失敗

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_070894f7acf2e760948980b538aedc5f.png)

## 作業三：密碼灑鹽

使用`libsodium`函式庫負責加密的功能。

首先先針對2位使用者的密碼使用hash加密儲存，新增一個hash function專門處理加密

```c
void hash_password(const char* input, char* output) {
    if(crypto_pwhash_str(output, input, strlen(input),crypto_pwhash_OPSLIMIT_INTERACTIVE,crypto_pwhash_MEMLIMIT_INTERACTIVE) != 0)
    {
        fprintf(stderr, "Out of memory.\n");
        exit(1);
    }
}
```

```c
  char *admin_Password="admin";
  char admin_hash_password[256]; 
  hash_password(admin_Password, admin_hash_password);

  char *webmail_Password="webmail";
  char webmail_hash_password[256];
  hash_password(webmail_Password,webmail_hash_password);
```

接著在比對密碼時不使用明文比對，因此使用`crypto_pwhash_str_verify()` 去驗證

```c
if (username && password && strcmp(username, "admin") == 0 && crypto_pwhash_str_verify(admin_hash_password, password, strlen(password)) == 0) 
{
    printf("<p>Hello admin</p>");
    printf("%s",admin_hash_password);
} 
else if (username && password && strcmp(username, "webmail") == 0 && crypto_pwhash_str_verify(webmail_hash_password, password, strlen(password)) == 0) 
{
    printf("<p>Hello webmail</p>");
    printf("%s",webmail_hash_password);
} 
else 
{
    printf("<p>Invalid username or password</p>");
}
```

最後察看結果(最後一行為加密後結果)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_35c74dec963ad52bdbd4f1ca977f35f0.png)


## 作業四：Redis 儲存 Session
在原本的登入cgi當中加入Redis儲存Session的功能。
在使用者登入後創建跟儲存Session

```c
void creatSession(char *userSessionID, char *username)
{
    redisContext *c = redisConnect("127.0.0.1", 6379);
    if (c == NULL || c->err) 
    {
        if (c) 
        {
            printf("Redis error: %s\n", c->errstr);
            redisFree(c);
        } 
        else 
        {
            printf("Redis allocation error\n");
        }
        exit(1);
    }
    redisReply *reply = redisCommand(c, "SET session:%s %s", userSessionID, username);
    if (reply) freeReplyObject(reply);
}
```

```c
if (username && password && strcmp(username, "admin") == 0 && crypto_pwhash_str_verify(admin_hash_password, password, strlen(password)) == 0) 
{
    printf("<p>Hello admin</p>");
    char *userSessionID="123";
    creatSession(userSessionID,username);
    printf("%s",admin_hash_password);
} 
else if (username && password && strcmp(username, "webmail") == 0 && crypto_pwhash_str_verify(webmail_hash_password, password, strlen(password)) == 0) 
{
    printf("<p>Hello webmail</p>");
    char *userSessionID="321";
    creatSession(userSessionID,username);
    printf("%s",webmail_hash_password);
} 
```

成功利用cgi登入後，session會被儲存。最後用redis檢查
透過輸入`redis-cli`後輸入`keys *`去顯示儲存的資料

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_705d37f248ef06973a2b2e86f321895b.png)


## 作業五：SQLite 儲存使用者資訊

1. **設計一個 table schema**
    
    首先先建立sqlite的db，我命名為test.db，並在裡面創建table
    
    ```c
    CREATE TABLE log_in_table (
        user TEXT,
        password TEXT,
        userID  TEXT  
    );
    ```
    
    之後更改程式碼內容，先將資料存進db當中
    
    ```c
        sqlite3 *db;
        char *err_msg = 0;
        int rc = sqlite3_open("test.db", &db);
        if(rc)
        {
            fprintf(stderr,"Fail to open db\n",sqlite3_errmsg(db));
            sqlite3_close(db);
            return ERR_OPEN_DB_FAIL;
        }
        const char *sql = "INSERT INTO log_in_table (user, password, userID) VALUES (?, ?, ?);";
        sqlite3_stmt *stmt;
        char *admin_Password = "admin";
        char admin_hash_password[256]; 
        hash_password(admin_Password, admin_hash_password);
        sqlite3_prepare_v2(db, sql, -1, &stmt, NULL);
        sqlite3_bind_text(stmt, 1, "admin", -1, SQLITE_STATIC);
        sqlite3_bind_text(stmt, 2, admin_hash_password, -1, SQLITE_STATIC);
        sqlite3_bind_text(stmt, 3, "admin123", -1, SQLITE_STATIC);
        rc=sqlite3_step(stmt);
        if (rc != SQLITE_DONE) 
        {
            printf("insert faile 1%s\n",sqlite3_errmsg(db));
        } 
        else 
        {
            printf("insert success 1\n");
        }
        sqlite3_reset(stmt);
        char *webmail_Password="webmail";
        char webmail_hash_password[256];
        hash_password(webmail_Password,webmail_hash_password);
        sqlite3_bind_text(stmt, 1, "webmail", -1, SQLITE_STATIC);
        sqlite3_bind_text(stmt, 2, webmail_hash_password, -1, SQLITE_STATIC);
        sqlite3_bind_text(stmt, 3, "webmail321", -1, SQLITE_STATIC);
        rc=sqlite3_step(stmt);
        if (rc != SQLITE_DONE) 
        {
            printf("insert fail 2%s\n",sqlite3_errmsg(db));
        } 
        else 
        {
            printf("insert success 2\n");
        }
        sqlite3_finalize(stmt);
        sqlite3_close(db);
    ```
    
    執行`sudo gcc -g -o log_in.cgi log_in.c -lsodium -I /var/www/cgi-bin/hiredis/ -L /var/www/cgi-bin/hiredis/ -l hiredis -I /home/harris/sqlite-amalgamation-3460000/ -L /home/harris/sqlite-amalgamation-3460000/ -lsqlite3` 
    通過上面的修改之後，檢查db當中的資料是否有成功儲存，透過指令`SELECT * FROM log_in_table;`
    
    可以看到table中儲存的資料
    
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_df3745b34df269f8cc05c8548f919231.png)
    
2. **提供一個修改使用者顯示名稱的 API，並在登入後的頁面提供介面讓使用者可以修改。**
    
    接下來我們提供一個新的功能讓使用者可以輸入想更改的userID
    
    透過新增一個html指令
    
    ```c
    void changeUserID(char *currentUserID) 
    {
        printf("<form action=\"/cgi-bin/log_in.cgi\" method=\"POST\">");
        printf("<label for=\"newUserID\">New UserID:</label>");
        printf("<input type=\"text\" id=\"newUserID\" name=\"newUserID\"><br><br>");
        printf("<input type=\"hidden\" name=\"action\" value=\"updateUserID\">");
        printf("<input type=\"hidden\" name=\"currentUserID\" value=\"%s\">", currentUserID);
        printf("<input type=\"submit\" value=\"Update UserID\">");
        printf("</form>");
    }
    ```
    
    使用者登入後會呼叫`changeUserID((char *)userID);`
    
    ```c
    printf("<p>Hello admin</p>");
    char *userSessionID = "123";
    createSession(userSessionID, username);
    
    sqlite3_bind_text(stmt, 1, username, -1, SQLITE_STATIC);
    if (sqlite3_step(stmt) == SQLITE_ROW) {
        const unsigned char *userID = sqlite3_column_text(stmt, 0);
        printf("<html><body>UserID: %s</body></html>", userID);
        changeUserID((char *)userID);
    } else {
        printf("<html><body>userID:none </body></html>");
    }
    ```
    
    頁面會像
    
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e9799ca8a16ba2027d3adbacf360e09c.png)

    
    接著使用者可輸入新的UserID，變更要顯示的id，並同步更新到sqllite。按下後會顯示
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a1023bacc943790f2743cbb5c451bbe2.png)

    
    之後登入後就為使用者新的id
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_417c6d6a81b6e1daaeb64dfbd3aa69d6.png)

    

## 作業六：動態連結
首先先cd到sqlite的資料夾，確認資料夾當中有sqlite3.c檔，接著執行   

`gcc -shared -fPIC -o libsqlite3.so sqlite3.c -lpthread -ldl`

- `shared`：告訴gcc生成共享庫。
- `fPIC`：表示生成位置獨立的代碼，這是共享庫所需要的。
- `o libsqlite3.so`：指定輸出的文件名為`libsqlite3.so`。
- `sqlite3.c`：這是SQLite的主要源碼文件。
- `lpthread -ldl`：這些是gcc的鏈接選項，`lpthread`用於支持多線程，`ldl`用於支持動態加載和鏈接。

接著使用`ldd`指令確認動態連接，輸出結果為

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e28702c6f291387857120c1407a7135d.png)


## 作業七：CSRF

1. **建兩個 site**
    
    首先先將user/local/apache2/http.conf當中關於cgi路徑的部註解掉，因為後續會依照兩個不同host呼叫不同路徑的cgi。
    
    接著新增一個路徑`sudo mkdir -p /usr/local/apache2/sites-available/vhosts.conf`  用來存放host
    
    ```c
    <VirtualHost *:80>
        ServerName vulnerable.example.com
        DocumentRoot /var/www/vulnerable
        ScriptAlias /cgi-bin/ "/var/www/vulnerable/cgi-bin/"
        <Directory "/var/www/vulnerable">
            AllowOverride None
            Require all granted
        </Directory>
        <Directory "/var/www/vulnerable/cgi-bin">
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Require all granted
            AddHandler cgi-script .cgi
        </Directory>
    </VirtualHost>
    
    <VirtualHost *:80>
        ServerName attacker.example.com
        DocumentRoot /var/www/attacker
        <Directory /var/www/attacker/>
           Require all granted
        </Directory>
    </VirtualHost>
    ```
    
    1. **實作一個登入後可以修改使用者暱稱的 CGI 放在 `vulnerable.example.com`**
        
        我使用的cgi是與前面練習題一模一樣的cgi以及html。之後測試登入都沒問題。
        
        後面發現更改etc/hosts檔案新增
        
        ```c
        172.16.222.101 attacker.example.com
        172.16.222.101 vulnerable.example.com
        ```
        
        之後就可透過下面兩個domain連到對應的html
        
        [`http://attacker.example.com/CSRF_attack.html`](http://attacker.example.com/CSRF_attack.html)
        
        [`http://vulnerable.example.com/change_nickname.html`](http://vulnerable.example.com/change_nickname.html)
        
    2. **實作一個網頁放在 `attacker.example.com` 可以發 Request 給 `vulnerable.example.com` 達成跨站攻擊，成功修改使用者名稱**
        
        接著實作攻擊的部分，首先需要確保使用者登入後頁面有紀錄以及保存cookie
        
        因此在登入後在http標頭設定cookie
        
        ```c
        printf("Set-Cookie: sessionID=%s; Path=/; HttpOnly\r\n",userSessionID);
        printf("Content-type: text/html\n\n");
        ```
        
        接著透果f12檢查是否成功
        
       ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0fd8d621d475d5329456791d2e3db5f1.png)

        
        可以看到使用者的cookie有確實被儲存。接著進行攻擊部分。    
        在attacker的html中，設定想要更改的userID，透過對方在登入狀態目前保存有效cookie時送出更改userID的POST請求
        
        ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>CSRF Attack Page</title>
        </head>
        <body>
            <h1>CSRF Attack Page</h1>
            <p>This page will attempt to log in and change the user ID on vulnerable.example.com</p>
            
            <!-- Form to change user ID -->
            <form id="csrfForm" method="POST" action="http://vulnerable.example.com/cgi-bin/change_nickname.cgi">
                <input type="hidden" name="action" value="updateUserID">
                <input type="hidden" name="currentUserID" value="webmail123">
                <input type="hidden" name="newUserID" value="HackedUserID">
            </form>
            
            <script>
                    window.onload = function() {
                    document.getElementById("csrfForm").submit();
                };
            </script>
        </body>
        </html>
        ```
        
        執行完後重新登入可以發現userID被改了，代表攻擊成功。
        
       ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9f862674b2b67c4baab0db280323720.png)

        
    3. **修改你的 vulnerable CGI，使之可以防禦 CSRF**
        
        接著開始進行防禦，我使用的防禦方式為CSRF token的方式，他的概念主要是在使用者登入後會生成一個token，此時若要進行更改userID時會要求驗證CSRF token以此確認更改userID是由本人發出，這樣就可以避免跨腳本攻擊
        首先先設定一個隨機生成token的function，他會依照使用者身分生成一個token
        
        ```c
        void generateCSRFToken(char *csrfToken, char *username, int tokenSize)
        {
            char charset[] = "0123456789"
                            "abcdefghijklmnopqrstuvwxyz"
                            "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
            int randomStrSize=tokenSize-sizeof(username);
            strncpy(csrfToken,username,strlen(username));
            for(int i=strlen(username);i<tokenSize;i++)
            {
                int key = rand() % (int) (sizeof(charset) - 1);
                csrfToken[i] = charset[key];
            }
            csrfToken[tokenSize-1]='\0';
        }
        ```
        
        再來就是準備進行更改ID時的設定，在準備進行更改ID前利用`generateCSRFToken`產生token，並用`createCsrfSession`將他存進redis中登入者對應的sessionID，之後呼叫`changeUserID`時也把token傳過去。
        
        ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_593d2dccbbfbca6ea1713a957a1ee6a1.png)

        
        再來就是進行changeUserID功能的部分，在一開始先透過`getenv("HTTP_COOKIE")`取得`userSessionID` 再來就是透過sessionID到redis中尋找對應的token，接著就是比對目前環境中的csrfToken(如果hacker有丟進來)與登入者合法的token(存在redis server中)來達成防護，以確保這個request是由本人發出。
        
        ```c
          char *userSessionID = getenv("HTTP_COOKIE"); 
          if (userSessionID == NULL || strncmp(userSessionID, "sessionID=", 10) != 0) {
              printf("Content-type: text/html\r\n\r\n");
              printf("<p>Invalid session</p>");
              return 1;
          }
          userSessionID += 10; // 跳過 "sessionID=" 部分
        
          char *serverCSRFToken = getCSRFTokenFromRedis(userSessionID);
          fprintf(stderr, "Client CSRF Token: %s\n", csrfToken);
          fprintf(stderr, "Server CSRF Token: %s\n", serverCSRFToken);
        
          if (csrfToken == NULL || serverCSRFToken == NULL || strcmp(csrfToken, serverCSRFToken) != 0) {
              printf("Content-type: text/html\r\n\r\n");
              printf("<p>Invalid CSRF token</p>");
              return 1;
          }
        ```
        
        因此再次進行攻擊時頁面會出現不合法token的訊息，代表攻擊者沒辦法正確執行更改ID的請求(下面那行為目前登入者的cookie)
        
       ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dfee65e5655f01f59d1923bf84563a93.png)

        

## 作業八：XSS

1. **實作一個反射型的 XSS** 
    
    首先我依樣在vulnerable底下新增一個簡單的search.cgi，內容就是在網頁印出`query_srting`中的字就好，接著在url中的query放進簡單的<scrip>語法，例如`<script>alert('XSS');</script>` 讓原本應該輸出query_string的頁面多跳出一個警告，內容為XSS。
    
    在實作過程中需要先將url進行decode，url_decode實作參考網路
    

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
void url_decode(char *dest, const char *src) {
    char a, b;
    while (*src) 
    {
        if ((*src == '%') && ((a = src[1]) && (b = src[2])) && (isxdigit(a) && isxdigit(b))) 
        {
            if (a >= 'a') a -= 'a'-'A';
            if (a >= 'A') a -= ('A' - 10);
            else a -= '0';
            if (b >= 'a') b -= 'a'-'A';
            if (b >= 'A') b -= ('A' - 10);
            else b -= '0';
            *dest++ = 16*a + b;
            src+=3;
        } 
        else if (*src == '+') 
        {
            *dest++ = ' ';
            src++;
        } 
        else 
        {
            *dest++ = *src++;
        }
    }
    *dest++ = '\0';
}

```

最後在瀏覽器輸入

[`http://vulnerable.example.com/cgi-bin/search.cgi?q=test`](http://vulnerable.example.com/cgi-bin/search.cgi?q=test) 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/465c7f3b-d372-4fd4-8002-81406f70eac1/Untitled.png)

網頁成功輸出test

接下來測試在query_string植入script腳本

[`http://vulnerable.example.com/cgi-bin/search.cgi?q=<script>alert('XSS');</script>`](http://vulnerable.example.com/cgi-bin/search.cgi?q=%3Cscript%3Ealert(%27XSS%27);%3C/script%3E)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/c3d4eec3-c958-49f1-84f6-0f25c752e5ee/Untitled.png)

可以看到腳本成功被執行，攻擊成功。

1. **防禦他**
    
    防禦方法主要透過字串轉換，將可能執行腳本的語法轉換掉
    
    參考https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html
    從文章作法看起來是將query string中 
    
    Convert `&` to `&amp;`, 
    
    Convert `<` to `&lt;`,
    
     Convert `>` to `&gt;`,
    
     Convert `"` to `&quot;`, 
    
    Convert `'` to `&#x27;`
    
    將他轉換為安全的html語法，避免執行惡意腳本，程式碼實作如下
    
    ```c
    void xssPrevent(char *dest, const char *src, size_t size) {
        size_t i, j = 0;
        for (i = 0; i < size && src[i] != '\0'; i++) {
            switch (src[i]) {
                case '&':
                    j += snprintf(dest + j, size - j, "&amp;");
                    break;
                case '<':
                    j += snprintf(dest + j, size - j, "&lt;");
                    break;
                case '>':
                    j += snprintf(dest + j, size - j, "&gt;");
                    break;
                case '"':
                    j += snprintf(dest + j, size - j, "&quot;");
                    break;
                case '\'':
                    j += snprintf(dest + j, size - j, "&#x27;");
                    break;
                case '/':
                    j += snprintf(dest + j, size - j, "&#x2F;");
                    break;
                default:
                    if (j < size - 1) {
                        dest[j++] = src[i];
                    }
                    break;
            }
        }
        dest[j] = '\0';
    }
    ```
    
    轉換後再次測試
    
    [`http://vulnerable.example.com/cgi-bin/search.cgi?q=<script>alert('XSS');</script>`](http://vulnerable.example.com/cgi-bin/search.cgi?q=%3Cscript%3Ealert(%27XSS%27);%3C/script%3E)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/b651eec8-9f26-4930-98ca-31ab28d190d3/5342ca27-4730-4584-9f8f-5c07210a93f8.png)
    
    可以看到腳本沒被執行成功防禦。