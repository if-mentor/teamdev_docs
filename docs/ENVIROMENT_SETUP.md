# 環境構築

## 1. リポジトリの clone

GitHubからリポジトリを取得する。

```sh
git clone [GitHub URL]
```

## 2. 依存関係のインストール

必要なライブラリ・パッケージをインストールする。

```sh
npm install
```

## 3. 環境変数の設定

環境変数のサンプルファイルをコピーする。

```sh
cp .env.example .env
```

**※ .env には機密情報が含まれる可能性があるため、GitHubへコミットしないこと。**

## 4. 動作確認

各サービスを起動し、ブラウザからアクセスする。

| Service | URL | Command |
| --- | --- | --- |
| Application | http://localhost:3000 | `npm run dev` |
| Storybook | http://localhost:6006 | `npm run storybook` |
