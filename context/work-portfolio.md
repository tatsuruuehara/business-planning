# 実績ポートフォリオ（2026年5月時点）

## 現在の業務委託先

BPG（ブランドポートグループ）— EC特化のホールディングス
- CARDS（株式会社cards）— 楽天・Amazon EC運用
- XICO（株式会社xico）
- HM（株式会社HM）— HUGH-MORGAN / SHIROE / VANILLA-WORKS
- FUUZ（株式会社FUUZ）— GINZA-HANACHA / 百福堂 / CHEF-NUMA

## 担当クライアント（楽天EC直接運用: 13店舗）

| 店舗 | 月商目標 | 自動化レベル |
|------|----------|-------------|
| 百福堂（Hyakufukudo） | ¥8,000,000 | 日次データ収集+月次Slidesレポート自動生成 |
| 関西酵素（Kansaikoso） | ¥5,000,000 | 日次データ収集+月次レポート（テンプレ構築中） |
| Her lip to BEAUTY | ¥7,000,000 | 日次更新+7タブダッシュボード |
| ベルーナ / 常総市 / リポC / ROSIER / LIENA / EZOBOLIC / nelse / ラブクロム / YUNOW / 和牛セレブ / KATAN | — | ECコンサルエージェント経由 |

## 構築した主要システム

### 1. 月次スライドレポート自動生成パイプライン
- Google Sheets → Claude API（4エージェント協調: 店舗分析→データ分析→レポート生成→品質チェック）→ Google Slides API → Slack通知
- ゼロタッチで月次経営レポートが生成される
- 技術: Node.js, Cloud Functions, Cloud Scheduler, Slides API直接描画（PptxGenJS不使用）

### 2. 楽天EC多店舗ダッシュボード
- 13店舗の売上・アクセス・CVR・広告データを日次自動収集
- GitHub Pagesでホスティング、店舗別HTMLダッシュボード
- BigQueryに受注データをウェアハウス化
- Cloud Scheduler（3ジョブ/店舗: RPP日次、広告日次、受注日次）

### 3. 競合リサーチ・戦略立案エージェント
- 楽天版: 9フェーズ（Sellersprite API、VOC分析、KWリサーチ、Geminiレビュー、鬼猿川壁打ち）
- Amazon版: Phase 0-9 商品リサーチパイプライン
- Geminiによる「鬼猿川」ペルソナでの提案検証（Devil's Advocate）

### 4. ECコンサルエージェント（Tool-Use型）
- 13店舗対応のマルチテナント設計
- Notionコメントからの人間フィードバックを自動ルール化（継続学習）
- 楽天運用マニュアル・RPP設定SOPをナレッジベース化

### 5. コンテンツ配信システム
- X自動投稿（猿川ペルソナ、Obsidian参照、Sheets記録）
- note.com記事生成（4役割編集チーム）
- コンテンツリパーパシング（note → Xスレッド → ショート動画 → LPコピー）

### 6. 社内オペレーション自動化
- アクショントラッカー（毎朝6:30、前日の会議/Slackを自動要約）
- CXOブリーフィング（Notion横断の経営サマリー）
- 違和感レーダー（数字GAP/約束未履行/NGライン抵触/論理飛躍の自動検出）

## 技術スタック

### AI/LLM
- Anthropic Claude API（claude-sonnet-4系）— レポート分析、エージェント基盤
- Google Gemini API（2.5-flash）— 壁打ち検証、戦略評価

### Google Cloud
- Sheets API v4 / Slides API / Calendar API / Drive API
- Cloud Functions（Node.js 22, 540s timeout, 1GB）
- Cloud Scheduler / Secret Manager / BigQuery
- OAuth2 + Service Account認証

### 楽天API
- RMS WEB API（RPP広告、ショップデータ、商品、受注、クーポン検索）

### その他
- Notion API（フィードバック収集、ナレッジベース）
- Slack Bolt/SDK（通知、エージェントbot）
- GitHub Pages（ダッシュボードホスティング）
- Cloud Run（Slackbot本番運用）

## スケール指標

- **エージェント数**: 20体（L1機能別6 + L2統合1 + L3秘書/通信4 + 企業別9）
- **スキル数**: 43個（レポート、リサーチ、コンテンツ、デザイン、オペレーション）
- **管理店舗数**: 13店舗（日次データパイプライン稼働）
- **構築期間**: 約6週間（2026年4月23日〜5月17日、日次イテレーション）

## ドメイン知見

### 楽天EC運用
- RPP広告最適化（キーワード別入札、ROAS管理）
- CVR改善施策（商品画像、レビュー誘導、イベント連動）
- 売上ロジックツリー（アクセス×購入率×客単価の因数分解）
- 月商500万〜800万円規模の店舗運用ノウハウ

### AI業務自動化
- 経営者の抽象的アイデア → 実装可能な仕様への翻訳
- マルチエージェント協調設計（4エージェントパイプライン）
- 人間フィードバックからの自動ルール学習
- ゼロタッチレポーティング（完全無人化）

### クライアントが実際に払っている対価
- EC運用コンサルティング（月額固定）
- 月次レポート作成（従来は人力で半日〜1日）
- 競合調査・戦略立案（従来は外注で数十万円/回）
- ダッシュボード構築・運用（従来はBIツール+設定工数）
