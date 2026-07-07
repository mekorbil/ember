# Mobile Map Resource Aggregator

Mobile Map Resource Aggregator (MMRA) 是一个面向移动端地理信息开发者和数据分析师的技术资源外链汇总工具。该项目通过系统化收集、分类和索引来自多个移动地图服务提供方的技术文档、API 说明、数据处理案例与运维日志，帮助开发团队快速定位所需的技术参考资料，减少在分散来源中检索信息的时间成本。

项目定位为技术资源导航中间层，不存储任何实际内容，仅提供结构化外链索引与基础元数据标注。适用于需要频繁查阅不同移动地图平台接口变更、故障处理记录或数据更新公告的开发运维人员。

## 功能概览

**多源外链统一收录** 系统化收集来自多个移动地图服务域的技术文章链接，并按来源域名和文章编号建立索引。

**分类筛选与全文检索** 支持按来源域名、发布时间段和文章类型进行筛选，提供基于文章标题和摘要的全文检索能力。

**元数据自动提取** 对外链页面进行轻量级元数据抓取，自动提取文章标题、发布日期、内容摘要和关键标签。

**定期健康检查** 每日自动检测已收录外链的可访问性，标记失效链接并生成异常报告。

**标签体系与关联推荐** 为每篇文章标注技术主题标签，基于标签共现关系推荐相关阅读。

**RSS 订阅与更新通知** 提供按来源域名的 RSS 订阅源，支持邮件和 Webhook 方式的更新推送。

**导入导出与批量操作** 支持 CSV 和 JSON 格式的链接列表批量导入导出，便于团队间共享资源索引。

## 应用场景

移动端地图 SDK 集成与维护 开发团队在接入或升级某个移动地图 SDK 时，需要查阅该平台近期的 API 变更公告、已知问题修复记录和兼容性说明。通过本项目的按域名筛选功能，可快速聚合特定平台的全部技术文章，系统性地完成集成前的调研工作。

线上故障排查与根因分析 当移动地图服务出现异常时，运维人员需要快速查看相关平台近期的运维日志、故障处理报告和临时补丁说明。本项目的全文检索功能支持按关键词和时间范围定位相关文档，缩短故障排查时间。

技术选型与平台对比 架构师在进行移动地图服务技术选型时，需要横向对比多个平台的性能数据、功能更新频率和社区活跃度。本项目的标签体系和关联推荐功能可辅助生成对比分析所需的参考资料清单。

定期技术知识库维护 技术团队的知识管理负责人可定期通过本项目的导入导出功能，将团队内部积累的地图相关技术链接汇总至统一索引，配合健康检查功能自动清理失效资源，保持知识库的有效性。

## 快速开始

以下命令演示如何获取项目代码、安装依赖并启动本地服务。

```bash
git clone https://github.com/example/mmra.git
cd mmra
npm install
npm run build
npm start
```

若使用 Docker 方式运行，可执行以下命令：

```bash
docker build -t mmra:latest .
docker run -d -p 3000:3000 --name mmra mmra:latest
```

服务启动后，访问 http://localhost:3000 即可进入资源检索界面。首次启动会自动执行外链健康检查，耗时约 3 至 5 分钟，检查结果将写入 logs 目录。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.0.0 或更高 | 运行时环境，建议使用 LTS 版本 |
| npm | 9.0.0 或更高 | 包管理器，用于安装项目依赖 |
| PostgreSQL | 14.0 或更高 | 主数据库，存储链接索引和元数据 |
| Redis | 7.0 或更高 | 缓存层，用于提升检索响应速度 |
| Elasticsearch | 8.5 或更高 | 全文检索引擎，提供分词和相关性排序 |
| PM2 | 5.0 或更高 | 进程管理工具，用于生产环境守护（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/ | 如何使用检索、筛选和订阅功能；如何导入导出链接列表 |
| 管理员手册 | /docs/admin/ | 如何配置健康检查策略；如何管理标签体系；如何清理失效链接 |
| 开发者文档 | /docs/developer/ | 如何扩展新的外链来源；如何自定义元数据提取规则；API 接口说明 |
| 部署运维 | /docs/deployment/ | 如何在不同环境中部署；如何配置数据库连接和缓存策略；日志与监控方案 |
| 数据模型 | /docs/data-model/ | 链接、标签、来源域名、健康检查记录等核心数据表结构说明 |

