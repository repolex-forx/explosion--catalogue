# Repolex Knowledge Graph of explosion/catalogue

RDF knowledge graph data for [explosion/catalogue](https://github.com/explosion/catalogue), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download explosion/catalogue
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4c815128eb73a4ecc54080d29810d080b2139ab8
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4c815128eb73a4ecc54080d29810d080b2139ab8
│           └── chunk-001.nq.gz
├── blob
│   ├── 1aba38f67a2211cf5b09466d7b411206cb7223bf.nq.gz
│   ├── 3077e40908d8c7d6e30d11f3a9e6f5f4d0b8a8ac.nq.gz
│   ├── 32490bdc27ec9460823441885d57d0f7b0aad78f.nq.gz
│   ├── 347ead66ab2a8b2ae2708a422f0b68eaa7368b5c.nq.gz
│   ├── 37f77c60f9236be556499225f09cb67c00eb4795.nq.gz
│   ├── a9626f6fe7eb450e38d3f012ed27fa6e2d9ddea1.nq.gz
│   ├── b82ffd6eb8681d8418583328a0074e9408028b37.nq.gz
│   ├── b8ee9273e6dc522275f1b958f6c322d3fc0801af.nq.gz
│   ├── be7e092b0b050da7385b1a5f1670f4c134cfa168.nq.gz
│   ├── e1129debea73d5e109f6b85e042e163d732d6a78.nq.gz
│   ├── e53ebf29217c4eecfd3fe47d3eb2e09a1091812e.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e87c7a95ade2beaf8f1e07b95df56e8ebaba76a9.nq.gz
│   ├── ea4317b11b8bb629b0041e3c0330ffa33f55ee25.nq.gz
│   └── f9c4a59eae550adc773a2a789d70d668aa54a81e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4c815128eb73a4ecc54080d29810d080b2139ab8.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 23 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[explosion/catalogue](https://github.com/explosion/catalogue)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
