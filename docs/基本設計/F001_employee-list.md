# F001 従業員一覧表示

## 1. 概要
- 登録済み従業員を一覧で表示する。

## 2. 主フロー
1. 利用者が一覧画面にアクセスする。
2. Controller がページング・ソート条件を Service に渡す。
3. Service が Repository 経由で従業員一覧を取得する。
4. Controller が Model に一覧情報を設定する。
5. `index.html` を返却する。

## 3. 入出力
- 入力: `pageNo`, `sortField`, `sortDir`
- 出力: `listEmployees`, `currentPage`, `totalPages`, `totalItems`

## 4. 責務分担
- Controller: 画面表示データの組み立て
- Service: 取得条件の組み立て
- Repository: DB からの一覧取得
