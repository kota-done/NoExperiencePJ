# クラス設計補足（手書き）

## EmployeeController
- 従業員管理画面の遷移制御を担当する。
- 一覧、登録画面、更新画面、削除、ページ切替・並び替えを扱う。

## EmployeeService
- 従業員データの業務処理インタフェースを定義する。

## EmployeeServiceImpl
- 従業員の取得・保存・削除・ページング処理を実装する。
- 一覧のソート条件を組み立てる。

## EmployeeRepository
- `Employee` エンティティの永続化アクセスを担当する。

## Employee
- `employees` テーブルと対応するデータモデルを定義する。
