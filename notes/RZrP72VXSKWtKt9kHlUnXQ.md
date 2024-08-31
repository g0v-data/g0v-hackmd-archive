---
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon, civil defense, meshtastic
image: https://adrelien.com/blog/content/images/2024/02/meshtastic.png
title: 來寫一個小白都會用的Meshtastic App吧！開發日誌
---
# 來寫一個小白都會用的Meshtastic App吧！開發日誌

[TOC]

# 2024.8.31
- **建置開發環境**：到[這裡](https://developer.android.com/studio?hl=zh-tw)下載安裝包，之後都是下一步下一步就是了。
    > 我虛擬機裝的Android 11，因為沒有這版本的實體機，不確定全部功能都能否使用。[name=minexo79]
- **新增打招呼快捷按鈕**：利用原有的QuickChat功能，在「第一次」開啟App的時候新增預設按鈕。
    > 這是我第一次寫Kotlin就上手，在此之前我都沒有寫過XD [name=minexo79]

## Meshtastic Android Build 
以下節錄自[Building the Android App - Meshtastic.org Docs](https://meshtastic.org/docs/development/android/)
- Clone Git / Fork Git From `https://github.com/meshtastic/Meshtastic-Android`.
- Use `git submodule update --init --recursive` to pull in the various sub-modules we depend on.
- There are a few config files which you'll need to copy from templates included in the project. Run the following commands to do so:
:::warning
**注意**：這裡原本是
```bash
rm ./app/google-services.json
cp ./app/google-services-example.json ./app/google-services.json
rm ./app/src/main/res/values/curfirmwareversion.xml
cp ./app/special/curfirmwareversion.xml ./app/src/main/res/values/
```
新版的 (v2.4.4 / master) 改成 
```bash
rm ./app/google-services.json
cp ./app/google-services-example.json ./app/google-services.json
```
:::

- Now you should be able to select "Run / Run" in the IDE and it will happily start running on your phone or the emulator.

## Source Code
- MainActivaty.kt
```kotlin
 override fun onCreate(savedInstanceState: Bundle?) {
        installSplashScreen()
        super.onCreate(savedInstanceState)

        if (savedInstanceState == null) {
            val prefs = UIViewModel.getPreferences(this)
            // 2024.8.31 Blackcat: First run Set Default Quick Chat Options
            if (!prefs.getBoolean("app_set_init_quick_chats", false)) {
                lifecycleScope.launch {
                    // 2024.8.31 Blackcat: add Taiwanese greet
                    model.initTaiwaneseGreetQuickChat()
                    prefs.edit { putBoolean("app_set_init_quick_chats", true) }
                }
            }
            
            // Next Init ...
        }
}
```
- UIState.kt
```kotlin
suspend fun initTaiwaneseGreetQuickChat()
{
    // 2024.8.31 Blackcat: add Taiwanese greet
    quickChatActionRepository.insert(QuickChatAction(0, "打招呼", "你好!", QuickChatAction.Mode.Instant, 0))
    quickChatActionRepository.insert(QuickChatAction(0, "吃飽沒", "甲霸味?", QuickChatAction.Mode.Instant, 0))
    quickChatActionRepository.insert(QuickChatAction(0, "問近況", "最近還好嗎?", QuickChatAction.Mode.Instant, 0))
    quickChatActionRepository.insert(QuickChatAction(0, "敷衍他", "喔好喔", QuickChatAction.Mode.Instant, 0))
}
```

## Result
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e4e44241aa9052e9157b4939cc6e38c.png)
