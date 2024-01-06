---
tags: cofacts
---

# Cofacts chatbot error analysis 2023/01/21 ~

## Operation / code changes

- 2023/1/21: Update API server
    - https://github.com/cofacts/rumors-api/releases/tag/release%2F20230121
- 2023/2/3 2 a.m.: Update LINE bot, API and site server
    - Changes log format so that each conversation emits one line of log instead of multiple lines
    - Revives group chat
    - Deploys API and website changes tested in https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FiGqCnbuoQfKlZLTNEyM3dw
- 2023/2/7 2 a.m.: Try to rollback API change on 1/21 by reverting to an image 8 weeks ago (should be https://github.com/cofacts/rumors-api/releases/tag/release%2F20221213 )
    - Error rate did not drop, so it's not due to 1/21 code release ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3d3729acfcc9d2076a7e9ea27cdf0df.png)
- Error went away on 2/11 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f2d50cd8f0d213058968e88eede9eed6.png)


## Linode server load <> LINE chatbot errors

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8b5fd4bcec6c71dd8b67302fc5906264.png)

- Upper: linode CPU load (%)
- Lower: chatbot errors (request timeout)
- No significant surge in CPU, but error happens every day starting from 1/21

Overall CPU load in 30 days
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c6818d3d8c133bf6fa90d2fe3c08407.png)

Out-going network spike on 1/21
- Reason: unknown

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3a7b94696fd6380147cec5fc6d19e627.png)


## Nginx request count <> LINE chatbot errors

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f4db35220253b11dc447a4ea8c3a1321.png)

- Upper: nginx (includes HTTPs requests to API, chatbot, website,... etc)
- Lower: chatbot errors (request timeout)
- No significant surge in nginx, but error happens every day starting from 1/21

## Nginx log <> LINE chatbot errors

## Chatbot log <> LINE chatbot errors

## Rollbar errors <> LINE chatbot errors


