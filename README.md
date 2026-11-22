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
│   │   ├── 4c815128eb73a4ecc54080d29810d080b2139ab8
│   │   │   └── chunk-001.nq.gz
│   │   └── e5fe944127cab62472a9657f0a5bb232e0303fc8
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── e5fe944127cab62472a9657f0a5bb232e0303fc8.nq.gz
│   └── repolex
│       ├── 4c815128eb73a4ecc54080d29810d080b2139ab8
│       │   └── chunk-001.nq.gz
│       └── e5fe944127cab62472a9657f0a5bb232e0303fc8
│           └── chunk-001.nq.gz
├── blob
│   ├── 131fd9236684f5164a5cf70629983d99bfc3a1f6.nq.gz
│   ├── 1aba38f67a2211cf5b09466d7b411206cb7223bf.nq.gz
│   ├── 27c9ec622ac08b8d9d1e29fcc1cea3e8afa783b0.nq.gz
│   ├── 3077e40908d8c7d6e30d11f3a9e6f5f4d0b8a8ac.nq.gz
│   ├── 32490bdc27ec9460823441885d57d0f7b0aad78f.nq.gz
│   ├── 330f2934a70040c13a2475fe4a22b8ddaa4d90c3.nq.gz
│   ├── 347ead66ab2a8b2ae2708a422f0b68eaa7368b5c.nq.gz
│   ├── 37f77c60f9236be556499225f09cb67c00eb4795.nq.gz
│   ├── 4914a026b53b31448575396e1e6d6595ae911218.nq.gz
│   ├── 4e60d185039599c2f9a7307e6a30a0b8d7988e0d.nq.gz
│   ├── 4ea60263b2a3f4e00ff4da09870436a343c22be9.nq.gz
│   ├── 7032c24a7f407c718ae320f395472a41f185e394.nq.gz
│   ├── 71b2a33b8121b276ff1a88e5f951ddb653ce724f.nq.gz
│   ├── 759b3da21604c54b3accb12fd45cfa29394e24ff.nq.gz
│   ├── a3c188e7af56a45ff43b500224c2a442ee713bae.nq.gz
│   ├── a9626f6fe7eb450e38d3f012ed27fa6e2d9ddea1.nq.gz
│   ├── b82ffd6eb8681d8418583328a0074e9408028b37.nq.gz
│   ├── b8ee9273e6dc522275f1b958f6c322d3fc0801af.nq.gz
│   ├── be7e092b0b050da7385b1a5f1670f4c134cfa168.nq.gz
│   ├── c9da8751fb82196b1b355ed47fd84f731c8e1868.nq.gz
│   ├── e1129debea73d5e109f6b85e042e163d732d6a78.nq.gz
│   ├── e416bb11fdb23c53bccab9564837217811eee2dc.nq.gz
│   ├── e53ebf29217c4eecfd3fe47d3eb2e09a1091812e.nq.gz
│   ├── e5e2c758b382e3fab4f669e4593ae45517e42d0d.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e87c7a95ade2beaf8f1e07b95df56e8ebaba76a9.nq.gz
│   ├── ea4317b11b8bb629b0041e3c0330ffa33f55ee25.nq.gz
│   └── f9c4a59eae550adc773a2a789d70d668aa54a81e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── e5fe944127cab62472a9657f0a5bb232e0303fc8.nq.gz
├── filetree
│   ├── 4c815128eb73a4ecc54080d29810d080b2139ab8.nq.gz
│   └── e5fe944127cab62472a9657f0a5bb232e0303fc8.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

17 directories, 41 files
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
*Parsed on 2026-11-22 by [repolex](https://repolex.ai)*
