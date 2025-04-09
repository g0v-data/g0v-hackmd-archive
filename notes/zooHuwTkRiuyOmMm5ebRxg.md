# g0v HackMD spam detection

## API tests

### Update other's note


https://hackmd.io/@hackmd-api/developer-portal/https%3A%2F%2Fhackmd.io%2F%40hackmd-api%2Fuser-notes-api#Update-a-note

```
curl -X PATCH \
  -H 'Authorization: Bearer <token>' \
     'https://g0v.hackmd.io/api/openAPI/v1/notes/pLAzxlEoT3KjdxLwVgqzXA' \
--data '{
   "readPermission": "signed_in"
}'
```

--> Forbidden，不能修改他人 note
    (UI 上也無法)

