# NoExperiencePJ

<img width="1206" height="914" alt="スクリーンショット 2026-03-02 20 37 00" src="https://github.com/user-attachments/assets/22b53381-05b4-402e-82d5-7aff4cd26f1b" />

Web画面のUIは改善中です。

## 概要
`NoExperiencePJ` は、Spring Boot + Thymeleaf + MySQL を用いて作成した、従業員および派遣先企業を管理するWebアプリケーションです。  
従業員情報の一覧表示、登録、更新、削除に加え、一覧のページングとソート機能を実装しています。  
現在は、従業員と派遣先企業を紐づけて管理する業務システムとして要件定義・基本設計・詳細設計を整理しています。

本プロジェクトでは、画面実装だけでなく、要件定義・基本設計・詳細設計・運用手順のドキュメント整備も並行して進めています。

## 作成背景
Java / Spring Boot を用いたWebアプリケーション開発の基礎を、未経験学習者に学んでもらうことを目的として作成したプロジェクトです。  
MVC構成、Thymeleafによる画面描画、Spring Data JPAによるDB連携、Docker ComposeによるローカルDB構築、設計書作成までを一通り学習できる構成を用意し、今後の追加機能実装や改善課題へ展開できるようにしています。

## 主な機能
- 従業員一覧表示
- 従業員登録
- 従業員更新
- 従業員削除
- 従業員一覧のページング
- 従業員一覧のソート
- 派遣先企業一覧表示
- 派遣先企業登録
- 派遣先企業更新
- 派遣先企業削除
- 従業員と派遣先企業の紐づけ管理
- 管理画面UIの改善
- 将来拡張を想定した仮導線の配置
  - ログイン
  - 通知
  - レポート
  - 補助ナビゲーション

## 画面イメージ
### 従業員一覧画面
- 従業員一覧を表示
- 更新 / 削除ボタンを配置
- ページング、ソートに対応
- 所属する派遣先企業と従業員ステータスを表示
- ログインや通知などの仮導線を配置

### 従業員登録画面
- 従業員情報の入力フォーム
- 一覧画面へ戻る導線を配置
- 将来課題向けの仮ボタンを配置

### 従業員更新画面
- 既存従業員情報の更新フォーム
- 一覧画面へ戻る導線を配置
- 履歴表示など将来拡張向けの仮導線を配置

### 派遣先企業管理画面
- 現在は要件定義・設計書まで整理済み
- 今後、一覧・登録・更新・削除画面を実装予定

## 使用技術
- Java 17
- Spring Boot 3.0.4
- Spring MVC
- Thymeleaf
- Spring Data JPA
- Hibernate
- MySQL
- Maven
- Docker / Docker Compose

## システム構成
- クライアント: Webブラウザ
- アプリケーション: Spring Boot
- データベース: MySQL
- 実行環境:
  - Local PC 上で Spring Boot アプリケーションを起動
  - Docker Compose 上で MySQL コンテナを起動

詳細は以下を参照してください。  
- `docs/基本設計/システム全体構成図.md`
- `docs/基本設計/システム全体構成図.drawio`

<img width="1561" height="655" alt="スクリーンショット 2026-03-03 20 32 34" src="https://github.com/user-attachments/assets/da8a35b4-2ba6-41fe-b390-b9d5dfe8a2aa" />

## ディレクトリ構成
```text
src/
├─ main/
│  ├─ java/com/dev/raise/
│  │  ├─ controller/
│  │  ├─ model/
│  │  ├─ repository/
│  │  └─ service/
│  └─ resources/
│     ├─ static/css/
│     └─ templates/
└─ test/

docs/
├─ 要件定義
├─ 基本設計
├─ 詳細設計
└─ 運用・保守
```

## セットアップ手順
詳細手順は以下を参照してください。

- `docs/運用・保守/セットアップ手順.md`

## 起動方法
### 1. リポジトリをクローン
```bash
git clone https://github.com/kota-done/NoExperiencePJ.git
cd NoExperiencePJ
```

### 2. Docker 用の環境変数ファイルを作成
```bash
cp Docker_MySQL/.env.example Docker_MySQL/.env.local
```

### 3. `.env.local` を確認
```env
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=demo
```

### 4. Docker で MySQL を起動
```bash
cd Docker_MySQL
docker compose up --build -d
cd ..
```

### 5. `application.properties` を作成
`src/main/resources/application.properties` は `.gitignore` 対象のため、各自のローカル環境で作成してください。

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/demo?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
spring.jpa.hibernate.ddl-auto=validate
logging.level.org.hibernate.SQL=DEBUG
logging.level.org.hibernate.type=TRACE
```

### 6. Spring Boot アプリを起動
```bash
./mvnw spring-boot:run
```

### 7. ブラウザで確認
```text
http://localhost:8080
```

## 動作確認方法
- 一覧画面が表示されること
- 初期データが表示されること
- 従業員の登録、更新、削除ができること
- ページングとソートが動作すること
- 初期化SQLで派遣先企業テーブルと従業員テーブルが作成されること

## DB / Docker 利用方法
- DB は Docker Compose 上で起動する MySQL を利用します
- 接続情報はローカルの `application.properties` で管理します
- `3306` ポートが既に使用されている場合は、既存の MySQL を停止するか Docker 側のポートを変更する必要があります
- 初期化SQLは `Docker_MySQL/init/` 配下で管理しています
- 現在の初期化SQLは、`client_companies` と `employees` のテーブル作成および初期データ投入に対応しています

## 現在の制約・未実装事項
- 認証 / 認可未実装
- ログイン機能未実装
- 通知機能未実装
- レポート出力未実装
- 入力バリデーション未実装
- 共通例外ハンドリング未実装
- REST API 未実装
- 更新履歴 / 監査機能未実装
- 派遣先企業管理画面の実装は未着手
- 従業員ステータス / 企業取引ステータスは設計済みだが、実装はこれから
- 企業削除時の所属従業員チェックは設計済みだが、実装はこれから

## 今後の改善予定
- 派遣先企業管理画面の追加
- 従業員と派遣先企業の紐づけ実装
- 従業員ステータス管理の実装
- 企業取引ステータス管理の実装
- 企業削除制約の実装
- ログイン機能の追加
- 入力バリデーションの追加
- 共通例外処理の追加
- REST API の追加
- 更新履歴表示機能の追加
- CSV出力やレポート機能の追加
- UI の継続改善

## 設計書
設計ドキュメントは `docs/` 配下に整理しています。

- `docs/要件定義`
- `docs/基本設計`
- `docs/詳細設計`
- `docs/運用・保守`

## 学習ポイント
- Spring Boot による MVC 開発
- Thymeleaf による画面描画
- Spring Data JPA による永続化
- Docker Compose を用いたローカルDB環境構築
- 要件定義から詳細設計までのドキュメント整理
- 既存画面のUI改善
- 従業員と派遣先企業を扱う業務要件への拡張検討

## 補足
本プロジェクトは既存の学習用サンプルを参考にしつつ、要件定義・設計・UI・運用資料を含めて再整理し、社内育成向けの学習教材として活用できる形へ改善を進めています。
