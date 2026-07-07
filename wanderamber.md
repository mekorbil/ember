# Mobile Article Resource Aggregator

Mobile Article Resource Aggregator（MARA）是一个面向移动端技术内容聚合与分发场景的开源资源导航系统。该项目定位于帮助开发者、技术内容运营者以及移动端产品团队快速定位分散在多个域名下的高质量技术文章与案例资源。MARA 本身不生产内容，而是通过结构化的资源索引机制，将来自不同移动端垂直站点的文章链接纳入统一的管理视图，解决资源碎片化、检索效率低、域名频繁变动导致的书签失效等问题。

本项目适用于需要定期跟进移动端技术动态、收集竞品案例、维护内部知识库的团队或个人。MARA 提供基于纯静态页面的资源列表呈现方式，无需后端服务即可运行，支持本地预览与一键部署到各类静态托管平台。

## 功能概览

**多源资源聚合** 支持将来自不同域名的移动端文章链接统一采集与归类，当前已覆盖多个垂直技术站点。

**结构化列表展示** 所有资源以清晰列表形式呈现，每条记录包含文章标题、所属域名、收录时间等元信息，便于快速浏览。

**按批次索引** 资源按批次组织，每批次包含固定数量的链接，本项目为第 34/80 批，共收录 250 条移动端文章链接。

**纯静态零依赖** 项目完全由 HTML 和 Markdown 构成，无需安装任何后端框架或数据库，开箱即用。

**快速检索支持** 内置简单的前端过滤功能，允许用户按域名关键词或文章 ID 快速定位目标资源。

**一键导出机制** 支持将当前批次资源列表导出为 CSV 或 JSON 格式，方便导入其他数据处理工具。

**移动端适配** 页面布局针对手机与平板设备进行优化，在移动端浏览器中拥有良好的阅读与操作体验。

**版本化记录** 每一批次资源均附带生成时间与版本号，便于追踪资源集合的变更历史。

## 应用场景

移动端技术团队的知识库建设。技术团队可将 MARA 作为内部知识库的数据采集前端，定期收录行业相关的技术文章链接，形成可持续积累的文档资源池。团队成员可通过统一入口访问经筛选的优质内容，减少重复搜索成本。

个人开发者的技术阅读清单管理。个人开发者可使用 MARA 维护自己的技术阅读清单，将散落在各技术社区、博客站点的有用文章通过本项目集中管理，避免浏览器书签杂乱无章。

技术内容运营的数据采集辅助。内容运营人员可利用 MARA 的结构化列表快速收集竞品站点或行业标杆的更新动态，按批次整理后用于周报、月报的材料汇编，提升信息整合效率。

开源项目文档的外部参考索引。开源项目维护者可将 MARA 嵌入项目文档站点，作为外部参考资料章节的补充，为使用者提供与项目技术栈相关的扩展阅读资源。

## 快速开始

以下命令将完整克隆项目仓库、安装必要工具依赖并启动本地预览服务。

```bash
git clone https://github.com/example/mobile-resource-aggregator.git
cd mobile-resource-aggregator
npm install -g markdown-server
md-server --port 8080
```

执行上述命令后，在浏览器中访问 http://localhost:8080 即可查看资源列表页面。若需要生成静态 HTML 文件，可运行 `npm run build`，输出目录为 `./dist`。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >= 14.0.0 | 用于运行本地开发服务器及构建脚本 |
| npm | >= 6.0.0 | 包管理器，用于安装项目工具链依赖 |
| markdown-server | >= 2.1.0 | 轻量级 Markdown 预览服务，用于本地调试 |
| git | >= 2.20.0 | 版本控制工具，用于克隆仓库及管理变更 |
| 现代网页浏览器 | Chrome 90+ / Firefox 88+ / Safari 14+ | 用于预览渲染后的资源列表页面 |
| 操作系统 | Windows 10 / macOS 11+ / Linux 内核 4.0+ | 项目运行环境，无特殊系统依赖 |
| 网络连接 | 稳定宽带 | 用于克隆仓库及可选的在线资源校验功能 |
| 磁盘空间 | 至少 50 MB | 存放源码、资源列表及构建产物 |
| Python（可选） | >= 3.6 | 若使用内置的链接可用性检查脚本则需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何浏览、筛选和导出资源列表；页面布局与操作说明 |
| 维护指南 | /docs/maintainer-guide.md | 如何新增资源批次、更新现有链接、处理失效 URL |
| 开发参考 | /docs/developer-guide.md | 项目目录结构说明、样式定制方法、脚本扩展接口 |
| 部署说明 | /docs/deployment.md | 如何将项目部署到 Vercel、Netlify、GitHub Pages 等平台 |
| 资源规范 | /docs/resource-spec.md | 资源链接的收录标准、字段定义、批次编号规则 |

