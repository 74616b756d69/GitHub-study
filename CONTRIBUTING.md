# コントリビューションガイド

このリポジトリへの貢献方法を説明します。

## 参加の流れ

### 1. Fork する

このリポジトリのページ右上にある **Fork** ボタンをクリックします。

### 2. Clone する

```bash
git clone https://github.com/あなたのユーザー名/GitHub-Studie.git
cd GitHub-Studie
```

### 3. ブランチを作る

```bash
git checkout -b feature/add-あなたの名前
```

### 4. 自己紹介カードを作る

`exercises/participants/` フォルダに、自分のカードを作成してください。

ファイル名: `あなたの名前.md`

テンプレート:

```markdown
# あなたの名前

## 自己紹介
ここに自己紹介を書いてください。

## 好きな技術・興味のある分野
- 例: Python
- 例: Web 開発

## ひとこと
ここに一言メッセージを書いてください。
```

### 5. Commit & Push

```bash
git add exercises/participants/あなたの名前.md
git commit -m "add: 自己紹介カード（あなたの名前）"
git push origin feature/add-あなたの名前
```

### 6. Pull Request を作成

GitHub 上で Pull Request を作成してください。

## コミットメッセージの書き方

```
種類: 変更内容の要約

例:
add: 自己紹介カード（田中太郎）
fix: READMEの誤字を修正
update: プロフィール情報を更新
```

## 注意事項

- 他の人のファイルは編集しないでください
- 個人情報（電話番号・住所など）は書かないでください
- 困ったらチームメンバーに気軽に聞いてください
