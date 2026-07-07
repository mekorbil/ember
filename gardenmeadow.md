# Mobile Link Navigator

Mobile Link Navigator 是一个面向移动端内容聚合与导航的开源工具，旨在帮助开发者、内容运营人员以及终端用户高效地整理、分类和访问分散在移动域名下的各类文章资源。该项目通过结构化的数据采集、索引和展示机制，将大量原始链接转化为可检索、可浏览的知识导航体系。

项目主要解决移动端内容碎片化问题。在日常工作中，用户可能积累大量来自不同移动子域名的文章链接，这些链接缺乏统一管理，难以快速定位所需信息。Mobile Link Navigator 提供一套轻量级、可自部署的解决方案，支持链接导入、自动归类、全文检索和访问统计，适用于个人知识管理、团队资料库建设以及小型内容门户的快速搭建。

## 功能概览

批量链接导入与解析：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动提取文章标题、发布时间、来源域名等元数据。

智能分类与标签系统：基于 URL 路径特征和域名规则，对导入的链接进行自动分类，并允许用户自定义标签体系，实现多维度的内容组织。

全文检索与高级筛选：内置倒排索引，支持对文章标题和内容摘要进行快速全文检索，同时提供按域名、分类、时间范围等条件的高级筛选功能。

访问统计与热度分析：记录每个链接的点击次数和访问时间，生成热度排行和访问趋势图，帮助用户识别高价值内容。

响应式移动端界面：前端采用响应式设计，完美适配手机、平板和桌面设备，确保在各类屏幕尺寸下均能获得良好的浏览体验。

数据导入导出与备份：支持 JSON、CSV、Markdown 三种格式的数据导出，方便用户进行本地备份、迁移或与其他工具集成。

定时更新与健康检查：内置定时任务，可定期检测已收录链接的可访问性，自动标记失效链接，并生成健康报告。

用户权限与多账户支持：提供基于角色的访问控制，支持多用户协同管理，每位用户可拥有独立的收藏夹和标签体系。

## 应用场景

个人知识库构建：开发者或研究者可将日常积累的技术文章、行业报告等链接导入系统，通过分类和标签构建个人知识库，方便后续查阅和引用。

团队协作资料库：产品、运营或技术团队可将项目相关的设计文档、需求说明、技术方案等链接集中管理，实现团队内部信息的高效共享与协同维护。

内容门户快速搭建：中小型内容创作者或自媒体运营者可使用本系统快速生成一个简洁的内容导航站，将分散在各处的原创文章或推荐资源统一展示给受众。

企业内部知识导航：企业可将内部 Wiki、培训资料、规章制度等链接纳入系统，为员工提供一站式的内部信息检索入口，降低信息获取成本。

## 快速开始

以下命令演示了从克隆仓库到启动服务的完整流程，适用于 Linux 和 macOS 环境。Windows 用户建议使用 WSL 或 Git Bash。

```bash
# 克隆仓库
git clone https://github.com/your-org/mobile-link-navigator.git
cd mobile-link-navigator

# 安装依赖（使用 pip 和 npm）
pip install -r requirements.txt
npm install --prefix frontend

# 构建前端静态文件
npm run build --prefix frontend

# 初始化数据库
python scripts/init_db.py

# 启动开发服务器
python app.py
```

