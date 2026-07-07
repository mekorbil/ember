# LinkMap Mobile Resource Aggregator

LinkMap Mobile Resource Aggregator 是一个面向移动端技术研究与内容聚合的开源外链管理工具，专为需要批量采集、分类整理和快速检索移动端 H5 页面、API 文档、技术博客及行业资讯的开发者与研究人员设计。该项目通过结构化 URL 索引机制，将分散的移动端技术资源统一归纳入可版本控制的知识库体系。

本项目定位于中小型技术团队、独立开发者及技术内容运营人员，帮助其从碎片化的浏览器书签和零散笔记中解脱出来，建立一套可维护、可共享、可追溯的技术外链资产库。LinkMap 不依赖任何第三方云服务，所有数据以纯文本形式存储在仓库中，支持 Git 工作流进行协作更新与变更审计。

## 功能概览

批量 URL 导入与去重校验：支持从 CSV、JSON 或纯文本列表中批量导入 URL，自动识别并剔除重复条目，保留原始域名与路径结构。

多维度标签分类系统：允许用户为每条链接添加多个自定义标签，并基于标签组合进行快速筛选，支持标签层级嵌套（如 "移动端/iOS/性能优化"）。

全文检索与正则匹配：内置基于 ripgrep 的轻量级全文检索引擎，支持对 URL、标题、摘要及自定义备注字段进行正则表达式搜索。

资源状态监控与健康检查：周期性对已收录链接发起 HEAD 请求，检测 HTTP 状态码变化，标记失效链接并生成变更报告。

Markdown 格式数据持久化：所有资源条目以 Markdown 列表形式存储于项目根目录的 /data 文件夹中，便于人工审阅和版本对比。

离线浏览模式支持：提供静态 HTML 导出功能，将资源列表和关联元数据生成为可离线访问的文档页面，适用于内网环境或文档归档。

协作审核工作流：集成 GitHub Issue 模板和 Pull Request 校验脚本，支持团队成员提交新链接、提议删除或修改已有条目，所有变更需经过 CI 检查。

## 应用场景

移动端技术文档聚合管理：技术负责人可以将分散在各大平台（如微信开放文档、Apple Developer、Android Developers、各大 CDN 厂商公告）的官方文档链接统一收录，按项目或技术领域分类，方便新成员快速查阅权威资料。

线上问题排查与日志溯源：运维或后端开发人员在处理移动端接口异常时，可将临时抓取到的日志平台链接、Nginx 状态页、CDN 刷新日志等临时性 URL 快速录入项目临时标签组，便于团队内部分享和事后复盘。

技术周报与资讯收集：内容运营或技术编辑可利用 LinkMap 的标签检索功能，按时间标签（如 "2026Q3"）和领域标签（如 "前端框架"）快速整理当周值得关注的技术文章、开源 release 公告和行业动态，生成 Markdown 格式周报草稿。

合规审计与链接生命周期管理：法务或合规部门可定期导出全部链接清单，配合状态监控功能筛查失效或内容变更为非预期页面的资源，确保对外文档中引用的所有第三方链接均为有效且合规。

## 快速开始

以下命令序列适用于 Linux/macOS 以及 Windows WSL 环境，请确保系统已安装 Git 和 Node.js（v18 及以上）。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/linkmap-mobile.git
cd linkmap-mobile

# 安装项目依赖（包括核心解析引擎和 CLI 工具）
npm install

# 执行初始化数据构建，生成索引文件并校验资源列表格式
npm run build:index

# 启动本地开发服务器，访问 http://localhost:3000 查看资源面板
npm run dev
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.0.0 或更高 | 运行时环境，用于执行构建脚本和 CLI 命令 |
| npm | 9.0.0 或更高 | 包管理器，用于安装项目依赖及运行脚本 |
| Git | 2.30.0 或更高 | 版本控制，用于克隆仓库及提交变更 |
| ripgrep | 13.0.0 或更高 | 全文检索引擎，用于快速正则搜索（可选，但推荐） |
| curl | 7.68.0 或更高 | 用于健康检查模块的 HTTP 探测（Linux/macOS 自带） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何添加新链接、如何应用标签筛选、如何导出静态报告 |
| 运维指南 | /docs/operations/ | 如何配置健康检查周期、如何迁移数据目录、如何备份索引 |
| 开发者文档 | /docs/developer/ | 插件扩展机制、API 接口定义、自定义解析器编写规范 |
| 设计说明 | /docs/design/ | 数据模型设计、索引结构、标签系统算法、性能优化策略 |

