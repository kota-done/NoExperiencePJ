# DirectEmployeeService

## 概要
- 従業員関連の業務処理インタフェース。

## 配置
- パッケージ: `com.company.training.java.service`
- ソース: `src/main/java/com/company/training/java/service/DirectEmployeeService.java`

## 主な責務
- 従業員一覧取得
- 従業員保存
- 指定 ID の従業員取得
- 指定 ID の従業員削除
- ページング/ソート付き一覧取得
- 従業員ステータス管理
- 派遣先企業との関連を含む従業員情報管理

## メソッド
### getAllDirectEmployees()
- 従業員一覧を取得する。
- 引数: なし
- 戻り値: `List<DirectEmployee>`
- 例外: なし（下位例外は呼び出し元へ伝播）

### saveDirectEmployee(DirectEmployee employee)
- 従業員情報を保存する。
- 引数:
  - `employee`: 保存対象の従業員エンティティ
- 戻り値: `void`
- 例外: 入力不正や永続化失敗時に実行時例外が発生し得る

### getDirectEmployeeById(long id)
- 指定 ID の従業員を取得する。
- 引数:
  - `id`: 取得対象の従業員 ID
- 戻り値: `DirectEmployee`
- 例外: 対象なしの場合 `RuntimeException`

### deleteDirectEmployeeById(long id)
- 指定 ID の従業員を削除する。
- 引数:
  - `id`: 削除対象の従業員 ID
- 戻り値: `void`
- 例外: 対象なしや整合性制約違反時に実行時例外が発生し得る

### findPaginated(int pageNo, int pageSize, String sortField, String sortDirection)
- ページングとソートを考慮した一覧を取得する。
- 引数:
  - `pageNo`: 1 始まりのページ番号
  - `pageSize`: 1 ページあたり件数
  - `sortField`: ソート対象フィールド名
  - `sortDirection`: `asc` または `desc`
- 戻り値: `Page<DirectEmployee>`
- 例外: ソート項目不正時に実行時例外が発生し得る

## 備考
- 実装は `DirectEmployeeServiceImpl` が担当する。
