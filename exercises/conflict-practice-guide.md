# コンフリクト解消の練習

## この演習の目的

実際にコンフリクトを発生させて、自分の手で解消する体験をします。

---

## 練習の流れ

### 準備（2人1組でやります）

Aさん・Bさんの2人で `conflict-practice.md` を **同じ行** を別々に編集します。

### Aさんの作業

1. ブランチを作る
   ```bash
   git checkout -b conflict-practice-a
   ```

2. `exercises/conflict-practice.md` を編集する
   ```
   変更前: 1. Python
   変更後: 1. TypeScript
   ```

3. コミット & プッシュ
   ```bash
   git add exercises/conflict-practice.md
   git commit -m "update: ランキング1位をTypeScriptに変更"
   git push origin conflict-practice-a
   ```

4. Pull Request を作成する

### Bさんの作業（Aさんの PR がマージされた後）

1. main を最新にする
   ```bash
   git checkout main
   git pull origin main
   ```

2. ブランチを作る
   ```bash
   git checkout -b conflict-practice-b
   ```

3. **同じ行** を別の内容に編集する
   ```
   変更前: 1. Python（※ Aさんの変更がマージ済みなら 1. TypeScript）
   変更後: 1. Go
   ```

4. コミット & プッシュ → PR を作成

### コンフリクトが発生！

Bさんの PR には「This branch has conflicts」と表示されます。

---

## コンフリクトの解消手順

### 1. 最新の main を取り込む

```bash
git checkout conflict-practice-b
git pull origin main
```

以下のようなメッセージが出ます:

```
Auto-merging exercises/conflict-practice.md
CONFLICT (content): Merge conflict in exercises/conflict-practice.md
Automatic merge failed; fix conflicts and then commit the result.
```

### 2. ファイルを開いて確認する

```
<<<<<<< HEAD
1. Go
=======
1. TypeScript
>>>>>>> main
```

### 3. 最終的に残したい内容に書き換える

例: 両方残す場合

```
1. TypeScript
2. Go
```

`<<<<<<<` `=======` `>>>>>>>` の行は **すべて削除** してください。

### 4. 解消をコミットする

```bash
git add exercises/conflict-practice.md
git commit -m "fix: コンフリクトを解消（両方のランキングを反映）"
git push origin conflict-practice-b
```

PR を確認すると、コンフリクトが解消されています。

---

## やってみよう

1. ペアを組む
2. 上の手順で実際にコンフリクトを起こす
3. 自分の手で解消する

焦らず、ゆっくりやれば大丈夫です。
