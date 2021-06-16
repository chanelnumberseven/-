# 工作问题及解决方案汇总
## 关于解构赋值默认值被null（后台数据）覆盖的问题

示例：
``
  const {data=[]}=await request('test.json'); // 后台返回数据格式{data:null}
  console.log(data) // null 而不是 []
``

解决方案：对request的返回数据的解析进行设置,过滤掉null值改为undefined
``
  const {data=[]}=JSON.parse('{"data":null}',(key,value)=>value??undefined);
  console.log(data) // []
``
