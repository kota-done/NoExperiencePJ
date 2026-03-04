# ClientCompanyService

## 概要
- 派遣先企業関連の業務処理インタフェース。

## 配置
- パッケージ: `com.dev.raise.service`
- ソース: `src/main/java/com/dev/raise/service/ClientCompanyService.java`

## 主な責務
- 派遣先企業一覧取得
- 派遣先企業保存
- 指定 ID の派遣先企業取得
- 指定 ID の派遣先企業削除

## メソッド
### getAllClientCompanies()
- 派遣先企業一覧を取得する。

### saveClientCompany(ClientCompany clientCompany)
- 派遣先企業情報を保存する。

### getClientCompanyById(long id)
- 指定 ID の派遣先企業を取得する。

### deleteClientCompanyById(long id)
- 指定 ID の派遣先企業を削除する。

## 備考
- 実装は `ClientCompanyServiceImpl` が担当する。
