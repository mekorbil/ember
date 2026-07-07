# MobileLink 聚合站

MobileLink 聚合站是一个面向移动端内容分发场景的轻量级外链资源归集与管理平台，专注于将散落在多个移动域名下的文章链接进行统一索引、分类标注与可检索化呈现。该项目主要服务于内容运营人员、数据采集工程师以及个人站长，帮助其在批量处理移动端 HTML 资源时，快速建立链接台账、去重校验、状态监控以及访问可达性分析，从而降低人工整理成本并提升批量外链管理效率。

本项目的核心定位不是内容生产，而是对已有移动端文章资源的链接层进行结构化收纳与导航。MobileLink 本身不存储任何文章正文，仅存储链接元数据（URL、来源域名、采集时间、状态码、标题摘要等）。通过简单的命令行工具与静态站点生成机制，用户可将任意数量的移动端文章链接转化为可浏览、可过滤、可导出为 JSON 或 CSV 的本地知识库，适用于爬虫后期处理、历史链接归档、批量跳转巡检等工程化场景。

## 功能概览

**批量链接导入与去重**：支持从纯文本文件、CSV 或标准输入中批量导入 URL，自动识别重复条目并基于域名与路径进行智能合并，保留首次导入时间与最新访问时间。

**域名维度自动归类**：根据 URL 中的二级域名（如 puhvjy.cn、jnjpgf.cn、cmcvrr.cn、nwbbyt.cn）自动生成分类标签，支持自定义域名别名与分组规则，便于按来源站点进行筛选统计。

**链接可达性实时检测**：内置异步 HTTP 探活模块，可配置超时与重试策略，对每条链接返回状态码、响应时间与重定向链，支持标记死链与异常链接。

**结构化元数据提取**：对可访问的 HTML 页面自动提取标题、字符编码、Content-Type 以及 meta description，作为链接的补充描述字段，提升检索与展示的信息密度。

**多格式数据导出**：支持将当前链接库导出为 Markdown 表格、JSON 数组、CSV 表格以及纯文本列表，满足不同下游工具链的输入要求。

**本地静态浏览界面**：基于模板引擎生成轻量级 HTML 页面，包含搜索框、域名筛选下拉菜单与分页列表，无需数据库即可在浏览器中打开查看完整链接台账。

## 应用场景

**移动端内容汇总与台账维护**：内容运营团队定期从多个合作站点获取文章链接，可通过 MobileLink 将所有链接归入统一台账，按域名查看每个来源的发布数量与活跃状态，便于后续安排外链置换或内容转载排期。

**爬虫采集后的链接清洗与归档**：数据采集工程师在大规模抓取移动页面后，可将提取到的内链或外链列表导入本工具，利用去重与可达性检测功能清洗无效链接，并将有效链接按域名分类存储，供后续分析脚本调用。

**历史链接周期性巡检**：站长或 SEO 专员可使用本项目对站内或友链的历史文章链接进行月度可达性巡检，批量检测 404、500 或超时状态，快速定位失效链接并生成报告，避免用户访问空白页面。

**链接数据交接与协作**：在团队协作场景中，成员可将整理好的链接库导出为 JSON 或 CSV，通过版本控制系统共享，保证多人维护的链接集合保持一致，且每次变更均有时间戳记录。

## 快速开始

以下命令演示了从克隆仓库到启动本地服务的完整流程，默认使用 Python 3.10 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/mobilelink.git
cd mobilelink

# 创建并激活虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate
# Windows 用户使用：venv\Scripts\activate

# 安装核心依赖
pip install -r requirements.txt

# 使用示例数据初始化链接库（包含 250 条移动端文章链接）
python mobilelink.py init --source ./data/sample_urls.txt

# 执行链接可达性检测（默认并发数 10）
python mobilelink.py check --concurrency 10

# 生成静态浏览页面到 output/ 目录
python mobilelink.py build --output ./output

