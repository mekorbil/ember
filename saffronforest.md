# Mobile Article Aggregator Service (MAAS)

Mobile Article Aggregator Service (MAAS) 是一个面向移动端内容聚合与分发的技术资源索引系统，专为需要批量采集、归档和检索移动端 HTML 文章资源的开发者与数据分析团队设计。MAAS 并非传统的内容管理系统，而是一套轻量级的 URL 资源网关，能够将散落在多个移动子域名下的文章链接进行统一归集，并提供基于正则匹配的快速筛选能力。

MAAS 的核心目标用户包括：数据采集工程师、移动端内容运营人员、SEO 分析师以及从事自然语言处理（NLP）语料构建的研究者。通过 MAAS，用户无需手动整理来自不同来源的移动文章链接，即可获得结构化的资源清单，并能够与下游的爬虫调度器或内容解析管道无缝对接。

## 功能概览

批量资源归集：支持一次性导入超过 200 条移动端文章 URL，自动识别来源域名并分组展示。

域名状态探测：内置 HTTP 头部检测模块，可快速标记每个 URL 的响应状态码与内容类型。

正则表达式过滤器：允许用户基于文章 ID 数字段或路径特征编写正则规则，实现精准筛选。

元数据提取存根：自动提取 URL 中的 Article ID 字段，生成可用于后续数据库索引的整数键值。

Markdown 原生输出：所有资源列表以纯文本格式呈现，保证与各类文档管理系统和版本控制工具的兼容性。

无状态设计：MAAS 不依赖后端数据库或缓存服务，所有处理流程均在单次请求上下文中完成，便于水平扩展。

跨平台兼容：基于 Python 3.9+ 开发，可在 Linux、macOS 和 Windows 系统的终端环境中稳定运行。

## 应用场景

移动内容库初始化：数据团队在启动新的移动端新闻聚合项目时，可使用 MAAS 快速导入一批种子文章链接，作为爬虫起始队列的输入源。

URL 健康度巡检：运营人员定期将 MAAS 输出的链接列表导入监控脚本，批量检查移动子域名下的文章是否仍可访问，及时剔除失效资源。

语料分类预处理：NLP 研究者在构建移动端文本语料前，通过 MAAS 对文章 ID 进行哈希分段，将大规模链接集拆分为多个子集，分发给不同的解析节点并行处理。

文档归档索引：内容管理人员使用 MAAS 生成每批次资源的 Markdown 清单，作为版本发布说明的附件或附录，便于审计与回溯。

## 快速开始

以下命令演示了如何从 GitHub 克隆 MAAS 仓库、安装依赖并执行一个基础的资源归集任务。

