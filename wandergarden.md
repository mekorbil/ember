# WebIndex 移动端资源导航系统

WebIndex 是一个面向移动端内容聚合场景的轻量级外链资源导航系统，专为中小型内容站点、个人站长及移动端信息聚合平台设计。该项目通过结构化的资源收录机制，将分散在多个移动端域名下的文章链接进行统一归集与分类管理，解决移动端内容分散、链接易失效、检索效率低下的问题。

WebIndex 本身不生产内容，而是作为内容索引层存在，为运营人员提供批量链接收录、分类标注、状态监控与快速检索能力。目标用户包括移动端资讯站运维人员、个人博客作者、内容聚合平台开发者以及需要批量管理外链资源的 SEO 从业者。

## 功能概览

- **批量链接导入与解析**：支持通过文本导入、API 推送、文件上传等方式批量收录外链，自动解析 URL 结构并提取域名、路径、参数等关键信息。

- **域名级自动分类**：根据链接所属域名自动归类，当前内置对 cmcvrr.cn、nwbbyt.cn、puhvjy.cn、jnjpgf.cn 等移动端域名的识别规则，支持自定义域名映射。

- **链接状态周期性检测**：后台定时任务对已收录链接进行 HTTP 状态码检测，自动标记失效链接（404、500 等），支持失效重试与告警通知。

- **多维度检索与筛选**：支持按域名、关键词、收录时间、状态码等维度进行组合检索，满足运营人员快速定位特定链接的需求。

- **数据导出与报表生成**：支持将链接列表导出为 CSV、JSON 格式，便于外部系统集成；定期生成收录统计报表，展示各域名链接数量与健康率。

- **RESTful API 接口**：提供完整的 JSON API，支持第三方系统对收录链接进行增删改查、状态更新等操作，便于嵌入现有工作流。

- **用户权限与操作日志**：支持多用户协作场景，提供基于角色的访问控制，所有增删改操作均记录审计日志。

## 应用场景

- **移动端资讯站日常运维**：运营人员每天需要将合作方或采集来源的数十至上百篇移动端文章链接录入系统，通过 WebIndex 的批量导入功能快速完成收录，并利用分类与检索功能进行后续编辑分发。

- **个人站点外链资源库建设**：个人博主或内容创作者在撰写文章时需引用大量外部来源，可使用 WebIndex 搭建私有外链库，按主题分类存储，避免重复搜索，提升写作效率。

- **SEO 外链效果追踪**：SEO 从业者将投放的外链统一录入系统，通过周期性状态检测功能监控链接存活情况，及时发现被删除或篡改的链接，调整优化策略。

- **内容聚合平台数据预处理**：聚合平台在抓取或接收第三方内容前，先通过 WebIndex 对来源链接进行收录与过滤，快速筛选出有效链接进入后续处理管道。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex.git

# 进入项目目录
cd webindex

# 安装依赖（使用 pip 和 npm）
pip install -r requirements.txt
npm install

# 初始化数据库
python manage.py migrate

# 导入示例链接数据（可选）
python manage.py load_links --file sample_links.json

