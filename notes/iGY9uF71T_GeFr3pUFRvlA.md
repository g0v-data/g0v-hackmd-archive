---
title: "鄉民關心你 - API"
tags: kuansim,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/z0XwS5cmyg9)

### ==本內容已被標註為過時或未維護。如果三十日內沒有更新，將會被移除。原有內容仍可在== ==[https://github.com/g0v-data/hackpad-backup-g0v](https://github.com/g0v-data/hackpad-backup-g0v)== ==找到。==


Version: 0.1

## Background

The backend is custom pgrest and the api is compatable with [https://support.mongolab.com/entries/20433053-rest-api-for-mongodb](https://support.mongolab.com/entries/20433053-rest-api-for-mongodb)

this api is possibled changed by implemented within json-ld ([https://www.youtube.com/watch?v=tRTD2W4W8G4](https://www.youtube.com/watch?v=tRTD2W4W8G4))

## Auth

git:master: unsupported
git:develop: support

GET /auth/facebook # authenticated by facebook account. (default enabled)
GET /me                   # get authenticatied user profile
GET /logout              # logout, clear session
GET /logged             # return true if user is authenticatied otherwise return false

## User

git:master: unsupported
git:develop: support

PUT /collections/users/{id}               # update a user
GET /collections/users                     # get all user
GET /collections/users/{id}               # get a user

- **_id**: user id
- **username**: The name of this user, suitable for display.
- **name**:
    - **familyName:**The family name of this user, or "last name" in most Western languages.
    - **givenName:**The given name of this user, or "first name" in most Western languages.
    - **middleName:** The middle name of this user.
- **display_name**: the name a user want to display in the system
- **photos**: array

## User Preferences


GET /collection/user_prefs/{user id} [#get](https://g0v.hackpad.tw/ep/search/?q=%23get&via=z0XwS5cmyg9) a user preference
PUT /collection/user_prefs/{user id} [#get](https://g0v.hackpad.tw/ep/search/?q=%23get&via=z0XwS5cmyg9) a user preference

- _id: object id
- **user_id:** user id
- **prefer_poston:** which system user prefer to use for posting a message (twitter/facebook/kunasim)
- **subscriptions**
    - **tags:** subscribed tags

## Bookmarked Items


POST /collections/bookmarks/                             # create a bookmarked item
GET /collections/bookmarks/                               # get all bookmarked items
GET /collections/bookmarks/{id}                          # get a bookmarked item
PUT /collections/bookmarks/{id}                          # update a bookmarked item
DELETE /collections/bookmarks/{id}                   # delete a bookmarked item (won't delete resolved items, e.x article)

- **_id:** Item id
- **normal_url:** The original url for the added item
- **resolved_id:** A unique identifier for the resolved item
- **resolved_type:** The type resolved item belongs to
- **date_resolved:** The date the item was resolved
- **date_happend:** 事件發生的時間
- **author:**author
- **tags:** Array of tags
- **messages:** associated messages
- **in_inbox:** false or true

### Articles (belongs to resolved items)


POST /articles                  # create a article
GET /articles/{article id}    # get a article

- **id:** article id
- **title:** article title
- **permanent_url:** permanent url of original article.
- **summary**: article summary
- **fulltext**: aticle full content
- **date_published**: The date the item was published
- **sources:** Array of sources where the article from
- **has_images:** 0: no image; 1: has an image in the body of the article; 2: is an image
- **images**: Array of image data
- **has_videos:** 0: no video; 1: has a video in the body of the article; 2: is a video
- **videos**: Array of video data
- **has_diffs:** 0: no; 1: has multiple versions
- **diffs:** Array of changes if this article has multiple version

### WebPages  (belongs to resolved items)


POST /webpages                 # create a webpages
GET /webpages/{item_id}    # get a webpages

- **id**: web page id
- **title**: article title
- **summary:** summary of web page
- **permanent_url:** permanent url of original article.
- **date_published:** The date the item was published
- **domain**: domain of url
- **has_images:** 0: no image; 1: has an image in the body of the article; 2: is an image
- **images**: Array of image data
- **has_videos:** 0: no video; 1: has a video in the body of the article; 2: is a video
- **videos**: Array of video data

### Tags


POST /collections/tags                         # create a tag
GET   /collections/tags/{tag name}       # get a tag by name
GET   /collections/tags/{id}                   # get a tag by id

- **id:** tag id
- **name:** tag name
- **authors:** Array of authors
- **is_issue:** return  true if at least a user think this tag is an issue title.

## Issues

Issue (爭議)

GET /collections/issues
GET /collections/issues/{id}

- **tag_id:**
- **bookmarked_items**
- **ongoing_actions**
- **watcher:**

## Positions


GET /collections/positions

- **_id:** object id
- **issue: **
- **title**: position title
- **tags**: ....
- **supportors:** \[\]
- **againstors**: \[\]

