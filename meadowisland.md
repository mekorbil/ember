# LinkHub Mobile Article Aggregator

LinkHub is a high-performance, structured aggregation system designed for collecting, indexing, and retrieving mobile-accessible technical articles and informational resources from distributed content sources. The system targets developers, technical researchers, and content curators who need to maintain a local mirror or searchable index of external article archives without relying on third-party API rate limits or scraping bottlenecks.

The project implements a modular pipeline architecture that handles HTTP fetching, HTML parsing, metadata extraction, full-text keyword indexing, and duplicate detection across multiple source domains. LinkHub operates as a standalone command-line tool with optional daemon mode for scheduled updates, making it suitable for both ad-hoc research tasks and production-grade knowledge base maintenance.

## 功能概览

- **Multi-Source Parallel Fetching** – Concurrent HTTP GET requests with configurable timeout, retry logic, and user-agent rotation to efficiently harvest articles from multiple domains without blocking.

- **Adaptive HTML Content Extraction** – Automatic detection and stripping of navigation menus, sidebars, footers, and advertising blocks using heuristic DOM analysis, retaining only primary article body text and structural headings.

- **Full-Text Inverted Indexing** – Tokenization, stop-word filtering, and stemming for Chinese and English mixed-language content, with index persistence using LMDB for low-latency keyword lookups.

- **Duplicate URL and Content Fingerprinting** – SHA-256 content hashing combined with URL normalisation to detect and skip already-indexed articles, reducing redundant storage and processing overhead.

- **Export and Serialisation Modules** – Support for output formats including JSON lines, CSV metadata tables, and plain-text markdown link collections, facilitating integration with static site generators or data analysis pipelines.

- **Scheduled Incremental Updates** – Built-in cron-style scheduler that triggers re-fetching of source URLs at configurable intervals, with delta indexing that only processes new or modified articles.

- **Query Interface with Boolean Operators** – Command-line search supporting AND, OR, and NOT operators, with relevance ranking based on term frequency and positional proximity.

## 应用场景

1. **Offline Technical Reference Library** – A developer working in an air-gapped environment can use LinkHub to periodically fetch and index articles from allowed external domains, building a searchable local knowledge base without requiring persistent internet connectivity.

2. **Content Aggregation for Research Projects** – Academic researchers studying web technologies or information dissemination patterns can collect article metadata and full-text samples across multiple source sites, then export structured datasets for quantitative analysis.

3. **Personal Knowledge Management Pipeline** – Technical writers and bloggers can configure LinkHub to monitor specific article categories, automatically extracting new content and generating markdown summaries that feed into note-taking systems such as Obsidian or Logseq.

4. **CI/CD Documentation Validation** – DevOps teams can integrate LinkHub into their documentation build process to verify that external reference links remain accessible and to cache fallback copies, preventing broken links in production documentation.

5. **Historical Content Archiving** – Organisations preserving legacy technical documentation can use the incremental update feature to maintain a time-series snapshot of article changes, with content fingerprinting enabling change detection and version tracking.

## 快速开始

The following commands clone the repository, install dependencies, build the binary, and run an initial indexing pass using the default configuration file.

```bash
git clone https://github.com/linkhub-io/linkhub.git
cd linkhub
make deps
make build
./bin/linkhub index --config configs/default.yaml --source sources.txt --output ./data
```

The `sources.txt` file should contain one URL per line. After indexing, use the search subcommand to query the local index.

```bash
./bin/linkhub search "performance optimization" --limit 20 --format table
```

## 安装要求

The following table lists the mandatory build-time and runtime dependencies for LinkHub. All dependencies are open-source and available through standard package managers.

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Go | 1.21 or higher | Core language runtime and compiler toolchain |
| GCC | 10.0 or higher | Required for CGO support and LMDB native bindings |
| LMDB | 0.9.29 or higher | Memory-mapped key-value store for index persistence |
| Make | 4.0 or higher | Build automation and task orchestration |
| Git | 2.30 or higher | Version control and source repository cloning |
| curl | 7.68 or higher | Used internally for health checks and debug logging |
| jq | 1.6 or higher | JSON processing for export pipeline validation |
| sqlite3 | 3.35 or higher | Optional metadata cache and deduplication log storage |
| protoc | 3.15 or higher | Protocol buffer compiler for gRPC extensions (optional) |
| Docker | 20.10 or higher | Containerised deployment and integration testing |

