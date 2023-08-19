<p align="center"><a href="https://mnotify.com" target="_blank"><img src="https://sms.velstack.com/build/images/velstack/logo-white.png" width="200" alt="Laravel Logo"></a></p>

<p align="center">
 <a href="https://packagist.org/packages/velstack/mnotify"><img alt="Packagist Version (custom server)" src="https://img.shields.io/packagist/v/velstack/mnotify?label=Version"></a>
<a href="https://packagist.org/packages/velstack/mnotify"><img src="https://img.shields.io/github/license/sammyfort/mNotify-laravel"></a>

 

</p>
 

## [Velstack SMS](https://www.sms.velstack.com/) API documentation.

## Introduction

Welcome to the Velstack Developer Documentation
where you’ll learn how to build amazing communication experiences with the Velstack API.

Base url

```bash
  https://sms.velstack.com
```

## Get Started


Velstack APIs was made with REST and uses http verbs such as `GET, POST, PATCH/PUT, DELETE` Every request to our endpoints must be restful..

 ## Authorization

Velstack uses API keys to authenticate requests. You can [login](https://www.sms.velstack.com/) to get your API key. Every request made to this endpoint requires API key to the server as a Header parameter:.

## Responses

All http responses are in json format that's every request to our endpoint must include a header of 'Accept:application/json'.


## Quick SMS

```bash

  curl https://sms.velstack.com/api/messaging/quick/sms
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -d '{ sender : "Velstack", recipient: "0205550368", message: "sent from the velstack api" }'
  -X POST
 
```

#### `Response`
```json
 {
  "status": true,
  "code": 200,
  "message": "Message sent Successfully",
  "data": {
    "summary": {
      "message_id": "550517f1-3810-4d17-bfdb-f2571d05c07c",
      "type": "Quick SMS",
      "message": "sent from the velstack api",
      "sender": "VELSTACK",
      "total_contacts": 1,
      "recipients": [
        "0205550368"
      ],
      "credit_used": 1,
      "credit_left": "47.00"
    }
  }
}
```
#### `In case of error`
```json
{
  "status": false,
  "message": "Insufficient to complete this message",
  "code": 403
}
```

```json
{
  "status": false,
  "message": "Service unavailable",
  "code": 503
}
```



## Group SMS

```bash

  curl https://sms.velstack.com/api/messaging/group/sms
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -d '{ sender : "Velstack", group_id: "a4a8da21-88f8-4395-a9df-f859f22c2dfa", message: "sent from the velstack api" }'
  -X POST
 
```

#### `Response`
```json
 {
  "status": true,
  "code": 200,
  "message": "Message sent Successfully",
  "data": {
    "summary": {
      "message_id": "a2500c66-5d60-4f5a-8503-2105151afdca",
      "type": "Group SMS",
      "message": "group sms sent from the velstack api",
      "sender": "VELSTACK",
      "total_contacts": 1,
      "recipients": [
        "0205550368"
      ],
      "credit_used": 1,
      "credit_left": 1
    }
  }
}
```
#### `In case of error`
```json
{
  "status": false,
  "message": "Insufficient to complete this message",
  "code": 403
}
```

```json
{
  "status": false,
  "message": "Service unavailable",
  "code": 503
}
```

## Groups

### Get all groups
See all groups you have with your account
```bash

  curl https://sms.velstack.com/api/messaging/group
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -X GET
 
```
 ```json
{
  "status": true,
  "code": 200,
  "message": "Showing all groups",
  "data": {
    "Summary": [
      {
        "id": "a4a8da21-88f8-4395-a9df-f859f22c2dfa",
        "name": "V BANK",
        "members": 1
      },
      {
        "id": "1298d77e-fa98-4304-b513-e4e190a46e28",
        "name": "My Group",
        "members": 0
      }
    ],
    "collection": null
  }
}
```

### Get a Group
Get a specific group. To get a specific group, append the group `id` to the url like below
```bash

  curl https://sms.velstack.com/api/messaging/group/d565d047-df83-4b33-a498-f9de2aca50e6
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -d '{ group_name : "My Group"}'
  -X GET
 
```
 ```json
{
  "status": true,
  "code": 200,
  "message": "Showing a single group",
  "data": [
    {
      "id": "d565d047-df83-4b33-a498-f9de2aca50e6",
      "name": "My Group",
      "members": 0
    }
  ]
}
```

### Create Group
Create a new group in your account
```bash

  curl https://sms.velstack.com/api/messaging/group
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -d '{ group_name : "My Group"}'
  -X POST
 
```
 ```json
{
  "status": true,
  "code": 200,
  "message": "Group created successfully",
  "data": {
    "id": "d565d047-df83-4b33-a498-f9de2aca50e6",
    "name": "My Group",
    "members": 0
  }
}
```

### Update Group
Update an existing group in your account
```bash

  curl https://sms.velstack.com/api/messaging/group/d565d047-df83-4b33-a498-f9de2aca50e6
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -d '{ group_new_name : "Man City Supporters"}'
  -X PUT
 
```
 ```json
{
  "status": true,
  "code": 200,
  "message": "Group updated to Man City Supporters",
  "data": null
}
```

### Delete Group
Delete group from account. To delete a group, append the group `id` to the url
```bash

  curl https://sms.velstack.com/api/messaging/group/d565d047-df83-4b33-a498-f9de2aca50e6
  -H "Authorization: Bearer YOUR_API_KEY"
  -H "Accept: application/json"
  -X DELETE
 
```
 ```json
{
  "status": true,
  "code": 200,
  "message": "Group deleted successfully",
  "data": null
}
```





<p align="center">
<a href="https://twitter.com/velstack"><img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/velstack?label=@velstack&style=social"></a>
 <a href="https://packagist.org/packages/velstack/mnotify"><img src="https://img.shields.io/github/license/sammyfort/mNotify-laravel"></a>

</p>


  
<p align="center">
  Sammy Fort ©2023. Powered by <a href="https://velstack.com/">Velstack</a>
</p>
