# Redis随笔
## 一、网络部分
### 1.默认配置文件位置 /etc/redis/redis.conf
### 2.bind绑定可以访问的IP地址，如：127.0.0.1 ::1只监听当前机器的连接
### 3.protected-mode, 保护模式默认打开。保护模式打开时，若bind没有绑定具体的地址且密码没有设置，则只接受本地的连接
### 4.port,端口默认6379。若端口设置为0，则redis不在TCP socket监听
### 5.tcp-backlog 511 ?
### 6.unixsocket默认是关闭的
* unixsocket /var/run/redis/redis-server.sock
* unixsocketperm 700
### 7.timeout 当一个客户端连接空闲时超过timeout配置时间时，redis会关闭当前连接单位秒，0为禁用此功能
### 8.tcp-keepalive，tcp连接保持，当客户端无数据发送时，用SO_KEEPALIVE发送tcp握手信息，两个有点：
* 1检测客户端是否已经断开
* 2保持网络连接不断开* 从Redis 3.2.1默认为300秒
# 二、通用部分
### 1.daemonize yes 后台运行
### 2.supervised no ?
### 3. pid文件，如果pid文件指定了,redis启动时会记录pid到文件中，退出时会删除。
* 非后台运行时，如果没有指定pid文件位置，则不会创建pid文件。
* 后台运行时，如果没有指定pid文件，默认位置为/var/run/redis.pid。
* 最好创建pid文件，如果没有创建pid文件，redis也可以正常运行。
### 4.loglevel, 日志记录层级，debug > verbose > notice > warning 
* notice,展示适度的提示信息，适用生产环境
### 5.logfile，配置日志记录文件，若配置为空，这日志输出到标准输出（standard output），如果是标准输出且后台话运行了，日志会被输出到/dev/null#默认配置文件为 /var/log/redis/redis-server.log
### 6.syslog-enabled，日志输出到系统日志只需配置syslog-enabled yes
### 7.syslog-ident redis，系统日志标识
### 8.syslog-facility ? 必须是USER或者是local0 到local7
### 9.databases 16 ?
### 10.always-show-logo，通常只在可交互对话框中才展示ASCII logo，配置yes会强制显示logo
# 三、镜像
### 1.save，镜像存储，当时间和变更满足时则存储db，如：(时间秒 写入次数）
* save 900 1
* save 300 10
* save 60 10000
* 注释掉所有的save则会完全禁用saving，或者save ""
### 2.stop-writes-on-bgsave-error，yes或者注释掉。
* 默认如果后台备份失败，redis会停止接受新的写入请求，好让用户感知到有错误发生，数据没有正确写入。
* 如果后台写入恢复了，redis会继续接受新的写入请求。
* 如果对redis有合适的监测，则可以禁用此选项，当磁盘相关的错误发生时，redis会继续接受新的写入请求。
### 3.rdbcompression， 当dump .rdb数据库时是否启用LZF压缩，默认启用压缩。如果想保存一些CPU in saving child把rdbcompression设置为no，不压缩，保存文件会相对于压缩大。
### 4.rdbchecksum，从版本5开始，一个CRC64的校验码会放在文件的末尾，以防止文件损坏。启用时对于读取或保存rdb文件会多出10%的开销。如果为了达到极限性能，可以no禁用当前选项。
* 校验为zero，会告知加载代码跳过checksum检验。
### 5.dbfilename dump.rdb， dump文件名称配置
### 6.dir,工作目录配置。dbfilename配置的dump文件名称文件会被保存在当前目录中。追加文件也会被写入在当前文件中。注意dir需配置为一个目录路径。如：/var/lib/redis
# 四、备份（replication）
### 1.利用slaveof使一个Redis复制另外一个Redis。
* Redis的拷贝是异步的，但是可以配置当master的备份数量少于给定的值时，停止接受新的写入请求。* 当同master的连接丢失了一小段时间，Redis从属对象可以从master进行局部重新同步。可以根据需要设置backlog的大小
* 拷贝是自动进行的，不需要人工干预。在进行网络划分之后，从属实例会自动重连master并同步。
* `slaveof <masterip> <masterportn>`
### 2.如果master是密码保护的，通过requirepass，从属Redis知道在进行拷贝同步之前需要进行认证，否则master会拒绝slave的拷贝请求。
* `masterauth <mater-password>`
### 3.slave-serve-stale-data，当备份节点失去了和master的连接或者拷贝正在进行，备份节点有两种不同的表现形式：
* 设置yes，从属节点仍会相应客户端请求，可能包含过期的数据，如果是首次同步，可能是空数据。
* 设置no，对于大部分命令从属节点会返回“SYNC with master in progress"，除了INFO和SLAVEOF命令。
