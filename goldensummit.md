# MobileLink 聚合站

MobileLink 聚合站是一个面向移动端开发者和技术内容研究者的外链资源归集系统。本项目并非内容生产平台，而是对分散在多个移动端技术站点上的高质量技术文章、案例分析及开发文档进行结构化整理与索引的元数据聚合层。项目目标用户包括移动端架构师、跨平台框架维护者、性能调优工程师以及技术决策者，帮助其从大量非结构化的技术文本中快速定位与自身工作相关的参考资料。

本项目通过对特定域名下文章资源的采集与分类，形成一套可检索、可订阅、可版本化的外链数据库。项目本身不存储任何文章正文或版权内容，仅保留文章标题、摘要哈希、发布时间戳及原始 URL 指纹，确保合规性。当前批次为第 36/80 批，共计归集 250 个外链资源，覆盖 5 个独立二级域名下的技术文章目录。

## 功能概览

多源外链统一归集：支持对 cmcvrr、puhvjy、nwbbyt、jnjpgf 等移动端技术站点的 Article 目录进行自动化采集与链接去重。

资源指纹防重机制：基于 URL 路径末尾的数字 ID 生成 SHA-256 指纹，避免同一文章在不同批次中重复录入。

批次化管理能力：项目采用 80 个批次的滚动采集策略，当前第 36 批，每批固定 250 条链接，便于增量更新与回溯。

原始链接保真输出：对所有收录的 URL 严格保持原始协议头、域名大小写及路径格式，不进行任何自动补全或规范化改写，确保溯源准确性。

结构化元数据提取：从 URL 路径中解析域名主体与文章数字编号，生成可供后续分析与报表使用的结构化字段。

纯静态站点生成：项目构建产物为完整的 HTML 目录页与 JSON 索引文件，可托管于任意静态服务器或 CDN，无需数据库支持。

命令行交互工具：提供 CLI 脚本用于手动触发采集、校验链接可用性以及导出不同格式的资源列表（Markdown、CSV、JSON）。

访问日志审计：记录每次采集任务的开始时间、结束时间、成功获取状态码分布及失败链接清单，便于运维监控。

## 应用场景

移动端技术周报编辑。技术编辑或社区运营人员可通过 MobileLink 聚合站快速获取本周新增的技术文章链接，从中筛选出高质量内容编入周报，无需逐个访问多个技术博客站点进行人工检索。

项目技术选型调研。架构师在进行跨平台框架或 UI 组件库选型时，可查阅聚合站中与特定关键词相关的历史文章链接，通过原文获取实际案例分析、性能对比数据及踩坑记录，辅助决策。

自动化外链监控。DevOps 工程师可配置定时任务调用项目 CLI 工具，将新增链接推送到企业微信或钉钉机器人，实现对特定域名下技术内容更新的实时感知。

数据归档与溯源。研究员或审计人员可基于批次号和时间范围导出某段时间内的所有外链清单，用于引用追溯、版权合规检查或内容演变趋势分析。

离线阅读准备。移动端开发者在网络受限环境中，可先通过聚合站导出链接清单，再利用批量下载工具预先获取文章正文进行离线阅读。

## 快速开始

以下命令序列适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/mobilelink-aggregator.git
cd mobilelink-aggregator

# 安装项目依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 运行采集任务，指定批次编号为 36
python cli.py collect --batch 36 --output ./data/batch_36.json

