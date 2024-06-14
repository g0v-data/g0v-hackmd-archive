# 編譯簡介

1. 用 sqlite3 指令新增一個 DB
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/e7b492b8-fe98-4abd-8eb2-9a6af399cfbf/Untitled.png)
    
2. 開出一個 TABLE，包含一個 id 欄位以及一個 content 
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/e395dcfe-42d9-4216-8f31-7c5a2377e9ed/Untitled.png)
    
3. 下載 `sqlite-amalgamation`接著在解壓縮
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/859a5df5-3123-4db3-be43-2c1258c17e10/Untitled.png)
    
4. 編譯出 `libsqlite3.a`
    
    由於.a檔靜態庫是由.o檔組成，因此可以用ar指令將文件打包成.a靜態庫
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/adaf3f45-97ad-42c6-9e56-7ed0a6682d81/Untitled.png)
    
5. 用 C 寫一個程式使用 `libsqlite3.a` 
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/b8d0a5bc-3639-43b9-958b-29d7e129e788/Untitled.png)
    
    先寫一個基本的開db測試，然後寫一個makfile嘗試讓他自動編譯
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/bd76aaed-8663-424e-a3ff-4cc8cf8ab0dd/Untitled.png)
    
6. C 寫的程式往 db 內插入資料 `INSERT INTO my_table (content) VALUES ('This is a test content');`
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cf8a3fab-80e0-4707-9926-7617fe831412/b8403de8-f5b5-4051-904b-c5459add363c/Untitled.png)
    
7. 展示資料已經被插入 DB 內 (在 sqlite3 指令中操作)
    
    輸入指令 `sqlite3 test.db` 進到資料庫內
    
    再輸入`SELECT * FROM my_table;` 就可看到剛剛insert進去的資料