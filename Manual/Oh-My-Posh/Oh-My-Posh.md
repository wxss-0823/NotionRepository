#  美化 Windows Powershell

## 安装

以管理员身份打开 PowerShell，输入：

```shell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

或者直接再 Github 库中下载，`install-amd64.exe`

## 设置排除项

终端输入：

```shell
(Get-Command oh-my-posh).Source
```

查询文件地址，添加至杀毒排除项。

## 更新

```shell
winget upgrade JanDeDobbeleer .OhMyPosh -s winget
```

## 安装字体

为了保证正确显示，安装 Nerd Font。Github 中为：`FiraCode Nerd Fond Mono`

## 美化

- 修改终端字体为 Nerd；

- 修改透明度为 80 左右；

- 在 ...\oh-my-posh\themes 下存放着全部的主题文件，终端输入下述命令后，即可完成终端主题的配置，但是配置无法保存，重启后配置消失。

  ```shell
  oh-my-posh init pwsh --config '...\oh-my-posh\themes\{主题文件名}.json' | Invoke-Expression
  
  oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\pure.omp.json" | Invoke-Expression
  ```

- 如果想要保存配置，需要按照如下步骤：

  - 创建配置文件

    ```shell
    New-Item -Path $PROFILE -Type File -Force
    ```

  - 编辑配置文件

    ```shell
    notepad $PROFILE
    ```

    输入后，会打开先前创建的配置文件，配置文件的路径为：

    ```shell
    C:\Users\{UserName}\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
    ```

  - 在配置文件中输入：

    ```shell
    oh-my-posh init pwsh --config '...\oh-my-posh\themes\{主题文件名}.json' | Invoke-Expression
    ```

  - 每次更改配置文件后需要重新加载配置

    ```shell
    .$PROFILE
    ```

## 报错

- 报错：`未对文件XXX进行数字签名。无法在当前系统上运行该脚本。`

  - 首次在计算机上启动 Windows PowerShell 时，现用执行策略很可能是 Restricted（默认设置）。Restricted 策略不允许任何脚本运行。所以需要开启运行脚本。

  - 终端输入命令：

    ```shell
    set-ExecutionPolicy RemoteSigned //设置为打开,选择Y
    get-executionpolicy				 //查看是否更改成功，为RemoteSigned表示成功
    ```

- 报错：Get-PSReadLineKeyHandler : 找不到接受实际参数“Spacebar”的位置形式参数。
  - 根据 `https://github.com/JanDeDobbeleer/oh-my-posh/issues/3136#issuecomment-1328544012` 中，开发者的指示，需要升级PSReadLine。
  - 根据 `https://github.com/PowerShell/PSReadLine#install-from-powershellgallery-preferred` 的指示，升级PSReadLine即可。