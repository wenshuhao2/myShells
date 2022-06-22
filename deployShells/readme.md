# 高值耗材项目部署
## 环境
- ubuntu16.04
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
对于微服务或者多个软件的安装非常适合。

## 端口约定
## 资源存放路径
## 账号密码
> note:可以提取为环境变量配置，同时如果不配置则使用默认账号。
