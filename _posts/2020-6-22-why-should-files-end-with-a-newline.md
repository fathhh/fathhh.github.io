## cat输出文件时会在末尾自动加上换行吗

> 今天带电脑来公司，想着加上 vscode remote authorized_keys，却发现只有最后的key生效，原本我以为ssh keychain抽风了，重置一次依然如旧。猛然输出authorized_keys发现只有一行。

编辑文件时，nano/vi都有换行，并没有意识到cat不会自动加换行，解决办法是提前加入一个换行符

```bash
echo -e '\n' >> ssh.pub
cat ssh.pub x.pub y.pub >> authorized_keys
service sshd start
ssh -T git@remote target
```

[Reference]: https://blog.csdn.net/hoxily/article/details/44242783

