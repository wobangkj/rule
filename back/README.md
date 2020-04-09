### 后端技术开发规范  

> 背景: 无规矩不成方圆，无规范不能协作. 合理的规范,使得团队在开发上更加高效.

*编程语言: go || java*  
> java经典语言,go新时代流行主流语言,两者均是阿里云,腾讯云支持的主流语言

#### 一.接口开发  
- 知识前提:  
1.mysql基础知识  
2.go[go语言基础]或java[java语言基础,熟练掌握spring boot]  
- 开发过程[如无说明,请以go版为例]  
1.下载[go版demo](https://github.com/dreamlu/deercoder-gin)或者[java版demo](https://gitlab.com/wobangkj/spring-boot)  
- go版demo  
1.默认提供了admin/客户/等增删改查/后台登录/文件上传等基本接口  
2.默认提供了使用redis的简要token验证,token要求请求时放入Header中  
3.更多内容参考demo中README.md  
4.稳定的开发版本: TODO  
- 开发经验[阅读](./开发经验/README.md)  
#### 二.部署运帷  
1.单机: docker-compose  最新文档以及脚本参考:[docker-compose](https://github.com/dreamlu/shell/tree/master/docker/docker-compose)  
ps: 如提供了快照备份, 则不需要上述中脚本备份, 直接执行上述链接中`update.sh`脚本即可  

2.多服务: 最新文档参考:[docker-compose](https://github.com/dreamlu/shell/tree/master/docker/k8s)  

### 三.数据备份  
1.无论客户是否需求,必须默认提供一种备份,快照(推荐,便宜)或脚本(部署运帷中,单机开发的备份脚本)  
2.脚本备份: 需要根据业务,修改备份时间和时长,默认脚本备份数据保留三天  
