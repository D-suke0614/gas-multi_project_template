# GAS-Multi_project_Template

同一リポジトリで複数のGASプロジェクトを管理するためのテンプレート

mainブランチにマージされると、CI上で `clasp push` が行われてGAS上に自動で反映される

```bash
# ディレクトリ構成
.
|––Project1 # GASプロジェクト
|   |–– .clasp.json # 対象のGAS IDを管理
|   |__src
|       |––appscript.json # GASのライブラリや設定を管理
|       |__index.js # ソースコード（任意のファイル名でOK）
|__Project2
    |–– .clasp.json
    |__src
        |––appscript.json
        |__index.js

```

## Setup

1. clone this repository
2. add clasp

```terminal
npm install -g @google/clasp
```

3. Repository secretsに`CLASP_TOKEN`を設定

`clasp login`を実行すると、`/home/{username}/.clasprc.json`が生成されるので、中身を取得する

取得した値をリポジトリ内のRepository secretsに`CLASP_TOKEN`という名前で保存する

```terminal
clasp login
cat /home/{username}/.clasprc.json
```

## 新規GASの作成手順

1. 新規ディレクトリを作成し、ディレクトリ構成通りにファイルを追加
2. `.clasp.json`にGASのIDを追加
3. `index.js`上でGASのコードを追加

## 既存GASのリポジトリへの追加手順

1. 既存のGASを追加するための、新規ディレクトリを作成
2. `cd ./[作成したディレクトリ名]`
3. `clasp clone [GAS ID] --rootDir ./src`
4. 必要に応じてディレクトリ構成にあうように、ファイルを動かす
