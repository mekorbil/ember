# WebIndex Aggregate

WebIndex Aggregate 是一个面向技术调研、内容聚合与外部链接治理的轻量级资源索引系统。本项目定位于帮助开发者、技术写作者、运维人员以及数据分析师，将分散在多个内容源、多级域名下的文章链接进行集中化整理与可复现的本地归档。项目本身不依赖数据库，不强制绑定前端框架，以纯静态可解析的索引结构为核心，便于嵌入现有文档站点、自动化流程或本地知识库体系。

WebIndex Aggregate 解决的核心问题是：当外部参考链接数量庞大、来源域名不统一、内容更新频率不确定时，如何通过一个本地可维护的项目结构，对这批链接进行版本化记录、分类标注、状态跟踪与快速检索。项目特别适用于需要长期维护外链清单的技术文档库、合规性审计材料附件的整理场景，以及个人或团队的知识资产管理。

## 功能概览

- 批量链接导入与结构化存储：支持将外部原始 URL 列表按批次导入项目，自动生成带批次号与时间戳的原始记录文件，保留完整 URL 元数据。

- 多级域名来源自动归类：根据 URL 中的域名主体（如 puhvjy.cn、cmcvrr.cn、njpgf.cn、nwbbyt.cn）自动划分来源类别，并在索引中生成按域名分组的视图。

- 文章 ID 提取与唯一性校验：从每条 URL 的路径中解析 Article 后的数字编号，建立本地唯一键，用于去重、变更追踪与冲突检测。

- 状态标记与备注扩展：每条索引记录支持自定义状态字段（如待读、已读、待复核、已归档）以及文本备注，便于团队协作或个人阅读进度管理。

- Markdown 索引自动生成：根据原始数据和用户补充信息，自动生成按域名、按批次、按状态的多维度 Markdown 索引表，可直接用于文档站点渲染。

- 纯文件系统存储，无外部依赖：所有索引数据以 Markdown 和 YAML Frontmatter 格式存储于本地目录，无需数据库服务，保证可移植性与版本控制友好性。

## 应用场景

技术文档团队外链管理：技术文档团队在撰写产品白皮书或技术方案时，需要引用大量外部参考资料。使用 WebIndex Aggregate 可以统一记录所有参考链接，并为每条链接标注引用章节、审核状态和备选镜像，避免链接失效导致文档质量下降。

个人知识库外链归档：个人研究员或技术博主在阅读技术文章时，可将分散在多个移动端域名下的文章链接集中收录，通过本地索引快速定位，结合状态标记管理阅读进度，构建个人化的外链知识图谱。

合规审计附件索引生成：在安全审计或合规检查场景中，需要提供完整的外部信息来源清单。本项目可将大量原始 URL 整理为结构化索引，导出为 Markdown 表格或 CSV 格式，直接嵌入审计报告附件。

自动化链路巡检前置数据源：运维或 SRE 团队可将本项目作为链接健康检查的数据源，通过脚本读取索引中的 URL 列表，定期发起 HTTP 请求检测可用性，并将结果回写至备注字段，形成链路监控闭环。

## 快速开始

以下步骤帮助您在本地环境中快速搭建并运行 WebIndex Aggregate 的基础索引生成流程。

```bash
# 克隆项目仓库
git clone https://github.com/webindex-aggregate/webindex-core.git
cd webindex-core

# 安装基础依赖（Python 3.9+ 环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 执行示例索引生成任务（使用项目自带示例数据）
python cli.py build --batch 35 --input data/raw/batch_35.txt --output docs/index.md
```

