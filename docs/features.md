# 機能一覧

| 機能ID | 機能名 | 概要 | エンドポイント | 画面 |
|--------|--------|------|----------------|------|
| F001 | 従業員一覧表示 | 登録済み従業員を一覧表示する | `GET /` | `index.html` |
| F002 | 従業員登録 | 新規従業員を登録する | `GET /showNewEmployeeForm`, `POST /saveEmployee` | `new_employee.html` |
| F003 | 従業員更新 | 既存従業員を更新する | `GET /showFormForUpdate/{id}`, `POST /saveEmployee` | `update_employee.html` |
| F004 | 従業員削除 | 指定従業員を削除する | `GET /deleteEmployee/{id}` | 一覧へリダイレクト |
| F005 | 一覧ページ切替・並び替え | 一覧のページングとソートを行う | `GET /page/{pageNo}` | `index.html` |
