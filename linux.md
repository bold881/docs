# Linux操作知识点

### 1.nginx设置开机启动

systemctl start nginx
systemctl status nginx
systemctl enable nginx (开机启动)

### 2.CentOS7配置

设置IP地址自动获取：

1）输入“vi ifcfg-ens33”并按回车键确定（网卡名称可能不同）。亦可在第二步直接输入“cd /etc/sysconfig/network-scripts/ifcfg-ens33”直接编辑文件。

2）按i插入模式，修改“ONBOOT=yes”，保存退出。

3）输入“service network restart”重启服务,亦可输入“systemctl restart netwrok”。

设置CentOS镜像：

1）备份

```shell
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

2）下载新的 CentOS-Base.repo 到 /etc/yum.repos.d/

```shell
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

或者

```shell
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

3）运行 yum makecache 生成缓存