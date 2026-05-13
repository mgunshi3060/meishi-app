# 名刺管理アプリ セットアップ手順

## リポジトリ構成
```
/
├── index.html       ← アプリ本体
├── data/
│   └── cards.json   ← 名刺データ（追加・更新のたびに上書き）
└── images/
    └── img_{id}.jpg ← 名刺画像（id紐付け）
```

---

## 1. GitHubリポジトリ作成

1. GitHub にログイン
2. 右上「+」→「New repository」
3. 設定：
   - Repository name: `meishi-app`（任意）
   - **Private** を選択（個人情報保護のため）
   - 「Initialize this repository with a README」にチェック
4. 「Create repository」

---

## 2. ファイルをアップロード

### data/cards.json
1. リポジトリ画面で「Add file」→「Upload files」
2. `data/` フォルダを作るには、ファイル名欄に `data/cards.json` と入力
3. cards.json の内容を貼り付けて保存

### images/.gitkeep
1. 同様に `images/.gitkeep` を作成（空ファイルでOK）

### index.html
1. index.html をアップロード
2. CONFIG部分を書き換えてからアップロードすること：
   ```javascript
   GITHUB_USER  : 'あなたのGitHubユーザー名',
   GITHUB_REPO  : 'meishi-app',
   GITHUB_TOKEN : 'ghp_xxxxx（PATトークン）',
   APP_PASSWORD : '好きなパスワード',
   BRANCH       : 'main',
   ```

---

## 3. GitHub Pages を有効化

1. リポジトリ → 「Settings」タブ
2. 左メニュー「Pages」
3. Source: 「Deploy from a branch」
4. Branch: `main` / `/(root)`
5. 「Save」
6. 数分後に `https://ユーザー名.github.io/meishi-app/` でアクセス可能

---

## 4. Personal Access Token（PAT）発行

1. GitHub右上アイコン → Settings
2. 左下「Developer settings」
3. 「Personal access tokens」→「Tokens (classic)」
4. 「Generate new token (classic)」
5. 設定：
   - Note: `meishi-app`
   - Expiration: `No expiration`
   - Scope: `repo` にチェック（1個のみ）
6. 「Generate token」→ 表示されたトークンをコピー（**一度しか表示されない**）

---

## 5. 日常の使い方

### 名刺を追加する
1. アプリにアクセス → ログイン
2. 「名刺を追加」→ 画像アップ＋情報入力 → 保存
3. → 自動でGitHubのcards.jsonと images/ に保存される

### cards.jsonを手動で編集したい場合
1. 「エクスポート」ボタンでJSONをダウンロード
2. テキストエディタやExcelで編集
3. 「インポート」ボタンで読み込み → 自動でGitHubに反映

### 名刺画像を手動でアップしたい場合
1. GitHubリポジトリの `images/` フォルダを開く
2. 「Add file」→「Upload files」
3. ファイル名を `img_{cards.jsonのid}.jpg` に合わせる

---

## 注意事項

- **PATトークンは絶対にpublicリポジトリに入れないこと**
- リポジトリはPrivateで運用推奨
- XServerに移行する場合はPHPファイル1本追加でPATを隠せる（別途対応）
