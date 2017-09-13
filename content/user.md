### 1. /tailor/user/update-cover

**描述**：更改定制师主页专封面

**request**：

``` json
{ "cover": "https://cdn1.zouke.com/xxx.png" }
```

**response**：

``` json
{ "code": 0 }
```

### 2. /tailor/user/get-user-info-by-id

**描述**：根据id获取定制师信息

**request**：

``` json
{ "uid": 10000 }
```

**response**：

``` json
{ 
    "code": 0,
    "info": {
        ...
    }
}
```

**说明**：反回的info信息同登录获取的用户信息，详见[获取用户详细信息接口](https://zouke-api.github.io/hotel/http/login.html)

### 3. /tailor/user/follow

**描述**：关注定制师

**request**：

``` json
{ "uid": 10000 }
```

**response**：

``` json
{ "code": 0 }
```

### 4. /tailor/user/unfollow

**描述**：取消关注

**说明**：用法同上

### 5. /tailor/user/get-my-follows

**描述**：获取我关注的定制师列表信息

**response**：

``` json
{
    "code": 0,
    "list": [
        { 
            "id": 10000,
            "nickName": "昵称",
            "avatarUrl": "头像url",
            "country": "国家",
            "city": "城市",
            "tailorInfo": {         //该对像可能为空
                "cover": "封页"
            }
        }
    ]
}
```

### 6. /tailor/user/get-my-views

**描述**：获取我浏览过的定制师列表

**说明**：用法同上