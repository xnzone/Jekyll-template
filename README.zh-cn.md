xnzone, jekyll主题，参考[fooleap博客](https://blog.fooleap.org)修改的，去掉了他博客里面个性化的东西。

集成了disqus和valine两种评论，具体可以看_config.yml配置

效果请参考[xnzone博客模板](http://jekyll-template.xnzone.ml)

# 使用
```bash
git clone git@github.com:znfang/Jekyll-template.git
```

# 本地调试使用
## 依赖
- nodejs >= 8.9.0
- ruby >= 2.3.0
- webpack 
- jekyll = v3.8.6

## 安装依赖
```bash
sudo apt-get install -y ruby2.3 ruby2.3-dev nodejs # 安装环境, 推荐使用rvm和nvm工具
gem install jekyll -v "3.8.6" # 安装jekyll
npm install -g webpack # 安装webpack
gem install bundler
```

## 本地调试
```bash
cd ${jekyll-template} # 进入下载的jekyll-template目录
npm install # 安装nodejs相关依赖，先需要安装node
webpack -p # 每次修改完js和scss文件需要执行此步骤
bundle install # 安装ruby的相关依赖，先需要安装ruby
bundle exec jekyll server # 本地执行jekyll服务器
```