执行上述命令后，项目将在 `docs/` 目录下生成按域名归类的索引文档，并输出统计摘要到控制台。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心 CLI 工具与索引生成脚本运行环境 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装依赖 |
| Git | 2.25 及以上 | 用于克隆仓库和版本管理 |
| Markdown 渲染器（可选） | 无强制要求 | 若需预览索引文档，建议安装 Python-Markdown 或 mkdocs |
| 操作系统 | Linux / macOS / Windows WSL2 | 项目在 POSIX 环境下测试最优，Windows 原生支持需配置 UTF-8 编码 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/guide/getting-started.md | 如何首次配置项目环境、理解目录结构以及执行第一条索引生成命令 |
| 批次管理 | docs/guide/batch-operations.md | 如何新增批次、追加链接、删除批次以及批量更新状态字段 |
| 索引定制 | docs/guide/custom-index.md | 如何调整索引输出的排序规则、分组维度、表格列以及备注模板 |
| 自动化集成 | docs/guide/automation.md | 如何将 WebIndex Aggregate 集成到 CI/CD 流水线、定时任务或监控系统中 |

## 资源列表

- http://www.mobile.puhvjy.cn/Article/68208.shtml
- http://www.mobile.cmcvrr.cn/Article/875393.shtml
- http://www.mobile.jnjpgf.cn/Article/479705.shtml
- http://www.mobile.cmcvrr.cn/Article/6295240.shtml
- http://www.mobile.puhvjy.cn/Article/23163.shtml
- http://www.mobile.nwbbyt.cn/Article/916864.shtml
- http://www.mobile.cmcvrr.cn/Article/4657.shtml
- http://www.mobile.nwbbyt.cn/Article/0079.shtml
- http://www.mobile.cmcvrr.cn/Article/71930.shtml
- http://www.mobile.jnjpgf.cn/Article/333412.shtml
- http://www.mobile.cmcvrr.cn/Article/15068.shtml
- http://www.mobile.nwbbyt.cn/Article/3769.shtml
- http://www.mobile.puhvjy.cn/Article/4177586.shtml
- http://www.mobile.jnjpgf.cn/Article/00316.shtml
- http://www.mobile.cmcvrr.cn/Article/3232431.shtml
- http://www.mobile.nwbbyt.cn/Article/730347.shtml
- http://www.mobile.jnjpgf.cn/Article/08497.shtml
- http://www.mobile.jnjpgf.cn/Article/4464.shtml
- http://www.mobile.puhvjy.cn/Article/9960.shtml
- http://www.mobile.jnjpgf.cn/Article/8519.shtml
- http://www.mobile.nwbbyt.cn/Article/1073387.shtml
- http://www.mobile.nwbbyt.cn/Article/29914.shtml
- http://www.mobile.cmcvrr.cn/Article/109504.shtml
- http://www.mobile.nwbbyt.cn/Article/9220599.shtml
- http://www.mobile.jnjpgf.cn/Article/8395.shtml
- http://www.mobile.jnjpgf.cn/Article/2904.shtml
- http://www.mobile.cmcvrr.cn/Article/4087037.shtml
- http://www.mobile.puhvjy.cn/Article/80367.shtml
- http://www.mobile.puhvjy.cn/Article/7416.shtml
- http://www.mobile.jnjpgf.cn/Article/0678.shtml
- http://www.mobile.cmcvrr.cn/Article/7074.shtml
- http://www.mobile.nwbbyt.cn/Article/0430.shtml
- http://www.mobile.nwbbyt.cn/Article/51518.shtml
- http://www.mobile.cmcvrr.cn/Article/459426.shtml
- http://www.mobile.cmcvrr.cn/Article/886245.shtml
- http://www.mobile.jnjpgf.cn/Article/8892704.shtml
- http://www.mobile.puhvjy.cn/Article/3444.shtml
- http://www.mobile.puhvjy.cn/Article/308647.shtml
- http://www.mobile.cmcvrr.cn/Article/6696.shtml
- http://www.mobile.nwbbyt.cn/Article/76760.shtml
- http://www.mobile.cmcvrr.cn/Article/5585.shtml
- http://www.mobile.cmcvrr.cn/Article/742642.shtml
- http://www.mobile.jnjpgf.cn/Article/6098.shtml
- http://www.mobile.jnjpgf.cn/Article/6591.shtml
- http://www.mobile.puhvjy.cn/Article/2336103.shtml
- http://www.mobile.puhvjy.cn/Article/060832.shtml
- http://www.mobile.jnjpgf.cn/Article/7215.shtml
- http://www.mobile.puhvjy.cn/Article/261287.shtml
- http://www.mobile.cmcvrr.cn/Article/4833743.shtml
- http://www.mobile.puhvjy.cn/Article/6358.shtml
- http://www.mobile.puhvjy.cn/Article/7893.shtml
- http://www.mobile.puhvjy.cn/Article/6480.shtml
- http://www.mobile.jnjpgf.cn/Article/46312.shtml
- http://www.mobile.cmcvrr.cn/Article/686933.shtml
- http://www.mobile.jnjpgf.cn/Article/17694.shtml
- http://www.mobile.puhvjy.cn/Article/9892.shtml
- http://www.mobile.nwbbyt.cn/Article/11819.shtml
- http://www.mobile.cmcvrr.cn/Article/7359.shtml
- http://www.mobile.nwbbyt.cn/Article/17110.shtml
- http://www.mobile.nwbbyt.cn/Article/0604.shtml
- http://www.mobile.jnjpgf.cn/Article/0809.shtml
- http://www.mobile.puhvjy.cn/Article/16400.shtml
- http://www.mobile.cmcvrr.cn/Article/4651.shtml
- http://www.mobile.jnjpgf.cn/Article/512834.shtml
- http://www.mobile.cmcvrr.cn/Article/8556.shtml
- http://www.mobile.nwbbyt.cn/Article/260123.shtml
- http://www.mobile.cmcvrr.cn/Article/1986.shtml
- http://www.mobile.jnjpgf.cn/Article/4321.shtml
- http://www.mobile.nwbbyt.cn/Article/95452.shtml
- http://www.mobile.jnjpgf.cn/Article/0369517.shtml
- http://www.mobile.nwbbyt.cn/Article/79440.shtml
- http://www.mobile.puhvjy.cn/Article/174981.shtml
- http://www.mobile.nwbbyt.cn/Article/3914707.shtml
- http://www.mobile.jnjpgf.cn/Article/0243097.shtml
- http://www.mobile.jnjpgf.cn/Article/414649.shtml
- http://www.mobile.nwbbyt.cn/Article/532023.shtml
- http://www.mobile.jnjpgf.cn/Article/160433.shtml
- http://www.mobile.jnjpgf.cn/Article/13232.shtml
- http://www.mobile.jnjpgf.cn/Article/478022.shtml
- http://www.mobile.cmcvrr.cn/Article/155476.shtml
- http://www.mobile.jnjpgf.cn/Article/7470696.shtml
- http://www.mobile.puhvjy.cn/Article/710409.shtml
- http://www.mobile.jnjpgf.cn/Article/0117269.shtml
- http://www.mobile.jnjpgf.cn/Article/007252.shtml
- http://www.mobile.cmcvrr.cn/Article/81681.shtml
- http://www.mobile.cmcvrr.cn/Article/201604.shtml
- http://www.mobile.nwbbyt.cn/Article/5686071.shtml
- http://www.mobile.jnjpgf.cn/Article/17822.shtml
- http://www.mobile.cmcvrr.cn/Article/572748.shtml
- http://www.mobile.cmcvrr.cn/Article/489477.shtml
- http://www.mobile.puhvjy.cn/Article/91764.shtml
- http://www.mobile.nwbbyt.cn/Article/27003.shtml
- http://www.mobile.nwbbyt.cn/Article/39882.shtml
- http://www.mobile.cmcvrr.cn/Article/026282.shtml
- http://www.mobile.cmcvrr.cn/Article/52235.shtml
- http://www.mobile.puhvjy.cn/Article/198950.shtml
- http://www.mobile.puhvjy.cn/Article/00613.shtml
- http://www.mobile.cmcvrr.cn/Article/2694.shtml
- http://www.mobile.puhvjy.cn/Article/9067035.shtml
- http://www.mobile.puhvjy.cn/Article/05914.shtml
- http://www.mobile.nwbbyt.cn/Article/92136.shtml
- http://www.mobile.puhvjy.cn/Article/898442.shtml
- http://www.mobile.jnjpgf.cn/Article/4869.shtml
- http://www.mobile.cmcvrr.cn/Article/461462.shtml
- http://www.mobile.cmcvrr.cn/Article/743074.shtml
- http://www.mobile.jnjpgf.cn/Article/4260444.shtml
- http://www.mobile.jnjpgf.cn/Article/1796119.shtml
- http://www.mobile.cmcvrr.cn/Article/9794630.shtml
- http://www.mobile.nwbbyt.cn/Article/801117.shtml
- http://www.mobile.jnjpgf.cn/Article/7924.shtml
- http://www.mobile.jnjpgf.cn/Article/4722.shtml
- http://www.mobile.jnjpgf.cn/Article/624626.shtml
- http://www.mobile.puhvjy.cn/Article/121456.shtml
- http://www.mobile.puhvjy.cn/Article/9720.shtml
- http://www.mobile.cmcvrr.cn/Article/494836.shtml
- http://www.mobile.nwbbyt.cn/Article/30297.shtml
- http://www.mobile.puhvjy.cn/Article/1838150.shtml
- http://www.mobile.jnjpgf.cn/Article/9607891.shtml
- http://www.mobile.cmcvrr.cn/Article/9652.shtml
- http://www.mobile.cmcvrr.cn/Article/392710.shtml
- http://www.mobile.nwbbyt.cn/Article/2764.shtml
- http://www.mobile.nwbbyt.cn/Article/83079.shtml
- http://www.mobile.nwbbyt.cn/Article/3556997.shtml
- http://www.mobile.cmcvrr.cn/Article/11170.shtml
- http://www.mobile.cmcvrr.cn/Article/10343.shtml
- http://www.mobile.cmcvrr.cn/Article/8688335.shtml
- http://www.mobile.nwbbyt.cn/Article/8242851.shtml
- http://www.mobile.cmcvrr.cn/Article/164077.shtml
- http://www.mobile.puhvjy.cn/Article/886650.shtml
- http://www.mobile.puhvjy.cn/Article/7269.shtml
- http://www.mobile.puhvjy.cn/Article/7962202.shtml
- http://www.mobile.puhvjy.cn/Article/4512.shtml
- http://www.mobile.jnjpgf.cn/Article/3456.shtml
- http://www.mobile.puhvjy.cn/Article/4149457.shtml
- http://www.mobile.jnjpgf.cn/Article/6312677.shtml
- http://www.mobile.cmcvrr.cn/Article/1771720.shtml
- http://www.mobile.puhvjy.cn/Article/88969.shtml
- http://www.mobile.cmcvrr.cn/Article/1810048.shtml
- http://www.mobile.cmcvrr.cn/Article/172930.shtml
- http://www.mobile.jnjpgf.cn/Article/5661730.shtml
- http://www.mobile.jnjpgf.cn/Article/4188282.shtml
- http://www.mobile.nwbbyt.cn/Article/5728.shtml
- http://www.mobile.jnjpgf.cn/Article/923656.shtml
- http://www.mobile.cmcvrr.cn/Article/7869.shtml
- http://www.mobile.puhvjy.cn/Article/3307.shtml
- http://www.mobile.puhvjy.cn/Article/0840536.shtml
- http://www.mobile.jnjpgf.cn/Article/9575137.shtml
- http://www.mobile.puhvjy.cn/Article/16966.shtml
- http://www.mobile.jnjpgf.cn/Article/9602893.shtml
- http://www.mobile.puhvjy.cn/Article/25823.shtml
- http://www.mobile.cmcvrr.cn/Article/03340.shtml
- http://www.mobile.cmcvrr.cn/Article/2443.shtml
- http://www.mobile.puhvjy.cn/Article/54235.shtml
- http://www.mobile.cmcvrr.cn/Article/7403.shtml
- http://www.mobile.cmcvrr.cn/Article/63873.shtml
- http://www.mobile.puhvjy.cn/Article/701894.shtml
- http://www.mobile.nwbbyt.cn/Article/2712272.shtml
- http://www.mobile.nwbbyt.cn/Article/343571.shtml
- http://www.mobile.puhvjy.cn/Article/9995.shtml
- http://www.mobile.jnjpgf.cn/Article/570540.shtml
- http://www.mobile.nwbbyt.cn/Article/9232.shtml
- http://www.mobile.cmcvrr.cn/Article/6874.shtml
- http://www.mobile.jnjpgf.cn/Article/64432.shtml
- http://www.mobile.puhvjy.cn/Article/28117.shtml
- http://www.mobile.cmcvrr.cn/Article/05922.shtml
- http://www.mobile.cmcvrr.cn/Article/1602292.shtml
- http://www.mobile.nwbbyt.cn/Article/363475.shtml
- http://www.mobile.puhvjy.cn/Article/8118908.shtml
- http://www.mobile.nwbbyt.cn/Article/992289.shtml
- http://www.mobile.cmcvrr.cn/Article/075979.shtml
- http://www.mobile.jnjpgf.cn/Article/1660707.shtml
- http://www.mobile.cmcvrr.cn/Article/3046.shtml
- http://www.mobile.nwbbyt.cn/Article/596912.shtml
- http://www.mobile.nwbbyt.cn/Article/93241.shtml
- http://www.mobile.nwbbyt.cn/Article/7489.shtml
- http://www.mobile.jnjpgf.cn/Article/62793.shtml
- http://www.mobile.puhvjy.cn/Article/59773.shtml
- http://www.mobile.nwbbyt.cn/Article/7676.shtml
- http://www.mobile.nwbbyt.cn/Article/56002.shtml
- http://www.mobile.nwbbyt.cn/Article/0631840.shtml
- http://www.mobile.jnjpgf.cn/Article/5192149.shtml
- http://www.mobile.nwbbyt.cn/Article/5675610.shtml
- http://www.mobile.jnjpgf.cn/Article/079924.shtml
- http://www.mobile.jnjpgf.cn/Article/2092.shtml
- http://www.mobile.jnjpgf.cn/Article/8771438.shtml
- http://www.mobile.puhvjy.cn/Article/920248.shtml
- http://www.mobile.cmcvrr.cn/Article/4650.shtml
- http://www.mobile.puhvjy.cn/Article/87980.shtml
- http://www.mobile.jnjpgf.cn/Article/05513.shtml
- http://www.mobile.jnjpgf.cn/Article/64747.shtml
- http://www.mobile.nwbbyt.cn/Article/23938.shtml
- http://www.mobile.cmcvrr.cn/Article/9416149.shtml
- http://www.mobile.nwbbyt.cn/Article/8693.shtml
- http://www.mobile.puhvjy.cn/Article/4025056.shtml
- http://www.mobile.cmcvrr.cn/Article/6690598.shtml
- http://www.mobile.cmcvrr.cn/Article/9973887.shtml
- http://www.mobile.jnjpgf.cn/Article/6168360.shtml
- http://www.mobile.jnjpgf.cn/Article/7349.shtml
- http://www.mobile.cmcvrr.cn/Article/2035.shtml
- http://www.mobile.nwbbyt.cn/Article/22380.shtml
- http://www.mobile.puhvjy.cn/Article/67803.shtml
- http://www.mobile.cmcvrr.cn/Article/8429.shtml
- http://www.mobile.nwbbyt.cn/Article/0131663.shtml
- http://www.mobile.jnjpgf.cn/Article/302559.shtml
- http://www.mobile.cmcvrr.cn/Article/63859.shtml
- http://www.mobile.nwbbyt.cn/Article/110843.shtml
- http://www.mobile.jnjpgf.cn/Article/123512.shtml
- http://www.mobile.nwbbyt.cn/Article/31927.shtml
- http://www.mobile.puhvjy.cn/Article/79611.shtml
- http://www.mobile.puhvjy.cn/Article/4944810.shtml
- http://www.mobile.nwbbyt.cn/Article/8405954.shtml
- http://www.mobile.cmcvrr.cn/Article/0870817.shtml
- http://www.mobile.jnjpgf.cn/Article/7881714.shtml
- http://www.mobile.puhvjy.cn/Article/14467.shtml
- http://www.mobile.jnjpgf.cn/Article/953210.shtml
- http://www.mobile.cmcvrr.cn/Article/750498.shtml
- http://www.mobile.puhvjy.cn/Article/09858.shtml
- http://www.mobile.puhvjy.cn/Article/5681676.shtml
- http://www.mobile.puhvjy.cn/Article/366495.shtml
- http://www.mobile.jnjpgf.cn/Article/2291861.shtml
- http://www.mobile.nwbbyt.cn/Article/017776.shtml
- http://www.mobile.nwbbyt.cn/Article/0611.shtml
- http://www.mobile.cmcvrr.cn/Article/9372.shtml
- http://www.mobile.cmcvrr.cn/Article/3792.shtml
- http://www.mobile.nwbbyt.cn/Article/324584.shtml
- http://www.mobile.nwbbyt.cn/Article/459786.shtml
- http://www.mobile.nwbbyt.cn/Article/6084677.shtml
- http://www.mobile.jnjpgf.cn/Article/9291725.shtml
- http://www.mobile.nwbbyt.cn/Article/8203.shtml
- http://www.mobile.cmcvrr.cn/Article/53633.shtml
- http://www.mobile.cmcvrr.cn/Article/404194.shtml
- http://www.mobile.puhvjy.cn/Article/50874.shtml
- http://www.mobile.nwbbyt.cn/Article/599024.shtml
- http://www.mobile.jnjpgf.cn/Article/9678.shtml
- http://www.mobile.nwbbyt.cn/Article/533850.shtml
- http://www.mobile.cmcvrr.cn/Article/301790.shtml
- http://www.mobile.nwbbyt.cn/Article/80931.shtml
- http://www.mobile.jnjpgf.cn/Article/83415.shtml
- http://www.mobile.jnjpgf.cn/Article/311376.shtml
- http://www.mobile.puhvjy.cn/Article/3728147.shtml
- http://www.mobile.puhvjy.cn/Article/6197.shtml
- http://www.mobile.cmcvrr.cn/Article/0086.shtml
- http://www.mobile.puhvjy.cn/Article/8264440.shtml
- http://www.mobile.jnjpgf.cn/Article/74570.shtml
- http://www.mobile.jnjpgf.cn/Article/6381130.shtml
- http://www.mobile.jnjpgf.cn/Article/9645.shtml
- http://www.mobile.cmcvrr.cn/Article/2361325.shtml
- http://www.mobile.nwbbyt.cn/Article/7160.shtml
- http://www.mobile.cmcvrr.cn/Article/3451.shtml
- http://www.mobile.cmcvrr.cn/Article/90197.shtml

