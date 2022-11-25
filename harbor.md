
[ref](https://ithelp.ithome.com.tw/articles/10249640)
[ref](https://medium.com/starbugs/%E7%94%A8-harbor-%E6%9E%B6%E8%A8%AD%E7%A7%81%E6%9C%89-docker-%E5%80%89%E5%BA%AB-9e7eb2bbf769)

```sh
$ wget https://github.com/goharbor/harbor/releases/download/v2.0.2/harbor-offline-installer-v2.0.2.tgz
$ tar -xvf harbor-offline-installer-v2.0.2.tgz
$ cd harbor
$ tree .
.
├── common.sh
├── harbor.v2.0.2.tar.gz
├── harbor.yml.tmpl
├── install.sh
├── LICENSE
└── prepare

$ sudo ./install.sh

cat /etc/docker/daemon.json
{
    "experimental": true,
    "debug": true,
    "log-level": "info",
    "insecure-registries": ["192.168.0.7"],
    "hosts": ["unix:///var/run/docker.sock", "tcp://0.0.0.0:2375"],
    "tls": false,
    "tlscacert": "",
    "tlscert": "",
    "tlskey": ""
}    
    
```
docker login --username admin --password 1313  https://192.168.0.7


# 準備一個 harbor.yml 的設定檔案
# 執行 prepare 這個腳本，此腳本會讀取 harbor.yml 的設定檔案，並根據此產生一個合適的 docker-compose 檔案
# 最後根據運行產生出來的 docker-compose 檔案即可