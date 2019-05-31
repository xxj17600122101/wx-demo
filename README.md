##小程序云开发

1. app.js
   默认传的是第一云环境 如果有 2 个环境需要制定环境 id

- env:表示环境 id 传入字符串形式的环境 ID
- traceUser:是否在将用户访问记录到用户管理中，在控制台中可见

```
   wx.cloud.init({
        traceUser: true,
		env:"node-90816d"
	})
```

2. 如果创建和上传云函数
   - cloudfunctins 点击右键创建 nodejs 云函数
   -  在自动生成的 index.js 编写云函数
   ```
   exports.main = async (event, context) => {
   console.log(event) //用来接收前端传参
   return event.number
   }
   ```
3. 云函数的调用

```
   wx.cloud.callFunction({
   //对应的云函数名称
   name:'book',
   //我们传给云函数的参数
   data:{
   number:12345
   },
   //调用云函数成功的回调
   success:(res)=>{
   console.log(res)
   },
   //调用云函数失败的回调
   fail:(err)=>{
   console.log(err)
   }
})
```

4. 使用数据库

- 必须先进行数据库初始化
  const db = wx.cloud.database()
- 获取数据库集合
  const todos = db.collection('todos')
- 数据库使用注意事项 一定要注意权限设置
