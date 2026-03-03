# F004 従業員削除

## 1. 概要
- 指定した従業員を削除する。

## 2. 主フロー
1. 利用者が削除操作を実行する。
2. Controller が ID を Service に渡す。
3. Service が Repository 経由で削除する。
4. 一覧画面へリダイレクトする。

## 3. 入出力
- 入力: `id`
- 出力: 一覧画面へ遷移

## 4. 責務分担
- Controller: 受け付けと遷移制御
- Service: 削除処理実行
- Repository: `employees` から削除
