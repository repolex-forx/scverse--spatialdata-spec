# Repolex Knowledge Graph of scverse/spatialdata-spec

RDF knowledge graph data for [scverse/spatialdata-spec](https://github.com/scverse/spatialdata-spec), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/spatialdata-spec
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f4e4fb4172c668b4a88cc5435ca91355a919a9b2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f4e4fb4172c668b4a88cc5435ca91355a919a9b2
│           └── chunk-001.nq.gz
├── blob
│   ├── 275aa4b62a64d717b9b2aa73b3de3571ba98d485.nq.gz
│   ├── 288185516d1202f5506cbdb3b864a10597d0afc4.nq.gz
│   ├── 43afdcb203ba3a31a556785b4762ec6f319778dd.nq.gz
│   └── ec396d0e2dc9f96b942c968e2c99d9f8711de444.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f4e4fb4172c668b4a88cc5435ca91355a919a9b2.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 12 files
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

[scverse/spatialdata-spec](https://github.com/scverse/spatialdata-spec)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