# 启动开发服务器
python manage.py runserver
```

访问 http://127.0.0.1:8000 进入管理界面，默认管理员账号 admin / password123，首次登录后请立即修改密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9+ | 核心后端运行环境，推荐 3.11 |
| Node.js | 18.x LTS | 前端构建工具与依赖管理 |
| PostgreSQL | 14+ | 生产环境推荐数据库，支持 JSONB 字段 |
| Redis | 7.0+ | 用于缓存与 Celery 任务队列 |
| Nginx | 1.24+ | 生产环境反向代理与静态文件服务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 部署运维 | /docs/deployment/ | 如何在不同环境下部署、配置环境变量、使用 Docker 容器化运行 |
| 使用手册 | /docs/usage/ | 如何批量导入链接、配置分类规则、使用检索与导出功能 |
| API 参考 | /docs/api/ | 所有 RESTful 接口的请求参数、响应格式与错误码说明 |
| 开发指南 | /docs/development/ | 如何二次开发、扩展域名识别规则、增加新的存储后端 |

## 资源列表

- http://m.mobile.cmcvrr.cn/Article/08068.shtml
- http://m.mobile.nwbbyt.cn/Article/5118.shtml
- http://m.mobile.puhvjy.cn/Article/274055.shtml
- http://m.mobile.puhvjy.cn/Article/1355.shtml
- http://m.mobile.puhvjy.cn/Article/5225932.shtml
- http://m.mobile.nwbbyt.cn/Article/7355.shtml
- http://m.mobile.cmcvrr.cn/Article/6511630.shtml
- http://m.mobile.nwbbyt.cn/Article/5162.shtml
- http://m.mobile.puhvjy.cn/Article/9600559.shtml
- http://m.mobile.jnjpgf.cn/Article/441477.shtml
- http://m.mobile.cmcvrr.cn/Article/995372.shtml
- http://m.mobile.jnjpgf.cn/Article/26408.shtml
- http://m.mobile.jnjpgf.cn/Article/37642.shtml
- http://m.mobile.jnjpgf.cn/Article/57453.shtml
- http://m.mobile.cmcvrr.cn/Article/9699.shtml
- http://m.mobile.nwbbyt.cn/Article/37069.shtml
- http://m.mobile.jnjpgf.cn/Article/64621.shtml
- http://m.mobile.jnjpgf.cn/Article/909099.shtml
- http://m.mobile.cmcvrr.cn/Article/246571.shtml
- http://m.mobile.puhvjy.cn/Article/907661.shtml
- http://m.mobile.puhvjy.cn/Article/7485.shtml
- http://m.mobile.puhvjy.cn/Article/8017.shtml
- http://m.mobile.cmcvrr.cn/Article/4812.shtml
- http://m.mobile.jnjpgf.cn/Article/283033.shtml
- http://m.mobile.jnjpgf.cn/Article/6147618.shtml
- http://m.mobile.cmcvrr.cn/Article/8175.shtml
- http://m.mobile.puhvjy.cn/Article/5034743.shtml
- http://m.mobile.nwbbyt.cn/Article/1004.shtml
- http://m.mobile.nwbbyt.cn/Article/2531328.shtml
- http://m.mobile.nwbbyt.cn/Article/6946317.shtml
- http://m.mobile.puhvjy.cn/Article/61744.shtml
- http://m.mobile.cmcvrr.cn/Article/01523.shtml
- http://m.mobile.jnjpgf.cn/Article/1172.shtml
- http://m.mobile.cmcvrr.cn/Article/64645.shtml
- http://m.mobile.nwbbyt.cn/Article/1784.shtml
- http://m.mobile.jnjpgf.cn/Article/7646986.shtml
- http://m.mobile.puhvjy.cn/Article/8456011.shtml
- http://m.mobile.puhvjy.cn/Article/397891.shtml
- http://m.mobile.jnjpgf.cn/Article/415552.shtml
- http://m.mobile.nwbbyt.cn/Article/2916.shtml
- http://m.mobile.puhvjy.cn/Article/600204.shtml
- http://m.mobile.cmcvrr.cn/Article/128794.shtml
- http://m.mobile.cmcvrr.cn/Article/3066557.shtml
- http://m.mobile.nwbbyt.cn/Article/428961.shtml
- http://m.mobile.puhvjy.cn/Article/7715.shtml
- http://m.mobile.cmcvrr.cn/Article/75205.shtml
- http://m.mobile.cmcvrr.cn/Article/6061.shtml
- http://m.mobile.nwbbyt.cn/Article/933259.shtml
- http://m.mobile.cmcvrr.cn/Article/7424.shtml
- http://m.mobile.puhvjy.cn/Article/54473.shtml
- http://m.mobile.puhvjy.cn/Article/5350823.shtml
- http://m.mobile.nwbbyt.cn/Article/608003.shtml
- http://m.mobile.puhvjy.cn/Article/31371.shtml
- http://m.mobile.nwbbyt.cn/Article/181571.shtml
- http://m.mobile.jnjpgf.cn/Article/6374102.shtml
- http://m.mobile.jnjpgf.cn/Article/79095.shtml
- http://m.mobile.cmcvrr.cn/Article/829635.shtml
- http://m.mobile.nwbbyt.cn/Article/7169935.shtml
- http://m.mobile.puhvjy.cn/Article/7003.shtml
- http://m.mobile.puhvjy.cn/Article/002744.shtml
- http://m.mobile.nwbbyt.cn/Article/704271.shtml
- http://m.mobile.puhvjy.cn/Article/624672.shtml
- http://m.mobile.puhvjy.cn/Article/1555243.shtml
- http://m.mobile.jnjpgf.cn/Article/489258.shtml
- http://m.mobile.puhvjy.cn/Article/021085.shtml
- http://m.mobile.puhvjy.cn/Article/989280.shtml
- http://m.mobile.jnjpgf.cn/Article/111228.shtml
- http://m.mobile.cmcvrr.cn/Article/484136.shtml
- http://m.mobile.jnjpgf.cn/Article/44041.shtml
- http://m.mobile.nwbbyt.cn/Article/319754.shtml
- http://m.mobile.nwbbyt.cn/Article/7303.shtml
- http://m.mobile.puhvjy.cn/Article/0975.shtml
- http://m.mobile.cmcvrr.cn/Article/291278.shtml
- http://m.mobile.jnjpgf.cn/Article/6024602.shtml
- http://m.mobile.cmcvrr.cn/Article/0582.shtml
- http://m.mobile.nwbbyt.cn/Article/1635.shtml
- http://m.mobile.puhvjy.cn/Article/4160.shtml
- http://m.mobile.jnjpgf.cn/Article/61392.shtml
- http://m.mobile.nwbbyt.cn/Article/6928368.shtml
- http://m.mobile.cmcvrr.cn/Article/2473091.shtml
- http://m.mobile.jnjpgf.cn/Article/2945886.shtml
- http://m.mobile.jnjpgf.cn/Article/4389.shtml
- http://m.mobile.jnjpgf.cn/Article/7418243.shtml
- http://m.mobile.cmcvrr.cn/Article/95145.shtml
- http://m.mobile.puhvjy.cn/Article/1766.shtml
- http://m.mobile.cmcvrr.cn/Article/63219.shtml
- http://m.mobile.puhvjy.cn/Article/4261.shtml
- http://m.mobile.jnjpgf.cn/Article/7722696.shtml
- http://m.mobile.nwbbyt.cn/Article/7704.shtml
- http://m.mobile.cmcvrr.cn/Article/89436.shtml
- http://m.mobile.cmcvrr.cn/Article/55928.shtml
- http://m.mobile.cmcvrr.cn/Article/1336118.shtml
- http://m.mobile.nwbbyt.cn/Article/83858.shtml
- http://m.mobile.cmcvrr.cn/Article/912434.shtml
- http://m.mobile.nwbbyt.cn/Article/173113.shtml
- http://m.mobile.jnjpgf.cn/Article/884970.shtml
- http://m.mobile.cmcvrr.cn/Article/3420.shtml
- http://m.mobile.puhvjy.cn/Article/4562884.shtml
- http://m.mobile.puhvjy.cn/Article/838301.shtml
- http://m.mobile.puhvjy.cn/Article/98744.shtml
- http://m.mobile.cmcvrr.cn/Article/3409677.shtml
- http://m.mobile.jnjpgf.cn/Article/5080240.shtml
- http://m.mobile.nwbbyt.cn/Article/84109.shtml
- http://m.mobile.cmcvrr.cn/Article/0269673.shtml
- http://m.mobile.nwbbyt.cn/Article/63145.shtml
- http://m.mobile.puhvjy.cn/Article/7677.shtml
- http://m.mobile.cmcvrr.cn/Article/388366.shtml
- http://m.mobile.nwbbyt.cn/Article/606950.shtml
- http://m.mobile.nwbbyt.cn/Article/4285.shtml
- http://m.mobile.nwbbyt.cn/Article/763202.shtml
- http://m.mobile.jnjpgf.cn/Article/5910.shtml
- http://m.mobile.nwbbyt.cn/Article/3367.shtml
- http://m.mobile.cmcvrr.cn/Article/069504.shtml
- http://m.mobile.nwbbyt.cn/Article/27280.shtml
- http://m.mobile.jnjpgf.cn/Article/9777988.shtml
- http://m.mobile.jnjpgf.cn/Article/716089.shtml
- http://m.mobile.cmcvrr.cn/Article/9015903.shtml
- http://m.mobile.cmcvrr.cn/Article/0999583.shtml
- http://m.mobile.nwbbyt.cn/Article/4659.shtml
- http://m.mobile.puhvjy.cn/Article/524608.shtml
- http://m.mobile.nwbbyt.cn/Article/010747.shtml
- http://m.mobile.jnjpgf.cn/Article/81942.shtml
- http://m.mobile.nwbbyt.cn/Article/7709927.shtml
- http://m.mobile.puhvjy.cn/Article/7900939.shtml
- http://m.mobile.jnjpgf.cn/Article/8859.shtml
- http://m.mobile.jnjpgf.cn/Article/495571.shtml
- http://m.mobile.nwbbyt.cn/Article/268083.shtml
- http://m.mobile.nwbbyt.cn/Article/9412157.shtml
- http://m.mobile.nwbbyt.cn/Article/61513.shtml
- http://m.mobile.nwbbyt.cn/Article/6319.shtml
- http://m.mobile.jnjpgf.cn/Article/4191.shtml
- http://m.mobile.nwbbyt.cn/Article/0286.shtml
- http://m.mobile.nwbbyt.cn/Article/77967.shtml
- http://m.mobile.cmcvrr.cn/Article/7988290.shtml
- http://m.mobile.nwbbyt.cn/Article/575531.shtml
- http://m.mobile.nwbbyt.cn/Article/685667.shtml
- http://m.mobile.puhvjy.cn/Article/89956.shtml
- http://m.mobile.cmcvrr.cn/Article/767658.shtml
- http://m.mobile.nwbbyt.cn/Article/6350.shtml
- http://m.mobile.nwbbyt.cn/Article/238800.shtml
- http://m.mobile.cmcvrr.cn/Article/75171.shtml
- http://m.mobile.nwbbyt.cn/Article/004191.shtml
- http://m.mobile.nwbbyt.cn/Article/9072503.shtml
- http://m.mobile.cmcvrr.cn/Article/75506.shtml
- http://m.mobile.cmcvrr.cn/Article/40978.shtml
- http://m.mobile.jnjpgf.cn/Article/2697.shtml
- http://m.mobile.cmcvrr.cn/Article/29093.shtml
- http://m.mobile.nwbbyt.cn/Article/622227.shtml
- http://m.mobile.jnjpgf.cn/Article/5514.shtml
- http://m.mobile.puhvjy.cn/Article/16644.shtml
- http://m.mobile.puhvjy.cn/Article/646239.shtml
- http://m.mobile.nwbbyt.cn/Article/896858.shtml
- http://m.mobile.nwbbyt.cn/Article/01444.shtml
- http://m.mobile.nwbbyt.cn/Article/40497.shtml
- http://m.mobile.jnjpgf.cn/Article/48019.shtml
- http://m.mobile.puhvjy.cn/Article/394867.shtml
- http://m.mobile.jnjpgf.cn/Article/0949.shtml
- http://m.mobile.puhvjy.cn/Article/733807.shtml
- http://m.mobile.cmcvrr.cn/Article/055008.shtml
- http://m.mobile.cmcvrr.cn/Article/6432929.shtml
- http://m.mobile.cmcvrr.cn/Article/2588266.shtml
- http://m.mobile.jnjpgf.cn/Article/5944253.shtml
- http://m.mobile.nwbbyt.cn/Article/0912.shtml
- http://m.mobile.puhvjy.cn/Article/3920641.shtml
- http://m.mobile.jnjpgf.cn/Article/8802109.shtml
- http://m.mobile.nwbbyt.cn/Article/0284249.shtml
- http://m.mobile.jnjpgf.cn/Article/53734.shtml
- http://m.mobile.cmcvrr.cn/Article/58243.shtml
- http://m.mobile.puhvjy.cn/Article/3655556.shtml
- http://m.mobile.jnjpgf.cn/Article/343300.shtml
- http://m.mobile.jnjpgf.cn/Article/097846.shtml
- http://m.mobile.jnjpgf.cn/Article/36558.shtml
- http://m.mobile.nwbbyt.cn/Article/273451.shtml
- http://m.mobile.cmcvrr.cn/Article/579607.shtml
- http://m.mobile.cmcvrr.cn/Article/7561256.shtml
- http://m.mobile.jnjpgf.cn/Article/81136.shtml
- http://m.mobile.nwbbyt.cn/Article/485242.shtml
- http://m.mobile.cmcvrr.cn/Article/5157.shtml
- http://m.mobile.nwbbyt.cn/Article/3563.shtml
- http://m.mobile.jnjpgf.cn/Article/79857.shtml
- http://m.mobile.nwbbyt.cn/Article/1188103.shtml
- http://m.mobile.nwbbyt.cn/Article/123597.shtml
- http://m.mobile.jnjpgf.cn/Article/73391.shtml
- http://m.mobile.puhvjy.cn/Article/7251348.shtml
- http://m.mobile.nwbbyt.cn/Article/2746280.shtml
- http://m.mobile.jnjpgf.cn/Article/639793.shtml
- http://m.mobile.cmcvrr.cn/Article/0751.shtml
- http://m.mobile.jnjpgf.cn/Article/1176217.shtml
- http://m.mobile.jnjpgf.cn/Article/8576501.shtml
- http://m.mobile.cmcvrr.cn/Article/0377.shtml
- http://m.mobile.nwbbyt.cn/Article/7474559.shtml
- http://m.mobile.nwbbyt.cn/Article/240632.shtml
- http://m.mobile.nwbbyt.cn/Article/18580.shtml
- http://m.mobile.jnjpgf.cn/Article/7820.shtml
- http://m.mobile.cmcvrr.cn/Article/3709.shtml
- http://m.mobile.puhvjy.cn/Article/7276425.shtml
- http://m.mobile.puhvjy.cn/Article/5410.shtml
- http://m.mobile.cmcvrr.cn/Article/2252105.shtml
- http://m.mobile.puhvjy.cn/Article/183129.shtml
- http://m.mobile.nwbbyt.cn/Article/14160.shtml
- http://m.mobile.cmcvrr.cn/Article/04447.shtml
- http://m.mobile.puhvjy.cn/Article/0408087.shtml
- http://m.mobile.jnjpgf.cn/Article/3299928.shtml
- http://m.mobile.nwbbyt.cn/Article/687979.shtml
- http://m.mobile.nwbbyt.cn/Article/042235.shtml
- http://m.mobile.jnjpgf.cn/Article/64997.shtml
- http://m.mobile.nwbbyt.cn/Article/96697.shtml
- http://m.mobile.puhvjy.cn/Article/2678.shtml
- http://m.mobile.nwbbyt.cn/Article/5360.shtml
- http://m.mobile.jnjpgf.cn/Article/82812.shtml
- http://m.mobile.jnjpgf.cn/Article/815795.shtml
- http://m.mobile.nwbbyt.cn/Article/289723.shtml
- http://m.mobile.cmcvrr.cn/Article/9266.shtml
- http://m.mobile.jnjpgf.cn/Article/3755.shtml
- http://m.mobile.puhvjy.cn/Article/822713.shtml
- http://m.mobile.cmcvrr.cn/Article/227928.shtml
- http://m.mobile.puhvjy.cn/Article/51631.shtml
- http://m.mobile.jnjpgf.cn/Article/3868625.shtml
- http://m.mobile.nwbbyt.cn/Article/753873.shtml
- http://m.mobile.jnjpgf.cn/Article/800871.shtml
- http://m.mobile.nwbbyt.cn/Article/9194147.shtml
- http://m.mobile.nwbbyt.cn/Article/5316890.shtml
- http://m.mobile.cmcvrr.cn/Article/2320.shtml
- http://m.mobile.cmcvrr.cn/Article/691797.shtml
- http://m.mobile.puhvjy.cn/Article/476649.shtml
- http://m.mobile.jnjpgf.cn/Article/0291.shtml
- http://m.mobile.puhvjy.cn/Article/5261203.shtml
- http://m.mobile.puhvjy.cn/Article/3252.shtml
- http://m.mobile.jnjpgf.cn/Article/6605.shtml
- http://m.mobile.cmcvrr.cn/Article/49514.shtml
- http://m.mobile.jnjpgf.cn/Article/11876.shtml
- http://m.mobile.jnjpgf.cn/Article/72817.shtml
- http://m.mobile.puhvjy.cn/Article/06332.shtml
- http://m.mobile.jnjpgf.cn/Article/7935.shtml
- http://m.mobile.cmcvrr.cn/Article/4142.shtml
- http://m.mobile.puhvjy.cn/Article/28927.shtml
- http://m.mobile.jnjpgf.cn/Article/547022.shtml
- http://m.mobile.puhvjy.cn/Article/01738.shtml
- http://m.mobile.puhvjy.cn/Article/470031.shtml
- http://m.mobile.puhvjy.cn/Article/1700877.shtml
- http://m.mobile.cmcvrr.cn/Article/6227.shtml
- http://m.mobile.nwbbyt.cn/Article/44967.shtml
- http://m.mobile.jnjpgf.cn/Article/0879352.shtml
- http://m.mobile.jnjpgf.cn/Article/8887.shtml
- http://m.mobile.puhvjy.cn/Article/357250.shtml
- http://m.mobile.nwbbyt.cn/Article/8068626.shtml
- http://m.mobile.nwbbyt.cn/Article/15106.shtml
- http://m.mobile.cmcvrr.cn/Article/33599.shtml
- http://m.mobile.puhvjy.cn/Article/125423.shtml
- http://m.mobile.nwbbyt.cn/Article/71510.shtml

## 项目结构

```
webindex/
├── manage.py                      # Django 项目管理入口
├── requirements.txt               # Python 依赖列表
├── package.json                   # 前端构建依赖
├── webindex/                      # 项目主配置目录
│   ├── settings/                  # 环境配置分拆
│   │   ├── base.py                # 公共基础配置
│   │   ├── development.py         # 开发环境配置
│   │   └── production.py          # 生产环境配置
│   ├── urls.py                    # 主路由定义
│   └── celery.py                  # 异步任务配置
├── apps/                          # 所有功能应用
│   ├── links/                     # 链接管理核心模块
│   │   ├── models.py              # Link, Category, DomainRule
│   │   ├── views.py               # 增删改查 API 与页面视图
│   │   ├── services/              # 业务逻辑层
│   │   │   ├── importer.py        # 批量导入与解析
│   │   │   └── checker.py         # 状态检测器
│   │   └── migrations/            # 数据库迁移文件
│   ├── accounts/                  # 用户与权限模块
│   ├── api/                       # RESTful API 接口
│   └── dashboard/                 # 统计看板与报表
├── static/                        # 静态资源（CSS / JS / 图片）
│   ├── css/                       # 样式文件
│   └── js/                        # 前端交互脚本
├── templates/                     # Django 模板文件
│   ├── layout/                    # 基础布局模板
│   └── links/                     # 链接相关页面模板
├── docs/                          # 完整项目文档
│   ├── deployment/                # 部署文档
│   ├── usage/                     # 使用手册
│   ├── api/                       # API 参考
│   └── development/               # 开发指南
├── scripts/                       # 运维与工具脚本
│   ├── init_db.py                 # 数据库初始化
│   └── import_links.py            # 命令行批量导入工具
├── docker/                        # Docker 相关文件
│   ├── Dockerfile                 # 镜像构建文件
│   └── docker-compose.yml         # 服务编排配置
└── tests/                         # 单元测试与集成测试
    ├── test_models.py
    ├── test_api.py
    └── test_checker.py
