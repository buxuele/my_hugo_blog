# hugo + github 博客

### 插入图片
- 必须使用 ![a1](/my_hugo_blog/images/a1.jpg)
- 而不是    ![a1](images/a1.jpg)

过程记录， 需要详细！ 因为问题非常多！


# 参考视频教程:          https://www.youtube.com/watch?v=_QSr2_pxIJs
# 配置文件，参考来源:     https://theplaybook.dev/docs/deploy-hugo-to-github-pages/


# hugo 是一个静态博客渲染工具， go 语言写的。
安装: 
> choco install hugo-extended  # 失败。 估计是权限  
> scoop install hugo-extended  # ok!
# 运行的话， 最好是使用 wsl , cmd 也行！！


# 新 hugo 建项目
hugo new site my_hugo_blog -f yaml
cd my_hugo_blog


# 安装主题, 
git init
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod

修改 "hugo.toml",  增加一行
theme = "PaperMod"


## 新建文章
hugo new docs/test_file.md
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# !!!!!!!  修改 draft = true， ----> draft = false 否则无法渲染。
#  而且必须是小写的 false !!!!
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

hugo new docs/del_later.md

查看文章：    
- hugo server
- localhost:7897/docs/test_file


# 下面就 github 相关的操作了
- 创建github 项目，上传文件。
- 新建一个分支， gh-pages !!!! 这里名称不能变。 必须是 gh! 一个字都不能变！
- 开启 github actions 读写权限 https://github.com/buxuele/my_hugo_blog/settings/actions
- mkdir -p .github/workflows， 新建+修改 deploy.yml
- 修改 "hugo.toml",  增加 baseUrl 