## 项目结构

```
webindex-core/
├── cli.py                      # 主命令行入口，解析参数并调度构建流程
├── requirements.txt            # Python 依赖声明（click, pyyaml, markdown）
├── config.yaml                 # 项目配置文件（域名别名、状态枚举、输出模板）
├── data/
│   ├── raw/                    # 原始批次数据存储目录
│   │   └── batch_35.txt        # 第 35 批原始 URL 列表（纯文本，每行一个 URL）
│   ├── parsed/                 # 解析后的结构化数据（YAML 格式）
│   │   └── batch_35_meta.yaml  # 包含域名分组、ID 列表、导入时间戳
│   └── cache/                  # 临时缓存文件（用于增量构建和去重校验）
│       └── url_hash.db         # SQLite 轻量级哈希索引
├── src/
│   ├── parser/                 # URL 解析与校验模块
│   │   ├── extractor.py        # 域名提取、Article ID 正则匹配
│   │   └── validator.py        # URL 格式校验与去重逻辑
│   ├── generator/              # 索引文档生成模块
│   │   ├── table_builder.py    # Markdown 表格构建器（按域名、状态分组）
│   │   └── frontmatter.py      # YAML Frontmatter 生成与合并
│   ├── state/                  # 状态管理模块
│   │   ├── tracker.py          # 读取/写入状态字段（待读、已读、待复核等）
│   │   └── history.py          # 状态变更日志记录
│   └── utils/                  # 通用工具函数
│       ├── file_ops.py         # 文件读写、目录创建、编码检测
│       └── logger.py           # 统一日志输出（支持 verbose 模式）
├── docs/                       # 生成的索引文档输出目录
│   ├── index.md                # 主索引（按域名分组总览）
│   ├── by_batch/               # 按批次索引子目录
│   │   └── batch_35.md         # 第 35 批详细索引表
│   └── by_status/              # 按状态索引子目录
│       └── pending.md          # 所有状态为“待读”的链接视图
├── tests/                      # 单元测试与集成测试目录
│   ├── test_parser.py          # 解析器单元测试
│   ├── test_generator.py       # 生成器单元测试
│   └── fixtures/               # 测试用固定样本数据
│       └── sample_urls.txt     # 模拟 URL 列表
└── .gitignore                  # Git 忽略规则（排除 cache/ 和 docs/ 下的临时文件）
```

