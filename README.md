# ダツイチ新大陸 S1 — ガントチャート

GitHub Pages で動くガントチャートアプリです。

## フォルダ構成

```
/
├── index.html       ← アプリ本体
├── data/
│   └── gantt.json   ← 共有データ（これをGitで管理）
└── README.md
```

---

## 初回セットアップ（GitHub Pages の有効化）

1. このリポジトリを GitHub に作成（または fork）
2. **Settings → Pages → Branch: `main` / folder: `/ (root)`** を選択して Save
3. 数分後に `https://<ユーザー名>.github.io/<リポジトリ名>/` で公開される

---

## 日々の使い方

### データを更新したいとき

1. ブラウザでアプリを開く（ページ読み込み時に `data/gantt.json` を自動取得）
2. タスクを編集・追加・完了マークなど操作する
3. ヘッダーの **「📤 エクスポート」** をクリック → `gantt.json` がダウンロードされる
4. ダウンロードした `gantt.json` をリポジトリの `data/` フォルダに上書きコピー
5. GitHub にコミット＆プッシュ

```bash
cp ~/Downloads/gantt.json ./data/gantt.json
git add data/gantt.json
git commit -m "ガントチャート更新 $(date '+%Y-%m-%d')"
git push
```

6. 他のメンバーがページをリロードすると最新データが反映される

---

## メンバーの役割

| 操作 | 誰でも？ |
|------|---------|
| 閲覧 | ✅ URLを知っていれば誰でも |
| 編集・エクスポート | ✅ ブラウザで操作するだけ |
| GitHubへのコミット | ⚠️ リポジトリの write 権限が必要 |

> **Tip:** 複数人が同時に編集してコミットすると競合する可能性があります。  
> 「編集担当」を決めるか、コミット前に `git pull` を忘れずに。

---

## ローカルで動かす場合

`fetch()` はローカルファイルでは動かないため、簡易サーバーを使ってください。

```bash
# Python 3
python3 -m http.server 8080
# → http://localhost:8080 で開く
```