## 资源列表

- http://map.mobile.cmcvrr.cn/Article/065624.shtml
- http://map.mobile.cmcvrr.cn/Article/75131.shtml
- http://map.mobile.puhvjy.cn/Article/380605.shtml
- http://map.mobile.puhvjy.cn/Article/533240.shtml
- http://map.mobile.nwbbyt.cn/Article/696107.shtml
- http://map.mobile.puhvjy.cn/Article/6723573.shtml
- http://map.mobile.cmcvrr.cn/Article/4795455.shtml
- http://map.mobile.cmcvrr.cn/Article/4558.shtml
- http://map.mobile.nwbbyt.cn/Article/6362819.shtml
- http://map.mobile.jnjpgf.cn/Article/957695.shtml
- http://map.mobile.cmcvrr.cn/Article/7301478.shtml
- http://map.mobile.puhvjy.cn/Article/04247.shtml
- http://map.mobile.nwbbyt.cn/Article/05725.shtml
- http://map.mobile.jnjpgf.cn/Article/706509.shtml
- http://map.mobile.cmcvrr.cn/Article/6660645.shtml
- http://map.mobile.nwbbyt.cn/Article/723729.shtml
- http://map.mobile.puhvjy.cn/Article/598111.shtml
- http://map.mobile.puhvjy.cn/Article/3459.shtml
- http://map.mobile.puhvjy.cn/Article/1817.shtml
- http://map.mobile.nwbbyt.cn/Article/46217.shtml
- http://map.mobile.jnjpgf.cn/Article/18062.shtml
- http://map.mobile.jnjpgf.cn/Article/323505.shtml
- http://map.mobile.nwbbyt.cn/Article/1461.shtml
- http://map.mobile.puhvjy.cn/Article/7402.shtml
- http://map.mobile.cmcvrr.cn/Article/94915.shtml
- http://map.mobile.cmcvrr.cn/Article/4793.shtml
- http://map.mobile.nwbbyt.cn/Article/0379.shtml
- http://map.mobile.puhvjy.cn/Article/2583.shtml
- http://map.mobile.cmcvrr.cn/Article/9117.shtml
- http://map.mobile.puhvjy.cn/Article/2055.shtml
- http://map.mobile.nwbbyt.cn/Article/5631.shtml
- http://map.mobile.jnjpgf.cn/Article/5492.shtml
- http://map.mobile.puhvjy.cn/Article/3790.shtml
- http://map.mobile.puhvjy.cn/Article/251809.shtml
- http://map.mobile.nwbbyt.cn/Article/25798.shtml
- http://map.mobile.cmcvrr.cn/Article/249654.shtml
- http://map.mobile.cmcvrr.cn/Article/9939903.shtml
- http://map.mobile.puhvjy.cn/Article/24272.shtml
- http://map.mobile.jnjpgf.cn/Article/6118293.shtml
- http://map.mobile.jnjpgf.cn/Article/999034.shtml
- http://map.mobile.nwbbyt.cn/Article/4801.shtml
- http://map.mobile.nwbbyt.cn/Article/94063.shtml
- http://map.mobile.cmcvrr.cn/Article/4013.shtml
- http://map.mobile.cmcvrr.cn/Article/2467.shtml
- http://map.mobile.nwbbyt.cn/Article/56855.shtml
- http://map.mobile.nwbbyt.cn/Article/97254.shtml
- http://map.mobile.puhvjy.cn/Article/9714.shtml
- http://map.mobile.puhvjy.cn/Article/5340445.shtml
- http://map.mobile.nwbbyt.cn/Article/5395729.shtml
- http://map.mobile.nwbbyt.cn/Article/35631.shtml
- http://map.mobile.nwbbyt.cn/Article/4024196.shtml
- http://map.mobile.nwbbyt.cn/Article/2926089.shtml
- http://map.mobile.puhvjy.cn/Article/7769.shtml
- http://map.mobile.cmcvrr.cn/Article/0492.shtml
- http://map.mobile.puhvjy.cn/Article/15831.shtml
- http://map.mobile.puhvjy.cn/Article/1172745.shtml
- http://map.mobile.puhvjy.cn/Article/495549.shtml
- http://map.mobile.cmcvrr.cn/Article/57691.shtml
- http://map.mobile.cmcvrr.cn/Article/96937.shtml
- http://map.mobile.nwbbyt.cn/Article/0171.shtml
- http://map.mobile.nwbbyt.cn/Article/954008.shtml
- http://map.mobile.cmcvrr.cn/Article/792256.shtml
- http://map.mobile.cmcvrr.cn/Article/7660.shtml
- http://map.mobile.nwbbyt.cn/Article/5645.shtml
- http://map.mobile.jnjpgf.cn/Article/831212.shtml
- http://map.mobile.jnjpgf.cn/Article/653105.shtml
- http://map.mobile.nwbbyt.cn/Article/3096.shtml
- http://map.mobile.puhvjy.cn/Article/45828.shtml
- http://map.mobile.cmcvrr.cn/Article/63144.shtml
- http://map.mobile.jnjpgf.cn/Article/41218.shtml
- http://map.mobile.nwbbyt.cn/Article/9208.shtml
- http://map.mobile.nwbbyt.cn/Article/2048614.shtml
- http://map.mobile.cmcvrr.cn/Article/018323.shtml
- http://map.mobile.jnjpgf.cn/Article/8976.shtml
- http://map.mobile.puhvjy.cn/Article/679718.shtml
- http://map.mobile.cmcvrr.cn/Article/2347.shtml
- http://map.mobile.nwbbyt.cn/Article/558032.shtml
- http://map.mobile.nwbbyt.cn/Article/629676.shtml
- http://map.mobile.puhvjy.cn/Article/51827.shtml
- http://map.mobile.nwbbyt.cn/Article/2135233.shtml
- http://map.mobile.jnjpgf.cn/Article/316340.shtml
- http://map.mobile.jnjpgf.cn/Article/874311.shtml
- http://map.mobile.nwbbyt.cn/Article/6302893.shtml
- http://map.mobile.puhvjy.cn/Article/9324.shtml
- http://map.mobile.nwbbyt.cn/Article/692689.shtml
- http://map.mobile.jnjpgf.cn/Article/2697553.shtml
- http://map.mobile.jnjpgf.cn/Article/1595870.shtml
- http://map.mobile.nwbbyt.cn/Article/8279.shtml
- http://map.mobile.jnjpgf.cn/Article/1782456.shtml
- http://map.mobile.puhvjy.cn/Article/735069.shtml
- http://map.mobile.jnjpgf.cn/Article/6135.shtml
- http://map.mobile.nwbbyt.cn/Article/5170.shtml
- http://map.mobile.nwbbyt.cn/Article/42024.shtml
- http://map.mobile.nwbbyt.cn/Article/226771.shtml
- http://map.mobile.cmcvrr.cn/Article/9249.shtml
- http://map.mobile.cmcvrr.cn/Article/2562.shtml
- http://map.mobile.cmcvrr.cn/Article/3976.shtml
- http://map.mobile.cmcvrr.cn/Article/344391.shtml
- http://map.mobile.nwbbyt.cn/Article/3941952.shtml
- http://map.mobile.puhvjy.cn/Article/7324601.shtml
- http://map.mobile.nwbbyt.cn/Article/52240.shtml
- http://map.mobile.cmcvrr.cn/Article/2638.shtml
- http://map.mobile.puhvjy.cn/Article/9418.shtml
- http://map.mobile.nwbbyt.cn/Article/613167.shtml
- http://map.mobile.nwbbyt.cn/Article/1390838.shtml
- http://map.mobile.nwbbyt.cn/Article/761993.shtml
- http://map.mobile.puhvjy.cn/Article/3140589.shtml
- http://map.mobile.nwbbyt.cn/Article/8477426.shtml
- http://map.mobile.cmcvrr.cn/Article/08605.shtml
- http://map.mobile.cmcvrr.cn/Article/3486296.shtml
- http://map.mobile.puhvjy.cn/Article/55101.shtml
- http://map.mobile.puhvjy.cn/Article/4733212.shtml
- http://map.mobile.jnjpgf.cn/Article/644417.shtml
- http://map.mobile.nwbbyt.cn/Article/642709.shtml
- http://map.mobile.cmcvrr.cn/Article/2300241.shtml
- http://map.mobile.jnjpgf.cn/Article/78870.shtml
- http://map.mobile.jnjpgf.cn/Article/4861.shtml
- http://map.mobile.puhvjy.cn/Article/485771.shtml
- http://map.mobile.jnjpgf.cn/Article/9851481.shtml
- http://map.mobile.jnjpgf.cn/Article/6185907.shtml
- http://map.mobile.jnjpgf.cn/Article/0619.shtml
- http://map.mobile.cmcvrr.cn/Article/70406.shtml
- http://map.mobile.puhvjy.cn/Article/4482.shtml
- http://map.mobile.nwbbyt.cn/Article/009590.shtml
- http://map.mobile.nwbbyt.cn/Article/422768.shtml
- http://map.mobile.puhvjy.cn/Article/110818.shtml
- http://map.mobile.cmcvrr.cn/Article/45700.shtml
- http://map.mobile.jnjpgf.cn/Article/12881.shtml
- http://map.mobile.jnjpgf.cn/Article/235693.shtml
- http://map.mobile.nwbbyt.cn/Article/91964.shtml
- http://map.mobile.nwbbyt.cn/Article/1598037.shtml
- http://map.mobile.jnjpgf.cn/Article/591003.shtml
- http://map.mobile.jnjpgf.cn/Article/1729188.shtml
- http://map.mobile.puhvjy.cn/Article/6035.shtml
- http://map.mobile.jnjpgf.cn/Article/36460.shtml
- http://map.mobile.jnjpgf.cn/Article/0462.shtml
- http://map.mobile.puhvjy.cn/Article/41589.shtml
- http://map.mobile.puhvjy.cn/Article/4988544.shtml
- http://map.mobile.puhvjy.cn/Article/2907578.shtml
- http://map.mobile.cmcvrr.cn/Article/5893568.shtml
- http://map.mobile.jnjpgf.cn/Article/0187.shtml
- http://map.mobile.nwbbyt.cn/Article/85887.shtml
- http://map.mobile.puhvjy.cn/Article/1118.shtml
- http://map.mobile.cmcvrr.cn/Article/48896.shtml
- http://map.mobile.jnjpgf.cn/Article/0743.shtml
- http://map.mobile.cmcvrr.cn/Article/4401812.shtml
- http://map.mobile.jnjpgf.cn/Article/239643.shtml
- http://map.mobile.puhvjy.cn/Article/152775.shtml
- http://map.mobile.puhvjy.cn/Article/9577627.shtml
- http://map.mobile.jnjpgf.cn/Article/2607.shtml
- http://map.mobile.jnjpgf.cn/Article/40020.shtml
- http://map.mobile.nwbbyt.cn/Article/845916.shtml
- http://map.mobile.cmcvrr.cn/Article/0106868.shtml
- http://map.mobile.jnjpgf.cn/Article/3805563.shtml
- http://map.mobile.cmcvrr.cn/Article/20702.shtml
- http://map.mobile.jnjpgf.cn/Article/1221.shtml
- http://map.mobile.cmcvrr.cn/Article/23496.shtml
- http://map.mobile.puhvjy.cn/Article/7196564.shtml
- http://map.mobile.puhvjy.cn/Article/6665.shtml
- http://map.mobile.puhvjy.cn/Article/2070.shtml
- http://map.mobile.cmcvrr.cn/Article/5672.shtml
- http://map.mobile.jnjpgf.cn/Article/53244.shtml
- http://map.mobile.puhvjy.cn/Article/5357.shtml
- http://map.mobile.cmcvrr.cn/Article/3396025.shtml
- http://map.mobile.nwbbyt.cn/Article/5064.shtml
- http://map.mobile.jnjpgf.cn/Article/08150.shtml
- http://map.mobile.nwbbyt.cn/Article/488722.shtml
- http://map.mobile.nwbbyt.cn/Article/77341.shtml
- http://map.mobile.jnjpgf.cn/Article/2299069.shtml
- http://map.mobile.puhvjy.cn/Article/1322.shtml
- http://map.mobile.puhvjy.cn/Article/346411.shtml
- http://map.mobile.cmcvrr.cn/Article/60386.shtml
- http://map.mobile.puhvjy.cn/Article/301524.shtml
- http://map.mobile.puhvjy.cn/Article/2130.shtml
- http://map.mobile.nwbbyt.cn/Article/1998847.shtml
- http://map.mobile.jnjpgf.cn/Article/861185.shtml
- http://map.mobile.puhvjy.cn/Article/9665907.shtml
- http://map.mobile.puhvjy.cn/Article/0109.shtml
- http://map.mobile.jnjpgf.cn/Article/85808.shtml
- http://map.mobile.jnjpgf.cn/Article/231557.shtml
- http://map.mobile.puhvjy.cn/Article/47560.shtml
- http://map.mobile.nwbbyt.cn/Article/0233489.shtml
- http://map.mobile.jnjpgf.cn/Article/2100.shtml
- http://map.mobile.cmcvrr.cn/Article/618897.shtml
- http://map.mobile.puhvjy.cn/Article/460608.shtml
- http://map.mobile.puhvjy.cn/Article/199324.shtml
- http://map.mobile.jnjpgf.cn/Article/2479889.shtml
- http://map.mobile.cmcvrr.cn/Article/266785.shtml
- http://map.mobile.jnjpgf.cn/Article/96638.shtml
- http://map.mobile.puhvjy.cn/Article/02527.shtml
- http://map.mobile.cmcvrr.cn/Article/9368.shtml
- http://map.mobile.cmcvrr.cn/Article/552150.shtml
- http://map.mobile.cmcvrr.cn/Article/174878.shtml
- http://map.mobile.puhvjy.cn/Article/5794.shtml
- http://map.mobile.jnjpgf.cn/Article/983153.shtml
- http://map.mobile.cmcvrr.cn/Article/83900.shtml
- http://map.mobile.puhvjy.cn/Article/0643433.shtml
- http://map.mobile.nwbbyt.cn/Article/698436.shtml
- http://map.mobile.jnjpgf.cn/Article/5250.shtml
- http://map.mobile.puhvjy.cn/Article/9998.shtml
- http://map.mobile.nwbbyt.cn/Article/170291.shtml
- http://map.mobile.cmcvrr.cn/Article/0776.shtml
- http://map.mobile.jnjpgf.cn/Article/20029.shtml
- http://map.mobile.puhvjy.cn/Article/9741.shtml
- http://map.mobile.puhvjy.cn/Article/01779.shtml
- http://map.mobile.jnjpgf.cn/Article/8596.shtml
- http://map.mobile.jnjpgf.cn/Article/1763410.shtml
- http://map.mobile.nwbbyt.cn/Article/35384.shtml
- http://map.mobile.cmcvrr.cn/Article/8278242.shtml
- http://map.mobile.jnjpgf.cn/Article/5487.shtml
- http://map.mobile.nwbbyt.cn/Article/1275.shtml
- http://map.mobile.cmcvrr.cn/Article/7096.shtml
- http://map.mobile.cmcvrr.cn/Article/848573.shtml
- http://map.mobile.jnjpgf.cn/Article/709436.shtml
- http://map.mobile.puhvjy.cn/Article/6023.shtml
- http://map.mobile.nwbbyt.cn/Article/309767.shtml
- http://map.mobile.jnjpgf.cn/Article/4486.shtml
- http://map.mobile.puhvjy.cn/Article/2278.shtml
- http://map.mobile.puhvjy.cn/Article/70882.shtml
- http://map.mobile.jnjpgf.cn/Article/7929186.shtml
- http://map.mobile.nwbbyt.cn/Article/888120.shtml
- http://map.mobile.cmcvrr.cn/Article/54816.shtml
- http://map.mobile.cmcvrr.cn/Article/3202.shtml
- http://map.mobile.cmcvrr.cn/Article/566215.shtml
- http://map.mobile.cmcvrr.cn/Article/0810.shtml
- http://map.mobile.jnjpgf.cn/Article/69141.shtml
- http://map.mobile.puhvjy.cn/Article/08697.shtml
- http://map.mobile.jnjpgf.cn/Article/5977486.shtml
- http://map.mobile.nwbbyt.cn/Article/0886.shtml
- http://map.mobile.nwbbyt.cn/Article/25371.shtml
- http://map.mobile.cmcvrr.cn/Article/1956998.shtml
- http://map.mobile.nwbbyt.cn/Article/36282.shtml
- http://map.mobile.nwbbyt.cn/Article/182605.shtml
- http://map.mobile.cmcvrr.cn/Article/412222.shtml
- http://map.mobile.jnjpgf.cn/Article/3239376.shtml
- http://map.mobile.puhvjy.cn/Article/5725.shtml
- http://map.mobile.cmcvrr.cn/Article/26807.shtml
- http://map.mobile.puhvjy.cn/Article/29226.shtml
- http://map.mobile.nwbbyt.cn/Article/9236.shtml
- http://map.mobile.cmcvrr.cn/Article/23027.shtml
- http://map.mobile.cmcvrr.cn/Article/4806553.shtml
- http://map.mobile.jnjpgf.cn/Article/923568.shtml
- http://map.mobile.cmcvrr.cn/Article/61565.shtml
- http://map.mobile.jnjpgf.cn/Article/067097.shtml
- http://map.mobile.jnjpgf.cn/Article/789013.shtml
- http://map.mobile.puhvjy.cn/Article/383173.shtml
- http://map.mobile.jnjpgf.cn/Article/28662.shtml
- http://map.mobile.nwbbyt.cn/Article/7201836.shtml
- http://map.mobile.jnjpgf.cn/Article/7007.shtml
- http://map.mobile.puhvjy.cn/Article/7565.shtml