# 生成 Markdown 资源列表
python cli.py export --input ./data/batch_36.json --format markdown --output ./docs/batch_36.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9.0 及以上 | 核心采集与处理脚本运行时环境 |
| requests | 2.28.0 及以上 | 用于发起 HTTP 请求获取文章元数据 |
| beautifulsoup4 | 4.11.0 及以上 | 可选依赖，用于解析 HTML 标题与摘要 |
| lxml | 4.9.0 及以上 | 与 beautifulsoup4 配合使用的解析器后端 |
| pytest | 7.2.0 及以上 | 单元测试与集成测试执行框架 |
| click | 8.1.0 及以上 | CLI 命令行交互界面构建库 |
| python-dotenv | 1.0.0 及以上 | 管理环境变量，如请求超时与重试次数 |
| setuptools | 65.0.0 及以上 | 项目打包与分发工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何配置采集源、调整批次大小、导出不同格式资源列表？ |
| 开发者指南 | docs/developer-guide.md | 如何扩展新的域名采集器、修改指纹算法、增加自定义过滤器？ |
| 运维手册 | docs/operations.md | 如何部署定时任务、监控采集任务状态、处理失败重试？ |
| 设计文档 | docs/design.md | 项目整体架构设计、数据流图、指纹去重策略与存储方案是什么？ |
| API 参考 | docs/api-reference.md | CLI 子命令的完整参数列表、环境变量配置项及返回码含义？ |
| 变更日志 | CHANGELOG.md | 每个版本新增功能、修复缺陷与不兼容变更记录？ |

## 资源列表

