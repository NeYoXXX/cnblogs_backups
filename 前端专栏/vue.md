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