## 资源列表

- http://www.mobile.puhvjy.cn/Article/1197848.shtml
- http://www.mobile.jnjpgf.cn/Article/61588.shtml
- http://www.mobile.jnjpgf.cn/Article/3940230.shtml
- http://www.mobile.cmcvrr.cn/Article/5742990.shtml
- http://www.mobile.nwbbyt.cn/Article/2936335.shtml
- http://www.mobile.cmcvrr.cn/Article/21213.shtml
- http://www.mobile.cmcvrr.cn/Article/12378.shtml
- http://www.mobile.puhvjy.cn/Article/2551293.shtml
- http://www.mobile.jnjpgf.cn/Article/5507408.shtml
- http://www.mobile.nwbbyt.cn/Article/97398.shtml
- http://www.mobile.nwbbyt.cn/Article/6784.shtml
- http://www.mobile.jnjpgf.cn/Article/0183.shtml
- http://www.mobile.cmcvrr.cn/Article/221398.shtml
- http://www.mobile.jnjpgf.cn/Article/66703.shtml
- http://www.mobile.puhvjy.cn/Article/88856.shtml
- http://www.mobile.nwbbyt.cn/Article/49228.shtml
- http://www.mobile.puhvjy.cn/Article/9458.shtml
- http://www.mobile.puhvjy.cn/Article/792613.shtml
- http://www.mobile.puhvjy.cn/Article/325896.shtml
- http://www.mobile.puhvjy.cn/Article/11177.shtml
- http://www.mobile.jnjpgf.cn/Article/8713.shtml
- http://www.mobile.cmcvrr.cn/Article/308712.shtml
- http://www.mobile.cmcvrr.cn/Article/3827408.shtml
- http://www.mobile.nwbbyt.cn/Article/948059.shtml
- http://www.mobile.puhvjy.cn/Article/7566.shtml
- http://www.mobile.jnjpgf.cn/Article/4812628.shtml
- http://www.mobile.puhvjy.cn/Article/35979.shtml
- http://www.mobile.puhvjy.cn/Article/9887654.shtml
- http://www.mobile.cmcvrr.cn/Article/640756.shtml
- http://www.mobile.jnjpgf.cn/Article/2453.shtml
- http://www.mobile.nwbbyt.cn/Article/5935807.shtml
- http://www.mobile.puhvjy.cn/Article/8563.shtml
- http://www.mobile.jnjpgf.cn/Article/1668516.shtml
- http://www.mobile.cmcvrr.cn/Article/0468.shtml
- http://www.mobile.nwbbyt.cn/Article/635824.shtml
- http://www.mobile.puhvjy.cn/Article/0832908.shtml
- http://www.mobile.cmcvrr.cn/Article/53928.shtml
- http://www.mobile.jnjpgf.cn/Article/01774.shtml
- http://www.mobile.cmcvrr.cn/Article/4683.shtml
- http://www.mobile.nwbbyt.cn/Article/304145.shtml
- http://www.mobile.cmcvrr.cn/Article/0652595.shtml
- http://www.mobile.nwbbyt.cn/Article/387442.shtml
- http://www.mobile.puhvjy.cn/Article/0947.shtml
- http://www.mobile.cmcvrr.cn/Article/1101100.shtml
- http://www.mobile.puhvjy.cn/Article/5973.shtml
- http://www.mobile.puhvjy.cn/Article/39446.shtml
- http://www.mobile.puhvjy.cn/Article/0161.shtml
- http://www.mobile.jnjpgf.cn/Article/57951.shtml
- http://www.mobile.nwbbyt.cn/Article/270913.shtml
- http://www.mobile.nwbbyt.cn/Article/8404.shtml
- http://www.mobile.nwbbyt.cn/Article/94812.shtml
- http://www.mobile.nwbbyt.cn/Article/236685.shtml
- http://www.mobile.puhvjy.cn/Article/8076410.shtml
- http://www.mobile.jnjpgf.cn/Article/56445.shtml
- http://www.mobile.jnjpgf.cn/Article/1264.shtml
- http://www.mobile.nwbbyt.cn/Article/0458127.shtml
- http://www.mobile.puhvjy.cn/Article/71443.shtml
- http://www.mobile.cmcvrr.cn/Article/515576.shtml
- http://www.mobile.cmcvrr.cn/Article/6520533.shtml
- http://www.mobile.jnjpgf.cn/Article/840163.shtml
- http://www.mobile.nwbbyt.cn/Article/95431.shtml
- http://www.mobile.jnjpgf.cn/Article/5063696.shtml
- http://www.mobile.puhvjy.cn/Article/339523.shtml
- http://www.mobile.nwbbyt.cn/Article/042719.shtml
- http://www.mobile.jnjpgf.cn/Article/4693.shtml
- http://www.mobile.nwbbyt.cn/Article/495995.shtml
- http://www.mobile.puhvjy.cn/Article/078133.shtml
- http://www.mobile.nwbbyt.cn/Article/6611.shtml
- http://www.mobile.nwbbyt.cn/Article/1640774.shtml
- http://www.mobile.nwbbyt.cn/Article/373700.shtml
- http://www.mobile.nwbbyt.cn/Article/6386.shtml
- http://www.mobile.cmcvrr.cn/Article/71770.shtml
- http://www.mobile.nwbbyt.cn/Article/0958764.shtml
- http://www.mobile.cmcvrr.cn/Article/3030534.shtml
- http://www.mobile.jnjpgf.cn/Article/06170.shtml
- http://www.mobile.puhvjy.cn/Article/6440.shtml
- http://www.mobile.cmcvrr.cn/Article/4985982.shtml
- http://www.mobile.cmcvrr.cn/Article/808257.shtml
- http://www.mobile.nwbbyt.cn/Article/379119.shtml
- http://www.mobile.puhvjy.cn/Article/42615.shtml
- http://www.mobile.nwbbyt.cn/Article/6226310.shtml
- http://www.mobile.nwbbyt.cn/Article/6799.shtml
- http://www.mobile.cmcvrr.cn/Article/60323.shtml
- http://www.mobile.jnjpgf.cn/Article/1119008.shtml
- http://www.mobile.puhvjy.cn/Article/8585005.shtml
- http://www.mobile.puhvjy.cn/Article/4456114.shtml
- http://www.mobile.puhvjy.cn/Article/957329.shtml
- http://www.mobile.cmcvrr.cn/Article/105827.shtml
- http://www.mobile.cmcvrr.cn/Article/66854.shtml
- http://www.mobile.cmcvrr.cn/Article/6767588.shtml
- http://www.mobile.puhvjy.cn/Article/7231827.shtml
- http://www.mobile.jnjpgf.cn/Article/99157.shtml
- http://www.mobile.jnjpgf.cn/Article/26470.shtml
- http://www.mobile.nwbbyt.cn/Article/5504.shtml
- http://www.mobile.nwbbyt.cn/Article/19533.shtml
- http://www.mobile.puhvjy.cn/Article/5420.shtml
- http://www.mobile.cmcvrr.cn/Article/96382.shtml
- http://www.mobile.cmcvrr.cn/Article/85209.shtml
- http://www.mobile.nwbbyt.cn/Article/890482.shtml
- http://www.mobile.jnjpgf.cn/Article/5569325.shtml
- http://www.mobile.jnjpgf.cn/Article/63859.shtml
- http://www.mobile.puhvjy.cn/Article/491025.shtml
- http://www.mobile.jnjpgf.cn/Article/4997.shtml
- http://www.mobile.puhvjy.cn/Article/7827.shtml
- http://www.mobile.puhvjy.cn/Article/8875.shtml
- http://www.mobile.cmcvrr.cn/Article/039617.shtml
- http://www.mobile.cmcvrr.cn/Article/8415902.shtml
- http://www.mobile.jnjpgf.cn/Article/2448644.shtml
- http://www.mobile.nwbbyt.cn/Article/653741.shtml
- http://www.mobile.jnjpgf.cn/Article/7621.shtml
- http://www.mobile.puhvjy.cn/Article/334578.shtml
- http://www.mobile.jnjpgf.cn/Article/616187.shtml
- http://www.mobile.nwbbyt.cn/Article/083987.shtml
- http://www.mobile.nwbbyt.cn/Article/11427.shtml
- http://www.mobile.nwbbyt.cn/Article/61320.shtml
- http://www.mobile.nwbbyt.cn/Article/6732.shtml
- http://www.mobile.puhvjy.cn/Article/128247.shtml
- http://www.mobile.cmcvrr.cn/Article/21953.shtml
- http://www.mobile.cmcvrr.cn/Article/754442.shtml
- http://www.mobile.jnjpgf.cn/Article/1697670.shtml
- http://www.mobile.nwbbyt.cn/Article/61102.shtml
- http://www.mobile.cmcvrr.cn/Article/497363.shtml
- http://www.mobile.nwbbyt.cn/Article/94809.shtml
- http://www.mobile.nwbbyt.cn/Article/57072.shtml
- http://www.mobile.puhvjy.cn/Article/5331392.shtml
- http://www.mobile.jnjpgf.cn/Article/98687.shtml
- http://www.mobile.jnjpgf.cn/Article/1596058.shtml
- http://www.mobile.jnjpgf.cn/Article/621985.shtml
- http://www.mobile.cmcvrr.cn/Article/63844.shtml
- http://www.mobile.cmcvrr.cn/Article/56245.shtml
- http://www.mobile.cmcvrr.cn/Article/60695.shtml
- http://www.mobile.nwbbyt.cn/Article/818705.shtml
- http://www.mobile.puhvjy.cn/Article/916920.shtml
- http://www.mobile.puhvjy.cn/Article/5047742.shtml
- http://www.mobile.jnjpgf.cn/Article/5621935.shtml
- http://www.mobile.cmcvrr.cn/Article/9970490.shtml
- http://www.mobile.jnjpgf.cn/Article/289151.shtml
- http://www.mobile.cmcvrr.cn/Article/32032.shtml
- http://www.mobile.jnjpgf.cn/Article/6756.shtml
- http://www.mobile.cmcvrr.cn/Article/52302.shtml
- http://www.mobile.cmcvrr.cn/Article/4458174.shtml
- http://www.mobile.puhvjy.cn/Article/010486.shtml
- http://www.mobile.jnjpgf.cn/Article/3119559.shtml
- http://www.mobile.jnjpgf.cn/Article/6959926.shtml
- http://www.mobile.nwbbyt.cn/Article/073989.shtml
- http://www.mobile.cmcvrr.cn/Article/927186.shtml
- http://www.mobile.cmcvrr.cn/Article/1486.shtml
- http://www.mobile.puhvjy.cn/Article/38918.shtml
- http://www.mobile.cmcvrr.cn/Article/5808310.shtml
- http://www.mobile.puhvjy.cn/Article/8150752.shtml
- http://www.mobile.puhvjy.cn/Article/7531.shtml
- http://www.mobile.nwbbyt.cn/Article/0295.shtml
- http://www.mobile.puhvjy.cn/Article/1810.shtml
- http://www.mobile.jnjpgf.cn/Article/7567950.shtml
- http://www.mobile.nwbbyt.cn/Article/1084.shtml
- http://www.mobile.nwbbyt.cn/Article/8015.shtml
- http://www.mobile.cmcvrr.cn/Article/0474692.shtml
- http://www.mobile.jnjpgf.cn/Article/158640.shtml
- http://www.mobile.cmcvrr.cn/Article/9262939.shtml
- http://www.mobile.cmcvrr.cn/Article/3387773.shtml
- http://www.mobile.puhvjy.cn/Article/80212.shtml
- http://www.mobile.puhvjy.cn/Article/15558.shtml
- http://www.mobile.nwbbyt.cn/Article/5465947.shtml
- http://www.mobile.nwbbyt.cn/Article/27793.shtml
- http://www.mobile.cmcvrr.cn/Article/307916.shtml
- http://www.mobile.nwbbyt.cn/Article/162038.shtml
- http://www.mobile.puhvjy.cn/Article/739668.shtml
- http://www.mobile.puhvjy.cn/Article/3162191.shtml
- http://www.mobile.puhvjy.cn/Article/55907.shtml
- http://www.mobile.cmcvrr.cn/Article/2107292.shtml
- http://www.mobile.nwbbyt.cn/Article/2802816.shtml
- http://www.mobile.puhvjy.cn/Article/8808.shtml
- http://www.mobile.puhvjy.cn/Article/912708.shtml
- http://www.mobile.jnjpgf.cn/Article/9641.shtml
- http://www.mobile.jnjpgf.cn/Article/457743.shtml
- http://www.mobile.nwbbyt.cn/Article/1482.shtml
- http://www.mobile.cmcvrr.cn/Article/7535058.shtml
- http://www.mobile.puhvjy.cn/Article/950261.shtml
- http://www.mobile.nwbbyt.cn/Article/804446.shtml
- http://www.mobile.nwbbyt.cn/Article/8553.shtml
- http://www.mobile.cmcvrr.cn/Article/9654679.shtml
- http://www.mobile.cmcvrr.cn/Article/616172.shtml
- http://www.mobile.cmcvrr.cn/Article/8593.shtml
- http://www.mobile.nwbbyt.cn/Article/176216.shtml
- http://www.mobile.jnjpgf.cn/Article/3137.shtml
- http://www.mobile.cmcvrr.cn/Article/617787.shtml
- http://www.mobile.jnjpgf.cn/Article/190650.shtml
- http://www.mobile.jnjpgf.cn/Article/9327819.shtml
- http://www.mobile.jnjpgf.cn/Article/2598069.shtml
- http://www.mobile.puhvjy.cn/Article/96433.shtml
- http://www.mobile.jnjpgf.cn/Article/363042.shtml
- http://www.mobile.nwbbyt.cn/Article/382230.shtml
- http://www.mobile.puhvjy.cn/Article/594128.shtml
- http://www.mobile.puhvjy.cn/Article/5894.shtml
- http://www.mobile.puhvjy.cn/Article/76013.shtml
- http://www.mobile.puhvjy.cn/Article/29362.shtml
- http://www.mobile.jnjpgf.cn/Article/4908.shtml
- http://www.mobile.puhvjy.cn/Article/4577.shtml
- http://www.mobile.cmcvrr.cn/Article/4651971.shtml
- http://www.mobile.nwbbyt.cn/Article/98988.shtml
- http://www.mobile.cmcvrr.cn/Article/9302.shtml
- http://www.mobile.jnjpgf.cn/Article/21215.shtml
- http://www.mobile.puhvjy.cn/Article/4721.shtml
- http://www.mobile.cmcvrr.cn/Article/624349.shtml
- http://www.mobile.puhvjy.cn/Article/0694.shtml
- http://www.mobile.cmcvrr.cn/Article/799740.shtml
- http://www.mobile.nwbbyt.cn/Article/3565584.shtml
- http://www.mobile.nwbbyt.cn/Article/243840.shtml
- http://www.mobile.nwbbyt.cn/Article/933114.shtml
- http://www.mobile.cmcvrr.cn/Article/21814.shtml
- http://www.mobile.puhvjy.cn/Article/4449.shtml
- http://www.mobile.cmcvrr.cn/Article/1451.shtml
- http://www.mobile.jnjpgf.cn/Article/2917.shtml
- http://www.mobile.cmcvrr.cn/Article/3682.shtml
- http://www.mobile.cmcvrr.cn/Article/879099.shtml
- http://www.mobile.nwbbyt.cn/Article/1339.shtml
- http://www.mobile.jnjpgf.cn/Article/8657884.shtml
- http://www.mobile.nwbbyt.cn/Article/5546277.shtml
- http://www.mobile.jnjpgf.cn/Article/1051981.shtml
- http://www.mobile.jnjpgf.cn/Article/873664.shtml
- http://www.mobile.nwbbyt.cn/Article/59702.shtml
- http://www.mobile.nwbbyt.cn/Article/8666057.shtml
- http://www.mobile.puhvjy.cn/Article/4380.shtml
- http://www.mobile.jnjpgf.cn/Article/381565.shtml
- http://www.mobile.jnjpgf.cn/Article/30549.shtml
- http://www.mobile.jnjpgf.cn/Article/6522759.shtml
- http://www.mobile.puhvjy.cn/Article/567715.shtml
- http://www.mobile.jnjpgf.cn/Article/0590.shtml
- http://www.mobile.jnjpgf.cn/Article/4957.shtml
- http://www.mobile.puhvjy.cn/Article/397873.shtml
- http://www.mobile.jnjpgf.cn/Article/072825.shtml
- http://www.mobile.nwbbyt.cn/Article/7037.shtml
- http://www.mobile.jnjpgf.cn/Article/862423.shtml
- http://www.mobile.cmcvrr.cn/Article/2972531.shtml
- http://www.mobile.jnjpgf.cn/Article/073570.shtml
- http://www.mobile.cmcvrr.cn/Article/3845.shtml
- http://www.mobile.puhvjy.cn/Article/52996.shtml
- http://www.mobile.nwbbyt.cn/Article/42301.shtml
- http://www.mobile.puhvjy.cn/Article/1025.shtml
- http://www.mobile.cmcvrr.cn/Article/8365.shtml
- http://www.mobile.nwbbyt.cn/Article/4879904.shtml
- http://www.mobile.cmcvrr.cn/Article/7974672.shtml
- http://www.mobile.cmcvrr.cn/Article/072776.shtml
- http://www.mobile.nwbbyt.cn/Article/1378661.shtml
- http://www.mobile.nwbbyt.cn/Article/08645.shtml
- http://www.mobile.jnjpgf.cn/Article/440496.shtml
- http://www.mobile.cmcvrr.cn/Article/7708.shtml
- http://www.mobile.puhvjy.cn/Article/5103.shtml
- http://www.mobile.cmcvrr.cn/Article/5440264.shtml
- http://www.mobile.nwbbyt.cn/Article/2372.shtml