## 文档导航

The documentation is organised into three layers: user-facing guides, operator manuals, and developer references. Each layer addresses distinct concerns for different audience segments.

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | docs/user/quickstart.md | How do I install LinkHub and index my first article collection within 10 minutes? |
| 用户指南 | docs/user/search-syntax.md | What boolean operators and field filters are supported in the query interface? |
| 操作手册 | docs/ops/deployment.md | How do I configure systemd service files and log rotation for production daemon mode? |
| 操作手册 | docs/ops/tuning.md | How do I adjust concurrency, memory limits, and LMDB map size for large-scale indexes? |
| 开发者参考 | docs/dev/architecture.md | What is the internal module structure and how do components communicate via channels? |
| 开发者参考 | docs/dev/writing-plugins.md | How can I implement a custom content extractor or export formatter using the plugin interface? |
| 综合 | docs/faq.md | What are the common error codes and their recovery procedures? |

## 资源列表

- http://www.mobile.cmcvrr.cn/Article/08068.shtml
- http://www.mobile.nwbbyt.cn/Article/5118.shtml
- http://www.mobile.puhvjy.cn/Article/274055.shtml
- http://www.mobile.puhvjy.cn/Article/1355.shtml
- http://www.mobile.puhvjy.cn/Article/5225932.shtml
- http://www.mobile.nwbbyt.cn/Article/7355.shtml
- http://www.mobile.cmcvrr.cn/Article/6511630.shtml
- http://www.mobile.nwbbyt.cn/Article/5162.shtml
- http://www.mobile.puhvjy.cn/Article/9600559.shtml
- http://www.mobile.jnjpgf.cn/Article/441477.shtml
- http://www.mobile.cmcvrr.cn/Article/995372.shtml
- http://www.mobile.jnjpgf.cn/Article/26408.shtml
- http://www.mobile.jnjpgf.cn/Article/37642.shtml
- http://www.mobile.jnjpgf.cn/Article/57453.shtml
- http://www.mobile.cmcvrr.cn/Article/9699.shtml
- http://www.mobile.nwbbyt.cn/Article/37069.shtml
- http://www.mobile.jnjpgf.cn/Article/64621.shtml
- http://www.mobile.jnjpgf.cn/Article/909099.shtml
- http://www.mobile.cmcvrr.cn/Article/246571.shtml
- http://www.mobile.puhvjy.cn/Article/907661.shtml
- http://www.mobile.puhvjy.cn/Article/7485.shtml
- http://www.mobile.puhvjy.cn/Article/8017.shtml
- http://www.mobile.cmcvrr.cn/Article/4812.shtml
- http://www.mobile.jnjpgf.cn/Article/283033.shtml
- http://www.mobile.jnjpgf.cn/Article/6147618.shtml
- http://www.mobile.cmcvrr.cn/Article/8175.shtml
- http://www.mobile.puhvjy.cn/Article/5034743.shtml
- http://www.mobile.nwbbyt.cn/Article/1004.shtml
- http://www.mobile.nwbbyt.cn/Article/2531328.shtml
- http://www.mobile.nwbbyt.cn/Article/6946317.shtml
- http://www.mobile.puhvjy.cn/Article/61744.shtml
- http://www.mobile.cmcvrr.cn/Article/01523.shtml
- http://www.mobile.jnjpgf.cn/Article/1172.shtml
- http://www.mobile.cmcvrr.cn/Article/64645.shtml
- http://www.mobile.nwbbyt.cn/Article/1784.shtml
- http://www.mobile.jnjpgf.cn/Article/7646986.shtml
- http://www.mobile.puhvjy.cn/Article/8456011.shtml
- http://www.mobile.puhvjy.cn/Article/397891.shtml
- http://www.mobile.jnjpgf.cn/Article/415552.shtml
- http://www.mobile.nwbbyt.cn/Article/2916.shtml
- http://www.mobile.puhvjy.cn/Article/600204.shtml
- http://www.mobile.cmcvrr.cn/Article/128794.shtml
- http://www.mobile.cmcvrr.cn/Article/3066557.shtml
- http://www.mobile.nwbbyt.cn/Article/428961.shtml
- http://www.mobile.puhvjy.cn/Article/7715.shtml
- http://www.mobile.cmcvrr.cn/Article/75205.shtml
- http://www.mobile.cmcvrr.cn/Article/6061.shtml
- http://www.mobile.nwbbyt.cn/Article/933259.shtml
- http://www.mobile.cmcvrr.cn/Article/7424.shtml
- http://www.mobile.puhvjy.cn/Article/54473.shtml
- http://www.mobile.puhvjy.cn/Article/5350823.shtml
- http://www.mobile.nwbbyt.cn/Article/608003.shtml
- http://www.mobile.puhvjy.cn/Article/31371.shtml
- http://www.mobile.nwbbyt.cn/Article/181571.shtml
- http://www.mobile.jnjpgf.cn/Article/6374102.shtml
- http://www.mobile.jnjpgf.cn/Article/79095.shtml
- http://www.mobile.cmcvrr.cn/Article/829635.shtml
- http://www.mobile.nwbbyt.cn/Article/7169935.shtml
- http://www.mobile.puhvjy.cn/Article/7003.shtml
- http://www.mobile.puhvjy.cn/Article/002744.shtml
- http://www.mobile.nwbbyt.cn/Article/704271.shtml
- http://www.mobile.puhvjy.cn/Article/624672.shtml
- http://www.mobile.puhvjy.cn/Article/1555243.shtml
- http://www.mobile.jnjpgf.cn/Article/489258.shtml
- http://www.mobile.puhvjy.cn/Article/021085.shtml
- http://www.mobile.puhvjy.cn/Article/989280.shtml
- http://www.mobile.jnjpgf.cn/Article/111228.shtml
- http://www.mobile.cmcvrr.cn/Article/484136.shtml
- http://www.mobile.jnjpgf.cn/Article/44041.shtml
- http://www.mobile.nwbbyt.cn/Article/319754.shtml
- http://www.mobile.nwbbyt.cn/Article/7303.shtml
- http://www.mobile.puhvjy.cn/Article/0975.shtml
- http://www.mobile.cmcvrr.cn/Article/291278.shtml
- http://www.mobile.jnjpgf.cn/Article/6024602.shtml
- http://www.mobile.cmcvrr.cn/Article/0582.shtml
- http://www.mobile.nwbbyt.cn/Article/1635.shtml
- http://www.mobile.puhvjy.cn/Article/4160.shtml
- http://www.mobile.jnjpgf.cn/Article/61392.shtml
- http://www.mobile.nwbbyt.cn/Article/6928368.shtml
- http://www.mobile.cmcvrr.cn/Article/2473091.shtml
- http://www.mobile.jnjpgf.cn/Article/2945886.shtml
- http://www.mobile.jnjpgf.cn/Article/4389.shtml
- http://www.mobile.jnjpgf.cn/Article/7418243.shtml
- http://www.mobile.cmcvrr.cn/Article/95145.shtml
- http://www.mobile.puhvjy.cn/Article/1766.shtml
- http://www.mobile.cmcvrr.cn/Article/63219.shtml
- http://www.mobile.puhvjy.cn/Article/4261.shtml
- http://www.mobile.jnjpgf.cn/Article/7722696.shtml
- http://www.mobile.nwbbyt.cn/Article/7704.shtml
- http://www.mobile.cmcvrr.cn/Article/89436.shtml
- http://www.mobile.cmcvrr.cn/Article/55928.shtml
- http://www.mobile.cmcvrr.cn/Article/1336118.shtml
- http://www.mobile.nwbbyt.cn/Article/83858.shtml
- http://www.mobile.cmcvrr.cn/Article/912434.shtml
- http://www.mobile.nwbbyt.cn/Article/173113.shtml
- http://www.mobile.jnjpgf.cn/Article/884970.shtml
- http://www.mobile.cmcvrr.cn/Article/3420.shtml
- http://www.mobile.puhvjy.cn/Article/4562884.shtml
- http://www.mobile.puhvjy.cn/Article/838301.shtml
- http://www.mobile.puhvjy.cn/Article/98744.shtml
- http://www.mobile.cmcvrr.cn/Article/3409677.shtml
- http://www.mobile.jnjpgf.cn/Article/5080240.shtml
- http://www.mobile.nwbbyt.cn/Article/84109.shtml
- http://www.mobile.cmcvrr.cn/Article/0269673.shtml
- http://www.mobile.nwbbyt.cn/Article/63145.shtml
- http://www.mobile.puhvjy.cn/Article/7677.shtml
- http://www.mobile.cmcvrr.cn/Article/388366.shtml
- http://www.mobile.nwbbyt.cn/Article/606950.shtml
- http://www.mobile.nwbbyt.cn/Article/4285.shtml
- http://www.mobile.nwbbyt.cn/Article/763202.shtml
- http://www.mobile.jnjpgf.cn/Article/5910.shtml
- http://www.mobile.nwbbyt.cn/Article/3367.shtml
- http://www.mobile.cmcvrr.cn/Article/069504.shtml
- http://www.mobile.nwbbyt.cn/Article/27280.shtml
- http://www.mobile.jnjpgf.cn/Article/9777988.shtml
- http://www.mobile.jnjpgf.cn/Article/716089.shtml
- http://www.mobile.cmcvrr.cn/Article/9015903.shtml
- http://www.mobile.cmcvrr.cn/Article/0999583.shtml
- http://www.mobile.nwbbyt.cn/Article/4659.shtml
- http://www.mobile.puhvjy.cn/Article/524608.shtml
- http://www.mobile.nwbbyt.cn/Article/010747.shtml
- http://www.mobile.jnjpgf.cn/Article/81942.shtml
- http://www.mobile.nwbbyt.cn/Article/7709927.shtml
- http://www.mobile.puhvjy.cn/Article/7900939.shtml
- http://www.mobile.jnjpgf.cn/Article/8859.shtml
- http://www.mobile.jnjpgf.cn/Article/495571.shtml
- http://www.mobile.nwbbyt.cn/Article/268083.shtml
- http://www.mobile.nwbbyt.cn/Article/9412157.shtml
- http://www.mobile.nwbbyt.cn/Article/61513.shtml
- http://www.mobile.nwbbyt.cn/Article/6319.shtml
- http://www.mobile.jnjpgf.cn/Article/4191.shtml
- http://www.mobile.nwbbyt.cn/Article/0286.shtml
- http://www.mobile.nwbbyt.cn/Article/77967.shtml
- http://www.mobile.cmcvrr.cn/Article/7988290.shtml
- http://www.mobile.nwbbyt.cn/Article/575531.shtml
- http://www.mobile.nwbbyt.cn/Article/685667.shtml
- http://www.mobile.puhvjy.cn/Article/89956.shtml
- http://www.mobile.cmcvrr.cn/Article/767658.shtml
- http://www.mobile.nwbbyt.cn/Article/6350.shtml
- http://www.mobile.nwbbyt.cn/Article/238800.shtml
- http://www.mobile.cmcvrr.cn/Article/75171.shtml
- http://www.mobile.nwbbyt.cn/Article/004191.shtml
- http://www.mobile.nwbbyt.cn/Article/9072503.shtml
- http://www.mobile.cmcvrr.cn/Article/75506.shtml
- http://www.mobile.cmcvrr.cn/Article/40978.shtml
- http://www.mobile.jnjpgf.cn/Article/2697.shtml
- http://www.mobile.cmcvrr.cn/Article/29093.shtml
- http://www.mobile.nwbbyt.cn/Article/622227.shtml
- http://www.mobile.jnjpgf.cn/Article/5514.shtml
- http://www.mobile.puhvjy.cn/Article/16644.shtml
- http://www.mobile.puhvjy.cn/Article/646239.shtml
- http://www.mobile.nwbbyt.cn/Article/896858.shtml
- http://www.mobile.nwbbyt.cn/Article/01444.shtml
- http://www.mobile.nwbbyt.cn/Article/40497.shtml
- http://www.mobile.jnjpgf.cn/Article/48019.shtml
- http://www.mobile.puhvjy.cn/Article/394867.shtml
- http://www.mobile.jnjpgf.cn/Article/0949.shtml
- http://www.mobile.puhvjy.cn/Article/733807.shtml
- http://www.mobile.cmcvrr.cn/Article/055008.shtml
- http://www.mobile.cmcvrr.cn/Article/6432929.shtml
- http://www.mobile.cmcvrr.cn/Article/2588266.shtml
- http://www.mobile.jnjpgf.cn/Article/5944253.shtml
- http://www.mobile.nwbbyt.cn/Article/0912.shtml
- http://www.mobile.puhvjy.cn/Article/3920641.shtml
- http://www.mobile.jnjpgf.cn/Article/8802109.shtml
- http://www.mobile.nwbbyt.cn/Article/0284249.shtml
- http://www.mobile.jnjpgf.cn/Article/53734.shtml
- http://www.mobile.cmcvrr.cn/Article/58243.shtml
- http://www.mobile.puhvjy.cn/Article/3655556.shtml
- http://www.mobile.jnjpgf.cn/Article/343300.shtml
- http://www.mobile.jnjpgf.cn/Article/097846.shtml
- http://www.mobile.jnjpgf.cn/Article/36558.shtml
- http://www.mobile.nwbbyt.cn/Article/273451.shtml
- http://www.mobile.cmcvrr.cn/Article/579607.shtml
- http://www.mobile.cmcvrr.cn/Article/7561256.shtml
- http://www.mobile.jnjpgf.cn/Article/81136.shtml
- http://www.mobile.nwbbyt.cn/Article/485242.shtml
- http://www.mobile.cmcvrr.cn/Article/5157.shtml
- http://www.mobile.nwbbyt.cn/Article/3563.shtml
- http://www.mobile.jnjpgf.cn/Article/79857.shtml
- http://www.mobile.nwbbyt.cn/Article/1188103.shtml
- http://www.mobile.nwbbyt.cn/Article/123597.shtml
- http://www.mobile.jnjpgf.cn/Article/73391.shtml
- http://www.mobile.puhvjy.cn/Article/7251348.shtml
- http://www.mobile.nwbbyt.cn/Article/2746280.shtml
- http://www.mobile.jnjpgf.cn/Article/639793.shtml
- http://www.mobile.cmcvrr.cn/Article/0751.shtml
- http://www.mobile.jnjpgf.cn/Article/1176217.shtml
- http://www.mobile.jnjpgf.cn/Article/8576501.shtml
- http://www.mobile.cmcvrr.cn/Article/0377.shtml
- http://www.mobile.nwbbyt.cn/Article/7474559.shtml
- http://www.mobile.nwbbyt.cn/Article/240632.shtml
- http://www.mobile.nwbbyt.cn/Article/18580.shtml
- http://www.mobile.jnjpgf.cn/Article/7820.shtml
- http://www.mobile.cmcvrr.cn/Article/3709.shtml
- http://www.mobile.puhvjy.cn/Article/7276425.shtml
- http://www.mobile.puhvjy.cn/Article/5410.shtml
- http://www.mobile.cmcvrr.cn/Article/2252105.shtml
- http://www.mobile.puhvjy.cn/Article/183129.shtml
- http://www.mobile.nwbbyt.cn/Article/14160.shtml
- http://www.mobile.cmcvrr.cn/Article/04447.shtml
- http://www.mobile.puhvjy.cn/Article/0408087.shtml
- http://www.mobile.jnjpgf.cn/Article/3299928.shtml
- http://www.mobile.nwbbyt.cn/Article/687979.shtml
- http://www.mobile.nwbbyt.cn/Article/042235.shtml
- http://www.mobile.jnjpgf.cn/Article/64997.shtml
- http://www.mobile.nwbbyt.cn/Article/96697.shtml
- http://www.mobile.puhvjy.cn/Article/2678.shtml
- http://www.mobile.nwbbyt.cn/Article/5360.shtml
- http://www.mobile.jnjpgf.cn/Article/82812.shtml
- http://www.mobile.jnjpgf.cn/Article/815795.shtml
- http://www.mobile.nwbbyt.cn/Article/289723.shtml
- http://www.mobile.cmcvrr.cn/Article/9266.shtml
- http://www.mobile.jnjpgf.cn/Article/3755.shtml
- http://www.mobile.puhvjy.cn/Article/822713.shtml
- http://www.mobile.cmcvrr.cn/Article/227928.shtml
- http://www.mobile.puhvjy.cn/Article/51631.shtml
- http://www.mobile.jnjpgf.cn/Article/3868625.shtml
- http://www.mobile.nwbbyt.cn/Article/753873.shtml
- http://www.mobile.jnjpgf.cn/Article/800871.shtml
- http://www.mobile.nwbbyt.cn/Article/9194147.shtml
- http://www.mobile.nwbbyt.cn/Article/5316890.shtml
- http://www.mobile.cmcvrr.cn/Article/2320.shtml
- http://www.mobile.cmcvrr.cn/Article/691797.shtml
- http://www.mobile.puhvjy.cn/Article/476649.shtml
- http://www.mobile.jnjpgf.cn/Article/0291.shtml
- http://www.mobile.puhvjy.cn/Article/5261203.shtml
- http://www.mobile.puhvjy.cn/Article/3252.shtml
- http://www.mobile.jnjpgf.cn/Article/6605.shtml
- http://www.mobile.cmcvrr.cn/Article/49514.shtml
- http://www.mobile.jnjpgf.cn/Article/11876.shtml
- http://www.mobile.jnjpgf.cn/Article/72817.shtml
- http://www.mobile.puhvjy.cn/Article/06332.shtml
- http://www.mobile.jnjpgf.cn/Article/7935.shtml
- http://www.mobile.cmcvrr.cn/Article/4142.shtml
- http://www.mobile.puhvjy.cn/Article/28927.shtml
- http://www.mobile.jnjpgf.cn/Article/547022.shtml
- http://www.mobile.puhvjy.cn/Article/01738.shtml
- http://www.mobile.puhvjy.cn/Article/470031.shtml
- http://www.mobile.puhvjy.cn/Article/1700877.shtml
- http://www.mobile.cmcvrr.cn/Article/6227.shtml
- http://www.mobile.nwbbyt.cn/Article/44967.shtml
- http://www.mobile.jnjpgf.cn/Article/0879352.shtml
- http://www.mobile.jnjpgf.cn/Article/8887.shtml
- http://www.mobile.puhvjy.cn/Article/357250.shtml
- http://www.mobile.nwbbyt.cn/Article/8068626.shtml
- http://www.mobile.nwbbyt.cn/Article/15106.shtml
- http://www.mobile.cmcvrr.cn/Article/33599.shtml
- http://www.mobile.puhvjy.cn/Article/125423.shtml
- http://www.mobile.nwbbyt.cn/Article/71510.shtml

