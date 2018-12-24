# 在CentOS 7下安装docker

## Environment:

`CentOS 7`

## Solution:
1. 换国内镜像源
```
$ mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
$ wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
$ yum makecache
$ yum -y update
```

2. 使用脚本安装docker
```
$ curl -fsSL get.docker.com -o get-docker.sh
$ sh get-docker.sh --mirror AzureChinaCloud
```

3. 启动docker
```
$ systemctl start docker
```

4. 设置docker加速器
```
$ cd /etc/docker
$ vi daemon.json

{
  "registry-mirrors": [
    "https://registry.docker-cn.com"
  ]
}
```
