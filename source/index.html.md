---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://clickup.com'>Sign Up to start using ClickUp</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to a mini ClickUp API documentation page! 

Here, we'll specifically discuss API calls for the Time Estimates feature only. This includes:

* Creating a task with Time Estimates
* Updating the Time Estimate of a specific task
* Retrieving a task with its Time Estimate
* Removing the Time Estimate of a specific task

# Authentication

**This part is taken from the [main ClickUp API documentation page](https://jsapi.apiary.io/apis/clickup20/introduction/authentication.html).**

There are two ways to authenticate with ClickUp API 2.0, with a personal token or creating an application and authenticating with an OAuth2 flow. Once you receive one of those two tokens, use that in the Authorization header of your API requests.

IMPORTANT - If you are creating an application for other's to use, it is highly recommended that you use the OAuth2 flow.

## Personal Token

> To start using an API call, you'll need to authorize with your access token in this format:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: access_token"
```

> Make sure to replace `access_token` with your API key.

If you are using the API for personal use, it is safe to use the personal API token. You can find this token in your user settings, under the Apps section. At the top of the page you have the option to generate a personal token. These tokens will always begin with pk_.personal_token

If your token becomes compromised, you can regenerate it. However, be aware that any applications that were using the old token will lose access once it has been regenerated.

`Authorization: access_token`

<aside class="notice">
You must replace <code>access_token</code> with your personal token.
</aside>

## OAuth2 Flow
When you want to develop an application that others can use, you must go through the OAuth2 flow so that ever user that uses your application gets assigned an individualized token. This way each user of your application is able to access their own ClickUp resources. [Click here to read further on how to use the ClickUp OAuth2 flow](https://jsapi.apiary.io/apis/clickup20/introduction/authentication/oauth2-flow.html)

Note: _ClickUp uses the authorization code grant type._

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

