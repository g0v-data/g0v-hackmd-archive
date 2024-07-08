---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240708 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::


## Talk


## LINE bot long response handling

票：https://github.com/cofacts/rumors-line-bot/blob/master/src/webhook/handlers/singleUserHandler.ts#L78

Details changed
- No need to transfer progress; build helper function and pass in each handler
- Just record last reply token is sufficient