## 项目结构

```
mobile-resource-aggregator/
├── index.md                         # 主入口文件，展示当前批次资源列表
├── README.md                        # 项目说明文档（本文件）
├── config/
│   ├── batch.yaml                   # 批次配置文件，定义当前批次号与总批次数
│   └── domains.yaml                 # 域名白名单配置，用于资源链接校验
├── scripts/
│   ├── fetch-resources.js           # 资源采集脚本，用于从各源拉取最新链接
│   ├── validate-urls.py             # 链接可用性校验脚本（Python）
│   └── export-csv.js                # 导出 CSV 格式数据的工具脚本
├── docs/
│   ├── user-guide.md                # 用户手册，包含浏览与筛选操作说明
│   ├── maintainer-guide.md          # 维护者指南，介绍如何更新和管理资源
│   ├── developer-guide.md           # 开发者参考，说明扩展与定制方法
│   ├── deployment.md                # 部署指南，涵盖各主流静态托管平台
│   └── resource-spec.md             # 资源收录规范，定义链接字段与批次规则
├── templates/
│   ├── list-template.html           # 资源列表页的 HTML 模板
│   └── detail-template.html         # 单条资源详情页的 HTML 模板
├── assets/
│   ├── css/
│   │   └── main.css                 # 全局样式表，含移动端适配规则
│   └── js/
│       ├── filter.js                # 前端过滤与搜索逻辑
│       └── export.js                # 前端导出功能脚本
├── output/
│   ├── index.html                   # 构建生成的静态首页
│   └── batch-34.json                # 当前批次资源的 JSON 格式数据
├── tests/
│   ├── test-validator.js            # 链接校验模块的单元测试
│   └── test-exporter.js             # 导出功能的单元测试
├── .gitignore                       # Git 忽略规则，排除 node_modules 与 output
├── package.json                     # npm 项目配置，定义依赖与脚本命令
└── LICENSE                          # MIT 许可证文件
```