# 启动简易 HTTP 服务查看生成的页面
python -m http.server 8000 --directory ./output
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，低版本不支持 match case 语法与异步特性 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端库，用于并发链接探测与页面获取 |
| beautifulsoup4 | 4.12.0 及以上 | HTML 解析库，用于提取页面标题及 meta 信息 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析后端，提供高性能 HTML 树解析 |
| click | 8.1.0 及以上 | 命令行接口框架，用于定义子命令与参数解析 |
| jinja2 | 3.1.0 及以上 | 模板渲染引擎，用于生成静态浏览界面 HTML |
| pytest | 7.4.0 及以上 | 单元测试框架，仅在开发模式时需要 |
| black | 23.0.0 及以上 | 代码格式化工具，仅在贡献代码时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速安装并导入第一批链接；如何理解本项目的输入输出模型 |
| 命令参考 | docs/commands.md | 每个 CLI 子命令的完整参数列表、用法示例与常见报错处理 |
| 配置说明 | docs/configuration.md | 如何通过配置文件或环境变量调整超时、并发、日志级别与输出路径 |
| 数据模型 | docs/data-model.md | 链接条目在内存与磁盘中的存储结构、字段含义以及扩展字段预留方式 |
| 静态生成 | docs/building.md | 如何定制页面模板、修改排序规则以及添加自定义 CSS 样式 |
| 部署指南 | docs/deployment.md | 如何将生成的静态站点部署到 Nginx、Vercel 或 GitHub Pages 等平台 |
| 故障排查 | docs/troubleshooting.md | 常见网络错误、编码问题以及性能瓶颈的诊断与解决方案 |

## 资源列表

