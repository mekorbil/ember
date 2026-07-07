# MobileLink 聚合索引服务

MobileLink 聚合索引服务是一个面向移动端技术内容与行业资讯的轻量级资源导航系统。该项目定位于技术社区维护者、内容运营人员以及个人研究者，用于对分散在不同移动域名下的技术文章、行业报告与案例分析进行统一索引、分类归档与快速检索。MobileLink 不直接存储或转发原始内容，而是基于结构化 URL 映射体系构建可扩展的外链索引目录，帮助用户在信息过载的环境中高效定位高价值技术资源。

## 功能概览

- **多源链接统一索引**：支持对多个移动端域名下的 Article 层级资源进行自动抓取与链接归类，形成单一入口的索引目录
- **结构化分类标记**：每条链接可根据域名来源、ID 范围、文章类型等维度自动打标，便于后续筛选与统计
- **批量链接状态巡检**：提供定期巡检机制，检测已收录链接的可访问性与响应码状态，辅助运维人员清理失效条目
- **快速全文检索**：基于文章 ID 与来源域名的组合查询，支持模糊匹配与精确匹配，可快速定位具体资源
- **外链导出与订阅**：支持将索引列表导出为 JSON、CSV 或纯文本格式，亦可生成静态页面供团队内部订阅使用
- **访问热度统计**：统计各域名及文章目录的请求频次，帮助内容运营识别热点话题与高频访问资源
- **轻量级部署与维护**：无需数据库，基于文件系统或内存缓存即可运行，适合低资源环境与边缘节点部署

## 应用场景

**技术博客聚合站运维**：个人站长或小型技术团队可使用 MobileLink 整合分散在多个移动端子域名下的技术文章链接，构建统一的主题目录页，提升站内内容复用率与用户浏览连贯性。

**行业报告归档与查阅**：研究机构或咨询团队可将不同移动端来源的行业分析报告、白皮书链接统一纳入索引，通过分类标签实现按年份、领域或地区快速检索，减少重复收藏与丢失风险。

**开发文档外部引用管理**：软件开发团队在编写技术文档或 Wiki 时，可将 MobileLink 作为外部引用资源的中转索引，确保所有外链经过统一校验与备案，避免文档中出现大量不可控的第三方地址。

**内容合规审计辅助**：内容安全团队可利用 MobileLink 的批量链接巡检功能，定期对收录的所有外链进行可访问性与内容变动检测，辅助判断是否存在违规内容或站点异常。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境，依赖 Git 与 Node.js 18 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/mobile-link/mobilelink-index.git

# 进入项目目录
cd mobilelink-index

# 安装项目依赖
npm install

# 启动索引服务（默认端口 3000）
npm start
```

服务启动后，访问 `http://127.0.0.1:3000` 可查看索引面板概览，访问 `/index` 接口可获取当前全量链接目录的 JSON 输出。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，用于执行索引服务与脚本工具 |
| npm | 9.x 或更高 | 包管理工具，用于安装项目依赖模块 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与拉取更新 |
| 可用磁盘空间 | 至少 50 MB | 用于存储索引缓存、日志文件与临时数据 |
| 网络访问 | 出方向 80/443 开放 | 用于巡检收录链接的可访问状态 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | `/docs/quickstart.md` | 如何在一分钟内完成服务搭建并查看第一个索引目录 |
| 链接管理 | `/docs/link-management.md` | 如何新增、编辑或移除索引中的链接条目，以及批量导入导出操作 |
| 巡检配置 | `/docs/health-check.md` | 如何调整链接巡检频率、超时阈值与报警通知方式 |
| API 参考 | `/docs/api-reference.md` | 所有对外提供的 RESTful 接口定义、请求参数与返回示例 |

## 资源列表