- http://www.mobile.cmcvrr.cn/Article/7172.shtml
- http://www.mobile.puhvjy.cn/Article/000425.shtml
- http://www.mobile.nwbbyt.cn/Article/0162.shtml
- http://www.mobile.puhvjy.cn/Article/9632495.shtml
- http://www.mobile.jnjpgf.cn/Article/190942.shtml
- http://www.mobile.nwbbyt.cn/Article/88695.shtml
- http://www.mobile.cmcvrr.cn/Article/3856146.shtml
- http://www.mobile.jnjpgf.cn/Article/825098.shtml
- http://www.mobile.puhvjy.cn/Article/8367.shtml
- http://www.mobile.cmcvrr.cn/Article/25604.shtml
- http://www.mobile.puhvjy.cn/Article/1715.shtml
- http://www.mobile.cmcvrr.cn/Article/7046.shtml
- http://www.mobile.jnjpgf.cn/Article/513695.shtml
- http://www.mobile.nwbbyt.cn/Article/44536.shtml
- http://www.mobile.nwbbyt.cn/Article/51503.shtml
- http://www.mobile.puhvjy.cn/Article/66943.shtml
- http://www.mobile.jnjpgf.cn/Article/274868.shtml
- http://www.mobile.puhvjy.cn/Article/74489.shtml
- http://www.mobile.puhvjy.cn/Article/9113.shtml
- http://www.mobile.nwbbyt.cn/Article/119855.shtml
- http://www.mobile.cmcvrr.cn/Article/386783.shtml
- http://www.mobile.cmcvrr.cn/Article/8214452.shtml
- http://www.mobile.cmcvrr.cn/Article/519015.shtml
- http://www.mobile.puhvjy.cn/Article/0034681.shtml
- http://www.mobile.puhvjy.cn/Article/00330.shtml
- http://www.mobile.nwbbyt.cn/Article/3862127.shtml
- http://www.mobile.jnjpgf.cn/Article/0166575.shtml
- http://www.mobile.cmcvrr.cn/Article/59636.shtml
- http://www.mobile.cmcvrr.cn/Article/0818492.shtml
- http://www.mobile.cmcvrr.cn/Article/4275.shtml
- http://www.mobile.puhvjy.cn/Article/956950.shtml
- http://www.mobile.cmcvrr.cn/Article/972871.shtml
- http://www.mobile.nwbbyt.cn/Article/6813006.shtml
- http://www.mobile.puhvjy.cn/Article/11612.shtml
- http://www.mobile.puhvjy.cn/Article/6272.shtml
- http://www.mobile.nwbbyt.cn/Article/20242.shtml
- http://www.mobile.cmcvrr.cn/Article/9688.shtml
- http://www.mobile.cmcvrr.cn/Article/2462076.shtml
- http://www.mobile.puhvjy.cn/Article/8797.shtml
- http://www.mobile.nwbbyt.cn/Article/356769.shtml
- http://www.mobile.puhvjy.cn/Article/352772.shtml
- http://www.mobile.cmcvrr.cn/Article/6767867.shtml
- http://www.mobile.jnjpgf.cn/Article/830095.shtml
- http://www.mobile.puhvjy.cn/Article/00462.shtml
- http://www.mobile.puhvjy.cn/Article/319653.shtml
- http://www.mobile.nwbbyt.cn/Article/43597.shtml
- http://www.mobile.cmcvrr.cn/Article/2358310.shtml
- http://www.mobile.puhvjy.cn/Article/8865757.shtml
- http://www.mobile.puhvjy.cn/Article/570334.shtml
- http://www.mobile.cmcvrr.cn/Article/1192085.shtml
- http://www.mobile.puhvjy.cn/Article/04522.shtml
- http://www.mobile.puhvjy.cn/Article/293357.shtml
- http://www.mobile.cmcvrr.cn/Article/837178.shtml
- http://www.mobile.nwbbyt.cn/Article/7548730.shtml
- http://www.mobile.nwbbyt.cn/Article/795442.shtml
- http://www.mobile.jnjpgf.cn/Article/8145360.shtml
- http://www.mobile.nwbbyt.cn/Article/4471.shtml
- http://www.mobile.jnjpgf.cn/Article/4391.shtml
- http://www.mobile.jnjpgf.cn/Article/385286.shtml
- http://www.mobile.nwbbyt.cn/Article/667967.shtml
- http://www.mobile.puhvjy.cn/Article/3647.shtml
- http://www.mobile.cmcvrr.cn/Article/8878.shtml
- http://www.mobile.cmcvrr.cn/Article/83433.shtml
- http://www.mobile.cmcvrr.cn/Article/250253.shtml
- http://www.mobile.cmcvrr.cn/Article/508113.shtml
- http://www.mobile.jnjpgf.cn/Article/314496.shtml
- http://www.mobile.cmcvrr.cn/Article/6935.shtml
- http://www.mobile.jnjpgf.cn/Article/5549.shtml
- http://www.mobile.puhvjy.cn/Article/520677.shtml
- http://www.mobile.puhvjy.cn/Article/36280.shtml
- http://www.mobile.jnjpgf.cn/Article/88903.shtml
- http://www.mobile.puhvjy.cn/Article/89032.shtml
- http://www.mobile.cmcvrr.cn/Article/45520.shtml
- http://www.mobile.jnjpgf.cn/Article/556066.shtml
- http://www.mobile.cmcvrr.cn/Article/41028.shtml
- http://www.mobile.cmcvrr.cn/Article/0528446.shtml
- http://www.mobile.puhvjy.cn/Article/69199.shtml
- http://www.mobile.cmcvrr.cn/Article/5327066.shtml
- http://www.mobile.nwbbyt.cn/Article/9680.shtml
- http://www.mobile.puhvjy.cn/Article/890136.shtml
- http://www.mobile.nwbbyt.cn/Article/52888.shtml
- http://www.mobile.nwbbyt.cn/Article/18831.shtml
- http://www.mobile.puhvjy.cn/Article/653365.shtml
- http://www.mobile.nwbbyt.cn/Article/42391.shtml
- http://www.mobile.jnjpgf.cn/Article/906789.shtml
- http://www.mobile.cmcvrr.cn/Article/589822.shtml
- http://www.mobile.nwbbyt.cn/Article/1943156.shtml
- http://www.mobile.puhvjy.cn/Article/315818.shtml
- http://www.mobile.puhvjy.cn/Article/856965.shtml
- http://www.mobile.cmcvrr.cn/Article/745535.shtml
- http://www.mobile.puhvjy.cn/Article/7394.shtml
- http://www.mobile.puhvjy.cn/Article/090485.shtml
- http://www.mobile.cmcvrr.cn/Article/6221.shtml
- http://www.mobile.jnjpgf.cn/Article/61320.shtml
- http://www.mobile.puhvjy.cn/Article/80202.shtml
- http://www.mobile.jnjpgf.cn/Article/5697.shtml
- http://www.mobile.nwbbyt.cn/Article/01503.shtml
- http://www.mobile.nwbbyt.cn/Article/8268.shtml
- http://www.mobile.jnjpgf.cn/Article/86289.shtml
- http://www.mobile.cmcvrr.cn/Article/2758.shtml
- http://www.mobile.puhvjy.cn/Article/528151.shtml
- http://www.mobile.cmcvrr.cn/Article/60763.shtml
- http://www.mobile.jnjpgf.cn/Article/387922.shtml
- http://www.mobile.nwbbyt.cn/Article/3474231.shtml
- http://www.mobile.jnjpgf.cn/Article/7544158.shtml
- http://www.mobile.cmcvrr.cn/Article/8373968.shtml
- http://www.mobile.nwbbyt.cn/Article/324983.shtml
- http://www.mobile.nwbbyt.cn/Article/6082.shtml
- http://www.mobile.puhvjy.cn/Article/270459.shtml
- http://www.mobile.puhvjy.cn/Article/621504.shtml
- http://www.mobile.puhvjy.cn/Article/243660.shtml
- http://www.mobile.jnjpgf.cn/Article/24191.shtml
- http://www.mobile.jnjpgf.cn/Article/24919.shtml
- http://www.mobile.jnjpgf.cn/Article/4313.shtml
- http://www.mobile.puhvjy.cn/Article/7151.shtml
- http://www.mobile.nwbbyt.cn/Article/584760.shtml
- http://www.mobile.jnjpgf.cn/Article/8982528.shtml
- http://www.mobile.cmcvrr.cn/Article/6455604.shtml
- http://www.mobile.nwbbyt.cn/Article/7671.shtml
- http://www.mobile.nwbbyt.cn/Article/93633.shtml
- http://www.mobile.puhvjy.cn/Article/0633644.shtml
- http://www.mobile.jnjpgf.cn/Article/0203199.shtml
- http://www.mobile.cmcvrr.cn/Article/5000384.shtml
- http://www.mobile.jnjpgf.cn/Article/8703830.shtml
- http://www.mobile.nwbbyt.cn/Article/9902034.shtml
- http://www.mobile.cmcvrr.cn/Article/9708409.shtml
- http://www.mobile.cmcvrr.cn/Article/749137.shtml
- http://www.mobile.jnjpgf.cn/Article/8424742.shtml
- http://www.mobile.nwbbyt.cn/Article/50582.shtml
- http://www.mobile.cmcvrr.cn/Article/21562.shtml
- http://www.mobile.nwbbyt.cn/Article/5465.shtml
- http://www.mobile.jnjpgf.cn/Article/495759.shtml
- http://www.mobile.nwbbyt.cn/Article/512649.shtml
- http://www.mobile.puhvjy.cn/Article/4321110.shtml
- http://www.mobile.cmcvrr.cn/Article/6253.shtml
- http://www.mobile.jnjpgf.cn/Article/1262.shtml
- http://www.mobile.jnjpgf.cn/Article/6857.shtml
- http://www.mobile.puhvjy.cn/Article/0038677.shtml
- http://www.mobile.cmcvrr.cn/Article/462618.shtml
- http://www.mobile.puhvjy.cn/Article/3024081.shtml
- http://www.mobile.puhvjy.cn/Article/3112636.shtml
- http://www.mobile.nwbbyt.cn/Article/7308440.shtml
- http://www.mobile.jnjpgf.cn/Article/9294.shtml
- http://www.mobile.jnjpgf.cn/Article/102634.shtml
- http://www.mobile.puhvjy.cn/Article/964194.shtml
- http://www.mobile.nwbbyt.cn/Article/6372.shtml
- http://www.mobile.nwbbyt.cn/Article/61008.shtml
- http://www.mobile.jnjpgf.cn/Article/195250.shtml
- http://www.mobile.cmcvrr.cn/Article/4246.shtml
- http://www.mobile.jnjpgf.cn/Article/1527041.shtml
- http://www.mobile.jnjpgf.cn/Article/62698.shtml
- http://www.mobile.nwbbyt.cn/Article/059243.shtml
- http://www.mobile.jnjpgf.cn/Article/25386.shtml
- http://www.mobile.nwbbyt.cn/Article/167341.shtml
- http://www.mobile.jnjpgf.cn/Article/0850.shtml
- http://www.mobile.cmcvrr.cn/Article/7313.shtml
- http://www.mobile.jnjpgf.cn/Article/232339.shtml
- http://www.mobile.cmcvrr.cn/Article/4608.shtml
- http://www.mobile.nwbbyt.cn/Article/843663.shtml
- http://www.mobile.jnjpgf.cn/Article/0469727.shtml
- http://www.mobile.nwbbyt.cn/Article/032241.shtml
- http://www.mobile.jnjpgf.cn/Article/6945.shtml
- http://www.mobile.jnjpgf.cn/Article/0827.shtml
- http://www.mobile.cmcvrr.cn/Article/809920.shtml
- http://www.mobile.jnjpgf.cn/Article/30235.shtml
- http://www.mobile.cmcvrr.cn/Article/84283.shtml
- http://www.mobile.puhvjy.cn/Article/3589599.shtml
- http://www.mobile.puhvjy.cn/Article/27794.shtml
- http://www.mobile.cmcvrr.cn/Article/3945.shtml
- http://www.mobile.nwbbyt.cn/Article/46841.shtml
- http://www.mobile.jnjpgf.cn/Article/113001.shtml
- http://www.mobile.puhvjy.cn/Article/700359.shtml
- http://www.mobile.jnjpgf.cn/Article/4909673.shtml
- http://www.mobile.nwbbyt.cn/Article/595948.shtml
- http://www.mobile.nwbbyt.cn/Article/8002245.shtml
- http://www.mobile.jnjpgf.cn/Article/1904.shtml
- http://www.mobile.puhvjy.cn/Article/633805.shtml
- http://www.mobile.puhvjy.cn/Article/6431.shtml
- http://www.mobile.cmcvrr.cn/Article/2174.shtml
- http://www.mobile.jnjpgf.cn/Article/7836.shtml
- http://www.mobile.jnjpgf.cn/Article/0094.shtml
- http://www.mobile.puhvjy.cn/Article/9660757.shtml
- http://www.mobile.puhvjy.cn/Article/9184799.shtml
- http://www.mobile.cmcvrr.cn/Article/3638803.shtml
- http://www.mobile.cmcvrr.cn/Article/36043.shtml
- http://www.mobile.nwbbyt.cn/Article/3372822.shtml
- http://www.mobile.jnjpgf.cn/Article/001100.shtml
- http://www.mobile.jnjpgf.cn/Article/1022.shtml
- http://www.mobile.nwbbyt.cn/Article/3862.shtml
- http://www.mobile.nwbbyt.cn/Article/31389.shtml
- http://www.mobile.puhvjy.cn/Article/52463.shtml
- http://www.mobile.nwbbyt.cn/Article/553594.shtml
- http://www.mobile.nwbbyt.cn/Article/793859.shtml
- http://www.mobile.puhvjy.cn/Article/2549942.shtml
- http://www.mobile.nwbbyt.cn/Article/8945.shtml
- http://www.mobile.jnjpgf.cn/Article/1091.shtml
- http://www.mobile.cmcvrr.cn/Article/0566958.shtml
- http://www.mobile.puhvjy.cn/Article/88524.shtml
- http://www.mobile.nwbbyt.cn/Article/2871.shtml
- http://www.mobile.nwbbyt.cn/Article/5020.shtml
- http://www.mobile.cmcvrr.cn/Article/6527028.shtml
- http://www.mobile.cmcvrr.cn/Article/20192.shtml
- http://www.mobile.cmcvrr.cn/Article/8404.shtml
- http://www.mobile.jnjpgf.cn/Article/4284.shtml
- http://www.mobile.jnjpgf.cn/Article/9584.shtml
- http://www.mobile.puhvjy.cn/Article/248663.shtml
- http://www.mobile.jnjpgf.cn/Article/8294327.shtml
- http://www.mobile.jnjpgf.cn/Article/7507.shtml
- http://www.mobile.puhvjy.cn/Article/8853.shtml
- http://www.mobile.nwbbyt.cn/Article/84202.shtml
- http://www.mobile.nwbbyt.cn/Article/7016919.shtml
- http://www.mobile.jnjpgf.cn/Article/3957.shtml
- http://www.mobile.cmcvrr.cn/Article/6357849.shtml
- http://www.mobile.jnjpgf.cn/Article/8014.shtml
- http://www.mobile.cmcvrr.cn/Article/1475698.shtml
- http://www.mobile.nwbbyt.cn/Article/7775804.shtml
- http://www.mobile.nwbbyt.cn/Article/260512.shtml
- http://www.mobile.puhvjy.cn/Article/893362.shtml
- http://www.mobile.cmcvrr.cn/Article/1109.shtml
- http://www.mobile.nwbbyt.cn/Article/5739.shtml
- http://www.mobile.nwbbyt.cn/Article/0715.shtml
- http://www.mobile.jnjpgf.cn/Article/6896.shtml
- http://www.mobile.puhvjy.cn/Article/3080933.shtml
- http://www.mobile.jnjpgf.cn/Article/7947.shtml
- http://www.mobile.cmcvrr.cn/Article/20156.shtml
- http://www.mobile.jnjpgf.cn/Article/0414.shtml
- http://www.mobile.jnjpgf.cn/Article/7995.shtml
- http://www.mobile.cmcvrr.cn/Article/1357.shtml
- http://www.mobile.cmcvrr.cn/Article/73990.shtml
- http://www.mobile.cmcvrr.cn/Article/9920.shtml
- http://www.mobile.puhvjy.cn/Article/72694.shtml
- http://www.mobile.nwbbyt.cn/Article/007867.shtml
- http://www.mobile.puhvjy.cn/Article/6242945.shtml
- http://www.mobile.puhvjy.cn/Article/104362.shtml
- http://www.mobile.cmcvrr.cn/Article/4517788.shtml
- http://www.mobile.puhvjy.cn/Article/804610.shtml
- http://www.mobile.nwbbyt.cn/Article/392800.shtml
- http://www.mobile.puhvjy.cn/Article/0562223.shtml
- http://www.mobile.puhvjy.cn/Article/383872.shtml
- http://www.mobile.jnjpgf.cn/Article/39156.shtml
- http://www.mobile.jnjpgf.cn/Article/9556282.shtml
- http://www.mobile.cmcvrr.cn/Article/513789.shtml
- http://www.mobile.puhvjy.cn/Article/796822.shtml
- http://www.mobile.jnjpgf.cn/Article/1511.shtml
- http://www.mobile.nwbbyt.cn/Article/3670284.shtml
- http://www.mobile.nwbbyt.cn/Article/423964.shtml
- http://www.mobile.jnjpgf.cn/Article/8071108.shtml
- http://www.mobile.puhvjy.cn/Article/88222.shtml
- http://www.mobile.cmcvrr.cn/Article/211181.shtml
- http://www.mobile.jnjpgf.cn/Article/300914.shtml

