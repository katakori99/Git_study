
# GitとGitHubの勉強

- Git：作業ファイルの変更履歴を、自分のパソコン内で管理するためのシステム\
  → 変更履歴を保存できる\
  → 過去の状態に戻れる・いつ何を変えたか見られる\
  → **=バージョンを管理できる**
- GitHub：Gitの履歴をオンラインで管理するサービス\
  → 複数人で共同作業ができる\
  → branch（枝）を使えば作業を分担できて、衝突しにくくなる
- リポジトリ：GitやGitHubで管理するフォルダ

## 基本コマンドの説明

- `init`：Git管理をそのフォルダで開始する  
- `add`：変更を次のコミットに含める  
- `commit`：変更を履歴として記録する  
- `status`：変更されたファイルを確認  
- `diff`：変更前との差分を表示  
- `push`：ローカルの履歴をGitHubへ送信  
- `pull`：GitHubの変更をローカルに取り込む  
- `log`：コミット履歴を一覧表示  
- **同期**：`pull`と`push`の総称（双方向で更新すること）

## 簡単な方法

1. VSCodeでGithubにログイン
2. GitHubと連携したいフォルダを開く
3. 左端の上から3番目の，点3つのアイコンをクリック
4. 「GitHubに公開」をクリック
5. 完了

## ステップ 1：ローカルリポジトリの作成

1. プロジェクト用のフォルダを作成  
2. VSCodeでそのフォルダを開き、ターミナルを起動  
3. 以下を実行してGit管理を開始：

   ```bash
   git init
   ```

4. 全ファイルをステージング：

   ```bash
   git add .
   ```

5. 初回コミットを作成：

   ※ コメントは何でも良い

   ```bash
   git commit -m "初回コミット：プロジェクト開始"
   ```

6. `.gitignore` を作成し、コミット対象外とするファイルを記述する
   ※ 必要なもの以外は無視するように設定  
   例：`*.pyc`, `.DS_Store`, `__pycache__/` など

---

## ステップ 2：GitHubリポジトリとの連携

1. GitHub上で新しいリポジトリを作成  
   - 「＋」→「New repository」  
   - Repository name：任意の名前  
   - Visibility：Private（非公開）  
   - 「Initialize with README」は **チェックしない**

2. 以下のコマンドでローカルリポジトリと紐づけ：

   ```bash
   git remote add origin https://github.com/<ユーザの名前>/<リポジトリの名前>.git
   git branch -M main
   git push -u origin main
   ```

---

## ステップ 3：変更を反映する手順

1. **pull（任意）**  
   他人の変更を取り込む場合：

   ```bash
   git pull
   ```

2. **ステージング**  
   ファイルを次のコミット対象に追加：

   ```bash
   git add .
   ```

3. **コミット**  
   コメント付きで変更履歴に記録：

   ```bash
   git commit -m "変更内容の説明"
   ```

4. **push**  
   GitHubに反映：

   ```bash
   git push
   ```

---

## 同期とは

- `pull`：他の環境からの変更を取得  
- `push`：自分の変更を送信  
- **同期**：両者を行い、ローカルとGitHubを一致させる操作

---

## イメージ

```bash

(作業フォルダ作成)
        ↓
   git init（初期化）
        ↓
   git add .（追加）
        ↓
git commit -m "コメント"（履歴に記録）
        ↓
git remote add origin（紐づけ）
        ↓
git push -u origin main（初回送信）
        ↓
─────────────────────
 以降の通常の開発サイクル：
─────────────────────
        ↓
    git pull（他者の更新を取得）
        ↓
    作業・編集
        ↓
    git add .（変更をステージ）
        ↓
git commit -m "コメント"（履歴に記録）
        ↓
    git push（更新を送信）


```