## 贡献指南

1. 复刻项目仓库至个人账号，在本地克隆复刻后的副本，并创建新的功能分支。分支命名建议采用 `feat/batch-update` 或 `fix/link-validation` 格式，以清晰区分变更类型。

2. 按照 /docs/resource-spec.md 中定义的资源收录规范，编辑 `config/batch.yaml` 文件以新增或更新资源链接。确保新增链接符合域名白名单要求，且文章 ID 未与历史批次重复。

3. 在本地运行链接可用性校验脚本 `python scripts/validate-urls.py`，检查所有新增或变更的链接是否可正常访问。对于返回 4xx 或 5xx 状态码的链接，需进行二次确认或替换为有效地址。

4. 提交变更并推送到远程分支，随后在 GitHub 上发起 Pull Request。请在 PR 描述中注明本次变更涉及的批次号、新增链接数量以及校验结果摘要，便于维护者审阅。

5. 等待项目维护者的代码审查与合并。合并完成后，CI 流水线将自动重新构建静态页面并更新部署站点，无需手动操作。

## 常见问题

Q: 资源列表中的链接出现访问失败或页面不存在的情况，应如何处理？

A: 请首先确认网络环境是否能够正常访问该域名。若域名可解析但页面返回 404 或 500 错误，说明原始文章可能已被移除或迁移。您可以在项目 Issues 中提交链接失效报告，或自行按照贡献指南提交 PR 移除失效链接并补充替代资源。

Q: 如何新增一个完整的资源批次，而不只是修改当前批次？

A: 新增批次需要先在 `config/batch.yaml` 中递增批次号（如从 34 改为 35），并重置总批次数为实际值。随后在 `output/` 目录下创建对应的 JSON 数据文件，并更新 `index.md` 中的列表内容。建议使用 `scripts/fetch-resources.js` 脚本辅助完成批量采集，避免手动录入错误。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
