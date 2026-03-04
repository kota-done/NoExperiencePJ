# EmployeeRepository

## 概要
- `Employee` エンティティの永続化アクセスを担当するリポジトリ。

## 配置
- パッケージ: `com.dev.raise.repository`
- ソース: `src/main/java/com/dev/raise/repository/EmployeeRepository.java`

## 主な責務
- 従業員データの CRUD
- ページング付き検索
- 所属派遣先企業を含めた従業員データ参照

## 継承
- `JpaRepository<Employee, Long>`

## 利用可能な主な操作
- `findAll()`
- `findAll(Pageable pageable)`
- `findById(Long id)`
- `save(Employee employee)`
- `deleteById(Long id)`

## 備考
- 独自クエリは未定義。
- Spring Data JPA の標準機能に依存する。
