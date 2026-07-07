# LinkMap 移动端资源索引系统

LinkMap 是一个面向移动端内容聚合与导航的开源资源索引系统，专为技术内容运营者、信息聚合平台及个人知识库管理者设计。该项目将分散于多个移动端内容源的文章链接进行统一结构化存储，提供可检索、可分类、可扩展的链接管理能力。目标用户包括运维工程师、内容运营人员、爬虫开发者以及需要长期维护大量外链资源的个人站长。LinkMap 不提供内容抓取与渲染功能，仅作为 URL 元数据索引层，保证链接的可追溯性与分类清晰度，降低外链管理过程中的丢失与重复风险。

## 功能概览

- 多源链接统一入库：支持从不同移动端域名下批量导入文章链接，自动识别来源域名与文章 ID，生成唯一索引标识。

- 灵活的分类标签系统：每条链接可绑定多个自定义标签，支持按专题、领域、优先级或审核状态进行多维筛选。

- 链接可用性周期检测：内置定时校验任务，支持 HTTP 状态码检查与响应超时判定，自动标记异常链接并生成告警日志。

- 批量导入与导出接口：提供 JSON 与 CSV 格式的批量导入导出能力，便于与外部爬虫系统或数据中台进行对接。

- 全文检索与高级过滤：基于文章 URL 关键词、来源域名、导入时间范围进行组合检索，支持分页排序与结果高亮。

- 访问统计与热度排序：记录每条链接的访问次数与最近访问时间，支持按热度、新鲜度或随机排序输出列表。

- 扩展字段自定义：每条链接支持 JSON 格式的扩展元数据，可用于存储摘要、作者、发布时间等补充信息。

- 多用户协作权限：内置基于角色的访问控制，区分管理员、编辑员与访客三类权限，适合团队协作管理。

## 应用场景

技术博客外链库管理：技术人员在阅读移动端技术文章时，可将有价值的外链统一收录至 LinkMap，并标注阅读状态与学习优先级，便于后续复盘与知识整理。

内容运营团队的素材池：内容编辑团队从多个移动端资讯源收集备选文章链接，通过标签分类区分领域（如前端、后端、运维、AI），快速定位可用素材进行二次加工。

爬虫系统的下游存储层：分布式爬虫抓取移动端文章页面后，将解析出的 URL 直接推送至 LinkMap API，作为原始链接池供下游去重、过滤与分发模块使用。

个人知识库的引用索引：个人知识管理用户可将笔记中引用的外部链接统一托管至 LinkMap，避免链接散落在多个文档中导致维护困难，同时可利用可用性检测功能定期清理失效引用。

## 快速开始

以下操作以 Linux/macOS 环境为例，确保系统已安装 Git 与 Python 3.9 及以上版本。

```bash
git clone https://github.com/linkmap-io/linkmap-core.git
cd linkmap-core
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py runserver
```

服务启动后默认监听 8000 端口，访问 http://127.0.0.1:8000/api/v1/links 可获取链接列表 JSON 响应。管理员后台路径为 /admin，默认账号密码请参考 .env 文件中的初始化配置说明。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 ~ 3.11 | 核心运行环境，3.12 及以上版本暂未完全适配 |
| PostgreSQL | 12.x ~ 15.x | 主数据库，用于存储链接元数据与标签关系 |
| Redis | 6.x 及以上 | 缓存与任务队列后端，用于异步检测任务 |
| Celery | 5.2.x | 分布式任务调度框架，执行周期校验 |
| Django | 4.2 LTS | Web 框架及 ORM 层，提供管理后台与 API |
| django-cors-headers | 4.3.x | 跨域资源共享中间件，供前端独立部署调用 |
| uWSGI | 2.0.x | 生产环境 WSGI 服务器（可选，开发环境可用 runserver） |
| Node.js | 18.x 及以上 | 仅前端管理面板构建时需要（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quickstart.md | 如何快速部署开发环境并导入第一批链接数据 |
| API 参考 | /docs/api/v1/links.md | 链接资源的增删改查接口规范与状态码说明 |
| 运维手册 | /docs/operations/healthcheck.md | 如何配置可用性检测周期、告警阈值与日志归档 |
| 扩展开发 | /docs/development/custom_field.md | 如何自定义扩展字段类型及编写数据校验钩子 |
| 部署指引 | /docs/deployment/gunicorn_nginx.md | 生产环境下的 Nginx 反向代理与 Gunicorn 配置示例 |
| 数据迁移 | /docs/migration/import_export.md | 从旧版 CSV 模板导入数据或导出全量备份的步骤 |

