## git 基本使用
+ 进入文件夹,右键选择git bash here
+ git init  创建仓库
+ 输入 git status 查看仓库状态
	- 如果存在红色文件列表,说明工作区内容有变动
	- 绿色说明文件已经存到暂存区,还未存储的存储区
+ git add .(一定要有空格)
+ 输入 git commit -m'first commit' ; 注意:-m不能忘记!!
+ 建立远程源:  git remote add origin https://github.com/nevermo2013/test3.git
+ git push -u origin master
+ 以后的推送 只需要 git  push 
	- 注意 本地必须要先存储到存取区