# DirectEmployeeController

## 概要
- 従業員管理画面の MVC コントローラ。
- 一覧、登録、更新、削除、ページング、ソートの画面遷移を担当する。

## 配置
- パッケージ: `com.company.training.java.controller`
- ソース: `src/main/java/com/company/training/java/controller/DirectEmployeeController.java`

## 主な責務
- 一覧画面表示
- 新規登録画面表示
- 登録/更新処理の受付
- 更新画面表示
- 削除処理の受付
- ページング/ソート付き一覧表示
- 一覧画面で所属派遣先企業と従業員ステータスを表示するための Model 設定

## 依存関係
- `DirectEmployeeService`
- `Model`

## メソッド
### viewHomePage(Model model)
- 1ページ目、`firstName` 昇順で一覧画面を表示する。
- 引数:
  - `model`: 画面描画に必要な属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: なし（下位例外は呼び出し元へ伝播）

### showNewDirectEmployeeForm(Model model)
- 新規登録用の空 `DirectEmployee` をモデルへ設定し、登録画面を返す。
- 画面では派遣先企業選択肢と従業員ステータス入力を扱う想定とする。
- 引数:
  - `model`: 登録画面初期表示用の属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: なし（下位例外は呼び出し元へ伝播）

### saveDirectEmployee(DirectEmployee employee)
- 登録または更新の保存を行い、一覧画面へリダイレクトする。
- 引数:
  - `employee`: フォームからバインドされた保存対象の従業員
- 戻り値: `String`（リダイレクト URL）
- 例外: 入力不正や永続化失敗時に実行時例外が発生し得る

### showDirectEmployeeFormForUpdate(long id, Model model)
- 指定 ID の従業員情報を取得し、更新画面へ表示する。
- 画面では派遣先企業変更と従業員ステータス変更を扱う想定とする。
- 引数:
  - `id`: 更新対象の従業員 ID
  - `model`: 更新画面表示用の属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: 対象なしの場合 `RuntimeException`

### deleteDirectEmployee(long id)
- 指定 ID の従業員情報を削除し、一覧画面へリダイレクトする。
- 引数:
  - `id`: 削除対象の従業員 ID
- 戻り値: `String`（リダイレクト URL）
- 例外: 対象なしや整合性制約違反時に実行時例外が発生し得る

### findPaginated(int pageNo, String sortField, String sortDir, Model model)
- ページ番号、ソート項目、ソート方向に応じた一覧画面を表示する。
- 引数:
  - `pageNo`: 表示対象ページ番号（1 始まり）
  - `sortField`: ソート対象フィールド名
  - `sortDir`: ソート方向（`asc` または `desc`）
  - `model`: 一覧描画用の属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: ソート項目不正時に実行時例外が発生し得る

## 入出力
- 入力: HTTP リクエスト、パス変数、フォーム値
- 出力: Thymeleaf テンプレート名、リダイレクト

## 備考
- REST API は未実装。
- 例外処理は共通化されていない。
