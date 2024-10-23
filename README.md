# プロジェクト名

## 開発環境のセットアップ

### 必要な環境
- Docker
- Docker Compose
- Git

### セットアップ手順

1. リポジトリのクローン
```bash
git clone [repository-url]
cd [project-name]
```

2. 環境変数ファイルの準備
```bash
cp .env.example .env
```

3. Dockerコンテナの起動
```bash
# イメージのビルド
docker compose build

# コンテナの起動
docker compose up -d
```

4. アプリケーションの確認
- ブラウザで http://localhost:5173 にアクセス

### 開発用コマンド

```bash
# コンテナのログを確認
docker compose logs -f frontend

# コンテナ内でコマンドを実行（例：パッケージのインストール）
docker compose exec frontend npm install [package-name]

# コンテナの停止
docker compose down

# コンテナの再起動
docker compose restart frontend
```

### ブランチ戦略

- `main`: プロダクション用のブランチ
- `develop`: 開発用のブランチ
- 機能追加時: `feature/機能名`
- バグ修正時: `fix/バグ内容`

### コミットメッセージの規約

以下の形式でコミットメッセージを書いてください：

- feat: 新機能
- fix: バグ修正
- docs: ドキュメントのみの変更
- style: コードの意味に影響しない変更（空白、フォーマット、等）
- refactor: バグ修正や機能追加を含まないコードの変更
- test: テストの追加・修正
- chore: ビルドプロセスやツールの変更、ライブラリの更新等

例：
```bash
feat: ユーザー認証機能の追加
fix: ログインフォームのバリデーションバグを修正
```