---
title: "Hacktabl 2"
tags: hackpad
---

# Hacktabl 2

> [點此觀看原始內容](https://g0v.hackpad.tw/nbhQS36Tcx9)


User interface improvements that features:
- Label view that shows all items with labels specified by the user.
- Column selection and row selection, allowing users to view a subset of table cells
- Mobile-friendly menu (navigational drawer for topics!) and tooltip
- Easy table creation
- Use of inline text for description page, in addition to URLs of a web page (which is the current setup)
- Possibly i18n?

And preserves the following hacktabl traits:
- using ethercalc and google doc as backend
- "Hightlight" and "summary" features
- Helpful error messages that guides the user to setup correctly

## TODOs

- [x] New table parser - [https://github.com/MrOrz/hacktabl-parser](https://github.com/MrOrz/hacktabl-parser)
- [x] UI sketch w/ interaction design (adopting google's material design)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3e6b1650b175059fc4bad1384934ccd7)

- [x] Implementation - [http://github.com/g0v/hacktabl/tree/2](http://github.com/g0v/hacktabl/tree/2)

## Solution stack (planned)

React.js w/ reduxjs
Frontend UI framework: material-design-light +
Dialects: CSS - sass(compiler:node-sass, lib: node-comoass or bourbon), JS - vanilla es6/7 (transpiler: babel, bundler: webpack)

multi-line ellipsis: steal code from [https://github.com/ideal-react/auto-ellipsis/blob/master/src/component/auto-ellipsis.jsx](https://github.com/ideal-react/auto-ellipsis/blob/master/src/component/auto-ellipsis.jsx) !