## 项目结构

```
linkmap-mobile/
├── data/                                 # 数据存储目录，所有资源列表和元数据文件
│   ├── raw/                              # 原始导入文件备份（CSV/JSON 格式）
│   │   ├── batch_26.json                 # 上一批次导入的原始数据快照
│   │   └── batch_27.json                 # 当前批次（第27批）原始数据
│   ├── indexed/                          # 构建后的索引文件（按标签和域名分区）
│   │   ├── by_domain/                    # 按一级域名分组的索引子目录
│   │   ├── by_tag/                       # 按标签分类的索引子目录
│   │   └── full_index.json               # 全量倒排索引主文件
│   └── assets/                           # 静态资源导出目录（离线浏览用）
│       ├── index.html                    # 离线面板主页
│       └── style.css                     # 面板样式表
├── src/                                  # 源代码目录
│   ├── cli/                              # CLI 命令行工具模块
│   │   ├── import.js                     # 批量导入逻辑
│   │   ├── validate.js                   # URL 校验与去重
│   │   └── export.js                     # 导出静态 HTML 和报告
│   ├── core/                             # 核心引擎模块
│   │   ├── indexer.js                    # 索引构建引擎
│   │   ├── searcher.js                   # 全文检索实现（封装 ripgrep）
│   │   └── health.js                     # 健康检查调度器
│   ├── server/                           # 本地开发服务器模块
│   │   ├── app.js                        # Express 应用主入口
│   │   ├── routes/                       # API 路由定义
│   │   └── middleware/                   # 请求拦截与日志中间件
│   └── utils/                            # 通用工具函数集合
│       ├── parser.js                     # URL 解析与标准化
│       ├── logger.js                     # 日志记录器（支持 JSON 格式输出）
│       └── config.js                     # 配置读取与环境变量校验
├── tests/                                # 单元测试与集成测试目录
│   ├── unit/                             # 单元测试（使用 Jest）
│   └── integration/                      # 集成测试（模拟完整构建流程）
├── docs/                                 # 完整文档体系
│   ├── user-guide/                       # 用户手册章节
│   ├── operations/                       # 运维与部署文档
│   ├── developer/                        # 开发者指南与 API 参考
│   └── design/                           # 设计文档与架构决策记录
├── scripts/                              # 辅助运维脚本（CI/CD 用）
│   ├── pre-commit.sh                     # Git 提交前校验脚本
│   ├── daily-health-check.sh             # 每日健康检查定时任务脚本
│   └── generate-report.sh                # 生成 Markdown 周报统计脚本
├── .github/                              # GitHub 工作流配置
│   ├── workflows/                        # Actions 流水线定义
│   │   ├── ci.yml                        # 持续集成流水线（构建、测试、校验）
│   │   └── schedule.yml                  # 定时健康检查流水线
│   └── ISSUE_TEMPLATE/                   # 新链接提交和问题反馈模板
├── package.json                          # npm 项目配置与脚本定义
├── README.md                             # 项目入口文档（本文件）
└── LICENSE                               # MIT 许可证文本
```

