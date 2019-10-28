# 重邮69周年生成专属头像

### 项目说明

庆祝重庆邮电大学69周年活动，微信公众号网页，基于vue-cli3快速开发

### 目录结构

```
|-- .gitignore
|-- babel.config.js
|-- package.json
|-- README.md
|-- vue.config.js
|-- yarn.lock
|-- public
|   |-- index.html
|-- src
    |-- App.vue  //无router，调整translate显示不同页
    |-- main.js
    |-- assets
    |-- components
        |-- Entrance.vue  //入口页
        |-- Generate.vue  //生成页
        |-- Save.vue  //保存页

```

### 技术

- vue
- html2canvas

### 坑

##### html2canvas

- 要截取部分含微信用户头像图导致canvas污染无法导出。解决办法：借助nginx反代改变图片域名
- 按节点生成canvas时在iOS上无效，全屏生成可用。解决办法：截取全屏并给定切割位置