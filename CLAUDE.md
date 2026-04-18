# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

note-writer is a writing intelligence skill for note.com and Zenn platforms. It provides searchable databases of article types, title formulas, opening patterns, structure templates, expression techniques, author styles, ending patterns, and publishing strategies.

## Search Command

```bash
python src/note-writer/scripts/search.py "<query>" --domain <domain> [-n <max_results>]
```

**Domain search:**
- `article-types` - 記事タイプ選択 (14 entries)
- `titles` - タイトル公式 (25 entries)
- `openings` - 書き出しパターン (19 entries)
- `structures` - 構成テンプレート (13 entries)
- `techniques` - 表現技法 (25 entries)
- `author-styles` - 作家別文体 (5 entries)
- `endings` - 結びパターン (15 entries)
- `publishing` - 公開戦略 (15 entries)

**Cross-domain search:**
```bash
python src/note-writer/scripts/search.py "<query>" --overview
```

**List all domains:**
```bash
python src/note-writer/scripts/search.py --domains
```

## Architecture

```
src/note-writer/                  # Source of Truth
├── SKILL.md                      # Skill guide (~280 lines)
├── data/                         # 8 CSV databases (131 entries total)
│   ├── article-types.csv         # 14 article type definitions
│   ├── titles.csv                # 25 title formulas
│   ├── openings.csv              # 19 opening patterns
│   ├── structures.csv            # 13 structure templates
│   ├── techniques.csv            # 25 expression techniques
│   ├── author-styles.csv         # 5 author style guides
│   ├── endings.csv               # 15 ending patterns
│   └── publishing.csv            # 15 publishing strategies
└── scripts/
    └── search.py                 # BM25 search engine (zero dependencies)

.claude/skills/note-writer/       # Claude Code skill (copy of src/)
```

## Prerequisites

Python 3.6+ (no external dependencies required)
