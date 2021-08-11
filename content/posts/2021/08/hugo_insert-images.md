---
title: "在 Hugo 文章裡顯示圖片"
menuTitle: "Hugo : how to display the images in the post"
date: 2021-08-11T11:44:56+08:00
publishDate: 2021-08-11T11:44:56+08:00
draft: false
tags: ["github page","hugo"]
pre : "<b>[架個部落格] </b>"
---

## 基本語法
```
![name](image_file_path.Extension)
```

## 如果是本地圖片
### step 1 : 將圖片放在 static 目錄下
例如我的目錄結構是這樣， static 裡面分門別類，其中一個目錄是 images

```
static
  |
  |-- images
        |-- picture_01.jpg
        |-- picture_02.png
        |__ picture_03.png
  |-- ...
  |__ ...
```

### step 2 : 在文章內引入
在文章內輸入如下內容，即可引入 picture_01.jpg ，命名可省略。  
```
![](/images/picture_01.jpg)
```

## 如果是線上圖片
上傳到雲端圖庫後，直接貼上分享網址即可，別忘記副檔名。  
```
![](http://[somewhere].com/picture_01.jpg)
```

## 參考資料
- [官方文件 : 框架結構](https://gohugo.io/getting-started/directory-structure/)
    - 文件有說圖片要放在 `static/` 目錄下。
- [官方文件 : 本地端存放圖片的地方](https://gohugo.io/content-management/static-files/)
    - 引入圖片的寫法跟一般 Markdown 語法相同，就是 `![Example image](/image.png)` 而已，但是路徑不用包含 `static/` 目錄，因為框架行為就是進 `static/` 目錄尋找。
- [Day 24. Hugo Shortcode 運用場景 - 圖片篇](https://ithelp.ithome.com.tw/articles/10250512)
    - Shortcodes 語法中文教學，包含調整大小
- [How To Add Image Processing to Your Hugo Website and Improve Performance](https://alexlakatos.com/web/2020/07/17/hugo-image-processing/)
    - 好像可以改預設尋找的資料夾，但尚未嘗試
- [Hugo: How can I display an image in my post list](https://stackoverflow.com/questions/62135931/hugo-how-can-i-display-an-image-in-my-post-list)
    - 使用 Shortcodes 語法，達成在文章列表顯示圖片的目的，但尚未嘗試
