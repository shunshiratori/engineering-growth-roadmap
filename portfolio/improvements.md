# Improvements

面接の質問がそのまま改善タスクになる。完了したらチェックを入れ、Todo API リポジトリも更新する。

## 完了済み

<!-- 完了した改善をここに移動 -->

## 進行中

### レイヤー責務の棚卸し

- [ ] Controller / Service / Repository の代表クラスを確認
- [ ] 各レイヤーの責務を `todo-api-review.md` に記録
- [ ] Controller に業務ロジックが漏れていないか確認
- [ ] 面接で設計意図を説明できる状態にする

### JWT 追加

- [ ] 実装
- [ ] README 更新
- [ ] 面接で説明できる状態にする

### README 更新

- [ ] アーキテクチャ図
- [ ] セットアップ手順
- [ ] API エンドポイント一覧

### Docker 対応

- [ ] Dockerfile
- [ ] docker-compose.yml
- [ ] ローカルで動作確認

## バックログ（面接から発生）

| 優先度 | タスク | きっかけになった質問 | 状態 |
|---|---|---|---|
| 高 | DTO 導入の理由を README に記載 | DTO を使う理由 | 未着手 |
| 高 | Service 層の責務を整理 | Service 層を分ける理由 | 進行中 |
| 中 | JWT 選定理由をドキュメント化 | JWT を選んだ理由 | 未着手 |

## 改善 → ドキュメント更新フロー

```
面接で質問される
  ↓
答えられない / 説明が弱い
  ↓
improvements.md にタスク追加
  ↓
Todo API に実装
  ↓
todo-api-review.md を更新
  ↓
interview/*.md の「実務で使った例」を追記
```
