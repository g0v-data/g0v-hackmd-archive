# Pony V6テストまとめ
> **1_png**
>黒髪の魔法使いの少女が、静かな森の中で古い本を見つけて驚いている。
````
test_prompt = (
        "score_9, score_8_up, score_7_up, score_6_up, score_5_up, score_4_up, source_anime, "
        "1girl, wizard black hair, holding ancient book, quiet forest, surprised, manga style, black and white, lineart"
    )
````
=== LLaVAの検品結果 ===
この画像は次のストーリーと矛盾していません。キャラの特徴にズレはありません。魔法使いの少女が古い本を見つけて驚いているというストーリーは、キャラクターの性格や外見に合っています。

----
>**2_boy**
>黒髪の魔法使いの少年が、静かな森の中で古い本を見つけて驚いている。
````
test_prompt = (
        "score_9, score_8_up, score_7_up, score_6_up, score_5_up, score_4_up, source_anime, "
        "1boy, wizard black hair, holding ancient book, quiet forest, surprised, manga style, black and white, lineart"
    )
````
=== LLaVAの検品結果 ===
この画像は、静かな森の中で古い本を見つけた驚きを表現していますが、キャラクターの特徴にズレがあります。キャラクターは、魔法使いの少年ではなく、普通の少年であることが分かります。また、キャラクターは髪の色が黒であることが分かりますが、髪の様子や髪型にズレがあります。このような特徴により、この画像はストーリーと矛盾しています。

----
> 3_boy
> 黒髪の魔法使いの少年が、静かな森の中で古い本を見つけて微笑んでいる。
````
test_prompt = (
        "score_9, score_8_up, score_7_up, score_6_up, score_5_up, score_4_up, source_anime, "
        "1boy, wizard black hair, holding ancient book, quiet forest, gentle smile, manga style, black and white, lineart"
    )
````
=== LLaVAの検品結果 ===
この画像は、キャラクターが静かな森の中で古い本を見つけて微笑んでいるというストーリーと一致しています。キャラクターは黒髪であり、その特徴は画像に反映されています。また、キャラクターが着用している衣服も、ストーリーに沿って描かれています。
