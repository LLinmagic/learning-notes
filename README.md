# learning-notes
# Git实践任务学习笔记

## 学习资料来源
- Git官方文档：[https://git-scm.com/doc](https://git-scm.com/doc)
- GitHub Guides：[https://guides.github.com/](https://guides.github.com/)
- CSDN：https://blog.csdn.net/qq_42808052/article/details/137476129?fromshare=blogdetail&sharetype=blogdetail&sharerId=137476129&sharerefer=PC&sharesource=ll0902&sharefrom=from_link
- CSDN：https://blog.csdn.net/sereasuesue/article/details/117080435?fromshare=blogdetail&sharetype=blogdetail&sharerId=117080435&sharerefer=PC&sharesource=ll0902&sharefrom=from_link

## 实践流程
1. 安装Git并配置用户名、邮箱。
2. 创建本地仓库，提交三次代码并推送至GitHub。
3. 解决SSH密钥认证问题。

## 遇到的困难及解决
- **问题**：推送时报错 `Permission denied (publickey)`。
  - **解决**：重新生成SSH密钥并添加到GitHub账户。
-**问题** fatal: refusing to merge unrelated histories 问题：
-这个错误表明你的本地仓库和远程仓库的历史记录（commit history）是完全独立的，Git 不知道如何将它们合并在一起。
-这通常发生在以下情况：
-你从一个全新的本地仓库开始，然后尝试将它推送到一个已经存在的远程仓库。
-或者，远程仓库和本地仓库的初始提交（initial commit）不同。
  - **解决**：git pull learning-notes main --allow-unrelated-histories  允许 Git 合并不相关的提交历史
- **问题**：解决 non-fast-forward 问题
- 这个错误表明你的本地分支落后于远程分支，Git 不允许你在本地分支落后的情况下直接推送更改。
  - **解决**：
  - git pull learning-notes main
  - git push -u learning-notes main

## 推荐书籍
- 《Pro Git》（免费在线阅读：[https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)）
