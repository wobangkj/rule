### 后端技术开发规范

> 无规矩不成方圆，无规范不能协作. 合理的规范,使得团队在开发上更加高效.

*编程语言: go || java*
> go新时代流行主流语言,java经典语言,两者均是阿里云,腾讯云支持的主流语言

### 一.基础知识(golang || java)

基础|文档|须知
---|---|---
mysql|[文档](https://www.runoob.com/mysql/mysql-tutorial.html)|必须
golang| [文档](https://www.runoob.com/go/go-tutorial.html)|必须
linux| [文档](https://www.runoob.com/linux/linux-tutorial.html)|必须
git| [文档](https://www.runoob.com/git/git-tutorial.html)|必须
docker & docker-compose| [文档](https://www.runoob.com/docker/docker-compose.html)|必须

### 二.关于框架

- GO:

框架|文档|须知
---|---|---  
gt手脚架| [文档](https://github.com/dreamlu/gt)| 必须
gorm| [文档](https://gorm.io/zh_CN/docs/)| 熟悉
gin| [文档](https://github.com/gin-gonic/gin)| 必须
上面为单机开发|以下为微服务开发|
micro| [文档](https://github.com/dreamlu/micro-go)| 微服务必须

- JAVA:

框架|文档|须知
---|---|---  
spring boot| | 必须
上面为单机开发|以下为微服务开发|
spring cloud| | 必须

### 三.接口开发

- GO:

demo|文档|场景
---|---|---  
gt-crud|[下载](https://github.com/dreamlu/gt-crud/archive/v1.20.5.zip)| 单机
micro-go|[下载](https://github.com/dreamlu/micro-go/archive/v1.20.5.zip)| 单机

- JAVA:

demo|文档|场景
---|---|---  
spring-boot|[链接](https://gitlab.com/wobangkj/spring-boot)| 单机
spring-cloud|[链接](https://gitlab.com/wobangkj/spring-cloud)| 微服务

- 开发过程[如无说明,请以go版为例]  
  1.整理业务整体逻辑  
  2.优先建立模型,写完绝大部分crud接口(保证前端调用),提供默认mock数据(mock暂时go版本支持)  
  3.格式化请使用ide自带格式化方式  
  4.变量和函数命名需要语义化  
  5.项目目录结构参考demo  
  6.参数命名规范和语义化,如id,指代当前接口的数据表的id字段,如关联其他表id(外健等),请使用`其他表名+_id`表示  
  7.每一个接口开发完成,必须通过eolinker(在线接口平台)或_test.go(单元测试)的测试  
  n.更多定义和使用需要[严格]参考仿照demo 
  

- go版demo  
  1.默认提供了admin/客户/等增删改查/后台登录/文件上传等基本接口  
  2.默认提供了使用redis的简要token验证,token要求请求时放入Header中  
  3.默认提供了GET请求的mock参数支持  
  4.更多内容参考demo中README.md  
  

- go版单元测试  
  1.代码同级目录下建立`包名_test.go`  
  2.测试的函数方法名要和测试的方法名一一对应  
  3.不得写无限循环之类的测试，测试要有限次  
  4.最后：项目根目录下，执行：  
  `go test ./...` 或 `go test ./... | grep -v 'no test files'`  
  确保单元测试全部通过 
  n...

- 开发经验[阅读](./开发经验/README.md)

### 四.部署运帷

- 部署  
  1.单机: docker-compose 最新文档以及脚本参考:[docker-compose](https://github.com/dreamlu/shell/tree/master/docker/docker-compose)  
  ps: 如提供了快照备份, 则不需要上述中脚本备份, 直接执行上述链接中`update.sh`脚本即可  
  2.分布式: 最新文档参考:[k8s](https://github.com/dreamlu/shell/tree/master/docker/k8s) ,ps:注意内存 
  

- 运帷  
  1.默认使用云平台自带监控(cpu/内存/流量等);其他监控(待定)  
  2.注意服务器内存,如果内存太小,请限制程序内存占用

Tips:  
ps: 云开发, 如服务器访问不通, 请优先检查--域名解析/端口开放规则/防火墙/证书是否失效/nginx解析配置等

### 五.数据备份

- 常规备份  
  1.无论客户是否需求,必须默认提供一种备份,快照(推荐,便宜)或脚本(部署运帷中,单机开发的备份脚本)  
  2.脚本备份: 需要根据业务,修改备份时间和时长,默认脚本备份数据保留三天

- 实时备份(待定)  