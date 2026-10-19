# Repolex Knowledge Graph of mitsuhiko/speaklater

RDF knowledge graph data for [mitsuhiko/speaklater](https://github.com/mitsuhiko/speaklater), parsed by [repolex](https://repolex.ai).

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
rlex download mitsuhiko/speaklater
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5e137816de91dcc9b9bf81f953460eb8066c3a70
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5e137816de91dcc9b9bf81f953460eb8066c3a70
│           └── chunk-001.nq.gz
├── blob
│   ├── 0501b57a19162665f4b0aa0fe8b7e56ad61a09ee.nq.gz
│   ├── 65fa51a9988dcc2865ec53f20ebc4e6818517bf5.nq.gz
│   ├── 67a4dc5dd5440ed57b743f18f84e2d218d7c1ec4.nq.gz
│   ├── 8d33ab1375899b420984632b6ef57eef8aa99943.nq.gz
│   ├── d67fe2d32dc0dfbdb0085dad5635209d00a2b665.nq.gz
│   └── d6fee648919ff436bf05cd37f06f2916b0cbac3b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5e137816de91dcc9b9bf81f953460eb8066c3a70.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
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

[mitsuhiko/speaklater](https://github.com/mitsuhiko/speaklater)

---
*Parsed on 2026-10-19 by [repolex](https://repolex.ai)*
