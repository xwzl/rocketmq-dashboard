# azul-jdk.zip 包

下载好后，放在当前目录即可

# windows 下 mvn docker 无效

把 rocketmq-dashboard-1.0.1-SNAPSHOT.jar 拷贝到当前目录下，Dockerfile-intel 文件内容复制到 Dockerfile 中，执行以下命令直接打镜像

    build -t rocketmq-dashboard:1.0.1 .