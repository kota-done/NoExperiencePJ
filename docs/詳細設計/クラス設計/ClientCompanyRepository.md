# ClientCompanyRepository

## 概要
- `ClientCompany` エンティティの永続化アクセスを担当するリポジトリ。

## 配置
- パッケージ: `com.dev.raise.repository`
- ソース: `src/main/java/com/dev/raise/repository/ClientCompanyRepository.java`

## 主な責務
- 派遣先企業データの CRUD

## 継承
- `JpaRepository<ClientCompany, Long>`

## 利用可能な主な操作
- `findAll()`
- `findById(Long id)`
- `save(ClientCompany clientCompany)`
- `deleteById(Long id)`

## 備考
- 所属従業員有無の確認が必要な場合、従業員側参照と組み合わせて利用する想定。
