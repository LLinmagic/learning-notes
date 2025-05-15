
1. **概述**

Git 的官方网站为 https://git-scm.com。

（1）版本控制介绍

版本控制系统（VCS）可以记录文件随时间的变化历史，支持以下核心功能：

1. 版本回溯：可恢复任意历史版本，例如回退错误提交：

git reset --hard [commit-hash]

1. 协作管理：多人并行开发时追踪代码变更来源，如查看某行代码修改者：

git blame [filename]

2. 分布式版本控制 VS 集中式版本控制

|**类型**|**特点**|
| :- | :- |
|**集中式（如 SVN）**|**依赖中央服务器，需联网提交代码，单点故障风险高**|
|**分布式（如 Git）**|**每个开发者拥有完整仓库，支持离线工作，例如本地提交：git commit -m "msg"**|

（3）Git 工作机制与代码托管平台

Git 使用快照记录文件，支持快速创建和管理分支。代码托管平台（如 GitHub、Gitee、GitLab）提供便捷的仓库托管、协作功能。

**2.Git 安装**

（1）下载安装

Windows：官网https://git-scm.com/downloads下载安装包后勾选 Add to PATH 以支持命令行操作

Linux：使用包管理器快速安装，例如 Ubuntu：sudo apt-get install git

macOS：通过 Homebrew 安装：brew install git

（2）使用命令行验证安装：

git --version

（3）配置用户信息：
\# 全局配置（适用于所有仓库）

git config --global user.name "Your Name"

git config --global user.email "your.email@example.com"

\# 为特定仓库单独配置（在仓库目录内执行）

git config --local user.email "work@company.com"

**3.Git 基本命令**

（1）配置用户信息

git config --global user.name "Your Name"

git config --global user.email "your.email@example.com"

可通过 --global 参数设置全局用户名和邮箱。

（2）初始化仓库

在项目根目录下初始化 Git 仓库：

mkdir git-project && cd git-project  # 创建项目目录

git init                         # 初始化仓库（生成隐藏的 .git 文件夹）

已有文件夹，则：

cd /d/git\_project

git init

（3）查看仓库状态

查看当前工作区与暂存区状态，包括文件的改动、添加、删除等：

git status

（4）暂存、提交与版本管理

添加文件到暂存区：
git add <filename> 
git add .     # 添加所有改动

提交到本地库：
git commit -m "提交描述信息"

查看提交日志：

git log # 显示详细的提交日志 

git log --oneline # 简略显示

查看提交的差异：

git diff # 显示工作区与暂存区的差异 

git diff HEAD~2 HEAD           # 比较最近两次提交的差异

git diff --staged # 显示暂存区与本地库的差异/查看暂存区与上次提交的差异

例子:
git add .                       # 添加所有修改到暂存区

git commit -m "fix: 修复登录按钮样式问题"  # 语义化提交信息

git log --graph --oneline       # 图形化显示提交历史

（5）分支管理

A.分支的创建与切换：分支使得开发多个功能独立进行，避免主分支的代码冲突和不稳定。

查看当前分支：

git branch

创建分支：

git branch <branch-name>

切换分支：

git checkout <branch-name>

创建并切换新分支：

git checkout -b <branch-name>

B.合并分支与解决冲突

合并分支（切换到主分支并合并）：

git checkout main 

git merge <branch-name>

解决冲突：

Git 会标记冲突位置，手动编辑并解决冲突后：

git add <filename> 

git commit -m "解决冲突描述"

例子：
git branch -a                  # 查看所有分支（含远程分支）

git checkout -b dev            # 创建并切换到 dev 分支

git merge dev --no-ff          # 合并 dev 分支（保留合并记录）

git push origin --delete dev   # 删除远程 dev 分支

（6）团队协作

Git 提供分布式版本控制，适用于不同场景的协作。

克隆仓库：git clone https://github.com/<user\_name>/<project\_name>.git

A.团队内协作

创建远程仓库并推送：

git remote add origin <repository-url> 

git push -u origin main

拉取远程仓库更新：

git pull origin main

B.跨团队协作

a.Fork 项目：在 GitHub 上 fork 他人的项目，建立自己版本的副本。

b.提交 Pull Request：在自己的项目仓库修改后，发起 Pull Request 请求，将代码合并回原始项目。

**4.GitHub 集成**

创建远程仓库并设置别名：

git remote add origin <repository-url>

推送代码：

git push -u origin main

克隆远程仓库：

git clone <repository-url> 

Eg.git clone https://github.com/<user\_name>/<project\_name>.git

SSH 免密登录：

\# 生成密钥对（默认保存到 ~/.ssh/）

ssh-keygen -t ed25519 -C "your.email@example.com"

\# 将公钥内容粘贴到 GitHub > Settings > SSH Keys

**5.IDEA 集成**

设置 Git：在 IDEA 设置中指定 Git 安装路径。

创建本地仓库：在 IDEA 中点击 Git > Enable Version Control Integration 以初始化本地仓库。

添加和提交：右键文件或项目，选择 Git > Commit 提交变更。

分支管理：在 IDEA 的 Git 工具窗口中可以创建、切换、合并分支。

推送与拉取：在 IDEA 中可以方便地将项目推送到远程仓库或拉取更新。
