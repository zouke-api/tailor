### 1. /tailor/material/query-text

**描述**：获取用户文本素材

**request**：

``` json
{ "keywords": ["巴黎"],"page":0 } # page从0开始
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

### 2. /tailor/material/create-text # 已经废弃-拆分为2个接口-自己编辑的和系统导入

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
{ 
    "id": 10000, 
    "content": "这是修改后的文本",
    "tags":[
        {"name":"巴黎","type":"custom","code":1111},
    ] 
}
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
{ "keywords": ["巴黎"], "page": 0 }
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
[
    { "src": "url-to-image", "tags": [] },
    { "src": "url-to-image2", "tags": [] }
]
```

**response**：

``` json
{ "code": 0, "msg": "success","data":null }
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

### 12. /tailor/material/query-system-text # 废弃 改用20

**描述**：获取系统文本素材

**request**：

``` json
{
    "type": "keyword/city/gps",
    "keyword": ["巴黎"],
    "city": 10000,
    "gps": { "lat": 1, "lng": 1 }
}
```

**response**：

``` json
{
    "code": 0,
    "result": [
        { 
            "city": "巴黎",
            "list": [ 
                {
                    "id": 10000,
                    "content": "一段文本",
                    "tags": [
                        { "code": 10000, "type": "city", "name": "巴黎" },
                        { "code": 10001, "type": "custom", "name": "其它标签" }
                    ]
                }, 
                {
                    "id": 10001,
                    "content": "另一段文本",
                    "tags": [
                        { "code": 10000, "type": "city", "name": "巴黎" },
                        { "code": 10001, "type": "custom", "name": "其它标签" }
                    ]
                }
            ]
        },
        {
            "city": "另一个城市",
            "list": [{
                    "id": 10003,
                    "content": "另一个城市的文本",
                    "tags": [
                        { "code": 10000, "type": "city", "name": "巴黎" },
                        { "code": 10001, "type": "custom", "name": "其它标签" }
                    ]
            }]
        }
    ]
}
```

**说明**：查询字段三个只传其一，传`city`和`gps`字段时，返回距离目标最近的四个城市的结果

### 13. /tailor/material/query-system-image # 废弃

**描述**：获取系统图片素材

**说明**：同上


### 14. /tailor/material/associate-sys-tags

**描述**：联想系统标签

**request**：

``` json
{ "keyword": "巴黎" }
```

**response**：

``` json
{
    "code": 0,
    "tags": [
        { "code": 10000, "type": "city", "name": "巴黎" },
        ...
    ],
    "msg":"success"
}
```

### 15. /tailor/material/cal-similar

**描述**：计算文本相似度 返回相似度 和匹配的文章内容及标签

**request**：

``` json
{ "content": "wo在巴黎" }
```

**response**：

``` json
{
    "code": 0,
    "data": {
        "similar": 100, 
        "content": "我在巴黎", 
        "tags":[
            { "code": 10000, "type": "city", "name": "巴黎" },
        ]
    },
    "msg":"success"
}
```

### 16. /tailor/material/create-tags

**描述**：创建标签 并返回

**request**：

``` json
{ "names": ["标签1","标签2"] }
```

**response**：

``` json
{
    "code": 0,
    "data": [
        { "code": 10000, "type": "custom", "name": "标签1" },
        { "code": 10000, "type": "custom", "name": "标签2" },
    ],
    "msg":"success"
}
```

### 17. /tailor/material/create-text-from-sys

**描述**：将系统素材保存为我的素材

**request**：

``` json
{ 
    "list": [
        {
            "type":"text",
            "content":"content text text text",
            "tags":[
                "name":"tag name",
                "type":"city",
                "code":1111,
            ],
        }
    ] 
}
```

**response**：

``` json
{
    "code": 0,
    "data": null,
    "msg":"success"
}
```


### 18. /tailor/material/create-text-self-edit

**描述**：保存自己编辑的素材 编辑内容长度大于10才入库

**request**：

``` json
{ 
    "list": [
        {
            "type":"text",
            "content":"content text text text",
            "tags":[
                "name":"tag name",
                "type":"city",
                "code":1111,
            ],
        }
    ] 
}
```

**response**：

``` json
{
    "code": 0,
    "data": null,
    "msg":"success"
}
```

### 19. /tailor/material/delete-tags

**描述**：删除标签-并清除文本素材和图片素材中相应的标签

**request**：

``` json
{ "codeId": 111111}
```

**response**：

``` json
{
    "code": 0,
    "data": null,
    "msg":"success"
}
```

### 20. /tailor/material/query-system-image-simple

**描述**：查询系统图片素材 - 独立定制师

**request**：

``` json
{
    "cities": [
        387523,3114921
    ],
    "gps": {
        "lat": 48.856614,
        "lng": 2.35222190000002
    },
    "keywords": [
       "巴","打","哥打"
    ],
    "type": "cities",
    "page":0
}
```

**response**：

``` json
{
    "code": 0,
    "list": [
        {
            "id":1111,
            "src":"src-url",
            "tags":[
                {
                    "code":232,
                    "name":"巴黎",
                    "type":"custom"
                }
            ]
        }
    ],
    "msg":"success"
}
```

### 21. /tailor/material/query-system-text-simple
**描述**：查询系统文字素材 - 独立定制师
**说明**：同上

### 22. /tailor/material/statistics-text-img
**描述**：素材统计

**response**：

``` json
{
    "code": 0,
    "data": {
        "textCount":100,
        "imgCount":200,
    },
    "msg":"success"
    }
}
```

### 23. /tailor/material/update-image
**描述**：修改图片素材
**request**：

``` json
{}
```
**response**：

``` json
{
    "code": 0,
    "data": {
        "textCount":100,
        "imgCount":200,
    },
    "msg":"success"
    }
}
```

### 24. /tailor/material/update-image
**描述**：修改图片素材
**request**：

``` json
{
    "id":1111,
    "src":"src-url",
    "tags":[
        {"name":"tagName","type":"city","code":1111},
    ]
}
```
**response**：

``` json
{
    "code": 0,
    "data": {
        "textCount":100,
        "imgCount":200,
    },
    "msg":"success"
    }
}
```

### 25. /tailor/material/user-tags
**描述**：获取用户标签
**request**：

``` json
{
    "keyword":"巴黎"
}
```
**response**：

``` json
{
    "code": 0,
    "tags": [
        {"name":"bali","type":"custom","code":111111}
    ],
    "msg":"success"
}
```


