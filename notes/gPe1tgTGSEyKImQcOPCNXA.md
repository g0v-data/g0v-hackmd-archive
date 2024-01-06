---
title: "Kuansim Meeting Minutes - 2013/10/05"
tags: kuansim,hackpad
---

# Kuansim Meeting Minutes - 2013/10/05

> [點此觀看原始內容](https://g0v.hackpad.tw/pIxnxJIDS0a)


### 會議目的(Goal of this meeting)


- _澄清這個專案在這個週期要做什麼, 不做什麼_
> To discuss what will be implemented in this project.
> [name=Michael H]

- _討論專案採取什麼方式實作_
> To discuss how g0v developers and Berkeley students  will cooperate together
> [name=HisnYi C]


### 參與者(Attendees)


- hychen (g0v kuansim coordinator & backend engineer)
- kcliu (g0v kuansim frontend engineer)
- raejin
- mmmmmhuang
- jason
- dseeto
- jerchung
- ayc92

### 達成的共識(Agreement)


- Berkeley 團隊主要實做列在 [_kuansim flow_](https://docs.google.com/drawings/d/1Oudpipsr42Iepw90nb3T0mtlltu8iVMYL5hUt90Lxjw/edit)  [_chart (English version)_](https://docs.google.com/drawings/d/1Oudpipsr42Iepw90nb3T0mtlltu8iVMYL5hUt90Lxjw/edit) _的 "high priority" 的頁面_除了公眾人物時間軸部份。
> Berkeley team will focus on implementing the "top priority" pages excluding the public figure timeline in the [kuansim flow](https://docs.google.com/drawings/d/1Oudpipsr42Iepw90nb3T0mtlltu8iVMYL5hUt90Lxjw/edit)  [chart (English version)](https://docs.google.com/drawings/d/1Oudpipsr42Iepw90nb3T0mtlltu8iVMYL5hUt90Lxjw/edit).
> [name=HisnYi C]

- Berkeley 團隊會用 Ruby on Rails 實作上面提到的 "top priroty" 頁面的後端, 同時 g0v kuansim 團隊會用 node.js 繼續實作其他功能。換句話說, 不同的後端實作各自負責的功能並且提供 Restful API。
> Berkeley team will implement the backend of above functionalities in Ruby on Rails and g0v kuansim team will implement the rest of kuansim in node.js in parallel. 
> [name=HisnYi C]

> In other words, different backend/db take care of different parts of the functionality and provide a consistent  RESTful API.
> [name=HisnYi C]

- g0v kuansim 團隊跟 Berkely 團隊使用共同的前端程式碼
> g0v kuansim team and Berkeley team will use the same front-end code base.
> [name=HisnYi C]

- Any UI/UX/technical suggestion is welcomed
- coding convention will follow each languages'/tools' offcial convention. e.g. we will follow jade's official coding style when writing jade.

### 尚待討論的問題(Open Questions)


- API
- 實作方式

### 待辦事項(Actions)


1.  hychen : add github id of Berkeley to g0v. done.
2.  hychen: 術語定義, 像是什麼是爭議, 什麼是事件, 什麼是問題 done.
> Glossary definition , such as "what is the meaning of an issue/event/problem?"
> [name=HisnYi C]


