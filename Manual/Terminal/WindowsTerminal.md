# 终端基础命令

## PowerShell 基础命令

### 可执行文件存在空格

- 空格转义符 `，在空格前加。
- 使用 `&` 取地址，例如：`& 'Clash for Windows'`

### 自动补全命令

#### 自动补全输入历史命令

```shell
Set-PSReadlineOption -PredictionSource History
```

#### 自动补全系统命令

```shell
Set-PSReadLineOption -ShowToolTips
```

#### 设置自动开启

##### 快捷方式添加参数

- 在快捷方式的目标地址后，添加如下代码：自动补全有时候使用 `Tab` ，有时候使用右键。

```shell
-noe -c "&{  Set-PSReadLineOption -PredictionSource History -ShowToolTips}"
```

##### PowerShell 配置文件

-  在 PowerShell 的配置文件里面添加相应的设置，使用 `notepad $PROFILE` 访问配置文件。

```shell
# Shows navigable menu of all options when hitting Tab
Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete

# Autocompletion for arrow keys
Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward

# auto suggestions
Import-Module PSReadLine
Set-PSReadLineOption -PredictionSource History
```

#### 查看输入历史命令

```shell
Get-PSReadLineOption
```

#### 更多操作

​	关于 PowerShell 中的更多自动补全的高级设置，详见[微软官方文档](https://learn.microsoft.com/zh-cn/powershell/scripting/learn/shell/tab-completion?view=powershell-7.4)

### 创建新文件

```shell
type nul>[]
```







