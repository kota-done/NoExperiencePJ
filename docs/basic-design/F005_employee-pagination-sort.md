# F005 一覧ページ切替・並び替え

## 1. 概要
- 一覧画面でページ切替と並び替えを行う。

## 2. 主フロー
1. 利用者がページ番号または並び替え条件を指定する。
2. Controller が条件を Service に渡す。
3. Service が `PageRequest` と `Sort` を組み立てる。
4. Repository が対象ページを取得する。
5. Controller が画面表示用情報を Model に設定し返却する。

## 3. 入力
- `pageNo`
- `sortField`
- `sortDir`（asc/desc）

## 4. 出力
- 対象ページの従業員一覧
- 総ページ数、総件数、現在ページ
- 逆順ソート値（`reverseSortDir`）

## 5. 責務分担
- Controller: 表示情報の設定
- Service: ページング・ソート条件の生成
- Repository: ページ単位データ取得
