#搜索接口

##搜索查询接口

> URL：api/search/  (http://www.example.com/?/api/search/)

> HTTP请求方式

- get

> 请求参数：

- q string 搜索内容（必选）
- type string 类型 users/topics/questions（选填）
- limit int 一页拉取的数量（必选）
- page int 第几页（必选，从1开始）
- topic_ids string 搜索的属于哪些话题，用英文逗号分隔（选填）
- is_recommend string 是否是推荐的问题（1是0否）（选填）

> 返回结果：

- uid int 然并卵
- score int 然并卵
- type string 分为/topics/quesitons/users/ 应该看得
- url string对于客户端来说，然并卵
- seacch_id int 然并卵
- name string 搜索的结果名称
- detail Array:
- 根据不同的返回类型有不同的结构，一共三种。
