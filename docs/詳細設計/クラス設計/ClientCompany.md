# ClientCompany

## 概要
- 派遣先企業情報を表す JPA エンティティ。
- `client_companies` テーブルに対応する。

## 配置
- パッケージ: `com.company.training.java.model`
- ソース: `src/main/java/com/company/training/java/model/ClientCompany.java`

## 主な責務
- 派遣先企業データの保持
- JPA エンティティとしてのマッピング定義

## テーブル対応
- テーブル名: `client_companies`

## 項目
### id
- 型: `long`
- 役割: 主キー
- 備考: `GenerationType.IDENTITY` による自動採番

### companyName
- 型: `String`
- 役割: 企業名
- カラム名: `company_name`

### charge
- 型: `BigDecimal`
- 役割: 単価
- カラム名: `charge`

### prefectureName
- 型: `String`
- 役割: 都道府県名
- カラム名: `prefecture_name`

### contactEmail
- 型: `String`
- 役割: 連絡先メールアドレス
- カラム名: `contact_email`

### phoneNumber
- 型: `String`
- 役割: 電話番号
- カラム名: `phone_number`

### businessStatus
- 型: `BusinessStatus`
- 役割: 企業の取引ステータス
- 想定値:
  - `ACTIVE`
  - `SUSPENDED`
  - `CLOSED`

## メソッド
- getter / setter のみ

## 備考
- 所属従業員が存在する場合は削除不可とする想定。
