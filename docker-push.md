# 在虚拟机下操作docker push <image>时报https连接错误

## Question:

```
root@ubuntu:/usr/local/docker/itoken-config/docker# docker push 192.168.191.131:5000/itoken-config
<font color=#ff0000 >The push refers to repository [192.168.191.131:5000/itoken-config]</font>
<font color=#f00 >Get https://192.168.191.131:5000/v2/: http: server gave HTTP response to HTTPS client</font>
```

## Environment:

`Ubuntu docker-18.09.0`

`docker镜像地址：192.168.191.131:5000`

## Solution:

1. 在/etc/docker下，修改daemon.json文件，写入：
  ```
  {
    "insecure-registries": [
      "192.168.191.131:5000"
    ]
  }
  ```

2. 重启docker

  `systemctl restart docker.service`
