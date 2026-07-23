## 開発ノート
`文字入力、プロンプト入力->ストーリーを入力することに絞る`
### h3 次にやること
* ハギングフェイスからAPIキーを用いて、メモ帳に書いたコードの書き方で解決する方法

> 7/16
>環境をllama と llavaで分けて、裏で片方のターミナルを開いておく
# llama環境を開くには
````
source LLaVA/llama/llama_env/bin/activate
````
Llavaをサーバーとして裏で起動しておき、Llamaの環境で一連の動作（メインスクリプト）を実行する流れが一番スムーズです。

* ステップ1：【Llavaの環境】でサーバーを起動する
ターミナルを開き、Llavaのvenvに入ってサーバーを起動します。これにより、Llavaが指定したポート（例: 8000番）で命令を待つ状態になります。

Bash
````
# Llavaの仮想環境をアクティベート
source llava_env/bin/activate  # Windowsなら llava_env\Scripts\activate

# vLLMなどを使ってLlavaをAPIサーバーとして起動
vllm serve "あなたのLlavaのモデル名" --port 8000
（※起動したら、このターミナルは閉じずにそのまま放置します）
````
* ステップ2：【Llamaの環境】で一連のコードを実行する
別のターミナル画面を開き、Llama-3.2-1B のvenvに入ります。そこで以下のような「一連の動きをまとめたスクリプト（pipeline.py）」を作成して実行します。

Python
````
import requests
import torch
from transformers import pipeline
````

# 動作1: 裏で待機しているLlavaサーバーに画像を分析してもらう
````
print("1. Llavaで画像を分析中...")
image_url = "https://example.com/sample.jpg"  # 分析したい画像

response = requests.post(
    "http://localhost:8000/v1/chat/completions",
    json={
        "model": "あなたのLlavaのモデル名",
        "messages": [
            {
                "role": "user",
                "content": [
                    {"type": "text", "text": "この画像には何が写っていますか？詳しく説明してください。"},
                    {"type": "image_url", "image_url": {"url": image_url}}
                ]
            }
        ]
    }
)
# Llavaが返してきた説明テキストを文字として受け取る
llava_description = response.json()["choices"][0]["message"]["content"]
print(f"Llavaの分析結果: {llava_description}\n")
````


# 動作2: 受け取った結果をそのままLlama-3.2に引き渡して文章を作らせる
````
print("2. Llama-3.2で文章を生成中...")
model_id = "meta-llama/Llama-3.2-1B"
pipe = pipeline("text-generation", model=model_id, torch_dtype=torch.bfloat16, device_map="auto")

# Llavaの解説をプロンプト（指示文）に組み込む
prompt = f"以下の画像の説明を元にして、面白いSNSの投稿文を作ってください。\n説明: {llava_description}"

final_output = pipe(prompt)
print("--- 最終出力結果 ---")
print(final_output[0]["generated_text"])
````
> 7/9
**llama**
clone
````
git clone https://github.com/meta-llama/llama3.git
cd llama3
````
「pip install -e」までやったところで、エラーが発生した。
**tiktoken は Rust 言語 のビルド環境が必要なパッケージのため、お使いの環境（Python や OS）に Rust や C++ のコンパイラが入っていないと、ソースコードからの組み立て（ホイール生成）に失敗してしまいます。**
まずは pip 自体を最新にし、tiktoken の既成バイナリ（すでにビルド済みのもの）を単体でインストールします。
````
pip install --upgrade pip setuptools wheel
pip install tiktoken
````
このあともう一度「pip install -e」をやりなおして成功

モデルを動かそうとするとエラーが出たので、
* requirements.txtをインストールする
````
pip install -r requirements.txt

````
requirements.txt を書き換えるメモ帳やエディタで requirements.txt を開き、tiktoken==0.4.0 と書かれている行を tiktoken>=0.7.0 に書き換えて保存します。手動で最新にするその上で、以下のコマンドを実行して最新の tiktoken を入れ直します。
````
bashpip install "tiktoken>=0.7.0"
````

````
from diffusers import StableDiffusionXLPipeline
````
これをtransformに


----
> 7/3
**Pony v6のコンテナ移行及び他AIとのつなげ作業**

* 必要なライブラリのインストール(ターミナル)
````
pip install diffusers transformers accelerate peft safetensors

