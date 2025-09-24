### `stunnel.conf` 文件

注意: 内容使用 AI 生成！

注释: 使用 `#` 注释。注释不能放在配置语句之后。

错误的注释:

```
connect = my.domain.com:10086   # 连接到服务端 stunnel 的 TLS 端口
```

正确的注释:

```
# 连接到服务端 stunnel 的 TLS 端口
connect = my.domain.com:10086
```

### 使用 stunnel 代理 SSH 连接

注意: 内容使用 AI 生成！

我使用域名网站生成的证书，生成的证书文件:

```
ca.cer
my.domain.com.cer
my.domain.com.key
```

写入证书文件: `cat my.domain.com.cer ca.cer my.domain.com.key > /etc/stunnel/stunnel.pem`

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
# 私钥是同一个文件，直接不写就行（这里注释掉了）
# key  = /etc/stunnel/stunnel.pem
```

查看服务器端是否启动 `systemctl status stunnel4.service`

客户端配置: `/root/stunnel-test/stunnel.conf`

```
client = yes

[echo_tls_client]
# 本地监听端口
accept = 127.0.0.1:9999
# 连接到服务端 stunnel 的 TLS 端口
connect = my.domain.com:10086
```

客户端运行:

```shell
cd /root/stunnel-test/
stunnel4 stunnel.conf
```

使用 `ps -aux | grep stunnel` 验证 stunnel 是否运行成功。

客户端使用 `ssh -p 9999 root@127.0.0.1` 连接服务器。

我自己配置服务端时遇到了问题，经过排错发现是证书与私钥不匹配导致的，这里给出验证证书与私钥是否匹配的方案:

```shell
# 查看证书的 modulus
openssl x509 -noout -modulus -in mydomain.cer | openssl md5

# 查看私钥的 modulus
openssl rsa  -noout -modulus -in mydomain.key | openssl md5
```

如果两个哈希值一样，说明证书和私钥是匹配的。
