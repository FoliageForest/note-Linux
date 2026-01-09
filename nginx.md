`nginx -s stop`: fast shutdown  
`nginx -s quit`: graceful shutdown  
`nginx -s reload`: reloading the configuration file  
`nginx -s reopen`: reopening the log files  

示例配置文件（由 AI 生成）:  

```
server {
    listen 443 ssl;
    server_name iamff.run.place;

    ssl_certificate     /root/ssl/fullchain.crt;
    ssl_certificate_key /root/ssl/iamff.run.place.key;

    root /var/www/html;
    index index.html;
}
```
