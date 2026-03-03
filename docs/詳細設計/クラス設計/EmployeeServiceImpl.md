# EmployeeServiceImpl

## 概要
- `EmployeeService` の実装クラス。
- リポジトリを利用して従業員管理の業務処理を実装する。

## 配置
- パッケージ: `com.dev.raise.service`
- ソース: `src/main/java/com/dev/raise/service/EmployeeServiceImpl.java`

## 主な責務
- 従業員の保存
- 指定 ID の従業員取得
- 指定 ID の従業員削除
- ソート条件付きページング処理

## 依存関係
- `EmployeeRepository`

## メソッド
### getAllEmployees()
- リポジトリから全件取得する。

### saveEmployee(Employee employee)
- リポジトリへ保存処理を委譲する。

### getEmployeeById(long id)
- 指定 ID を検索し、存在しない場合は例外を送出する。

### deleteEmployeeById(long id)
- 指定 ID を削除する。

### findPaginated(int pageNo, int pageSize, String sortField, String sortDirection)
- ソート条件を組み立て、`PageRequest` を生成してページング結果を返す。

## 備考
- 取得失敗時は `RuntimeException` を送出する。
- ビジネスルールは少なく、現在はリポジトリ委譲が中心。
