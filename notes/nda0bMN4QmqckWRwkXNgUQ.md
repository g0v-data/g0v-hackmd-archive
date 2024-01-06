---
title: "Welcome to hackfoldr.org"
tags: hackpad
---

# Welcome to hackfoldr.org

> [點此觀看原始內容](https://g0v.hackpad.tw/Z7w9CVHTHEh)

> This document is a copy of [https://hackpad.com/Welcome-to-hackfoldr.org-NBPEZPxIRw9](https://hackpad.com/Welcome-to-hackfoldr.org-NBPEZPxIRw9)
> [name=caasi H]


People use various online collaboration tools nowadays.  It has become difficult to share all the relevant information and services used within a project.  Until hackfoldr.

## Quick Start

Go to [http://ethercalc.org](http://ethercalc.org) and create a spreadsheet.  Paste in a bunch of urls in the first column, and add titles to the second column.  copy the path component in the your url and append it to [http://hackfoldr.com/#/](http://hackfoldr.com/#/), for example:

```txt
http://ethercalc.org/hackfoldr gets you http://hack.g0v.tw/#/hackfoldr

```
## Why?

We need a way to organize many dynamic documents before and during _hackathons_.
The shared folder feature in _google docs_, which is surprisingly unknown to many, comes very close to what we want.  But as every document is opened in edit mode, it soon becomes unusable due to the number of concurrent connections. It is also impossible to sort the items, and we had to use numeric prefix to achieve that.  Remember gopher?

_Hackpad_ is slightly easier for hackathon collaboration with concise authorship coloring, and it also has better formatting compared to vanilla etherpad/etherpad-lite based services.  But when it comes to organizing lots of  documents, _Hackpad collections_ isn't really much better than google doc folders.

So we build this small single-page static web application that reads a list of url from an EtherCalc document, rendering it in a way similar to a google docs folder. If the document supports read-only mode, we use that by default when it is opened by the user, and provide an additional edit link.

## Features

Supported document types
    - Google Docs, Presentation, Drawing: view mode by default
    - Google Spreadsheets
    - Hackpad
    - EtherCalc
    - ... actually just any url that does not forbid iframe embedding via X-Frame-Options

On the 4th column you can add comma-separated values that will be rendered as [bootstrap-labels](http://twitter.github.com/bootstrap/components.html#labels-badges) to the entry.  each tag can optionally contain a bootstrap label class name, followed by :.  For example README:important creates a read important label of "README".

Indenting urls in the first column of the spreadsheets with spaces creates subfolders.  Currently only 1 level of folders is supported.

## Install

If you want to run your own instance and/or help improving hackfoldr, checkout [https://github.com/hackfoldr/hackfoldr](https://github.com/hackfoldr/hackfoldr) and:

% npm i
% ./node_modules/.bin/brunch w -s

It is built with Angular.js and LiveScript.

## Contributing

hackfoldr is young and lacks lots of features. Please report issues, send feature requests via github, and  fork the repository on github to send pull requests. Happy hacking!

## Acknowledgements

Special thanks to [#g0v](https://g0v.hackpad.tw/ep/search/?q=%23g0v&via=Z7w9CVHTHEh).tw hackers and early-adopters for insipiring and improving hackfoldr.

## License

CC0 1.0 Universal

To the extent possible under law, Chia-liang Kao has waived all copyright and related or neighboring rights to hackfoldr.

This work is published from Taiwan.

[http://creativecommons.org/publicdomain/zero/1.0](http://creativecommons.org/publicdomain/zero/1.0)

