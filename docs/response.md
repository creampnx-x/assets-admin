# 服务端 Response Json 格式

> 尽可能的简单，并忽略性能

## 成功

成功时直接返回全部数据，将状态放在http code中。

```json
{
    "user_id": "aabb",
    "user_name": "ccdd"
}
```

## 失败

失败时直接返回`message`字段，将状态放在http code中。

```json
{
    "message": "user already exist."
}
```

# Http Code

服务器状态码按照首位数字分为5类

+ 1xx -> 信息类
+ 2xx -> 成功类
+ 3xx -> 重定向
+ 4xx -> 客户端错误
+ 5xx -> 服务端错误

按照设计来说，`1xx`多用于长链接或者`socket`，3xx用于重定向，所以用的不多。所以现在使用比较频繁的2xx, 4xx, 5xx。

## 2xx

一般在服务中，可以将`200`作为请求成功的状态码，在一些弱返回结果的请求中直接使用`200`作为结果而不用在 body 中添加返回内容。

## 4xx 

返回`400`以表示客户端的操作有问题

## 5xx

返回`500`以表示服务端执行出问题，需要程序员介入