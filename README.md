# Git
### 1.安装Git
Git官方下载地址:[http://git-scm.com/download](http://git-scm.com/download)
### 2.建立连接

网址：https://help.github.com/articles/generating-ssh-keys

#### 官方步骤：

##### Step1:Check for SSH Keys 
首先检查在你的电脑上是否存在SSH命令：
     		
	cd ~/.ssh
如果显示‘No such file or directory’那么直接到step3

如果没有显示‘No such file or directory’删除掉之前的密钥和目录~/.ssh，删除掉同级目录下的.gitconfig文件，重试该命令，就会显示‘No such file or directory’


##### Step2: Back up and remove exiting SSH
    $ ls -l
    $ mkdir key_backup 
    $ cp id_rsa* key_backup 
    $ rm id_rsa*

##### Step3:Generate a new ssh key
    $ $ ssh-keygen -t rsa -C "yourEmail@example.com" 
或者去掉 －t rsa，接下来会提示你输入一个文件名来保存你的SSH key ，如果不输入直接回车，则会保存在默认的文件里id_rsa.pub，然后会提示你输入passphrases 连续输入两次，这在你在网页中添加SSH key的时候会让你输入一次(可以两次回车，页面添加时不用输入)。

##### Step4:Add you ssh key to GitHub
首先得到刚才生成的SSH，C:\Users\主机名\\.ssh自己打开id_rsa.pub复制内容或者如下命令放到剪切板中也可以

    $ sudo apt-get install xclip   //安装剪切板
    $ xclip -sel clip < ~/.ssh/id_rsa.pub 
    
这样就复制到剪切板了

然后到github.com 登录自己的帐号。Account Setting ---->SSH KEYS ---->Add SSH key ------>粘贴到KEY feild  然后自己取个名------>会提示你confirm password 点击 ------>弹出密码输入框，就是输入给你刚才的自己设置的passphrases ，ok！


##### Step5:testing
命令：

    $ ssh -T git@github.com
     
如果看到提示:
    
The authenticity of host 'github.com (207.97.227.239)' can't be established.RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.Are you sure you want to continue connecting (yes/no)?
    
没关系，正常情况……yes

Enter passphrase for key '/c/Users/shanqingmei/.ssh/id_rsa':……输入设置的passphrases密码

Hi `username!` You've successfully authenticated, but GitHub does not provide shell access.


##### Step6：安装完成后，验证身份

	$git config --global user.email "you@example.com"
	$git config --global user.name "Your Name"
Git是分布式版本控制系统，需要登陆账号信息：你的名字和Email地址。




--------------------------------------------------------------------------------------------



#### 提交流程

1.git add <file>

2.git commit -m "Operation description"

3.git remote add origin git@github.com:ki3wi/project.git（第二次提交时可以省略）

4.git push -u origin master

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

从现在起，只要本地作了提交，就可以通过命令：

$ git push origin master
#### 拉取

1.git pull 抓取远程库到本地
#### 其他
2.git remote rm origin 

