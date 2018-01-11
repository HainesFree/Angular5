# 1.Form 表单
## 1.1 取值
* 事件`$event`
* 模板变量`#var`
* 双向数据绑定`[(NgModel)]`
## 1.2 校验 (模板表单校验和响应式表单校验)
* 同步校验: 响应式表单
* 异步校验: 模板表单
## 1.3 提交
> `(ngSubmit)="事件方法"` 拦截提交请求
## 1.4 FormBuilder 
> 帮助我我们创建`FormGroup` 和 `FormControl`
* 多级group嵌套, 应对复杂的表单数据结构
* FormControl的属性: `value` `status` `pristine` `untouched`
* 强制重置 重置默认值 `reset()` 提交
## 1.5 表单模型 和 数据模型
> 表单模型跟DOM结构是绑定的, 可以对DOM结构进行数据初始化,DOM结构数据流向表单模型,而不会更改数据模型.
> 数据模型一般指的数据后台定义的一个数据结构: 比如: Address类: 有两个字段: street 和 city
## 1.6 常用方法
* `setValue` : 设置表单模型的值, 属于严格设置! 如果缺少字段就会报错.
* `patchValue`: 作用同上,但是不会报错!
# 2. 组件
## 2.1 交互
* 父->子: @Input
* 子->父: @Output
* setter监听输入值
* 本地模板变量: #var 代替子组件在模板中使用
* 使用@ViewChild() 在JS中操作子组件
## 2.2 样式
* `styles`
* `styleUrls`
* `<link>` 模板直接使用
* `<style>` 模板直接使用
* `@import()` 在style.css中
## 2.3 封装模式
* `Native`: 不进不出
* `Emulated`: 只进不出
* `None`: 可出可进
实例: 在`@Component`添加属性`encapsulation: ViewEncapsulation.Native`
## 2.4 特殊选择器
* `:host` 选中宿主元素
* `:host(.class)` 对宿主元素过滤
* `:host-context(.class)` 选择祖先元素
* 废弃的选择器:`/deep/、>>>` 
