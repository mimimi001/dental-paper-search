# GitHub Pagesデプロイ手順

このドキュメントでは、歯科系ガイドライン・論文検索アプリをGitHub Pagesにデプロイする詳細な手順を説明します。

## 前提条件

- GitHubアカウントを持っていること
- 基本的なGitの知識があること（なくても手順に従えば可能です）

## 手順1: GitHubリポジトリの作成

1. [GitHub](https://github.com/)にログインします
2. 右上の「+」アイコンをクリックし、「New repository」を選択します
3. リポジトリ名を入力します（例: `dental-paper-search`）
4. 説明（Description）を任意で入力します（例: 「歯科系ガイドライン・論文検索アプリ」）
5. リポジトリの可視性を選択します（Public推奨）
6. 「Add a README file」のチェックを外します（すでに用意しているため）
7. 「Create repository」ボタンをクリックします

## 手順2: ファイルのアップロード

### GitHubウェブインターフェースを使用する場合:

1. 作成したリポジトリページで「Add file」→「Upload files」をクリックします
2. 以下のファイルをドラッグ＆ドロップまたは選択してアップロードします:
   - `index.html`
   - `README.md`
   - `LICENSE`
3. 「Commit changes」ボタンをクリックします

### Gitコマンドを使用する場合:

```bash
# リポジトリをクローン
git clone https://github.com/あなたのユーザー名/リポジトリ名.git
cd リポジトリ名

# ファイルをコピー
cp /path/to/index.html .
cp /path/to/README.md .
cp /path/to/LICENSE .

# 変更をコミット
git add .
git commit -m "Initial commit"

# GitHubにプッシュ
git push origin main
```

## 手順3: GitHub Pagesの有効化

1. リポジトリページで「Settings」タブをクリックします
2. 左側のメニューから「Pages」を選択します
3. 「Source」セクションで「Deploy from a branch」を選択します
4. 「Branch」ドロップダウンから「main」を選択し、フォルダを「/ (root)」に設定します
5. 「Save」ボタンをクリックします
6. 設定が保存されると、「Your site is published at https://あなたのユーザー名.github.io/リポジトリ名/」というメッセージが表示されます

## 手順4: デプロイの確認

1. 「Your site is published at」の後に表示されるURLにアクセスします
2. アプリケーションが正常に表示されることを確認します
3. 各機能（検索、フィルタリング、CSVエクスポートなど）が正常に動作することを確認します

## トラブルシューティング

### サイトが表示されない場合:
- GitHub Pagesの設定が正しく行われているか確認します
- デプロイには数分かかる場合があります。少し待ってからアクセスしてみてください
- ブラウザのキャッシュをクリアしてみてください

### JavaScript機能が動作しない場合:
- ブラウザの開発者ツール（F12キー）でエラーがないか確認します
- index.htmlファイル内のスクリプトパスが正しいか確認します

## カスタマイズ

アプリケーションをカスタマイズする場合は、以下のファイルを編集します:

- `index.html`: UIデザインやJavaScriptコードを変更できます
- `README.md`: リポジトリの説明を更新できます

変更後は、GitHubにコミットしてプッシュすることで、自動的にサイトが更新されます。

## 注意事項

- GitHub Pagesは静的ウェブサイト向けのホスティングサービスです
- サーバーサイドの処理は実行できないため、すべての機能はクライアントサイドのJavaScriptで実装されています
- 現在のバージョンではモックデータを使用しています。実際のAPIと連携する場合は、CORSの設定に注意してください
