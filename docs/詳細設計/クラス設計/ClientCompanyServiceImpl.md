# ClientCompanyServiceImpl

## 概要
- `ClientCompanyService` の実装クラス。
- リポジトリを利用して派遣先企業管理の業務処理を実装する。

## 配置
- パッケージ: `com.dev.raise.service`
- ソース: `src/main/java/com/dev/raise/service/ClientCompanyServiceImpl.java`

## 主な責務
- 派遣先企業の保存
- 指定 ID の派遣先企業取得
- 指定 ID の派遣先企業削除
- 取引ステータスの保持・更新
- 所属従業員が存在する場合の削除制御

## 依存関係
- `ClientCompanyRepository`
- `EmployeeRepository` または従業員存在確認手段

## メソッド
### getAllClientCompanies()
- リポジトリから全件取得する。

### saveClientCompany(ClientCompany clientCompany)
- リポジトリへ保存処理を委譲する。

### getClientCompanyById(long id)
- 指定 ID を検索し、存在しない場合は例外を送出する。

### deleteClientCompanyById(long id)
- 所属従業員がいる場合は削除不可とし、問題なければ削除する。

## 備考
- 取引ステータスは `BusinessStatus` enum で管理する。
