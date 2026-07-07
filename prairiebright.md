# Mobile Link Aggregator Service (MLAS)

MLAS 是一个面向移动端内容聚合与批量外链管理的开源基础设施项目，专为需要在大规模域名池下进行高效链接采集、分类与存储的场景设计。项目面向数据运营团队、内容聚合平台开发者以及个人站点管理员，解决多源异构链接的统一收录、快速检索与自动化维护问题。当前批次为第 11/80 批，共收录 250 个移动端资讯类资源链接，覆盖 cmcvrr、puhvjy、nwbbyt、jnjpgf 四个主要域名体系。

## 功能概览

- **多域名源统一接入**：支持同时接入 cmcvrr、puhvjy、nwbbyt、jnjpgf 等不同根域的移动端页面，通过配置化方式新增或停用数据源。
- **批量链接解析与入库**：提供批量 URL 导入接口，自动解析文章编号、来源域名、时间戳等元信息，并写入结构化存储。
- **去重与状态检测**：内置基于 URL 哈希和文章 ID 的双重去重机制，定期检测链接可用性并标记异常状态。
- **分类标签自动生成**：根据 URL 路径中的 Article 数字段特征，自动为每条链接生成分类标签，便于后续按主题筛选。
- **检索与导出接口**：提供基于域名、时间段、状态等多维度的查询接口，支持 JSON 和 CSV 格式的批量导出。
- **增量更新与批次管理**：按批次（每批 250 条）管理链接集合，支持批次状态标记、增量追加和历史回溯。
- **移动端适配预览**：为每条链接生成简化的移动端预览摘要，包含标题推测和来源标识，方便快速浏览。

## 应用场景

- **内容聚合平台的数据采集层**：平台运营方可使用 MLAS 作为外部链接的统一入口，将从多个移动站点采集的文章链接进行集中管理和状态监控，避免链接分散在多个脚本或临时文件中。
- **运营团队的链接库维护**：运营人员需要定期整理一批外部参考链接，MLAS 提供批量导入和自动去重能力，减少人工比对时间，同时支持按来源域名快速筛选。
- **个人站长的外链资源整理**：独立站点管理员可将日常积累的移动端参考文章链接通过 MLAS 进行归档，配合检索接口快速找到特定域名下的历史链接。
- **数据分析前的链接预处理**：在进行移动端内容分析或舆情监控前，使用 MLAS 对原始链接列表进行清洗、去重和状态检测，确保进入分析管道的数据质量。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/mlas-org/mlas-service.git

# 进入项目目录
cd mlas-service

# 安装依赖（使用 pip 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化配置（复制示例配置并修改数据库连接）
cp config.example.yaml config.yaml
vim config.yaml

# 初始化数据库表结构
python scripts/init_db.py

# 启动服务（默认监听 8080 端口）
python app.py
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐使用 3.10 LTS |
| SQLite / PostgreSQL | SQLite 3.35+ / PostgreSQL 12+ | 存储链接元数据与批次信息，生产环境推荐 PostgreSQL |
| requests | 2.28.0 及以上 | 用于链接可用性检测和状态码获取 |
| pyyaml | 6.0 及以上 | 解析配置文件 config.yaml |
| pandas | 1.5.0 及以上 | 用于批量数据的 DataFrame 处理和 CSV 导出 |
| aiohttp | 3.8.0 及以上 | 可选依赖，用于异步批量请求提升检测效率 |
| Flask | 2.2.0 及以上 | Web 服务框架，提供 API 接口 |
| click | 8.1.0 及以上 | 命令行工具框架，用于管理脚本 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何导入链接、如何查询已有链接、如何导出数据？ |
| 运维指南 | docs/ops-guide.md | 如何部署生产环境、如何配置数据库连接、如何进行批次管理？ |
| API 参考 | docs/api-reference.md | 对外提供哪些 RESTful 接口、请求与响应格式是什么、如何鉴权？ |
| 开发规范 | docs/development.md | 如何新增数据源适配器、如何编写单元测试、代码风格要求？ |
| 常见排错 | docs/troubleshooting.md | 链接检测超时怎么办、数据库连接失败如何处理、批次状态异常如何修复？ |

## 资源列表