## 项目结构

The following ASCII directory tree illustrates the core module organisation and source code layout. Each top-level directory corresponds to a distinct functional component with well-defined interfaces.

```
linkhub/
├── cmd/                              # Command-line entry points and subcommand implementations
│   ├── linkhub/                      # Main binary package
│   │   ├── main.go                   # Program initialisation and flag parsing
│   │   ├── index.go                  # Index subcommand: fetch and parse articles
│   │   ├── search.go                 # Search subcommand: query the local index
│   │   └── export.go                 # Export subcommand: serialise to JSON/CSV/Markdown
│   └── daemon/                       # Optional daemon mode for scheduled updates
│       ├── main.go                   # Service runner and signal handling
│       └── scheduler.go              # Cron expression parser and job dispatcher
├── internal/                         # Private packages, not exposed to external consumers
│   ├── fetcher/                      # HTTP client pool, redirect handling, retry logic
│   │   ├── client.go                 # Configurable transport with timeout and proxy support
│   │   └── rotator.go                # User-agent and IP rotation helpers
│   ├── extractor/                    # DOM parsing and content cleaning algorithms
│   │   ├── html.go                   # goquery-based node traversal and noise removal
│   │   └── fingerprint.go            # SHA-256 content hashing and similarity scoring
│   ├── indexer/                      # Inverted index builder and LMDB data access layer
│   │   ├── tokenizer.go              # Chinese/English segmentation and stop-word filter
│   │   ├── lmbd.go                   # LMDB transaction management and bucket operations
│   │   └── ranking.go                # TF-IDF and positional scoring functions
│   ├── storage/                      # Metadata persistence and deduplication logs
│   │   ├── sqlite.go                 # SQLite-backed cache for URL visit history
│   │   └── blob.go                   # Filesystem-based blob store for raw HTML archives
│   └── scheduler/                    # Internal scheduling and event loop
│       ├── cron.go                   # Time-based trigger evaluation
│       └── worker.go                 # Goroutine pool for parallel fetch tasks
├── pkg/                              # Reusable libraries intended for public consumption
│   ├── types/                        # Shared data structures and type definitions
│   │   ├── article.go                # Article struct with metadata fields
│   │   └── query.go                  # Query AST and filter representation
│   └── utils/                        # Utility functions for logging, config, and file I/O
│       ├── logger.go                 # Structured logging with level filtering
│       └── config.go                 # YAML configuration loader and validation
├── configs/                          # Sample configuration files for various environments
│   ├── default.yaml                  # Base config with moderate concurrency and caching
│   └── production.yaml               # Tuned for large-scale deployments
├── docs/                             # Complete documentation suite
│   ├── user/                         # End-user tutorials and reference guides
│   ├── ops/                          # System administrator and deployment manuals
│   └── dev/                          # Developer contribution guidelines and API design
├── scripts/                          # Build, test, and deployment automation scripts
│   ├── build.sh                      # Cross-platform compilation wrapper
│   └── test.sh                       # Unit and integration test runner with coverage
├── testdata/                         # Sample article HTML files for unit testing
│   ├── sample1.html                  # Static fixture with mixed Chinese and English text
│   └── sample2.html                  # Edge case with missing metadata tags
├── go.mod                            # Go module dependency declaration
├── go.sum                            # Dependency checksums
├── Makefile                          # Primary build orchestration and task runner
└── README.md                         # This document
```

