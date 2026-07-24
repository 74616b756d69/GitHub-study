# 10. 認証の設定（PAT / SSH）

[< 前へ: よく使うコマンド集](09-cheatsheet.md) | [目次](../README.md) | [次へ: 困ったときは（トラブル集） >](11-troubleshooting.md)

---

## この章でやること

- なぜ push でパスワードが使えないのかを理解する
- Personal Access Token（PAT）を発行する
- SSH キーで認証する（上級者向け・任意）

---

## なぜ認証でつまずくの？

`git push` や `git clone`（プライベートリポジトリ）をするとき、GitHub は
「本当にあなた本人ですか？」を確認します。これが **認証** です。

ここで多くの初心者がつまずきます。理由はシンプルで、

> **GitHub は 2021 年から、パスワードでの push を廃止しました。**

つまり、GitHub のログインパスワードをそのまま入力しても弾かれます。
代わりに次のどちらかを使います。

| 方法 | 難易度 | おすすめ |
|------|--------|----------|
| **PAT（Personal Access Token）** | ★☆☆ かんたん | 初心者はこちら |
| **SSH キー** | ★★☆ 少し手間 | 慣れてきたら |

---

## 方法A: PAT（Personal Access Token）を使う 🔰

PAT は「パスワードの代わりに使う、使い捨ての長い文字列」です。
HTTPS で clone / push している人はこちらが一番かんたんです。

### 1. トークンを発行する

1. GitHub にログインした状態で [https://github.com/settings/tokens](https://github.com/settings/tokens) にアクセス
2. **「Generate new token」→「Generate new token (classic)」** をクリック
3. 以下を設定:
   - **Note**: `github-studie`（自分が分かる名前でOK）
   - **Expiration**: `30 days` など（学習用なら短めで十分）
   - **Select scopes**: **`repo`** にチェック（これだけで push できます）
4. 一番下の **「Generate token」** をクリック

> ⚠️ **超重要**: 表示されたトークン（`ghp_xxxx...`）は **この画面を離れると二度と見られません**。
> 必ずこの場でコピーしてメモ帳などに一時保存してください。

### 2. push のときにトークンを入力する

push すると、ユーザー名とパスワードを聞かれます:

```
Username: あなたのGitHubユーザー名
Password: ← ここに【パスワードではなく PAT】を貼り付ける
```

> 💡 貼り付けても画面には何も表示されませんが、正しく入力されています。
> そのまま Enter を押してください。

### 3. 毎回入力しなくて済むようにする（任意）

毎回トークンを貼るのは面倒なので、一度入力したら記憶させることができます。

**macOS:**
```bash
git config --global credential.helper osxkeychain
```

**Windows（Git for Windows）:**
```bash
git config --global credential.helper manager
```

これで次回以降、一度入力したトークンを OS が覚えてくれます。

---

## 方法B: SSH キーを使う（任意・慣れてきたら）

SSH は「自分専用の鍵（キー）」を作って GitHub に登録する方法です。
一度設定すればトークンの入力が一切不要になります。

### 1. すでに鍵があるか確認

```bash
ls -al ~/.ssh
```

`id_ed25519.pub` があれば「2. 鍵を作る」は飛ばして構いません。

### 2. 鍵を作る

```bash
ssh-keygen -t ed25519 -C "あなたのメールアドレス"
```

- 保存場所を聞かれたら **そのまま Enter**（デフォルトでOK）
- パスフレーズは空でも設定してもOK（空なら Enter を2回）

### 3. 公開鍵をコピーする

**macOS:**
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

**Windows（Git Bash）:**
```bash
cat ~/.ssh/id_ed25519.pub | clip
```

### 4. GitHub に登録する

1. [https://github.com/settings/keys](https://github.com/settings/keys) にアクセス
2. **「New SSH key」** をクリック
3. **Title** は自分のPC名など、**Key** に先ほどコピーした内容を貼り付け
4. **「Add SSH key」** をクリック

### 5. 接続テスト

```bash
ssh -T git@github.com
```

`Hi あなたの名前! You've successfully authenticated...` と出れば成功です。

### 6. リモートURLを SSH に切り替える

HTTPS で clone 済みの場合は、SSH に切り替えます:

```bash
git remote set-url origin git@github.com:あなたの名前/GitHub-Studie.git
```

---

## HTTPS と SSH、どっちを使えばいい？

| | HTTPS + PAT | SSH |
|---|---|---|
| 設定のかんたんさ | ◎ すぐ使える | △ 少し準備が必要 |
| 毎回の入力 | 記憶させれば不要 | 不要 |
| おすすめの人 | **これから始める人** | 複数PC・頻繁に使う人 |

> **迷ったら HTTPS + PAT でOK。** まずは push できることを体験しましょう。

---

## チェックポイント

- [ ] `git push` で認証が通り、GitHub にアップできた
- [ ] （PATの人）トークンを OS に記憶させた、または安全に保管した
- [ ] （SSHの人）`ssh -T git@github.com` で成功メッセージが出た

---

[< 前へ: よく使うコマンド集](09-cheatsheet.md) | [目次](../README.md) | [次へ: 困ったときは（トラブル集） >](11-troubleshooting.md)
