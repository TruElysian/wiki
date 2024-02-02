---
title: Debian 配置 SSH
tags:
- Debian
- Linux
- SSH
---

# Debian 配置 SSH

基于 Debian 12 进行配置

## Install SSH

---

安装命令

```sh
sudo apt install openssh-server
```

服务状态命令

```sh
sudo systemctl status ssh.service

sudo systemctl restart ssh.service
```

## Generate SSH Key

---

```sh
# 生成 ssh 密钥对
ssh-keygen -t rsa -b 4096
```

将 `id_rsa` 文件保存到本地计算机中并注意保密

一般会生成在 `.ssh/` 目录下，如果没有则进行以下步骤，如果有则跳过以下步骤

创建目录和文件，移动文件，更改权限

```sh
mkdir .ssh
mv id_rsa .ssh/
mv id_rsa.pub .ssh/

cd .ssh/
touch authorized_keys
cat id_rsa.pub >> authorized_keys
chmod 0600 authorized_keys
chmod 0600 id_rsa
chmod 0644 id_rsa.pub
cd ../ && chmod 700 ~/.ssh
```

## SSH 加固

---

### 编辑 SSH 配置

编辑配置文件

```sh
sudo nano /etc/ssh/sshd_config
```

```conf
# 禁止使用密码登入
PasswordAuthentication no
# 禁止空密码账户登入
PermitEmptyPasswords no

# 禁止 root 账户通过 SSH 登入
PermitRootLogin no

# 启用严格模式 需保证存放公钥的文件夹的拥有者与登陆用户名是相同的
StrictModes yes

# 将压缩延迟到身份认证后
Compression delayed

# 限制最大身份验证尝试次数
MaxAuthTries 3

# 显示最后一次登录的日期和时间
PrintLastLog yes

# 900s 后关闭不活动的会话
ClientAliveInterval 900

# 发送客户端探活消息达到此阈值，则 sshd 服务端将终止会话
ClientAliveCountMax 0

# 指定白名单用户
AllowUsers Bob Alan

# 指定黑名单用户
DenyUsers root
```

### 在 UFW 中配置 SSH

```sh
sudo ufw allow from <ip> to any port <ssh-port>
sudo ufw deny <ssh-port>
```

## Source Link

---

- [【教程】SSH 分析及安全设置](https://pa.ci/18.html)
- [SSH 安全加固的一些措施](https://zzz.buzz/zh/2016/04/18/hardening-sshd/)
- [SSH 安全加固指南](https://www.freebuf.com/articles/system/246994.html)
- [A Guide to Securing the SSH Daemon](https://www.putorius.net/how-to-secure-ssh-daemon.html)
