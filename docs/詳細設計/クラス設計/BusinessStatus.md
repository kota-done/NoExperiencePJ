# BusinessStatus

## 概要
- 派遣先企業の取引ステータスを表す列挙型。

## 配置
- パッケージ: `com.dev.raise.model` または `com.dev.raise.enums`
- ソース: `src/main/java/com/dev/raise/.../BusinessStatus.java`

## 値
- `ACTIVE`
  - 日本語表示: 取引中
- `SUSPENDED`
  - 日本語表示: 取引停止
- `CLOSED`
  - 日本語表示: 契約終了

## 備考
- DB には enum 名を保存する想定。
- 画面表示時は日本語ラベルへ変換する想定。
