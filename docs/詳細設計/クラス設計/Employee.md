# Employee

## 概要
- 従業員情報を表す JPA エンティティ。
- `employees` テーブルに対応する。

## 配置
- パッケージ: `com.dev.raise.model`
- ソース: `src/main/java/com/dev/raise/model/Employee.java`

## 主な責務
- 従業員データの保持
- JPA エンティティとしてのマッピング定義

## テーブル対応
- テーブル名: `employees`

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

## メソッド
- getter / setter のみ

## 備考
- 現状はバリデーションアノテーション未付与。
