#地理社交接口

##地理位置提交

> URL：api/lbs/post_location/  (http://www.example.com/?/api/lbs/post_location/)

> HTTP请求方式

- get

> 请求参数：

- latitude 纬度（必选）
- longitude 经度（选填）

> 返回结果：

- 成功为空

> 可能遇到的错误：

- 参数不完整
- 未登录


##附近的人/问题 查询


> URL：api/lbs/near_by/  (http://www.example.com/?/api/lbs/near_by/)

> HTTP请求方式

- GET

> 请求参数：

- type (user为附近的人,question为附近的问题）

> 返回结果：

- 相关数组

> 可能返回的错误原因：

- 未登录
- 未设定获取类型
- 未提交过定位信息
- 超过1天未更新地理位置