- http://m.mobile.cmcvrr.cn/Article/065624.shtml
- http://m.mobile.cmcvrr.cn/Article/75131.shtml
- http://m.mobile.puhvjy.cn/Article/380605.shtml
- http://m.mobile.puhvjy.cn/Article/533240.shtml
- http://m.mobile.nwbbyt.cn/Article/696107.shtml
- http://m.mobile.puhvjy.cn/Article/6723573.shtml
- http://m.mobile.cmcvrr.cn/Article/4795455.shtml
- http://m.mobile.cmcvrr.cn/Article/4558.shtml
- http://m.mobile.nwbbyt.cn/Article/6362819.shtml
- http://m.mobile.jnjpgf.cn/Article/957695.shtml
- http://m.mobile.cmcvrr.cn/Article/7301478.shtml
- http://m.mobile.puhvjy.cn/Article/04247.shtml
- http://m.mobile.nwbbyt.cn/Article/05725.shtml
- http://m.mobile.jnjpgf.cn/Article/706509.shtml
- http://m.mobile.cmcvrr.cn/Article/6660645.shtml
- http://m.mobile.nwbbyt.cn/Article/723729.shtml
- http://m.mobile.puhvjy.cn/Article/598111.shtml
- http://m.mobile.puhvjy.cn/Article/3459.shtml
- http://m.mobile.puhvjy.cn/Article/1817.shtml
- http://m.mobile.nwbbyt.cn/Article/46217.shtml
- http://m.mobile.jnjpgf.cn/Article/18062.shtml
- http://m.mobile.jnjpgf.cn/Article/323505.shtml
- http://m.mobile.nwbbyt.cn/Article/1461.shtml
- http://m.mobile.puhvjy.cn/Article/7402.shtml
- http://m.mobile.cmcvrr.cn/Article/94915.shtml
- http://m.mobile.cmcvrr.cn/Article/4793.shtml
- http://m.mobile.nwbbyt.cn/Article/0379.shtml
- http://m.mobile.puhvjy.cn/Article/2583.shtml
- http://m.mobile.cmcvrr.cn/Article/9117.shtml
- http://m.mobile.puhvjy.cn/Article/2055.shtml
- http://m.mobile.nwbbyt.cn/Article/5631.shtml
- http://m.mobile.jnjpgf.cn/Article/5492.shtml
- http://m.mobile.puhvjy.cn/Article/3790.shtml
- http://m.mobile.puhvjy.cn/Article/251809.shtml
- http://m.mobile.nwbbyt.cn/Article/25798.shtml
- http://m.mobile.cmcvrr.cn/Article/249654.shtml
- http://m.mobile.cmcvrr.cn/Article/9939903.shtml
- http://m.mobile.puhvjy.cn/Article/24272.shtml
- http://m.mobile.jnjpgf.cn/Article/6118293.shtml
- http://m.mobile.jnjpgf.cn/Article/999034.shtml
- http://m.mobile.nwbbyt.cn/Article/4801.shtml
- http://m.mobile.nwbbyt.cn/Article/94063.shtml
- http://m.mobile.cmcvrr.cn/Article/4013.shtml
- http://m.mobile.cmcvrr.cn/Article/2467.shtml
- http://m.mobile.nwbbyt.cn/Article/56855.shtml
- http://m.mobile.nwbbyt.cn/Article/97254.shtml
- http://m.mobile.puhvjy.cn/Article/9714.shtml
- http://m.mobile.puhvjy.cn/Article/5340445.shtml
- http://m.mobile.nwbbyt.cn/Article/5395729.shtml
- http://m.mobile.nwbbyt.cn/Article/35631.shtml
- http://m.mobile.nwbbyt.cn/Article/4024196.shtml
- http://m.mobile.nwbbyt.cn/Article/2926089.shtml
- http://m.mobile.puhvjy.cn/Article/7769.shtml
- http://m.mobile.cmcvrr.cn/Article/0492.shtml
- http://m.mobile.puhvjy.cn/Article/15831.shtml
- http://m.mobile.puhvjy.cn/Article/1172745.shtml
- http://m.mobile.puhvjy.cn/Article/495549.shtml
- http://m.mobile.cmcvrr.cn/Article/57691.shtml
- http://m.mobile.cmcvrr.cn/Article/96937.shtml
- http://m.mobile.nwbbyt.cn/Article/0171.shtml
- http://m.mobile.nwbbyt.cn/Article/954008.shtml
- http://m.mobile.cmcvrr.cn/Article/792256.shtml
- http://m.mobile.cmcvrr.cn/Article/7660.shtml
- http://m.mobile.nwbbyt.cn/Article/5645.shtml
- http://m.mobile.jnjpgf.cn/Article/831212.shtml
- http://m.mobile.jnjpgf.cn/Article/653105.shtml
- http://m.mobile.nwbbyt.cn/Article/3096.shtml
- http://m.mobile.puhvjy.cn/Article/45828.shtml
- http://m.mobile.cmcvrr.cn/Article/63144.shtml
- http://m.mobile.jnjpgf.cn/Article/41218.shtml
- http://m.mobile.nwbbyt.cn/Article/9208.shtml
- http://m.mobile.nwbbyt.cn/Article/2048614.shtml
- http://m.mobile.cmcvrr.cn/Article/018323.shtml
- http://m.mobile.jnjpgf.cn/Article/8976.shtml
- http://m.mobile.puhvjy.cn/Article/679718.shtml
- http://m.mobile.cmcvrr.cn/Article/2347.shtml
- http://m.mobile.nwbbyt.cn/Article/558032.shtml
- http://m.mobile.nwbbyt.cn/Article/629676.shtml
- http://m.mobile.puhvjy.cn/Article/51827.shtml
- http://m.mobile.nwbbyt.cn/Article/2135233.shtml
- http://m.mobile.jnjpgf.cn/Article/316340.shtml
- http://m.mobile.jnjpgf.cn/Article/874311.shtml
- http://m.mobile.nwbbyt.cn/Article/6302893.shtml
- http://m.mobile.puhvjy.cn/Article/9324.shtml
- http://m.mobile.nwbbyt.cn/Article/692689.shtml
- http://m.mobile.jnjpgf.cn/Article/2697553.shtml
- http://m.mobile.jnjpgf.cn/Article/1595870.shtml
- http://m.mobile.nwbbyt.cn/Article/8279.shtml
- http://m.mobile.jnjpgf.cn/Article/1782456.shtml
- http://m.mobile.puhvjy.cn/Article/735069.shtml
- http://m.mobile.jnjpgf.cn/Article/6135.shtml
- http://m.mobile.nwbbyt.cn/Article/5170.shtml
- http://m.mobile.nwbbyt.cn/Article/42024.shtml
- http://m.mobile.nwbbyt.cn/Article/226771.shtml
- http://m.mobile.cmcvrr.cn/Article/9249.shtml
- http://m.mobile.cmcvrr.cn/Article/2562.shtml
- http://m.mobile.cmcvrr.cn/Article/3976.shtml
- http://m.mobile.cmcvrr.cn/Article/344391.shtml
- http://m.mobile.nwbbyt.cn/Article/3941952.shtml
- http://m.mobile.puhvjy.cn/Article/7324601.shtml
- http://m.mobile.nwbbyt.cn/Article/52240.shtml
- http://m.mobile.cmcvrr.cn/Article/2638.shtml
- http://m.mobile.puhvjy.cn/Article/9418.shtml
- http://m.mobile.nwbbyt.cn/Article/613167.shtml
- http://m.mobile.nwbbyt.cn/Article/1390838.shtml
- http://m.mobile.nwbbyt.cn/Article/761993.shtml
- http://m.mobile.puhvjy.cn/Article/3140589.shtml
- http://m.mobile.nwbbyt.cn/Article/8477426.shtml
- http://m.mobile.cmcvrr.cn/Article/08605.shtml
- http://m.mobile.cmcvrr.cn/Article/3486296.shtml
- http://m.mobile.puhvjy.cn/Article/55101.shtml
- http://m.mobile.puhvjy.cn/Article/4733212.shtml
- http://m.mobile.jnjpgf.cn/Article/644417.shtml
- http://m.mobile.nwbbyt.cn/Article/642709.shtml
- http://m.mobile.cmcvrr.cn/Article/2300241.shtml
- http://m.mobile.jnjpgf.cn/Article/78870.shtml
- http://m.mobile.jnjpgf.cn/Article/4861.shtml
- http://m.mobile.puhvjy.cn/Article/485771.shtml
- http://m.mobile.jnjpgf.cn/Article/9851481.shtml
- http://m.mobile.jnjpgf.cn/Article/6185907.shtml
- http://m.mobile.jnjpgf.cn/Article/0619.shtml
- http://m.mobile.cmcvrr.cn/Article/70406.shtml
- http://m.mobile.puhvjy.cn/Article/4482.shtml
- http://m.mobile.nwbbyt.cn/Article/009590.shtml
- http://m.mobile.nwbbyt.cn/Article/422768.shtml
- http://m.mobile.puhvjy.cn/Article/110818.shtml
- http://m.mobile.cmcvrr.cn/Article/45700.shtml
- http://m.mobile.jnjpgf.cn/Article/12881.shtml
- http://m.mobile.jnjpgf.cn/Article/235693.shtml
- http://m.mobile.nwbbyt.cn/Article/91964.shtml
- http://m.mobile.nwbbyt.cn/Article/1598037.shtml
- http://m.mobile.jnjpgf.cn/Article/591003.shtml
- http://m.mobile.jnjpgf.cn/Article/1729188.shtml
- http://m.mobile.puhvjy.cn/Article/6035.shtml
- http://m.mobile.jnjpgf.cn/Article/36460.shtml
- http://m.mobile.jnjpgf.cn/Article/0462.shtml
- http://m.mobile.puhvjy.cn/Article/41589.shtml
- http://m.mobile.puhvjy.cn/Article/4988544.shtml
- http://m.mobile.puhvjy.cn/Article/2907578.shtml
- http://m.mobile.cmcvrr.cn/Article/5893568.shtml
- http://m.mobile.jnjpgf.cn/Article/0187.shtml
- http://m.mobile.nwbbyt.cn/Article/85887.shtml
- http://m.mobile.puhvjy.cn/Article/1118.shtml
- http://m.mobile.cmcvrr.cn/Article/48896.shtml
- http://m.mobile.jnjpgf.cn/Article/0743.shtml
- http://m.mobile.cmcvrr.cn/Article/4401812.shtml
- http://m.mobile.jnjpgf.cn/Article/239643.shtml
- http://m.mobile.puhvjy.cn/Article/152775.shtml
- http://m.mobile.puhvjy.cn/Article/9577627.shtml
- http://m.mobile.jnjpgf.cn/Article/2607.shtml
- http://m.mobile.jnjpgf.cn/Article/40020.shtml
- http://m.mobile.nwbbyt.cn/Article/845916.shtml
- http://m.mobile.cmcvrr.cn/Article/0106868.shtml
- http://m.mobile.jnjpgf.cn/Article/3805563.shtml
- http://m.mobile.cmcvrr.cn/Article/20702.shtml
- http://m.mobile.jnjpgf.cn/Article/1221.shtml
- http://m.mobile.cmcvrr.cn/Article/23496.shtml
- http://m.mobile.puhvjy.cn/Article/7196564.shtml
- http://m.mobile.puhvjy.cn/Article/6665.shtml
- http://m.mobile.puhvjy.cn/Article/2070.shtml
- http://m.mobile.cmcvrr.cn/Article/5672.shtml
- http://m.mobile.jnjpgf.cn/Article/53244.shtml
- http://m.mobile.puhvjy.cn/Article/5357.shtml
- http://m.mobile.cmcvrr.cn/Article/3396025.shtml
- http://m.mobile.nwbbyt.cn/Article/5064.shtml
- http://m.mobile.jnjpgf.cn/Article/08150.shtml
- http://m.mobile.nwbbyt.cn/Article/488722.shtml
- http://m.mobile.nwbbyt.cn/Article/77341.shtml
- http://m.mobile.jnjpgf.cn/Article/2299069.shtml
- http://m.mobile.puhvjy.cn/Article/1322.shtml
- http://m.mobile.puhvjy.cn/Article/346411.shtml
- http://m.mobile.cmcvrr.cn/Article/60386.shtml
- http://m.mobile.puhvjy.cn/Article/301524.shtml
- http://m.mobile.puhvjy.cn/Article/2130.shtml
- http://m.mobile.nwbbyt.cn/Article/1998847.shtml
- http://m.mobile.jnjpgf.cn/Article/861185.shtml
- http://m.mobile.puhvjy.cn/Article/9665907.shtml
- http://m.mobile.puhvjy.cn/Article/0109.shtml
- http://m.mobile.jnjpgf.cn/Article/85808.shtml
- http://m.mobile.jnjpgf.cn/Article/231557.shtml
- http://m.mobile.puhvjy.cn/Article/47560.shtml
- http://m.mobile.nwbbyt.cn/Article/0233489.shtml
- http://m.mobile.jnjpgf.cn/Article/2100.shtml
- http://m.mobile.cmcvrr.cn/Article/618897.shtml
- http://m.mobile.puhvjy.cn/Article/460608.shtml
- http://m.mobile.puhvjy.cn/Article/199324.shtml
- http://m.mobile.jnjpgf.cn/Article/2479889.shtml
- http://m.mobile.cmcvrr.cn/Article/266785.shtml
- http://m.mobile.jnjpgf.cn/Article/96638.shtml
- http://m.mobile.puhvjy.cn/Article/02527.shtml
- http://m.mobile.cmcvrr.cn/Article/9368.shtml
- http://m.mobile.cmcvrr.cn/Article/552150.shtml
- http://m.mobile.cmcvrr.cn/Article/174878.shtml
- http://m.mobile.puhvjy.cn/Article/5794.shtml
- http://m.mobile.jnjpgf.cn/Article/983153.shtml
- http://m.mobile.cmcvrr.cn/Article/83900.shtml
- http://m.mobile.puhvjy.cn/Article/0643433.shtml
- http://m.mobile.nwbbyt.cn/Article/698436.shtml
- http://m.mobile.jnjpgf.cn/Article/5250.shtml
- http://m.mobile.puhvjy.cn/Article/9998.shtml
- http://m.mobile.nwbbyt.cn/Article/170291.shtml
- http://m.mobile.cmcvrr.cn/Article/0776.shtml
- http://m.mobile.jnjpgf.cn/Article/20029.shtml
- http://m.mobile.puhvjy.cn/Article/9741.shtml
- http://m.mobile.puhvjy.cn/Article/01779.shtml
- http://m.mobile.jnjpgf.cn/Article/8596.shtml
- http://m.mobile.jnjpgf.cn/Article/1763410.shtml
- http://m.mobile.nwbbyt.cn/Article/35384.shtml
- http://m.mobile.cmcvrr.cn/Article/8278242.shtml
- http://m.mobile.jnjpgf.cn/Article/5487.shtml
- http://m.mobile.nwbbyt.cn/Article/1275.shtml
- http://m.mobile.cmcvrr.cn/Article/7096.shtml
- http://m.mobile.cmcvrr.cn/Article/848573.shtml
- http://m.mobile.jnjpgf.cn/Article/709436.shtml
- http://m.mobile.puhvjy.cn/Article/6023.shtml
- http://m.mobile.nwbbyt.cn/Article/309767.shtml
- http://m.mobile.jnjpgf.cn/Article/4486.shtml
- http://m.mobile.puhvjy.cn/Article/2278.shtml
- http://m.mobile.puhvjy.cn/Article/70882.shtml
- http://m.mobile.jnjpgf.cn/Article/7929186.shtml
- http://m.mobile.nwbbyt.cn/Article/888120.shtml
- http://m.mobile.cmcvrr.cn/Article/54816.shtml
- http://m.mobile.cmcvrr.cn/Article/3202.shtml
- http://m.mobile.cmcvrr.cn/Article/566215.shtml
- http://m.mobile.cmcvrr.cn/Article/0810.shtml
- http://m.mobile.jnjpgf.cn/Article/69141.shtml
- http://m.mobile.puhvjy.cn/Article/08697.shtml
- http://m.mobile.jnjpgf.cn/Article/5977486.shtml
- http://m.mobile.nwbbyt.cn/Article/0886.shtml
- http://m.mobile.nwbbyt.cn/Article/25371.shtml
- http://m.mobile.cmcvrr.cn/Article/1956998.shtml
- http://m.mobile.nwbbyt.cn/Article/36282.shtml
- http://m.mobile.nwbbyt.cn/Article/182605.shtml
- http://m.mobile.cmcvrr.cn/Article/412222.shtml
- http://m.mobile.jnjpgf.cn/Article/3239376.shtml
- http://m.mobile.puhvjy.cn/Article/5725.shtml
- http://m.mobile.cmcvrr.cn/Article/26807.shtml
- http://m.mobile.puhvjy.cn/Article/29226.shtml
- http://m.mobile.nwbbyt.cn/Article/9236.shtml
- http://m.mobile.cmcvrr.cn/Article/23027.shtml
- http://m.mobile.cmcvrr.cn/Article/4806553.shtml
- http://m.mobile.jnjpgf.cn/Article/923568.shtml
- http://m.mobile.cmcvrr.cn/Article/61565.shtml
- http://m.mobile.jnjpgf.cn/Article/067097.shtml
- http://m.mobile.jnjpgf.cn/Article/789013.shtml
- http://m.mobile.puhvjy.cn/Article/383173.shtml
- http://m.mobile.jnjpgf.cn/Article/28662.shtml
- http://m.mobile.nwbbyt.cn/Article/7201836.shtml
- http://m.mobile.jnjpgf.cn/Article/7007.shtml
- http://m.mobile.puhvjy.cn/Article/7565.shtml

