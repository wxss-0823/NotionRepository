# Git使用笔记

### Git基础语法

​	[常用命令](https://www.runoob.com/git/git-basic-operations.html)

### Git遇见的问题

- `fatal: unable to access 'https://github.com/wxss-0823/MathCodes.git/': Failure when receiving data from the peer`
  - 网速太差，换网
- `fatal: refusing to merge unrelated histories`
  - 最后加上`--allow-unrelated-histories`

- `! [remote rejected] master -> master (pre-receive hook declined)`
  `error: failed to push some refs to 'https://github.com/wxss-0823/MathCodes.git'`
  - 超出了github允许的50.00 MB，上传大文件详见[Git Large File Storage](https://git-lfs.github.com. )