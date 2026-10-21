# Repolex Knowledge Graph of PyCQA/meta

RDF knowledge graph data for [PyCQA/meta](https://github.com/PyCQA/meta), parsed by [repolex](https://repolex.ai).

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
rlex download PyCQA/meta
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c31221a4c76fcef10fc7e5a79c20f168f71e2d01
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c31221a4c76fcef10fc7e5a79c20f168f71e2d01
│           └── chunk-001.nq.gz
├── blob
│   ├── 091d2a30bd6aa03e04c1faee70b320875086f964.nq.gz
│   ├── 0becc082d20ea5c0aba60400a4e62d3d36f8950f.nq.gz
│   ├── 14f4c921fe330e191c4b65e5db547c918f2a8b13.nq.gz
│   ├── 1fba11befbea186c00683a55b64764529ad7afdd.nq.gz
│   ├── 3c2fe2775404dba47434c3ae4e619af59bd7e869.nq.gz
│   ├── 708ad52bc7477a899c809457ef87dad2320529c8.nq.gz
│   ├── 903276a008528355dfb1871e4068b957a555ed44.nq.gz
│   ├── 90859aef6ea83f41d8591ee0bec07012c6bae7f5.nq.gz
│   ├── 939c83d22145c3e17bcdb732878cb87a3c8cf4cd.nq.gz
│   ├── 9731b5ae02af982c0e852269c9bafee0917593a9.nq.gz
│   ├── a0377392b439a71829af3bf3da92e41fb418a2a3.nq.gz
│   ├── abb90580b38cba33f3adf556245788ff2c5b05eb.nq.gz
│   ├── aeb501289453fb242f97a0689b25cdb5b89eadb9.nq.gz
│   ├── b64a7f277327b654a566798668b4fc45592ed705.nq.gz
│   ├── b6e5459b468f8031dbca58f2c9221241fd190c2f.nq.gz
│   ├── bca3bea84eeeb0c8d451f8aecb7ee14f47006155.nq.gz
│   ├── cae26c7c6f0f49f4df394222398fa2087ec227d6.nq.gz
│   ├── dd5ae85324a6539e6d0ed00bf26ec15823a0db66.nq.gz
│   ├── e25ae776f03cd505082a044c2d09e6330c02126f.nq.gz
│   ├── e9bfba6fb4284b6407d99f92d4a7a529ed7da4e7.nq.gz
│   └── fd662a7e6c628e351ccd072bf4a30710d36f4556.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c31221a4c76fcef10fc7e5a79c20f168f71e2d01.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 29 files
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

[PyCQA/meta](https://github.com/PyCQA/meta)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
