# ClientCompanyController

## 概要
- 派遣先企業管理画面の MVC コントローラ。
- 一覧、登録、更新、削除の画面遷移を担当する。

## 配置
- パッケージ: `com.dev.raise.controller`
- ソース: `src/main/java/com/dev/raise/controller/ClientCompanyController.java`

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

### showNewClientCompanyForm(Model model)
- 新規登録用の空 `ClientCompany` をモデルへ設定し、登録画面を返す。

### saveClientCompany(ClientCompany clientCompany)
- 登録または更新の保存を行い、一覧画面へリダイレクトする。

### showClientCompanyFormForUpdate(long id, Model model)
- 指定 ID の派遣先企業情報を取得し、更新画面へ表示する。

### deleteClientCompany(long id)
- 指定 ID の派遣先企業情報を削除し、一覧画面へリダイレクトする。

## 備考
- 所属従業員が存在する場合の削除制御は Service 層で判定する想定。