## 贡献指南

提交新资源链接前，请先执行本地去重校验，确保待添加的 URL 未存在于当前索引中。可通过 `npm run check:dup -- <url>` 命令进行单条校验。

所有新增、修改或删除链接的操作均需通过 Pull Request 提交。PR 标题请遵循 `[类别] 简要描述` 格式，类别包括 `add`、`update`、`remove` 和 `fix`。

在 PR 描述中需注明操作原因，例如新链接的来源依据、旧链接失效的检测结果或内容变更为非预期页面的证据。项目维护者会在 48 小时内进行审阅。

提交前请运行 `npm run test` 确保所有单元测试和集成测试通过，并执行 `npm run lint:data` 校验数据目录下所有 Markdown 列表的语法正确性。

对于批量导入（超过 10 条链接），请使用 `npm run import:batch -- --file <path>` 命令，并提供原始来源文件的说明和采集时间范围，以便追溯。

## 常见问题

Q: 健康检查模块报告大量链接状态码为 403 或 429，是否视为失效？
A: 403 通常表示服务器拒绝了 HEAD 请求，部分 CDN 或源站会屏蔽非浏览器的探测请求。此时系统会自动在 24 小时后重试一次，若仍返回 403 且响应头中不包含 `X-Robots-Tag`，则标记为 "需人工复核" 而不直接列为失效。429 则按照响应头中的 `Retry-After` 字段进行退避等待，若未提供该字段则默认等待 3600 秒后重试。人工复核建议通过浏览器直接访问验证。

Q: 如何迁移 LinkMap 数据到另一台服务器或新仓库？
A: 所有数据均存储在 `/data` 目录下，迁移时只需完整复制该目录即可。索引文件 `full_index.json` 和按域名的分区索引会在下次运行 `npm run build:index` 时自动根据 `/data/raw` 和 `/data/indexed` 中的已有文件进行重建，无需额外导出导入流程。建议同时复制 `/config/local.json` 以保留自定义标签映射规则。

Q: 项目中的 URL 资源列表是否会定期自动更新内容快照？
A: 本项目定位为链接索引管理工具，默认不抓取目标页面的完整 HTML 内容，仅记录 URL 元数据（标题、摘要）和健康状态。若需要页面内容归档，请自行配置外部爬虫或使用浏览器书签的离线保存功能。LinkMap 的核心设计理念是轻量化索引，而非内容缓存。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
