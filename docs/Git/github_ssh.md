#### 在你的电脑上创建github ssh

1.在电脑上生成一段生成SSH密钥对

```bash
      ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

不保存密码，直接按两次回车键

内容通常保存在~/.ssh/id_rsa.pub (公钥) ~/.ssh/id_rsa (私钥)

复制公钥内容到github

add ssh key 完成后回到，电脑terminal

```bash
      ssh -T git@github.com
```

返回正确信息则连接成功

```bash
Hi iocion! You've successfully authenticated, but GitHub does not provide shell access.
```