- http://m.mobile.puhvjy.cn/Article/1197848.shtml
- http://m.mobile.jnjpgf.cn/Article/61588.shtml
- http://m.mobile.jnjpgf.cn/Article/3940230.shtml
- http://m.mobile.cmcvrr.cn/Article/5742990.shtml
- http://m.mobile.nwbbyt.cn/Article/2936335.shtml
- http://m.mobile.cmcvrr.cn/Article/21213.shtml
- http://m.mobile.cmcvrr.cn/Article/12378.shtml
- http://m.mobile.puhvjy.cn/Article/2551293.shtml
- http://m.mobile.jnjpgf.cn/Article/5507408.shtml
- http://m.mobile.nwbbyt.cn/Article/97398.shtml
- http://m.mobile.nwbbyt.cn/Article/6784.shtml
- http://m.mobile.jnjpgf.cn/Article/0183.shtml
- http://m.mobile.cmcvrr.cn/Article/221398.shtml
- http://m.mobile.jnjpgf.cn/Article/66703.shtml
- http://m.mobile.puhvjy.cn/Article/88856.shtml
- http://m.mobile.nwbbyt.cn/Article/49228.shtml
- http://m.mobile.puhvjy.cn/Article/9458.shtml
- http://m.mobile.puhvjy.cn/Article/792613.shtml
- http://m.mobile.puhvjy.cn/Article/325896.shtml
- http://m.mobile.puhvjy.cn/Article/11177.shtml
- http://m.mobile.jnjpgf.cn/Article/8713.shtml
- http://m.mobile.cmcvrr.cn/Article/308712.shtml
- http://m.mobile.cmcvrr.cn/Article/3827408.shtml
- http://m.mobile.nwbbyt.cn/Article/948059.shtml
- http://m.mobile.puhvjy.cn/Article/7566.shtml
- http://m.mobile.jnjpgf.cn/Article/4812628.shtml
- http://m.mobile.puhvjy.cn/Article/35979.shtml
- http://m.mobile.puhvjy.cn/Article/9887654.shtml
- http://m.mobile.cmcvrr.cn/Article/640756.shtml
- http://m.mobile.jnjpgf.cn/Article/2453.shtml
- http://m.mobile.nwbbyt.cn/Article/5935807.shtml
- http://m.mobile.puhvjy.cn/Article/8563.shtml
- http://m.mobile.jnjpgf.cn/Article/1668516.shtml
- http://m.mobile.cmcvrr.cn/Article/0468.shtml
- http://m.mobile.nwbbyt.cn/Article/635824.shtml
- http://m.mobile.puhvjy.cn/Article/0832908.shtml
- http://m.mobile.cmcvrr.cn/Article/53928.shtml
- http://m.mobile.jnjpgf.cn/Article/01774.shtml
- http://m.mobile.cmcvrr.cn/Article/4683.shtml
- http://m.mobile.nwbbyt.cn/Article/304145.shtml
- http://m.mobile.cmcvrr.cn/Article/0652595.shtml
- http://m.mobile.nwbbyt.cn/Article/387442.shtml
- http://m.mobile.puhvjy.cn/Article/0947.shtml
- http://m.mobile.cmcvrr.cn/Article/1101100.shtml
- http://m.mobile.puhvjy.cn/Article/5973.shtml
- http://m.mobile.puhvjy.cn/Article/39446.shtml
- http://m.mobile.puhvjy.cn/Article/0161.shtml
- http://m.mobile.jnjpgf.cn/Article/57951.shtml
- http://m.mobile.nwbbyt.cn/Article/270913.shtml
- http://m.mobile.nwbbyt.cn/Article/8404.shtml
- http://m.mobile.nwbbyt.cn/Article/94812.shtml
- http://m.mobile.nwbbyt.cn/Article/236685.shtml
- http://m.mobile.puhvjy.cn/Article/8076410.shtml
- http://m.mobile.jnjpgf.cn/Article/56445.shtml
- http://m.mobile.jnjpgf.cn/Article/1264.shtml
- http://m.mobile.nwbbyt.cn/Article/0458127.shtml
- http://m.mobile.puhvjy.cn/Article/71443.shtml
- http://m.mobile.cmcvrr.cn/Article/515576.shtml
- http://m.mobile.cmcvrr.cn/Article/6520533.shtml
- http://m.mobile.jnjpgf.cn/Article/840163.shtml
- http://m.mobile.nwbbyt.cn/Article/95431.shtml
- http://m.mobile.jnjpgf.cn/Article/5063696.shtml
- http://m.mobile.puhvjy.cn/Article/339523.shtml
- http://m.mobile.nwbbyt.cn/Article/042719.shtml
- http://m.mobile.jnjpgf.cn/Article/4693.shtml
- http://m.mobile.nwbbyt.cn/Article/495995.shtml
- http://m.mobile.puhvjy.cn/Article/078133.shtml
- http://m.mobile.nwbbyt.cn/Article/6611.shtml
- http://m.mobile.nwbbyt.cn/Article/1640774.shtml
- http://m.mobile.nwbbyt.cn/Article/373700.shtml
- http://m.mobile.nwbbyt.cn/Article/6386.shtml
- http://m.mobile.cmcvrr.cn/Article/71770.shtml
- http://m.mobile.nwbbyt.cn/Article/0958764.shtml
- http://m.mobile.cmcvrr.cn/Article/3030534.shtml
- http://m.mobile.jnjpgf.cn/Article/06170.shtml
- http://m.mobile.puhvjy.cn/Article/6440.shtml
- http://m.mobile.cmcvrr.cn/Article/4985982.shtml
- http://m.mobile.cmcvrr.cn/Article/808257.shtml
- http://m.mobile.nwbbyt.cn/Article/379119.shtml
- http://m.mobile.puhvjy.cn/Article/42615.shtml
- http://m.mobile.nwbbyt.cn/Article/6226310.shtml
- http://m.mobile.nwbbyt.cn/Article/6799.shtml
- http://m.mobile.cmcvrr.cn/Article/60323.shtml
- http://m.mobile.jnjpgf.cn/Article/1119008.shtml
- http://m.mobile.puhvjy.cn/Article/8585005.shtml
- http://m.mobile.puhvjy.cn/Article/4456114.shtml
- http://m.mobile.puhvjy.cn/Article/957329.shtml
- http://m.mobile.cmcvrr.cn/Article/105827.shtml
- http://m.mobile.cmcvrr.cn/Article/66854.shtml
- http://m.mobile.cmcvrr.cn/Article/6767588.shtml
- http://m.mobile.puhvjy.cn/Article/7231827.shtml
- http://m.mobile.jnjpgf.cn/Article/99157.shtml
- http://m.mobile.jnjpgf.cn/Article/26470.shtml
- http://m.mobile.nwbbyt.cn/Article/5504.shtml
- http://m.mobile.nwbbyt.cn/Article/19533.shtml
- http://m.mobile.puhvjy.cn/Article/5420.shtml
- http://m.mobile.cmcvrr.cn/Article/96382.shtml
- http://m.mobile.cmcvrr.cn/Article/85209.shtml
- http://m.mobile.nwbbyt.cn/Article/890482.shtml
- http://m.mobile.jnjpgf.cn/Article/5569325.shtml
- http://m.mobile.jnjpgf.cn/Article/63859.shtml
- http://m.mobile.puhvjy.cn/Article/491025.shtml
- http://m.mobile.jnjpgf.cn/Article/4997.shtml
- http://m.mobile.puhvjy.cn/Article/7827.shtml
- http://m.mobile.puhvjy.cn/Article/8875.shtml
- http://m.mobile.cmcvrr.cn/Article/039617.shtml
- http://m.mobile.cmcvrr.cn/Article/8415902.shtml
- http://m.mobile.jnjpgf.cn/Article/2448644.shtml
- http://m.mobile.nwbbyt.cn/Article/653741.shtml
- http://m.mobile.jnjpgf.cn/Article/7621.shtml
- http://m.mobile.puhvjy.cn/Article/334578.shtml
- http://m.mobile.jnjpgf.cn/Article/616187.shtml
- http://m.mobile.nwbbyt.cn/Article/083987.shtml
- http://m.mobile.nwbbyt.cn/Article/11427.shtml
- http://m.mobile.nwbbyt.cn/Article/61320.shtml
- http://m.mobile.nwbbyt.cn/Article/6732.shtml
- http://m.mobile.puhvjy.cn/Article/128247.shtml
- http://m.mobile.cmcvrr.cn/Article/21953.shtml
- http://m.mobile.cmcvrr.cn/Article/754442.shtml
- http://m.mobile.jnjpgf.cn/Article/1697670.shtml
- http://m.mobile.nwbbyt.cn/Article/61102.shtml
- http://m.mobile.cmcvrr.cn/Article/497363.shtml
- http://m.mobile.nwbbyt.cn/Article/94809.shtml
- http://m.mobile.nwbbyt.cn/Article/57072.shtml
- http://m.mobile.puhvjy.cn/Article/5331392.shtml
- http://m.mobile.jnjpgf.cn/Article/98687.shtml
- http://m.mobile.jnjpgf.cn/Article/1596058.shtml
- http://m.mobile.jnjpgf.cn/Article/621985.shtml
- http://m.mobile.cmcvrr.cn/Article/63844.shtml
- http://m.mobile.cmcvrr.cn/Article/56245.shtml
- http://m.mobile.cmcvrr.cn/Article/60695.shtml
- http://m.mobile.nwbbyt.cn/Article/818705.shtml
- http://m.mobile.puhvjy.cn/Article/916920.shtml
- http://m.mobile.puhvjy.cn/Article/5047742.shtml
- http://m.mobile.jnjpgf.cn/Article/5621935.shtml
- http://m.mobile.cmcvrr.cn/Article/9970490.shtml
- http://m.mobile.jnjpgf.cn/Article/289151.shtml
- http://m.mobile.cmcvrr.cn/Article/32032.shtml
- http://m.mobile.jnjpgf.cn/Article/6756.shtml
- http://m.mobile.cmcvrr.cn/Article/52302.shtml
- http://m.mobile.cmcvrr.cn/Article/4458174.shtml
- http://m.mobile.puhvjy.cn/Article/010486.shtml
- http://m.mobile.jnjpgf.cn/Article/3119559.shtml
- http://m.mobile.jnjpgf.cn/Article/6959926.shtml
- http://m.mobile.nwbbyt.cn/Article/073989.shtml
- http://m.mobile.cmcvrr.cn/Article/927186.shtml
- http://m.mobile.cmcvrr.cn/Article/1486.shtml
- http://m.mobile.puhvjy.cn/Article/38918.shtml
- http://m.mobile.cmcvrr.cn/Article/5808310.shtml
- http://m.mobile.puhvjy.cn/Article/8150752.shtml
- http://m.mobile.puhvjy.cn/Article/7531.shtml
- http://m.mobile.nwbbyt.cn/Article/0295.shtml
- http://m.mobile.puhvjy.cn/Article/1810.shtml
- http://m.mobile.jnjpgf.cn/Article/7567950.shtml
- http://m.mobile.nwbbyt.cn/Article/1084.shtml
- http://m.mobile.nwbbyt.cn/Article/8015.shtml
- http://m.mobile.cmcvrr.cn/Article/0474692.shtml
- http://m.mobile.jnjpgf.cn/Article/158640.shtml
- http://m.mobile.cmcvrr.cn/Article/9262939.shtml
- http://m.mobile.cmcvrr.cn/Article/3387773.shtml
- http://m.mobile.puhvjy.cn/Article/80212.shtml
- http://m.mobile.puhvjy.cn/Article/15558.shtml
- http://m.mobile.nwbbyt.cn/Article/5465947.shtml
- http://m.mobile.nwbbyt.cn/Article/27793.shtml
- http://m.mobile.cmcvrr.cn/Article/307916.shtml
- http://m.mobile.nwbbyt.cn/Article/162038.shtml
- http://m.mobile.puhvjy.cn/Article/739668.shtml
- http://m.mobile.puhvjy.cn/Article/3162191.shtml
- http://m.mobile.puhvjy.cn/Article/55907.shtml
- http://m.mobile.cmcvrr.cn/Article/2107292.shtml
- http://m.mobile.nwbbyt.cn/Article/2802816.shtml
- http://m.mobile.puhvjy.cn/Article/8808.shtml
- http://m.mobile.puhvjy.cn/Article/912708.shtml
- http://m.mobile.jnjpgf.cn/Article/9641.shtml
- http://m.mobile.jnjpgf.cn/Article/457743.shtml
- http://m.mobile.nwbbyt.cn/Article/1482.shtml
- http://m.mobile.cmcvrr.cn/Article/7535058.shtml
- http://m.mobile.puhvjy.cn/Article/950261.shtml
- http://m.mobile.nwbbyt.cn/Article/804446.shtml
- http://m.mobile.nwbbyt.cn/Article/8553.shtml
- http://m.mobile.cmcvrr.cn/Article/9654679.shtml
- http://m.mobile.cmcvrr.cn/Article/616172.shtml
- http://m.mobile.cmcvrr.cn/Article/8593.shtml
- http://m.mobile.nwbbyt.cn/Article/176216.shtml
- http://m.mobile.jnjpgf.cn/Article/3137.shtml
- http://m.mobile.cmcvrr.cn/Article/617787.shtml
- http://m.mobile.jnjpgf.cn/Article/190650.shtml
- http://m.mobile.jnjpgf.cn/Article/9327819.shtml
- http://m.mobile.jnjpgf.cn/Article/2598069.shtml
- http://m.mobile.puhvjy.cn/Article/96433.shtml
- http://m.mobile.jnjpgf.cn/Article/363042.shtml
- http://m.mobile.nwbbyt.cn/Article/382230.shtml
- http://m.mobile.puhvjy.cn/Article/594128.shtml
- http://m.mobile.puhvjy.cn/Article/5894.shtml
- http://m.mobile.puhvjy.cn/Article/76013.shtml
- http://m.mobile.puhvjy.cn/Article/29362.shtml
- http://m.mobile.jnjpgf.cn/Article/4908.shtml
- http://m.mobile.puhvjy.cn/Article/4577.shtml
- http://m.mobile.cmcvrr.cn/Article/4651971.shtml
- http://m.mobile.nwbbyt.cn/Article/98988.shtml
- http://m.mobile.cmcvrr.cn/Article/9302.shtml
- http://m.mobile.jnjpgf.cn/Article/21215.shtml
- http://m.mobile.puhvjy.cn/Article/4721.shtml
- http://m.mobile.cmcvrr.cn/Article/624349.shtml
- http://m.mobile.puhvjy.cn/Article/0694.shtml
- http://m.mobile.cmcvrr.cn/Article/799740.shtml
- http://m.mobile.nwbbyt.cn/Article/3565584.shtml
- http://m.mobile.nwbbyt.cn/Article/243840.shtml
- http://m.mobile.nwbbyt.cn/Article/933114.shtml
- http://m.mobile.cmcvrr.cn/Article/21814.shtml
- http://m.mobile.puhvjy.cn/Article/4449.shtml
- http://m.mobile.cmcvrr.cn/Article/1451.shtml
- http://m.mobile.jnjpgf.cn/Article/2917.shtml
- http://m.mobile.cmcvrr.cn/Article/3682.shtml
- http://m.mobile.cmcvrr.cn/Article/879099.shtml
- http://m.mobile.nwbbyt.cn/Article/1339.shtml
- http://m.mobile.jnjpgf.cn/Article/8657884.shtml
- http://m.mobile.nwbbyt.cn/Article/5546277.shtml
- http://m.mobile.jnjpgf.cn/Article/1051981.shtml
- http://m.mobile.jnjpgf.cn/Article/873664.shtml
- http://m.mobile.nwbbyt.cn/Article/59702.shtml
- http://m.mobile.nwbbyt.cn/Article/8666057.shtml
- http://m.mobile.puhvjy.cn/Article/4380.shtml
- http://m.mobile.jnjpgf.cn/Article/381565.shtml
- http://m.mobile.jnjpgf.cn/Article/30549.shtml
- http://m.mobile.jnjpgf.cn/Article/6522759.shtml
- http://m.mobile.puhvjy.cn/Article/567715.shtml
- http://m.mobile.jnjpgf.cn/Article/0590.shtml
- http://m.mobile.jnjpgf.cn/Article/4957.shtml
- http://m.mobile.puhvjy.cn/Article/397873.shtml
- http://m.mobile.jnjpgf.cn/Article/072825.shtml
- http://m.mobile.nwbbyt.cn/Article/7037.shtml
- http://m.mobile.jnjpgf.cn/Article/862423.shtml
- http://m.mobile.cmcvrr.cn/Article/2972531.shtml
- http://m.mobile.jnjpgf.cn/Article/073570.shtml
- http://m.mobile.cmcvrr.cn/Article/3845.shtml
- http://m.mobile.puhvjy.cn/Article/52996.shtml
- http://m.mobile.nwbbyt.cn/Article/42301.shtml
- http://m.mobile.puhvjy.cn/Article/1025.shtml
- http://m.mobile.cmcvrr.cn/Article/8365.shtml
- http://m.mobile.nwbbyt.cn/Article/4879904.shtml
- http://m.mobile.cmcvrr.cn/Article/7974672.shtml
- http://m.mobile.cmcvrr.cn/Article/072776.shtml
- http://m.mobile.nwbbyt.cn/Article/1378661.shtml
- http://m.mobile.nwbbyt.cn/Article/08645.shtml
- http://m.mobile.jnjpgf.cn/Article/440496.shtml
- http://m.mobile.cmcvrr.cn/Article/7708.shtml
- http://m.mobile.puhvjy.cn/Article/5103.shtml
- http://m.mobile.cmcvrr.cn/Article/5440264.shtml
- http://m.mobile.nwbbyt.cn/Article/2372.shtml

