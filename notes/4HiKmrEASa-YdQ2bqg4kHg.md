---
title: "2D Online Chat: Story Line Feature"
tags: "2d-online-chat"
---

# 2D Online Chat: Story Line Feature

Code base (WIP): https://github.com/g0v/greatescape2035/tree/story-line


## Proposal
This is a proposal for the "story line" or "mission" framework in 2d-online-chat. Key features we want to support:
  - [x] Talk to an NPC to trigger the next step.
  - [x] Go to a specific region on the map to trigger the next step.
  - [ ] Branches. For example,
    - [x] Go to different branch when a user select a different answer.
    - [ ] Go to different branch when a user go to different region on the map.
  - [ ] Game states
    - [x] Global state (e.g. a counter of some choices)
    - [x] Choices made by the current user
    - [ ] Randomly generated state

## Detail Design


### File schema
We use JSON format, since it is natively supported by javascript. However, I'll use YAML in the example, since it is easier to type.

The file contains multiple missions, each "mission" will have a title, multiple steps.  "steps" is a mapping from `step-id` to step definition.  "steps" forms a directed graph (a state machine).

```
missions:
  <mission-id>:  # repeated
    title: <mission-title>
    description: <...>
    depend:
      - [
          "<mission>/<step>/done", 
          {
            "storeKey": "<key>",
            "value": "<expected value>"
          } 
        ]
      - ...
    firstStep: <step-id>
    steps:
      <step-id>:  # repeated
        title: <step-title>
        description: <...>
        nextStep: <step-id>  # the default next step
        npcId: <npc-id>  # Trigger this step by pressing ENTER near this NPC.
                         # NPC can be an object (e.g. a box).
        locationId: <locationId>  # Trigger this step by move close to a
                                  # location on the map.
        # if none of <npcId> and <locationId> are given, the conversation
        # will be triggered immediately.
        dialog:
          - name: "NPC name" or $player  # who is talking
            line: "hello, $player"
            id: <line-id>  # optional
            nextLine: <line-id>  # optional: if we don't want to fallthrough.  "$EOD" means "end of dialog"
          - name: "NPC name" or $player
            type: "input.select"  # declare a multiple choice question
            storeKey: "<key>"  # field name to save the answer
            question: "Red pill or blue pill?"
            choices:
              - text: "Red"
                nextLine: <line-id>
              - text: "Blue"
                nextLine: <line-id>
          - name: ...
            type: "input.text"  # declare a open-ended question.
            storeKey: "<key>"  # answer will be saved in this field.
            question: "what is your name?"
```


#### Example
You can also check out this [JSON file](https://github.com/g0v/IDystopia/blob/builder/static/story-lines/regular.json).

```
missions:
  mission-find-axe:
    # mission definition
    title: "打電話"
    description: "收到法院的通知,銀行帳戶被列為警示帳戶..."
    firstStep: step-1
    steps:
      step-1:
        title: "打給爸爸"
        description: "到法院的通知,銀行帳戶被列為警示帳戶...打給爸爸"
        npcId: "lost-and-found-npc"
        nextStep: step-2
        dialog:
          - name: 玩家
            line: 爸,我的手機剛剛收到一個通知說我的銀行帳戶被列為警示帳戶,怎麼辦!!
          - name: 父親
            line: 你想想看是不是有亂簽名或者是有做過什麼事情
          - name: 玩家
            line1:沒有阿 
            Line2:好像有在...
      step-2:
        title: "和媽媽對話"
        description: "收到法院的通知,銀行帳戶被列為警示帳戶...打給媽媽"
        npcId: "Lady of Lake"
        nextStep: step-3
        dialog:
          - name: $player
            line: 不好意思，請問您有撿到我的斧頭嗎？
          - name: 湖中女神
            question: 我最近確實撿到了一些斧頭，請問你掉的是金斧頭還是銀斧頭？
            choices:
              - text: 銀色的
                nextLine: label-bad
              - text: 金色的
                nextLine: label-bad
              - text: 都不是
                nextLine: label-good
          - id: label-bad
            name: 湖中女神
            line: 騙子！受死吧！
            nextLine: $EOD  # "EOD" is a special label, which means end of dialog.
            nextStep: step-5  # override the default next step
          - id: label-good
            name: 湖中女神
            line: 那我沒撿到你的斧頭，自己去找吧！
            nextLine: $EOD
```

### Game Mechanism
All missions of a given map should be collected into one single file.
Each player will have a new property: `story_line_states`, which is a list of strings `"<mission-id>:<step-id>"`.  For each step, there is an NPC id, players have to find these NPCs (active NPC) to trigger the next step.  In render function, active NPCs will have exclamation marks ("!") on their heads.  When a player is standing next to an active NPC, a dialog will be shown to select a dialog (because there might be multiple steps of missions assigned to the same NPC).

* Save user state to local storage
* Global state
  1. there are `n` people online that has finished mission `m1`, mission `m2` will be enabled.
     * this might be easier, because we only need to maintain the "current state".
  3. there are `n` people finished mission `m1` (accumulative), then mission `m2` will be enabled.
     * this is more difficult, we need to save this info somewhere.

### Game State


## Alternatives

## Required Works

## Open Questions
