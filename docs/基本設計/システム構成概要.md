# アーキテクチャ設計

## 1. システム全体像
- 本システムは「従業員管理画面」を提供する Web アプリケーションである。
- 利用者は以下の画面機能を利用できる。
  - 従業員一覧画面の表示
  - 従業員登録画面の表示と登録処理
  - 従業員更新画面の表示と更新処理
  - 従業員削除処理
  - 一覧のページ切替と並び替え
- 画面は Thymeleaf テンプレートで HTML を生成し、Spring MVC がリクエストを受け付ける。

## 2. レイヤ構成と責務

### 2.1 Controller層
- 対象クラス: `EmployeeController`
- 役割:
  - 画面リクエストの受付
  - フォーム入力の受け取り（`Employee` へのバインド）
  - 画面表示に必要な値の Model 設定
  - Service 呼び出し結果に応じた画面返却・リダイレクト
- 非役割:
  - SQL 発行や永続化処理の実行
  - 業務判定ロジックの直接実装

### 2.2 Service層
- 対象クラス: `EmployeeService`, `EmployeeServiceImpl`
- 役割:
  - 従業員情報の業務処理（取得、登録/更新、削除）
  - 一覧表示向けページング・ソート条件の組み立て
  - Repository 呼び出しの集約
- 扱うデータ:
  - `Employee` エンティティ

### 2.3 Repository層
- 対象クラス: `EmployeeRepository`
- 役割:
  - `employees` テーブルに対する永続化アクセス
  - `Employee` エンティティの保存・取得・削除
  - ページング/ソート付きの一覧取得（`findAll(Pageable)`）
- 補足:
  - 本プロジェクトでは `JpaRepository<Employee, Long>` を利用する

### 2.4 Model層
- 対象クラス: `Employee`
- 役割:
  - アプリケーション内で扱う従業員データ構造の定義
  - `employees` テーブルとのマッピング（JPA）

## 3. 依存関係ルール
- 現行実装の依存方向は `Controller -> Service -> Repository` で統一されている。
- 本設計では上記を必須ルールとして定義する。
- 禁止事項:
  - Repository から Service/Controller への依存（逆依存）
  - Service を経由せず Controller が Repository を直接呼び出す構成

## 4. 現状の横断設計
- 例外処理:
  - `getEmployeeById` で対象なしの場合は `RuntimeException` を送出する。
  - 共通例外ハンドラ（`@ControllerAdvice`）は未実装。
- 認証・認可:
  - 未実装。
- 永続化基盤:
  - DB は MySQL を使用。
  - ORM は Spring Data JPA / Hibernate。