## 项目结构

```
mobilelink-aggregator/
├── cli.py                      # 命令行入口，注册 collect/export/validate 子命令
├── requirements.txt            # Python 依赖清单，固定版本号以保持可复现性
├── setup.py                    # 项目打包配置，定义入口点与元数据
├── src/                        # 核心源代码目录
│   ├── collector/              # 采集器模块
│   │   ├── base.py             # 抽象采集器基类，定义 fetch/parse/persist 接口
│   │   ├── cmcvrr.py           # cmcvrr.cn 域名的具体采集实现
│   │   ├── puhvjy.py           # puhvjy.cn 域名的具体采集实现
│   │   └── registry.py         # 采集器注册表，根据域名动态加载对应类
│   ├── fingerprint/            # 指纹计算模块
│   │   ├── hasher.py           # SHA-256 与 MD5 双指纹生成器
│   │   └── cache.py            # 基于 SQLite 的指纹持久化缓存
│   ├── exporter/               # 导出模块
│   │   ├── markdown.py         # 生成 Markdown 格式资源列表
│   │   ├── csv.py              # 生成 CSV 表格，含文章编号与域名分列
│   │   └── json.py             # 生成结构化 JSON，用于前端渲染或 API 消费
│   └── utils/                  # 通用工具函数
│       ├── http.py             # 带重试与超时控制的 requests 封装
│       └── logger.py           # 基于 logging 的日志配置与格式化
├── tests/                      # 测试套件
│   ├── unit/                   # 单元测试，覆盖哈希计算与 URL 解析逻辑
│   └── integration/            # 集成测试，模拟真实 HTTP 响应进行端到端验证
├── docs/                       # 文档目录
│   ├── user-guide.md
│   ├── developer-guide.md
│   ├── operations.md
│   ├── design.md
│   └── api-reference.md
├── data/                       # 数据存储目录（不纳入版本控制）
│   ├── batches/                # 按批次号存储的 JSON 结果文件
│   └── cache/                  # 指纹缓存 SQLite 数据库文件
├── scripts/                    # 运维辅助脚本
│   ├── cron_daily.sh           # 每日定时采集的 crontab 调用脚本
│   └── notify.sh               # 采集完成后发送通知的 webhook 脚本
├── config.yaml                 # 项目配置文件，含超时时间、重试次数与目标域名列表
└── CHANGELOG.md                # 版本变更历史记录
```

