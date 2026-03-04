# AEO Checker

AI検索対策チェッカー。URLを入力するだけでAI検索エンジン（ChatGPT、Perplexity、Claude等）での発見されやすさを100点満点でスコアリング。

## 技術スタック

- Next.js 16 (App Router)
- TypeScript (strict)
- Tailwind CSS v4
- shadcn/ui
- Cheerio (HTMLパース)

## セットアップ

```bash
npm install
npm run dev
```

http://localhost:3000 で起動。

## ページ構成

| パス | 説明 |
|------|------|
| `/` | トップページ: URL入力フォーム |
| `/result/[id]` | スキャン結果: スコア + 改善提案 |
| `/guides/*` | 7つのAEO対策ガイド |

## API

| エンドポイント | メソッド | 説明 |
|---------------|---------|------|
| `/api/scan` | POST | URLスキャン実行 |
| `/api/result/[id]` | GET | 結果取得 |
| `/api/generate` | POST | llms.txt/robots.txt生成 |
| `/api/mcp` | POST | MCP Server (JSON-RPC 2.0) |

## スコアリング (100点満点)

| カテゴリ | 配点 |
|----------|------|
| llms.txt | 15点 |
| robots.txt AI対応 | 15点 |
| 構造化データ | 15点 |
| メタタグ | 15点 |
| コンテンツ構造 | 15点 |
| 内部リンク | 15点 |
| 技術的要素 | 10点 |

## AI公開チャネル

- `/llms.txt` - AI向けサイト説明
- `/.well-known/agent.json` - A2A Agent Card
- `/robots.txt` - AIクローラー許可設定
- `/api/mcp` - MCP Server エンドポイント

## デプロイ

```bash
npm run build
```

Vercel にデプロイ。ドメイン: `aeo.ezoai.jp`