※ torch と torchvision はすでにLLaVAのインストール時に最適なバージョンが入っているため、上書きによる競合を防ぐためにここでは除外しています。

````
> pipeline.py の書き換え(書き換え前のコードは前回) 
````
import subprocess
import torch
from diffusers import StableDiffusionXLPipeline

def generate_pony_image(prompt, output_path):
    print("\n--- [Pony v6] 画像の生成を開始します ---")
    
    # 1. Pony V6のベースモデルを読み込む
    pipe = StableDiffusionXLPipeline.from_pretrained(
        "Bakanayatsu/Pony-Diffusion-V6-XL-for-Anime",
        torch_dtype=torch.bfloat16
    )
    pipe = pipe.to("cuda")

    # 2. Pony V6用の固定ネガティブプロンプト
    negative_prompt = (
        "score_4, score_5, score_6, source_pony, source_furry, lowres, "
        "bad anatomy, bad hands, text, error, missing fingers, extra digit, "
        "fewer digits, cropped, worst quality, low quality"
    )

    # 3. 画像を生成
    image = pipe(
        prompt=prompt,
        negative_prompt=negative_prompt,
        num_inference_steps=30,
        guidance_scale=7.0
    ).images[0]

    # 4. 指定されたパスに画像を保存
    image.save(output_path)
    print(f"--- [Pony v6] 画像を保存しました: {output_path} ---")


def check_contradiction_with_llava(image_path, story_text):
    print("\n--- [LLaVA] 画像の検品を開始します ---")
    
    # ターミナルコマンドを再現
    query_text = f"この画像は次のストーリーと矛盾していますか？キャラの特徴にズレがあれば具体的に指摘してください。 ストーリー: {story_text}"
    cmd = [
        "python", "-m", "llava.eval.run_llava",
        "--model-path", "liuhaotian/llava-v1.5-7b",
        "--image", image_path,
        "--query", query_text
    ]
    
    # 実行して結果を取得
    result = subprocess.run(cmd, stdout=subprocess.PIPE, text=True, encoding="utf-8")
    return result.stdout


if __name__ == "__main__":
    # テスト用の仮の1コマ目ストーリー
    test_story = "黒髪の魔法使いの少女が、静かな森の中で古い本を見つけて驚いている。"
    
    # Pony v6用のプロンプト（提供いただいた品質タグ + ストーリーの要素）
    test_prompt = (
        "score_9, score_8_up, score_7_up, score_6_up, score_5_up, score_4_up, source_anime, "
        "1girl, wizard black hair, holding ancient book, quiet forest, surprised, manga style, black and white, lineart"
    )
    
    # 保存先ファイルのパス
    output_image = "frame_1.png"
    
    # 【処理1】Pony v6で1コマ目の画像を生成
    generate_pony_image(test_prompt, output_image)
    
    # 【処理2】生成された画像をLLaVAで検品
    llava_feedback = check_contradiction_with_llava(output_image, test_story)
    
    print("\n=== LLaVAの検品結果 ===")
    print(llava_feedback)

````
> テスト実行
````
python pipeline.py
````



----

> 6/28
LLaVAの導入（マルチモーダルAIとして）
**新しく Python 3.10 を入れ直すよりも、「現在の Python 3.12 のままで、LLaVA 側の要求（Python 3.10用である PyTorch 2.1.2）を無視して最新の PyTorch を強制的に使う」方式**

* 仮想環境（venv）を作る
````
# 仮想環境を作成
python3 -m venv l_env

# 仮想環境を有効化（画面左端に (l_env) と出ます）
source l_env/bin/activate

# pipを最新にする
pip install --upgrade pip
````
* LLaVA が求めている 2.1.2 は諦めて、現在の Python 3.12 で動く最新の PyTorch（2.4以上など）を先に手動でインストール

````
# Python 3.12 に対応した PyTorch をインストール
pip install torch torchvision torchaudio

````

* 通常通り pip install -e . を実行すると、LLaVA が「やっぱり 2.1.2 じゃないとダメ！」とエラーを出してしまいます。そのため、--no-deps（依存関係のチェックを無視する） というオプションを使って、LLaVA 本体だけを強制インストールします。

````
# LLaVAフォルダに移動
cd /workspace/LLaVA

# バージョンチェックを無視して LLaVA を強制インストール
pip install --no-deps -e .

