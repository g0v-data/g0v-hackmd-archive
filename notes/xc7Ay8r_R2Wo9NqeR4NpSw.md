---
tags: g0vernance
---

slack admin 能做和不能做的事
=========================

為了方便討論 slack 治理機制需要如何限制 admin ，這邊想要條列在技術上 admin 能做到和不能做到的事情，以便知道需要在哪些能做到的事需要多加限制，以及當有人疑慮時，可以用已測試過確認 admin 做不到來做澄清。

本共筆分三區，「才能做」寫 admin 在技術上可以做到的事（但我們治理機制不一定允許 admin 做）、「做不到」寫 admin 在 slack 現有機制做不到，而「疑問」則是放各種還未經證實的，可以請 admin 再測試確認做的到或做不到。


才能做
-----
- 對 slack
    - 進行各種設定（可見下面 slack 設定列表）
- 對 user
    - 查詢到 user 的 email
    - 將 user 停權
    - 查到 user 的登入時間、IP 和裝置種類（付費功能）
    - 邀請 email 加入 slack
    - 建立邀請連結
    - 看使用者在哪一天變 active 或 inactive (7天未動作會變 inactive)
- 對頻道
    - 修改頻道名稱
    - 封存頻道（仍可解除封存）
    - 刪除頻道（不留下頻道對話紀錄）
- 對 App
    - 安裝/反安裝 App
    - 審核是否要安裝 App
- 其他
    - 當官方提供 30 天免費 Pro Workspace 時，可以啟用試用
    - 匯出所有公開對話紀錄（從2015年開始）

做不到
-----
- 對 user
    - 無法修改使用者密碼
    - 無法變身成使用者
    - 無法得到使用者私訊內容
- 對頻道
    - 無法知道有哪些 private 頻道

風險
---
- admin行使權限沒有紀錄
- 其中一個admin可以將其他所有admin剔除（這在大部分的聊天平台都有這類的問題。）-->確保所有對話紀錄都有備份，而且不只單一備份

疑問
----
* Q1: 可否就某先權限對某個admin做限制？
* Q2: 能否將所有的對話紀錄做Backup？


slack 設定列表
-------------
https://slack.com/intl/zh-tw/help/articles/201314026-Slack-%E5%90%84%E8%A7%92%E8%89%B2%E7%9A%84%E6%AC%8A%E9%99%90
這個表會不會比較清楚？
但可能目前有些設定是跟預設不同？

## Settings
Joining This Workspace
Choose how people join your workspace: by accepting an email invitation or signing up with an email address from an approved domain. If you enable the setting to let people with an email address on an approved domain join automatically, Slack will generate a link that anyone with an approved email address can use to confirm their email and sign up.

Workspace Language
Set the language for your workspace. This affects system notifications, Slackbot messages, and sign-up emails. Your workspace language is currently set to: English (US)

Default Channels
Choose the channels new members will automatically be added to (in addition to #general).

Display Name Guidelines
Explain the guidelines you want members to follow when they set their display names.

Name Display
If you’d like, Slack can show your members’ full names instead of their shorter display names.

Email Display
Choose whether to display members’ email addresses in their Slack profiles.

Pronouns Display
Choose whether to display members' pronouns (ex: they/them/theirs) in their Slack profiles.

Do Not Disturb
Set default Do Not Disturb hours for members of your workspace.

Channel Join & Leave Messages
If you’d like, Slack can let the channel know whenever someone joins or leaves.

Calls
Choose how members make calls in Slack. You can use Slack itself or a third-party calling app.

Mobile Usage
Choose whether members are prompted to use the Slack mobile app.

Message history
Historical messages help members find info they need to get work done. In channels shared with other organizations, your retention settings will only apply to messages from members of your organization. Learn more

File history
By default, Slack keeps all your files for the lifetime of your workspace. If you’d like, you can have them deleted after a set amount of time. Note that this affects all files — including images, docs, Slack posts, clips and more.


Workspace Icon
Your workspace icon is used in the desktop and mobile apps, where it’s useful in helping you quickly identify this workspace.


Workspace Name & URL
Your workspace name is g0v and your URL is https://g0v-tw.slack.com.


## Permissions
Messaging
Set who can use @everyone, @channel, and @here.

Invitations
By default, any member can invite new people to your workspace. If you’d like, you can change this so invitations require admin approval.
Channel Management
Choose who can create, archive, remove members, and manage posting permissions in channels.

Slack Connect DiscoverabilityCOMING SOON
Choose who can see members’ names and that they use Slack before connecting. Learn more

Slack Connect ChannelsPRO
Slack Connect enables members of your organization to work with partners, vendors, and other third parties in the same channel. Learn more

File uploads for Slack ConnectPRO
Choose whether people can upload files from their device — or share files already uploaded in Slack — to channels and conversations that include people from outside g0v. This permission does not control audio and video clip sharing. Learn more

Slack Connect for direct messages
Allow members of your organization to start DMs with people from companies not already connected to g0v. Learn more

User GroupsPRO
Set who can create and manage user groups.

Message Editing & Deletion
Choose when to allow message editing and deletion.

Profile CustomizationPRO
Choose who can add new fields to your workspace’s profile.

Workspace Analytics
Choose who can view the Analytics page.

Custom Emoji
Choose who can manage custom emoji ()

Slackbot Responses
Choose who can manage Slackbot responses for your workspace.

Gateways
Slack no longer supports connecting through XMPP or IRC clients. Learn more

Workflow creation
Choose who can create workflows with Workflow Builder in your workspace.

Webhooks in Workflow Builder
Allow external apps or services to start and send data to workflows.

Downloads of workflow form responses
Allow downloads of responses to Workflow Builder forms as a CSV file.

Workflow Builder steps from apps
Allow apps to add steps to Workflow Builder.

Channel email addressesPRO
Choose who can get email addresses for channels in your workspace.

Apps & Custom Integrations
Manage permissions for apps and integrations in the App Directory

## Authentication
Slack supports a number of single sign-on (SSO) services. Get started with setting up your workspace’s SSO below, or learn more about using single sign-on with Slack.

Configure an authentication methodPRO
Google Apps authentication
Upgrade to enable signing in with a Google account.
SAML authentication
Azure, Okta, and OneLogin, or your custom SAML 2.0 solution is only available on the Business+ plan.
Workspace-wide two-factor authentication
Require each user to configure and use two-factor authentication for signing in.

Session DurationPRO
Once logged in, users will remain signed in until they explicitly sign out. This setting allows you to force users to log in after a certain amount of time has elapsed since their last login.

Forced Password Reset
You can force a reset of all passwords for all members in your workspace. Each member will receive a message from Slackbot telling them that you’ve triggered the reset, and will then receive a password reset link via email.

Automatically Open This Workspace for Members
Admins can configure Slack for Windows, Mac or Linux to automatically open a specific workspace for members and allow them to sign in without having to enter the workspace URL. Download the “slacktoken” file and place it in a user’s download directory.

## Attachments
Slack will automatically display previews for links when possible.

Blocked previews
To block previews from a specific link or domain for your entire workspace, click the  to the left of the preview inside Slack. You’ll then have an option to block all previews from that domain.

Once a domain is blocked, you’ll see it listed here.
