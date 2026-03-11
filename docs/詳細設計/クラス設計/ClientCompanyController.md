# ClientCompanyController

## 概要
- 派遣先企業管理画面の MVC コントローラ。
- 一覧、登録、更新、削除の画面遷移を担当する。

## 配置
- パッケージ: `com.company.training.java.controller`
- ソース: `src/main/java/com/company/training/java/controller/ClientCompanyController.java`

## 主な責務
- 派遣先企業一覧画面表示
- 新規登録画面表示
- 登録/更新処理の受付
- 更新画面表示
- 削除処理の受付

## 依存関係
- `ClientCompanyService`
- `Model`

## メソッド
### viewClientCompanyList(Model model)
- 派遣先企業一覧画面を表示する。
- 引数:
  - `model`: 一覧描画に必要な属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: なし（下位例外は呼び出し元へ伝播）

### showNewClientCompanyForm(Model model)
- 新規登録用の空 `ClientCompany` をモデルへ設定し、登録画面を返す。
- 引数:
  - `model`: 登録画面初期表示用の属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: なし（下位例外は呼び出し元へ伝播）

### saveClientCompany(ClientCompany clientCompany)
- 登録または更新の保存を行い、一覧画面へリダイレクトする。
- 引数:
  - `clientCompany`: フォームからバインドされた保存対象の派遣先企業
- 戻り値: `String`（リダイレクト URL）
- 例外: 入力不正や永続化失敗時に実行時例外が発生し得る

### showClientCompanyFormForUpdate(long id, Model model)
- 指定 ID の派遣先企業情報を取得し、更新画面へ表示する。
- 引数:
  - `id`: 更新対象の派遣先企業 ID
  - `model`: 更新画面表示用の属性を格納する `Model`
- 戻り値: `String`（遷移先テンプレート名）
- 例外: 対象なしの場合 `RuntimeException`

### deleteClientCompany(long id)
- 指定 ID の派遣先企業情報を削除し、一覧画面へリダイレクトする。
- 引数:
  - `id`: 削除対象の派遣先企業 ID
- 戻り値: `String`（リダイレクト URL）
- 例外: 所属従業員が存在する場合や対象なしの場合に実行時例外が発生し得る

## 備考
- 所属従業員が存在する場合の削除制御は Service 層で判定する想定。
