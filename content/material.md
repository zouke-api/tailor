### 1. /tailor/material/query-text

**描述**：获取用户文本素材

**request**：

``` json
{ "keywords": ["巴黎"] }
```

**response**：

``` json
{
    "code": 0,
    "list": [
        {
            "id": 10000,
            "content": "这是一段文本",
            "tags": [
                { "code": 10000, "type": "city", "name": "巴黎" },
                { "code": 10001, "type": "custom", "name": "其它标签" }
            ]
        }
    ]
}
```

**说明**：可以不传参数获取所有我的文本素材

### 2. /tailor/material/create-text

**描述**：添加用户文本素材

**request**：

``` json
{ "content": "这是新建的文本", "tags": [] }
```

**response**：

``` json
{ "code": 0, "id": 10005 }
```

### 3. /tailor/material/update-text

**描述**：更新用户文本素材

**request**：

``` json
{ "id": 10000, "content": "这是修改后的文本" }
```

**response**：

``` json
{ "code": 0 }
```

### 4. /tailor/material/change-text-tags

**描述**：更改用户文本标签

**request**：

``` json
{ 
    "id": 10000,
    "tags": [
        { "code": 10000, "type": "city", "name": "巴黎" },
        { "code": 0, "name": "新标签" }
    ]
}
```

**response**：

``` json
{
    "code": 0,
    "id": 10000,
    "tags": [
        { "code": 10000, "type": "city", "name": "巴黎" },
        { "code": 10002, "type": "custom", "name": "新标签" }
    ]
}
```

### 5. /tailor/material/delete-text

**描述**：删除用户文本

**request**：

``` json
{ 
    "id": 10000
}
```

**response**：

``` json
{
    "code": 0
}
```

### 6. /tailor/material/get-similar-text

**描述**：获取与给定文本相似的文本素材

**request**：

``` json
{ "content": "给定文本" }
```

**response**：

``` json
{ 
    "code": 0,
    "list": [
        {
            "id": 10000,
            "content": "这是一段文本",
            "tags": [
                { "code": 10000, "type": "city", "name": "巴黎" },
                { "code": 10001, "type": "custom", "name": "其它标签" }
            ],
            "similar": 85
        }
    ]
}
```

**说明**：响应数据中的similar字段表示相似度的百分比

### 7. /tailor/material/query-image

**描述**：获取用户图片素材

**request**：

``` json
{ "keywords": ["巴黎"] }
```

**response**：

``` json
{
    "code": 0,
    "list": [
        {
            "id": 10000,
            "src": "url-to-image",
            "tags": [
                { "code": 10000, "type": "city", "name": "巴黎" },
                { "code": 10001, "type": "custom", "name": "其它标签" }
            ]
        }
    ]
}
```

**说明**：可以不传参数获取所有我的文本素材

### 8. /tailor/material/create-image

**描述**：添加用户图片素材

**request**：

``` json
{ "src": "url-to-image", "tags": [] }
```

**response**：

``` json
{ "code": 0, "id": 10005 }
```

### 9. /tailor/material/change-image-tags

**描述**：更改用户图片标签

**request**：

``` json
{ 
    "id": 10000,
    "tags": [
        { "code": 10000, "type": "city", "name": "巴黎" },
        { "code": 0, "name": "新标签" }
    ]
}
```

**response**：

``` json
{
    "code": 0,
    "id": 10000,
    "tags": [
        { "code": 10000, "type": "city", "name": "巴黎" },
        { "code": 10002, "type": "custom", "name": "新标签" }
    ]
}
```

### 10. /tailor/material/delete-image

**描述**：删除用户图片

**request**：

``` json
{ 
    "id": 10000
}
```

**response**：

``` json
{
    "code": 0
}
```

### 11. /tailor/material/query-tags

**描述**：根据关键字查询该用户的标签和系统标签等

**request**：

``` json
{
    "keyword": "标签名"
}
```

**response**：

``` json
{
    "code": 0,
    "tags": [
        { "code": 10000, "type": "city", "name": "巴黎" },
        { "code": 10002, "type": "custom", "name": "新标签" }
    ]
}
```

**说明**：若无keyword字段，则返回用户名下所有标签。文本和图片**共用一套标签**

