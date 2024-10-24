# Character Game - Frontend

## 開発環境セットアップ

### 必要な環境
- Docker
- Docker Compose
- Git

### 初回セットアップ手順

1. リポジトリのクローン
```bash
# リポジトリをクローン（mainブランチ）
git clone [repository-url]
cd [project-name]

# フロントエンド開発用のブランチ情報を取得
git fetch origin
git checkout -b front/develop origin/front/develop
```

2. 依存パッケージのインストール

```bash
# frontディレクトリに移動
cd front

# パッケージのインストール（IDE用）
npm install

# プロジェクトルートに戻る
cd ..
```

3. 環境変数ファイルの準備
```bash
cp .env.example .env
```

4. Dockerコンテナの起動
```bash
# イメージのビルド
docker compose build

# コンテナの起動
docker compose up -d
```

5. アプリケーションの確認
- ブラウザで http://localhost:5173 にアクセス

### 開発用コマンド

```bash
# コンテナのログを確認
docker compose logs -f front

# コンテナ内でコマンドを実行（例：パッケージのインストール）
docker compose exec front npm install [package-name]

# コンテナの停止
docker compose down

# コンテナの再起動
docker compose restart front
```

## 開発フロー

### ブランチ戦略

```
front/develop
    ├── front/feature/***  # 機能追加
    ├── front/fix/***      # バグ修正
    ├── front/refactor/*** # リファクタリング
    └── front/docs/***     # ドキュメント更新
```

### 新機能の開発手順

1. front/developブランチの最新情報を取得
```bash
git checkout front/develop
git pull origin front/develop
```

2. 新しい機能ブランチを作成
```bash
git checkout -b front/feature/[機能名]
```

3. 開発作業

4. 変更をコミット
```bash
git add .
git commit -m "feat: 機能の説明"
```

5. 変更をプッシュ
```bash
git push -u origin front/feature/[機能名]
```

6. プルリクエストの作成
- front/feature/[機能名] → front/develop 宛にプルリクエストを作成

### コミットメッセージの規約

プレフィックス:
- `feat:` 新機能
- `fix:` バグ修正
- `docs:` ドキュメントのみの変更
- `style:` コードの意味に影響しない変更（空白、フォーマット等）
- `refactor:` バグ修正や機能追加を含まないコードの変更
- `test:` テスト関連の追加・修正
- `chore:` ビルドプロセスやツールの変更、ライブラリの更新等

例：
```bash
feat: ユーザー認証フォームの追加
fix: ログインボタンのスタイル修正
```

## プロジェクト構成

```
project-root/
├── docker/
│   └── front/
│       └── Dockerfile
├── front/
│   ├── src/
│   ├── package.json
│   └── vite.config.ts
├── docker-compose.yml
├── .env.example
└── README.md （このファイル）
```

## その他

### VS Code 推奨設定

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

### トラブルシューティング

1. ブランチの確認
```bash
# 現在のブランチを確認
git branch

# リモートブランチも含めて確認
git branch -a
```

2. コンテナが起動しない場合
```bash
# ログを確認
docker compose logs front

# コンテナを再構築
docker compose down
docker compose build --no-cache
docker compose up -d
```

3. ホットリロードが効かない場合
```bash
# コンテナを再起動
docker compose restart front
```

### 注意事項
- 直接front/developにプッシュしないでください
- プルリクエストは必ずレビューを受けてからマージしてください
- 環境変数を追加した場合は.env.exampleも更新してください