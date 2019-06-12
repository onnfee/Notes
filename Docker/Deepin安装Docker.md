# Deepin安装Docker-ce
- 安装docer-ce、密钥管理、下载相关的工具
```bash
sudo apt-get install apt-transport-https ca-certificates curl python-software-properties software-properties-common
```
- 下载并安装密钥
```shell
# Deepin基于debian
# 这里用中国科技大学源
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/debian/gpg | sudo apt-key add -
```

- 添加docer仓库

```shell
sudo add-apt-repository "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/debian jessie stable"
```

- 安装docker-ce

```shell
# 更新本地软件仓库
sudo apt-get update
# 安装docker-ce
sudo apt-get install docker-ce
# 命令行查看docker版本
docker version
```

- 当前用户加入docer用户组

```shell
# username替换为当前用户，注销后生效
sudo usermod -aG docker username
```

- hello world

```shell
docker run hello-world
```

- docer官方源

```
https://download.docker.com/
```