## 资源列表

- http://map.mobile.cmcvrr.cn/Article/7172.shtml
- http://map.mobile.puhvjy.cn/Article/000425.shtml
- http://map.mobile.nwbbyt.cn/Article/0162.shtml
- http://map.mobile.puhvjy.cn/Article/9632495.shtml
- http://map.mobile.jnjpgf.cn/Article/190942.shtml
- http://map.mobile.nwbbyt.cn/Article/88695.shtml
- http://map.mobile.cmcvrr.cn/Article/3856146.shtml
- http://map.mobile.jnjpgf.cn/Article/825098.shtml
- http://map.mobile.puhvjy.cn/Article/8367.shtml
- http://map.mobile.cmcvrr.cn/Article/25604.shtml
- http://map.mobile.puhvjy.cn/Article/1715.shtml
- http://map.mobile.cmcvrr.cn/Article/7046.shtml
- http://map.mobile.jnjpgf.cn/Article/513695.shtml
- http://map.mobile.nwbbyt.cn/Article/44536.shtml
- http://map.mobile.nwbbyt.cn/Article/51503.shtml
- http://map.mobile.puhvjy.cn/Article/66943.shtml
- http://map.mobile.jnjpgf.cn/Article/274868.shtml
- http://map.mobile.puhvjy.cn/Article/74489.shtml
- http://map.mobile.puhvjy.cn/Article/9113.shtml
- http://map.mobile.nwbbyt.cn/Article/119855.shtml
- http://map.mobile.cmcvrr.cn/Article/386783.shtml
- http://map.mobile.cmcvrr.cn/Article/8214452.shtml
- http://map.mobile.cmcvrr.cn/Article/519015.shtml
- http://map.mobile.puhvjy.cn/Article/0034681.shtml
- http://map.mobile.puhvjy.cn/Article/00330.shtml
- http://map.mobile.nwbbyt.cn/Article/3862127.shtml
- http://map.mobile.jnjpgf.cn/Article/0166575.shtml
- http://map.mobile.cmcvrr.cn/Article/59636.shtml
- http://map.mobile.cmcvrr.cn/Article/0818492.shtml
- http://map.mobile.cmcvrr.cn/Article/4275.shtml
- http://map.mobile.puhvjy.cn/Article/956950.shtml
- http://map.mobile.cmcvrr.cn/Article/972871.shtml
- http://map.mobile.nwbbyt.cn/Article/6813006.shtml
- http://map.mobile.puhvjy.cn/Article/11612.shtml
- http://map.mobile.puhvjy.cn/Article/6272.shtml
- http://map.mobile.nwbbyt.cn/Article/20242.shtml
- http://map.mobile.cmcvrr.cn/Article/9688.shtml
- http://map.mobile.cmcvrr.cn/Article/2462076.shtml
- http://map.mobile.puhvjy.cn/Article/8797.shtml
- http://map.mobile.nwbbyt.cn/Article/356769.shtml
- http://map.mobile.puhvjy.cn/Article/352772.shtml
- http://map.mobile.cmcvrr.cn/Article/6767867.shtml
- http://map.mobile.jnjpgf.cn/Article/830095.shtml
- http://map.mobile.puhvjy.cn/Article/00462.shtml
- http://map.mobile.puhvjy.cn/Article/319653.shtml
- http://map.mobile.nwbbyt.cn/Article/43597.shtml
- http://map.mobile.cmcvrr.cn/Article/2358310.shtml
- http://map.mobile.puhvjy.cn/Article/8865757.shtml
- http://map.mobile.puhvjy.cn/Article/570334.shtml
- http://map.mobile.cmcvrr.cn/Article/1192085.shtml
- http://map.mobile.puhvjy.cn/Article/04522.shtml
- http://map.mobile.puhvjy.cn/Article/293357.shtml
- http://map.mobile.cmcvrr.cn/Article/837178.shtml
- http://map.mobile.nwbbyt.cn/Article/7548730.shtml
- http://map.mobile.nwbbyt.cn/Article/795442.shtml
- http://map.mobile.jnjpgf.cn/Article/8145360.shtml
- http://map.mobile.nwbbyt.cn/Article/4471.shtml
- http://map.mobile.jnjpgf.cn/Article/4391.shtml
- http://map.mobile.jnjpgf.cn/Article/385286.shtml
- http://map.mobile.nwbbyt.cn/Article/667967.shtml
- http://map.mobile.puhvjy.cn/Article/3647.shtml
- http://map.mobile.cmcvrr.cn/Article/8878.shtml
- http://map.mobile.cmcvrr.cn/Article/83433.shtml
- http://map.mobile.cmcvrr.cn/Article/250253.shtml
- http://map.mobile.cmcvrr.cn/Article/508113.shtml
- http://map.mobile.jnjpgf.cn/Article/314496.shtml
- http://map.mobile.cmcvrr.cn/Article/6935.shtml
- http://map.mobile.jnjpgf.cn/Article/5549.shtml
- http://map.mobile.puhvjy.cn/Article/520677.shtml
- http://map.mobile.puhvjy.cn/Article/36280.shtml
- http://map.mobile.jnjpgf.cn/Article/88903.shtml
- http://map.mobile.puhvjy.cn/Article/89032.shtml
- http://map.mobile.cmcvrr.cn/Article/45520.shtml
- http://map.mobile.jnjpgf.cn/Article/556066.shtml
- http://map.mobile.cmcvrr.cn/Article/41028.shtml
- http://map.mobile.cmcvrr.cn/Article/0528446.shtml
- http://map.mobile.puhvjy.cn/Article/69199.shtml
- http://map.mobile.cmcvrr.cn/Article/5327066.shtml
- http://map.mobile.nwbbyt.cn/Article/9680.shtml
- http://map.mobile.puhvjy.cn/Article/890136.shtml
- http://map.mobile.nwbbyt.cn/Article/52888.shtml
- http://map.mobile.nwbbyt.cn/Article/18831.shtml
- http://map.mobile.puhvjy.cn/Article/653365.shtml
- http://map.mobile.nwbbyt.cn/Article/42391.shtml
- http://map.mobile.jnjpgf.cn/Article/906789.shtml
- http://map.mobile.cmcvrr.cn/Article/589822.shtml
- http://map.mobile.nwbbyt.cn/Article/1943156.shtml
- http://map.mobile.puhvjy.cn/Article/315818.shtml
- http://map.mobile.puhvjy.cn/Article/856965.shtml
- http://map.mobile.cmcvrr.cn/Article/745535.shtml
- http://map.mobile.puhvjy.cn/Article/7394.shtml
- http://map.mobile.puhvjy.cn/Article/090485.shtml
- http://map.mobile.cmcvrr.cn/Article/6221.shtml
- http://map.mobile.jnjpgf.cn/Article/61320.shtml
- http://map.mobile.puhvjy.cn/Article/80202.shtml
- http://map.mobile.jnjpgf.cn/Article/5697.shtml
- http://map.mobile.nwbbyt.cn/Article/01503.shtml
- http://map.mobile.nwbbyt.cn/Article/8268.shtml
- http://map.mobile.jnjpgf.cn/Article/86289.shtml
- http://map.mobile.cmcvrr.cn/Article/2758.shtml
- http://map.mobile.puhvjy.cn/Article/528151.shtml
- http://map.mobile.cmcvrr.cn/Article/60763.shtml
- http://map.mobile.jnjpgf.cn/Article/387922.shtml
- http://map.mobile.nwbbyt.cn/Article/3474231.shtml
- http://map.mobile.jnjpgf.cn/Article/7544158.shtml
- http://map.mobile.cmcvrr.cn/Article/8373968.shtml
- http://map.mobile.nwbbyt.cn/Article/324983.shtml
- http://map.mobile.nwbbyt.cn/Article/6082.shtml
- http://map.mobile.puhvjy.cn/Article/270459.shtml
- http://map.mobile.puhvjy.cn/Article/621504.shtml
- http://map.mobile.puhvjy.cn/Article/243660.shtml
- http://map.mobile.jnjpgf.cn/Article/24191.shtml
- http://map.mobile.jnjpgf.cn/Article/24919.shtml
- http://map.mobile.jnjpgf.cn/Article/4313.shtml
- http://map.mobile.puhvjy.cn/Article/7151.shtml
- http://map.mobile.nwbbyt.cn/Article/584760.shtml
- http://map.mobile.jnjpgf.cn/Article/8982528.shtml
- http://map.mobile.cmcvrr.cn/Article/6455604.shtml
- http://map.mobile.nwbbyt.cn/Article/7671.shtml
- http://map.mobile.nwbbyt.cn/Article/93633.shtml
- http://map.mobile.puhvjy.cn/Article/0633644.shtml
- http://map.mobile.jnjpgf.cn/Article/0203199.shtml
- http://map.mobile.cmcvrr.cn/Article/5000384.shtml
- http://map.mobile.jnjpgf.cn/Article/8703830.shtml
- http://map.mobile.nwbbyt.cn/Article/9902034.shtml
- http://map.mobile.cmcvrr.cn/Article/9708409.shtml
- http://map.mobile.cmcvrr.cn/Article/749137.shtml
- http://map.mobile.jnjpgf.cn/Article/8424742.shtml
- http://map.mobile.nwbbyt.cn/Article/50582.shtml
- http://map.mobile.cmcvrr.cn/Article/21562.shtml
- http://map.mobile.nwbbyt.cn/Article/5465.shtml
- http://map.mobile.jnjpgf.cn/Article/495759.shtml
- http://map.mobile.nwbbyt.cn/Article/512649.shtml
- http://map.mobile.puhvjy.cn/Article/4321110.shtml
- http://map.mobile.cmcvrr.cn/Article/6253.shtml
- http://map.mobile.jnjpgf.cn/Article/1262.shtml
- http://map.mobile.jnjpgf.cn/Article/6857.shtml
- http://map.mobile.puhvjy.cn/Article/0038677.shtml
- http://map.mobile.cmcvrr.cn/Article/462618.shtml
- http://map.mobile.puhvjy.cn/Article/3024081.shtml
- http://map.mobile.puhvjy.cn/Article/3112636.shtml
- http://map.mobile.nwbbyt.cn/Article/7308440.shtml
- http://map.mobile.jnjpgf.cn/Article/9294.shtml
- http://map.mobile.jnjpgf.cn/Article/102634.shtml
- http://map.mobile.puhvjy.cn/Article/964194.shtml
- http://map.mobile.nwbbyt.cn/Article/6372.shtml
- http://map.mobile.nwbbyt.cn/Article/61008.shtml
- http://map.mobile.jnjpgf.cn/Article/195250.shtml
- http://map.mobile.cmcvrr.cn/Article/4246.shtml
- http://map.mobile.jnjpgf.cn/Article/1527041.shtml
- http://map.mobile.jnjpgf.cn/Article/62698.shtml
- http://map.mobile.nwbbyt.cn/Article/059243.shtml
- http://map.mobile.jnjpgf.cn/Article/25386.shtml
- http://map.mobile.nwbbyt.cn/Article/167341.shtml
- http://map.mobile.jnjpgf.cn/Article/0850.shtml
- http://map.mobile.cmcvrr.cn/Article/7313.shtml
- http://map.mobile.jnjpgf.cn/Article/232339.shtml
- http://map.mobile.cmcvrr.cn/Article/4608.shtml
- http://map.mobile.nwbbyt.cn/Article/843663.shtml
- http://map.mobile.jnjpgf.cn/Article/0469727.shtml
- http://map.mobile.nwbbyt.cn/Article/032241.shtml
- http://map.mobile.jnjpgf.cn/Article/6945.shtml
- http://map.mobile.jnjpgf.cn/Article/0827.shtml
- http://map.mobile.cmcvrr.cn/Article/809920.shtml
- http://map.mobile.jnjpgf.cn/Article/30235.shtml
- http://map.mobile.cmcvrr.cn/Article/84283.shtml
- http://map.mobile.puhvjy.cn/Article/3589599.shtml
- http://map.mobile.puhvjy.cn/Article/27794.shtml
- http://map.mobile.cmcvrr.cn/Article/3945.shtml
- http://map.mobile.nwbbyt.cn/Article/46841.shtml
- http://map.mobile.jnjpgf.cn/Article/113001.shtml
- http://map.mobile.puhvjy.cn/Article/700359.shtml
- http://map.mobile.jnjpgf.cn/Article/4909673.shtml
- http://map.mobile.nwbbyt.cn/Article/595948.shtml
- http://map.mobile.nwbbyt.cn/Article/8002245.shtml
- http://map.mobile.jnjpgf.cn/Article/1904.shtml
- http://map.mobile.puhvjy.cn/Article/633805.shtml
- http://map.mobile.puhvjy.cn/Article/6431.shtml
- http://map.mobile.cmcvrr.cn/Article/2174.shtml
- http://map.mobile.jnjpgf.cn/Article/7836.shtml
- http://map.mobile.jnjpgf.cn/Article/0094.shtml
- http://map.mobile.puhvjy.cn/Article/9660757.shtml
- http://map.mobile.puhvjy.cn/Article/9184799.shtml
- http://map.mobile.cmcvrr.cn/Article/3638803.shtml
- http://map.mobile.cmcvrr.cn/Article/36043.shtml
- http://map.mobile.nwbbyt.cn/Article/3372822.shtml
- http://map.mobile.jnjpgf.cn/Article/001100.shtml
- http://map.mobile.jnjpgf.cn/Article/1022.shtml
- http://map.mobile.nwbbyt.cn/Article/3862.shtml
- http://map.mobile.nwbbyt.cn/Article/31389.shtml
- http://map.mobile.puhvjy.cn/Article/52463.shtml
- http://map.mobile.nwbbyt.cn/Article/553594.shtml
- http://map.mobile.nwbbyt.cn/Article/793859.shtml
- http://map.mobile.puhvjy.cn/Article/2549942.shtml
- http://map.mobile.nwbbyt.cn/Article/8945.shtml
- http://map.mobile.jnjpgf.cn/Article/1091.shtml
- http://map.mobile.cmcvrr.cn/Article/0566958.shtml
- http://map.mobile.puhvjy.cn/Article/88524.shtml
- http://map.mobile.nwbbyt.cn/Article/2871.shtml
- http://map.mobile.nwbbyt.cn/Article/5020.shtml
- http://map.mobile.cmcvrr.cn/Article/6527028.shtml
- http://map.mobile.cmcvrr.cn/Article/20192.shtml
- http://map.mobile.cmcvrr.cn/Article/8404.shtml
- http://map.mobile.jnjpgf.cn/Article/4284.shtml
- http://map.mobile.jnjpgf.cn/Article/9584.shtml
- http://map.mobile.puhvjy.cn/Article/248663.shtml
- http://map.mobile.jnjpgf.cn/Article/8294327.shtml
- http://map.mobile.jnjpgf.cn/Article/7507.shtml
- http://map.mobile.puhvjy.cn/Article/8853.shtml
- http://map.mobile.nwbbyt.cn/Article/84202.shtml
- http://map.mobile.nwbbyt.cn/Article/7016919.shtml
- http://map.mobile.jnjpgf.cn/Article/3957.shtml
- http://map.mobile.cmcvrr.cn/Article/6357849.shtml
- http://map.mobile.jnjpgf.cn/Article/8014.shtml
- http://map.mobile.cmcvrr.cn/Article/1475698.shtml
- http://map.mobile.nwbbyt.cn/Article/7775804.shtml
- http://map.mobile.nwbbyt.cn/Article/260512.shtml
- http://map.mobile.puhvjy.cn/Article/893362.shtml
- http://map.mobile.cmcvrr.cn/Article/1109.shtml
- http://map.mobile.nwbbyt.cn/Article/5739.shtml
- http://map.mobile.nwbbyt.cn/Article/0715.shtml
- http://map.mobile.jnjpgf.cn/Article/6896.shtml
- http://map.mobile.puhvjy.cn/Article/3080933.shtml
- http://map.mobile.jnjpgf.cn/Article/7947.shtml
- http://map.mobile.cmcvrr.cn/Article/20156.shtml
- http://map.mobile.jnjpgf.cn/Article/0414.shtml
- http://map.mobile.jnjpgf.cn/Article/7995.shtml
- http://map.mobile.cmcvrr.cn/Article/1357.shtml
- http://map.mobile.cmcvrr.cn/Article/73990.shtml
- http://map.mobile.cmcvrr.cn/Article/9920.shtml
- http://map.mobile.puhvjy.cn/Article/72694.shtml
- http://map.mobile.nwbbyt.cn/Article/007867.shtml
- http://map.mobile.puhvjy.cn/Article/6242945.shtml
- http://map.mobile.puhvjy.cn/Article/104362.shtml
- http://map.mobile.cmcvrr.cn/Article/4517788.shtml
- http://map.mobile.puhvjy.cn/Article/804610.shtml
- http://map.mobile.nwbbyt.cn/Article/392800.shtml
- http://map.mobile.puhvjy.cn/Article/0562223.shtml
- http://map.mobile.puhvjy.cn/Article/383872.shtml
- http://map.mobile.jnjpgf.cn/Article/39156.shtml
- http://map.mobile.jnjpgf.cn/Article/9556282.shtml
- http://map.mobile.cmcvrr.cn/Article/513789.shtml
- http://map.mobile.puhvjy.cn/Article/796822.shtml
- http://map.mobile.jnjpgf.cn/Article/1511.shtml
- http://map.mobile.nwbbyt.cn/Article/3670284.shtml
- http://map.mobile.nwbbyt.cn/Article/423964.shtml
- http://map.mobile.jnjpgf.cn/Article/8071108.shtml
- http://map.mobile.puhvjy.cn/Article/88222.shtml
- http://map.mobile.cmcvrr.cn/Article/211181.shtml
- http://map.mobile.jnjpgf.cn/Article/300914.shtml

