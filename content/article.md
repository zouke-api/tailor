### 1. /tailor/article/create

**说明**：创建文章

**request**：

``` json
{
    "title": "文章标题",
    "detail": [
        { "type": "text", "content": "这是一段文本" },
        { "type": "image", "src": "image-url-path" }
    ]
}
```

**response**:

``` json
{
    "code": 0,
    "id": 10000
}
```

### 2. /tailor/article/update

**说明**：更改文章

**request**：

``` json
{
    "id": 10000,
    "title": "更改的文章标题",
    "detail": [
        { "type": "text", "content": "更改后的文本" },
        { "type": "image", "src": "changed-url-path" }
    ]
}
```

**response**：
``` json
{
    "code": 0
}
```

### 3. /tailor/article/delete

**说明**：删除文章

**request**：

``` json
{
    "id": 10000,
}
```

**response**：

``` json
{
    "code": 0
}
```

### 4. /tailor/article/get-list

**说明**：获取文章列表

**request**：

``` json
{
    "uid": 10000
}
```

**response**：

``` json
{
    "code": 0,
    "list": [
        { "id": 1000, "title": "xxxxx", "content": "rrrrr", "image": "url-to-path" }
        { "id": 1001, "title": "xxxxx", "content": "rrrrr", "image": "url-to-path" }
    ]
}
```

**说明**：若无uid，获取登录用户文章列表，若传递uid，获取该用户的文章列表

### 5. /tailor/article/get-detail

**说明**：查询文章详情

**request**：

``` json
{
    "uid": 10000,
    "id": 10000
}
```

**response**：

``` json
{
    "code": 0,
    "id": 10000,
    "title": "文章标题",
    "detail": [
        { "type": "text", "content": "文本" },
        { "type": "image", "src": "url-path" }
    ]
}
```

**说明**：uid字段同上