# 一、gitlab的安装与管理
## 1.安装
```
[root@ci-node1 git_test]# yum install curl policycoreutils openssh-server openssh-clients policycoreutils-python –y

[root@ci-node1 src]# wget https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el7/gitlab-ce-10.0.6-ce.0.el7.x86_64.rpm
[root@ci-node1 src]# rpm -ivh gitlab-ce-10.0.6-ce.0.el7.x86_64.rpm
```
## 2.配置
GitLab 的默认配置文件为于：/etc/gitlab/gitlab.rb，external_url为本机 公网IP 地址或者本机的域名。如下：
```
external_url 'http://11.11.11.11'
```
修改完主配置文件后，使用 gitlab-ctl reconfigure 重新配置 gitlab 
## 3.启动
重新配置执行成功后，我们就可以启动 Gitlab
```
gitlab-ctl restart

# 启动详情
ok: run: gitaly: (pid 17752) 1s
ok: run: gitlab-monitor: (pid 17768) 0s
ok: run: gitlab-workhorse: (pid 17771) 1s
ok: run: logrotate: (pid 17815) 0s
ok: run: nginx: (pid 17821) 1s
ok: run: node-exporter: (pid 17828) 0s
ok: run: postgres-exporter: (pid 17833) 0s
ok: run: postgresql: (pid 17841) 1s
ok: run: prometheus: (pid 17850) 0s
ok: run: redis: (pid 17858) 1s
ok: run: redis-exporter: (pid 17865) 0s
ok: run: sidekiq: (pid 17871) 0s
ok: run: unicorn: (pid 17880) 0s
```
启动后在浏览器中输入：`http://11.11.11.11`访问首次进入要重新设置root用户的密码。
### **问题**：访问遇到502错误
```
502，Whoops, GitLab is taking too much time to respond.
```
解决方案：修改配置文件/etc/gitlab/gitlab.rb，以下两个属性：
```
unicorn['worker_timeout'] = 60
unicorn['worker_processes'] = 3
```
若还是502错误，查看是否占用gitlab所需的端口，如：服务tomcat占用8080端口。  
若问题还没有解决请往下看：
输入命令`free`查看内存占用，显示如下：
```
              total        used        free      shared  buff/cache   available
Mem:        1881700     1782432       74156       53636      125112       35012
Swap:       0      0     0
```
内存占用量很大，没有开交换区，请看此教程开启交换区 https://www.jianshu.com/p/04c7a9ab438c
开启后输入命令`free`：
```
              total        used        free      shared  buff/cache   available
Mem:        1881700     1687132       73776       53636      120792       32484
Swap:       1999996      873728     1126268
```
再次访问`http://11.11.11.11` （笔者改完后再次访问不会立马生效，需要等几分钟）
## 4.gitlab服务构成

GitLab 由主要由以下服务构成，他们共同承担了 Gitlab 的运作需要
Nginx：静态 web 服务器。
gitlab-shell：用于处理 Git 命令和修改 authorized keys 列表。
gitlab-workhorse: 轻量级的反向代理服务器。
logrotate：日志文件管理工具。
postgresql：数据库。
redis：缓存数据库。
sidekiq：用于在后台执行队列任务（异步执行）。
unicorn：An HTTP server for Rack applications，GitLab Rails 应用是托管在这个服务器上面的。
我们可以使用 gitlab-ctl status 命令来查看各服务的状态

## 5.gitlab常用命令
```
# 启动所有 gitlab 组件：
   gitlab-ctl start
# 停止所有 gitlab 组件：
   gitlab-ctl stop
# 停止 postgresql 组件：
   gitlab-ctl stop postgresql
# 停止相关数据连接服务
   gitlab-ctl stop unicorn
   gitlab-ctl stop sidekiq
# 重启所有 gitlab 组件：
   gitlab-ctl restart
# 重启 gitlab-workhorse 组件：
   gitlab-ctl restart gitlab-workhorse
# 查看服务状态
   gitlab-ctl status
# 如果更改了主配置文件 [gitlab.rb 文件],使配置文件生效 但是会初始化除了gitlab.rb 之外的所有文件
   sudo gitlab-ctl reconfigure
# 查看日志
   sudo gitlab-ctl tail
# 检查 redis 的日志
   sudo gitlab-ctl tail redis   
```
参考链接地址：https://www.cnblogs.com/harryblog/p/10863117.html