## 贡献指南

Contributions to LinkHub are welcome provided they adhere to the following procedural standards. All submissions must pass the existing test suite and maintain backward compatibility unless explicitly approved by the maintainers.

1. **Fork the Repository and Create a Feature Branch** – Fork the upstream repository to your personal account, then create a branch with a descriptive name prefixed by the component being modified, for example `extractor/improve-parser` or `indexer/fix-lmdb-transaction`.

2. **Run the Full Test Suite Locally** – Execute `make test` from the project root. This runs unit tests, integration tests, and linters including go vet and staticcheck. Ensure all tests pass before opening a pull request.

3. **Update Documentation for Any User-Facing Changes** – If your contribution modifies command-line flags, configuration keys, or public API behaviour, update the corresponding section in the docs directory and provide a brief example.

4. **Open a Pull Request Against the Main Branch** – Submit your pull request with a clear title and a detailed description that references the issue number, explains the motivation, and outlines the testing performed. Include before-and-after benchmarks if performance is affected.

5. **Participate in Code Review** – Respond to feedback from maintainers and other contributors in a timely manner. Pull requests that remain inactive for more than 30 days may be closed.

## 常见问题

**Q: 为什么索引过程中出现 LMDB 内存映射大小不足的错误？**

A: 默认的 LMDB 映射大小为 1 GB，当索引文章数量超过约 200 万篇时可能触发该错误。可以通过修改配置文件中 `storage.lmdb_map_size_mb` 参数增加映射大小，建议设置为预期数据量的 1.5 倍。如果运行在 32 位系统上，映射大小受限于进程地址空间，建议迁移到 64 位环境。

**Q: 某些来源网址返回 HTTP 403 或者连接超时，如何绕过限制？**

A: LinkHub 支持用户代理轮换和请求延迟配置。在配置文件中调整 `fetcher.user_agents` 列表，添加移动端或桌面端浏览器标识。对于严格的防爬策略，可以启用 `fetcher.random_delay_ms` 参数，设定 500 到 3000 毫秒之间的随机延迟。如果问题持续，请检查目标站点是否要求特定的 Cookie 或 Referer 头。

**Q: 导出的 Markdown 链接列表能否直接用于静态站点生成器？**

A: 可以。使用 `export --format markdown` 命令生成的输出为标准无序列表格式，每条记录包含标题、来源域名和原始 URL。该输出可直接嵌入 Hugo、Jekyll、Zola 等静态站点生成器的内容目录，也可以作为自定义导航页的数据源。如需调整字段顺序或添加额外元数据，可以修改 `pkg/export/markdown.go` 中的模板逻辑。

## 许可证

This project is distributed under the terms of the MIT License. The full license text is available in the LICENSE file in the repository root. Use, modification, and redistribution are permitted provided that the copyright notice and permission notice are retained in all copies or substantial portions of the software.

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
