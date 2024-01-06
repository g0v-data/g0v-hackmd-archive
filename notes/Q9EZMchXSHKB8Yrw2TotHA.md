---
title: Hackfoldr Theme for HackMD Book mode
author: Yukai Huang
description: use `{%hackmd @yukaii/hackfoldr-book-mode-theme %}` syntax to include this theme
image: https://i.imgur.com/VqTF1wq.png
tags: theme
---

<style>


@media (min-width: 759px) {
    .summary .toolbar {
        padding-top: 6px;
        top: 0px;
        height: 51px;
    }

    .summary #summary {
        padding-top: 0;
    }
}


#summary ul li a {
    margin-top: -2px;
}

#summary ul li.active a, #summary ul li a:hover, #summary ul li a:active {
    color: white;
    text-decoration: none;
    border-radius: 6px;
}

#summary ul li.active a {
    background-color: #383838;
}

#summary ul li a .label {
    position: absolute;
    right: 1em;
    padding: 5px 8px;
}

#summary h1 {
    border-bottom: none;
}

#summary h2 {
    color: #a9a9a9;
    margin: 0;
    padding: 15px 25px 15px;
    cursor: pointer;
    font-size: 15px; 
}

.summary h1 + .nav, 
.summary h2 + .nav, 
.summary h3 + .nav, 
.summary h4 + .nav, 
.summary h5 + .nav, 
.summary h6 + .nav {
    padding-left: 0px;
    padding-right: 0px;
}

.nav-stacked>li {
    padding-left: 10px;
    padding-right: 10px;
}

.summary h1 + .nav li:last-child, .summary h2 + .nav li:last-child, .summary h3 + .nav li:last-child, .summary h4 + .nav li:last-child, .summary h5 + .nav li:last-child, .summary h6 + .nav li:last-child {
    margin-bottom: 0;
}

.nav>li>a {
    padding: 7px 15px;
}

.summary .nav > li > a {
    font-size: 14px;
}
</style>


<style>
:root {
    --bg-color: #131313;
    --text-color: white;
    --highlight-color: #13ed00;
    --border-color: #515151;
}

.summary {
    background-color: var(--bg-color);
    color: var(--text-color);
    box-shadow: none;
    border: none;
}

.summary .toolbar {
    background-color: var(--bg-color);
    border-color: var(--border-color);
    color: var(--text-color);
}

.summary h1.collapsible:not(:first-child), 
.summary h2.collapsible:not(:first-child), 
.summary h3.collapsible:not(:first-child), 
.summary h4.collapsible:not(:first-child), 
.summary h5.collapsible:not(:first-child),
.summary h6.collapsible:not(:first-child) {
    border-color: var(--border-color);
}

.summary h1 .fa-angle-down,
.summary h2 .fa-angle-down, 
.summary h3 .fa-angle-down, 
.summary h4 .fa-angle-down, 
.summary h5 .fa-angle-down, 
.summary h6 .fa-angle-down {
    color: var(--highlight-color);
}

.summary .nav > li > a {
    color: var(--text-color);
    opacity: .8;
}


.summary .nav-pills > li.active > a, .summary .nav-pills > li.active > a:focus, .summary .nav-pills > li.active > a:hover {
    color: var(--highlight-color);
    opacity: 1;
}

.topbar {
    color: var(--text-color);
    background-color: var(--bg-color);
    box-shadow: none;
    border-bottom: 1px solid var(--border-color);
}

.ui-summary-action {
    opacity: .7;
    color: var(--text-color);
}

.book-container {
    box-shadow: none;
    border-left: solid 1px var(--border-color);
}


.btn.focus, .btn:focus, .btn:hover {
    color: var(--highlight-color);
}

input.form-control {
    background-color: var(--bg-color);
    color: var(--text-color);
    border-color: var(--border-color);
}

input.form-control:focus {
    border-color: var(--highlight-color);
    box-shadow: none;
}

body {
    background-color: var(--bg-color);
}

code {
    background-color: #651fff;
    color: white;
    border-radius: 10px;
    padding: 3px 10px;
}
</style>

```jsx=
const EDITABLE_VARIABLES = {
  [REQUEST_VARIABLE_ID.gender]: true,
  [REQUEST_VARIABLE_ID.age]: true,
  [REQUEST_VARIABLE_ID.accidentRecord]: true,
  [REQUEST_VARIABLE_ID.carModel]: true,
  [REQUEST_VARIABLE_ID.year]: true,
}
```