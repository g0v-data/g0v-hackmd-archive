# Bitnami Redmine

メールサーバーでメールを交換実行の手順

Bitnami Redmineインストール
---
- Step1. Bitnami 4.1.0-8をダウンロードする
    ダウンロードURI: https://bitnami.com/stack/redmine/installer
    
- Step2. インストールフロー
    
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a0f602c0625a35d63c7e0352c331d095)
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c4b2c51805f9591c7e12f20d78c60855)
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7800101b9c4a0ecee8e5fb8b614f2b39)
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_81ba7114fff8e2a1bf3705f502d55486)
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_83eb242a5423a7fef0d29094df9ac386)
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b82bbf4f4771fc7647cbd77278280555)



    アプリケーションはデフォルトパスにインストールする:
    > C:\Bitnami\APPNAME-VERSION

Redmine設定
---

* REST APIによるWebサービスを有効にする
    
    設定方法
    >管理-> 設定 -> API の画面に**RESTによるWebサービスを有効にする**のオプションをクリックする
    
    JAVA使用RedmineのlibaryにAPI keyをもらいます
    >
    
* メールサーバーからRedmineにチケットを作成するの設定
    
    Incomingメール有効にするし、redmineにログインと次の手順を実行する。
    >管理 -> 設定 -> 受信メール.
    
    **APIキー** をクリックと **受信メール用のWebサービスを有効にする**をチェック、それから保存をクリックする。
    
    Redmineは受信メールを自動に処理してメールのcontentをticketに変換するように設定できます
    メールサーバーからメールをもらいように次のコマンドでフォルダーにバッチファイルを作成します
    ```
    @echo off
    CALL C:\Bitnami\REDMIN~1.0-8\scripts\setenv.bat
    cd C:\Bitnami\redmine-4.1.0-8\apps\redmine\htdocs
    START "Bitnami Redmine Stack Environment" cmd /c "bundle exec rake redmine:email:receive_pop3 RAILS_ENV='production' host=outlook.office365.com port=995 ssl=1 username=your_mail password=your_password allow_override=all unknown_user=accept no_permission_check=1"
    ```
    
    **your_mail** と **your_password**を設定の正しい情報に設定えることを忘れない
    そしでバッチファイルを実行するタスクを作成する。
* [Example email template](/)

    次のメールcontentにプロジェクトは特定のプロジェクトに必要な設定する。
    >Mail content<br>
    優先度: Choose an item.
    プロジェクト: 
    トラッカー: Choose an item.
    担当者: 
    開始日:Click or tap to enter a date.
    期日:Click or tap to enter a date.
    
    [Outlookテンプレート](https://bit.ly/3cG33Ir)
    
Install plugins
---    
* [XLSX format issue exporter](/)

    ```
    public class SampleRecord {

        @XlsColumn(columnName="No.")
        private int id;

        @XlsColumn(columnName="名前")
        private String name;

        @XlsMapColumns(previousColumnName="名前", nextColumnName="備考")
        private Map<String, String> attendedMap;

        @XlsColumn(columnName="備考")
        private String comment;

    }
    ```
    
    そしてRedmineをrestart

Other tips
---    
* [Command error](/)

    If batch file can't work smoothly, copy the following command on Bitnami cmd.
    **C:\Bitnami\redmine-4.1.0-8** go to Bitnami path and open **use_redmine.bat**
    ```
    gem install rake
    ```
    
###### tags: `Bitnami` `Redmine` `Exchange mail`

<style>

html, body, .ui-content {
    background-color: #333;
    color: #ddd;
}

.markdown-body h1,
.markdown-body h2,
.markdown-body h3,
.markdown-body h4,
.markdown-body h5,
.markdown-body h6 {
    color: #ddd;
}

.markdown-body h1,
.markdown-body h2 {
    border-bottom-color: #ffffff69;
}

.markdown-body h1 .octicon-link,
.markdown-body h2 .octicon-link,
.markdown-body h3 .octicon-link,
.markdown-body h4 .octicon-link,
.markdown-body h5 .octicon-link,
.markdown-body h6 .octicon-link {
    color: #fff;
}

.markdown-body img {
    background-color: transparent;
}

.ui-toc-dropdown .nav>.active:focus>a, .ui-toc-dropdown .nav>.active:hover>a, .ui-toc-dropdown .nav>.active>a {
    color: white;
    border-left: 2px solid white;
}

.expand-toggle:hover, 
.expand-toggle:focus, 
.back-to-top:hover, 
.back-to-top:focus, 
.go-to-bottom:hover, 
.go-to-bottom:focus {
    color: white;
}


.ui-toc-dropdown {
    background-color: #333;
}

.ui-toc-label.btn {
    background-color: #191919;
    color: white;
}

.ui-toc-dropdown .nav>li>a:focus, 
.ui-toc-dropdown .nav>li>a:hover {
    color: white;
    border-left: 1px solid white;
}

.markdown-body blockquote {
    color: #bcbcbc;
}

.markdown-body table tr {
    background-color: #5f5f5f;
}

.markdown-body table tr:nth-child(2n) {
    background-color: #4f4f4f;
}

.markdown-body code,
.markdown-body tt {
    color: #eee;
    background-color: rgba(230, 230, 230, 0.36);
}

a,
.open-files-container li.selected a {
    color: #5EB7E0;
}

</style>
