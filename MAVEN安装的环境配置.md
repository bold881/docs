### MAVEN安装的环境配置

* 下载maven要所包到本并解压

* 复制解压后的目录到/opt/apache-maven-3.6.3

* 修改/etc/profile配置文件，在文件末尾添加如下内容

  ```sh
  M2_HOME='/opt/apache-maven-3.6.3'
  PATH="$M2_HOME/bin:$PATH"
  export PATH
  ```

* 执行如下命令是配置生效

  ```shell
  source /etc/profile
  ```

  