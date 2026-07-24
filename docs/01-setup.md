# 01. 環境セットアップ

[< 目次に戻る](../README.md) | [次へ: Fork と Clone >](02-fork-and-clone.md)

---

## この章でやること

- Git をインストールする
- Git の初期設定をする
- GitHub アカウントを確認する

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
