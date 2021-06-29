<!--
 * @Author: joker.zhang
 * @Date: 2021-04-19 15:11:36
 * @LastEditors: joker.zhang
 * @LastEditTime: 2021-06-29 17:43:42
 * @mail: zhanghua7890@163.com
 * @Description: For Automation
-->
## 替换字符

替换每一行中所有 xx为oo
```
:%s/xx/oo/g
```
```
:g/xx/oo/g
```

# 常用命令速查
[速查表](https://github.com/ZZHH7890/learning-journey/blob/master/images/%E9%80%9F%E6%9F%A5%E8%A1%A8.jpg)

# 常用命令

git status  

git clone https://git.thy360.com/test/API_Automation.git

git add 文件名   # 指定git跟踪该文件   git add .

git commit -am"备注" 提交代码

git pull  # 拉取远程代码，并自动合并

git push # 推代码到远程库

git branch 查看当前分支

git branch -a 查看所有的分支

git checkout -b 分支 origin/分支 切到分支

git checkout master 切到master

git reset --hard origin/master指令把HEAD指向master最新版本
	
git diff  #查看当前所有未提交的更改
