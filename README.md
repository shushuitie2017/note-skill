# note-writer

<p align="center">
  <img src="https://img.shields.io/badge/entries-131-blue?style=for-the-badge" alt="131 Entries">
  <img src="https://img.shields.io/badge/domains-8-purple?style=for-the-badge" alt="8 Domains">
  <img src="https://img.shields.io/badge/python-3.6+-yellow?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.6+">
  <a href="https://github.com/shushuitie2017/note-skill/blob/main/LICENSE"><img src="https://img.shields.io/github/license/shushuitie2017/note-skill?style=for-the-badge&color=green" alt="License"></a>
</p>

note.com / Zenn 向け記事執筆のライティングインテリジェンス Skill。14記事タイプ、25タイトル公式、25表現技法、5作家別文体を収録。8ドメインのCSVデータベースをBM25検索エンジンで横断検索可能。

## Features

| Domain | Entries | Description |
|--------|---------|-------------|
| `article-types` | 14 | 記事タイプ定義・特徴・目標スキ数 |
| `titles` | 25 | タイトル公式・パターン・例文 |
| `openings` | 19 | 書き出しパターン・フック技法 |
| `structures` | 13 | 記事構成テンプレート |
| `techniques` | 25 | 表現技法（自虐・比喩・対比・会話等） |
| `author-styles` | 5 | 作家別文体ガイド |
| `endings` | 15 | 結びパターン |
| `publishing` | 15 | 公開戦略・ハッシュタグ・スキ数予測 |

**Total: 131 entries / 8 domains**

### Author Styles

| Author | Core Concept |
|--------|-------------|
| 岸田奈美 | 100文字で済むことを2000文字で書く。悲劇を喜劇に変える力 |
| 椹野道流 | 日常を淡々と・一段落で流れるように。猫と母と仕事と健康 |
| さすらい | ツッコミ一人称スタイル。日常からの気付きと観察眼 |
| IT告白者 | 加害者側から語る。業界インサイダーの率直な告白 |
| Zennバズり著者 | 笑いと技術の同居。強烈なメタファーで複雑を簡単に |

## Installation

### Claude Code

```bash
# Clone into your project's skill directory
git clone https://github.com/shushuitie2017/note-skill.git .claude/skills/note-writer
```

Or manually copy the `.claude/skills/note-writer/` directory into your project.

## Usage

### Search Commands

```bash
# List all domains
python .claude/skills/note-writer/scripts/search.py --domains

# Search a specific domain
python .claude/skills/note-writer/scripts/search.py "IT 告白 タイトル" --domain titles

# Auto-detect domain
python .claude/skills/note-writer/scripts/search.py "岸田奈美 エッセイ 書き方"

# Cross-domain search
python .claude/skills/note-writer/scripts/search.py "自虐 ユーモア" --overview

# JSON output
python .claude/skills/note-writer/scripts/search.py "ハッシュタグ 投稿時間" --json
```

### Workflow

```
Step 1: 記事タイプを決める
  python search.py "[素材のキーワード]" --domain article-types
    ↓
Step 2: タイトルを作成する
  python search.py "[記事タイプ] タイトル" --domain titles
    ↓
Step 3: 構成を設計する
  python search.py "[記事タイプ] 構成" --domain structures
    ↓
Step 4: 表現技法を適用する
  python search.py "[技法名]" --domain techniques
    ↓
Step 5: 公開準備
  python search.py "スキ数 予測" --domain publishing
```

### Article Type Selection Flow

```
素材は何？
├── 深刻な個人体験 → ファン感情系（5,000-10,000スキ）
├── 業界の内部事情 → IT告白懺悔系（5,000-10,000スキ）
├── 専門知識・分析 → 専門インサイト系（2,000-5,000スキ）
├── キャリアの警告 → キャリア警告系（2,000-4,000スキ）
├── 問題解決方法 → ハウツー実用系（2,000-4,000スキ）
├── エラー解決記録 → トラブルシューティング系（2,000-5,000スキ）
├── AI/DXの考察 → AI DX論考系（2,000-6,000スキ）
├── 日常の小さな出来事 → エッセイ系・岸田奈美式（10,000+スキ）
├── 日常の淡々とした記録 → 日記系・椹野道流式（500-2,000スキ）
├── ツール比較・紹介 → ツールまとめ系（2,000-5,000スキ）
├── 技術プロジェクト → Zenn技術記事系（100-1,000いいね）
└── 社会現象・文化批評 → 社会評論系（2,000-3,500スキ）
```

### Title Formula Quick Reference

| Article Type | Formula | Example |
|-------------|---------|---------|
| IT告白系 | [対象者]の皆様、[問題]を[動詞]のは、私です | 御社SaaS導入を止めていたのは、私です |
| 逆説警告系 | [行為]するな | プログラミングが好きな人は来るな |
| 岸田奈美式 | [深刻な状況]+[意外な比喩] | 母は赤べこになった |
| 椹野道流式 | たぶん誰も読まない日記（[キーワード]） | たぶん誰も読まない日記（カレー） |
| Zennバズり | [ツール]で[成果]を作ったら[予想外]になった | AI部下10人を作ったら切腹ルールを追加 |

## Tech Stack

- **Search Engine**: BM25 (TF-IDF variant with document length normalization)
- **Data**: 8 CSV databases, zero external dependencies
- **Language**: Python 3.6+
- **Platform**: Claude Code Skill

## Data Sources

Built from analysis of:
- note.com TOP 100 articles (2026年1月)
- 8 writing checklists (general, IT, IT-buzz, IT-confession, Zenn, 岸田奈美, 椹野道流, tool-roundup)
- 5 style analysis documents (岸田奈美, 椹野道流, さすらい, article rankings, writing guide)

## License

MIT
