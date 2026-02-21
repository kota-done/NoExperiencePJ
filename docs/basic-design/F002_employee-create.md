# F002 従業員登録

## 1. 概要
- 新規従業員を登録する。

## 2. 主フロー
1. 利用者が登録画面を開く。
2. Controller が空の Employee を Model に設定し画面表示する。
3. 利用者が入力して送信する。
4. Controller が Employee を Service に渡す。
5. Service が Repository を通じて保存する。
6. 一覧画面へリダイレクトする。

## 3. 入出力
- 入力: `firstName`, `lastName`, `email`
- 出力: 一覧画面へ遷移

## 4. 責務分担
- Controller: 入力受領と遷移制御
- Service: 登録処理の実行
- Repository: `employees` への保存
