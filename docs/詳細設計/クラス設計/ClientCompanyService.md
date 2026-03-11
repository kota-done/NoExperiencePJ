# ClientCompanyService

## 概要
- 派遣先企業関連の業務処理インタフェース。

## 配置
- パッケージ: `com.company.training.java.service`
- ソース: `src/main/java/com/company/training/java/service/ClientCompanyService.java`

## 主な責務
- 派遣先企業一覧取得
- 派遣先企業保存
- 指定 ID の派遣先企業取得
- 指定 ID の派遣先企業削除

## メソッド
### getAllClientCompanies()
- 派遣先企業一覧を取得する。
- 引数: なし
- 戻り値: `List<ClientCompany>`
- 例外: なし（下位例外は呼び出し元へ伝播）

### saveClientCompany(ClientCompany clientCompany)
- 派遣先企業情報を保存する。
- 引数:
  - `clientCompany`: 保存対象の派遣先企業エンティティ
- 戻り値: `void`
- 例外: 入力不正や永続化失敗時に実行時例外が発生し得る

### getClientCompanyById(long id)
- 指定 ID の派遣先企業を取得する。
- 引数:
  - `id`: 取得対象の派遣先企業 ID
- 戻り値: `ClientCompany`
- 例外: 対象なしの場合 `RuntimeException`

### deleteClientCompanyById(long id)
- 指定 ID の派遣先企業を削除する。
- 引数:
  - `id`: 削除対象の派遣先企業 ID
- 戻り値: `void`
- 例外: 所属従業員が存在する場合や対象なしの場合に実行時例外が発生し得る

## 備考
- 実装は `ClientCompanyServiceImpl` が担当する。
