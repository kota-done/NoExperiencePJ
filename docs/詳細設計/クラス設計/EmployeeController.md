# EmployeeController

## 概要
- 従業員管理画面の MVC コントローラ。
- 一覧、登録、更新、削除、ページング、ソートの画面遷移を担当する。

## 配置
- パッケージ: `com.dev.raise.controller`
- ソース: `src/main/java/com/dev/raise/controller/EmployeeController.java`

## 主な責務
- 一覧画面表示
- 新規登録画面表示
- 登録/更新処理の受付
- 更新画面表示
- 削除処理の受付
- ページング/ソート付き一覧表示
- 一覧画面で所属派遣先企業と従業員ステータスを表示するための Model 設定

## 依存関係
- `EmployeeService`
- `Model`

## メソッド
### viewHomePage(Model model)
- 1ページ目、`firstName` 昇順で一覧画面を表示する。

### showNewEmployeeForm(Model model)
- 新規登録用の空 `Employee` をモデルへ設定し、登録画面を返す。
- 画面では派遣先企業選択肢と従業員ステータス入力を扱う想定とする。

### saveEmployee(Employee employee)
- 登録または更新の保存を行い、一覧画面へリダイレクトする。

### showFormForUpdate(long id, Model model)
- 指定 ID の従業員情報を取得し、更新画面へ表示する。
- 画面では派遣先企業変更と従業員ステータス変更を扱う想定とする。

### deleteEmployee(long id)
- 指定 ID の従業員情報を削除し、一覧画面へリダイレクトする。

### findPaginated(int pageNo, String sortField, String sortDir, Model model)
- ページ番号、ソート項目、ソート方向に応じた一覧画面を表示する。

## 入出力
- 入力: HTTP リクエスト、パス変数、フォーム値
- 出力: Thymeleaf テンプレート名、リダイレクト

## 備考
- REST API は未実装。
- 例外処理は共通化されていない。
