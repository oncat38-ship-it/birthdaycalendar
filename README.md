# Birthday Palette (第一版)

スマートフォン優先の誕生日管理Webアプリです。Firebase Authentication（メール/パスワード・Google）、Cloud Firestore、Firebase Storageを使用します。

## セットアップ

1. Node.js 20以降を用意します。
2. このフォルダで `npm install` を実行します。
3. `.env.example` を `.env` にコピーし、Firebase Webアプリの設定値を入力します。
4. `npm run dev` でローカル起動、`npm run build` で本番ビルドします。

## Firebase側の設定

- Authenticationでメール/パスワードとGoogleを有効化。
- Firestore Databaseを作成し、`firestore.rules` の内容を「ルール」に公開。
- Storageを利用する場合はFirebase ConsoleでStorageを有効化し、`storage.rules` を公開。
- Authentication > Settings > Authorized domains に、開発/公開で使うドメインを追加。
- Firebase Storageはプロジェクトのプラン・利用条件を確認してから有効化してください。

## Vercel

GitHubへアップロード後、VercelでリポジトリをImportします。Framework PresetはVite、Build Commandは `npm run build`、Output Directoryは `dist`。Environment Variablesに`.env.example`と同じ `VITE_` 変数を登録します。

## 現在の機能

- メール/パスワード新規登録・ログイン、Googleログイン
- アカウントごとの人物データ保存
- 月間カレンダー、今月の誕生日表示
- 一覧、近日順/五十音順/日付順/グループ別ソート、検索、グループ絞り込み
- 人物の追加/編集/削除、誕生日（生年は任意）、カラー、グループ、画像、備考
- グループ追加/削除
- 文字サイズ、一覧密度の設定

## 第一版の範囲・注意

- 公開/共有機能はまだ実装していません。データはログイン中の本人だけが読み書きできます。
- 画像アップロードにはFirebase Storageの有効化とルール公開が必要です。Storage未設定時は画像保存に失敗します。
- Firestoreルールはユーザーごとのデータ領域だけを許可します。公開データベース用ルールは後続段階で別途設計します。
- 画像は5MB未満に制限しています。実運用前に画像圧縮を追加することを推奨します。
