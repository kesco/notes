# 使用SSL证书登陆Linux服务器

保护服务器一个比较简单的方法是禁止用户密码远程登陆服务器。那么如果不用密码去登陆服务器的话，我们需要用什么作为凭证呢。目前业界比较通用的方法是用SSL证书登陆的。

## 上传SSL证书

用SSL证书登陆比较简单，只需要一步就可以了：

```sh
ssh-copy-id username@remote_host # username是远程服务器用户账号，remote_host是服务器地址
```

## 禁止密码登陆

有了SSL证书的方式登陆后，我们就不需要用密码登陆了。禁用密码登陆的方法也比较简单，只要编辑`/etc/ssh/sshd_config`，修改里面的属性为`PasswordAuthentication no`即可。

