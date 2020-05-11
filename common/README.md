#### 公共约定

- 状态码  

1.200(创建/修改/删除)  
```js
{
    "status": 200,
    "msg": "请求成功"
}
```
2.200(请求成功)
```js
{   
    "status":200,
    "msg":"请求成功",
    "data":
        {
         "id":1,
         "other":"other"
        }
}
```
3.271(文字提示)
```js
{
    "status": 271,
    "msg": "用户已存在"
}
```
1.500(接口错误)  
```js
{
    "status": 500,
    "msg": "缺少token"
}
```

- eolinker  

状态如下:  
![状态](../img/eolinker_status.png)  

- 状态修改流程  
> 已发布/待定/对接  

```flow
st=>start: 新接口(已发布)
op=>operation: 前端调用后(待定)
op2=>operation: 接口修改(对接)
e=>end: 全部状态为待定
cond=>condition: 接口修改Yes or No?
st->op->cond->op2
cond(yes)->e
cond(no)->op
&```