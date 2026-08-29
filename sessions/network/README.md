# ネットワーク問題演習

Webエンジニアに必要なネットワーク知識を、暗記ではなく、説明・通信フロー・障害切り分け・実機確認を通して身につける。

## ゴール

- URL入力から画面表示までを、DNS、IP、Routing、TCP、Port、TLS、HTTP、Server、Responseのつながりとして説明できる
- Webサービスへアクセスできないとき、DNS、疎通、TCP、TLS、HTTP、Applicationの順に切り分けられる
- 重要テーマであるDNS、TCP、HTTP/HTTPS、Port、IP、TLSをLevel 4程度まで上げる

## 進め方

1. 一度に5問だけ出題する
2. 資料を見ず、自分の言葉で回答する
3. 回答を採点し、理解できている点・不足・誤解・追加質問・Levelを記録する
4. 追加質問1〜3問への回答が終わったら、その問題を完了とする
5. 理解不足なら次の番号で補強問題を出し、十分なら次のテーマへ進む

最初の問題は[001〜005](001-005.md)。問題番号は今後も通し番号で管理する。

今後作成する問題もこのディレクトリへ保存する。原則として5問ごとに `006-010.md`、`011-015.md` のようなファイルを追加する。理解不足を補う追加問題も通し番号に含め、元の問題の採点欄からリンクする。

## 問題の段階

| 段階 | 確認すること | 主な出題形式 |
|---|---|---|
| 1 | 用語を目的や必要性まで説明できる | 説明、なぜ、もし〜なら、比較 |
| 2 | 複数技術を順序と理由を含めて説明できる | 通信フロー |
| 3 | レイヤーを意識して原因を切り分けられる | 障害調査、コマンド |
| 4 | 実環境で通信を確認・再現できる | Docker、curl、dig、tcpdump、ss |

## 理解度 Level

| Level | 状態 |
|---|---|
| 0 | 知らない |
| 1 | 聞いたことがあり、簡単な定義を説明できる |
| 2 | なぜ必要かまで説明できる |
| 3 | 他のネットワーク技術との関係を説明できる |
| 4 | 障害発生時に調査・切り分けできる |
| 5 | 実環境で確認・再現でき、人に説明できる |

すべてをLevel 5にすることは目標にしない。実務上の優先度に応じて必要なLevelを目指す。

## 採点形式

各回答を5点満点で採点し、次の形式で記録する。正誤だけで完了にしない。

```text
評価: X / 5

正しく理解している部分:
- ...

不足している知識:
- ...

誤解している部分:
- ...

追加質問:
- ...

理解度: Level X
```

回答が正しくても、暗記ではなく理解できているかを確かめる追加質問を1〜3問出す。

## 学習順序

1. 基礎: IP、Private/Public IP、IPv4、Subnet、Default Gateway、Router、Port、DNS、TCP、UDP
2. Web通信: HTTP/HTTPS、Request/Response、Method、Status Code、Header、Cookie、TCP Connection、TLS、証明書
3. 実務: NAT、Firewall、Load Balancer、Proxy、Reverse Proxy、CDN、Docker Network、localhost、0.0.0.0、代表的な障害
4. AWSへの接続: VPC、Subnet、Route Table、Internet Gateway、NAT Gateway、Security Group、Load Balancer、Public/Private Subnet

AWS固有用語は単独で暗記せず、基礎ネットワークのどの仕組みに対応するかを確認する。

## 理解度記録

| テーマ | 現在Level | 根拠 | 次の確認 |
|---|---:|---|---|
| IPアドレス | 0 | 未回答 | 001 |
| Private IP / Public IP | 0 | 未回答 | 002 |
| Subnet | 0 | 未回答 | 003 |
| Default Gateway / Router | 0 | 未回答 | 004 |
| Port | 0 | 未回答 | 005 |
| DNS | 0 | 未出題 | 今後出題 |
| TCP / UDP | 0 | 未出題 | 今後出題 |
| HTTP / HTTPS | 0 | ネットワーク演習では未確認 | 今後出題 |
| TLS / SSL証明書 | 0 | 未出題 | 今後出題 |
