# Disfactory i18n (internationalization) solution brainstorming

###### tags: `Disfactory` `dev`

## Problem 

Disfactory's frontend is only avaialble in Mandarin. This makes it inaccessible to non-mandarin readers. 

## Solution

This problem will be solved if users can select the language of their choice to use the app in. 

## Examples

### Secret Project #1

* /
* ?hl=ja_JP
* /?hl=zh_CN

I have to mask the project names to protect myself legally, but you can message me if you want to see live examples of the websites. 

Locale-based language. Set by url but also automatically detected based on, if I remember correctly, your browser/OS locale setting ( I think? ). 

On the backend, localization uses Django's gettext. Translation files are generated via a script, coming as .po files. 

Frontend localization uses vuex-i18n and gettext-extract. So, strings are input in their native language by developers, and then output to a .pot file that can then be converted to JSON and translated. The native language string is the key against which locale languages are resolved. 

A little convoluted, but it is the Offical Way By Gigantic Software Company You Definitely Have Heard Of


### Secret Project #2


![screenshot of language dropdown](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_01644662570d988806f10d4e69326e8f.png)

Uses a language dropdown to set language temporarily as a global frontend variable. Could save it to localstorage, for some reason doesn't. Don't ask me why. 

Uses i18next and react-i18next. Locale files are big JSONs that look like 

``` 
  some_key: "The Translatione Text"
```

And then you import like

          <H4>{t(`some_key`)}</H4>

Seems easier. I've poked around i18next and looks pretty well developed and maintained. 


## Disfactory


