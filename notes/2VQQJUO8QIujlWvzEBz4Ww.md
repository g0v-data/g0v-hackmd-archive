---
title: "g0v web app generator"
tags: hackpad
---

# g0v web app generator

> [點此觀看原始內容](https://g0v.hackpad.tw/h7l85hxQsF5)


利用yeoman建立g0v 網頁快速開發的框架，將g0v常用的套件包裝起來，下次可以重複利用，加速開發
短期目標是 2/22 黑客松當天可以讓大家使用，同樣可以衍生出g0v extension generator 加速瀏覽器擴充開發
repo: [https://github.com/g0v/generator-g0v-webapp](https://github.com/g0v/generator-g0v-webapp)
> 先push 上去 慢慢加東西 !!
> [name=Yuan C]

常用項目
- [ ] angular
- [ ] bower
    - [ ] semantic ui
    - [ ] twitter bootstrap 3.0
    - [ ] angular
- [x] files
    - [x] deploy script [https://github.com/g0v/ly.g0v.tw/blob/master/deploy](https://github.com/g0v/ly.g0v.tw/blob/master/deploy)
    - [x] .editorconfig
    - [x] .gitignore
- [x] livescript
- [x] gulp
    - [x] express
    - [x] jade
        - [ ] (static and compile to angularjs templates
    - [x] stylus
        - [ ] ruby-sass
    - [x] livereload
- [ ] karma tests
- [ ] protractor tests
- [ ] g0v common navbar <\-\- 這是...?
> 有g0v logo的navbar之類的
> [name=Yuan C]

> 話說之前有的g0v tabzllla 的想法 XDDD
> [name=Yuan C]

- [ ] travis config
目錄結構
```
_public/ (compile後的資料夾, watch point)
app/
|_ partials/
|_ app/
     | controllers/
     | directives/
     | services/
|_ assets/
     | img/
           | g0v logo
     | styles/
test/
.travis/
.gitignore
.editorconfig
gulpfile.ls
package.json
bower.json
.bowerrc
karma.conf.js
deploy



