# Git 使用笔记

## Git 常用命令

### 初始化

```shell
git init
```

### 生成密钥

```shell
# 使用 rsa 算法生成密钥 -t 指定密钥类型 -C 设置注释文字 -f 指定密钥文件存储文件名
ssh-keygen -t rsa –C "youremail@example.com"
# 命令行执行后会在 /Users/[yourusername]/.ssh 中生成两个文件 id_rsa（私钥）和 id_rsa.pub（公钥）
# 取消 http 的 ssh 校验
git config --global http.sslverify=false
```

#### 验证密钥是否配置成功

​	在 Git Bash 中输入：

```shell
ssh -T -v git@github.com
# 返回下面的消息证明配置成功 -v 打印详细日志
# Hi wxss-0823! You've successfully authenticated, but GitHub does not provide shell access.
```

​	如果报错：

```shell
# 返回 git@github.com: Permission denied (publickey). 说明配置失败
eval `ssh-agent -s`
ssh-add /c/User/[username]/.ssh/id_rsa
```

### 关联远程仓库

```shell
# 在 github 新建 SSH Key，并粘贴 id_rsa.pub 的内容
# 使用 HTTP/HTTPs 添加远程仓库
git remote add origin "http://....git"
# 使用 SSH 添加远程仓库
git remote set-url origin git@github.com:xxx/xxx.git
# 查看远程仓库地址
git remote -v
```

### 配置用户和邮箱

```shell
git config --global user.email "you@example.com"  
git config --global user.name "Your Name"
```

​	或者在 `.git/config` 中添加：

```text
[user]
	name = wxss
	email = 2198993328@qq.com
```

### 配置代理

```shell
# 为 http 与 https 设置全局代理
git config --global http.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890
# 查看全局设置
git config --global -l
# 取消代理配置
git config --global --unset http.proxy
git config --global --unset https.proxy
```

### 克隆仓库到本地

```shell
# 使用 HTTP/HTTPs 克隆
git clone "url"
# 使用 SSH 克隆
git clone "ssh"
```

### 查询状态

```shell
git status
```

### 本地文件上传过程

```shell
# Git将文件分为四个部分，工作区、暂存区、仓库区和远程仓库
# 将指定文件或者所有文件从工作区添加至暂存区
git add filename/.
# 将文件提交至仓库区
git commit filename/. -m "commit log"
# 将文件推送至远程仓库
git push origin main
# 应当注意，若远程仓库修改，本地版本落后于远程，无法推送，可以先获取修改，再推送
git pull origin main
```

- [常用命令](https://www.runoob.com/git/git-basic-operations.html)

## Git遇见的问题

- `fatal: unable to access 'https://github.com/wxss-0823/MathCodes.git/': Failure when receiving data from the peer`
  - 网速太差，换网
- `fatal: refusing to merge unrelated histories`
  - 最后加上`--allow-unrelated-histories`
- `! [remote rejected] master -> master (pre-receive hook declined)`
  `error: failed to push some refs to 'https://github.com/wxss-0823/MathCodes.git'`
  - 超出了github允许的50.00 MB，上传大文件详见[Git Large File Storage](https://git-lfs.github.com. )
- `fatal: unable to auto-detect email address (got 'Wang Xishengshun@DESKTOP-WXSS.(none)')`
  - 未配置 github 用户名和邮箱
- `fatal: unable to access 'https://github.com/xxx/******.git/': Failed to connect to github.com port 443 after 21090 ms: Couldn't connect to server`
  - 使用代理问题，需要指定 `Static Host` 和 `Port`
- ` fatal: The request was aborted: Could not create SSL/TLS secure channel.`
  - 建立 SSH 连接失败，需要检查密钥的配置情况
- `fatal: unable to access 'https://github/wxss-0823/CompanyBackup.git/': Recv failure: Connection was [reset|aborted]`
  - 代理网络问题，检查代理网络是否故障
- `fatal: unable to access 'https://github/wxss-0823/CompanyBackup.git/': OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github:443`
  - 报错 443：网络原因无法使用 http/https 连接仓库，可以换为使用 ssh 连接
