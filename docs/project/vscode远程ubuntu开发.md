## linux使用指南

#### 1.查看系统信息

```bash
hostname
whoami
uname
```

```bash
whereis python
whatis python
which python
```

#### 2.接受网络资源

```bash
wget
curl
```

#### 3.显示文件内容

```bash
cat
less
head
tail
cmp 
diff
sort 
find / -name "file.*"
find . -type f -name ".*"
find . -type f -empty
find . -perm /a=x
```

#### 4.尽可能少使用mv命令,改用使用cp命令

```bash
我在使用命令的时候由于使用了 mv
mv pr /project 之后，提示我要使用sudo，感觉不太对劲，使用了sudo之后 cd project 发现文件内容为空
原来是由于/的原因，导致pr移动到根目录下的位置，然后改名project了
通过这个事件，告诉我备份的重要性，可以使用testdisk进行回档，但是我不太会用
所以移动文件应该使用 cp 命令
```



