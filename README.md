# Introduction
TBD
Just for test

# Build
  - install gitbook-cli 
    - npm install -g gitbook-cli (please check [this](http://blog.teamtreehouse.com/install-node-js-npm-mac) for how to install npm in Mac OS X)
  - gitbook install
  - gitbook init

# Serve it locally
 - gitbook serve
 
```bash
➜  icebreaking git:(master) ✗ gitbook serve
Live reload server started on port: 35729
Press CTRL+C to quit ...

info: 7 plugins are installed
info: loading plugin "livereload"... OK
info: loading plugin "highlight"... OK
info: loading plugin "search"... OK
info: loading plugin "lunr"... OK
info: loading plugin "sharing"... OK
info: loading plugin "fontsettings"... OK
info: loading plugin "theme-default"... OK
info: found 14 pages
info: found 0 asset files
info: >> generation finished with success in 1.0s !

Starting server ...
Serving book on http://localhost:4000

``` 
 
# Generate PDF
 - gitbook pdf . ./icebreaking.pdf (need install [calibre](https://calibre-ebook.com), please check [this](https://toolchain.gitbook.com/ebook.html) for detail)
