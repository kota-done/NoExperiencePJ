# ClientCompanyServiceImpl

## 概要
- `ClientCompanyService` の実装クラス。
- リポジトリを利用して派遣先企業管理の業務処理を実装する。

## 配置
- パッケージ: `com.company.training.java.service`
- ソース: `src/main/java/com/company/training/java/service/ClientCompanyServiceImpl.java`

## 主な責務
- 派遣先企業の保存
- 指定 ID の派遣先企業取得
- 指定 ID の派遣先企業削除
- 取引ステータスの保持・更新
- 所属従業員が存在する場合の削除制御

## 依存関係
- `ClientCompanyRepository`
- `DirectEmployeeRepository` または従業員存在確認手段

## メソッド
### getAllClientCompanies()
- リポジトリから全件取得する。
- 引数: なし
- 戻り値: `List<ClientCompany>`
- 例外: なし（下位例外は呼び出し元へ伝播）

### saveClientCompany(ClientCompany clientCompany)
- リポジトリへ保存処理を委譲する。
- 引数:
  - `clientCompany`: 保存対象の派遣先企業エンティティ
- 戻り値: `void`
- 例外: 入力不正や永続化失敗時に実行時例外が発生し得る

### getClientCompanyById(long id)
- 指定 ID を検索し、存在しない場合は例外を送出する。
- 引数:
  - `id`: 取得対象の派遣先企業 ID
- 戻り値: `ClientCompany`
- 例外: 対象なしの場合 `RuntimeException`

### deleteClientCompanyById(long id)
- 所属従業員がいる場合は削除不可とし、問題なければ削除する。
- 引数:
  - `id`: 削除対象の派遣先企業 ID
- 戻り値: `void`
- 例外: 所属従業員が存在する場合や対象なしの場合に実行時例外が発生し得る

## 備考
- 取引ステータスは `BusinessStatus` enum で管理する。
