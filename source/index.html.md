---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# 挪瓦本地生活API

欢迎使用挪瓦本地生活API。本API以挪瓦咖啡小程序为载体，涵盖了本地生活的大多数领域，包括小程序、支付、地图、配送、云打印等。

主要使用语言为 Shell, Python, 和 JavaScript! 你可以在右侧的暗黑区域里看代码示例, 切换你想要的语言版本，当然也欢迎补充其他语言版本.

# 微信小程序(客户端)

## 用code换取userinfo

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl -X POST -d '{"code":"043t2s0q01DAfk1uW11q0Opg0q0t2s0P","invitor":"oRYTz5BuN1jmXDg5VnevUMD9PTa0"}' https://talk.cirray.cn/api/code2userinfo
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

如果是已注册用户(已授权绑定手机号),则返回用户的详细信息,包括phone,avatar,nickname等;否则返回用户的openid

### 方法

`POST`

### 参数

参数名 | 示例 | 描述
--------- | ------- | -----------
code | 043t2s0q01DAfk1uW11q0Opg0q0t2s0P | 微信小程序里拿到的code
invitor | oRYTz5BuN1jmXDg5VnevUMD9PTa0 | 邀请者的openid,非必须

### URL

<aside class="success">https://talk.cirray.cn/api/code2userinfo</aside>

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

# 微信小程序(商家端)

## 用code换取userinfo

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl -X POST -d '{"code":"043t2s0q01DAfk1uW11q0Opg0q0t2s0P"}' https://talk.cirray.cn/api/mer/code2userinfo
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

返回用户的openid,phone等信息

### 方法

`POST`

### 参数

参数名 | 示例 | 描述
--------- | ------- | -----------
code | 043t2s0q01DAfk1uW11q0Opg0q0t2s0P | 微信小程序里拿到的code

### URL

<aside class="success">https://talk.cirray.cn/api/mer/code2userinfo</aside>

