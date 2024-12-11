---
tags: vTaiwan小松
---
# 1101小松 1101 Meetup 
參與連結 / Links：https://meet.jit.si/vTaiwan
參與者簽到 / Participants：peter, bruno, eli,vienna, tzu sheng, deger
本週議題 / Issues：

後續分享內容 / sharing 
報告與提案書翻譯 / Translation 
與 Talk to the City 合作 / Cooperation with Talk to the City 
成果延續 / Things TBD 

## 後續分享內容 / sharing 

10/31 National Yang Ming Chiao Tung University sharing (one of the most prominent institutions on development of semiconductor and AI)
陽明交通大學 戴瑀慧老師 分享 9:00-12:00
(postponed)> 11/28 

11/16 GCTF Forum (project between US Department of States, Taiwan Ministry of Foreign Affairs, and Japan)

11/25 Code for Japan Summit 2023 (biggest civic tech community in Japan)


## 報告與提案書翻譯 / Translation 

it will be done in 11/10, but it can be sooner

traslation: https://g0v.hackmd.io/@Pno233SAS8G5UfL5OvSRmA/DIforAIvTaiwanxChatham/%2FtuP2xx-ETjiKhfx9XYv6kA 

## 與 Talk to the City 合作 / Cooperation with Talk to the City 


1. Reaching out government agency 

2. Using the transcript of the civic assembly to input the data. 

3. challenges: 
- problems on deployment, different environment. 


### introduction of Talk to the City 

1. Future direction: reaching out to gov/buttom-up strategy 

2. Taiwan AI Academy - looking at diarization. (from different participants)

### Tools application 

[TTTC github](https://github.com/AIObjectives/talk-to-the-city-reports)



:::warning

-  for some reason example.csv is broken when downloading repo as zip file
-  does not work on python3.12
- it works for a while, then it doesn't
```
python main.py configs/example.json                                                                                                                                                                         ─╯

So, here is what I am planning to run:
{'step': 'extraction', 'run': False, 'reason': 'nothing changed'}
{'step': 'embedding', 'run': False, 'reason': 'nothing changed'}
{'step': 'clustering', 'run': False, 'reason': 'nothing changed'}
{'step': 'labelling', 'run': False, 'reason': 'nothing changed'}
{'step': 'takeaways', 'run': False, 'reason': 'nothing changed'}
{'step': 'overview', 'run': False, 'reason': 'nothing changed'}
{'step': 'translation', 'run': False, 'reason': 'nothing changed'}
{'step': 'aggregation', 'run': False, 'reason': 'nothing changed'}
{'step': 'visualization', 'run': True, 'reason': 'previous data not found'}
Looks good? Press enter to continue or Ctrl+C to abort.

Skipping 'extraction'
Skipping 'embedding'
Skipping 'clustering'
Skipping 'labelling'
Skipping 'takeaways'
Skipping 'overview'
Skipping 'translation'
Skipping 'aggregation'
Running step: visualization

> next-app@0.1.0 build
> next build

Errors:
/home/elilin/tttc/next-app/node_modules/next/dist/lib/picocolors.js:130
const { env, stdout } = ((_globalThis = globalThis) == null ? void 0 : _globalThis.process) ?? {};
                                                                                             ^

SyntaxError: Unexpected token '?'
    at wrapSafe (internal/modules/cjs/loader.js:915:16)
    at Module._compile (internal/modules/cjs/loader.js:963:27)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1027:10)
    at Module.load (internal/modules/cjs/loader.js:863:32)
    at Function.Module._load (internal/modules/cjs/loader.js:708:14)
    at Module.require (internal/modules/cjs/loader.js:887:19)
    at Module.mod.require (/home/elilin/tttc/next-app/node_modules/next/dist/server/require-hook.js:64:28)
    at require (internal/modules/cjs/helpers.js:74:18)
    at Object.<anonymous> (/home/elilin/tttc/next-app/node_modules/next/dist/build/output/log.js:55:21)
    at Module._compile (internal/modules/cjs/loader.js:999:30)

Pipeline completed.
```
:::








:::info

processced data from 0924 event

- [ manually tag and revised transcipt in csv](https://drive.google.com/file/d/1Ep6Gt68CEI8gR1GvqrbSCUscNBKAHf6i/view?usp=sharing)

- [polis comment in csv](https://drive.google.com/file/d/1X5xg4TDm_wKJ6uoHBs9Tm5LPYi343HrI/view?usp=sharing)

:::

tttc把一堆東西都先翻譯成英文來處裡

### Rough Timeline

## 成果延續 / Things TBD 


### diarization 
> [name=Eli]

:::success

[pyannote/speaker-diarization-3.0 ](https://huggingface.co/pyannote/speaker-diarization-3.0)

[result](https://pastebin.com/NM04256a)

:::

:::    success

[whisperx](https://github.com/m-bain/whisperX)

[result](https://drive.google.com/file/d/1Jc8tGDKfr35936W07h_kp6kULmEuCAlF/view?usp=drive_link)

- super fast
- no idead how to use it :(

:::

:::warning


trying with [nemo](https://github.com/NVIDIA/NeMo/tree/177a67fa4a43ed6f7c4fb39a66c0a2998a27fef1) now

:::
---
### proposal: 
１. setting up a communication group with MODA and AIA to have discussion with AIA 
2. Using GitHub to do the sharing of features
- diarization 
    - isabel 
    - 
- time=stamp 

3. ways to communicate 
- message: signal 
- repo/product: github

4. Potential development:
- AI agent 
- AI host for discussion 
- AI analyzation 

related links:
- [AI Objective Institute](https://ai.objectives.institute/)
- [final report of recursive public](https://vtaiwan-openai-2023.vercel.app/Report_%20Recursive%20Public.pdf)
- [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442)
- [Deliberating with AI: Improving Decision-Making for the Future through Participatory AI Design and Stakeholder Deliberation](https://dl.acm.org/doi/10.1145/3579601)
- [depolarized app](https://github.com/Onurbon/depolarized-app)

## Ramdon notes
- translation functions


- josh's cute cat!






