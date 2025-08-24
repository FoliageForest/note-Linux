使用 `nohup ./bash.sh &` 让 VPS 在 SSH 断开后继续进行下载


```
aria2c --listen-port=6962 --dht-listen-port=6994 --seed-ratio=100.0 --max-overall-download-limit=128K --max-overall-upload-limit=1024M 'https://releases.ubuntu.com/24.04/ubuntu-24.04.3-desktop-amd64.iso.torrent'
```



```
--max-overall-download-limit=<SPEED>
--max-overall-upload-limit=<SPEED>
--seed-ratio=<RATIO>
--listen-port=<PORT>...
--dht-listen-port=<PORT>...
--console-log-level=<LEVEL>
```
