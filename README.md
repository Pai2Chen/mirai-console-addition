# mirai-console-addition
<a href = "https://github.com/mamoe/mirai-console">mirai-console</a>的扩展插件，提供对console功能的增强
<p>重写于<a href = "https://github.com/ryoii/mirai-console-addition/">ryoii/mirai-console-addition</a>

### 使用

将该插件放入`plugins`目录下，并修改`plugins/ConsoleAddition`目录下的配置文件

### 功能一览

+ [x] [MD5密码登录](#md5密码登录)
+ [x] [保存MD5密码，并自动登录](#自动登录)
+ [ ] [欢迎讨论和贡献代码][Issue]



### 配置文件
```yaml
## config/Console-Addition/top.fan2tao.mirai.consoleaddition.AdditionBase.PluginConfig
autologin: 
  enabled: true
  qq: 0
  passwd: 1E5CE73F4FC4C3B764FB66811F093C87
md5login: 
  enabled: true

```

> 设置为false关闭指定子功能


### 管理命令
`Console Addition`提供一个复合命令经行管理子功能

```
/addition:
    reload #重载插件
    enable 子功能名（autologin / md5login） #启用子功能
    disable 子功能名（autologin / md5login） #禁用子功能
```

### md5密码登录

`Console Addition`提供了新的Command进行md5登录

```
/md5login qq md5
```

> md5密码为32位md5。
> md5密码是QQ的登录方式，相对于明文密码较安全。
> 但md5密码的丢失，依旧会导致QQ被他人登录。

### 自动登录

`Console Addition`提供了新的Command进行自动保存密码，并在下次启动时，对于保存密码的账号进行自动登录

```
/autologin qq password
```

> 为保留正常登录（不保存密码）的模式，自动登录采用了新的命令作为入口。
> 自动登录保存的是用户的md5密码，保存在config/Console-Addition/top.fan2tao.mirai.consoleaddition.AdditionBase.PluginConfig内autologin字段中

```yaml
## config/Console-Addition/top.fan2tao.mirai.consoleaddition.AdditionBase.PluginConfig

autologin: 
  enabled: true
  qq: 12345678911
  passwd: 1E5CE73F4FC4C3B764FB66811F093C87

```

> 该文件保存自动登录的信息，不建议手动修改


### FAQ.

#### 重写该插件的目的

原先的[Console-Addition][Console-AdditionOld]是对[Mirai-Console][Mirai-Console]功能的扩展，方便插件开发者和使用者。
但新版本的console推出后，该插件不兼容新版console，便参照原先的插件写了个新的插件。
同时该项目可以作为一个插件开发的例子，供想要对`Mirai`贡献插件的开发者参考。


#### 为什么没有某某某功能

这里，并不实现复杂的逻辑功能。只针对日常开发测试和使用中，能够方便开发者和使用者的功能，进行补充。
如您需要高定制化的功能，可以寻找其他插件，或在[Issue][Issue]中进行讨论。

#### 某某功能会被移除吗

随着[Mirai-core][Mirai-core]和[Mirai-Console][Mirai-Console]的完善，[Console-Addition][Console-Addition]的功能会逐步被取代。



[Console-Addition]: https://github.com/Pai2Chen/mirai-console-addition
[Console-AdditionOld]: https://github.com/ryoii/mirai-console-addition
[Mirai-core]: https://github.com/mamoe/mirai
[Mirai-Console]: https://github.com/mamoe/mirai-console
[Issue]: https://github.com/Pai2Chen/mirai-console-addition/issues
