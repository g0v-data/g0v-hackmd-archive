# Speech Translation Notes (Speech Lab 531)


> :arrow_right: Share your reading notes/implementation detail or secret/idea here. :arrow_left:

> 大家佛系更新，有看完paper來這邊隨便寫幾句話，分享某篇paper的重點，簡單幾句話都好，以省去其他人survey的時間，也供自己往後翻找資料便利; 有新發現的paper或想看的也可以貼上來，~~也可以把專題生寫的丟上來~~。 若有東西要討論也可以先貼在這，大家一起看共筆或許比較有效率？在這個艱困的語音研究路上互利共生ＸＤ。 [color=#d2a517] 
> 既然是佛系更新，就請隨便亂改沒關係，不影響閱讀為主。

> 不熟 HackMD 語法的我另外把 tutorial 獨立出來了，在這邊 [HackMD Tutorial](https://g0v.hackmd.io/_adY2HRWQ5W_Uufqa_VRaQ?view) 不佔這篇的空間。需要嵌入再加上 <code>{\%hackmd _adY2HRWQ5W_Uufqa_VRaQ %}</code> 就行了～
> [name=陳建成]



---

> **目錄會自動更新～** [color=#3b75c6]
- Auto-generated Table of Content
[ToC]


:::info
:pushpin: 使用教學 ➜ [HackMD Tutorials](https://hackmd.io/c/tutorials-tw/%2Fs%2Ftutorials-tw) 
:pushpin: 表情包 ➜ [Github](https://github.com/ikatyang/emoji-cheat-sheet)
:pushpin: 眼睛痛可以換暗色主題 ➜ [Reference link](https://titangene.github.io/article/hackmd-dark-theme.html)
:pushpin: Hex顏色編碼 ➜ [Link](https://color-hex.org)
:::
###### tags: `Speech-to-speech`, `Speech-to-text`, `Text-to-text`, `Meta learning`, `Self-supervised`, `ACL2021`, `Interspeech2021`, `AAAI2021`, `Simultaneous`

---

## :memo: Topic : Speech-to-text

> 隨意新增種類跟paper ～ [color=#3b75c6] 
> 可以留下名字以便討論
---
### Improving Speech Translation by Understanding and Learning from the Auxiliary Text Translation Task
:arrow_right: [paper link](https://aclanthology.org/2021.acl-long.328.pdf)
###### tags: `Speech-to-text`, `ACL2021`

Notes:

Decoupled acoustic and semantic encoder. ...

Shared by :dolphin: 

### "Listen, Understand and Translate": Triple Supervision Decouples End-to-end Speech-to-text Translation
:arrow_right: [paper link](https://arxiv.org/abs/2009.09704)
###### tags: `Speech-to-text`

Notes: Decoupled acoustic and semantic encoder. Use CTC loss on acoustic encoder, BERT distillation on semantic encoder.

Shared by george 

### Bridging the Modality Gap for Speech-to-Text Translation
:arrow_right: [paper link](https://arxiv.org/abs/2010.14920)
###### tags: `Speech-to-text`

Notes: Decoupled acoustic and semantic encoder. Use CTC loss on acoustic encoder, and use the CTC prediction to shrink acoustic encoder output by removing positions corresponding to blank or repeated tokens. Add NMT task on the semantic encoder and decoder, trained jointly.

Shared by george 

### Consecutive Decoding for Speech-to-text Translation
:arrow_right: [paper link](https://arxiv.org/abs/2009.09737)
###### tags: `Speech-to-text`

Notes: Decoupled acoustic and semantic encoder. Use CTC loss on acoustic encoder, and use the CTC prediction to shrink acoustic encoder output by removing blank and averaging repeated tokens. Concatenate the transcription and translation as training target.


Shared by george 

### Adaptive Feature Selection for End-to-End Speech Translation
:arrow_right: [paper link](https://aclanthology.org/2020.findings-emnlp.230/)
###### tags: `Speech-to-text`

Notes: Decoupled acoustic and semantic encoder. Use CTC loss on acoustic encoder, and use Adaptive feature selection (AFS) to shrink acoustic encoder output.


Shared by george 

---

## :memo: Topic : Speech-to-Speech

---
### Translatotron 2: Robust direct speech-to-speech translation
:arrow_right: [paper link](https://arxiv.org/abs/2107.08661)
###### tags: `Speech Translation` `Speech-to-speech`
Notes:

其實跟第一代沒啥太多的差別，主要是：
1. 不用source phoneme 做 multitask
2. target token會被decoder吃進去做語音合成
3. 移除speaker embedding，改用額外的TTS model生成特定語者的聲音當作training target，然後嘴砲說是為了anti-spoofing。
4. 新的data augmentation方法：任意sample dataset裡面的兩組資料，將他們concatenate起來直接丟下去train，以此確保model能夠preserve speaker information，貌似對聲音的quality蠻有用的，demo值得去聽聽。

Shared by Shun-Po

---

### SIMULS2S: END-TO-END SIMULTANEOUS SPEECH TO SPEECH TRANSLATION


---

## :memo: Topic : Text-to-text

---
### Contextual Parameter Generation for Universal Neural Machine Translation
:arrow_right: [paper link](https://arxiv.org/abs/1808.08493)
###### `Machine Translation`,`Meta Learning`
Notes:



Shared by :dolphin: 

---

## :memo: Topic : Text-to-speech

---
### One Model, Many Languages: Meta-learning for Multilingual Text-to-Speech

:arrow_right: [paper link](https://arxiv.org/pdf/2008.00768.pdf)

###### tags: `Text-to-speech`, `Multilingual`, `Meta-learning`

這篇paper最主要在做multilingual的TTS，最特別之處是他用meta-learning--> generated parameter 的方式去設計他的model。

paper寫得其實沒有很清楚，不過我是自己去翻他的[code](https://github.com/Tomiinek/Multilingual_Text_to_Speech)看他怎麼實作，code寫得很乾淨，推推，下圖是model，基於tacotron2去改的：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7a93b616f641a5cfed65b763ed029d3c.png)

* 所謂parameter generation？ 
基本上就是會有一個fully-connected network(左邊綠色的parameter generator)去吃language ID，那convolutional text encoder (中間粉紅色)裡面CNN的kernal就是parameter generator產生出來的weight，以此達到cross-lingual sharing。

* 右下角gradient reversal ?
其實就是常見的domain adaptation技巧，在backpropagate的時候法gradient加上一個負號。 所以classier目標是分辨speaker的話，reverse完就是希望去除speaker的資訊。(老師youtube有教可以找找)
這橘色的框框可有可無，端看是不是multi-speaker的dataset。

* 用language id去控制？
這篇paper因為用language id去控制，所以還可以達到code-switching的效果，蠻讚的。但他的code-switching的部分code不知為何跑不起來。

* corpus?
他們用CSS10，也有自己整理好的data非常方便，有一坨語言給你用，是從audiobook拿出來的，但偏偏沒有英文:).....?

shared by Shun-Po




---


## :memo: Topic : General topics

---
### 快速讀懂Gumbel softmax

讀原作者的[Blog](https://blog.evjang.com/2016/11/tutorial-categorical-variational.html)最快，其他中文資源都有點難看懂。

---




---

# :penguin: Idea Discussion
> 任何想法或研究問題都可以在這分享@@

---
#### Shun-Po
* Efficient data augmentation method for speech processing
* Self-supervised speech-to-speech translation
* Multilingual ASR + Tacotron 2
* Generated-parameter based code-switching framework




---

# :bug:  Data / Implementation Resources
> 各式疑難雜症，好用小東西分享。估計這區會很亂ＸＤ
:::info
:arrow_right: [在筆記中貼入程式碼](https://hackmd.io/s/how-to-use-code-blocks-tw#在筆記中貼入程式碼)
:::

## 裝ESPnet 沒 root

ESPnet就是難搞。
在戰艦雖然有kaldi，但缺的東西不少，沒root權限弄不起來
:arrow_right: 去 CI/ 下，用complie好的kaldi裝是最快的。[link](https://github.com/espnet/espnet/tree/master/ci)

---
## Kaldi format 問題

wav.scp, segmentation file.

---
## Multilingual Pre-trained ASR model
如果你想找multilingual pre-trained好的model，目前只有發現wav2vec 2.0 ，但他沒有給vocab，所以還是要自己fine-tune，[看這頁就夠了](https://colab.research.google.com/github/patrickvonplaten/notebooks/blob/master/Fine_Tune_XLSR_Wav2Vec2_on_Turkish_ASR_with_🤗_Transformers.ipynb#scrollTo=LBSYoWbi-45k) 。

也可參考huggingface上的說明。

---

## Download large files from Google drive
> [color=lime]
> > provided by george, documented by Chien-cheng Chen
> > Ref.: https://www.quora.com/How-do-I-download-a-very-large-file-from-Google-Drive/answer/Shane-F-Carr
> [name=陳建成][time=Sat, Sep 11, 2021 2:47 AM]
> ```bash
> FILEID=``""  # the file ID
> TOKEN=` `""  # the access token
> FILENAME=""  # the file name
> curl -H "Authorization: Bearer ${TOKEN}"         \
>      -o "${FILENAME}"                            \
>      'https://www.googleapis.com/drive/v3/files/'`
>     `"${FILEID}"'?alt=media'
> ```
> * `FILEID` is from the sharable link `https://drive.google.com/open?id=FILEID` of the target file. Steps:
>    1. Go to your Google Drive in your browser.
>    2. Right-click (or control-click) the file you want to download and click “Get shareable link”. The link looks like this: `https://drive.google.com/open?id=FILEID`. Make note of the file ID “FILEID”.
> 
> * `TOKEN` is the OAuth token obtained from:
>    1. Go to [OAuth 2.0 Playground](https://developers.google.com/oauthplayground/)
>    2. In the “Select the Scope” box, scroll down, expand “Drive API v3”, and select `https://www.googleapis.com/auth/drive.readonly`
>    3. Click “Authorize APIs” and then “Exchange authorization code for tokens”. Copy the “Access token”; you will be needing it below.
> 
> * `FILENAME` is the file name to be downloaded.
> 
> Windows version
> ```
> Invoke-RestMethod                              `
>     -Method  Get                                `
>     -OutFile FILENAME                          `
>     -Headers @{"Authorization"="Bearer TOKEN"} `
>     -Uri     https://www.googleapis.com/drive/v3/files/FILEID?alt=media
> ```