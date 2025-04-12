+++
title = 'hugo + github 博客, 使用笔记'
date = 2024-10-14T14:13:24+08:00
draft = false
+++

![a1](/images/a1.jpg)

#### hugo 博客插入图片
把图片放在 static/ 文件夹下

```txt
your-hugo-site/
├── content/
│   └── docs/
│       └── read_books.md
├── static/
│   └── images/
│       └── a1.jpg

然后使用
 ![a1](/images/a1.jpg)
```



draft = false 必须设置为 false！ 否则无法渲染！


过程记录， 需要详细！ 因为问题非常多！


- 参考视频教程:          https://www.youtube.com/watch?v=_QSr2_pxIJs
- 配置文件，参考来源:     https://theplaybook.dev/docs/deploy-hugo-to-github-pages/


#### hugo 是一个静态博客渲染工具， go 语言写的。
安装: 
> choco install hugo-extended  # 失败。 估计是权限  
> scoop install hugo-extended  # ok!
### 运行的话， 最好是使用 wsl , cmd 也行！！


### 新 hugo 建项目
hugo new site my_hugo_blog -f yaml
cd my_hugo_blog


### 安装主题,
```bash
git init
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

### 新建文章
hugo new docs/test_file.md
修改 draft = true， ----> draft = false 否则无法渲染。