服务启动后，访问 http://localhost:5000 即可进入系统。首次访问将引导用户创建管理员账户。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 后端运行环境，建议使用 3.10 LTS 版本 |
| Node.js | 18.x 及以上 | 前端构建工具依赖，建议使用 18.17.0 LTS |
| SQLite | 3.35 及以上 | 默认内置数据库，无需额外安装；生产环境可切换至 PostgreSQL |
| Redis | 6.2 及以上 | 用于会话缓存和任务队列，生产环境必选 |
| Nginx | 1.22 及以上 | 生产环境推荐反向代理服务器，用于静态文件服务和负载均衡 |
| Git | 2.30 及以上 | 版本控制工具，用于代码克隆和更新 |
| make | 3.82 及以上 | 构建脚本工具，用于自动化任务执行 |
| gcc | 9.4 及以上 | 部分 Python 原生扩展编译所需（Linux 环境） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速部署并运行系统？如何进行初始配置？ |
| 数据管理 | docs/data-management.md | 如何导入链接、配置分类规则、执行数据清洗？ |
| 前端开发 | docs/frontend-dev.md | 前端技术栈是什么？如何自定义主题和页面布局？ |
| 运维部署 | docs/deployment.md | 生产环境如何配置 Nginx 和 Supervisor？如何进行性能调优？ |
| API 参考 | docs/api-reference.md | 后端提供了哪些 RESTful 接口？请求和响应格式是什么？ |
| 故障排查 | docs/troubleshooting.md | 常见错误码含义及解决办法？日志如何查看和分析？ |

## 资源列表

