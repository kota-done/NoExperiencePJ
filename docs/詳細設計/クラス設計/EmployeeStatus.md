# EmployeeStatus

## 概要
- 従業員の現在ステータスを表す列挙型。

## 配置
- パッケージ: `com.dev.raise.model` または `com.dev.raise.enums`
- ソース: `src/main/java/com/dev/raise/.../EmployeeStatus.java`

## 値
- `ON_ASSIGNMENT`
  - 日本語表示: 出向中
- `WAITING`
  - 日本語表示: 待機
- `LEAVE_OF_ABSENCE`
  - 日本語表示: 休職中
- `TRAINING`
  - 日本語表示: 育成中

## 備考
- DB には enum 名を保存する想定。
- 画面表示時は日本語ラベルへ変換する想定。
