# DirectEmployeeServiceImpl

## 概要
- `DirectEmployeeService` の実装クラス。
- リポジトリを利用して従業員管理の業務処理を実装する。

## 配置
- パッケージ: `com.company.training.java.service`
- ソース: `src/main/java/com/company/training/java/service/DirectEmployeeServiceImpl.java`

## 主な責務
- 従業員の保存
- 指定 ID の従業員取得
- 指定 ID の従業員削除
- ソート条件付きページング処理
- 所属派遣先企業を含む従業員情報の管理
- 従業員ステータスの保持・更新

## 依存関係
- `DirectEmployeeRepository`

## メソッド
### getAllDirectEmployees()
- リポジトリから全件取得する。
- 引数: なし
- 戻り値: `List<DirectEmployee>`
- 例外: なし（下位例外は呼び出し元へ伝播）

### saveDirectEmployee(DirectEmployee employee)
- リポジトリへ保存処理を委譲する。
- 引数:
  - `employee`: 保存対象の従業員エンティティ
- 戻り値: `void`
- 例外: 入力不正や永続化失敗時に実行時例外が発生し得る

### getDirectEmployeeById(long id)
- 指定 ID を検索し、存在しない場合は例外を送出する。
- 引数:
  - `id`: 取得対象の従業員 ID
- 戻り値: `DirectEmployee`
- 例外: 対象なしの場合 `RuntimeException`

### deleteDirectEmployeeById(long id)
- 指定 ID を削除する。
- 引数:
  - `id`: 削除対象の従業員 ID
- 戻り値: `void`
- 例外: 対象なしや整合性制約違反時に実行時例外が発生し得る

### findPaginated(int pageNo, int pageSize, String sortField, String sortDirection)
- ソート条件を組み立て、`PageRequest` を生成してページング結果を返す。
- 引数:
  - `pageNo`: 1 始まりのページ番号
  - `pageSize`: 1 ページあたり件数
  - `sortField`: ソート対象フィールド名
  - `sortDirection`: `asc` または `desc`
- 戻り値: `Page<DirectEmployee>`
- 例外: ソート項目不正時に実行時例外が発生し得る

## 備考
- 取得失敗時は `RuntimeException` を送出する。
- ビジネスルールは少なく、現在はリポジトリ委譲が中心。
