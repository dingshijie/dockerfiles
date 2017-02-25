# dockerfiles
###[centos-jdk8-tomcat8](https://github.com/dingshijie/dockerfiles/tree/master/centos-jdk8-tomcat8)	
```Bash
#进入Dockerfile所在目录，dir为DockerFile所在目录
cd dir

#构建镜像，其中最后一个英文点不可少
docker run build -t 镜像名称 .  

#以交互模式启动一个容器,在容器内执行/bin/bash命令，就可以在容器中做想做的操作了，比如安装openssh-server
docker run -i -t --name container-name -p 8080:8080 镜像ID或名称 /bin/bash 
```
