## Docker安装--CentOS

1) 添加依赖项

```shell
$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

2）添加repo

```shell
$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

3) 安装docker

```shell
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

4) 启动docker

```shell
$ sudo systemctl start docker
```

5）自启动docker

```shell
$ sudo systemctl enable docker
```

