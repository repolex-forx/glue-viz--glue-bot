# Repolex Knowledge Graph of glue-viz/glue-bot

RDF knowledge graph data for [glue-viz/glue-bot](https://github.com/glue-viz/glue-bot), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/glue-bot
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a668d7ea11498d72a8649307c890ea2b704fbe0f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a668d7ea11498d72a8649307c890ea2b704fbe0f
│           └── chunk-001.nq.gz
├── blob
│   ├── 26157c7f2e6aaa29393516b0d58e5e855c197ab4.nq.gz
│   ├── 321aaeed6d10baa6a442b138d161407f0cdb9362.nq.gz
│   ├── 5901e01602e5ab5bb271f1047e8947f7ed076aed.nq.gz
│   ├── 77dd84fe3256c8ac31cc3af16b2eba941ebf5b3f.nq.gz
│   ├── 840c04542a1685283d860015486f4a8a10259568.nq.gz
│   ├── 8a694a37ac7a11f94e1461b4a5ce4580ac5d8ca6.nq.gz
│   ├── c56ecff11f16c925706b5c0ded86d6207ddaa844.nq.gz
│   └── f73b30cae8c69ca1421e87ab2bd49f8b411468d5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a668d7ea11498d72a8649307c890ea2b704fbe0f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 16 files
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

[glue-viz/glue-bot](https://github.com/glue-viz/glue-bot)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
