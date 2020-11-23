# 创建项目之vue init 和 vue create的区别

**vue init**

是vue-cli2.x的初始化方式，可以使用github上面的一些模板来初始化项目

webpack是官方推荐的标准模板名

使用方式：vue init webpack 项目名称

electron-vue的模板

使用方式：vue init simulatedgreg/electron-vue 项目名称

**vue create**

是vue-cli3.x的初始化方式，模板是固定的，模板选项可自由配置

使用方式：vue create 项目名称

# 如何查看自己项目中vue的版本号和cli的版本号

查看Vue版本号

代码方式

    npm list vue
其他方式

找到package.json文件夹 找"dependencies"然后就可以看到你装的vue的版本了

查看cli版本号

    vue -V

# 开发环境、测试环境、生产环境

开发环境(DEV)：开发环境是程序猿们专门用于开发的服务器，配置可以比较随意， 为了开发调试方便，一般打开全部错误报告。

测试环境(UAT)：一般是克隆一份生产环境的配置，一个程序在测试环境工作不正常，那么肯定不能把它发布到生产机上。

生产环境(PROD)：是指正式提供对外服务的，一般会关掉错误报告，打开错误日志。可以理解为包含所有的功能的环境，任何项目所使用的环境都以这个为基础，然后根据客户的个性化需求来做调整或者修改。

 

三个环境也可以说是系统开发的三个阶段：开发->测试->上线，其中生产环境也就是通常说的真实环境。

UAT环境：UAT，(User Acceptance Test),用户接受度测试 即验收测试，所以UAT环境主要是用来作为客户体验的环境。

仿真环境：顾名思义是和真正使用的环境一样的环境（即已经出售给客户的系统所在环境，也成为商用环境），所有的配置，页面展示等都应该和商家正在使用的一样，差别只在环境的性能方面。

# javascript中var,let,const的区别用法
https://www.jianshu.com/p/7be962a355f8

# vue组件
Vue组件 = Vue实例 = new Vue(options)
不同的组件options数据的不同
# vue组件核心概念
## 属性
单向数据流-属性分为：自定义属性（props）、原生属性（attrs）和特殊属性（class、style） 
- 自定义属性：组件props中声明的属性 
- 原生属性：没有声明的属性，默认自动挂载到组件上，设置inheritAttrs为false可以关闭自动挂载 
- 特殊属性：挂载到组件根元素上，支持字符串、对象、数组等多种语法
自定义属性代码请移步到`vue_code/Props.vue`文件
属性使用示例：`Props.vue`组件的子组件，这段代码的作用是把父组件的属性值在子组件展示出来。
```
<Props
    name="123"
    :is-visible="false"
    title="属性测试"
    class="test1"
    :class="['test2']"
    :style="{marginTop:'20px'}"
    style="marginTop:10px"
     />
```
注意：属性是单项数据流，不能在组件中直接修改父组件传递的值。
## 事件
- 普通事件：@click，@input，@change，@xxx等事件，通过this.$emit('xxx',...)触发。
- 修饰符事件：@input.trim，@click.stop等，一般用于原生HTML元素，自定义组件需要自行开发支持。
## 插槽
- 普通插槽
- 作用域插槽
## 双向绑定和单项数据流
### 什么是双向绑定
model的更新能触发view的更新
view的更新能触发model的更新
### 什么是单项数据流
model的更新能触发view的更新，view的更新和model没有任何关系
- vue是单项数据流，不是双向绑定
- vue的双向绑定不过是语法糖
- Object.defineProperty 是用来做相应式更新的，和双向绑定没有关系
# 虚拟DOM及key属性的作用
？？？
# 如何触发组件的更新
## 数据驱动
任何直接更改DOM的行为都是在作死！！！
## 数据来源（单向的）
- 来自父元素的属性
- 来自组件的自身的状态 data
- 来自状态管理器，如 vuex,Vue.observable
## 状态data vs 属性props
- 状态是组件自身的数据
- 属性是来自父组件的数据
- 状态的改变未必会触发更新
- 属性的改变未必会触发更新
代码地址：1.4
1.name并没有做响应式

# 计算属性和侦听器
## 计算属性 computed
- 减少模板中计算逻辑
- 数据缓存
- 依赖固定的数据类型（响应式数据）
## 侦听器 watch
- 更加灵活
- watch中可以执行任何逻辑，如函数节流，Ajax异步获取数据，甚至操作DOM
## computed vs watch
- computed能做的，watch都能做到，反之不行
- 能用computed的尽量用computed
# 声明周期的应用场景和函数组件
？？
## 函数式组件
- functional:true
- 无状态、无实例、没有this上下文、无生命周期
# 指令的本质
语法糖、标志位
## 自定义指令
自定义生命周期
# 高级特性 provide-inject
## 组件通信
？？
# 优雅地获取层级组件实例（拒绝递归）
## ref 引用信息
？？
# template 和 JSX对比及他们的本质
## template
- 模板语法（html的拓展）
- 数据绑定使用Mustache语法（双大括号）
## JSX
- JavaScript的语法拓展
- 数据绑定使用单引号







