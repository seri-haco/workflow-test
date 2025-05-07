# Workflow Test

このリポジトリは、GitHub Actionsを使用してGitのコミットハッシュをAWS S3にアップロードするワークフローのテスト用リポジトリです。

## 機能

- GitHub Actionsのワークフローを使用して、コミットハッシュをS3バケットにテキストファイルとしてアップロード
- ワークフローは手動実行（workflow_dispatch）に対応

## 使用方法

### 前提条件

- AWSアカウントと適切な権限を持つIAMユーザー
- S3バケットの作成済み

### セットアップ

1. GitHubのリポジトリ設定で以下のSecretsを設定：

   - `AWS_ACCESS_KEY_ID`: AWSのアクセスキーID
   - `AWS_SECRET_ACCESS_KEY`: AWSのシークレットアクセスキー
   - `AWS_REGION`: AWSのリージョン（例：ap-northeast-1）
   - `S3_BUCKET`: アップロード先のS3バケット名

### ワークフローの実行

1. GitHubのActionsタブを開く
2. 「Upload Commit Hash to S3」ワークフローを選択
3. 「Run workflow」ボタンをクリック
4. ワークフローが完了すると、指定したS3バケットに`commit-hash.txt`ファイルが作成されます

## ワークフローの動作

1. リポジトリをチェックアウト
2. AWS認証情報を設定
3. 現在のコミットハッシュを`commit-hash.txt`ファイルに書き込み
4. ファイルをS3バケットにアップロード 