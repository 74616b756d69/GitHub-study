# 主催者セットアップ手順

このファイルはイベント前に主催者が実行する手順です。
参加者には見せません。セットアップ完了後に削除してください。

---

## 1. main ブランチをプッシュ

```bash
git add .
git commit -m "初期セットアップ: GitHub ハンズオンガイド"
git push origin main
```

---

## 2. サンプル PR（良い例）を作成

```bash
# main から良い例ブランチを作成
git checkout -b example/good-pr

# 佐藤花子のファイルだけをこのブランチに残すため、一度削除して再追加
# （main に既に含まれているので、ブランチ上で差分を作る）
git checkout main -- exercises/participants/sato-hanako.md 2>/dev/null
git add exercises/participants/sato-hanako.md
git commit -m "add: 自己紹介カード（佐藤花子）"
git push origin example/good-pr
```

GitHub で PR を作成:

```bash
gh pr create \
  --base main \
  --head example/good-pr \
  --title "add: 自己紹介カード（佐藤花子）" \
  --body "$(cat <<'EOF'
## 変更内容

自己紹介カードを追加しました。
- ファイル: `exercises/participants/sato-hanako.md`
- 名前、自己紹介、好きな技術、ひとことを記載

## 変更の理由

ハンズオン演習として自己紹介カードを作成しました。

## 確認したこと

- [x] ファイル名が正しい（`exercises/participants/sato-hanako.md`）
- [x] Markdown の表示が崩れていないことを確認した
- [x] 他の人のファイルを変更していない
- [x] 個人情報（電話番号・住所など）を含めていない

---
**これはサンプル PR です。PR の書き方の参考にしてください。**
EOF
)" \
  --draft \
  --label "サンプル（マージしないで）"
```

### レビューコメントを追加

PR のページを開いて、以下のコメントを手動で追加してください:

**PR 全体へのコメント:**
> 自己紹介カードの追加ありがとうございます！
> 内容もしっかり書かれていて、とても良い PR ですね。
> 
> - 変更内容・理由・確認事項がしっかり書かれている
> - ファイル名も正しい
> - 他のファイルに影響がない
> 
> LGTM（Looks Good To Me）！ 👍

---

## 3. サンプル PR（改善が必要な例）を作成

```bash
git checkout main
git checkout -b example/needs-improvement

git checkout main -- exercises/participants/suzuki-ken.md 2>/dev/null
git add exercises/participants/suzuki-ken.md
git commit -m "追加"
git push origin example/needs-improvement
```

GitHub で PR を作成:

```bash
gh pr create \
  --base main \
  --head example/needs-improvement \
  --title "追加" \
  --body "$(cat <<'EOF'
追加しました。
よろしくお願いします。

---
**これはサンプル PR です。「改善が必要な PR」の例として参考にしてください。**
EOF
)" \
  --draft \
  --label "サンプル（マージしないで）"
```

### レビューコメント（修正依頼）を追加

PR のページを開いて、以下のコメントを手動で追加してください:

**PR 全体へのコメント:**
> レビューさせていただきました！いくつか気になる点があります。
> 
> **PR について:**
> - タイトルが「追加」だけだと、何を追加したのかわかりません
>   → `add: 自己紹介カード（鈴木健）` のようにしましょう
> - 変更内容・理由・確認事項を書きましょう（テンプレートを参考にしてください）
> 
> **ファイルの内容について:**
> - 自己紹介をもう少し書いてみましょう（どんな仕事をしているか、など）
> - 好きな技術も具体的に書くと、共通点のあるメンバーと話が広がりますよ
> - ひとことも、もう一言あると嬉しいです
> 
> 修正をお願いします！

**Files changed で `suzuki-ken.md` の特定行にコメント:**

`- プログラミング` の行に:
> ここをもう少し具体的に書いてみましょう！
> 例: `- Python（データ分析に使っています）`
> 例: `- React（個人開発で勉強中）`

---

## 4. ラベルを作成

```bash
gh label create "サンプル（マージしないで）" --color "d93f0b" --description "主催者が用意したサンプル PR。マージしないでください"
```

---

## 5. main に戻る

```bash
git checkout main
```

---

## 6. セットアップ完了後

- この `SETUP.md` を削除するか `.gitignore` に追加
- PR が2つ（Draft 状態）で表示されていることを確認
- 参加者に「Pull requests タブにサンプルがあるので見てみてください」と案内

---

## サンプル PR の構成

| PR | タイトル | 目的 |
|----|---------|------|
| 良い例 | `add: 自己紹介カード（佐藤花子）` | PRの書き方・レビューの良い例を見せる |
| 改善が必要な例 | `追加` | よくある悪い例と、具体的な指摘の仕方を見せる |

どちらも **Draft PR** にしているのでマージボタンが押せません。
参加者が誤ってマージする心配はありません。
