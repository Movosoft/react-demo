1. git 配置：
git config --global user.name "xxx"      -- 配置用户名，上传本地 repository 到服务器上的时候，在 Github 上会显示这里配置的上传者信息
git config --global user.email "xxx"     -- 配置邮箱
git config --list        查看配置列表

配置 sshkey ： 上传代码时使用这个 sshkey 来确认是否有上传权限
    1. 创建本地 ssh ： ssh-keygen -t rsa -C "Github 的注册邮箱"
    2. 在 Github 中添加这个 sshkey ： 
        复制  C:\Documents and Settings\Administrator\.ssh\id_rsa.pub 文件中的内容；
        登录 Github --> Account Setting  --> SSH-KEY --> Add SSH-KEY --> 粘贴id_rsa.pub中的内容；
    3. 验证： ssh -T git@github.com
        出现 Hi xxx! You've successfully authenticated, but GitHub does not provide shell access. 说明配置成功，可以连接上 Github
        

2. 建立仓库 repository ：
git init here       -- 创建本地仓库
git remote add origin git@github.com:用户名/仓库名.git
                    -- 把本地仓库和远程仓库关联起来， 如果不执行这个命令的话，每次 push 的时候都需要指定远程服务器的地址

                    
3. 从远程仓库中下载新的改动：
git pull origin master


4. 提交本地修改到远程仓库中：
git add
git add -A      -- 将改动添加到本地仓库中
git rm xxx      -- 从本地仓库中删除指定文件
git rm -r xxx   -- 从本地仓库中删除指定文件夹

git commit -m "注释"    -- 把本机缓存中的内容提交到本机的 HEAD 里面

git push origin master      -- 把本地的 commit push 到远程仓库中