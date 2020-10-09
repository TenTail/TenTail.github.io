---
title: Gulp錯誤 - Reference Error primordials is not defined error
date: 2020-10-09 23:45:02
uri:  gulp-reference-error-primordials-is-not-defined-error
tags:
- Gulp
---

> 文章參考
> [How to solve gulp exception: Reference Error primordials is not defined error](https://ourcodeworld.com/articles/read/1188/how-to-solve-gulp-exception-reference-error-primordials-is-not-defined-error)

# 懶人包

1. 刪除 node_modules 資料夾

```shell
rm -rf node_modules
```

2. 建立 npm-shrinkwrap.json （可參考npm官方文件 [shrinkwrap.json](https://docs.npmjs.com/files/shrinkwrap.json)）

```json
{
    "dependencies": {
        "graceful-fs": {
            "version": "4.2.2"
        }
    }
}
```

3. 執行 `npm install`，此時應該會看到 **shrinkwrap** 的相關說明文字，如下圖

![](/../assets/gulp-reference-error-primordials-is-not-defined-error/1.png)

4. 執行 `gulp build`
