---
title: 仓库已经成功链接github接下来的操作
date: 2026-02-20 07:20:52
tags:
---
后续建议与操作
✅ 你现在可以继续提交代码

现在仓库已经成功连接到了 GitHub，接下来你只需要继续写作或修改 Hexo 文章后，执行以下两条命令就可以将更新同步到 GitHub 了：

git add .
git commit -m "更新文章"
git push
🛠️ 如何处理远程仓库已存在的情况

如果你真的需要修改远程仓库的 URL（比如你不小心填错了仓库地址），可以使用以下命令：

git remote set-url origin https://github.com/JTSTV/hexo.git


GitHub 创建仓库并上传代码
1
2
3
将本地项目上传到 GitHub 是版本控制与协作开发的基础操作，以下是从零开始的完整流程。

1. 配置 Git 环境

安装 Git 并配置全局身份：

git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub邮箱"
复制
建议先在 GitHub 生成 Personal Access Token (PAT)，替代密码进行推送验证。

2. 在 GitHub 创建远程仓库

登录 GitHub → 点击右上角 "+" → New repository。

填写仓库名、选择可见性（Public/Private）。

不勾选 README、.gitignore 等初始化选项，保持仓库为空。

创建后复制仓库地址，例如：

https://github.com/用户名/仓库名.git
复制
3. 初始化本地仓库并提交代码

进入本地项目根目录：

cd /path/to/your/project
git init
git add
git commit -m "首次提交项目代码"
复制
4. 关联远程仓库并推送

git remote add origin https://github.com/用户名/仓库名.git
# 若本地分支为 master，建议统一为 main
git branch -M main
git push -u origin main
复制
首次推送会要求输入 GitHub 用户名和 PAT。

5. 后续更新

当有新修改时：

git add
git commit -m "更新说明"
git push
复制
最佳实践与提示

使用 .gitignore 忽略不必要的文件（如日志、编译产物）。

若遇到 SSL 证书错误，可更新根证书或临时关闭验证：

git config --global http.sslVerify false
复制
（仅临时测试用，长期建议修复证书问题）。

推送前可用 git status 检查变更，确保提交内容正确。

这样即可完成从本地到 GitHub 的首次上传，并为后续版本管理打下基础。
