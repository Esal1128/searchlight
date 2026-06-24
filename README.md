# 🔦 Searchlight

> 情報の海から、必要なものだけを照らす。
> **Gemini で収集 → Claude で検証 → Obsidian に保存** する、リサーチ支援アプリ。

[**▶ デモを見る**](https://esal1128.github.io/searchlight/)（フロントのUI／画面遷移のみ動作）

---

## これは何

リサーチを 3 段のパイプラインで支援するツールです。各 AI の得意分野で役割分担し、低コストで「深く・正確な」リサーチ結果をノートとして蓄積します。

```
① 収集 (Gemini)  →  ② 整形・検証 (Claude)  →  ③ ノート化 (Obsidian)
   情報を広く集める      事実を検証・構造化         vault に保存
```

- **鮮度は Gemini**：Deep Research で情報を広く収集
- **正確さは Claude**：根拠の薄い主張を検証・是正し、構造化
- **蓄積は Obsidian**：検証済みノートを vault に保存して再利用

## 主な機能

- テーマを入力 → リサーチ結果を「要点ハイライト / 概要 / 主なポイント / 参照ソース」に整形
- 検証済みノートの一覧・閲覧（ノート / 履歴）
- エンジン連携・リサーチ設定の管理（設定）
- ライト / ダークテーマ切り替え
- レスポンシブ対応（PC / タブレット / スマホ）

## 構成

```
.
├── frontend/        # 静的フロント（HTML 1枚 / CSS / JS）
│   └── index.html
└── backend/         # FastAPI（Claude 検証 + Obsidian 書き出し）
    ├── main.py
    └── .env         # APIキー・vaultパス（リポジトリには含めない）
```

## 技術

- **フロント**：HTML / CSS / Vanilla JS（外部ビルドなし）
- **バックエンド**：Python / FastAPI / Uvicorn
- **AI**：Anthropic Claude（整形・検証）、Google Gemini（収集）
- **保存先**：Obsidian vault（Markdown）

## ローカルでの起動

### バックエンド

```bash
cd backend
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
# .env を用意（ANTHROPIC_API_KEY / CLAUDE_MODEL / VAULT_PATH など）
uvicorn main:app --reload --port 8000
```

API ドキュメント：<http://localhost:8000/docs>

### フロント

```bash
cd frontend
python -m http.server 5500
# http://localhost:5500 を開く
```

## 現在のステータス

- ✅ フロント UI / 画面遷移（デモ公開中）
- ✅ バックエンド：リサーチ → Claude 検証 → Obsidian 保存（ローカルで動作）
- 🚧 フロントとバックエンドの接続（配線中）

> 公開デモはフロントのみのため、「リサーチ開始」などの実機能はローカル環境でのみ動作します。

## ライセンス

個人プロジェクト（Personal project）
