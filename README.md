# 工作问题及解决方案汇总
## 关于解构赋值默认值被null（后台数据）覆盖的问题

示例：

```jsx
  
  // 后台返回数据格式{data:null}  
  const {data=[]} = await request('test.json');
  
  // null 而不是 []
  console.log(data)
  
```

解决方案：对request的返回数据的解析进行设置,过滤掉null值改为undefined

```jsx
  
  // 可以对自己的请求插件进行配置如何解析后台返回的json数据    
  const {data=[]} = JSON.parse('{"data":null}',(key,value)=>value??undefined);  
    
  // 返回结果[]    
  console.log(data)
  
```
