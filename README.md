# dockerfiles相关说明
###[centos-jdk8-tomcat8](https://github.com/dingshijie/dockerfiles/tree/master/centos-jdk8-tomcat8 "点击查看")	
```Bash
#进入Dockerfile所在目录，dir为DockerFile所在目录
cd dir

#构建镜像，其中最后一个英文点不可少
docker run build -t 镜像名称 .  

#以交互模式启动一个容器,在容器内执行/bin/bash命令，就可以在容器中做想做的操作了，比如安装openssh-server
docker run -i -t --name container-name -p 8080:8080 镜像ID或名称:TAG /bin/bash 
```

>tips: 
  1. server.xml和tomcat-user.xml在构建镜像时均会被复制到tomcat的conf文件夹中并对应覆盖原有文件。

###[centos-jdk8-tomcat8-v2.0](https://github.com/dingshijie/dockerfiles/tree/master/centos-jdk8-tomcat8-v2.0 "点击查看")
```Bash
#进入Dockerfile所在目录，dir为DockerFile所在目录
cd dir

#构建镜像，其中最后一个英文点不可少
docker run build -t 镜像名称 .  

#后台运行容器，并将宿主机的/test目录挂载到容器的/home/apache-tomcat-8.5.11/webapps/目录
docker run -d --name comtainer-name -p 8080:8080 -v /test:/home/apache-tomcat-8.5.11/webapps/ 镜像ID或名称:TAG
```
>tips: 
  1. server.xml和tomcat-user.xml在构建镜像时均会被复制到tomcat的conf文件夹中并对应覆盖原有文件。
  2. 宿主机目录如果不存在，则会自动生成；容器目录不可以为相对路径。
  3. 宿主机目录为相对路径时,容器内的/home/apache-tomcat-8.5.11/webapps/目录挂载的是宿主机上的/var/lib/docker/volumes/test/\_data目录，所谓的相对路径指的是/var/lib/docker/volumes/，与宿主机的当前目录无关。
