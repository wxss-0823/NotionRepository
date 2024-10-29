# Git使用笔记

## Git基础语法

- 初始化

```
git init
```

- 生成密钥

```shell
# 使用rsa算法生成密钥
ssh-keygen -t rsa –C "youremail@example.com"
# 命令行执行后会在/Users/[yourusername]/.ssh中生成两个文件id_rsa（私钥）和id_rsa.pub（公钥）
```

- 关联远程仓库

```
# 在github新建SSH Key，并粘贴id_rsa.pub的内容
# 添加远程仓库
git remote add origin "http://....git"
```

- 克隆仓库到本地

```
git clone "url"
```

- 查询状态

```
git status
```

- 本地文件上传过程

```
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