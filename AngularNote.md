# Angular notes

## 20220410  

**生成组件**
``ng g component components/login``  
g是generate的缩写,也可以写全。

**padding**
内边距：内边和文字的距离。

**英文网页改中文**
修改 index.html 的第二行，“en”改为“zh”。

    # index.html
    <!doctype html>
    <html lang="zh">
    ...

index.html 是 html 的入口。
若此处不修改，会弹出是否需要翻译提示。

**以 app- 开头的就是Angular官方提供的组件**
例如,在index.html 中的 ``<app-root><app-root>``