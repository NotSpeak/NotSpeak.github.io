---
title: Npm常用命令
date: 2022-09-09 17:07:57
tags:
- Npm常用命令
categories:
- Npm
top_img: /img/cover1.jpg
cover: /img/cover1.jpg
---
## npm命令
### 1. npm 安装配置（可选）
{% note %}
现在安装的新版本的nodejs可以直接使用默认配置的即可，不须再配置任何内容。
 1. 在nodejs安装的根目录下新建 node_cache 和 node_global 两个文件夹。
 2. 分别使用以下命令设置全局的安装包目录：
    npm config set prefix "D:\Program Files\nodejs\node_global"
    npm config set cache "D:\Program Files\nodejs\node_cache"
 3. 配置环境变量：
   打开计算机的环境变量，找到系统变量，新增一项 NODE_PATH，值为安装目录下的nodejs，   D:\Program Files\nodejs\node_global\node_modules
{% endnote %}
### 2. 查看 npm 版本
```
npm -v
```
### 3. npm淘宝镜像（可选）
```
# 设置全局的npm淘宝镜像
npm config set registry https://registry.npm.taobao.org
# 也可以切换回默认全局镜像
npm config set registry https://registry.npmjs.org
```
### 4. npm 常用命令简写说明
方便统一和阅读，文中全部使用简写方式。
| 命令 | 说明 | 
|:-----|:-----|
|-g：| 为 --global 的缩写，表示安装到全局目录里 |
|-S：| 为 --save 的缩写，表示安装的包将写入package.json里面的dependencies |
|-D：| 为 --save-dev 的缩写，表示将安装的包将写入packege.json里面的devDependencies |
| i：| 为install的缩写，表示安装 |
### 5. npm 安装模块
| 命令 | 说明 | 
|:-----|:-----|
| npm init  | npm 初始化当前目录|
| npm i  | 安装所有依赖|
| npm i express  |安装模块到默认dependencies|
| npm i express -g  | 会安装到配置的全局目录下|
| npm i express -S  | 安装包信息将加入到dependencies生产依赖|
| npm i express -D  | 安装包信息将加入到devDependencies开发依赖|
| npm i jquery@1.8.3  | 安装jquery指定的1.8.3版本|
### 6. npm 卸载模块
| 命令 | 说明 | 
|:-----|:-----|
| npm uninstall express  | 卸载模块，但不卸载模块留在package.json中的对应信息|
| npm uninstall express -g  | 卸载全局模块|
| npm uninstall express --save  | 卸载模块，同时卸载留在package.json中dependencies下的信息|
| npm uninstall express --save-dev  | 卸载模块，同时卸载留在package.json中devDependencies下的信息|
### 7. npm 更新模块
| 命令 | 说明 | 
|:-----|:-----|
| npm update jquery  | 更新最新版本的jquery|
| npm update jquery@2.1.0  | 更新到指定版本号的jquery|
| npm install jquery@latest  | 可以直接更新到最后一个新版本|
### 8. npm 查看命令
| 命令 | 说明 | 
|:-----|:-----|
| npm root  | 查看项目中模块所在的目录|
| npm root -g  | 查看全局安装的模块所在目录|
| npm list 或者 npm ls | 查看本地已安装模块的清单列表|
| npm view jquery dependencies  | 查看某个包对于各种包的依赖关系|
| npm view jquery version  | 查看jquery最新的版本号|
| npm view jquery versions  | 查看所有jquery历史版本号（很实用）|
| npm view jquery  | 查看最新的jquery版本的信息|
| npm info jquery  | 查看jquery的详细信息，等同于上面的npm view jquery|
| npm list jquery 或 npm ls jquery | 查看本地已安装的jquery的详细信息|
| npm view jquery repository.url  | 查看jquery包的来源地址|
### 9. npm 其他命令
| 命令 | 说明 | 
|:-----|:-----|
| npm cache clean  | 清除npm的缓存|
| npm prune  | 清除项目中没有被使用的包|
| npm outdated  | 检查模块是否已经过时|
| npm repo jquery  | 会打开默认浏览器跳转到github中jquery的页面|
| npm docs jquery  | 会打开默认浏览器跳转到github中jquery的README.MD文件信息|
| npm home jquery  | 会打开默认浏览器跳转到github中jquery的主页|