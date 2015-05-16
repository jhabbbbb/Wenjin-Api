#用户通知中心相关接口
##action_type列表
	const TYPE_PEOPLE_FOCUS	= 101;	// 被人关注
	const TYPE_NEW_ANSWER	= 102;	// 关注的问题增加了新回复
	const TYPE_COMMENT_AT_ME	= 103;	// 有评论@提到我
	const TYPE_INVITE_QUESTION	= 104;	// 被人邀请问题问题
	const TYPE_ANSWER_COMMENT	= 105;	// 我的回复被评论
	const TYPE_QUESTION_COMMENT	= 106;	// 我的问题被评论
	const TYPE_ANSWER_AGREE	= 107;	// 我的回复收到赞同
	const TYPE_ANSWER_THANK	= 108;	// 我的回复收到感谢
	const TYPE_MOD_QUESTION	= 110;	// 我发布的问题被编辑
	const TYPE_REMOVE_ANSWER	= 111;	// 我发表的回复被删除

	const TYPE_REDIRECT_QUESTION	= 113;	// 我发布的问题被重定向
	const TYPE_QUESTION_THANK	= 114;	// 我发布的问题收到感谢
	const TYPE_CONTEXT	= 100;	// 纯文本通知

	const TYPE_ANSWER_AT_ME	= 115;	// 有回答 @ 提到我
	const TYPE_ANSWER_COMMENT_AT_ME	= 116;	// 有回答评论 @ 提到我

	const TYPE_ARTICLE_NEW_COMMENT	= 117; // 文章有新评论
	const TYPE_ARTICLE_COMMENT_AT_ME	= 118; // 文章评论提到我

	const TYPE_ARTICLE_APPROVED = 131; // 文章通过审核
	const TYPE_ARTICLE_REFUSED = 132; // 文章未通过审核
	const TYPE_QUESTION_APPROVED = 133; // 问题通过审核
	const TYPE_QUESTION_REFUSED = 134; // 问题未通过审核

	const TYPE_TICKET_REPLIED = 141; // 工单被回复
	const TYPE_TICKET_CLOSED = 142; // 工单被关闭
	
##检查是否有通知、未读私信、动态

> URL：api/notification/notifications/  (/?/api/notification/notifications/)

> HTTP请求方式

- GET

> 请求参数：

- [int] time 当前Unix时间戳

> 返回结果：

- [int] inbox_num 未读私信数量
- [int] notifications_num 未读通知数量
- [int] new_action  新动态数量

> 可能返回的错误原因：

- 未登录

##获取通知列表

> URL：api/notification/list/  (/?/api/notification/list/)

> HTTP请求方式

- GET

> 请求参数：

- [int] page  页数
- [int] flag  0未读  1已读


> 返回结果：

- [int] notification_id 通知编号
- [int] action_type 通知类型（对应编码表）
- [int] read_flag 是否已读 0 未读 1已读
- [array]  related  通知所涉及的问题和回答类型的详细信息，包含问题id和回答id
- [int]key_url 最直接涉及id，如果为回答，则为答案id；如果是编辑了问题，则为问题id；如果是有人关注了你，则为关注你的人的uid；如果为文章评论，则为文章id；如果是点赞、感谢了某个答案，则为答案id；如果感谢了某个问题，则为问题id；
- [string] message 对于通知消息的封装结果。客户端可以根据自己的需要利用上述键值进行自行组装，也可以调用封装结果。
- 其他返回项看键名应该易懂。

> 可能返回的错误原因：

- 未登录

##标记已读消息

> URL：api/notification/read_notification/  (/?/api/notification/read_notification/)

> HTTP请求方式

- GET

> 请求参数：

- [int]  notification_id(通知的id)
- 如果notification_id为确定的int值，则标记id为notification_id的消息为已读。如果不传送notification_id值，则为标记【所有】未读消息为已读

> 返回结果：

- 见实际结果

> 可能返回的错误原因：

- 未登录