## 项目结构

```
mlas-service/
├── app.py                         # Flask 应用入口，注册路由和启动服务
├── config.yaml                    # 配置文件，包含数据库连接、批次参数、检测间隔
├── requirements.txt               # Python 依赖声明
├── README.md                      # 项目说明文档（本文档）
├── docs/                          # 文档目录
│   ├── user-guide.md              # 用户手册：导入、查询、导出操作说明
│   ├── ops-guide.md               # 运维指南：部署、备份、监控
│   ├── api-reference.md           # API 参考：端点定义与示例
│   ├── development.md             # 开发规范：代码结构与测试
│   └── troubleshooting.md         # 常见排错：错误码与解决方案
├── mlas/                          # 核心源代码包
│   ├── __init__.py
│   ├── models.py                  # 数据模型定义（链接、批次、状态）
│   ├── parser.py                  # URL 解析器：提取域名、文章 ID、来源
│   ├── checker.py                 # 链接检测器：HTTP 状态码与响应时间
│   ├── importer.py                # 批量导入器：去重与入库逻辑
│   ├── exporter.py                # 导出器：JSON/CSV 格式输出
│   └── utils.py                   # 工具函数：日志、时间转换、哈希计算
├── scripts/                       # 独立脚本
│   ├── init_db.py                 # 初始化数据库表结构
│   ├── batch_import.py            # 命令行批量导入工具
│   ├── run_checker.py             # 手动触发链接检测
│   └── migrate_schema.py          # 数据库结构迁移
├── tests/                         # 单元测试目录
│   ├── test_parser.py             # URL 解析器测试
│   ├── test_checker.py            # 链接检测器测试
│   └── test_importer.py           # 导入器集成测试
├── data/                          # 数据存储目录（SQLite 默认位置）
│   └── mlas.db                    # SQLite 数据库文件
└── logs/                          # 日志目录
    ├── app.log                    # 应用运行日志
    └── checker.log                # 链接检测任务日志
```

