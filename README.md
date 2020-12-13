znfang theme of jekyll, which is modified according to [fooleap's blog](https://blog.fooleap.org). I hava deleted some personal pages.

It also contains disqus and valine comment system.

# How to Use
```bash
git clone git@github.com:znfang/Jekyll-template.git
```

# Debug Local
## dependencies
- nodejs >= 8.9.0
- ruby > 2.6.0
- webpack 
- jekyll = v3.8.6
## dependencies installed
```bash
sudo apt-get install ruby2.3 ruby2.3-dev nodejs # recommend to use rvm and nvm tools
# run anywhere as you like
gem install jekyll -v "3.8.6" # you must install ruby first
gem install bundler # you must install ruby first
npm install -g webpack
```

## debug
```bash
cd ${jekyll-template} # enter your jekyll-template folder
# run under srcipts in your target folder
npm install # ryou must install nodejs first 
webpack -p # you must run this script if you modified css and js file
bundle install # you need install ruby first
bundle exec jekyll server # run jekyll local
```