- http://m.mobile.cmcvrr.cn/Article/7172.shtml
- http://m.mobile.puhvjy.cn/Article/000425.shtml
- http://m.mobile.nwbbyt.cn/Article/0162.shtml
- http://m.mobile.puhvjy.cn/Article/9632495.shtml
- http://m.mobile.jnjpgf.cn/Article/190942.shtml
- http://m.mobile.nwbbyt.cn/Article/88695.shtml
- http://m.mobile.cmcvrr.cn/Article/3856146.shtml
- http://m.mobile.jnjpgf.cn/Article/825098.shtml
- http://m.mobile.puhvjy.cn/Article/8367.shtml
- http://m.mobile.cmcvrr.cn/Article/25604.shtml
- http://m.mobile.puhvjy.cn/Article/1715.shtml
- http://m.mobile.cmcvrr.cn/Article/7046.shtml
- http://m.mobile.jnjpgf.cn/Article/513695.shtml
- http://m.mobile.nwbbyt.cn/Article/44536.shtml
- http://m.mobile.nwbbyt.cn/Article/51503.shtml
- http://m.mobile.puhvjy.cn/Article/66943.shtml
- http://m.mobile.jnjpgf.cn/Article/274868.shtml
- http://m.mobile.puhvjy.cn/Article/74489.shtml
- http://m.mobile.puhvjy.cn/Article/9113.shtml
- http://m.mobile.nwbbyt.cn/Article/119855.shtml
- http://m.mobile.cmcvrr.cn/Article/386783.shtml
- http://m.mobile.cmcvrr.cn/Article/8214452.shtml
- http://m.mobile.cmcvrr.cn/Article/519015.shtml
- http://m.mobile.puhvjy.cn/Article/0034681.shtml
- http://m.mobile.puhvjy.cn/Article/00330.shtml
- http://m.mobile.nwbbyt.cn/Article/3862127.shtml
- http://m.mobile.jnjpgf.cn/Article/0166575.shtml
- http://m.mobile.cmcvrr.cn/Article/59636.shtml
- http://m.mobile.cmcvrr.cn/Article/0818492.shtml
- http://m.mobile.cmcvrr.cn/Article/4275.shtml
- http://m.mobile.puhvjy.cn/Article/956950.shtml
- http://m.mobile.cmcvrr.cn/Article/972871.shtml
- http://m.mobile.nwbbyt.cn/Article/6813006.shtml
- http://m.mobile.puhvjy.cn/Article/11612.shtml
- http://m.mobile.puhvjy.cn/Article/6272.shtml
- http://m.mobile.nwbbyt.cn/Article/20242.shtml
- http://m.mobile.cmcvrr.cn/Article/9688.shtml
- http://m.mobile.cmcvrr.cn/Article/2462076.shtml
- http://m.mobile.puhvjy.cn/Article/8797.shtml
- http://m.mobile.nwbbyt.cn/Article/356769.shtml
- http://m.mobile.puhvjy.cn/Article/352772.shtml
- http://m.mobile.cmcvrr.cn/Article/6767867.shtml
- http://m.mobile.jnjpgf.cn/Article/830095.shtml
- http://m.mobile.puhvjy.cn/Article/00462.shtml
- http://m.mobile.puhvjy.cn/Article/319653.shtml
- http://m.mobile.nwbbyt.cn/Article/43597.shtml
- http://m.mobile.cmcvrr.cn/Article/2358310.shtml
- http://m.mobile.puhvjy.cn/Article/8865757.shtml
- http://m.mobile.puhvjy.cn/Article/570334.shtml
- http://m.mobile.cmcvrr.cn/Article/1192085.shtml
- http://m.mobile.puhvjy.cn/Article/04522.shtml
- http://m.mobile.puhvjy.cn/Article/293357.shtml
- http://m.mobile.cmcvrr.cn/Article/837178.shtml
- http://m.mobile.nwbbyt.cn/Article/7548730.shtml
- http://m.mobile.nwbbyt.cn/Article/795442.shtml
- http://m.mobile.jnjpgf.cn/Article/8145360.shtml
- http://m.mobile.nwbbyt.cn/Article/4471.shtml
- http://m.mobile.jnjpgf.cn/Article/4391.shtml
- http://m.mobile.jnjpgf.cn/Article/385286.shtml
- http://m.mobile.nwbbyt.cn/Article/667967.shtml
- http://m.mobile.puhvjy.cn/Article/3647.shtml
- http://m.mobile.cmcvrr.cn/Article/8878.shtml
- http://m.mobile.cmcvrr.cn/Article/83433.shtml
- http://m.mobile.cmcvrr.cn/Article/250253.shtml
- http://m.mobile.cmcvrr.cn/Article/508113.shtml
- http://m.mobile.jnjpgf.cn/Article/314496.shtml
- http://m.mobile.cmcvrr.cn/Article/6935.shtml
- http://m.mobile.jnjpgf.cn/Article/5549.shtml
- http://m.mobile.puhvjy.cn/Article/520677.shtml
- http://m.mobile.puhvjy.cn/Article/36280.shtml
- http://m.mobile.jnjpgf.cn/Article/88903.shtml
- http://m.mobile.puhvjy.cn/Article/89032.shtml
- http://m.mobile.cmcvrr.cn/Article/45520.shtml
- http://m.mobile.jnjpgf.cn/Article/556066.shtml
- http://m.mobile.cmcvrr.cn/Article/41028.shtml
- http://m.mobile.cmcvrr.cn/Article/0528446.shtml
- http://m.mobile.puhvjy.cn/Article/69199.shtml
- http://m.mobile.cmcvrr.cn/Article/5327066.shtml
- http://m.mobile.nwbbyt.cn/Article/9680.shtml
- http://m.mobile.puhvjy.cn/Article/890136.shtml
- http://m.mobile.nwbbyt.cn/Article/52888.shtml
- http://m.mobile.nwbbyt.cn/Article/18831.shtml
- http://m.mobile.puhvjy.cn/Article/653365.shtml
- http://m.mobile.nwbbyt.cn/Article/42391.shtml
- http://m.mobile.jnjpgf.cn/Article/906789.shtml
- http://m.mobile.cmcvrr.cn/Article/589822.shtml
- http://m.mobile.nwbbyt.cn/Article/1943156.shtml
- http://m.mobile.puhvjy.cn/Article/315818.shtml
- http://m.mobile.puhvjy.cn/Article/856965.shtml
- http://m.mobile.cmcvrr.cn/Article/745535.shtml
- http://m.mobile.puhvjy.cn/Article/7394.shtml
- http://m.mobile.puhvjy.cn/Article/090485.shtml
- http://m.mobile.cmcvrr.cn/Article/6221.shtml
- http://m.mobile.jnjpgf.cn/Article/61320.shtml
- http://m.mobile.puhvjy.cn/Article/80202.shtml
- http://m.mobile.jnjpgf.cn/Article/5697.shtml
- http://m.mobile.nwbbyt.cn/Article/01503.shtml
- http://m.mobile.nwbbyt.cn/Article/8268.shtml
- http://m.mobile.jnjpgf.cn/Article/86289.shtml
- http://m.mobile.cmcvrr.cn/Article/2758.shtml
- http://m.mobile.puhvjy.cn/Article/528151.shtml
- http://m.mobile.cmcvrr.cn/Article/60763.shtml
- http://m.mobile.jnjpgf.cn/Article/387922.shtml
- http://m.mobile.nwbbyt.cn/Article/3474231.shtml
- http://m.mobile.jnjpgf.cn/Article/7544158.shtml
- http://m.mobile.cmcvrr.cn/Article/8373968.shtml
- http://m.mobile.nwbbyt.cn/Article/324983.shtml
- http://m.mobile.nwbbyt.cn/Article/6082.shtml
- http://m.mobile.puhvjy.cn/Article/270459.shtml
- http://m.mobile.puhvjy.cn/Article/621504.shtml
- http://m.mobile.puhvjy.cn/Article/243660.shtml
- http://m.mobile.jnjpgf.cn/Article/24191.shtml
- http://m.mobile.jnjpgf.cn/Article/24919.shtml
- http://m.mobile.jnjpgf.cn/Article/4313.shtml
- http://m.mobile.puhvjy.cn/Article/7151.shtml
- http://m.mobile.nwbbyt.cn/Article/584760.shtml
- http://m.mobile.jnjpgf.cn/Article/8982528.shtml
- http://m.mobile.cmcvrr.cn/Article/6455604.shtml
- http://m.mobile.nwbbyt.cn/Article/7671.shtml
- http://m.mobile.nwbbyt.cn/Article/93633.shtml
- http://m.mobile.puhvjy.cn/Article/0633644.shtml
- http://m.mobile.jnjpgf.cn/Article/0203199.shtml
- http://m.mobile.cmcvrr.cn/Article/5000384.shtml
- http://m.mobile.jnjpgf.cn/Article/8703830.shtml
- http://m.mobile.nwbbyt.cn/Article/9902034.shtml
- http://m.mobile.cmcvrr.cn/Article/9708409.shtml
- http://m.mobile.cmcvrr.cn/Article/749137.shtml
- http://m.mobile.jnjpgf.cn/Article/8424742.shtml
- http://m.mobile.nwbbyt.cn/Article/50582.shtml
- http://m.mobile.cmcvrr.cn/Article/21562.shtml
- http://m.mobile.nwbbyt.cn/Article/5465.shtml
- http://m.mobile.jnjpgf.cn/Article/495759.shtml
- http://m.mobile.nwbbyt.cn/Article/512649.shtml
- http://m.mobile.puhvjy.cn/Article/4321110.shtml
- http://m.mobile.cmcvrr.cn/Article/6253.shtml
- http://m.mobile.jnjpgf.cn/Article/1262.shtml
- http://m.mobile.jnjpgf.cn/Article/6857.shtml
- http://m.mobile.puhvjy.cn/Article/0038677.shtml
- http://m.mobile.cmcvrr.cn/Article/462618.shtml
- http://m.mobile.puhvjy.cn/Article/3024081.shtml
- http://m.mobile.puhvjy.cn/Article/3112636.shtml
- http://m.mobile.nwbbyt.cn/Article/7308440.shtml
- http://m.mobile.jnjpgf.cn/Article/9294.shtml
- http://m.mobile.jnjpgf.cn/Article/102634.shtml
- http://m.mobile.puhvjy.cn/Article/964194.shtml
- http://m.mobile.nwbbyt.cn/Article/6372.shtml
- http://m.mobile.nwbbyt.cn/Article/61008.shtml
- http://m.mobile.jnjpgf.cn/Article/195250.shtml
- http://m.mobile.cmcvrr.cn/Article/4246.shtml
- http://m.mobile.jnjpgf.cn/Article/1527041.shtml
- http://m.mobile.jnjpgf.cn/Article/62698.shtml
- http://m.mobile.nwbbyt.cn/Article/059243.shtml
- http://m.mobile.jnjpgf.cn/Article/25386.shtml
- http://m.mobile.nwbbyt.cn/Article/167341.shtml
- http://m.mobile.jnjpgf.cn/Article/0850.shtml
- http://m.mobile.cmcvrr.cn/Article/7313.shtml
- http://m.mobile.jnjpgf.cn/Article/232339.shtml
- http://m.mobile.cmcvrr.cn/Article/4608.shtml
- http://m.mobile.nwbbyt.cn/Article/843663.shtml
- http://m.mobile.jnjpgf.cn/Article/0469727.shtml
- http://m.mobile.nwbbyt.cn/Article/032241.shtml
- http://m.mobile.jnjpgf.cn/Article/6945.shtml
- http://m.mobile.jnjpgf.cn/Article/0827.shtml
- http://m.mobile.cmcvrr.cn/Article/809920.shtml
- http://m.mobile.jnjpgf.cn/Article/30235.shtml
- http://m.mobile.cmcvrr.cn/Article/84283.shtml
- http://m.mobile.puhvjy.cn/Article/3589599.shtml
- http://m.mobile.puhvjy.cn/Article/27794.shtml
- http://m.mobile.cmcvrr.cn/Article/3945.shtml
- http://m.mobile.nwbbyt.cn/Article/46841.shtml
- http://m.mobile.jnjpgf.cn/Article/113001.shtml
- http://m.mobile.puhvjy.cn/Article/700359.shtml
- http://m.mobile.jnjpgf.cn/Article/4909673.shtml
- http://m.mobile.nwbbyt.cn/Article/595948.shtml
- http://m.mobile.nwbbyt.cn/Article/8002245.shtml
- http://m.mobile.jnjpgf.cn/Article/1904.shtml
- http://m.mobile.puhvjy.cn/Article/633805.shtml
- http://m.mobile.puhvjy.cn/Article/6431.shtml
- http://m.mobile.cmcvrr.cn/Article/2174.shtml
- http://m.mobile.jnjpgf.cn/Article/7836.shtml
- http://m.mobile.jnjpgf.cn/Article/0094.shtml
- http://m.mobile.puhvjy.cn/Article/9660757.shtml
- http://m.mobile.puhvjy.cn/Article/9184799.shtml
- http://m.mobile.cmcvrr.cn/Article/3638803.shtml
- http://m.mobile.cmcvrr.cn/Article/36043.shtml
- http://m.mobile.nwbbyt.cn/Article/3372822.shtml
- http://m.mobile.jnjpgf.cn/Article/001100.shtml
- http://m.mobile.jnjpgf.cn/Article/1022.shtml
- http://m.mobile.nwbbyt.cn/Article/3862.shtml
- http://m.mobile.nwbbyt.cn/Article/31389.shtml
- http://m.mobile.puhvjy.cn/Article/52463.shtml
- http://m.mobile.nwbbyt.cn/Article/553594.shtml
- http://m.mobile.nwbbyt.cn/Article/793859.shtml
- http://m.mobile.puhvjy.cn/Article/2549942.shtml
- http://m.mobile.nwbbyt.cn/Article/8945.shtml
- http://m.mobile.jnjpgf.cn/Article/1091.shtml
- http://m.mobile.cmcvrr.cn/Article/0566958.shtml
- http://m.mobile.puhvjy.cn/Article/88524.shtml
- http://m.mobile.nwbbyt.cn/Article/2871.shtml
- http://m.mobile.nwbbyt.cn/Article/5020.shtml
- http://m.mobile.cmcvrr.cn/Article/6527028.shtml
- http://m.mobile.cmcvrr.cn/Article/20192.shtml
- http://m.mobile.cmcvrr.cn/Article/8404.shtml
- http://m.mobile.jnjpgf.cn/Article/4284.shtml
- http://m.mobile.jnjpgf.cn/Article/9584.shtml
- http://m.mobile.puhvjy.cn/Article/248663.shtml
- http://m.mobile.jnjpgf.cn/Article/8294327.shtml
- http://m.mobile.jnjpgf.cn/Article/7507.shtml
- http://m.mobile.puhvjy.cn/Article/8853.shtml
- http://m.mobile.nwbbyt.cn/Article/84202.shtml
- http://m.mobile.nwbbyt.cn/Article/7016919.shtml
- http://m.mobile.jnjpgf.cn/Article/3957.shtml
- http://m.mobile.cmcvrr.cn/Article/6357849.shtml
- http://m.mobile.jnjpgf.cn/Article/8014.shtml
- http://m.mobile.cmcvrr.cn/Article/1475698.shtml
- http://m.mobile.nwbbyt.cn/Article/7775804.shtml
- http://m.mobile.nwbbyt.cn/Article/260512.shtml
- http://m.mobile.puhvjy.cn/Article/893362.shtml
- http://m.mobile.cmcvrr.cn/Article/1109.shtml
- http://m.mobile.nwbbyt.cn/Article/5739.shtml
- http://m.mobile.nwbbyt.cn/Article/0715.shtml
- http://m.mobile.jnjpgf.cn/Article/6896.shtml
- http://m.mobile.puhvjy.cn/Article/3080933.shtml
- http://m.mobile.jnjpgf.cn/Article/7947.shtml
- http://m.mobile.cmcvrr.cn/Article/20156.shtml
- http://m.mobile.jnjpgf.cn/Article/0414.shtml
- http://m.mobile.jnjpgf.cn/Article/7995.shtml
- http://m.mobile.cmcvrr.cn/Article/1357.shtml
- http://m.mobile.cmcvrr.cn/Article/73990.shtml
- http://m.mobile.cmcvrr.cn/Article/9920.shtml
- http://m.mobile.puhvjy.cn/Article/72694.shtml
- http://m.mobile.nwbbyt.cn/Article/007867.shtml
- http://m.mobile.puhvjy.cn/Article/6242945.shtml
- http://m.mobile.puhvjy.cn/Article/104362.shtml
- http://m.mobile.cmcvrr.cn/Article/4517788.shtml
- http://m.mobile.puhvjy.cn/Article/804610.shtml
- http://m.mobile.nwbbyt.cn/Article/392800.shtml
- http://m.mobile.puhvjy.cn/Article/0562223.shtml
- http://m.mobile.puhvjy.cn/Article/383872.shtml
- http://m.mobile.jnjpgf.cn/Article/39156.shtml
- http://m.mobile.jnjpgf.cn/Article/9556282.shtml
- http://m.mobile.cmcvrr.cn/Article/513789.shtml
- http://m.mobile.puhvjy.cn/Article/796822.shtml
- http://m.mobile.jnjpgf.cn/Article/1511.shtml
- http://m.mobile.nwbbyt.cn/Article/3670284.shtml
- http://m.mobile.nwbbyt.cn/Article/423964.shtml
- http://m.mobile.jnjpgf.cn/Article/8071108.shtml
- http://m.mobile.puhvjy.cn/Article/88222.shtml
- http://m.mobile.cmcvrr.cn/Article/211181.shtml
- http://m.mobile.jnjpgf.cn/Article/300914.shtml