## 贡献指南

1. 复刻项目仓库并在本地完成开发环境搭建，确保 Python 3.9 及以上版本可用，运行 `python -m pip install -r requirements.txt` 安装所有开发依赖。

2. 在 `data/raw/` 目录下新增批次文件，遵循项目规定的纯文本格式（每行一个完整 URL），并运行 `python cli.py validate --batch <编号>` 进行格式校验。

3. 若需扩展索引输出格式，请在 `src/generator/` 下新增对应的生成器类，并继承基础 `BaseGenerator`，在 `config.yaml` 中注册新输出类型。

4. 提交代码前请执行 `python -m pytest tests/` 确保所有单元测试通过，并更新 `docs/guide/` 下对应的文档说明以反映您的变更。

5. 发起 Pull Request 至主仓库的 `develop` 分支，在 PR 描述中附上变更摘要、测试结果以及是否影响现有索引结构的说明。

## 常见问题

问：批量导入 URL 后，如何手动修改某一条链接的状态或备注？

答：项目在 `data/parsed/` 目录下为每个批次生成对应的 YAML 元数据文件。您可以直接编辑该文件，在对应 Article ID 条目下修改 `status` 或 `remark` 字段，然后重新运行 `python cli.py build --batch <编号>` 即可生成更新后的索引。建议在编辑前备份原始文件。

问：索引文档中链接较多时，构建速度明显变慢，如何优化？

答：对于超过 500 条链接的批次，建议启用增量构建模式。使用 `python cli.py build --batch <编号> --incremental` 命令，该模式会利用 `data/cache/url_hash.db` 中的哈希索引，仅重新处理变更或新增的链接，大幅减少重复解析和表格重建的时间。此外，您也可以按域名或日期拆分批次，避免单个批次过大。

问：项目是否支持将索引导出为 CSV 或 JSON 格式，以便导入其他系统？

答：支持。从 v1.2.0 版本开始，`cli.py` 提供了 `export` 子命令。例如 `python cli.py export --batch <编号> --format csv --output report.csv` 可将指定批次的索引数据导出为 CSV 格式，包含 URL、域名、状态、备注、导入时间等完整字段。若需 JSON 格式，将 `--format` 参数改为 `json` 即可。导出的文件默认保存在 `exports/` 目录下。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
