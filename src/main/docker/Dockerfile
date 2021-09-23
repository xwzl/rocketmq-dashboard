#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
FROM centos:7

#RUN yum install -y java-1.8.0-openjdk-devel.x86_64 unzip gettext nmap-ncat openssl, which gnupg, telnet \
#&& yum clean all -y

# 安装 zip 插件
RUN yum install -y unzip && yum clean all -y
# 添加 jdk jar 包
ADD jdk.zip /usr/local
# 移动 jdk jar 包到自定位置,jak 解压缩后的包在 jdk 中，此版本只适用于 m1 芯片
RUN  cd /usr/local && unzip jdk.zip -d jdk && mv ./jdk/jdk java;

# 配置环境变量
ENV JAVA_HOME /usr/local/java
ENV JRE_HOME /usr/local/java/jre
ENV PATH $JAVA_HOME/bin:$PATH

VOLUME /tmp
ADD rocketmq-dashboard-*.jar rocketmq-dashboard.jar
RUN sh -c 'touch /rocketmq-dashboard.jar'
ENV JAVA_OPTS=""
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar /rocketmq-dashboard.jar" ]
