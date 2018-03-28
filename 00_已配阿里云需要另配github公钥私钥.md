1. 生成github上某账号的私钥公钥
	1. ssh-keygen -t rsa -C ruilovechu@live.com
	2. 注意！当提示Enter file in which to save:时，注意文件名要手动输入： id_rsa_github
2. 将1中生成的id_rsa_github及id_rsa_github.pub拷贝到~/.ssh/下（这里使用gitbash工具）
3. 把公钥填写到服务器上（相同账号）
4. 打开或创建于.ssh目录中的config文件，文本内容如下：
```
# 每个账号单独配置一个Host，每个Host要取一个别名，每个Host主要配置HostName和IdentityFile两个属性即可
# Host的名字可以取为自己喜欢的名字，不过这个会影响git相关命令，例如：
# Host mygithub 这样定义的话，命令如下，即git@后面紧跟的名字改为mygithub
# git clone git@mygithub:PopFisher/AndroidRotateAnim.git
# 所以最好使用与HostName相同的
# HostName 　　　　　　　   这个是真实的域名地址
# IdentityFile 　　　　　　　  这里是id_rsa的地址
# PreferredAuthentications   配置登录时用什么权限认证--可设为publickey,password publickey,keyboard-interactive等
# User 　　　　　　　　　　　配置使用用户名

# 配置github.com
Host github.com                 
    HostName github.com
    IdentityFile C:\\Users\\popfisher\\.ssh\\id_rsa_github
    PreferredAuthentications publickey
    User username1

# 配置git.oschina.net 
Host git.oschina.net 
    HostName git.oschina.net
    IdentityFile C:\\Users\\popfisher\\.ssh\\id_rsa_oschina
    PreferredAuthentications publickey
    User username2
```
5. 使用ssh -T git@github.com测试，注意！！使用管理员启动git bash！！！