## 资源列表

- http://map.mobile.jnjpgf.cn/Article/6020764.shtml
- http://map.mobile.nwbbyt.cn/Article/05504.shtml
- http://map.mobile.jnjpgf.cn/Article/43204.shtml
- http://map.mobile.nwbbyt.cn/Article/602468.shtml
- http://map.mobile.nwbbyt.cn/Article/1718.shtml
- http://map.mobile.cmcvrr.cn/Article/292851.shtml
- http://map.mobile.puhvjy.cn/Article/8545.shtml
- http://map.mobile.jnjpgf.cn/Article/3343.shtml
- http://map.mobile.jnjpgf.cn/Article/02586.shtml
- http://map.mobile.jnjpgf.cn/Article/024682.shtml
- http://map.mobile.cmcvrr.cn/Article/5803.shtml
- http://map.mobile.nwbbyt.cn/Article/14895.shtml
- http://map.mobile.nwbbyt.cn/Article/0198922.shtml
- http://map.mobile.puhvjy.cn/Article/69075.shtml
- http://map.mobile.jnjpgf.cn/Article/9116.shtml
- http://map.mobile.puhvjy.cn/Article/6296083.shtml
- http://map.mobile.nwbbyt.cn/Article/3037961.shtml
- http://map.mobile.puhvjy.cn/Article/72254.shtml
- http://map.mobile.cmcvrr.cn/Article/101784.shtml
- http://map.mobile.puhvjy.cn/Article/3729783.shtml
- http://map.mobile.jnjpgf.cn/Article/4218498.shtml
- http://map.mobile.nwbbyt.cn/Article/78036.shtml
- http://map.mobile.nwbbyt.cn/Article/236378.shtml
- http://map.mobile.nwbbyt.cn/Article/838570.shtml
- http://map.mobile.cmcvrr.cn/Article/22310.shtml
- http://map.mobile.nwbbyt.cn/Article/51041.shtml
- http://map.mobile.nwbbyt.cn/Article/90852.shtml
- http://map.mobile.puhvjy.cn/Article/1282.shtml
- http://map.mobile.nwbbyt.cn/Article/2111.shtml
- http://map.mobile.jnjpgf.cn/Article/56005.shtml
- http://map.mobile.nwbbyt.cn/Article/7461.shtml
- http://map.mobile.cmcvrr.cn/Article/3228286.shtml
- http://map.mobile.jnjpgf.cn/Article/73056.shtml
- http://map.mobile.cmcvrr.cn/Article/5135262.shtml
- http://map.mobile.puhvjy.cn/Article/6145610.shtml
- http://map.mobile.nwbbyt.cn/Article/8646200.shtml
- http://map.mobile.jnjpgf.cn/Article/5905264.shtml
- http://map.mobile.jnjpgf.cn/Article/643940.shtml
- http://map.mobile.nwbbyt.cn/Article/06562.shtml
- http://map.mobile.nwbbyt.cn/Article/52175.shtml
- http://map.mobile.jnjpgf.cn/Article/267151.shtml
- http://map.mobile.puhvjy.cn/Article/71310.shtml
- http://map.mobile.cmcvrr.cn/Article/3481716.shtml
- http://map.mobile.puhvjy.cn/Article/8327243.shtml
- http://map.mobile.cmcvrr.cn/Article/5563506.shtml
- http://map.mobile.nwbbyt.cn/Article/0529913.shtml
- http://map.mobile.cmcvrr.cn/Article/478244.shtml
- http://map.mobile.jnjpgf.cn/Article/9533.shtml
- http://map.mobile.puhvjy.cn/Article/986900.shtml
- http://map.mobile.cmcvrr.cn/Article/5979784.shtml
- http://map.mobile.cmcvrr.cn/Article/01419.shtml
- http://map.mobile.cmcvrr.cn/Article/6897850.shtml
- http://map.mobile.puhvjy.cn/Article/21055.shtml
- http://map.mobile.puhvjy.cn/Article/727567.shtml
- http://map.mobile.cmcvrr.cn/Article/6474.shtml
- http://map.mobile.nwbbyt.cn/Article/4398959.shtml
- http://map.mobile.nwbbyt.cn/Article/01898.shtml
- http://map.mobile.puhvjy.cn/Article/64707.shtml
- http://map.mobile.puhvjy.cn/Article/3894633.shtml
- http://map.mobile.nwbbyt.cn/Article/87492.shtml
- http://map.mobile.nwbbyt.cn/Article/02984.shtml
- http://map.mobile.jnjpgf.cn/Article/949090.shtml
- http://map.mobile.nwbbyt.cn/Article/37259.shtml
- http://map.mobile.cmcvrr.cn/Article/2078.shtml
- http://map.mobile.jnjpgf.cn/Article/3852880.shtml
- http://map.mobile.jnjpgf.cn/Article/272447.shtml
- http://map.mobile.puhvjy.cn/Article/392315.shtml
- http://map.mobile.cmcvrr.cn/Article/07163.shtml
- http://map.mobile.puhvjy.cn/Article/1087770.shtml
- http://map.mobile.puhvjy.cn/Article/8306248.shtml
- http://map.mobile.nwbbyt.cn/Article/8242.shtml
- http://map.mobile.cmcvrr.cn/Article/9490645.shtml
- http://map.mobile.cmcvrr.cn/Article/20085.shtml
- http://map.mobile.nwbbyt.cn/Article/2362.shtml
- http://map.mobile.puhvjy.cn/Article/76962.shtml
- http://map.mobile.jnjpgf.cn/Article/6515.shtml
- http://map.mobile.jnjpgf.cn/Article/2598.shtml
- http://map.mobile.jnjpgf.cn/Article/92661.shtml
- http://map.mobile.cmcvrr.cn/Article/4102.shtml
- http://map.mobile.puhvjy.cn/Article/3950.shtml
- http://map.mobile.jnjpgf.cn/Article/9915677.shtml
- http://map.mobile.nwbbyt.cn/Article/0051.shtml
- http://map.mobile.cmcvrr.cn/Article/31694.shtml
- http://map.mobile.cmcvrr.cn/Article/8364.shtml
- http://map.mobile.jnjpgf.cn/Article/560036.shtml
- http://map.mobile.jnjpgf.cn/Article/5712.shtml
- http://map.mobile.cmcvrr.cn/Article/399462.shtml
- http://map.mobile.cmcvrr.cn/Article/14033.shtml
- http://map.mobile.jnjpgf.cn/Article/8953.shtml
- http://map.mobile.jnjpgf.cn/Article/7252914.shtml
- http://map.mobile.cmcvrr.cn/Article/8651435.shtml
- http://map.mobile.puhvjy.cn/Article/3497730.shtml
- http://map.mobile.nwbbyt.cn/Article/2499062.shtml
- http://map.mobile.puhvjy.cn/Article/3257350.shtml
- http://map.mobile.nwbbyt.cn/Article/8938.shtml
- http://map.mobile.puhvjy.cn/Article/53017.shtml
- http://map.mobile.nwbbyt.cn/Article/5895.shtml
- http://map.mobile.nwbbyt.cn/Article/71498.shtml
- http://map.mobile.cmcvrr.cn/Article/943603.shtml
- http://map.mobile.cmcvrr.cn/Article/7425.shtml
- http://map.mobile.cmcvrr.cn/Article/0962636.shtml
- http://map.mobile.cmcvrr.cn/Article/6909.shtml
- http://map.mobile.cmcvrr.cn/Article/759488.shtml
- http://map.mobile.jnjpgf.cn/Article/880343.shtml
- http://map.mobile.nwbbyt.cn/Article/3538170.shtml
- http://map.mobile.puhvjy.cn/Article/05972.shtml
- http://map.mobile.puhvjy.cn/Article/7265918.shtml
- http://map.mobile.puhvjy.cn/Article/7829.shtml
- http://map.mobile.jnjpgf.cn/Article/34654.shtml
- http://map.mobile.cmcvrr.cn/Article/20632.shtml
- http://map.mobile.nwbbyt.cn/Article/5277.shtml
- http://map.mobile.jnjpgf.cn/Article/310759.shtml
- http://map.mobile.jnjpgf.cn/Article/1567892.shtml
- http://map.mobile.jnjpgf.cn/Article/95582.shtml
- http://map.mobile.cmcvrr.cn/Article/964298.shtml
- http://map.mobile.puhvjy.cn/Article/5011526.shtml
- http://map.mobile.cmcvrr.cn/Article/0045437.shtml
- http://map.mobile.cmcvrr.cn/Article/5063501.shtml
- http://map.mobile.puhvjy.cn/Article/741467.shtml
- http://map.mobile.puhvjy.cn/Article/1652.shtml
- http://map.mobile.jnjpgf.cn/Article/6340951.shtml
- http://map.mobile.jnjpgf.cn/Article/74322.shtml
- http://map.mobile.puhvjy.cn/Article/4974.shtml
- http://map.mobile.jnjpgf.cn/Article/76947.shtml
- http://map.mobile.nwbbyt.cn/Article/32931.shtml
- http://map.mobile.cmcvrr.cn/Article/16218.shtml
- http://map.mobile.cmcvrr.cn/Article/6141.shtml
- http://map.mobile.jnjpgf.cn/Article/87969.shtml
- http://map.mobile.jnjpgf.cn/Article/123906.shtml
- http://map.mobile.nwbbyt.cn/Article/722631.shtml
- http://map.mobile.cmcvrr.cn/Article/7967.shtml
- http://map.mobile.puhvjy.cn/Article/7101017.shtml
- http://map.mobile.puhvjy.cn/Article/8145.shtml
- http://map.mobile.nwbbyt.cn/Article/1189797.shtml
- http://map.mobile.nwbbyt.cn/Article/8656003.shtml
- http://map.mobile.jnjpgf.cn/Article/165114.shtml
- http://map.mobile.cmcvrr.cn/Article/60180.shtml
- http://map.mobile.nwbbyt.cn/Article/2803.shtml
- http://map.mobile.puhvjy.cn/Article/2148.shtml
- http://map.mobile.puhvjy.cn/Article/667884.shtml
- http://map.mobile.puhvjy.cn/Article/1621.shtml
- http://map.mobile.cmcvrr.cn/Article/361095.shtml
- http://map.mobile.cmcvrr.cn/Article/46228.shtml
- http://map.mobile.puhvjy.cn/Article/8356149.shtml
- http://map.mobile.puhvjy.cn/Article/4468.shtml
- http://map.mobile.jnjpgf.cn/Article/1639.shtml
- http://map.mobile.nwbbyt.cn/Article/7552.shtml
- http://map.mobile.puhvjy.cn/Article/0683350.shtml
- http://map.mobile.nwbbyt.cn/Article/61374.shtml
- http://map.mobile.cmcvrr.cn/Article/0458.shtml
- http://map.mobile.puhvjy.cn/Article/605133.shtml
- http://map.mobile.jnjpgf.cn/Article/1663.shtml
- http://map.mobile.cmcvrr.cn/Article/0840939.shtml
- http://map.mobile.cmcvrr.cn/Article/7694.shtml
- http://map.mobile.nwbbyt.cn/Article/4885.shtml
- http://map.mobile.puhvjy.cn/Article/111918.shtml
- http://map.mobile.jnjpgf.cn/Article/6589864.shtml
- http://map.mobile.puhvjy.cn/Article/350871.shtml
- http://map.mobile.jnjpgf.cn/Article/4071846.shtml
- http://map.mobile.nwbbyt.cn/Article/413513.shtml
- http://map.mobile.puhvjy.cn/Article/48839.shtml
- http://map.mobile.cmcvrr.cn/Article/9010109.shtml
- http://map.mobile.nwbbyt.cn/Article/622698.shtml
- http://map.mobile.cmcvrr.cn/Article/9999.shtml
- http://map.mobile.cmcvrr.cn/Article/3402.shtml
- http://map.mobile.jnjpgf.cn/Article/0365986.shtml
- http://map.mobile.jnjpgf.cn/Article/599715.shtml
- http://map.mobile.puhvjy.cn/Article/917738.shtml
- http://map.mobile.puhvjy.cn/Article/18993.shtml
- http://map.mobile.jnjpgf.cn/Article/642874.shtml
- http://map.mobile.nwbbyt.cn/Article/590684.shtml
- http://map.mobile.cmcvrr.cn/Article/5040.shtml
- http://map.mobile.cmcvrr.cn/Article/31260.shtml
- http://map.mobile.jnjpgf.cn/Article/1921.shtml
- http://map.mobile.nwbbyt.cn/Article/4903752.shtml
- http://map.mobile.puhvjy.cn/Article/49148.shtml
- http://map.mobile.cmcvrr.cn/Article/85223.shtml
- http://map.mobile.jnjpgf.cn/Article/211621.shtml
- http://map.mobile.cmcvrr.cn/Article/0018.shtml
- http://map.mobile.puhvjy.cn/Article/07071.shtml
- http://map.mobile.nwbbyt.cn/Article/8178507.shtml
- http://map.mobile.cmcvrr.cn/Article/810026.shtml
- http://map.mobile.cmcvrr.cn/Article/5418526.shtml
- http://map.mobile.jnjpgf.cn/Article/93015.shtml
- http://map.mobile.jnjpgf.cn/Article/644803.shtml
- http://map.mobile.jnjpgf.cn/Article/63373.shtml
- http://map.mobile.jnjpgf.cn/Article/8264141.shtml
- http://map.mobile.cmcvrr.cn/Article/1996.shtml
- http://map.mobile.nwbbyt.cn/Article/552590.shtml
- http://map.mobile.puhvjy.cn/Article/3100498.shtml
- http://map.mobile.nwbbyt.cn/Article/6027.shtml
- http://map.mobile.cmcvrr.cn/Article/2201.shtml
- http://map.mobile.nwbbyt.cn/Article/050252.shtml
- http://map.mobile.jnjpgf.cn/Article/6063.shtml
- http://map.mobile.cmcvrr.cn/Article/6946314.shtml
- http://map.mobile.nwbbyt.cn/Article/0216.shtml
- http://map.mobile.jnjpgf.cn/Article/5939.shtml
- http://map.mobile.puhvjy.cn/Article/6737367.shtml
- http://map.mobile.cmcvrr.cn/Article/12495.shtml
- http://map.mobile.cmcvrr.cn/Article/4105434.shtml
- http://map.mobile.jnjpgf.cn/Article/10328.shtml
- http://map.mobile.jnjpgf.cn/Article/7847571.shtml
- http://map.mobile.nwbbyt.cn/Article/1526390.shtml
- http://map.mobile.puhvjy.cn/Article/521655.shtml
- http://map.mobile.puhvjy.cn/Article/749225.shtml
- http://map.mobile.jnjpgf.cn/Article/0554.shtml
- http://map.mobile.cmcvrr.cn/Article/7040.shtml
- http://map.mobile.puhvjy.cn/Article/0551536.shtml
- http://map.mobile.cmcvrr.cn/Article/3044308.shtml
- http://map.mobile.puhvjy.cn/Article/9639.shtml
- http://map.mobile.puhvjy.cn/Article/7498191.shtml
- http://map.mobile.puhvjy.cn/Article/9605.shtml
- http://map.mobile.puhvjy.cn/Article/585224.shtml
- http://map.mobile.jnjpgf.cn/Article/49529.shtml
- http://map.mobile.puhvjy.cn/Article/82469.shtml
- http://map.mobile.cmcvrr.cn/Article/7443.shtml
- http://map.mobile.jnjpgf.cn/Article/25323.shtml
- http://map.mobile.jnjpgf.cn/Article/2752.shtml
- http://map.mobile.jnjpgf.cn/Article/310756.shtml
- http://map.mobile.jnjpgf.cn/Article/641654.shtml
- http://map.mobile.jnjpgf.cn/Article/7539.shtml
- http://map.mobile.puhvjy.cn/Article/01626.shtml
- http://map.mobile.nwbbyt.cn/Article/6305746.shtml
- http://map.mobile.puhvjy.cn/Article/44196.shtml
- http://map.mobile.cmcvrr.cn/Article/3028.shtml
- http://map.mobile.cmcvrr.cn/Article/3651669.shtml
- http://map.mobile.jnjpgf.cn/Article/49898.shtml
- http://map.mobile.cmcvrr.cn/Article/3160.shtml
- http://map.mobile.cmcvrr.cn/Article/9466658.shtml
- http://map.mobile.jnjpgf.cn/Article/4205944.shtml
- http://map.mobile.jnjpgf.cn/Article/8228599.shtml
- http://map.mobile.nwbbyt.cn/Article/7773970.shtml
- http://map.mobile.puhvjy.cn/Article/5631774.shtml
- http://map.mobile.nwbbyt.cn/Article/4655644.shtml
- http://map.mobile.cmcvrr.cn/Article/31932.shtml
- http://map.mobile.cmcvrr.cn/Article/77305.shtml
- http://map.mobile.jnjpgf.cn/Article/9203011.shtml
- http://map.mobile.nwbbyt.cn/Article/13742.shtml
- http://map.mobile.jnjpgf.cn/Article/2179030.shtml
- http://map.mobile.nwbbyt.cn/Article/364139.shtml
- http://map.mobile.jnjpgf.cn/Article/0664.shtml
- http://map.mobile.nwbbyt.cn/Article/256242.shtml
- http://map.mobile.jnjpgf.cn/Article/40235.shtml
- http://map.mobile.nwbbyt.cn/Article/1185.shtml
- http://map.mobile.jnjpgf.cn/Article/4709594.shtml
- http://map.mobile.puhvjy.cn/Article/3970876.shtml
- http://map.mobile.jnjpgf.cn/Article/097108.shtml
- http://map.mobile.jnjpgf.cn/Article/9145.shtml
- http://map.mobile.cmcvrr.cn/Article/622085.shtml
- http://map.mobile.jnjpgf.cn/Article/3407248.shtml

