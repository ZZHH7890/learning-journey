<!--
 * @Author: joker.zhang
 * @Date: 2021-04-12 15:36:46
 * @LastEditors: joker.zhang
 * @LastEditTime: 2021-04-12 16:20:50
 * @mail: zhanghua7890@163.com
 * @Description: For Automation
-->

# 清空文件内容
```
[root@localhost tmp]# >zhang.log
```
```
[root@localhost tmp]# cat /dev/null > zhang.log
```
类似/dev/null,可以自己创建一个空文件，然后重定向到指定要清空的文件>
```
[root@localhost tmp]# touch hua.log
[root@localhost tmp]# cat hua.log
[root@localhost tmp]# cat hua.log > zhang.log
[root@localhost tmp]# cat zhang.log
```
# 查看文件前面5行
```
[root@localhost tmp]# head -n 5 joker.log
```
# 查看文件最后面5行
```
[root@localhost tmp]# tail -n 5 joker.log
```

# 查看文件第6行到第8行
```
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


