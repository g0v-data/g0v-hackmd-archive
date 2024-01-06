---
tags: bridge
title: Matterbridge Slack bot setup
---
# Matterbridge Slack bot setup

Due to changes in Slack app management interface, please refer to https://github.com/42wim/matterbridge/wiki/Slack-bot-setup for the latest instructions to setup a matterbridge slack bot.

## Old method (not working any more)

> The following work doesn't work any more.  Please use the setup method in https://github.com/42wim/matterbridge/wiki/Slack-bot-setup

How to configure documents, based on [Slack bot setup](https://github.com/42wim/matterbridge/wiki/Slack-bot-setup), using https://g0v-tw.slack.com as an example.

1. Go to Manage App page: https://g0v-tw.slack.com/apps/manage

   You need to log in with an account that has administrative permissions over the Slack Workspace (server) that you want to setup Matterbridge.

   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fed1947c046cd947c3cb794438e91457.png)

2. :warning: **Don't** click on the "Create App" button.  Use [this link](https://api.slack.com/apps?new_classic_app=1) to create a classic app.  Set **App Name** to "Matterbridge" and choose the workspace you want to setup Matterbridge as the **Development Slack Workspace**.

3. Go to https://g0v-tw.slack.com/apps/manage, find the Matterbridge App you just created, click on it and click **View in App Directory**.  Add a Bot User.  You can name the bot "HelloWorld bot" or any name so that people in your workspace knows it's a bot.

   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65de4b4062cef59b97fd5619ae9675e4.png)

4. Go back to [App configure page](https://api.slack.com/apps)

   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5bb2870906195438f6e5cfab2fbdc6cf.png)

   to configure the App.  Save the **Client ID** and **Client secret** to somewhere for later use.


5. Set App scopes as follows

   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f34a6f80660ea4c1dfcd5ae1185f977b.png)
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee2ef1609b69c878f24c45de7e6cb243.png)
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a83b44d91c1f2e33750b8973746518ad.png)

6. The next step is to select user token scopes

   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e796e66ee1d7f601dc7173df07178cf9.png)


   Selected the following bot token scopes:

   * bot
   * channels:write
   * chat:write:bot
   * chat:write:user
   * im:*
   * mpim:*
   * users.profile:read

   Selected bot user: None selected
    
7. Click **Yes, migrate my app**

   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f6c1542d0d5806790dd3302735d48ed3.png)

8. Once the App has been installed the top of the OAuth & Permissions page will show two tokens: an **OAuth Access Token** starting with xoxp-... and a **Bot User OAuth Access Token** starting with xoxb-.... You will need to use the second in your Matterbridge configuration.

---

Note that [RTM](https://api.slack.com/rtm) API is no longer supported.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1005eb47f8c168481e5db18f94ee3640.png)
