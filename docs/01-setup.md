# 01. 環境セットアップ

[< 目次に戻る](../README.md) | [次へ: Fork と Clone >](02-fork-and-clone.md)

---

## この章でやること

- VS Code をインストールして、ターミナルを開けるようにする
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

## 1. VS Code を用意する

このガイドでは、エディタとして **VS Code（Visual Studio Code）** を使う前提で進めます。
コードを書くのも、ターミナルでコマンドを打つのも、VS Code の中だけで完結できて楽だからです。

1. [https://code.visualstudio.com/](https://code.visualstudio.com/) にアクセス
2. **「Download」** ボタンから自分の OS 版をダウンロード
3. ダウンロードしたファイルを開いてインストール
   - **macOS**: 解凍された `Visual Studio Code` を **「アプリケーション」フォルダにドラッグ**
   - **Windows**: インストーラーを実行し、デフォルト設定のまま進める

### VS Code のターミナルの開き方

VS Code を起動して、以下のショートカットでターミナルが開きます:

| OS | ショートカット |
|----|--------------|
| macOS | `Control` + `Shift` + `` ` `` |
| Windows | `Ctrl` + `Shift` + `` ` `` |

> メニューから開く場合は **「表示（View）」→「ターミナル（Terminal）」** です。
> **これ以降のコマンドは、すべてこの VS Code のターミナルに打ち込みます。**

---

## 2. Git のインストール

> **注意**: VS Code をインストールしても Git は入りません。
> VS Code は「Git を操作する画面」であって、Git 本体は別途インストールが必要です。

### macOS の場合

**方法A: 公式インストーラーを使う（おすすめ・確実）**

1. [https://git-scm.com/download/mac](https://git-scm.com/download/mac) にアクセス
2. **「Binary installer」** のリンクからインストーラーをダウンロード
3. ダウンロードした `.pkg` ファイルを開いて、案内どおりに進める

**方法B: Homebrew を使う（Homebrew を入れている人向け）**

VS Code のターミナルで以下を実行:

```bash
brew install git
```

> Homebrew を使ったことがなければ、方法A を選んでください。
> どちらの方法でも、入る Git は同じものです。

### Windows の場合

1. [https://git-scm.com/](https://git-scm.com/) にアクセス
2. **「Download for Windows」** をクリック
3. ダウンロードしたインストーラーを実行
4. 基本的にすべて **デフォルト設定のまま「Next」** で進めて OK

### インストール確認

**VS Code のターミナル** で以下を実行:

```bash
git --version
```

バージョンが表示されれば OK です:

```
git version 2.xx.x
```

> **うまくいかない場合**: VS Code を一度完全に終了して、開き直してからもう一度試してください。
> インストール直後は、VS Code がまだ Git の場所を認識できていないことがあります。

---

## 3. Git の初期設定

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

## 4. GitHub アカウントの確認

[https://github.com/](https://github.com/) にログインできることを確認してください。

アカウントがまだない場合は、新規登録してください。

---

## チェックポイント

以下がすべてできていれば、この章は完了です:

- [ ] VS Code が起動して、ターミナルを開ける
- [ ] `git --version` でバージョンが表示される
- [ ] `git config --global --list` で名前とメールが表示される
- [ ] GitHub にログインできる

---

[< 目次に戻る](../README.md) | [次へ: Fork と Clone >](02-fork-and-clone.md)
