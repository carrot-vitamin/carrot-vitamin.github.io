## 环境：
* git
* node.js
* hexo
* deploy-git

## 安装顺序：
* Node.js
> brew install node

 *检测： node -v, npm -v*

* Hexo:
> npm install -g hexo-cli

 *检测：hexo -v*

* deploy-git：
> npm install hexo-deployer-git --save



## 启动服务
进入目录下：
`hexo g`
`hexo server`
浏览器输入 `http://localhost:4000` 即可看到自己的页面，ctrl + c 退出

## 部署命令
* hexo clean `清除了你之前生成的东西，也可以不加`
* hexo generate `生成静态文章，可以用 hexo g缩写`
* hexo deploy `部署文章，可以用hexo d缩写`
