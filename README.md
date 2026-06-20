# prc-digitalschool-ds

デジスク研修 DS実践コース「PPH売上向上分析」解答例リポジトリ

## 概要

本リポジトリは、DS実践コース研修の**講師用解答例**を管理・共有するためのものです。

研修では、コニカミノルタ PPH（プロフェッショナル印刷事業）の売上向上をテーマに、以下のステップを受講者に体験してもらいます。

1. **ビジネス理解 & ロジックツリー作成** — PPH事業の構造を理解し、売上向上の打ち手を分解する
2. **分析チュートリアル** — 重回帰分析・ランダムフォレスト等の手法をハンズオンで学ぶ
3. **自由分析** — 受講者が自らデータを探索し、施策提案を組み立てる
4. **発表** — 「○○の施策を○○向けに打つことで○○円の効果が出る」を提示する

受講者発表ののち、本リポジトリの内容を解答例として共有します。

## ディレクトリ構成

```
prc-digitalschool-ds/
├── docs/                  # 背景理解資料
│   ├── ビジネス理解_事前資料_PPH.md
│   └── ビジネス理解_ロジックツリー解答例_PPH.md
├── inputs/                # 分析用データ
│   ├── master/            # マスタデータ (product, option, option_price)
│   ├── meta/              # メタデータ (月次)
│   ├── option/            # オプションデータ (月次)
│   └── 仕様書/            # データ仕様書, FAQ
├── notebooks/             # 分析チュートリアル
│   ├── Notebook_重回帰分析やってみよう.ipynb
│   └── Notebook_RandomForestやってみよう.ipynb
├── main.py                # エントリーポイント
├── pyproject.toml         # 依存関係定義
├── CLAUDE.md              # Claude Code設定ガイド
└── .claude/               # Claude Code プロジェクト設定
```

## セットアップ

### 前提条件

- Python 3.11.8
- [uv](https://docs.astral.sh/uv/) パッケージマネージャー

### 手順

```bash
git clone https://github.com/Yuki-Shinohara-BAG/prc-digitalschool-ds.git
cd prc-digitalschool-ds
uv python install 3.11.8
uv python pin 3.11.8
uv sync
```

### 動作確認

```bash
uv run python main.py
```

### Jupyter Lab 起動

```bash
uv run jupyter lab --no-browser
```

## 研修の流れ

| 日程 | 内容 | 関連資料 |
|------|------|----------|
| 1日目PM | ビジネス理解 + ロジックツリーワーク | `docs/` |
| 2日目AM | データ理解 + 分析チュートリアル | `notebooks/`, `inputs/` |
| 2日目PM〜3日目AM | 自由分析・グループワーク | `inputs/` |
| 3日目PM | 発表 + 解答例共有 | 本リポジトリ全体 |

## 技術スタック

- **パッケージ管理**: uv
- **分析ライブラリ**: pandas, numpy, scikit-learn, matplotlib, seaborn
- **Notebook**: Jupyter Lab
- **コード品質**: ruff (linter/formatter)
