# 1. @Input 和 @Output 别名
> @Input 代表从外部获取数据, @Output代表对外输出事件
> 别名是因为外部传入的变量名有可能跟内部的同名,会发生覆盖,所以可以自定内部使用名称.
## 1.1 @Input
  * @Input(外部公开名) 内部使用名称
  * inputs:['内部使用名称: 外部公开名称']
## 1.2 @Output
  * @Output(外部公开名) 内部使用名称
  * outputs:['内部使用名称: 外部公开名称']
# 2. 模板引用变量 #var
> 在一个DOM元素上加一个引用名称,可以代指该片段. 类似于React中的ref.
## 2.1 用法
  * #名称 名称.value 获取表单的值
  * ref-名称`全写`,用法一致
# 3. 安全导航符 ?.
> 防止取一个空对象的属性值时报错,导致view加载不出来.使用安全导航符?.可以避免报错.
# 4.Typescript
> JS的一个超集,支持变量和方法拥有自己的数据类型.
* 定义变量:  `string` `number` `boolean` `Array` `enum` `any`
* 定义变量: `let name: string = 'Tim'`
* 定义方法: 
```python
function fn(age: number): number{
  return 12;
  return '12';//报错
}
function fn(age: number): void{
  //代表没有返回值
}
```
# 5. 表单
> 既重要又复杂, 两种: 模板驱动表单 和 响应式驱动表单.
## 5.1 获取用户输入(3种)
* 事件获取$event,但是值能监听表单元素的事件
* 模板变量获取#var.value
* 双向数据绑定[(ngModel)]
## 5.2 事件修饰符
修饰事件发生的条件: (keyup.enter)="" 代表只能在enter键抬起时触发.
## 5.3 class类响应数据变化
| 状态为真时的     | CSS类为假时  |  CSS 类  |
| --------   | -----:  | :----:  |
| 控件被访问过     | ng-touched |  ng-untouched    |
| 控件的值变化了      |   ng-dirty   |  ng-pristine   |
| 控件的值有效        |   ng-valid    |   ng-invalid  |

## 5.4 模板校验
> 在一个表单上添加双向数据绑定[(ngModel)] 和 #var ,然后两者联系起来 #var="ngModel".那么就可以通过模板变量获取校验信息.
* `valid` `invalid` `dirty` `touched` `errors`
## 5.5 表单提交
> 在`form`标签上使用`(ngSubmit)="事件方法"` 拦截表单提交请求.
## 5.6 响应式表单校验
> 数据校验和模板分离
* 依赖`ReactiveFormsModule`
* 添加`[formGroup]="myGroup"`
* 修改 
```python
<input type="text" 
[(ngModel)]="user.name" 
name="name" 
required 
minlength="4">
```
为
```python
<input type="text" 
name="name" 
formControlName="name">
```
只留下一个`formControlName`
* 在组件中创建FormGroup
```python
myGroup: FormGroup;//指定类型为FormGroup
  
  ngOnInit() {
    //第四步 初始化 FormGroup
    this.myGroup = new FormGroup({
      // 第五步 初始化一个表单控制组件
      myAge: new FormControl(this.user.age,[
        //第六步 配置内置校验
        Validators.required,//必输
        Validators.minLength(4), //最小长度4
        forbidenNameValiator(/lala/i)
      ])
    });
  }

```
## 5.7 自定义表单校验
```python
function forbiddenNameValidator(nameReg: RegExp): ValidatorFn{
return (control: AbstractControl): {[key: string]: any} =>{
const forbidden = nameReg.test(control.value);
return forbidden `?` {'forbiddenName': {value: control.value}} : null;
}
}
```
使用方式: 放在 `FormControl`的数组里
