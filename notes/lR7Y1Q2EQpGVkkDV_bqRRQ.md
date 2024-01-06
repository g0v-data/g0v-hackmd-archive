# Epic-slack-app
Retrieve selected conversations from slack, transfer these conversation to a prefered data objects and build api for others to retrieve the data.

## Dependencies
This app uses the following dependencies:

* dotenv
* @slack/bolt
* @slack/web-api
* fs
* http
## Installation
Clone the repository: git clone https://github.com/[USERNAME]/[REPOSITORY_NAME].git
Install dependencies: npm install
## Configuration
This app uses environment variables to store sensitive information. Create a .env file in the root directory of the project and add the following:


```makefile
SLACK_BOT_TOKEN=your_slack_bot_token_here
SLACK_SIGNING_SECRET=your_slack_signing_secret_here
```
## Usage
To run the app, use the command npm start.

## Functions
### selectConversation(name)
This function filters conversations by keywords and emojis and saves them to JSON files.

### Variables
This app uses the following variables:

* wordFilter: an array of keywords to filter conversations by.
* emojiFilter: an array of emojis to filter conversations by.
* userAddressAndId: a JSON file containing the user addresses and IDs.
* userList: a JSON file containing a list of users.
* userSelectedConversationObject: a JSON file containing the selected conversations.
* tsSelectedJson: a JSON file containing the selected conversations by timestamp.