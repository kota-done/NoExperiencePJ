# 全体ルール

## 1. 目的
- 本設計書は、従業員管理画面の構造・責務・品質ルールを定義することを目的とする。

## 2. 対象範囲
- 本リポジトリの Spring Boot バックエンドおよび Thymeleaf 画面

## 3. 非対象
- インフラ構築手順
- CI/CD 詳細設定

## 4. 用語
| 用語 | 意味 |
|------|------|
| 機能 | 画面上で利用者が実行する処理単位 |
| レイヤ | Controller / Service / Repository / Model の責務単位 |

## 5. 命名規則
- Controller: `XXXController`
- Service: `XXXService` / `XXXServiceImpl`
- Repository: `XXXRepository`
- Entity: `XXX`

## 6. 設計規約
- Controller は業務処理・永続化処理を直接実装しない。
- Service は業務処理と Repository 呼び出しの集約を担当する。
- Repository は Entity の永続化操作のみに責務を限定する。
- 依存方向は `Controller -> Service -> Repository` を必須とする。

## 7. コーディング規約
- 取得結果なしの扱いは呼び出し元に伝わる形で明示する。
- ログレベルは INFO/WARN/ERROR を使い分ける。
- 例外文言は利用者影響を判別できる内容にする。

## 8. ドキュメント更新ルール
- 機能を追加・変更した場合は `docs/features.md` と該当 `docs/basic-design/` を更新する。
- `docs/class-design.generated.md` は自動生成想定ファイルのため手動編集しない。
- 手動補足は `docs/class-design-notes.md` に記載する。
