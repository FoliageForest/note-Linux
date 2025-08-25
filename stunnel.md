### `stunnel.conf` 文件

注意: 内容使用 AI 生成！

注释: 使用 `#` 注释。注释不能放在配置语句之后。

错误的注释:

```
connect = my.domain:10086   # 连接到服务端 stunnel 的 TLS 端口
```

正确的注释:

```
# 连接到服务端 stunnel 的 TLS 端口
connect = my.domain:10086
```

### 使用 stunnel 代理 SSH 连接

注意: 内容使用 AI 生成！

服务器端配置: `/etc/stunnel/stunnel.conf`

```
# 开启服务端模式
[echo_tls]
# stunnel 接收 TLS 连接的端口
accept = 10086
# stunnel 转发到本地 TCP 服务
connect = 127.0.0.1:22

# TLS 证书配置
cert = /etc/stunnel/stunnel.pem
# key  = /etc/stunnel/stunnel.pem
```

客户端配置: `/root/stunnel-test/stunnel.conf`

```
client = yes

[echo_tls_client]
# 本地监听端口
accept = 127.0.0.1:9999
# 连接到服务端 stunnel 的 TLS 端口
connect = my.domain.com:10086
```
