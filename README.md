# PBL Application

## 実行方法

仮想環境を作成していない場合は以下のコマンドで作成

```
python3 -m venv ./venv
```

以下のコマンドで仮想環境に入る。作業する時は常に仮想環境に入ること。

```sh
source ./venv/bin/activate  # 仮想環境に入る
```

仮想環境に入ったら最初は必要なパッケージをインストールする。(以降は不要)

```
pip install -r requirements.txt
```

パッケージがインストールできたら以下のコマンドで実行できる。

```
./run.sh
```

## 設計

3層アーキテクチャを雰囲気だけ採用する。

### プレゼンテーション層

`server.py` `templates/`

Webサーバーの入出力を担当する層。

#### 流れ

1. リクエストを受け取る
1. リクエストを元にアプリケーション層の関数を呼び、情報を取得・更新する
1. 取得した情報を元にレスポンスを作成して送信する

### モデル層

`model/`

プレゼンテーション層とアプリケーション層間でデータのやり取りをするために使用。

### アプリケーション層

`application/`

アプリケーションのメイン処理を担当する層。

#### 流れ

1. プレゼンテーション層から呼び出される
1. DBから情報を取得したり更新する
1. 必要なら結果を返す

### データ層

データを扱う層。実際にクエリを発行する処理をコードに切り分けてデータ層と言ったりもするが、今回は単にデータベースが担当する。

- データベースそのまま

