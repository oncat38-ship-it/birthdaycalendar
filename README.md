# Birthday Palette v0.2

スマホ優先の誕生日管理アプリ。React + Vite + Firebase Authentication / Firestore / Storage。

## Vercel環境変数
`.env.example` の7項目をVercelのEnvironment Variablesへ登録し、再デプロイしてください。

## Firebase設定
1. Authenticationでメール/パスワード・Googleを有効化。
2. Firestore > ルールへ `firestore.rules` を貼り付けて「公開」。本ルールはログイン中の本人の `/users/{uid}/...` のみ許可します。
3. 画像を使う場合のみStorageを有効化し、`storage.rules` を公開してください。Storageが未設定でも画像なしの人物データは保存できます。
4. Authenticationの承認済みドメインにVercelドメインを登録。

## データ構造
- `users/{uid}/books/{bookId}` : データ枠（誕生日帳）と公開範囲設定
- `users/{uid}/books/{bookId}/people/{personId}` : 人物・誕生日・色・タグ・備考
- `users/{uid}/books/{bookId}/groups/{groupId}` : グループ
- `users/{uid}/settings/profile` : 表示名・アバター色
- `users/{uid}/settings/display` : 表示設定

## 注意
- データ枠ごとの非公開/限定公開/公開の設定UIと公開ページの入口を用意しています。
- 現時点では公開・共有の実配信は未接続です。誤公開を避けるためFirestoreは本人のみアクセス可能です。公開データベースを有効化する段階で公開用コレクションとルールを追加します。
- v0.1の旧パス `users/{uid}/people` / `groups` はv0.2のデータ枠配下へ自動移行しません。旧版で保存済みデータがある場合は、更新前にお知らせください。
