---
title: Install_1
date: 2019-11-01 10:46:19
tags:
- 安装教程
-
categories: 安装教程
---
# markdowm+hero+github搭建博客
1. github账号注册和管理
    - 注册 github 账号
    - 建立一个代码仓库"repository"，命名为"ElainaChan.github.io"，前缀必须是用户名格式
2. Github Desktop安装（可选）
    - 下载地址：https://desktop.github.com/
    - 配置 git 账号信息
3. 安装 node 环境
    - node 下载地址：https://nodejs.org/en/，下载安装msi文件并安装
    - 检查是否成功，输入命令：node -v
4. 安装 git 环境
    - 下载地址：https://git-scm.com/download/win
    - 安装后命令行输入 "git -v"测试是否成功
    - 本地 git 与 github 账号绑定
        - 右键点击 Git Bash。或者在菜单里搜索 Git Bash，设置 user.name 和user.email 配置信息，输入命令：
            - i) git config --global user.name "你的GitHub用户名"
            - ii) git config --global user.email "你的GitHub注册邮箱"
        - 生成ssh密钥文件（重要！！）
            - i)检查ssh密钥，输入命令:   cd ~/. ssh
            - ii)若没有则生成密匙，输入命令:   ssh-keygen -t rsa -C "邮件地址"
            - iii)然后连续3次回车，即可生成 ssh key。输入命令： ~/.ssh/id_rsa.pub  ，获取到你的 SSH key->复制密钥
            - iv)需要确认并添加主机到本机SSH可信列表，输入命令：  ssh -T git@github.com  ，若返回"Hi xxx! You've successfully …… but …… "，则说明添加成功
            - v)登录 Github ，右边栏头像点击"Settings"->"SSH and GPG keys"->"New SSH key"->复制刚刚的ssh密钥
5. 安装 Hexo 环境
    - 新建一个文件夹用于存放以后发布的网页，命名为"Hexo"
    - 不要进入文件夹，在文件夹的父目录下右击并点击"Git Bash"
    - 输入命令进行安装：
        - npm install -g hexo-cli
        - hexo  &nbsp;&nbsp;&nbsp;  #是否安装成功
    - 进入文件夹查看新建候得目录结构
6. 搭建网站
    - 初始化生成静态网页文件，Hexo目录下右击选择"Git Bash Here"，输入命令：
        - hexo init
    - 安装 hexo-deployer-git 用于后续的 deploy，输入命令：
        - npm install hexo-deployer-git --save
    - 当前文件夹下找到"_config.yml"文件，进行个性化配置，设置标题及作者如下所示：
        - title: BlogTest
        - author: ElainaChan
      - 更新博客到github上
        - 进入根目录文件夹，找到"_config.yml"文件，文件最后修改为：
        -           deploy:
                    type: git
                    repo: https://github.com/ElainaChan/ElainaChan.github.io.git
                    branch: master
    - 网站雏形，分别输入命令
        - hexo new "test_my_site"   &nbsp;&nbsp;&nbsp;  #创建一篇新文章
        - hexo g   &nbsp;&nbsp;&nbsp;                 #生成文件
        - hexo d   &nbsp;&nbsp;&nbsp;                 #更新部署到github上
        - hexo s   &nbsp;&nbsp; &nbsp;            #本地 server 部署
    - 浏览器输入地址：  localhost:4000   ，访问博客内容

# Atom安装+配置 Markdown
1. 下载安装：https://atom.io/ ，解压压缩包
2. 安装markdown编辑器的插件：
    - markdown-writer、markdown-toc、markdown-table-editor、markdown-themeable-pdf、git、markdown-image-paste
    - pdf-view、language-markdown、markdown-preview-enhanced、language-gfm-enhanced、git-plus
3. 使用快捷键 Ctrl + Shift + M 则可打开Markdown的预览界面
4. Markdown 基本语法：https://www.runoob.com/markdown/md-lists.html

# Maven安装配置
1. 安装 Maven：http://maven.apache.org/download.cgi 下载".zip"解压到一个文件夹
2. 环境变量配置
    - 新建环境变量"MAVEN_HOME"，赋值maven解压文件夹路径
    - 编辑环境变量Path，增加 "%MAVEN_HOME%\bin\;"
    - 命令行检查是否安装成功，命令"mvn -v"
3. 配置本地仓库路径
    - 在Maven目录下新建maven-repository文件夹，该目录用作maven的本地库。
    - 找到"conf"文件下的"settings.xml"文件，找到代码"<localRepository>/path/to/local/repo</localRepository>"
    - localRepository节点默认是被注释掉的，需要把它移到注释之外，然后将localRepository节点的值改为创建的目录，如 "< localRepository> F:/Maven/maven-repository </localRepository>"

# Idea破解
1. 下载并安装idea
    - 官网下载地址：https://www.jetbrains.com/idea/
    - 选择 <u> Ultimate </u> 版本下载并安装
2. 注册破解
    - 方法一：注册码激活（可能不成功）
      - 选择 Activation code，查注册码进行复制验证
      - 选择 License server 进行地址验证（不推荐）
    - 方法二（推荐，成功激活到 2089年8月）：
        - 下载破解JAR，放入IDEA的bin文件夹中（本百度云备份）
        - 链接：https://pan.baidu.com/s/1N1BHeJ0-mmFIWbrh5h4k-g ，提取码：gx7n
        - 选择"试用"，进入idea后选择"Help"->"Edit Custom VM Options"->点击创建后重启
        - 打开文档，在最后一行添加  -javaagent:D:\IntelliJ IDEA 2019.1.2\bin\jetbrains-agent.jar，将路径换成自己本地的
        - 选择Help -> Register -License server， 输入 http://jetbrains-license-server
        - 若之前有激活码，必须移除之前的 Remove License （非常重要）
        - 重启IDEA，填入激活码（下载jar里的激活码.txt），复制文件中激活码，填入Activation code
        - 重启，破解完成
3. JDK 配置
    - 点击"File"->"Project Structure"->"SDKs"->点击"+"，选择"JDK"
    - 选择 JDK 安装文件夹的目录->"ok"
4. MAVEN 配置
    - 点击"File"->"Settings"->"Maven"
    - 选择"directory"选择 maven 安装文件夹的目录
    - 选择"settings file"选择 修改后配置文件夹的目录，查看下面的reposity是否为修改后