## 贡献指南

1. 复刻项目仓库并在本地克隆复刻后的副本，创建以 feature/ 或 fix/ 为前缀的分支进行开发。确保分支名称简洁描述本次变更内容。

2. 在 src/collector/ 目录下新增域名采集器时，需继承 base.py 中的 BaseCollector 抽象类，并实现 fetch_metadata 与 parse_article_id 两个抽象方法。新增采集器完成后，须在 registry.py 中完成注册。

3. 所有新增或修改的代码必须附带对应的单元测试用例，放置在 tests/unit/ 目录下，测试覆盖率不得低于 85%。运行 pytest 命令确保全部测试通过后方可提交。

4. 提交代码前执行 pre-commit 钩子进行代码风格检查（基于 flake8 与 black），确保符合 PEP 8 规范。提交信息需遵循 Conventional Commits 格式，即 feat:、fix:、docs:、refactor: 等类型前缀。

5. 发起 Pull Request 至主仓库的 develop 分支，在 PR 描述中说明变更动机、影响范围及测试结果。至少需要一名项目维护者审核通过后，方可合并至 develop 分支。

## 常见问题

Q: 采集过程中出现 HTTP 429 或 503 错误如何处理？

A: 项目内置了指数退避重试机制，默认最大重试次数为 5 次，初始退避间隔为 1 秒。若持续失败，请检查网络环境或目标站点是否临时不可用。用户可通过 config.yaml 中的 retry.max_attempts 和 retry.backoff_factor 调整重试参数。对于持续失败的链接，系统会在日志中记录并跳过，不影响后续链接采集。

Q: 如何确保不同批次的资源列表不会重复收录同一篇文章？

A: 项目使用 URL 路径末尾的数字 ID 结合域名主体生成 SHA-256 指纹，并在 data/cache/ 目录下维护一个全局指纹库。每次采集新批次时，系统会先计算每个 URL 的指纹并与历史指纹库比对，若命中则自动跳过该链接，确保同一篇文章只出现在首次收录的批次中。指纹库支持手动重置或导出备份。

Q: 项目能否采集需要登录或带有反爬机制的站点？

A: 当前版本仅支持公开可访问的静态 HTML 页面。对于需要 Cookie 认证、JavaScript 动态渲染或具有严格反爬策略的站点，项目暂不提供原生支持。建议用户在采集此类站点时，通过配置代理池或使用 Selenium/Playwright 等浏览器自动化工具作为前置数据获取层，然后将获取到的 HTML 内容通过适配器传入项目的解析模块。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
