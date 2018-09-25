# hexo-backup
记录一下搭建过程中的要注意的点，以及hexo配置，主要是./下和./themes/next/下的两个_config.yml文件

**hexo 是基于nodejs的，我的node: v10.10.0, npm: 6.4.1**

安装使用见hexo官网：[https://hexo.io/zh-cn/docs/setup]

## deploy 配置
- deploy 注意按官网介绍，需要安装插件
  ```
  $ npm install hexo-deployer-git --save
  ```
- 托管到 GitHub
  - GitHub 可以建一个特殊的repo来托管网站：repo名字按规则来建 ***username.github.io***。把网站文件push到这个repo下，然后访问[https://b0o0wen.github.io/]
  - 在本地
    在 ./_config.yml最后添加：
    ```
    deploy:
      type: git
      repo: git@github.com:b0o0wen/b0o0wen.github.io.git
      branch: master
    ```
    注意冒号后一定要有个空格


## appearance 配置
- 主题配置
  主题使用next [https://github.com/iissnan/hexo-theme-next] 我的next版本是 v5.1.2
  ```
  $ git clone --branch v5.1.2 https://github.com/iissnan/hexo-theme-next themes/next
  ```
  clone next之后，在./themes/next/下有了另一个_config.yml文件
  主要有：
  - menu：如tags, categories等。在menu下新建一行xxxx，hexo就会在网站上生成一个名为xxxx的tab，对于常用的menu，hexo还会自带图标。需要注意的是要：
    ```
    hexo new page 'xxxx'
    ```
    来在./source/xxxx建立一个index.md，即点击该tab对应的页面。对于tags，在该index.md中修改这个页面的type为tags，hexo就给你生成一个tags页面，还自带词云效果
  - scheme：hexo共四个scheme
  - avatar：头像的默认根目录在 ./themes/next/source/ 下，支持各种图片格式
  - social：hexo自带图标
  
- 背景图及透明度
  在./themes/next/source/css/ 下有个_custom文件夹，这里可以修改custom.styl来定制css
  ```
  body {
  //    background:url(https://source.unsplash.com/random/1600x900);
    background:url(/images/background_leaf.jpg)   //背景图片，默认根目录在 ./themes/next/source/ 下
    background-repeat: no-repeat;  
    background-attachment:fixed;
    background-position:50% 50%;
  }
  
  //页面上menu那部分class是 .header-inner
  .header-inner {
    opacity: 0.88
  }

  .main-inner {
      opacity: 0.9;
  }
  ```
