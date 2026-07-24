# 01. 環境セットアップ

[< 目次に戻る](../README.md) | [次へ: Fork と Clone >](02-fork-and-clone.md)

---

## この章でやること

- Git をインストールする
- Git の初期設定をする
- GitHub アカウントを確認する

---

## Git って何をしてくれるの？

Git はファイルの変更履歴を記録してくれるツールです。

普通にファイルを保存すると「今の状態」しか残りませんが、Git を使うと **コミットするたびにフォルダ全体の状態をまるごと記録** してくれます。差分（変更した部分）だけでなくフォルダ全体を記録しているので、いつでも過去の状態に完全に戻すことができます。

<p align="center">
  <img src="../images/git-snapshot.svg" alt="Git のスナップショットの仕組み" width="700">
</p>

> **たとえば**: コードを書き換えてバグが出てしまったとき、`git restore` で前の状態に戻せます。
> 「あのときの状態に戻したい！」が何度でもできるのが Git の強みです。

---

## 1. Git のインストール

### Windows の場合

1. [https://git-scm.com/](https://git-scm.com/) にアクセス
2. **「Download for Windows」** をクリック
3. ダウンロードしたインストーラーを実行
4. 基本的にすべて **デフォルト設定のまま「Next」** で進めて OK

### macOS の場合

ターミナルを開いて以下を実行:

```bash
xcode-select --install
```

ポップアップが出たら「インストール」をクリックしてください。

### インストール確認

ターミナル（Windows の場合は Git Bash）を開いて、以下を実行:

```bash
git --version
```

バージョンが表示されれば OK です:

```
git version 2.xx.x
```

> **うまくいかない場合**: ターミナルを一度閉じて開き直してからもう一度試してください。

---

## 2. Git の初期設定

Git に自分の名前とメールアドレスを登録します。
これはコミット（変更の記録）に「誰が変更したか」を残すためです。

```bash
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

**例:**

```bash
git config --global user.name "Taro Yamada"
git config --global user.email "taro@example.com"
```

### 設定の確認

```bash
git config --global --list
```

`user.name` と `user.email` が表示されれば OK です。

---

## 3. GitHub アカウントの確認

[https://github.com/](https://github.com/) にログインできることを確認してください。

アカウントがまだない場合は、新規登録してください。

---

## チェックポイント

以下がすべてできていれば、この章は完了です:

- [ ] `git --version` でバージョンが表示される
- [ ] `git config --global --list` で名前とメールが表示される
- [ ] GitHub にログインできる

---

[< 目次に戻る](../README.md) | [次へ: Fork と Clone >](02-fork-and-clone.md)
