# 聯絡人 Addressbook
## 概述
---
## API文件：AddressBookController

### `/newfriends/All`
- **HTTP Method**: `Get`
- **Description**: 所有的會員列表(只有公司名，姓名，產業別)，用於測試新增好友。
- **Business Logic**:
  - Validates if the username is already in use through `UserService.registerUser`.
  - Encrypts the password using `BCrypt` (encryption located in `encryptPassword` method within `UserService`).
- **Response**:
  - **Success**: Returns `201` with `UserResponse` (contains `id` and `username`).
  - **Failure**: Returns error message with `400` if username already exists (`UserAlreadyExistsException`).