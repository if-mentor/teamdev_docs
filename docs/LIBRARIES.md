# 使用技術

プロジェクトで使用するプログラミング言語・フレームワーク・インフラ・開発ツール・ライブラリについて記載します。

## フロントエンド

| 技術 | 用途 |
| --- | --- |
| [HTML](https://developer.mozilla.org/ja/docs/Web/HTML) | Webページの構造やコンテンツを定義する |
| [CSS](https://developer.mozilla.org/ja/docs/Web/CSS) | Webページのレイアウトや色、フォントなどのデザインを指定する |
| [JavaScript](https://developer.mozilla.org/ja/docs/Web/JavaScript) | Webページに動的な処理やインタラクティブな機能を実装する |
| [TypeScript](https://www.typescriptlang.org) | JavaScriptに静的型付けを追加し、型チェックによって開発時のエラーを防止するとともに、コードの保守性を向上させる |
| [React](https://ja.react.dev) | UIをコンポーネント単位で構築するためのJavaScriptライブラリ |
| [Next.js](https://nextjs.org) | ReactをベースとしたWebアプリケーションフレームワーク |

## バックエンド

| 技術 | 用途 |
| --- | --- |
| [Node.js](https://nodejs.org) | JavaScriptをサーバーサイドで実行するためのJavaScriptランタイム環境 |
| [Supabase](https://supabase.com) | PostgreSQLをベースとしたデータベースや認証、ストレージなどの機能を提供するバックエンドサービス |
| [Prisma](https://www.prisma.io) | データベースとアプリケーション間のデータ操作を効率化し、型安全なクエリの実行やスキーマ管理をサポートするORM |

## インフラ

| 技術 | 用途 |
| --- | --- |
| [Vercel](https://vercel.com) | Webアプリケーションのホスティング・デプロイを行うクラウドプラットフォーム |

## ツール

| 技術 | 用途 |
| --- | --- |
| [GitHub](https://github.co.jp) | Gitを利用したソースコードのバージョン管理や、チームでの共同開発、プルリクエストによるコードレビューを行うプラットフォーム |
| [npm](https://www.npmjs.com) | JavaScript・Node.js向けのパッケージ管理ツール |
| [Storybook](https://storybook.js.org) | UIコンポーネントを独立した環境で開発・表示・検証するためのツール |
| [Vite](https://ja.vite.dev) | 高速な開発サーバーとビルド機能を提供するフロントエンドビルドツール |
| [Postman](https://www.postman.com) | HTTPリクエストを送信してAPIの動作確認やレスポンスの検証を行うAPI開発・テストツール |

## ライブラリ / プラグイン

### バリデーション

| ライブラリ | 用途 |
| --- | --- |
| [Zod](https://github.com/colinhacks/zod) | TypeScriptとの親和性が高く、データの型や構造を検証するスキーマバリデーションライブラリ |

### コード品質・フォーマット

| ライブラリ | 用途 |
| --- | --- |
| [ESLint](https://github.com/eslint/eslint) | JavaScript・TypeScriptのソースコードを静的解析し、潜在的なバグや記述上の問題を検出するリンター |
| [eslint-config-next](https://nextjs.org/docs/app/api-reference/config/eslint) | Next.js向けのESLint設定パッケージ。Next.js特有のルールや推奨されるコーディング規約を適用する |
| [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) | Prettierと競合するESLintルールを無効化し、両ツールのルールの競合を防ぐ設定パッケージ |
| [eslint-plugin-storybook](https://storybook.js.org/docs/configure/integration/eslint-plugin) | Storybookのファイルや設定に対して、推奨されるコーディングルールを適用するESLintプラグイン |
| [Prettier](https://github.com/prettier/prettier) | ソースコードのインデントや改行、スペースなどの書式を自動的に整えるコードフォーマッター |
| [prettier-plugin-sort-imports](https://github.com/trivago/prettier-plugin-sort-imports) | import文を指定したルールに従って自動的に並び替え、インポートの記述順序を統一するPrettierプラグイン |

### 自動化

| ライブラリ | 用途 |
| --- | --- |
| [Husky](https://github.com/typicode/husky) | Git Hooksを管理し、コミットやプッシュなどのGit操作を契機に任意のコマンドを自動実行するツール |
| [lint-staged](https://github.com/lint-staged/lint-staged) | Gitでステージングされたファイルのみに対して、ESLintやPrettierなどのコマンドを実行するツール |
