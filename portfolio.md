# Todo API

学習内容を実務へつなげるため、Todo APIで確認した事実と改善タスクを管理する。

## プロジェクト

| 項目 | 内容 |
|---|---|
| リポジトリ | https://github.com/shunshiratori/task-manager |
| 技術スタック | Java、Spring Boot |
| 目的 | 面接で設計・実装を説明できるバックエンドAPIにする |

## 現在の改善

現在はなし。

第3回に対応するコード確認は今回はスキップした（2026-09-09）。必要になった時点で、ServiceとRepositoryの依存関係、トランザクション境界、所有者確認を確認する。

Todo APIを副業案件で提示する主な成果物へ育てる方針とする（2026-09-10）。改善作業は学習サイクルと分け、別Issueで実施する。現状はセキュリティ上の問題があるため、そのまま案件へ提示せず、下記の最優先改善を完了してから公開品質を再評価する。

> 同時に進行中にできる改善は1件だけ。着手するときは、バックログからここへ移す。

## 改善バックログ

| 優先度 | タスク | 学習との関連 | 状態 |
|---|---|---|---|
| 最優先 | パスワードを平文保存・直接比較せず、Spring SecurityのPasswordEncoderでハッシュ化・照合する | 認証・パスワード保存 | 未着手 |
| 最優先 | JWT秘密鍵をソースコードから環境変数へ移し、未認証・不正トークンを適切な401として処理する | JWT・秘密情報管理 | 未着手 |
| 最優先 | Taskの取得・更新・削除を認証ユーザーの`userId`で制限し、リクエストの`userId`を信用しない | 認可・IDOR対策 | 未着手 |
| 高 | 正常時・異常時のHTTPステータスコードをAPIごとに整理 | 400、401、403、404の使い分け | 未着手 |
| 高 | `@RestControllerAdvice`でエラーレスポンスを統一 | バリデーション・想定外例外の扱い | 未着手 |
| 高 | Todoの未存在・未認証・権限不足を区別して返す | HTTPステータスコード | 未着手 |
| 高 | DTO導入の理由をREADMEに記載 | DTOを使う理由 | 未着手 |
| 高 | Service層の責務を整理 | Service層を分ける理由 | 未着手 |
| 中 | 独自Filter中心のJWT認証をSpring Securityへ統合し、選定理由をREADMEへ記載 | 認証・認可 | 未着手 |
| 中 | READMEへアーキテクチャ図・セットアップ・API一覧を追加 | 面接で成果物を説明する | 未着手 |
| 中 | DockerfileとComposeを追加して動作確認する | 開発環境の再現性 | 未着手 |
| 中 | 一部更新の要件があればPATCHを追加 | PUTとPATCHの違い | 未着手 |
| 中 | タグや権限に重複を許さない場合はSetの利用を検討 | ListとSetの使い分け | 未着手 |

## コード確認

### 初回評価（2026-09-10）

- 案件向け成果物として育てる題材には適している。Java・Spring Boot、REST API、JPA、DTO、JWT、Service単体テストを説明材料にできる
- 現状のまま提示する品質ではない。平文パスワード、ハードコードされたJWT秘密鍵、Task単体取得・更新・削除の所有者確認不足を先に修正する
- READMEには設計意図がある一方、PostgreSQLとMySQLの記述、Java 17とコンパイラ設定8など、実装・設定との不一致を解消する必要がある
- `contoroller`、`ResourceNotFountException`、`Util`などの命名を修正し、空のテストと異常系テストを整備する
- 最優先改善後に、Docker、CI、API実行例、構成図、デモ環境を追加すると案件で確認しやすい成果物になる

### アーキテクチャ

```text
Client → Controller → Service → Repository → DB
```

| レイヤー | 代表クラス | 入力 | 主な責務 | 出力・依存先 |
|---|---|---|---|---|
| Controller | `TaskController` | HTTPリクエスト | タスクAPIの受付とService呼び出し | `TasksService` |
| Service | `TasksService` | DTO・ID | タスクの作成・取得・更新・削除、DTO変換、トランザクション | 各Repository |
| Repository | `TaskRepository`ほか | Entity・検索条件 | Spring Data JPAによるデータアクセス | DB |

`AuthController`が`UserRepository`へ直接依存しているため、現状は全Controllerでレイヤー分離が統一されているわけではない。

### 確認観点

- [ ] ControllerはHTTPの入出力とバリデーションに集中している
- [ ] Serviceにユースケース・トランザクション境界がまとまっている
- [ ] Repositoryはデータアクセスに集中している
- [ ] EntityをAPIの入出力として直接公開していない
- [ ] 依存方向が`Controller → Service → Repository`になっている

## 完了した改善

まだなし。

改善完了時は、実装内容・確認方法・面接での説明をここへ記録する。
