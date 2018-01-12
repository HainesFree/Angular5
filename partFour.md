# 1. 生命周期
> 组件生命周期: 创建 更新 销毁
> 钩子函数: 声明周期的每一个阶段的监听函数, 会自动触发!
* `OnInit`: 初始化组件数据, 初始化组件的业务逻辑
* `OnDestroy`: 变量回收 结束的逻辑处理 或者通知其他组件
* `OnChanges`: 监听输入属性@Input() 的变化, 不能监听组件其他属性的变化!
* `DoCheck`: 监听组件内部任意属性的变化, 触发频率高, 小心使用!
* `AfterView`: 组件视图渲染完毕后触发, 不允许直接在这里修改数据(单项数据流),可以使用setTimeout(fn,0) 等到事件执行的下一轮开始执行.
* `AfterContent`: 当外部投影插入组件后触发: `<content><child></child></content>`
# 2. 管道Pipe
## 2.1 用法
* 使用{{ name | json }}
* 参数化{{name | date:'yyyy-MM-dd'}}
* 变量{{name | date:format}} `format` 是一个变量
* 链式管道 {{name | json | date | uppercase}}
* 自定义管道:ng-pipe
## 2.2 纯管道(pure)和非纯管道(impure)
>区别: 纯管道只有在数据发生`完全替换`时才触发,比如: `Number` `Boolean` `String` 
> 还有`var obj = {name:'zhangsan'}; -> obj = {name:'lisi'}` 会触发
> 如果`var obj = {name:'zhangsan'}; -> obj.name='lisi'` 不会触发
> 非纯管道触发频次比较高, 他会在对象属性变化时也触发! 性能不好.
# 3. 依赖注入(DI depend Inject)
> 依赖注入是一种设计模式, 在Angular中应用非常广泛.
> 有全局注册`NgModule`和局部注册`Component`两种模式.
## 3.1 创建服务
* 定义服务类`@Injectable()`
* 引入到根模块
* 在组件的构造器中注入服务: 形式: `constructor(private userListService: UserListService) { }`
## 3.2 带依赖类的服务
> 一个服务依赖另外一个服务, 可以把另外一个服务注入到当前服务
## 3.3 新服务提供商
> 修改/升级旧的服务`{ provide: LoggerService, useClass: BetterLoggerService }`
## 3.4 值提供商
> 通过一个对象替换旧的服务: `{provide: LoggerService, useValue: silentLogger}`
## 3.5 可选依赖
>`@Optional()` 有或者没有都可以
## 3.6 多级依赖注入器
> 在Angular中,有一个和组件系统平级的注入器系统.
> 注入器冒泡: 在一个组件中注册服务时, 先找自己有没有注入当前服务, 没有继续往上找,直到找到位置,最后找不到就报错.
# 4. HttpClient 库
> 用来发送Ajax请求.