## 项目结构

项目采用分层架构，将数据存储、业务逻辑、命令行接口与视图生成四部分解耦，便于单元测试与功能扩展。

```
mobilelink/
├── mobilelink.py                # CLI 入口，定义 click 命令组及上下文配置
├── requirements.txt             # 生产环境依赖列表，锁定主要版本号
├── setup.py                     # 项目打包与安装配置，声明 entry_points 控制台脚本
├── .gitignore                   # 忽略虚拟环境、缓存文件与临时输出目录
├── data/                        # 数据存储层，默认使用 SQLite 存放链接台账
│   ├── links.db                 # SQLite 数据库文件，包含 urls 与 domains 两张表
│   └── migrations/              # 数据库版本迁移脚本，使用手工 SQL 管理
│       ├── 001_initial_schema.sql
│       └── 002_add_meta_fields.sql
├── mobilelink/                  # 核心业务逻辑包
│   ├── __init__.py              # 包版本号与导出符号声明
│   ├── importer.py              # 链接导入模块：支持 txt、csv 与 stdin 解析
│   ├── checker.py               # 异步链接检测模块：aiohttp 会话池与重试策略
│   ├── extractor.py             # 元数据提取模块：BeautifulSoup 标题与编码解析
│   ├── deduper.py               # 去重模块：基于 URL 归一化与路径相似度算法
│   ├── exporter.py              # 导出模块：支持 json、csv、markdown 与 plain 格式
│   ├── builder.py               # 静态站点生成模块：Jinja2 模板渲染与分页逻辑
│   └── models.py                # 数据模型定义：Link 与 Domain 的 dataclass 与 ORM 映射
├── templates/                   # 静态页面模板目录
│   ├── base.html                # 基础 HTML 骨架，包含 CSS 框架引用
│   ├── index.html               # 链接列表页模板，含筛选表单与分页控件
│   └── detail.html              # 单条链接详情页模板（预留）
├── tests/                       # 单元测试目录，使用 pytest 框架
│   ├── test_importer.py         # 导入模块测试用例
│   ├── test_checker.py          # 检测模块模拟响应测试
│   ├── test_deduper.py          # 去重算法边界条件测试
│   └── fixtures/                # 测试用固定数据，包含示例 URL 列表与模拟 HTML
│       ├── sample_urls.txt
│       └── mock_response.html
├── docs/                        # 完整文档目录，与文档导航章节对应
│   ├── getting-started.md
│   ├── commands.md
│   ├── configuration.md
│   ├── data-model.md
│   ├── building.md
│   ├── deployment.md
│   └── troubleshooting.md
└── output/                      # 默认输出目录，存放生成的静态 HTML 页面与导出文件
    ├── index.html
    ├── links.json
    ├── links.csv
    └── report.md
```

