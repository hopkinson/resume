# 一个会动的简历模板

> This is my resume

[预览](http://120.76.230.40:7081/index.html)

## 使用方法

``` bash
git clone https://github.com/hopkinson/resume.git
cd animating-resume
npm install
npm run dev
```

## 部署方法


1. 编辑 config/index.js，修改第 10 行的 assetsPublicPath，值为 `项目名/dist`。如果你没有修改项目名 animating-resume，则可跳过此步骤。

2. 编译、上传
    ``` bash
    npm run build
    git add .
    git commit -m "update"
    git push
    ```


