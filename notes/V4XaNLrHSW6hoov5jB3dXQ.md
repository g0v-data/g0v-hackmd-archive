# Bitnami Redmine

[日文版](https://g0v.hackmd.io/Wz4IDLx1SlmMUlc4xlDHPg?view)

Bitnami Redmineの実装手順

Bitnamiインストール
---
- [Getting Start](/)

    In this post I'll describe how to install Redmine on Windows10, and configure it to receive email from Exchange server.<br> 
Dowload Bitnami: https://bitnami.com/stack/wordpress/installer<br>
The application will be installed on the following default path:
    > C:\Bitnami\APPNAME-VERSION

Outgoing (SMTP) Server Settings
---
- [Configure SMTP For Outgoing Emails](/)

    Email settings can be configured following path: 
  >../apps/redmine/htdocs/config/configuration.yml
    
   The file includes sample configuration settings for most common scenarios
   
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2f21c4e9b802ed120bc6374f0d030fc1)
    
    
    Remember to update the **address, port, user_name. password** variables with the correct credentials for the Gmail account you plan to use.
    
* [Sending email notifications from Redmine](/)

    To configure email notifications login to redmine and folloing steps.
    >Administration -> Email notifications -> Emission email address
     
    Set the field to the email address that you want notifications to be sent from.
    Writing down anything you want to fill in the **Email Header and Email footer**.
    In the outgoing setting end you can click **Save button and Send a test mail** to your provider mail.
    
Convert Incoming Email To Issues
---    
* [Receiving email into Redmine from Exchange Server(1/2)](/)

    To enable incoming email login to redmine and following the steps: 
    >Administration -> Incoming emails.

    Click the **Generate a key** link and check the **Enable WS for incoming emails** checkbox, then      click Save.
    
* [Receiving email into Redmine from Exchange Server(2/2)](/)

    Redmine can be configured to automatically process incoming email messages and convert them to     issues. To do this, it is necessary to configure Redmine to connect to an IMAP or POP3 account periodically, check incoming messages and convert those containing Redmine keywords into issues. To do this, create a scheduled task and follow the following steps in Bitnami:
    >Project -> Choose your project -> Issue
    
    And then fill the **Tracker, Subject, Status, Priority** whatever you want, then click save.
    To receive email from Exchange, create a batch file in the folder **C:\Program Files\BitNami Redmine Stack\apps\redmine** with the following commands:
    ```
    @echo off
    CALL C:\Bitnami\REDMIN~1.0-8\scripts\setenv.bat
    cd C:\Bitnami\redmine-4.1.0-8\apps\redmine\htdocs
    START "Bitnami Redmine Stack Environment" cmd /k "bundle exec rake redmine:email:receive_pop3 RAILS_ENV='production' host=mail server port=mail server port ssl=1 username=your_mail password=your_password allow_override=project,tracker,priority unknown_user=accept no_permission_check=1"

    ```
    Remembering to replace **mail server, mail server port, your_mail and your_password** with the correct information for your mail provider
    Then create a scheduled task to execute the batch file every 5 minutes (or however often you like).
* [Example email template](/)

    The following email content, **Project** is the required fields for your specific project
    >This is a new issue that will be added to project foo. Here we have the issue description [...] 
Project: test

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
