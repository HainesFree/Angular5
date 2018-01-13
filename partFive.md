# 1. HttpClient
- [ ] `{observe: 'response'}` 获取完整的请求题信息: `200`等 数据在`body`里面
- [ ] 错误处理在`subscribe`传入第二个函数即可
- [ ] `HttpErrorResponse` 获取完整错误信息,区分前台或者后台错误
- [ ] `.retry() 操作符` 当请求失败时,会再次发送请求,可以自定义请求次数
- [ ] `{responseType: 'text'}` 请求非JSON数据
- [ ] GET传参: 两种: 1.在url地址后边问号隔开 2.使用对象传入get请求中: 形式`{params: obj}`
- [ ] POST传参: 可以直接使用对象放入post方法中, 也可以通过:`{params:new HttpParams().set('id','1')}` 来传递get参数
# 2. 路由和导航
> 根据不同的url地址显示不同的页面
- [x] `**` 通配符路由, 拦截无效的url跳转到这个页面

- [x]  `redirectTo`重定向路由, 把一个路由重定向到另一个路由
- [x]  参数路由: 页面之间传递参数 路由配置`:id`
- [x]  路由嵌套: 可以配置多个子路由, 形成一个复杂的路由系统
- [x]  路由模块: 当路由多时,不方便维护, 可以把他单独组建一个模块!进行引用
- [x]  函数式路由: 通过JS的方式实现路由跳转. `navigateByUrl ` 和 `navigate`
- [x]  `{ skipLocationChange: true }`: 浏览器地址不变,页面变化