## 贡献指南

1. 阅读项目开发规范文档 `docs/development.md`，了解代码风格要求、测试标准和 Git 提交信息格式。
2. 在 GitHub Issues 中查找或新建一个 Issue，说明你希望修复的问题或新增的功能，等待维护者确认。
3. Fork 本项目并创建以 `feature/` 或 `fix/` 为前缀的分支，基于 `main` 分支进行开发。
4. 完成代码修改后，运行已有单元测试并新增针对修改内容的测试用例，确保所有测试通过。
5. 提交 Pull Request，在描述中关联对应的 Issue 编号，并详细说明改动点与测试结果。

## 常见问题

**Q：批量导入时出现重复链接如何处理？**

A：MLAS 在导入过程中会自动基于 URL 的 SHA256 哈希值和文章 ID 进行双重去重。重复链接不会再次写入数据库，但会在日志中记录冲突信息。你可以通过配置 `config.yaml` 中的 `dedup.strategy` 字段选择严格模式或宽松模式。

**Q：链接检测失败的原因有哪些？**

A：常见原因包括目标服务器返回 4xx/5xx 状态码、网络超时、DNS 解析失败、SSL 证书问题（针对 HTTPS 链接）以及目标页面被移动或删除。检测器会记录具体的错误类型，建议结合 `logs/checker.log` 中的详细错误信息进行排查。

**Q：如何迁移数据库从 SQLite 到 PostgreSQL？**

A：项目提供了迁移脚本 `scripts/migrate_schema.py`，执行时需在 `config.yaml` 中配置 PostgreSQL 连接字符串，然后运行该脚本即可自动导出 SQLite 数据并导入 PostgreSQL。迁移完成后请更新配置文件中的 `database.url` 字段。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
