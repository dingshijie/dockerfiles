FROM centos:latest 

# 刷新包缓存 并且 安装wget工具
RUN yum -y update && yum install -y wget

# 配置编码
ENV LANG en_US.UTF-8

# 配置时区
RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN /bin/echo -e "ZONE="Asia/Shanghai"\nUTC=false\nRTC=false" > /etc/sysconfig/clock


# 设置工作目录
WORKDIR /home
# 安装jdk8
RUN wget --no-cookies --no-check-certificate --header "Cookie:gpw_e24=http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html;oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u101-b13/jdk-8u101-linux-x64.tar.gz
RUN tar -zxf jdk-8u101-linux-x64.tar.gz


# 配置环境变量
ENV JAVA_HOME /home/jdk1.8.0_101
ENV JRE_HOME $JAVA_HOME/jre
ENV CLASSPATH .:$JAVA_HOME/lib:$JRE_HOME/lib
ENV PATH $PATH:$JAVA_HOME/bin

# 安装 tomcat8
RUN wget http://mirrors.hust.edu.cn/apache/tomcat/tomcat-8/v8.5.11/bin/apache-tomcat-8.5.11.tar.gz
RUN tar xvf apache-tomcat-8.5.11.tar.gz

# 替换tomcat配置文件
COPY tomcat-users.xml /home/apache-tomcat-8.5.11/conf/
COPY server.xml /home/apache-tomcat-8.5.11/conf/

# 配置tomcat的环境变量
ENV CATALINA_HOME /home/apache-tomcat-8.5.11
ENV CATALINA_BASE /home/apache-tomcat-8.5.11
ENV CATALINA_PID  /var/run/tomcat8.5.11.pid
ENV CATALINA_SH   /home/apache-tomcat-8.5.11/bin/catalina.sh
ENV CATALINA_TMPDIR /tmp/apache-tomcat-8.5.11-tmp

RUN mkdir -p $CATALINA_TMPDIR

VOLUME ["/home/apache-tomcat-8.5.11/webapps/"]

EXPOSE 8080

# 设置tomcat 自启动
ENTRYPOINT [ "/home/apache-tomcat-8.5.11/bin/catalina.sh", "run" ]


