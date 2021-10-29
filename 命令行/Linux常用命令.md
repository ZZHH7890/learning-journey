<!--
 * @Author: joker.zhang
 * @Date: 2021-07-21 10:28:40
 * @LastEditors: joker.zhang
 * @LastEditTime: 2021-07-21 10:29:25
 * @mail: zhanghua7890@163.com
-->
# Linux
不想安装Linux的同学（比较穷的同学，比如我）可以直接在线练习
https://bellard.org/jslinux/vm.html?cpu=riscv64&url=fedora33-riscv.cfg&mem=256令

# 查看CPU个数
```python
[root@localhost tmp]# cat /proc/cpuinfo | grep "physical id" | uniq | wc -l
12
```
# 查看CPU核数
```python
[root@localhost tmp]# cat /proc/cpuinfo | grep "cpu cores" | uniq
```
# 查看CPU型号
```python
[root@localhost tmp]# cat /proc/cpuinfo | grep 'model name' |uniq
```
# 查看Linux发行版本
```python
[root@localhost tmp]# cat /etc/redhat-release
```

# 清空文件内容
```python
[root@localhost tmp]# >zhang.log
```
```python
[root@localhost tmp]# cat /dev/null > zhang.log
```
类似/dev/null,可以自己创建一个空文件，然后重定向到指定要清空的文件>
```python
[root@localhost tmp]# touch hua.log
[root@localhost tmp]# cat hua.log
[root@localhost tmp]# cat hua.log > zhang.log
[root@localhost tmp]# cat zhang.log
```
# 查看文件前面5行
```python
[root@localhost tmp]# head -n 5 joker.log
```
# 查看文件最后面5行
```
[root@localhost tmp]# tail -n 5 joker.log
```

# 查看文件第6到第8行
```python
[root@localhost tmp]# cat joker.log
1
2
3
4
5
6
7
8
9
10
[root@localhost tmp]# cat joker.log |tail -n 5
6
7
8
9
10
[root@localhost tmp]# cat joker.log |tail -n 5|head -n 3
6
7
8
```

# 通过关键字过滤
```python
[root@localhost tmp]# cat joker.log
1
2
3
4
5
6
7
8
9
10
[root@localhost tmp]# grep 2 joker.log
2
[root@localhost tmp]# cat joker.log |grep 2
2
```
# Linux查看版本信息
```python
[root@localhost ~]# uname -a
Linux localhost 4.15.0-00049-ga3b1e7a-dirty #11 Thu Nov 8 20:30:26 CET 2018 riscv64 riscv64 riscv64 GNU/Linux
[root@localhost ~]# cat /proc/version
Linux version 4.15.0-00049-ga3b1e7a-dirty (bellard@localhost.localdomain) (gcc version 7.3.0 (Buildroot 2016.08-git-svn30683)) #11 Thu Nov 8 20:30:26 CET 2018
[root@localhost ~]# cat /etc/redhat-release
Fedora release 33 (Rawhide)
[root@localhost ~]# cat /proc/cpuinfo
hart    : 0
isa     : rv64acdfimsu
mmu     : sv48
```
# Linux上的防火墙
```python
[root@localhost proc]# cat /etc/selinux/config
 
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of these three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
```
```python
[root@localhost proc]# /usr/sbin/sestatus -v
SELinux status:                 disabled

```
# 动态查看日志文件
```python
[root@localhost tmp]# tail -f joker.log |grep 3
```
# 压缩解压文件tar
```python
[root@localhost tmp]# ls
90.log  a9.log  joker.log  joker_up.log  test  zhang.log
[root@localhost tmp]# tar -cvf joker.tar.gz joker.log
joker.log
[root@localhost tmp]# ls
90.log  a9.log  joker.log  joker.tar.gz  joker_up.log  test  zhang.log
[root@localhost tmp]# rm -rf joker.log
[root@localhost tmp]# tar -xvf joker.tar.gz
joker.log
[root@localhost tmp]# ls
90.log  a9.log  joker.log  joker.tar.gz  joker_up.log  test  zhang.log
3
```
# 提取/etc/passwd 的前两行的用户名
```python
[root@localhost tmp]# cat /etc/passwd|head -n 2|cut -d : -f1
root
bin
```
# rm命令删除文件夹
```python
[root@localhost tmp]# rm aa/
rm: cannot remove 'aa/': Is a directory
[root@localhost tmp]# rm -f aa/
rm: cannot remove 'aa/': Is a directory
[root@localhost tmp]# rm -rf aa/
```
