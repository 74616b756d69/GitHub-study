# 04. ファイルを編集する

[< 前へ: ブランチを切る](03-branch.md) | [目次](../README.md) | [次へ: Commit と Push >](05-commit-and-push.md)

---

## この章でやること

- 自己紹介カードのファイルを作成する
- Markdown の基本的な書き方を覚える
- 変更の状態を確認する

---

## 1. 自分のブランチにいることを確認

まず、正しいブランチにいることを確認しましょう:

```bash
git branch
```

`*` が `feature/add-自分の名前` についていますか？
ついていない場合は切り替えます:

```bash
git checkout feature/add-自分の名前
```

---

## 2. 自己紹介カードを作成する

`exercises/participants/` フォルダに、自分のファイルを作ります。

### テキストエディタで作成する場合

好きなエディタ（VS Code、メモ帳など）で新しいファイルを作成してください。

**ファイルの場所**: `exercises/participants/自分の名前.md`

**例**: `exercises/participants/taro-yamada.md`

### ターミナルから作成する場合

```bash
# エディタで新しいファイルを作成して開く（VS Code の場合）
code exercises/participants/taro-yamada.md
```

---

## 3. 自己紹介を書く

以下のテンプレートをコピーして、自分の情報に書き換えてください:

```markdown
# あなたの名前

## 自己紹介
ここに自己紹介を書いてください。
例: 「はじめまして！○○です。△△部署で働いています。」

## 好きな技術・興味のある分野
- 例: Python
- 例: Web 開発
- 例: データ分析

## ひとこと
ここに一言メッセージを書いてください。
```

### 完成例

[サンプルカード](../exercises/participants/example-taro.md) も参考にしてください。

---

## Markdown ミニガイド

今書いている `.md` ファイルは **Markdown** という形式です。
GitHub 上では見やすく整形されて表示されます。

| 書き方 | 表示 |
|--------|------|
| `# 見出し1` | 大きな見出し |
| `## 見出し2` | 中くらいの見出し |
| `**太字**` | **太字** |
| `- リスト項目` | リスト |
| `` `コード` `` | `コード` |

---

## 4. 変更の状態を確認する

ファイルを保存したら、Git がどう認識しているか確認しましょう:

```bash
git status
```

以下のように表示されます:

```
On branch feature/add-taro-yamada
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        exercises/participants/taro-yamada.md

nothing added to commit but untracked files present
```

**Untracked files** = Git がまだ追跡していない新しいファイル、という意味です。

次の章で、このファイルを Git に登録（コミット）します。

---

## チェックポイント

- [ ] `exercises/participants/自分の名前.md` ファイルを作成した
- [ ] 自己紹介の内容を書いた
- [ ] `git status` で自分のファイルが Untracked files として表示されている

---

[< 前へ: ブランチを切る](03-branch.md) | [目次](../README.md) | [次へ: Commit と Push >](05-commit-and-push.md)
