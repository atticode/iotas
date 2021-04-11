

## WSL 安装
### WSL 安装文档
[WSL 安装文档](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10#manual-installation-steps)

### 安装路径
C:\Users\admin\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu20.04onWindows_79rhkp1fndgsc\LocalState


## WSL 安装Docker
### Ubuntu
1. 移除旧版本
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```
2. 更新
```
sudo apt-get update
```

3. 安装依赖
```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

4. Add Docker’s official GPG key:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

5. set up the stable repository
```
 echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

6. INSTALL DOCKER ENGINE
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

7. 添加当前用户到 docker 组
```
sudo gpasswd -a $USER docker
newgrp docker

```

```
systemctl daemon-reload
```

### 常见问题
1. Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
解决: 执行`systemctl daemon-reload`