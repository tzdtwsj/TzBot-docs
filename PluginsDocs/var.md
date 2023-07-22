# 自定义数据类型
一般的数据类型并不够我们使用，因此我们衍生了如下数据类型：  
## MessageParam - 信息数据类型
此数据类型原型为数组，以下是该数据类型的具体信息：  
```
array(
    "mydata" => array(
        "user_id" => 机器人的QQ号(int),
        "nickname" => QQ昵称(string),
    ),
    "msg" => 已经去掉了开头"at机器人"的消息,
    "message_id" => 消息id,
    "raw_message" => 原消息，参见https://docs.go-cqhttp.org/cqcode (string),
    "message_type" => 消息类型，有group与private两个可能值，分别是群聊和私聊,
    "sub_type" => 子消息类型，可能值：friend (好友)，normal (群聊)，anonymous (匿名)，group_self (群中自身发送)，group (群临时会话)，notice (系统提示)，参见https://docs.go-cqhttp.org/reference/data_struct.html#post-message-subtype,
    "user_id" => 发送者QQ号 (int),
    "sender" => 发送者，参见https://docs.go-cqhttp.org/reference/data_struct/#post-message-messagesender,
    "group_id" => 群QQ号，仅message_type为group时才会存在 (int),
);
```