```bash
# 克隆仓库
git clone https://github.com/maas-dev/mobile-aggregator.git
cd mobile-aggregator

# 创建并激活 Python 虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate

# 安装核心依赖
pip install -r requirements.txt

# 运行资源归集示例（使用项目内置的示例 URL 清单）
python maas.py --input samples/urls_80.txt --output report_80.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 解释器环境，不支持 3.8 以下版本 |
| pip | 21.0+ | Python 包管理工具，用于安装依赖项 |
| requests | 2.28.2 | HTTP 请求库，用于发送探测请求 |
| re (内置) | 标准库 | 正则表达式模块，用于 URL 解析与过滤 |
| argparse (内置) | 标准库 | 命令行参数解析，用于脚本入口控制 |
| logging (内置) | 标准库 | 日志记录模块，用于输出运行状态信息 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | docs/user-guide.md | 如何使用 MAAS 进行基本的 URL 导入与导出？ |
| 配置参考 | docs/config-reference.md | 如何自定义 HTTP 超时时间、重试次数和 User-Agent？ |
| 过滤器语法 | docs/filter-syntax.md | 如何编写正则表达式以匹配特定范围的 Article ID？ |
| 贡献者指南 | CONTRIBUTING.md | 如何向 MAAS 提交新功能或修复 Bug？ |

## 资源列表

- http://m.mobile.jnjpgf.cn/Article/6020764.shtml
- http://m.mobile.nwbbyt.cn/Article/05504.shtml
- http://m.mobile.jnjpgf.cn/Article/43204.shtml
- http://m.mobile.nwbbyt.cn/Article/602468.shtml
- http://m.mobile.nwbbyt.cn/Article/1718.shtml
- http://m.mobile.cmcvrr.cn/Article/292851.shtml
- http://m.mobile.puhvjy.cn/Article/8545.shtml
- http://m.mobile.jnjpgf.cn/Article/3343.shtml
- http://m.mobile.jnjpgf.cn/Article/02586.shtml
- http://m.mobile.jnjpgf.cn/Article/024682.shtml
- http://m.mobile.cmcvrr.cn/Article/5803.shtml
- http://m.mobile.nwbbyt.cn/Article/14895.shtml
- http://m.mobile.nwbbyt.cn/Article/0198922.shtml
- http://m.mobile.puhvjy.cn/Article/69075.shtml
- http://m.mobile.jnjpgf.cn/Article/9116.shtml
- http://m.mobile.puhvjy.cn/Article/6296083.shtml
- http://m.mobile.nwbbyt.cn/Article/3037961.shtml
- http://m.mobile.puhvjy.cn/Article/72254.shtml
- http://m.mobile.cmcvrr.cn/Article/101784.shtml
- http://m.mobile.puhvjy.cn/Article/3729783.shtml
- http://m.mobile.jnjpgf.cn/Article/4218498.shtml
- http://m.mobile.nwbbyt.cn/Article/78036.shtml
- http://m.mobile.nwbbyt.cn/Article/236378.shtml
- http://m.mobile.nwbbyt.cn/Article/838570.shtml
- http://m.mobile.cmcvrr.cn/Article/22310.shtml
- http://m.mobile.nwbbyt.cn/Article/51041.shtml
- http://m.mobile.nwbbyt.cn/Article/90852.shtml
- http://m.mobile.puhvjy.cn/Article/1282.shtml
- http://m.mobile.nwbbyt.cn/Article/2111.shtml
- http://m.mobile.jnjpgf.cn/Article/56005.shtml
- http://m.mobile.nwbbyt.cn/Article/7461.shtml
- http://m.mobile.cmcvrr.cn/Article/3228286.shtml
- http://m.mobile.jnjpgf.cn/Article/73056.shtml
- http://m.mobile.cmcvrr.cn/Article/5135262.shtml
- http://m.mobile.puhvjy.cn/Article/6145610.shtml
- http://m.mobile.nwbbyt.cn/Article/8646200.shtml
- http://m.mobile.jnjpgf.cn/Article/5905264.shtml
- http://m.mobile.jnjpgf.cn/Article/643940.shtml
- http://m.mobile.nwbbyt.cn/Article/06562.shtml
- http://m.mobile.nwbbyt.cn/Article/52175.shtml
- http://m.mobile.jnjpgf.cn/Article/267151.shtml
- http://m.mobile.puhvjy.cn/Article/71310.shtml
- http://m.mobile.cmcvrr.cn/Article/3481716.shtml
- http://m.mobile.puhvjy.cn/Article/8327243.shtml
- http://m.mobile.cmcvrr.cn/Article/5563506.shtml
- http://m.mobile.nwbbyt.cn/Article/0529913.shtml
- http://m.mobile.cmcvrr.cn/Article/478244.shtml
- http://m.mobile.jnjpgf.cn/Article/9533.shtml
- http://m.mobile.puhvjy.cn/Article/986900.shtml
- http://m.mobile.cmcvrr.cn/Article/5979784.shtml
- http://m.mobile.cmcvrr.cn/Article/01419.shtml
- http://m.mobile.cmcvrr.cn/Article/6897850.shtml
- http://m.mobile.puhvjy.cn/Article/21055.shtml
- http://m.mobile.puhvjy.cn/Article/727567.shtml
- http://m.mobile.cmcvrr.cn/Article/6474.shtml
- http://m.mobile.nwbbyt.cn/Article/4398959.shtml
- http://m.mobile.nwbbyt.cn/Article/01898.shtml
- http://m.mobile.puhvjy.cn/Article/64707.shtml
- http://m.mobile.puhvjy.cn/Article/3894633.shtml
- http://m.mobile.nwbbyt.cn/Article/87492.shtml
- http://m.mobile.nwbbyt.cn/Article/02984.shtml
- http://m.mobile.jnjpgf.cn/Article/949090.shtml
- http://m.mobile.nwbbyt.cn/Article/37259.shtml
- http://m.mobile.cmcvrr.cn/Article/2078.shtml
- http://m.mobile.jnjpgf.cn/Article/3852880.shtml
- http://m.mobile.jnjpgf.cn/Article/272447.shtml
- http://m.mobile.puhvjy.cn/Article/392315.shtml
- http://m.mobile.cmcvrr.cn/Article/07163.shtml
- http://m.mobile.puhvjy.cn/Article/1087770.shtml
- http://m.mobile.puhvjy.cn/Article/8306248.shtml
- http://m.mobile.nwbbyt.cn/Article/8242.shtml
- http://m.mobile.cmcvrr.cn/Article/9490645.shtml
- http://m.mobile.cmcvrr.cn/Article/20085.shtml
- http://m.mobile.nwbbyt.cn/Article/2362.shtml
- http://m.mobile.puhvjy.cn/Article/76962.shtml
- http://m.mobile.jnjpgf.cn/Article/6515.shtml
- http://m.mobile.jnjpgf.cn/Article/2598.shtml
- http://m.mobile.jnjpgf.cn/Article/92661.shtml
- http://m.mobile.cmcvrr.cn/Article/4102.shtml
- http://m.mobile.puhvjy.cn/Article/3950.shtml
- http://m.mobile.jnjpgf.cn/Article/9915677.shtml
- http://m.mobile.nwbbyt.cn/Article/0051.shtml
- http://m.mobile.cmcvrr.cn/Article/31694.shtml
- http://m.mobile.cmcvrr.cn/Article/8364.shtml
- http://m.mobile.jnjpgf.cn/Article/560036.shtml
- http://m.mobile.jnjpgf.cn/Article/5712.shtml
- http://m.mobile.cmcvrr.cn/Article/399462.shtml
- http://m.mobile.cmcvrr.cn/Article/14033.shtml
- http://m.mobile.jnjpgf.cn/Article/8953.shtml
- http://m.mobile.jnjpgf.cn/Article/7252914.shtml
- http://m.mobile.cmcvrr.cn/Article/8651435.shtml
- http://m.mobile.puhvjy.cn/Article/3497730.shtml
- http://m.mobile.nwbbyt.cn/Article/2499062.shtml
- http://m.mobile.puhvjy.cn/Article/3257350.shtml
- http://m.mobile.nwbbyt.cn/Article/8938.shtml
- http://m.mobile.puhvjy.cn/Article/53017.shtml
- http://m.mobile.nwbbyt.cn/Article/5895.shtml
- http://m.mobile.nwbbyt.cn/Article/71498.shtml
- http://m.mobile.cmcvrr.cn/Article/943603.shtml
- http://m.mobile.cmcvrr.cn/Article/7425.shtml
- http://m.mobile.cmcvrr.cn/Article/0962636.shtml
- http://m.mobile.cmcvrr.cn/Article/6909.shtml
- http://m.mobile.cmcvrr.cn/Article/759488.shtml
- http://m.mobile.jnjpgf.cn/Article/880343.shtml
- http://m.mobile.nwbbyt.cn/Article/3538170.shtml
- http://m.mobile.puhvjy.cn/Article/05972.shtml
- http://m.mobile.puhvjy.cn/Article/7265918.shtml
- http://m.mobile.puhvjy.cn/Article/7829.shtml
- http://m.mobile.jnjpgf.cn/Article/34654.shtml
- http://m.mobile.cmcvrr.cn/Article/20632.shtml
- http://m.mobile.nwbbyt.cn/Article/5277.shtml
- http://m.mobile.jnjpgf.cn/Article/310759.shtml
- http://m.mobile.jnjpgf.cn/Article/1567892.shtml
- http://m.mobile.jnjpgf.cn/Article/95582.shtml
- http://m.mobile.cmcvrr.cn/Article/964298.shtml
- http://m.mobile.puhvjy.cn/Article/5011526.shtml
- http://m.mobile.cmcvrr.cn/Article/0045437.shtml
- http://m.mobile.cmcvrr.cn/Article/5063501.shtml
- http://m.mobile.puhvjy.cn/Article/741467.shtml
- http://m.mobile.puhvjy.cn/Article/1652.shtml
- http://m.mobile.jnjpgf.cn/Article/6340951.shtml
- http://m.mobile.jnjpgf.cn/Article/74322.shtml
- http://m.mobile.puhvjy.cn/Article/4974.shtml
- http://m.mobile.jnjpgf.cn/Article/76947.shtml
- http://m.mobile.nwbbyt.cn/Article/32931.shtml
- http://m.mobile.cmcvrr.cn/Article/16218.shtml
- http://m.mobile.cmcvrr.cn/Article/6141.shtml
- http://m.mobile.jnjpgf.cn/Article/87969.shtml
- http://m.mobile.jnjpgf.cn/Article/123906.shtml
- http://m.mobile.nwbbyt.cn/Article/722631.shtml
- http://m.mobile.cmcvrr.cn/Article/7967.shtml
- http://m.mobile.puhvjy.cn/Article/7101017.shtml
- http://m.mobile.puhvjy.cn/Article/8145.shtml
- http://m.mobile.nwbbyt.cn/Article/1189797.shtml
- http://m.mobile.nwbbyt.cn/Article/8656003.shtml
- http://m.mobile.jnjpgf.cn/Article/165114.shtml
- http://m.mobile.cmcvrr.cn/Article/60180.shtml
- http://m.mobile.nwbbyt.cn/Article/2803.shtml
- http://m.mobile.puhvjy.cn/Article/2148.shtml
- http://m.mobile.puhvjy.cn/Article/667884.shtml
- http://m.mobile.puhvjy.cn/Article/1621.shtml
- http://m.mobile.cmcvrr.cn/Article/361095.shtml
- http://m.mobile.cmcvrr.cn/Article/46228.shtml
- http://m.mobile.puhvjy.cn/Article/8356149.shtml
- http://m.mobile.puhvjy.cn/Article/4468.shtml
- http://m.mobile.jnjpgf.cn/Article/1639.shtml
- http://m.mobile.nwbbyt.cn/Article/7552.shtml
- http://m.mobile.puhvjy.cn/Article/0683350.shtml
- http://m.mobile.nwbbyt.cn/Article/61374.shtml
- http://m.mobile.cmcvrr.cn/Article/0458.shtml
- http://m.mobile.puhvjy.cn/Article/605133.shtml
- http://m.mobile.jnjpgf.cn/Article/1663.shtml
- http://m.mobile.cmcvrr.cn/Article/0840939.shtml
- http://m.mobile.cmcvrr.cn/Article/7694.shtml
- http://m.mobile.nwbbyt.cn/Article/4885.shtml
- http://m.mobile.puhvjy.cn/Article/111918.shtml
- http://m.mobile.jnjpgf.cn/Article/6589864.shtml
- http://m.mobile.puhvjy.cn/Article/350871.shtml
- http://m.mobile.jnjpgf.cn/Article/4071846.shtml
- http://m.mobile.nwbbyt.cn/Article/413513.shtml
- http://m.mobile.puhvjy.cn/Article/48839.shtml
- http://m.mobile.cmcvrr.cn/Article/9010109.shtml
- http://m.mobile.nwbbyt.cn/Article/622698.shtml
- http://m.mobile.cmcvrr.cn/Article/9999.shtml
- http://m.mobile.cmcvrr.cn/Article/3402.shtml
- http://m.mobile.jnjpgf.cn/Article/0365986.shtml
- http://m.mobile.jnjpgf.cn/Article/599715.shtml
- http://m.mobile.puhvjy.cn/Article/917738.shtml
- http://m.mobile.puhvjy.cn/Article/18993.shtml
- http://m.mobile.jnjpgf.cn/Article/642874.shtml
- http://m.mobile.nwbbyt.cn/Article/590684.shtml
- http://m.mobile.cmcvrr.cn/Article/5040.shtml
- http://m.mobile.cmcvrr.cn/Article/31260.shtml
- http://m.mobile.jnjpgf.cn/Article/1921.shtml
- http://m.mobile.nwbbyt.cn/Article/4903752.shtml
- http://m.mobile.puhvjy.cn/Article/49148.shtml
- http://m.mobile.cmcvrr.cn/Article/85223.shtml
- http://m.mobile.jnjpgf.cn/Article/211621.shtml
- http://m.mobile.cmcvrr.cn/Article/0018.shtml
- http://m.mobile.puhvjy.cn/Article/07071.shtml
- http://m.mobile.nwbbyt.cn/Article/8178507.shtml
- http://m.mobile.cmcvrr.cn/Article/810026.shtml
- http://m.mobile.cmcvrr.cn/Article/5418526.shtml
- http://m.mobile.jnjpgf.cn/Article/93015.shtml
- http://m.mobile.jnjpgf.cn/Article/644803.shtml
- http://m.mobile.jnjpgf.cn/Article/63373.shtml
- http://m.mobile.jnjpgf.cn/Article/8264141.shtml
- http://m.mobile.cmcvrr.cn/Article/1996.shtml
- http://m.mobile.nwbbyt.cn/Article/552590.shtml
- http://m.mobile.puhvjy.cn/Article/3100498.shtml
- http://m.mobile.nwbbyt.cn/Article/6027.shtml
- http://m.mobile.cmcvrr.cn/Article/2201.shtml
- http://m.mobile.nwbbyt.cn/Article/050252.shtml
- http://m.mobile.jnjpgf.cn/Article/6063.shtml
- http://m.mobile.cmcvrr.cn/Article/6946314.shtml
- http://m.mobile.nwbbyt.cn/Article/0216.shtml
- http://m.mobile.jnjpgf.cn/Article/5939.shtml
- http://m.mobile.puhvjy.cn/Article/6737367.shtml
- http://m.mobile.cmcvrr.cn/Article/12495.shtml
- http://m.mobile.cmcvrr.cn/Article/4105434.shtml
- http://m.mobile.jnjpgf.cn/Article/10328.shtml
- http://m.mobile.jnjpgf.cn/Article/7847571.shtml
- http://m.mobile.nwbbyt.cn/Article/1526390.shtml
- http://m.mobile.puhvjy.cn/Article/521655.shtml
- http://m.mobile.puhvjy.cn/Article/749225.shtml
- http://m.mobile.jnjpgf.cn/Article/0554.shtml
- http://m.mobile.cmcvrr.cn/Article/7040.shtml
- http://m.mobile.puhvjy.cn/Article/0551536.shtml
- http://m.mobile.cmcvrr.cn/Article/3044308.shtml
- http://m.mobile.puhvjy.cn/Article/9639.shtml
- http://m.mobile.puhvjy.cn/Article/7498191.shtml
- http://m.mobile.puhvjy.cn/Article/9605.shtml
- http://m.mobile.puhvjy.cn/Article/585224.shtml
- http://m.mobile.jnjpgf.cn/Article/49529.shtml
- http://m.mobile.puhvjy.cn/Article/82469.shtml
- http://m.mobile.cmcvrr.cn/Article/7443.shtml
- http://m.mobile.jnjpgf.cn/Article/25323.shtml
- http://m.mobile.jnjpgf.cn/Article/2752.shtml
- http://m.mobile.jnjpgf.cn/Article/310756.shtml
- http://m.mobile.jnjpgf.cn/Article/641654.shtml
- http://m.mobile.jnjpgf.cn/Article/7539.shtml
- http://m.mobile.puhvjy.cn/Article/01626.shtml
- http://m.mobile.nwbbyt.cn/Article/6305746.shtml
- http://m.mobile.puhvjy.cn/Article/44196.shtml
- http://m.mobile.cmcvrr.cn/Article/3028.shtml
- http://m.mobile.cmcvrr.cn/Article/3651669.shtml
- http://m.mobile.jnjpgf.cn/Article/49898.shtml
- http://m.mobile.cmcvrr.cn/Article/3160.shtml
- http://m.mobile.cmcvrr.cn/Article/9466658.shtml
- http://m.mobile.jnjpgf.cn/Article/4205944.shtml
- http://m.mobile.jnjpgf.cn/Article/8228599.shtml
- http://m.mobile.nwbbyt.cn/Article/7773970.shtml
- http://m.mobile.puhvjy.cn/Article/5631774.shtml
- http://m.mobile.nwbbyt.cn/Article/4655644.shtml
- http://m.mobile.cmcvrr.cn/Article/31932.shtml
- http://m.mobile.cmcvrr.cn/Article/77305.shtml
- http://m.mobile.jnjpgf.cn/Article/9203011.shtml
- http://m.mobile.nwbbyt.cn/Article/13742.shtml
- http://m.mobile.jnjpgf.cn/Article/2179030.shtml
- http://m.mobile.nwbbyt.cn/Article/364139.shtml
- http://m.mobile.jnjpgf.cn/Article/0664.shtml
- http://m.mobile.nwbbyt.cn/Article/256242.shtml
- http://m.mobile.jnjpgf.cn/Article/40235.shtml
- http://m.mobile.nwbbyt.cn/Article/1185.shtml
- http://m.mobile.jnjpgf.cn/Article/4709594.shtml
- http://m.mobile.puhvjy.cn/Article/3970876.shtml
- http://m.mobile.jnjpgf.cn/Article/097108.shtml
- http://m.mobile.jnjpgf.cn/Article/9145.shtml
- http://m.mobile.cmcvrr.cn/Article/622085.shtml
- http://m.mobile.jnjpgf.cn/Article/3407248.shtml

## 项目结构

```
mobile-aggregator/
├── maas.py                      # 命令行入口脚本，负责参数解析与流程编排
├── requirements.txt             # Python 依赖声明文件，包含 requests 等库
├── config/
│   ├── default.ini              # 默认配置项：超时时间、重试策略、日志级别
│   └── filter_rules.json        # 预定义的正则过滤规则集合，可按 Article ID 范围筛选
├── core/
│   ├── fetcher.py               # HTTP 请求模块，封装了带有重试机制的 GET 方法
│   ├── parser.py                # URL 解析模块，提取域名、路径和 Article ID
│   └── reporter.py              # Markdown 报告生成器，负责格式化输出资源列表
├── samples/
│   ├── urls_80.txt              # 包含 80 条示例 URL 的输入文件（第 9/80 批次）
│   └── report_80.md             # 由 maas.py 生成的示例输出报告
├── tests/
│   ├── test_fetcher.py          # 针对 fetcher 模块的单元测试
│   ├── test_parser.py           # 针对 parser 模块的单元测试
│   └── test_reporter.py         # 针对 reporter 模块的单元测试
├── docs/
│   ├── user-guide.md            # 用户指南，涵盖安装、配置与日常操作
│   ├── config-reference.md      # 配置参数完整参考手册
│   └── filter-syntax.md         # 正则过滤器语法说明与示例
├── .gitignore                   # 忽略虚拟环境、缓存文件和临时输出
└── LICENSE                      # MIT 许可证文本
```

## 贡献指南

我们欢迎开发者以多种形式参与 MAAS 项目的改进。请遵循以下步骤提交贡献。

提交 Issue 报告缺陷或提出新功能建议。在创建 Issue 前，请搜索现有议题以避免重复，并尽可能提供详细的复现步骤或使用场景说明。

Fork 主仓库并创建本地功能分支。所有新功能开发或缺陷修复均应在独立分支上进行，分支名称建议使用 `feature/` 或 `fix/` 前缀。

编写或更新单元测试。任何代码变更都必须通过新增或修改测试用例来覆盖，确保测试通过率为 100%。

提交 Pull Request 并填写变更摘要模板。在 PR 描述中引用相关的 Issue 编号，并简要说明变更的目的、实现方式以及潜在影响。

遵循 PEP 8 编码规范与项目现有的代码风格。提交前运行 `flake8` 和 `pylint` 进行静态检查，确保无严重警告。

## 常见问题

Q: MAAS 是否支持 HTTPS 协议的 URL 输入？

A: MAAS 对输入 URL 的协议不做强制限制，但内部探测模块默认使用与输入相同的协议。如果需要强制升级到 HTTPS，可以在配置文件中设置 `force_https = true`，此时所有请求将使用 HTTPS 发送，但不会修改输出列表中的 URL 文本。

Q: 如何处理大批量 URL 时的超时问题？

A: MAAS 默认的单个请求超时时间为 10 秒，并开启最多 3 次重试。若遇到大量超时，建议通过 `--timeout` 命令行参数增加超时阈值，或使用 `--concurrency` 参数降低并发数以减少网络拥塞。

Q: 输出的 Markdown 报告能否自定义排序方式？

A: 可以。MAAS 支持按域名、Article ID 数字值或随机顺序排序，具体可通过 `--sort` 参数指定 `domain`、`id` 或 `random` 三种模式之一。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
