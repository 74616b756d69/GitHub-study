# 11. 困ったときは（トラブル集）

[< 前へ: 認証の設定](10-authentication.md) | [目次](../README.md)

---

## この章について

作業中によく出るエラーと、その対処法をまとめました。
**エラーメッセージは「怒られている」のではなく「次にやることのヒント」** です。
落ち着いて、まずは `git status` を実行しましょう。

> 💡 **最強のコマンド**: `git status`
> 「今どういう状態か」「次に何をすべきか」を Git 自身が教えてくれます。迷ったらまずこれ。

---

## 認証・push まわり

### `Updates were rejected` / `failed to push some refs`

**意味**: GitHub 側に、自分の手元にない変更があります。

**対処**: 先に取り込んでから push します。

```bash
git pull origin ブランチ名
git push origin ブランチ名
```

> それでもコンフリクトが出たら → [08. コンフリクトの解消](08-conflict.md)

---

### `Permission denied (publickey)` / パスワードが弾かれる

**意味**: 認証に失敗しています。GitHub はパスワードでの push を廃止しています。

**対処**: PAT か SSH を設定してください。→ [10. 認証の設定](10-authentication.md)

---

### `remote: Support for password authentication was removed`

**意味**: 上と同じく、ログインパスワードは使えません。

**対処**: パスワードの代わりに **PAT** を入力します。→ [10. 認証の設定](10-authentication.md)

---

## 設定まわり

### `Please tell me who you are`

**意味**: コミットする人の名前・メールが未設定です。

**対処**:

```bash
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

→ 詳しくは [01. 環境セットアップ](01-setup.md)

---

### `fatal: not a git repository`

**意味**: Git リポジトリの外にいます。

**対処**: `cd` でリポジトリのフォルダに移動します。

```bash
cd GitHub-Studie
```

---

## 「やっちゃった」ときのリカバリー

### mainブランチで作業してしまった

まだコミットしていなければ、変更を持ったままブランチを作れます:

```bash
git checkout -b feature/add-自分の名前
```

これで今の変更ごと新しいブランチに移動できます。安心してください。

---

### コミットメッセージを間違えた（まだ push していない）

直前のコミットメッセージを書き直せます:

```bash
git commit --amend -m "正しいメッセージ"
```

> ⚠️ すでに push 済みの場合は履歴が変わるため、共同作業中はチームに相談を。

---

### 変更を全部なかったことにしたい（未コミット）

```bash
# 特定のファイルだけ元に戻す
git restore ファイル名

# ステージングだけ取り消す（変更は残る）
git restore --staged ファイル名
```

---

### 直前のコミットを取り消したい（変更は残す）

```bash
git reset --soft HEAD^
```

コミットだけ取り消され、編集内容はそのまま残ります。

---

### 作業を一時中断したい（別の作業に切り替えたい）

```bash
git stash        # 今の変更を退避
# ...別の作業...
git stash pop    # 退避した変更を戻す
```

---

## フォークが古くなったとき（upstream 同期）

演習で他の人の PR がマージされると、**元のリポジトリ**が進み、
自分のフォークが古くなります。最新に追いつく方法です。

### 1. 元のリポジトリを upstream として登録（初回だけ）

```bash
git remote add upstream https://github.com/【元のオーナー】/GitHub-Studie.git
```

確認:

```bash
git remote -v
```

`origin`（自分のフォーク）と `upstream`（元のリポジトリ）が両方見えればOK。

### 2. 最新を取り込む

```bash
git checkout main
git fetch upstream
git merge upstream/main
```

### 3. 自分のフォークにも反映

```bash
git push origin main
```

> これで自分のフォークが元のリポジトリと同じ最新状態になります。

---

## それでも解決しないときは

1. **エラーメッセージ全文をそのままコピー** して読む（英語でも大事なヒントがあります）
2. `git status` の出力を見る
3. チームメンバーに **「何をしたら」「何が出たか」をセットで** 聞く
4. [GitHub 公式ドキュメント（日本語）](https://docs.github.com/ja)

> エラーは誰でも出します。詰まること自体が学びです。焦らず一つずつ。

---

[< 前へ: 認証の設定](10-authentication.md) | [目次](../README.md)