## 项目结构

```
mmra/
├── src/                               # 源代码主目录
│   ├── core/                          # 核心业务逻辑模块
│   │   ├── crawler.js                 # 外链元数据抓取引擎
│   │   ├── health-check.js            # 链接健康检查调度器
│   │   └── indexer.js                 # Elasticsearch 索引管理
│   ├── api/                           # RESTful API 路由层
│   │   ├── links.js                   # 链接检索与筛选接口
│   │   ├── tags.js                    # 标签管理接口
│   │   └── import-export.js           # 批量导入导出接口
│   ├── services/                      # 外部服务集成层
│   │   ├── database.js                # PostgreSQL 连接池与查询构造
│   │   ├── redis.js                   # Redis 缓存操作封装
│   │   └── elastic.js                 # Elasticsearch 客户端封装
│   ├── models/                        # 数据模型定义
│   │   ├── Link.js                    # 链接实体模型
│   │   ├── Source.js                  # 来源域名模型
│   │   └── CheckRecord.js             # 健康检查记录模型
│   ├── workers/                       # 后台任务进程
│   │   ├── update-metadata.js         # 元数据批量更新任务
│   │   └── send-notification.js       # RSS 与 Webhook 推送任务
│   └── utils/                         # 通用工具函数
│       ├── validator.js               # URL 格式校验与规范化
│       └── logger.js                  # 统一日志输出格式
├── config/                            # 配置文件目录
│   ├── default.yaml                   # 默认配置（开发环境）
│   ├── production.yaml                # 生产环境覆盖配置
│   └── schema.yaml                    # 配置项说明与校验规则
├── migrations/                        # 数据库迁移脚本
│   ├── 001_init_links.sql             # 链接表初始建表语句
│   ├── 002_add_tags.sql               # 标签表与关联表
│   └── 003_add_check_records.sql      # 健康检查记录表
├── scripts/                           # 运维与辅助脚本
│   ├── seed.js                        # 初始数据填充脚本
│   └── clean-expired.js               # 过期缓存清理脚本
├── tests/                             # 单元测试与集成测试
│   ├── unit/                          # 单元测试用例
│   └── integration/                   # 接口集成测试
├── logs/                              # 日志存储目录（运行时生成）
├── public/                            # 前端静态资源
│   ├── index.html                     # 主页面入口
│   └── css/                           # 样式文件
├── package.json                       # npm 项目清单
├── Dockerfile                         # Docker 镜像构建文件
├── docker-compose.yml                 # 本地开发环境编排配置
└── README.md                          # 项目说明文档（本文件）
```