## 贡献指南

本项目欢迎外部贡献者提交改进建议、功能扩展与缺陷修复。所有贡献需遵循以下流程：

1. 在 GitHub 仓库中 fork 项目到个人账号，并克隆到本地开发环境。创建新分支时请使用 feature/ 或 fix/ 前缀，并附上简短描述，例如 feature/support-ftp-import。

2. 编写代码或文档变更后，请确保所有现有单元测试通过，并为新增功能补充对应的测试用例。测试覆盖率不得低于 85%。运行 pytest 命令执行全部测试套件。

3. 更新 docs/ 目录下的相关文档，确保命令行参数、配置项与使用示例与代码实现保持一致。对于破坏性变更，需在文档中明确标注迁移指南。

4. 提交前使用 black 与 flake8 对 Python 代码进行格式化与静态检查，保证代码风格符合 PEP 8 标准。提交信息遵循 Conventional Commits 规范，使用 feat:、fix:、docs:、refactor: 等类型前缀。

5. 向原仓库发起 Pull Request，并在描述中关联对应的 Issue 编号（如有）。维护者将在三个工作日内进行代码审查，给出合并或修改意见。

## 常见问题

Q：导入的链接数量很大（超过一万条）时，内存占用和检测速度如何优化？

A：建议分批次导入，每批次不超过 2000 条。检测时可通过 --concurrency 参数控制并发数，默认 10，可根据网络带宽与目标服务器承受能力适当调低或调高。对于超大规模场景，推荐使用 --no-extract 关闭元数据提取，仅做状态码检测，可显著降低 CPU 与内存开销。

Q：生成的静态页面在移动设备上显示错乱，如何调整？

A：请检查 templates/base.html 中是否包含 viewport meta 标签。项目默认模板已适配移动端，若自定义后出现问题，可恢复默认模板或修改 CSS 媒体查询断点。建议使用浏览器的开发者工具模拟移动设备进行调试。

Q：链接检测返回大量超时或连接拒绝错误，如何排查？

A：首先确认目标网站是否允许来自当前 IP 的访问，部分站点可能对非移动端 User-Agent 或高频请求进行限制。可在配置文件中设置 CHECK_USER_AGENT 为移动端 UA 字符串，并适当增加 CHECK_TIMEOUT 与 CHECK_RETRY 参数。若问题持续，请使用 curl 或 wget 手动测试单条链接以排除网络环境因素。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
