# Birthday Palette v0.3

React + Vite + Firebase の誕生日管理アプリです。

## v0.3の変更
- カレンダー／一覧に「コンパクト・標準・詳細」の即時切替を追加。選択はアカウント設定に保存。
- コンパクトは名前・誕生日を中心に表示、標準は従来の表示、詳細は生年・公開範囲・タグ・備考を表示。
- アカウントプロフィールに写真アップロードを追加（5MB未満）。
- グループの名称変更・削除を追加。削除時は所属人物を未分類に移動。
- タグの名称変更・削除を追加。人物に付与されたタグにも反映。
- データ枠の名称変更・削除を追加。最後の1枠は削除不可。削除時は配下の人物・グループも削除。
- ToDoカレンダー連携の設定案内を追加。既存のtv-todo-bridgeはTV予定表とToDo間の連携専用で、Birthday Paletteを直接接続するAPIはまだありません。既存連携を壊さないよう、この版では未接続のままです。

## Vercel
既存のVercelプロジェクトへ、フォルダ内のファイルを置き換えてデプロイしてください。
環境変数はv0.2から変更ありません。

## Firebase Storage
プロフィール画像と人物画像を使う場合は、Firebase ConsoleでStorageを有効化してください。
その後 `storage.rules` の内容を Firebase Storage > Rules に反映してください。
画像は5MB未満、画像形式のみ許可しています。保存先はユーザーUID配下です。

## Firestore
Firestoreの保存先構造・既存データ形式はv0.2から変更していません。Firestoreルールの変更は不要です。

## ToDoカレンダー連携について
既存の中継Worker `tv-todo-bridge` は `/api/link/code`、`/api/link/redeem`、`/api/link/status`、`/api/schedules` を持ち、TVアプリとToDoアプリの2者連携を前提にしています。Birthday Paletteは別Firebaseプロジェクト `birthday-7852d` なので、単純に既存のTV役割として接続してはいけません。次段階で誕生日専用の連携テーブル/APIとToDo側の日めくり表示を追加します。
