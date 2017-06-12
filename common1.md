### 常用命令1  


```
  C0
  C1
  C2
  C3  master*
  C4
  C5
  C6
  C7  dev
```

### **cherry-pick** 
>git cherry-pick HEAD^^ HEAD~4  

将一些commit复制到当前的位置(HEAD)下;但不能是HEAD上游的记录

### **rebase**  
>git rebase master  

将master分支复制到当前分支下

>git rebase dev master  

将master复制到dev分支下方 

### **rebase -i**  
>git rebase -i HEAD~4;  

重新编辑HEAD 到 HEAD~4之前的提交  

### **~ 和 ^**

>git checkout master^

选择第一个父提交

> git checkout master^2

选择第二个父提交

>git checkout master~4

向上移动4个提交

### **fetch**  
>git fetch  

从远程库下载所有数据,但不会更改本地文件;  
### **pull**  
>git pull   
==>   
git fetch;  
git merge origin/master;
### **checkout或branch追踪远程分支**  
>git checkout -b dev origin/master  

创建dev,跟踪origin/master

执行pull或push时,dev将会替代本地的master进行更新  

---
>git branch -u origin/master dev;  
git branch -u origin/master;//当前分支为dev时可省略;  


### **push**  
>git push <remote> <place>;  
git push origin master;

切到本地仓库中的“master”分支，获取所有的提交，再到远程仓库“origin”中找到“master”分支，将远程仓库中没有的提交记录都添加上去  

>git push origin dev^:master;  

更新远程master分支,获取到的本地提交的位置为dev^;  
如果master在远程和本地中不存在,会自动创建;

**fetch与pull**用法与之类似;


### **情景一**  
本地提交少于远程提交？

方法一:  
>git fetch; //下载远程提交  
git rebase origin/master; //将本地复制到本地远程下 
git push;   

方法二:  
>git fetch;  
git merge origin/master;  
git push;  

方法三（推荐):  
>git pull --rebase;  
git push;  
或  
git pull;  
git push;

git pull --rebase; ==> git fetch;git rebase origin/master;  


