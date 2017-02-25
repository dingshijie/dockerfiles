# dockerfiles
###[centos-jdk8-tomcat8](https://github.com/dingshijie/dockerfiles/tree/master/centos-jdk8-tomcat8)	
```Bash
cd dir #dir为DockerFile所在目录
docker run build -t 镜像名称 .  #构建镜像，其中最后一个英文点不可少
docker run -i -t --name container-name -p 8080:8080 镜像ID或名称 /bin/bash #以交互模式启动一个容器,在容器内执行/bin/bash命令
```