````
* 足りない他のパッケージを補う

````
pip install -r requirements.txt

````
*上記でエラーが出たので、足りていないパッケージを別の方法で補う
````
pip install bitsandbytes fastapi markdown2[all] pydantic shortuuid uvicorn peft gradio==4.16.0 gradio_client==0.8.1 timm==0.6.13 einops-exts==0.0.4 scikit-learn==1.2.2

````
* 7Bモデルを4bitで軽く動かすコマンド（そんなものはなく、失敗したので次回はやらない）
````
python -m llava.eval.run_llava \
    --model-path liuhaotian/llava-v1.5-7b \
    --image images/llava_logo.png \
    --query "What is unusual about this image?" \
    --load-4bit
````
### h3「次回コンテナを開いたときの注意点」

もし一度コンテナを閉じたり、パソコンを再起動したりして、新しくターミナルを開き直したときは、環境を思い出すために以下のコマンドだけ毎回実行してください。


````
# LLaVAのフォルダに移動する
cd /workspace/LLaVA

# 作成した仮想環境を起動する（これをやらないとLLaVAが動かない）
source l_env/bin/activate

````
* 標準的な7Bモデルの実行コマンド
````
python -m llava.eval.run_llava \
    --model-path liuhaotian/llava-v1.5-7b \
    --image images/llava_logo.png \
    --query "What is unusual about this image?"
````
----
ここまでターミナル
* ここからはコード
````
import subprocess

def test_run():
    print("--- LLaVAのテスト呼び出しを開始します ---")
    
    # ターミナルで打っていたコマンドをそのまま再現
    cmd = [
        "python3", "-m", "llava.eval.run_llava",
        "--model-path", "liuhaotian/llava-v1.5-7b",
        "--image", "images/llava_logo.png",
        "--query", "What is unusual about this image?"
    ]
    
    # コマンドを実行して、ターミナルに表示される結果をそのまま画面に出力する
    subprocess.run(cmd)

if __name__ == "__main__":
    test_run()
````
上を実行時、ターミナルにて
````
python3 pipeline.py
````

----
> 6/25
* マルチモーダルAI 
GPT-4V
tsuzumi
**LLaVAに決定**

* graphRAG
LlamaIndex

---
>Llama(ラマ) 3.1 8B ins 

* 文字数（Maxtext）:128k(約10万〜15万文字,一般的な小説や新書で約1〜1.5冊分)

* 変圧器と一緒に使用してください
以降ではtransformers >= 4.43.0、Transformers のpipeline抽象化を使用するか、関数を使用して Auto クラスを活用することで、会話推論を実行できますgenerate()。

----

> RAG技術(要約する、外部記憶として使う)

トランスフォーマーのインストールを必ず更新してくださいpip install --upgrade transformers。

> ~~~~数式エディタの搭載
>* MathJax(JavaScriptプログラム)~~~~

> ~~~ベンゼン環の描画
>* RDKit~~~

> AIによる仮漫画化　（orネーム案の考案）
>* (Stable Diffusion XL(画像))　もしくは　Pony Diffusion V6(アニメや漫画風に特化) + LoRA(キャラの固定)

> タグ付けの自動化
>* Mistral 7B, (LIama 3.1 8B)

> 漫画を本投稿
>人間がやる

--------------------------
文章を受け入れられる画像生成AI探す
->文章とイラストをまとめる

Qwen(2b/7b)
対話の場合はInstructがいい
react->ユーザーインタフェースを簡単にJavaScriptでつくれる
RAGをつかうときにLangChain, Llamaindex

### AIメモ
- 画像生成AIの別候補について
* Anything v5（ベース：SD 1.5）パソコンのスペックを抑えつつ、手軽に綺麗な日本の「アニメ・マンガ風」イラストを生成したい場合の定番モデルです。メリット: 動作が非常に軽く、VRAMが少ないパソコン（8GB以下）でもサクサク動きます。一般的なプロンプトで、最初から綺麗な「アニメ塗り」のキャラクターが出力されます。デメリット: Ponyに比べると、複雑なポーズの指定や「持ち物」などの細かい指示が通りにくい傾向があります。

- RAGを、タスクに特化した、オープンモデルAIを用いてgoogle colabで使うには？
-----
>git hubにあげるときのコミット・プッシュ

`git add`
`git commit`
`git push`
