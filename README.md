# sns-auto-poster-workflows（Public）

SNS自動投稿システムの GitHub Actions ワークフロー置き場（Public リポジトリ）。

コード・設定・認証情報は [sns-auto-poster-core](https://github.com/aa-0921/sns-auto-poster-core)（Private）に集約し、
このリポジトリはワークフローファイルのみを管理する。

Public リポジトリの GitHub Actions は**実行時間が無制限・無料**。

## 必要なSecrets設定

このリポジトリの Settings > Secrets and variables > Actions に設定する:

| Secret名 | 内容 |
|---------|------|
| `PAT_CLASSIC` | Private repo（sns-auto-poster-core）にアクセスするための Classic PAT（`repo` スコープ） |

## ワークフロー一覧

| ファイル | トリガー | プラットフォーム |
|--------|---------|----------------|
| `bluesky.yml` | cron（週4回）+ 手動 | Bluesky |
| `instagram.yml` | cron（週1回）+ 手動 | Instagram |
| `qiita.yml` | 手動のみ | Qiita |

## PATの管理

- Expiration は 90日〜1年で設定（無期限PATはセキュリティリスク）
- 期限切れになるとワークフローが失敗する → カレンダーにリマインダーを設定
- Fine-grained token を使う場合は対象リポジトリを sns-auto-poster-core のみに限定

## セキュリティ注意事項

- このリポジトリは Public なので、ワークフローファイルは誰でも閲覧可能
- APIトークン・パスワードは **絶対にワークフローに直書きしない**（Secrets を使う）
- スクリプトのロジックは Private リポジトリに置く