```

## 贡献指南

1. 阅读项目开发文档 /docs/development/ 了解技术栈、代码规范与模块划分，确认本地环境满足 Python 3.9+ 及 Node.js 18+ 的要求。

2. 在 GitHub 或 Gitee 上 Fork 项目仓库，克隆到本地后创建功能分支，分支命名采用 feature/xxx 或 fix/xxx 格式。

3. 编写代码时遵循 PEP 8 规范与 ESLint 规则，新增功能需同步编写单元测试，确保测试覆盖率不低于 80%。

4. 提交前运行全套测试套件（python manage.py test）与构建流程（npm run build），确保无报错且性能无明显衰退。

5. 发起 Pull Request 并填写变更模板，详细说明改动原因、影响范围及测试情况，等待项目维护者审核与合并。

## 常见问题

**Q：系统最多能承载多少条链接的收录与检测？**

A：在推荐的硬件配置（4C8G、PostgreSQL 14）下，单实例可稳定承载 50 万条链接的元数据存储与每日全量状态检测。若链接数量超过百万级，建议启用 Redis 缓存并配置 Celery 分布式任务队列进行横向扩展。当前资源列表包含 250 条链接，属于极小规模，无需额外优化。

**Q：如何添加新的域名分类规则？**

A：通过管理后台的「域名规则」配置入口，可添加新的域名前缀或正则表达式映射到已有分类，或创建新分类。系统在导入链接时会根据配置自动匹配。如需代码级扩展，可继承 apps.links.services.classifier.BaseClassifier 类实现自定义分类逻辑。

**Q：链接状态检测的频率和超时时间如何调整？**

A：检测频率由 Celery 周期性任务配置决定，默认每 24 小时执行一次全量检测。可在 settings/base.py 中修改 CELERY_BEAT_SCHEDULE 下的 checker_task 配置项。单次请求超时时间默认为 10 秒，可通过 CHECKER_TIMEOUT 环境变量调整，建议不超过 30 秒以避免任务堆积。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