## 项目结构

```
mobilelink-index/
├── index.js                  # 服务入口，初始化 HTTP 服务器与路由注册
├── package.json              # 项目元信息与依赖声明，包含启动脚本定义
├── config/
│   ├── default.yaml          # 默认配置参数，包含端口、巡检间隔与缓存策略
│   └── custom.yaml.example   # 用户自定义配置模板，可覆盖默认值
├── src/
│   ├── core/
│   │   ├── indexer.js        # 核心索引引擎，负责链接增删改查与内存缓存管理
│   │   └── validator.js      # URL 格式校验与域名白名单过滤逻辑
│   ├── health/
│   │   ├── checker.js        # 链接可访问性巡检任务调度器
│   │   └── reporter.js       # 巡检结果汇总与状态报告生成器
│   ├── api/
│   │   ├── routes.js         # RESTful 路由定义，挂载所有对外接口
│   │   └── handlers.js       # 请求处理函数，包含参数解析与响应构造
│   └── utils/
│       ├── logger.js         # 统一日志输出模块，支持多级别与文件落盘
│       └── cache.js          # 内存缓存封装，提供过期清理与命中统计
├── data/
│   ├── index.db.json         # 持久化索引数据文件，定期由内存同步落盘
│   └── health.log            # 巡检历史记录，按时间轮转存储
├── scripts/
│   ├── import.js             # 批量导入脚本，支持从 CSV/JSON 文件加载链接
│   └── export.js             # 导出工具，可输出索引目录为多种格式
├── docs/                     # 完整项目文档，涵盖使用教程与 API 规范
│   ├── quickstart.md
│   ├── link-management.md
│   ├── health-check.md
│   └── api-reference.md
└── test/
    ├── unit/                 # 单元测试用例，覆盖索引引擎与校验逻辑
    └── integration/          # 集成测试，模拟完整请求-响应流程
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并 Clone 到本地开发环境中，确保基于 main 分支创建新的功能分支（feature/xxx 或 fix/xxx）。
2. 安装项目依赖后，运行 `npm run test` 执行现有测试用例，确认当前环境通过所有测试。
3. 完成代码修改后，需补充对应的单元测试或集成测试，确保新增功能或修复的代码覆盖率不低于 80%。
4. 更新相关文档，包括但不限于 README、API 参考文档以及配置说明，确保文档描述与实际行为一致。
5. 提交 Pull Request 到主仓库的 develop 分支，并在 PR 描述中清晰说明变更目的、实现思路以及测试验证情况。

## 常见问题

**Q：服务启动后，无法访问任何链接资源，返回空列表是什么原因？**

A：首次启动时，索引缓存为空，需要手动导入初始链接数据。请执行 `npm run import -- --source=data/seed.json` 加载示例数据，或通过 `/link/add` 接口逐条添加链接。此外请确认 `config/default.yaml` 中的 `storage.filePath` 指向正确的数据文件路径。

**Q：链接巡检功能总是超时，报告大量失败状态，如何解决？**

A：建议调整 `config/default.yaml` 中的 `health.timeout` 参数，将该值从默认的 3000 毫秒适当增加至 8000 或 10000 毫秒。同时检查运行环境的网络出口是否存在防火墙限制，确保对目标域名的出方向请求未被拦截。

**Q：索引数据丢失或异常，如何从备份恢复？**

A：项目在每次成功导入或删除链接时，会自动在 `data/backups/` 目录下生成带时间戳的 JSON 备份文件。您可以将对应时间点的备份文件复制并重命名为 `data/index.db.json`，随后重启服务即可加载该备份数据。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