- http://m.mobile.jnjpgf.cn/Article/2343.shtml
- http://m.mobile.cmcvrr.cn/Article/2772.shtml
- http://m.mobile.puhvjy.cn/Article/17730.shtml
- http://m.mobile.cmcvrr.cn/Article/3465242.shtml
- http://m.mobile.puhvjy.cn/Article/5049419.shtml
- http://m.mobile.puhvjy.cn/Article/7671348.shtml
- http://m.mobile.puhvjy.cn/Article/51853.shtml
- http://m.mobile.cmcvrr.cn/Article/893513.shtml
- http://m.mobile.nwbbyt.cn/Article/27475.shtml
- http://m.mobile.cmcvrr.cn/Article/6700.shtml
- http://m.mobile.puhvjy.cn/Article/5704.shtml
- http://m.mobile.cmcvrr.cn/Article/438786.shtml
- http://m.mobile.cmcvrr.cn/Article/89339.shtml
- http://m.mobile.puhvjy.cn/Article/22712.shtml
- http://m.mobile.cmcvrr.cn/Article/72607.shtml
- http://m.mobile.nwbbyt.cn/Article/173529.shtml
- http://m.mobile.jnjpgf.cn/Article/10393.shtml
- http://m.mobile.cmcvrr.cn/Article/9422787.shtml
- http://m.mobile.cmcvrr.cn/Article/677924.shtml
- http://m.mobile.cmcvrr.cn/Article/6949.shtml
- http://m.mobile.puhvjy.cn/Article/3649.shtml
- http://m.mobile.cmcvrr.cn/Article/4567.shtml
- http://m.mobile.cmcvrr.cn/Article/7786.shtml
- http://m.mobile.cmcvrr.cn/Article/1155.shtml
- http://m.mobile.puhvjy.cn/Article/915465.shtml
- http://m.mobile.cmcvrr.cn/Article/43818.shtml
- http://m.mobile.cmcvrr.cn/Article/86903.shtml
- http://m.mobile.cmcvrr.cn/Article/7843.shtml
- http://m.mobile.jnjpgf.cn/Article/69031.shtml
- http://m.mobile.puhvjy.cn/Article/819224.shtml
- http://m.mobile.jnjpgf.cn/Article/612475.shtml
- http://m.mobile.cmcvrr.cn/Article/7672.shtml
- http://m.mobile.jnjpgf.cn/Article/77811.shtml
- http://m.mobile.puhvjy.cn/Article/6619977.shtml
- http://m.mobile.puhvjy.cn/Article/735541.shtml
- http://m.mobile.cmcvrr.cn/Article/4077.shtml
- http://m.mobile.nwbbyt.cn/Article/124854.shtml
- http://m.mobile.jnjpgf.cn/Article/405828.shtml
- http://m.mobile.jnjpgf.cn/Article/4829.shtml
- http://m.mobile.cmcvrr.cn/Article/428703.shtml
- http://m.mobile.puhvjy.cn/Article/889296.shtml
- http://m.mobile.jnjpgf.cn/Article/2408831.shtml
- http://m.mobile.cmcvrr.cn/Article/1152.shtml
- http://m.mobile.jnjpgf.cn/Article/526602.shtml
- http://m.mobile.cmcvrr.cn/Article/9011064.shtml
- http://m.mobile.jnjpgf.cn/Article/1217303.shtml
- http://m.mobile.jnjpgf.cn/Article/3619356.shtml
- http://m.mobile.nwbbyt.cn/Article/51206.shtml
- http://m.mobile.jnjpgf.cn/Article/1457353.shtml
- http://m.mobile.nwbbyt.cn/Article/600278.shtml
- http://m.mobile.jnjpgf.cn/Article/29471.shtml
- http://m.mobile.nwbbyt.cn/Article/49083.shtml
- http://m.mobile.nwbbyt.cn/Article/93181.shtml
- http://m.mobile.nwbbyt.cn/Article/8742.shtml
- http://m.mobile.jnjpgf.cn/Article/5617568.shtml
- http://m.mobile.nwbbyt.cn/Article/981025.shtml
- http://m.mobile.cmcvrr.cn/Article/9547.shtml
- http://m.mobile.cmcvrr.cn/Article/612472.shtml
- http://m.mobile.puhvjy.cn/Article/2698.shtml
- http://m.mobile.nwbbyt.cn/Article/584181.shtml
- http://m.mobile.nwbbyt.cn/Article/8454117.shtml
- http://m.mobile.jnjpgf.cn/Article/2359.shtml
- http://m.mobile.nwbbyt.cn/Article/5907.shtml
- http://m.mobile.cmcvrr.cn/Article/35530.shtml
- http://m.mobile.puhvjy.cn/Article/327060.shtml
- http://m.mobile.cmcvrr.cn/Article/2609.shtml
- http://m.mobile.puhvjy.cn/Article/7842.shtml
- http://m.mobile.puhvjy.cn/Article/8649.shtml
- http://m.mobile.jnjpgf.cn/Article/73489.shtml
- http://m.mobile.puhvjy.cn/Article/9393.shtml
- http://m.mobile.jnjpgf.cn/Article/08532.shtml
- http://m.mobile.jnjpgf.cn/Article/1546889.shtml
- http://m.mobile.puhvjy.cn/Article/425813.shtml
- http://m.mobile.jnjpgf.cn/Article/032053.shtml
- http://m.mobile.nwbbyt.cn/Article/0601.shtml
- http://m.mobile.jnjpgf.cn/Article/9370.shtml
- http://m.mobile.nwbbyt.cn/Article/9326239.shtml
- http://m.mobile.nwbbyt.cn/Article/575209.shtml
- http://m.mobile.nwbbyt.cn/Article/03261.shtml
- http://m.mobile.jnjpgf.cn/Article/68758.shtml
- http://m.mobile.nwbbyt.cn/Article/9520924.shtml
- http://m.mobile.puhvjy.cn/Article/3962547.shtml
- http://m.mobile.nwbbyt.cn/Article/240253.shtml
- http://m.mobile.cmcvrr.cn/Article/772348.shtml
- http://m.mobile.cmcvrr.cn/Article/9845322.shtml
- http://m.mobile.puhvjy.cn/Article/67914.shtml
- http://m.mobile.cmcvrr.cn/Article/25440.shtml
- http://m.mobile.jnjpgf.cn/Article/24376.shtml
- http://m.mobile.nwbbyt.cn/Article/730843.shtml
- http://m.mobile.puhvjy.cn/Article/144882.shtml
- http://m.mobile.jnjpgf.cn/Article/3078.shtml
- http://m.mobile.puhvjy.cn/Article/65850.shtml
- http://m.mobile.jnjpgf.cn/Article/14706.shtml
- http://m.mobile.nwbbyt.cn/Article/88992.shtml
- http://m.mobile.nwbbyt.cn/Article/03995.shtml
- http://m.mobile.puhvjy.cn/Article/634135.shtml
- http://m.mobile.puhvjy.cn/Article/71880.shtml
- http://m.mobile.puhvjy.cn/Article/1946.shtml
- http://m.mobile.nwbbyt.cn/Article/708062.shtml
- http://m.mobile.puhvjy.cn/Article/1451938.shtml
- http://m.mobile.cmcvrr.cn/Article/2031071.shtml
- http://m.mobile.jnjpgf.cn/Article/1324.shtml
- http://m.mobile.cmcvrr.cn/Article/335692.shtml
- http://m.mobile.puhvjy.cn/Article/27011.shtml
- http://m.mobile.puhvjy.cn/Article/2431557.shtml
- http://m.mobile.nwbbyt.cn/Article/466310.shtml
- http://m.mobile.jnjpgf.cn/Article/256384.shtml
- http://m.mobile.nwbbyt.cn/Article/8169.shtml
- http://m.mobile.jnjpgf.cn/Article/8718932.shtml
- http://m.mobile.nwbbyt.cn/Article/3717684.shtml
- http://m.mobile.puhvjy.cn/Article/9990.shtml
- http://m.mobile.cmcvrr.cn/Article/4788379.shtml
- http://m.mobile.nwbbyt.cn/Article/34645.shtml
- http://m.mobile.puhvjy.cn/Article/72738.shtml
- http://m.mobile.jnjpgf.cn/Article/93474.shtml
- http://m.mobile.puhvjy.cn/Article/2837646.shtml
- http://m.mobile.jnjpgf.cn/Article/074669.shtml
- http://m.mobile.puhvjy.cn/Article/5691923.shtml
- http://m.mobile.jnjpgf.cn/Article/301793.shtml
- http://m.mobile.puhvjy.cn/Article/0437555.shtml
- http://m.mobile.jnjpgf.cn/Article/651204.shtml
- http://m.mobile.nwbbyt.cn/Article/79864.shtml
- http://m.mobile.jnjpgf.cn/Article/3697264.shtml
- http://m.mobile.puhvjy.cn/Article/917155.shtml
- http://m.mobile.puhvjy.cn/Article/222109.shtml
- http://m.mobile.cmcvrr.cn/Article/546795.shtml
- http://m.mobile.puhvjy.cn/Article/73171.shtml
- http://m.mobile.jnjpgf.cn/Article/133803.shtml
- http://m.mobile.cmcvrr.cn/Article/9505.shtml
- http://m.mobile.nwbbyt.cn/Article/1802096.shtml
- http://m.mobile.cmcvrr.cn/Article/2112.shtml
- http://m.mobile.puhvjy.cn/Article/14231.shtml
- http://m.mobile.nwbbyt.cn/Article/20071.shtml
- http://m.mobile.nwbbyt.cn/Article/67933.shtml
- http://m.mobile.cmcvrr.cn/Article/96577.shtml
- http://m.mobile.nwbbyt.cn/Article/069969.shtml
- http://m.mobile.jnjpgf.cn/Article/4589.shtml
- http://m.mobile.jnjpgf.cn/Article/534262.shtml
- http://m.mobile.nwbbyt.cn/Article/172807.shtml
- http://m.mobile.nwbbyt.cn/Article/3000.shtml
- http://m.mobile.cmcvrr.cn/Article/776859.shtml
- http://m.mobile.nwbbyt.cn/Article/942039.shtml
- http://m.mobile.cmcvrr.cn/Article/6263.shtml
- http://m.mobile.nwbbyt.cn/Article/755642.shtml
- http://m.mobile.nwbbyt.cn/Article/7296087.shtml
- http://m.mobile.jnjpgf.cn/Article/067899.shtml
- http://m.mobile.cmcvrr.cn/Article/2608.shtml
- http://m.mobile.jnjpgf.cn/Article/811289.shtml
- http://m.mobile.jnjpgf.cn/Article/0988.shtml
- http://m.mobile.puhvjy.cn/Article/863507.shtml
- http://m.mobile.jnjpgf.cn/Article/8878.shtml
- http://m.mobile.jnjpgf.cn/Article/76704.shtml
- http://m.mobile.cmcvrr.cn/Article/4498.shtml
- http://m.mobile.nwbbyt.cn/Article/773100.shtml
- http://m.mobile.nwbbyt.cn/Article/644488.shtml
- http://m.mobile.cmcvrr.cn/Article/429025.shtml
- http://m.mobile.nwbbyt.cn/Article/9378468.shtml
- http://m.mobile.puhvjy.cn/Article/1829724.shtml
- http://m.mobile.puhvjy.cn/Article/6431677.shtml
- http://m.mobile.nwbbyt.cn/Article/6832149.shtml
- http://m.mobile.jnjpgf.cn/Article/6540326.shtml
- http://m.mobile.cmcvrr.cn/Article/1576.shtml
- http://m.mobile.jnjpgf.cn/Article/594094.shtml
- http://m.mobile.jnjpgf.cn/Article/8668425.shtml
- http://m.mobile.jnjpgf.cn/Article/5583.shtml
- http://m.mobile.puhvjy.cn/Article/17404.shtml
- http://m.mobile.jnjpgf.cn/Article/27308.shtml
- http://m.mobile.cmcvrr.cn/Article/454164.shtml
- http://m.mobile.puhvjy.cn/Article/205637.shtml
- http://m.mobile.nwbbyt.cn/Article/2628.shtml
- http://m.mobile.cmcvrr.cn/Article/906263.shtml
- http://m.mobile.jnjpgf.cn/Article/841001.shtml
- http://m.mobile.cmcvrr.cn/Article/55989.shtml
- http://m.mobile.jnjpgf.cn/Article/6548739.shtml
- http://m.mobile.cmcvrr.cn/Article/80690.shtml
- http://m.mobile.puhvjy.cn/Article/811467.shtml
- http://m.mobile.nwbbyt.cn/Article/256588.shtml
- http://m.mobile.puhvjy.cn/Article/08477.shtml
- http://m.mobile.jnjpgf.cn/Article/2383255.shtml
- http://m.mobile.nwbbyt.cn/Article/6878.shtml
- http://m.mobile.cmcvrr.cn/Article/98286.shtml
- http://m.mobile.jnjpgf.cn/Article/6465.shtml
- http://m.mobile.nwbbyt.cn/Article/996930.shtml
- http://m.mobile.jnjpgf.cn/Article/66726.shtml
- http://m.mobile.nwbbyt.cn/Article/7383.shtml
- http://m.mobile.cmcvrr.cn/Article/50082.shtml
- http://m.mobile.jnjpgf.cn/Article/2224023.shtml
- http://m.mobile.nwbbyt.cn/Article/9079817.shtml
- http://m.mobile.cmcvrr.cn/Article/1941703.shtml
- http://m.mobile.nwbbyt.cn/Article/4969.shtml
- http://m.mobile.cmcvrr.cn/Article/647844.shtml
- http://m.mobile.puhvjy.cn/Article/987431.shtml
- http://m.mobile.jnjpgf.cn/Article/49184.shtml
- http://m.mobile.puhvjy.cn/Article/788628.shtml
- http://m.mobile.jnjpgf.cn/Article/4481983.shtml
- http://m.mobile.jnjpgf.cn/Article/1674.shtml
- http://m.mobile.puhvjy.cn/Article/9774331.shtml
- http://m.mobile.cmcvrr.cn/Article/7289338.shtml
- http://m.mobile.cmcvrr.cn/Article/717225.shtml
- http://m.mobile.nwbbyt.cn/Article/97721.shtml
- http://m.mobile.cmcvrr.cn/Article/135527.shtml
- http://m.mobile.puhvjy.cn/Article/1199.shtml
- http://m.mobile.nwbbyt.cn/Article/02213.shtml
- http://m.mobile.cmcvrr.cn/Article/7005406.shtml
- http://m.mobile.cmcvrr.cn/Article/296666.shtml
- http://m.mobile.jnjpgf.cn/Article/5108.shtml
- http://m.mobile.jnjpgf.cn/Article/080241.shtml
- http://m.mobile.nwbbyt.cn/Article/398924.shtml
- http://m.mobile.jnjpgf.cn/Article/2275.shtml
- http://m.mobile.nwbbyt.cn/Article/8330388.shtml
- http://m.mobile.puhvjy.cn/Article/3996279.shtml
- http://m.mobile.nwbbyt.cn/Article/408174.shtml
- http://m.mobile.jnjpgf.cn/Article/866931.shtml
- http://m.mobile.puhvjy.cn/Article/5286261.shtml
- http://m.mobile.nwbbyt.cn/Article/6882.shtml
- http://m.mobile.nwbbyt.cn/Article/5541.shtml
- http://m.mobile.nwbbyt.cn/Article/880813.shtml
- http://m.mobile.puhvjy.cn/Article/74753.shtml
- http://m.mobile.nwbbyt.cn/Article/7442585.shtml
- http://m.mobile.puhvjy.cn/Article/47027.shtml
- http://m.mobile.nwbbyt.cn/Article/768617.shtml
- http://m.mobile.nwbbyt.cn/Article/9688.shtml
- http://m.mobile.nwbbyt.cn/Article/135502.shtml
- http://m.mobile.puhvjy.cn/Article/27718.shtml
- http://m.mobile.cmcvrr.cn/Article/8753015.shtml
- http://m.mobile.puhvjy.cn/Article/865454.shtml
- http://m.mobile.jnjpgf.cn/Article/4043.shtml
- http://m.mobile.jnjpgf.cn/Article/3395040.shtml
- http://m.mobile.cmcvrr.cn/Article/826306.shtml
- http://m.mobile.puhvjy.cn/Article/7284.shtml
- http://m.mobile.puhvjy.cn/Article/33254.shtml
- http://m.mobile.puhvjy.cn/Article/1898083.shtml
- http://m.mobile.nwbbyt.cn/Article/215736.shtml
- http://m.mobile.cmcvrr.cn/Article/9448615.shtml
- http://m.mobile.jnjpgf.cn/Article/922200.shtml
- http://m.mobile.nwbbyt.cn/Article/9088.shtml
- http://m.mobile.puhvjy.cn/Article/04768.shtml
- http://m.mobile.nwbbyt.cn/Article/4705419.shtml
- http://m.mobile.cmcvrr.cn/Article/77792.shtml
- http://m.mobile.jnjpgf.cn/Article/570065.shtml
- http://m.mobile.nwbbyt.cn/Article/00369.shtml
- http://m.mobile.nwbbyt.cn/Article/00697.shtml
- http://m.mobile.nwbbyt.cn/Article/59711.shtml
- http://m.mobile.puhvjy.cn/Article/2233127.shtml
- http://m.mobile.puhvjy.cn/Article/56130.shtml
- http://m.mobile.cmcvrr.cn/Article/21173.shtml
- http://m.mobile.nwbbyt.cn/Article/3297157.shtml
- http://m.mobile.jnjpgf.cn/Article/1541458.shtml
- http://m.mobile.nwbbyt.cn/Article/989073.shtml
- http://m.mobile.nwbbyt.cn/Article/923375.shtml

