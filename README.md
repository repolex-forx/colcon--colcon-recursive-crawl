# Repolex Knowledge Graph of colcon/colcon-recursive-crawl

RDF knowledge graph data for [colcon/colcon-recursive-crawl](https://github.com/colcon/colcon-recursive-crawl), parsed by [repolex](https://repolex.ai).

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
rlex download colcon/colcon-recursive-crawl
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 645281d4233a6b909fa9546a5bf360d39a715a7f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 645281d4233a6b909fa9546a5bf360d39a715a7f
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f17157ed42b486a0c57cbffddd97987a4844e6b.nq.gz
│   ├── 367a701a37b7a60d73de2cbdebcc138a7b8307dd.nq.gz
│   ├── 3ebc1bca3dc9eef5822e4ae83a74fb240965b8ff.nq.gz
│   ├── 564465c231fafe0a00586317d1c519587378dc3b.nq.gz
│   ├── a0ebe91c6cf7732cc16ac88702c5875280719dfa.nq.gz
│   ├── bd7c8693b373f16474a10254e75b502ef8389f27.nq.gz
│   ├── bebe3811f51e5f0e363bd5f2ee261c2f95e6f30c.nq.gz
│   ├── cf943d2f8aa9719c5ea8320ace481784da2969d9.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   ├── dffe460f162da9929178a7ce342532e7ba896425.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e82fd0b0abbf1472480d19d468efe7819276e80d.nq.gz
│   ├── f172ba418a5710213278041c9d035a6f8732dfa8.nq.gz
│   └── fe623ed3c61efeaefed8cb33ec347d388f218e5e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 645281d4233a6b909fa9546a5bf360d39a715a7f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[colcon/colcon-recursive-crawl](https://github.com/colcon/colcon-recursive-crawl)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
