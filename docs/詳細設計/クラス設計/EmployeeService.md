# EmployeeService

## 概要
- 従業員関連の業務処理インタフェース。

## 配置
- パッケージ: `com.dev.raise.service`
- ソース: `src/main/java/com/dev/raise/service/EmployeeService.java`

## 主な責務
- 従業員一覧取得
- 従業員保存
- 指定 ID の従業員取得
- 指定 ID の従業員削除
- ページング/ソート付き一覧取得
- 従業員ステータス管理
- 派遣先企業との関連を含む従業員情報管理

## メソッド
### getAllEmployees()
- 従業員一覧を取得する。

### saveEmployee(Employee employee)
- 従業員情報を保存する。

### getEmployeeById(long id)
- 指定 ID の従業員を取得する。

### deleteEmployeeById(long id)
- 指定 ID の従業員を削除する。

### findPaginated(int pageNo, int pageSize, String sortField, String sortDirection)
- ページングとソートを考慮した一覧を取得する。

## 備考
- 実装は `EmployeeServiceImpl` が担当する。
