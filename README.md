# NoExperiencePJ
<img width="1206" height="914" alt="スクリーンショット 2026-03-02 20 37 00" src="https://github.com/user-attachments/assets/22b53381-05b4-402e-82d5-7aff4cd26f1b" />
Web画面のUIは改善中

## 概要
`NoExperiencePJ` は、Spring Boot + Thymeleaf + MySQL を用いて作成した従業員管理Webアプリケーション。  
従業員情報の一覧表示、登録、更新、削除に加えて、一覧のページングとソート機能を実装。

本プロジェクトでは、画面実装だけでなく、要件定義・基本設計・詳細設計・運用手順のドキュメント整備も並行


## 作成背景
Java / Spring Boot を用いたWebアプリケーション開発の基礎を未経験学習者に学んでもらうことを目的に作成したプロジェクト。  
MVC構成、Thymeleafによる画面描画、Spring Data JPAによるDB連携、Docker ComposeによるローカルDB構築、設計書作成までを一通りこちらで用意し、追加機能を。

## 主な機能
- 従業員一覧表示
- 従業員登録
- 従業員更新
- 従業員削除
- 一覧のページング
- 一覧のソート
- 管理画面UIの改善
- 将来拡張を想定した仮導線の配置
  - ログイン
  - 通知
  - レポート
  - 補助ナビゲーション

## 画面イメージ
### 一覧画面
- 従業員一覧を表示
- 更新 / 削除ボタンを配置
- ページング、ソートに対応
- ログインや通知などの仮導線を配置

### 登録画面
- 従業員情報の入力フォーム
- 一覧画面へ戻る導線を配置
- 将来課題向けの仮ボタンを配置

### 更新画面
- 既存従業員情報の更新フォーム
- 一覧画面へ戻る導線を配置
- 履歴表示など将来拡張向けの仮導線を配置

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

## DB / Docker 利用方法
- DB は Docker Compose 上で起動する MySQL を利用します
- 接続情報はローカルの `application.properties` で管理します
- `3306` ポートが既に使用されている場合は、既存の MySQL を停止するか Docker 側のポートを変更する必要があります

## 現在の制約・未実装事項
- 認証 / 認可未実装
- ログイン機能未実装
- 通知機能未実装
- レポート出力未実装
- 入力バリデーション未実装
- 共通例外ハンドリング未実装
- REST API 未実装
- 更新履歴 / 監査機能未実装

## 今後の改善予定
- ログイン機能の追加
- 入力バリデーションの追加
- 共通例外処理の追加
- REST API の追加
- 更新履歴表示機能の追加
- CSV出力やレポート機能の追加
- UI の継続改善

## 設計書
設計ドキュメントは `docs/` 配下に整理

- `docs/要件定義`
- `docs/基本設計`
- `docs/詳細設計`
- `docs/運用・保守`

## 学習ポイント
- Spring Boot による MVC 開発
- Thymeleaf による画面描画
- Spring Data JPA による永続化
- Docker Compose を用いたローカルDB環境構築
- 設計書の分類整理と運用
- 既存画面のUI改善

## 参考サイトおよびプロジェクト
### Tutorial - Spring Boot CRUD Web Application with Thymeleaf, Spring MVC, Spring Data JPA, Hibernate, MySQL
https://www.javaguides.net/2020/05/spring-boot-crud-web-application-with-thymeleaf.html

### YouTube Video - Spring Boot CRUD Web Application with Thymeleaf, Spring MVC, Spring Data JPA, Hibernate, MySQL
https://youtu.be/_5sAmaRJd2c

### Tutorial - Pagination and Sorting with Spring Boot, ThymeLeaf, Spring Data JPA, Hibernate, MySQL
https://www.javaguides.net/2020/06/pagination-and-sorting-with-spring-boot-thymeleaf-spring-data-jpa-hibernate-mysql.html

### YouTube Video  - Pagination and Sorting with Spring Boot, ThymeLeaf, Spring Data JPA, Hibernate, MySQL
=> https://youtu.be/Aie8n12EFQc
