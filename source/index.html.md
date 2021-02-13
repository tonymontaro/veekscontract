---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Veeks (API Docs).
I've left out the creating and update (PUT) routes for now, till we agree on the structure/contract.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```


> Make sure to replace `meowmeowmeow` with your API key.

A valid API key will be provided.

Veeks expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>





# Users

## Get A User


```shell
curl -d "email=usermail" -X POST "/users/" \
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
 {
    "id": 1,
    "email": "nujabes@seba.com",
    "name": "Nujabes",
    "photo": "https://abc.jpg",
    "watchList": [4, 5, 6],
    "goals": [1, 2, 3],
  }
```

This endpoint retrieves the user by email.


### HTTP Request

`POST /users`

### Query Parameters

Parameter | Description
--------- | -----------
email | Email of the user to retrieve


# Goals

## Get A Goal


```shell
curl "/goals/1" \
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
 {
    "id": 1,
    "userId": 1,
    "title": "Make a million dollars.",
    "inviteLink": "https://invite.com/1",
    "status": "Ongoing",
    "progress": 20,
    "steps": [
      {
        "id": 1,
        "goalId": 1,
        "name": "Rob a bank",
        "Description": "Description ...",
        "done": false,
      },
    ]
  }
```

This endpoint retrieves the goal by id.


### HTTP Request

`GET /goals/<ID>`

### Query Parameters

Parameter | Description
--------- | -----------
ID | ID of goal to retrieve


## Get A Goal Progress Logs

```shell
curl "/goals/1/progress" \
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "content": "Started goal: Make a million bucks.".
  },
  {
    "id": 2,
    "content": "Completed Step 1: Rob a bank"
  }
]
```

This endpoint retrieves the progress logs for a goal.

### HTTP Request

`GET /goals/<ID>/progress`

### Query Parameters

Parameter | Description
--------- | -----------
ID | ID of goal to retrieve



# Steps

## Get A Goal Step


```shell
curl "/steps/1" \
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
  {
    "id": 1,
    "goalId": 1,
    "name": "Rob a bank",
    "Description": "Description ...",
    "done": false,
  }
```

This endpoint retrieves the step by id.


### HTTP Request

`GET /steps/<ID>`

### Query Parameters

Parameter | Description
--------- | -----------
ID | ID of step to retrieve



