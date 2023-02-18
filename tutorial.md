# 个人github page 搭建教程

### 克隆项目
### 安装ruby nodejs
* ruby下载
  * https://rubyinstaller.org/downloads/
  * 选择网页中 WITH DEVKIT 中高亮的选项
  * 安装
    * 直接默认配置next到底即可（可以自选安装目录）
  * 确认安装成功
    * 命令行（win+R输入cmd回车打开命令行）输入 `ruby -v` 出现对应版本号
    * 命令行（win+R输入cmd回车打开命令行）输入 `gem -v` 出现对应版本号
* nodejs下载：
  * https://nodejs.org/en/download/
  * 选择windows installer
  * 安装
  * 确认安装成功
    * 命令行（win+R输入cmd回车打开命令行）输入 `node -v` 出现对应版本号
### 安装github page需要的依赖（此处参考readme.md，但是项目原本是在linux下运行的）
* 命令行输入`bundle clean`清空当前ruby依赖包
* 命令行输入`bundle install`安装当前项目所需ruby依赖包
  * 命令行输入`bundle exec jekyll liveserve`启动项目
    * 启动可能提示时区找不到，这是linux和win的差异需要补充安装依赖，在gemfile最后补充以下内容后`bundle install`
      ```bash
      gem "webrick", "~> 1.8"
      gem 'tzinfo'
      gem 'tzinfo-data'
      gem "jekyll", "3.9.0"
      gem "jekyll-paginate"
      gem "jekyll-gist"
      gem "jekyll-redirect-from"
      gem "kramdown-parser-gfm"
      ```
    * 启动后在浏览器输入`127.0.0.1:4000`或者`localhost:4000`可以看到当前项目的github page，可以实时编译（如果直接在github上修改需要数分钟才能看到自己修改的结果）

### 编辑github page
以上步骤的目的是为了在本地可以实时看到自己的编辑结果，具体的编辑方式如下：
* 基本配置
* 修改文字
* 插入图片
* 增减栏目


### 上传自己编辑后的github page
* 命令行输入`git add .`将变更写入缓存区
* 命令行输入`git commit -m “xxx”`将缓存区内容提交本地仓库，xxx可以替换成自己对这次commit的备注，例如`git commit -m “init”`
* 命令行输入`git push`将本地仓库同步到远程仓库（github仓库），通过项目预设的github action编译成网页（几分钟后生效）