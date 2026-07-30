# aiPicasso用仮想環境構築

````
# 1. テスト用のフォルダを作成して移動
mkdir picasso_test_env && cd picasso_test_env

# 2. 仮想環境を作成（"test_venv" という名前の仮想環境を作成）
python3 -m venv test_venv

# 3. 仮想環境を有効化（有効化するとターミナルの先頭に (test_venv) と表示されます）
# Linux / macOS の場合:
source test_venv/bin/activate

# 4. この中でライブラリのインストールやエラーの検証を行う
pip install --upgrade pip
pip install torch diffusers transformers
````
仮想環境を抜けたい時: deactivate と入力するだけです。

環境をやり直したい/消したい時: 作成した my_test_env フォルダをそのまま削除すればOKです。

# プロンプトと画像
````
prompt = "monochrome, grayscale, people"
````
![](https://g0v.hackmd.io/_uploads/S1uOEDuBMx.png)

----
````
prompt = "monochrome, grayscale, people"
````
![](https://g0v.hackmd.io/_uploads/S1xKkSv_HMe.png)


# 吹き出しをつけたいときのコマンド
````
positive: 1girl with the speech bubble saying "Happy Holidays!", upper body, sivler short hair, blue eyes, warm wear, outdoor, snow
negative: photo
````