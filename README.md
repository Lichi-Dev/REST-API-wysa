# REST API wysa

The REST API to the Wysa sleep is described below.

## User Schema

    user {
    nickname: { type: String, required: true, unique: true },
    password: { type: String, required: true },
    formdata: {
      sleepchange: { type: Array, default: [] },
      sleepstruggle: { type: String, default: "" }}
    }

## Create User

### Request

`POST /api/user/signup`
```
POST http://localhost:5000/api/user/signup 
Content-Type: application/json 

{"nickname":"rahul", "password":"rahul123"}
```

### Response
```
{
  "user": {
    "nickname": "rahul",
    "password": "$2b$10$0sCF1lO8dyxQuLtip5GKqOWoy8xjizSNcdW9002qa7al6mlfMAdYC",
    "_id": "653f6f88d571ba405d9e8898",
    "__v": 0
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuaWNrbmFtZSI6InJhaHVsIiwiaWQiOiI2NTNmNmY4OGQ1NzFiYTQwNWQ5ZTg4OTgiLCJpYXQiOjE2OTg2NTYxMzZ9.dvxfyXVMY9Dq06AIbthTEGxyTwELv_pbzK50oa-0r6U",
  "message": "User created successfully"
}
```

## Login User

### Request

`POST /api/user/login`
```
POST http://localhost:5000/api/user/login
Content-Type: application/json

{
"nickname":"rahul", "password":"rahul123"
}
```

### Response

   ```
{
  "user": {
    "_id": "653f6f88d571ba405d9e8898",
    "nickname": "rahul",
    "password": "$2b$10$0sCF1lO8dyxQuLtip5GKqOWoy8xjizSNcdW9002qa7al6mlfMAdYC",
    "__v": 0
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuaWNrbmFtZSI6InJhaHVsIiwiaWQiOiI2NTNmNmY4OGQ1NzFiYTQwNWQ5ZTg4OTgiLCJpYXQiOjE2OTg2NTYzOTB9.ldN7pVGnxKpVQyREXgL7lAkMLqawGno_rEcOfwI1rOw",
  "message": "User logged in successfully"
}
```

## Get all users

### Request

`GET /api/user/all`

    GET http://localhost:5000/api/user/all

### Response

  ```
{
  "users": [
    {
      "_id": "653ea449383cc0292d9ee54c",
      "nickname": "bb",
      "password": "$2b$10$JFvNAYqY.gE9Q.2d4oTa/uayV0XYQnE4sJszo1TRK/51aYFcwiaPK",
      "__v": 0,
      "formdata": {
        "sleepchange": [
          "I would sleep through the night"
        ],
        "sleepstruggle": "More than 8 weeks"
      }
    },
    {
      "_id": "653ea521383cc0292d9ee563",
      "nickname": "bb123",
      "password": "$2b$10$GDytsJdN25VHhPSXQ8prHOoOHL183ibnTmFOaGzIF3vD2BsZV7o6m",
      "__v": 0
    },
    {
      "_id": "653eaa1a8374955d6493e2ee",
      "nickname": "appu",
      "password": "$2b$10$rd05iibSDNPEHhmdlrnJ3Obgxu6JrF9qDusNuys6KTzCL5.luYFZq",
      "__v": 0,
      "formdata": {
        "sleepchange": "2week",
        "sleepstruggle": "5week"
      }
    },
    {
      "_id": "653eb133a8433b4a0ebe4e56",
      "nickname": "redskull",
      "password": "$2b$10$41YuNx1fmP7aDCRtInXAVuVpjvoHpvoPuHzW7F8p.Ut2zdEnKB3rW",
      "__v": 0,
      "formdata": {
        "sleepchange": [
          "I'd wake up on time, refreshed"
        ],
        "sleepstruggle": "More than 8 weeks"
      }
    },
    {
      "_id": "653f39cd3fd7b52e8351b0d0",
      "nickname": "justin",
      "password": "$2b$10$Yu9rZrLGa4AG1ft3AUN7r.8rOsEmTRHs1ncikng1fO/VPzVwpUD2e",
      "__v": 0,
      "formdata": {
        "sleepchange": [
          "I would go to sleep easily"
        ],
        "sleepstruggle": "2 to 8 weeks"
      }
    },
    {
      "_id": "653f6f88d571ba405d9e8898",
      "nickname": "rahul",
      "password": "$2b$10$0sCF1lO8dyxQuLtip5GKqOWoy8xjizSNcdW9002qa7al6mlfMAdYC",
      "__v": 0
    }
  ],
  "message": "All Users fetched successfully"
}
```

## Get a particular user

### Request

`GET /api/user/id`

    GET http://localhost:5000/api/user/653f6f88d571ba405d9e8898

### Response
```
{
  "user": {
    "_id": "653f6f88d571ba405d9e8898",
    "nickname": "rahul",
    "password": "$2b$10$0sCF1lO8dyxQuLtip5GKqOWoy8xjizSNcdW9002qa7al6mlfMAdYC",
    "__v": 0
  },
  "message": "User fetched successfully"
}
```
## Add sleep change data

### Request

`PATCH /api/user/sleepchange/id`

    PATCH http://localhost:5000/api/user/sleepchange/653f6f88d571ba405d9e8898
    Content-Type: application/json
    
    {
     "sleepchange":["I would sleep through the night","I'd wake up on time, refreshed"]
    }

### Response

    {
      "user": {
        "_id": "653f6f88d571ba405d9e8898",
        "nickname": "rahul",
        "password": "$2b$10$0sCF1lO8dyxQuLtip5GKqOWoy8xjizSNcdW9002qa7al6mlfMAdYC",
        "__v": 0,
        "formdata": {
          "sleepchange": [
            "I would sleep through the night",
            "I'd wake up on time, refreshed"
          ]
        }
      },
      "message": "Submitted"
    }

## Add sleep struggle data

### Request

`PATCH /api/user/sleepstruggle/id`

    PATCH http://localhost:5000/api/user/sleepstruggle/653f6f88d571ba405d9e8898
    Content-Type: application/json
    
    {
     "sleepstruggle":"More than 8 weeks"
    }

### Response

    {
      "user": {
        "_id": "653f6f88d571ba405d9e8898",
        "nickname": "rahul",
        "password": "$2b$10$0sCF1lO8dyxQuLtip5GKqOWoy8xjizSNcdW9002qa7al6mlfMAdYC",
        "__v": 0,
        "formdata": {
          "sleepchange": [
            "I would sleep through the night",
            "I'd wake up on time, refreshed"
          ],
          "sleepstruggle": "More than 8 weeks"
        }
      },
      "message": "Submitted"
    }

    HTTP/1.1 204 No Content
    Date: Thu, 24 Feb 2011 12:36:33 GMT
    Status: 204 No Content
    Connection: close

