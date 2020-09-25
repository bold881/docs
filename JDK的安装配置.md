### Java环境变量的设置

* 下载JDK压缩包，并解压

* 复制JDK目录到/usr/lib/jvm/jdk-xxx

* 修改/etc/profile，在文件末尾添加配置

  ```shell
  export JAVA_HOME=/usr/lib/jvm/jdk-11.0.8+10
  export CLASSPATH=.:${JAVA_HOME}/lib
  export PATH=${JAVA_HOME}/bin:$PATH
  ```

* 运行命令使配置生效

  ```shell
  source /etc/profile
  ```