## 项目结构

```
linkmap-core/
├── .env.example                  # 环境变量模板，含数据库连接与密钥配置
├── .gitignore                    # Git 忽略规则，排除 venv 与本地配置
├── README.md                     # 项目说明文档（本文件）
├── requirements.txt              # Python 依赖清单，锁定主版本号
├── docker-compose.yml            # 开发环境容器编排，含 Postgres 与 Redis
├── docker/                       # Docker 构建上下文目录
│   ├── app.Dockerfile            # 应用服务镜像构建文件
│   └── nginx.conf               # 生产环境 Nginx 站点配置样例
├── src/                          # 项目源码主目录
│   ├── __init__.py
│   ├── manage.py                 # Django 项目管理入口
│   ├── config/                   # 全局配置模块
│   │   ├── settings.py           # 分环境配置（开发/测试/生产）
│   │   ├── urls.py               # 根路由定义
│   │   └── celery.py             # Celery 应用实例与定时任务声明
│   ├── apps/                     # 各功能应用集合
│   │   ├── links/                # 链接核心模块：模型、序列化器、视图
│   │   ├── tags/                 # 标签系统：多对多关系管理
│   │   ├── checks/               # 可用性检测：异步任务与结果记录
│   │   ├── stats/                # 访问统计：中间件与聚合查询
│   │   └── users/                # 用户与权限：扩展 Django 内置模型
│   ├── libs/                     # 通用工具库
│   │   ├── http_client.py        # 封装 requests 与超时重试逻辑
│   │   ├── parser.py             # URL 解析与域名提取工具
│   │   └── validators.py         # 自定义字段校验器
│   ├── tests/                    # 单元测试与集成测试用例
│   │   ├── test_links_api.py
│   │   ├── test_checks_task.py
│   │   └── fixtures/             # 测试用 JSON 样本数据
│   └── templates/                # 管理后台自定义模板（仅扩展使用）
└── scripts/                      # 运维与部署辅助脚本
    ├── init_db.sql               # 初始化数据库表结构
    ├── import_csv.py             # 批量导入 CSV 链接数据
    └── healthcheck.py            # 独立运行的链接状态扫描器
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制至个人账户下，随后将 Fork 后的仓库克隆至本地开发环境。

2. 创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式，例如 `feature/support-batch-delete`。

3. 完成代码修改后，运行现有单元测试确保无回归问题，并为新增功能补充对应的测试用例，测试覆盖率不低于百分之八十。

4. 提交代码时使用规范的 Commit 信息格式，首行简明描述改动类型与范围，例如 `feat(links): add bulk delete endpoint`。

5. 推送分支至远程仓库后，通过 GitHub 界面发起 Pull Request，并在 PR 描述中关联相关 Issue 或说明改动动机与影响范围。

## 常见问题

Q: 启动服务时提示 PostgreSQL 连接失败，如何排查？

A: 首先检查 .env 文件中的 DATABASE_URL 配置是否正确，确保主机地址、端口、用户名与密码无误。若使用 Docker Compose 启动的数据库，需确认容器处于运行状态。可执行 `docker ps` 查看容器状态，或使用 `nc -zv 127.0.0.1 5432` 测试端口可达性。若数据库服务位于远程主机，请检查防火墙规则是否放行对应端口。

Q: 如何自定义链接可用性检测的超时时间与重试次数？

A: 在 src/config/settings.py 中找到 `CHECKER_TIMEOUT` 和 `CHECKER_RETRIES` 变量，分别对应单次请求超时秒数与失败重试次数。修改后重启 Celery 工作进程即可生效。若需对不同域名使用差异化策略，可继承 `src/libs/http_client.py` 中的 `HttpClient` 类并覆写 `get_timeout` 方法。

Q: 导入大量链接时出现性能瓶颈，有哪些优化手段？

A: 批量导入场景下，建议使用 Django 的 `bulk_create` 接口并设置 `batch_size` 参数，避免逐条插入造成数据库连接开销。同时可临时关闭链接可用性检测的后台任务，待导入完成后再手动触发全量校验。若数据量超过十万条，建议使用 PostgreSQL 的 COPY 命令直接导入 CSV 文件，脚本位于 `scripts/import_csv.py` 中已提供示例实现。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
