
# 高值耗材项目部署
## 环境
- ubuntu 16.04
- jdk1.8
- docker & docker-compose
- 应用版本：v2.9.4.17
## 为什么选择docker-compose
> 由于项目现场通常是**离线环境**，安装软件（nginx/mysql/ftp/redis/rabbitmq/elasticsearch/mongodb/）需要很多依赖，操作不太方便，而docker可以很好的解决这个问题。而且docker还有很多优点。比如：
1. 更高效的利用系统资源
2. 启动更快
3. 保证运行环境的一致性
4. 持续交付和部署
5. 方便迁移
6. 方便维护和扩展

> docker-compose是用于定义和运行多容器Docker应用程序的工具。通过docker-compose，可以使用YAML文件来配置应用程序的服务。然后，使用一个命令，就可以从配置中创建并启动所有服务。
> Docker-Compose是一个容器编排工具。通过一个.yml或.yaml文件，将所有的容器的部署方法、文件映射、容器端口映射等情况写在一个配置文件里，执行docker-compose up命令就像执行脚本一样，一个一个的安装并部署容器。
对于微服务部署或者多个软件的安装非常适合。

## 端口约定
- 基础应用

|mysql|3306|
|:--:|:--:|
|ftp  |21  |
|redis|6379|
|rabbitmq|后台:5672  web:15672|
|elasticsearch|后台:9300  web:9200|
|mongodb|27017|
|portainer|后台:8000  web:9000|
|nginx|管理端访问端口:8050, FTP文件服务端口:8051, 代理网关端口:8070|
> 可以手动在docker-compose.yml文件中修改基础应用暴露的端口。
- 高值app

|eureka|8761|
|:--:|:--:|
|gateway|9527|
|bdm|8030|
|hvc|8022|
|print|8052|
|log|8029|
> 可以手动修改脚本变量，修改默认应用端口。

## 资源存放路径
>data
>>resources
>>>baseApp
>>>
>>>configFiles
>>>
>>> dockerResource
>>> 
>>>jdk-8u231-linux-x64.tar.gz
>>>
>>>ntp
>>>
>>> vimdebs
>>> 
>>rivaApp
>>>bdm-2.9.4.16
>>>
>>>eureka-2.9.4.0
>>>
>>>gateway-2.9.4.0
>>>
>>>hvc-dept-2.9.4.16
>>>
>>>log-service-2.9.4.16
>>>
>>>spd-print-2.9.4.0
>>>
>>>webapp-2.9.4.16
>>>
>>startShells
>>>deployJdk.sh
>>>
>>>initShells
>>>
>>>startBaseApp.sh
>>>
>>>startRivaApp.sh
   

## 账号密码
> note:可以提取为环境变量配置，同时如果不配置则使用默认账号。
### mysql
- 数据库名称
    默认是"ispd_"+"应用名称" eg:ispd_bdm/ispd_hvc/ispd_print
- MYSQL_USER:root
- MYSQL_PASSWORD:Rivamed@2018
### rabbitmq
- MQ_USER=rivamed
- MQ_PASSWORD=rivamed
### ftp
- FTP_USER=uftp
- FTP_PASSWORD=1234
### redis && mongodb
- 未开启认证
    
## 配置
- application-deploy.properties
    
    TODO 数据库名称，默认是"ispd_"+"应用名称" eg:ispd_bdm/ispd_hvc/ispd_print
- application-public.yml
    
    ftpPath: /
- default_ng.conf
    1. 网关IP为本机IP
    2. web存放目录/data/nginx/html
    3. ftp存放目录/home/uftp/recpserfile(文件存放目录)
- ./eureka/config/application.yml
    
    配置mq信息，默认连接是使用guest用户，不配置会抛异常。
- config.json
    
    CONFIG_JSON_PORT=8070