## 项目结构

```
mobile-link-navigator/
├── app/                                # 后端应用主目录
│   ├── __init__.py                     # 应用工厂模式入口
│   ├── routes/                         # 路由控制器层
│   │   ├── auth.py                     # 认证相关接口（登录、注册、令牌刷新）
│   │   ├── links.py                    # 链接管理接口（增删改查、导入导出）
│   │   ├── categories.py               # 分类与标签管理接口
│   │   └── stats.py                    # 统计与健康检查接口
│   ├── models/                         # 数据模型层（SQLAlchemy ORM）
│   │   ├── user.py                     # 用户账户模型
│   │   ├── link.py                     # 链接资源模型
│   │   ├── tag.py                      # 标签模型及多对多关联表
│   │   └── visit.py                    # 访问记录模型
│   ├── services/                       # 业务逻辑服务层
│   │   ├── crawler.py                  # 链接解析与元数据提取服务
│   │   ├── indexer.py                  # 全文索引构建与检索服务
│   │   └── scheduler.py                # 定时任务调度器（健康检查、统计汇总）
│   ├── utils/                          # 通用工具函数
│   │   ├── validators.py               # URL 校验与规范化工具
│   │   ├── parsers.py                  # HTML 内容解析与清洗工具
│   │   └── converters.py               # 数据格式转换工具（JSON/CSV/Markdown）
│   └── config/                         # 配置管理
│       ├── default.py                  # 默认配置参数
│       ├── development.py              # 开发环境配置
│       └── production.py               # 生产环境配置示例
├── frontend/                           # 前端单页应用目录
│   ├── src/                            # 源码目录
│   │   ├── components/                 # Vue/React 组件库（按功能模块拆分）
│   │   ├── pages/                      # 页面级组件（首页、列表页、详情页、管理页）
│   │   ├── assets/                     # 静态资源（样式表、图片、字体）
│   │   └── store/                      # 状态管理（Vuex/Pinia 模块化定义）
│   ├── public/                         # 公共静态文件（不经过构建工具处理）
│   └── package.json                    # 前端依赖声明与脚本命令
├── scripts/                            # 运维与开发辅助脚本
│   ├── init_db.py                      # 数据库初始化脚本（建表、创建默认管理员）
│   ├── seed_data.py                    # 示例数据填充脚本（用于开发测试）
│   └── backup.py                       # 数据备份脚本（自动打包并压缩）
├── tests/                              # 测试套件
│   ├── unit/                           # 单元测试（各模块独立测试）
│   ├── integration/                    # 集成测试（API 端到端测试）
│   └── fixtures/                       # 测试固定数据（模拟请求与响应样本）
├── docs/                               # 项目文档（详见文档导航）
├── requirements.txt                    # Python 后端依赖清单
├── Makefile                            # 常用命令封装（启动、测试、构建）
└── README.md                           # 项目说明文件（本文件）
```

