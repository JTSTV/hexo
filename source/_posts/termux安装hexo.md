---
title: termux安装hexo
date: 2026-02-21 02:47:51
tags:
---
termux安装hexo
回答
Termux 中安装 Hexo 并部署博客的过程相对简单，主要步骤包括：更新 Termux 环境 → 安装 Node.js → 安装 Hexo → 初始化博客 → 启动预览 →（可选）部署到 GitHub Pages。
以下是详细的操作步骤：
步骤一：准备工作
更新系统软件源
打开 Termux 应用，首先确保所有软件源和已安装的包都是最新的，以免出现依赖错误[[1]][[2]]。
pkg update -y

pkg upgrade -y

安装必要工具
安装 nodejs（Node.js 环境）和 git（用于获取 Hexo 主题或插件）。建议直接安装 nodejs 包（包括 npm），如果有需求也可以安装 nodejs-lts（长期支持版）[[3]][[4]]。
pkg install nodejs git -y

步骤二：安装 Hexo
配置 npm 镜像（可选）
如果你在国内使用 Termux，可能会遇到 npm 安装速度慢或失败的问题。建议配置淘宝镜像源来加速下载[[5]]。
npm config set registry https://registry.npmmirror.com

全局安装 Hexo CLI
使用 npm 命令全局安装 Hexo 命令行工具 hexo-cli[[6]][[7]]。
npm install -g hexo-cli

步骤三：初始化 Hexo 项目
创建博客目录
建议在 Termux 的主目录（/data/data/com.termux/files/home）下创建博客目录，避免权限问题[[8]][[9]]。
mkdir myblog

cd myblog

初始化 Hexo 环境
运行 hexo init . 来初始化当前目录为 Hexo 项目。如果初始化过程卡住或出错，可以尝试重新安装依赖（见下一步）[[10]][[11]]。
hexo init .

安装项目依赖
初始化完成后，执行 npm install 来安装 package.json 中列出的依赖包[[12]]。
npm install

步骤四：本地预览
生成静态文件
hexo g

启动本地服务器
hexo s

启动成功后，你可以在手机浏览器中访问 http://localhost:4000  来预览你的博客[[13]][[14]]。
步骤五：部署到 GitHub Pages（可选）
如果你想让博客在互联网上访问（即通过 username.github.io 访问），需要进行以下配置[[15]][[16]]：
在 GitHub 创建仓库
通常命名为 username.github.io（将 username 替换为你的 GitHub 用户名）。
配置 Hexo 部署插件
在 Termux 中安装 Hexo 部署插件 hexo-deployer-git，并编辑 Hexo 项目的 _config.yml 文件，设置 deploy 部分的仓库地址为你的 GitHub 仓库地址。
npm install hexo-deployer-git --save

然后编辑 _config.yml（参考插件文档），配置 url、root、deploy 等字段。
生成并部署
hexo g

hexo d

执行完成后，你的博客就会自动推送到 GitHub Pages 并上线。
常见问题与解决
报错或卡住：如果在 hexo init 或 npm install 时卡住，可能是网络问题。可以尝试换用其他网络环境（如使用 VPN）或更换 npm 镜像源[[17]]。
GitHub Pages 访问慢：Termux 中生成的博客在上传至 GitHub 前可以使用 hexo clean 清理缓存，然后重新生成。
通过以上步骤，你就可以在手机上通过 Termux 搭建起一个完整的 Hexo 博客系统。
其他来源
[1,10,14]. Termux最快安装Hexo博客详细
[2]. Termux搭建Hexo博客并部署到GitHub
[3,8,13]. 如何在Termux中使用Hexo结合内网穿透工具实现远程访问本地博客站点
[4,5,7,9,11,12]. termux 搭建hexo博客教程
[6]. Termux 中启动 Hexo 博客教程
[15]. 使用Termux制作Hexo的详细攻略
[16]. Termux部署hexo
[17]. 在termux上安装express js时出现Npm错误
以下来源未被直接引用
Termux 高级终端安装使用配置教程
Termux部署Hexo
认识工具
Termux 高级终端使用配置