## 贡献指南

提交 Issue 报告问题 在 GitHub Issues 页面提交新 Issue，使用提供的模板填写问题类型、复现步骤和运行环境信息。建议在提交前搜索已有 Issue，避免重复报告。

创建分支并编写代码 从 main 分支创建新的功能分支，命名格式为 feature/功能简述 或 fix/问题简述。代码编写需遵循项目 ESLint 配置，并确保所有单元测试通过。

提交 Pull Request 推送分支至远程仓库后，在 GitHub 上创建 Pull Request。PR 描述中需说明变更目的、实现方案和测试覆盖情况。至少需要一名项目维护者审核通过后方可合并。

更新文档与迁移脚本 若变更涉及配置项变动、新增 API 接口或数据库结构调整，需同步更新 docs 目录下的对应文档，并在 migrations 目录中添加相应的迁移脚本。

参与代码审查与讨论 欢迎在他人提交的 Pull Request 中参与代码审查，提出建设性意见。对于长期活跃的贡献者，项目维护团队将邀请加入核心开发者小组。

## 常见问题

Q: 健康检查功能检测到失效链接后会如何处理？

A: 健康检查任务每日凌晨 2:00 自动执行。检测到失效链接后，系统会将该链接的状态标记为 unavailable，并记录最后一次成功访问的时间戳。失效链接不会从索引中删除，但在检索结果中会默认排在最后，并附有警告标识。管理员可在后台手动重新验证，或通过导入功能更新链接地址。

Q: 如何添加新的外链接入来源？

A: 新来源的接入需要完成两步操作。首先在数据库的 sources 表中插入新记录，填写域名、名称和默认标签。然后在 config/default.yaml 中的 crawler.rules 段落添加对应的元数据提取规则，包括标题选择器、日期选择器和正文摘要选择器。规则语法基于 CSS 选择器或 XPath。添加完成后，执行 npm run refresh-sources 命令即可对新来源的历史文章进行回溯抓取。

Q: 全文检索的搜索结果相关性不如预期，如何调优？

A: 相关性排序由 Elasticsearch 的评分机制决定。可通过调整 config/default.yaml 中 elasticsearch.settings 下的 similarity 参数和字段权重（field boost）来优化。常见的调优方向包括提高标题字段的权重、为短文档增加长度归一化补偿，以及根据点击日志配置学习排序（Learning to Rank）模型。更详细的调优指南请参考 docs/developer/search-tuning.md。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