## 贡献指南

问题报告与建议提交：请在 GitHub Issues 中详细描述所遇到的问题或功能建议，包含复现步骤、预期行为和实际表现，并附上系统环境信息（操作系统、Python 版本、浏览器版本等）。

代码贡献流程：Fork 本仓库并创建特性分支，提交代码前请确保通过所有单元测试，并编写对应的测试用例以覆盖新增功能。提交 Pull Request 时请清晰描述改动内容和关联 Issue 编号。

文档完善：欢迎协助改进项目文档，包括修正拼写错误、补充 API 示例、完善部署指南等。文档更新请与代码改动分开提交，以便快速审阅。

社区交流：参与 Discussions 板块的讨论，帮助解答其他用户的问题，分享使用经验和最佳实践。活跃贡献者将被邀请加入项目维护团队。

## 常见问题

系统启动后无法访问前端页面，应如何排查？

首先检查前端构建是否完成，确保 frontend/dist 目录存在且包含编译后的文件。其次确认后端服务已正确启动，可通过 curl http://localhost:5000/health 检查健康状态。若使用反向代理，请验证 Nginx 配置中的静态文件路径是否正确。日志文件位于 logs/app.log，可查看详细错误信息。

导入大量链接时页面响应缓慢或超时，有何优化建议？

建议将导入操作改为异步任务模式。系统默认提供了 Celery 任务队列支持，可配置 Redis 作为消息代理。对于超过 1000 条链接的批量导入，系统会自动切换至后台处理，完成后再通过邮件或站内通知提醒用户。也可以调整前端 axios 的超时时间，并在后端使用分页查询和流式处理来降低内存占用。

如何从 SQLite 迁移至 PostgreSQL 生产数据库？

首先在 config/production.py 中修改 SQLALCHEMY_DATABASE_URI 为 PostgreSQL 连接字符串，格式为 postgresql://user:password@host:port/dbname。然后运行 python scripts/migrate_db.py 执行数据迁移，该脚本会自动读取现有 SQLite 数据并写入 PostgreSQL。迁移前请务必备份原始数据。迁移完成后，建议重启服务并验证所有接口功能正常。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
