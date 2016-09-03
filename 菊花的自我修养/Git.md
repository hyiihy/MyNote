#  <center>Git</center>
## 分布式与集中式
## 安装
- **Windows上**  
Git原本是Linux上的软件，在Windows上运行Linux软件需要安装模拟环境。Cygwin是一个在windows平台上运行的类UNIX模拟环境，安装和配置比较复杂。  
对于Git的安装，有个封装好Git和Cygwin的软件——msysgit。  
[下载地址](https://git-for-windows.github.io/)  

- **安装过程**

- **安装好后**  
    会出现三个应用程序
    - Git GUI
    - Git Bash
    - Git cmd（取决于安装时的设置）  

  安装好后前两个会出现在右键菜单中，右击即可在当前位置创建Git本地仓库  

## 常用命令
- 创建版本库  
    - 在本地新建文件夹，在此路径下使用`git init`命令
    - 使用`git clone`命令克隆远程仓库，如：  
    `git clone git@github.com:hyiihy/MyNote.git`  
    此方法可以随便克隆别人的公开库，不用SSH密钥验证。  

  以上两种方法均会在版本库所在文件夹在产生隐藏文件.git（使用`ls -ah`查看）,此即为存储版本库信息的文件。
  删除它，则版本库与普通文件夹无异。  
- 添加文件到版本库  
    - 使用`git add`命令将文件添加进暂存区
    - 使用`git commit`将文件提交到本地版本库

- 查看本地版本库信息  
    - 使用`git status`命令查看当前版本库状态
    - 使用`git diff`查看当前文件在工作区和版本库里面的区别  

- 版本回滚  
    - 使用`git log`命令查看历史记录
    - 使用`git reset`命令回退到上一个版本




## 远程仓库  
1. **利用GitHub做远程仓库**
    - 注册GitHub账号
    - 在本机创建SSH Key  
    首先查看用户主目录是否存在.ssh目录，若不存在则使用以下命令创建：  
     `ssh-keygen -t rsa -C "867611472@qq.com"`
    - 在.ssh目录下有id_rsa(私钥)和id_rsa.pub(公钥)两个文件，将公钥上传到GitHub中  

  GitHub上同一个的用户的所有仓库通过一个SSH密钥确定上传者是否合法，在不同的电脑上用不同的SSH密钥连接同一个GitHub仓库，即形成了团队协作。

- **在GitHub上创建一个仓库**  
将GitHub仓库克隆到本地或与一个已有的本地仓库关联  
使用以下命令克隆GitHub仓库到本地：  
`git clone git@github.com:hyiihy/MyNote.git`  
使用以下命令将本地仓库与GitHub上的空仓库关联：  
`git remote add origin git@github.com:hyiihy/MyNote.git`

- **将本地库的内容推送到远程仓库**  
`git push origin master`

- **将远程仓库的更新同步到本地**
`git pull origin master`

- **pull命令可拆分为2个单独的命令**  
`git fetch origin master`  
`git merge origin/master`  
执行`git pull`等同于：`git fetch`加上`git merge`

## Git分支
![](Git分支.png)  
每个分支由一个指针表示，HEAD指针指向当前分支的指针。

##gitignore
创建一个名为 `.gitignore` 的文件，列出要忽略的文件模式,如：  
```
$ cat .gitignore
*.[oa]
*~
```
文件 `.gitignore` 的格式规范如下：
- 所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
- 可以使用标准的 glob 模式匹配。
- 匹配模式最后跟反斜杠（/）说明要忽略的是目录。
- 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。
