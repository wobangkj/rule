### 后端技术开发规范  

> 背景: 无规矩不成方圆，无规范不能协作. 合理的规范,使得团队在开发上更加高效.

*编程语言: go || java*  
> go新时代流行主流语言,java经典语言,两者均是阿里云,腾讯云支持的主流语言

#### 一.接口开发  
- 知识前提:  
1.[开发]mysql基础知识  
2.[开发]go[go语言基础]或java[java语言基础,熟练掌握spring boot]  
3.[开发]go版根据[demo](https://github.com/dreamlu/deercoder-gin) 运行并学习其中gt业务框架,熟练使用其各种快速开发方法  
4.[运维]linux操作基础  
5.[运维]docker常见命令  

- 开发过程[如无说明,请以go版为例]  
1.下载[go版demo](https://github.com/dreamlu/deercoder-gin) 或者[java版demo](https://gitlab.com/wobangkj/spring-boot)  
2.整理业务整体逻辑  
3.优先建立模型,写完绝大部分crud接口(保证前端调用),提供默认mock数据(mock暂时go版本支持)  
4.格式化请使用ide自带格式化方式  
5.变量和函数命名需要语义化  
6.项目目录结构参考demo  
7.参数命名规范和语义化,如id,指代当前接口的数据表的id字段,如关联其他表id(外健等),请使用`其他表名+_id`表示  
8.每一个接口开发完成,必须通过eolinker(在线接口平台)或_test.go(单元测试)的测试  
9.增删改查常用5个接口名称规范: create/update/delete/search/id, 其他命名语义化  
n.更多定义和使用需要[严格]参考仿照demo  

- go版demo  
1.默认提供了admin/客户/等增删改查/后台登录/文件上传等基本接口  
2.默认提供了使用redis的简要token验证,token要求请求时放入Header中  
3.默认提供了GET请求的mock参数支持  
4.更多内容参考demo中README.md  
5.稳定的开发版本: [demo v1.9.1](https://github.com/dreamlu/deercoder-gin/releases/tag/v1.9.1)  

- 开发经验[阅读](./开发经验/README.md)  

#### 二.部署运帷  
- 部署  
1.单机: docker-compose  最新文档以及脚本参考:[docker-compose](https://github.com/dreamlu/shell/tree/master/docker/docker-compose)  
ps: 如提供了快照备份, 则不需要上述中脚本备份, 直接执行上述链接中`update.sh`脚本即可  
2.多服务: 最新文档参考:[k8s](https://github.com/dreamlu/shell/tree/master/docker/k8s) ,ps:注意内存  

- 运帷  
1.默认使用云平台自带监控(cpu/内存/流量等);其他监控(待定)  
2.注意服务器内存,如果内存太小,请限制程序内存占用  

其他:  
ps: 云开发, 如服务器访问不通, 请优先检查--域名解析/端口开放规则/防火墙/证书是否失效/nginx解析配置等

### 三.数据备份  
- 常规备份  
1.无论客户是否需求,必须默认提供一种备份,快照(推荐,便宜)或脚本(部署运帷中,单机开发的备份脚本)  
2.脚本备份: 需要根据业务,修改备份时间和时长,默认脚本备份数据保留三天    

- 实时备份(待定)  