# DirectEmployee

## 概要
- 従業員情報を表す JPA エンティティ。
- `direct_employees` テーブルに対応する。

## 配置
- パッケージ: `com.company.training.java.model`
- ソース: `src/main/java/com/company/training/java/model/DirectEmployee.java`

## 主な責務
- 従業員データの保持
- JPA エンティティとしてのマッピング定義

## テーブル対応
- テーブル名: `direct_employees`

## 項目
### id
- 型: `long`
- 役割: 主キー
- 備考: `GenerationType.IDENTITY` による自動採番

### firstName
- 型: `String`
- 役割: 名
- カラム名: `first_name`

### lastName
- 型: `String`
- 役割: 姓
- カラム名: `last_name`

### email
- 型: `String`
- 役割: メールアドレス
- カラム名: `email`

### status
- 型: `DirectEmployeeStatus`
- 役割: 従業員の現在ステータス
- 想定値:
  - `ON_ASSIGNMENT`
  - `WAITING`
  - `LEAVE_OF_ABSENCE`
  - `TRAINING`

### clientCompany
- 型: `ClientCompany`
- 役割: 所属する派遣先企業
- 関連: `ManyToOne`
- 外部キー: `client_company_id`

## メソッド
- getter / setter のみ

## 備考
- 現状はバリデーションアノテーション未付与。
- 一覧画面では `clientCompany.companyName` と `status` を表示対象に含める。
