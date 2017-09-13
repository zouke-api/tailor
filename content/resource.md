### 登录相关接口详见[登录](https://zouke-api.github.io/hotel/http/login.html)，该应用对应的app为`tailor`

### 1. /auth/commit-identity

**描述**：提交用户认证

### 2. /city/query

**描述**：根据关键字查询城市

**request**：

``` json
{
    "keyword": "巴黎"
}
```

### 3. /utils/get-qn-token

**描述**：获取七牛上传token

**response**：

``` json
{
    "code": 0,
    "token": "qiniu token",
    "cdns": "上传七牛文件的域名(https)",
    "uploads": "七牛的上传地址(https)"
}
```