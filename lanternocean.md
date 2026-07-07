# MobileLink 聚合网关

MobileLink 聚合网关是一个面向移动端内容聚合与分发场景的轻量级链接管理中间件。该项目定位于技术内容运营团队、个人站长及移动端应用开发者，用于对分散于多个移动域名下的文章资源进行统一收录、分类索引与结构化导出。MobileLink 不提供内容生产功能，而是作为外链资源的规范化整理工具，帮助用户从大量无结构的移动文章链接中提取可维护的元信息，并生成标准化的资源清单供下游系统使用。

MobileLink 的核心设计原则为“只做链接的搬运工与整理员”，不涉及爬虫、不存储文章全文、不修改原始资源内容。项目内置基于 URL 模式的自动归类引擎，支持对 m.mobile.* 类域名进行站点归属识别、文章 ID 提取与批次标记，适用于第 13/80 批共 250 条移动文章链接的批量处理场景。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动过滤重复项与无效协议。

**域名归属识别** 内置域名映射表，自动识别 cmcvrr、nwbbyt、jnjpgf、puhvjy 四个移动子站域名的文章链接。

**文章 ID 提取** 从 URL 路径中正则提取 Article 后的数字编号，支持 3 至 8 位不等的 ID 长度。

**批次标记与追踪** 每个链接可标记所属批次（如 13/80），支持按批次号筛选与导出，便于多批次项目管理。

**结构化导出** 支持将链接列表导出为 Markdown 列表、JSON 数组或纯文本行三种格式，适配不同的下游文档生成需求。

**链接校验与状态检查** 提供可选的 HTTP HEAD 请求校验，检查链接是否可访问并记录状态码，用于定期清理失效资源。

**标签分类与备注** 允许用户为每条链接添加自定义标签（如“技术文章”“行业报告”）和备注说明，增强可维护性。

**搜索与过滤** 支持按域名、文章 ID 范围、批次号、标签等多维度组合过滤，快速定位特定链接。

## 应用场景

移动内容运营团队在整理每周资讯汇总时，编辑人员从多个移动端内容源收集到大量文章链接，这些链接分散在不同的域名下且缺乏统一管理。使用 MobileLink 可以将这批链接一次性导入，自动按域名归类并生成一份结构化的 Markdown 链接清单，直接用于对外发布的内容导航页。

个人技术博客作者在撰写“每周好文推荐”系列文章时，需要从移动端阅读应用中收藏大量参考链接。通过 MobileLink 的批次标记功能，作者可以为每一期推荐创建一个独立批次，导入链接后添加阅读笔记标签，最终导出为带有注释的链接列表，方便直接粘贴到博客文章中。

小型技术团队在搭建内部知识库时，需要将团队文档、外部参考文章、技术规范等各类链接资源集中管理。MobileLink 提供统一的链接录入入口，支持多人协作维护标签分类，导出为 JSON 格式后可被其他内部系统（如 Confluence、Notion API）二次加工使用。

开发者在进行移动端应用内“推荐阅读”模块的链接配置时，需要从运营人员提供的原始链接列表中筛选特定域名的文章。MobileLink 的过滤与导出功能可以快速按域名提取链接子集，并输出为应用配置文件所需的数组格式，减少手动复制出错。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-org/mobilelink-gateway.git

# 进入项目目录
cd mobilelink-gateway

# 安装依赖（基于 Python 3.10+，使用 pip 安装）
pip install -r requirements.txt

# 运行链接导入与导出示例（以第 13/80 批数据为例）
python cli.py import --batch 13 --file ./data/links_13_80.txt --export markdown --output ./output/links_13_80.md
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.10 及以上 | 核心运行环境，建议使用 3.11 长期支持版本 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| requests | 2.28.0 及以上 | 用于可选的 HTTP 链接状态校验功能 |
| pydantic | 2.0.0 及以上 | 数据模型校验与配置管理 |
| pyyaml | 6.0 及以上 | 用于 YAML 格式的配置文件解析与导出 |
| click | 8.1.0 及以上 | 命令行界面交互框架 |
| pytest | 7.0.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |
| black | 23.0.0 及以上 | 代码格式化工具（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何导入链接、如何按域名过滤、如何导出不同格式的链接清单 |
| 配置参考 | docs/configuration.md | 支持哪些配置项、域名映射表如何自定义、批次号命名规则 |
| API 接口 | docs/api_reference.md | 内部模块提供了哪些函数、Link 数据模型字段定义、校验器方法说明 |
| 部署指南 | docs/deployment.md | 项目如何部署到生产环境、依赖安装优化、日志与监控配置建议 |
| 开发指引 | docs/development.md | 如何扩展新的域名识别规则、如何添加自定义导出格式、测试用例编写规范 |

## 资源列表

- http://m.mobile.cmcvrr.cn/Article/3313282.shtml
- http://m.mobile.nwbbyt.cn/Article/5005.shtml
- http://m.mobile.nwbbyt.cn/Article/9812.shtml
- http://m.mobile.cmcvrr.cn/Article/4608853.shtml
- http://m.mobile.nwbbyt.cn/Article/6175409.shtml
- http://m.mobile.nwbbyt.cn/Article/0148.shtml
- http://m.mobile.jnjpgf.cn/Article/6290311.shtml
- http://m.mobile.puhvjy.cn/Article/0215689.shtml
- http://m.mobile.cmcvrr.cn/Article/8134.shtml
- http://m.mobile.puhvjy.cn/Article/299899.shtml
- http://m.mobile.nwbbyt.cn/Article/897244.shtml
- http://m.mobile.cmcvrr.cn/Article/94708.shtml
- http://m.mobile.cmcvrr.cn/Article/141609.shtml
- http://m.mobile.puhvjy.cn/Article/816374.shtml
- http://m.mobile.puhvjy.cn/Article/0243.shtml
- http://m.mobile.jnjpgf.cn/Article/54742.shtml
- http://m.mobile.puhvjy.cn/Article/4523.shtml
- http://m.mobile.cmcvrr.cn/Article/1335.shtml
- http://m.mobile.nwbbyt.cn/Article/23907.shtml
- http://m.mobile.cmcvrr.cn/Article/7763805.shtml
- http://m.mobile.jnjpgf.cn/Article/6437525.shtml
- http://m.mobile.cmcvrr.cn/Article/037327.shtml
- http://m.mobile.jnjpgf.cn/Article/16062.shtml
- http://m.mobile.nwbbyt.cn/Article/4159349.shtml
- http://m.mobile.cmcvrr.cn/Article/27699.shtml
- http://m.mobile.jnjpgf.cn/Article/2593257.shtml
- http://m.mobile.cmcvrr.cn/Article/3182.shtml
- http://m.mobile.jnjpgf.cn/Article/25049.shtml
- http://m.mobile.cmcvrr.cn/Article/7028050.shtml
- http://m.mobile.puhvjy.cn/Article/67172.shtml
- http://m.mobile.jnjpgf.cn/Article/285673.shtml
- http://m.mobile.puhvjy.cn/Article/718188.shtml
- http://m.mobile.cmcvrr.cn/Article/1918.shtml
- http://m.mobile.puhvjy.cn/Article/4684090.shtml
- http://m.mobile.nwbbyt.cn/Article/9435036.shtml
- http://m.mobile.puhvjy.cn/Article/9869183.shtml
- http://m.mobile.jnjpgf.cn/Article/163636.shtml
- http://m.mobile.nwbbyt.cn/Article/4495.shtml
- http://m.mobile.puhvjy.cn/Article/50580.shtml
- http://m.mobile.nwbbyt.cn/Article/226684.shtml
- http://m.mobile.jnjpgf.cn/Article/1507491.shtml
- http://m.mobile.nwbbyt.cn/Article/91778.shtml
- http://m.mobile.cmcvrr.cn/Article/8410171.shtml
- http://m.mobile.cmcvrr.cn/Article/6540512.shtml
- http://m.mobile.puhvjy.cn/Article/677632.shtml
- http://m.mobile.jnjpgf.cn/Article/64169.shtml
- http://m.mobile.cmcvrr.cn/Article/7068.shtml
- http://m.mobile.puhvjy.cn/Article/5494.shtml
- http://m.mobile.nwbbyt.cn/Article/10120.shtml
- http://m.mobile.jnjpgf.cn/Article/0926160.shtml
- http://m.mobile.jnjpgf.cn/Article/237961.shtml
- http://m.mobile.cmcvrr.cn/Article/3742327.shtml
- http://m.mobile.puhvjy.cn/Article/1801.shtml
- http://m.mobile.cmcvrr.cn/Article/9249390.shtml
- http://m.mobile.jnjpgf.cn/Article/889485.shtml
- http://m.mobile.nwbbyt.cn/Article/523179.shtml
- http://m.mobile.nwbbyt.cn/Article/64853.shtml
- http://m.mobile.nwbbyt.cn/Article/0413435.shtml
- http://m.mobile.puhvjy.cn/Article/93276.shtml
- http://m.mobile.cmcvrr.cn/Article/2260.shtml
- http://m.mobile.jnjpgf.cn/Article/046680.shtml
- http://m.mobile.cmcvrr.cn/Article/1471591.shtml
- http://m.mobile.jnjpgf.cn/Article/2750273.shtml
- http://m.mobile.puhvjy.cn/Article/9814442.shtml
- http://m.mobile.jnjpgf.cn/Article/4469083.shtml
- http://m.mobile.cmcvrr.cn/Article/6065.shtml
- http://m.mobile.cmcvrr.cn/Article/216442.shtml
- http://m.mobile.cmcvrr.cn/Article/2631.shtml
- http://m.mobile.cmcvrr.cn/Article/3339897.shtml
- http://m.mobile.cmcvrr.cn/Article/117352.shtml
- http://m.mobile.nwbbyt.cn/Article/99035.shtml
- http://m.mobile.nwbbyt.cn/Article/0247.shtml
- http://m.mobile.cmcvrr.cn/Article/00170.shtml
- http://m.mobile.nwbbyt.cn/Article/12942.shtml
- http://m.mobile.cmcvrr.cn/Article/4493532.shtml
- http://m.mobile.jnjpgf.cn/Article/754111.shtml
- http://m.mobile.nwbbyt.cn/Article/493772.shtml
- http://m.mobile.cmcvrr.cn/Article/53015.shtml
- http://m.mobile.nwbbyt.cn/Article/6574595.shtml
- http://m.mobile.jnjpgf.cn/Article/76866.shtml
- http://m.mobile.cmcvrr.cn/Article/6439087.shtml
- http://m.mobile.nwbbyt.cn/Article/5917704.shtml
- http://m.mobile.cmcvrr.cn/Article/39544.shtml
- http://m.mobile.nwbbyt.cn/Article/3886293.shtml
- http://m.mobile.jnjpgf.cn/Article/4830.shtml
- http://m.mobile.cmcvrr.cn/Article/6150409.shtml
- http://m.mobile.nwbbyt.cn/Article/9502675.shtml
- http://m.mobile.puhvjy.cn/Article/105916.shtml
- http://m.mobile.puhvjy.cn/Article/4379.shtml
- http://m.mobile.puhvjy.cn/Article/8065594.shtml
- http://m.mobile.jnjpgf.cn/Article/5122.shtml
- http://m.mobile.nwbbyt.cn/Article/4906.shtml
- http://m.mobile.puhvjy.cn/Article/6651981.shtml
- http://m.mobile.jnjpgf.cn/Article/4740.shtml
- http://m.mobile.cmcvrr.cn/Article/9784386.shtml
- http://m.mobile.puhvjy.cn/Article/192066.shtml
- http://m.mobile.cmcvrr.cn/Article/061145.shtml
- http://m.mobile.puhvjy.cn/Article/86235.shtml
- http://m.mobile.jnjpgf.cn/Article/99197.shtml
- http://m.mobile.cmcvrr.cn/Article/0237196.shtml
- http://m.mobile.nwbbyt.cn/Article/827951.shtml
- http://m.mobile.puhvjy.cn/Article/8953689.shtml
- http://m.mobile.puhvjy.cn/Article/9201770.shtml
- http://m.mobile.cmcvrr.cn/Article/5155.shtml
- http://m.mobile.nwbbyt.cn/Article/76625.shtml
- http://m.mobile.cmcvrr.cn/Article/8337371.shtml
- http://m.mobile.nwbbyt.cn/Article/4774594.shtml
- http://m.mobile.cmcvrr.cn/Article/8004838.shtml
- http://m.mobile.nwbbyt.cn/Article/9869203.shtml
- http://m.mobile.puhvjy.cn/Article/431834.shtml
- http://m.mobile.jnjpgf.cn/Article/79346.shtml
- http://m.mobile.jnjpgf.cn/Article/5404284.shtml
- http://m.mobile.puhvjy.cn/Article/75746.shtml
- http://m.mobile.nwbbyt.cn/Article/3157.shtml
- http://m.mobile.puhvjy.cn/Article/429350.shtml
- http://m.mobile.cmcvrr.cn/Article/20579.shtml
- http://m.mobile.nwbbyt.cn/Article/1885205.shtml
- http://m.mobile.puhvjy.cn/Article/641135.shtml
- http://m.mobile.nwbbyt.cn/Article/21049.shtml
- http://m.mobile.jnjpgf.cn/Article/3459.shtml
- http://m.mobile.nwbbyt.cn/Article/57861.shtml
- http://m.mobile.jnjpgf.cn/Article/633359.shtml
- http://m.mobile.puhvjy.cn/Article/2004526.shtml
- http://m.mobile.nwbbyt.cn/Article/7425136.shtml
- http://m.mobile.jnjpgf.cn/Article/030140.shtml
- http://m.mobile.jnjpgf.cn/Article/05753.shtml
- http://m.mobile.jnjpgf.cn/Article/036842.shtml
- http://m.mobile.nwbbyt.cn/Article/9258613.shtml
- http://m.mobile.puhvjy.cn/Article/8664.shtml
- http://m.mobile.puhvjy.cn/Article/1702.shtml
- http://m.mobile.cmcvrr.cn/Article/804491.shtml
- http://m.mobile.jnjpgf.cn/Article/68014.shtml
- http://m.mobile.cmcvrr.cn/Article/763779.shtml
- http://m.mobile.jnjpgf.cn/Article/9643.shtml
- http://m.mobile.cmcvrr.cn/Article/481108.shtml
- http://m.mobile.cmcvrr.cn/Article/5024.shtml
- http://m.mobile.jnjpgf.cn/Article/773689.shtml
- http://m.mobile.jnjpgf.cn/Article/024851.shtml
- http://m.mobile.nwbbyt.cn/Article/46075.shtml
- http://m.mobile.cmcvrr.cn/Article/11591.shtml
- http://m.mobile.jnjpgf.cn/Article/0534364.shtml
- http://m.mobile.jnjpgf.cn/Article/02315.shtml
- http://m.mobile.nwbbyt.cn/Article/899467.shtml
- http://m.mobile.nwbbyt.cn/Article/2202034.shtml
- http://m.mobile.jnjpgf.cn/Article/1750.shtml
- http://m.mobile.jnjpgf.cn/Article/261161.shtml
- http://m.mobile.puhvjy.cn/Article/1540.shtml
- http://m.mobile.nwbbyt.cn/Article/58239.shtml
- http://m.mobile.jnjpgf.cn/Article/029847.shtml
- http://m.mobile.cmcvrr.cn/Article/4619.shtml
- http://m.mobile.puhvjy.cn/Article/33551.shtml
- http://m.mobile.cmcvrr.cn/Article/8044.shtml
- http://m.mobile.jnjpgf.cn/Article/056759.shtml
- http://m.mobile.nwbbyt.cn/Article/1572215.shtml
- http://m.mobile.cmcvrr.cn/Article/24184.shtml
- http://m.mobile.nwbbyt.cn/Article/8520318.shtml
- http://m.mobile.puhvjy.cn/Article/52112.shtml
- http://m.mobile.jnjpgf.cn/Article/6617440.shtml
- http://m.mobile.jnjpgf.cn/Article/390833.shtml
- http://m.mobile.puhvjy.cn/Article/2457112.shtml
- http://m.mobile.cmcvrr.cn/Article/9469269.shtml
- http://m.mobile.cmcvrr.cn/Article/8412.shtml
- http://m.mobile.puhvjy.cn/Article/31017.shtml
- http://m.mobile.cmcvrr.cn/Article/5352462.shtml
- http://m.mobile.jnjpgf.cn/Article/96732.shtml
- http://m.mobile.cmcvrr.cn/Article/2182.shtml
- http://m.mobile.puhvjy.cn/Article/582182.shtml
- http://m.mobile.puhvjy.cn/Article/45288.shtml
- http://m.mobile.puhvjy.cn/Article/02935.shtml
- http://m.mobile.jnjpgf.cn/Article/7603688.shtml
- http://m.mobile.nwbbyt.cn/Article/81306.shtml
- http://m.mobile.nwbbyt.cn/Article/2868846.shtml
- http://m.mobile.nwbbyt.cn/Article/298837.shtml
- http://m.mobile.nwbbyt.cn/Article/5307117.shtml
- http://m.mobile.jnjpgf.cn/Article/73132.shtml
- http://m.mobile.nwbbyt.cn/Article/2991.shtml
- http://m.mobile.jnjpgf.cn/Article/0990.shtml
- http://m.mobile.nwbbyt.cn/Article/7109.shtml
- http://m.mobile.nwbbyt.cn/Article/0366.shtml
- http://m.mobile.cmcvrr.cn/Article/5395.shtml
- http://m.mobile.nwbbyt.cn/Article/714958.shtml
- http://m.mobile.cmcvrr.cn/Article/612029.shtml
- http://m.mobile.cmcvrr.cn/Article/8799.shtml
- http://m.mobile.jnjpgf.cn/Article/25448.shtml
- http://m.mobile.jnjpgf.cn/Article/11121.shtml
- http://m.mobile.nwbbyt.cn/Article/87506.shtml
- http://m.mobile.puhvjy.cn/Article/51452.shtml
- http://m.mobile.puhvjy.cn/Article/233327.shtml
- http://m.mobile.jnjpgf.cn/Article/4854.shtml
- http://m.mobile.puhvjy.cn/Article/83750.shtml
- http://m.mobile.jnjpgf.cn/Article/78248.shtml
- http://m.mobile.jnjpgf.cn/Article/4158338.shtml
- http://m.mobile.puhvjy.cn/Article/30986.shtml
- http://m.mobile.puhvjy.cn/Article/57956.shtml
- http://m.mobile.puhvjy.cn/Article/544925.shtml
- http://m.mobile.cmcvrr.cn/Article/7259411.shtml
- http://m.mobile.jnjpgf.cn/Article/61863.shtml
- http://m.mobile.cmcvrr.cn/Article/89877.shtml
- http://m.mobile.jnjpgf.cn/Article/3640.shtml
- http://m.mobile.nwbbyt.cn/Article/6197387.shtml
- http://m.mobile.puhvjy.cn/Article/981642.shtml
- http://m.mobile.jnjpgf.cn/Article/1079024.shtml
- http://m.mobile.cmcvrr.cn/Article/21946.shtml
- http://m.mobile.puhvjy.cn/Article/292490.shtml
- http://m.mobile.cmcvrr.cn/Article/608273.shtml
- http://m.mobile.nwbbyt.cn/Article/65389.shtml
- http://m.mobile.jnjpgf.cn/Article/774780.shtml
- http://m.mobile.cmcvrr.cn/Article/0947177.shtml
- http://m.mobile.cmcvrr.cn/Article/060837.shtml
- http://m.mobile.cmcvrr.cn/Article/80692.shtml
- http://m.mobile.nwbbyt.cn/Article/79729.shtml
- http://m.mobile.puhvjy.cn/Article/4386.shtml
- http://m.mobile.puhvjy.cn/Article/761546.shtml
- http://m.mobile.puhvjy.cn/Article/4867.shtml
- http://m.mobile.jnjpgf.cn/Article/15025.shtml
- http://m.mobile.nwbbyt.cn/Article/45597.shtml
- http://m.mobile.cmcvrr.cn/Article/4521.shtml
- http://m.mobile.nwbbyt.cn/Article/420490.shtml
- http://m.mobile.puhvjy.cn/Article/1616.shtml
- http://m.mobile.cmcvrr.cn/Article/105450.shtml
- http://m.mobile.nwbbyt.cn/Article/67809.shtml
- http://m.mobile.nwbbyt.cn/Article/6369.shtml
- http://m.mobile.puhvjy.cn/Article/4564.shtml
- http://m.mobile.nwbbyt.cn/Article/1370812.shtml
- http://m.mobile.cmcvrr.cn/Article/0227989.shtml
- http://m.mobile.cmcvrr.cn/Article/45861.shtml
- http://m.mobile.nwbbyt.cn/Article/09462.shtml
- http://m.mobile.nwbbyt.cn/Article/0918536.shtml
- http://m.mobile.puhvjy.cn/Article/2949546.shtml
- http://m.mobile.cmcvrr.cn/Article/85920.shtml
- http://m.mobile.cmcvrr.cn/Article/2403386.shtml
- http://m.mobile.nwbbyt.cn/Article/53430.shtml
- http://m.mobile.jnjpgf.cn/Article/6505.shtml
- http://m.mobile.cmcvrr.cn/Article/53001.shtml
- http://m.mobile.jnjpgf.cn/Article/4279.shtml
- http://m.mobile.nwbbyt.cn/Article/199821.shtml
- http://m.mobile.nwbbyt.cn/Article/5253.shtml
- http://m.mobile.jnjpgf.cn/Article/5294.shtml
- http://m.mobile.jnjpgf.cn/Article/672762.shtml
- http://m.mobile.cmcvrr.cn/Article/51214.shtml
- http://m.mobile.puhvjy.cn/Article/7358.shtml
- http://m.mobile.cmcvrr.cn/Article/8775.shtml
- http://m.mobile.puhvjy.cn/Article/127353.shtml
- http://m.mobile.puhvjy.cn/Article/10936.shtml
- http://m.mobile.cmcvrr.cn/Article/4663.shtml
- http://m.mobile.cmcvrr.cn/Article/6009.shtml
- http://m.mobile.cmcvrr.cn/Article/547775.shtml
- http://m.mobile.nwbbyt.cn/Article/7434.shtml
- http://m.mobile.jnjpgf.cn/Article/42454.shtml
- http://m.mobile.cmcvrr.cn/Article/2102.shtml

## 项目结构

```
mobilelink-gateway/
├── cli.py                  # 命令行入口，注册 import/export/filter 子命令
├── config.yaml             # 主配置文件，包含域名映射表、默认导出格式、批次号定义
├── requirements.txt        # 生产环境依赖列表
├── src/                    # 核心源码目录
│   ├── __init__.py
│   ├── importer.py         # 链接导入模块，支持 txt/csv/json 格式解析
│   ├── exporter.py         # 导出模块，支持 markdown/json/text 三种输出格式
│   ├── validator.py        # 链接校验模块，包含 URL 正则匹配与 HTTP 状态检查
│   ├── models.py           # Pydantic 数据模型定义（Link、Batch、DomainMap）
│   └── filters.py          # 过滤器实现，按域名/ID/批次/标签组合筛选
├── data/                   # 数据存储目录
│   ├── raw/                # 原始导入文件存放位置
│   ├── processed/          # 处理后的中间数据缓存
│   └── output/             # 导出文件输出目录
├── tests/                  # 单元测试目录
│   ├── test_importer.py
│   ├── test_exporter.py
│   ├── test_validator.py
│   └── fixtures/           # 测试用固定数据集
├── docs/                   # 文档目录
│   ├── user_guide.md
│   ├── configuration.md
│   ├── api_reference.md
│   ├── deployment.md
│   └── development.md
└── scripts/                # 运维辅助脚本
    ├── batch_import.sh     # 批量导入快捷脚本
    └── validate_all.sh     # 全量链接校验脚本
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。创建新分支时请使用 `feature/` 或 `fix/` 前缀，并附上简短描述，例如 `feature/support-csv-export`。

2. 编写或修改代码后，确保所有现有单元测试通过，并为新增功能补充对应的测试用例。测试文件位于 `tests/` 目录，使用 pytest 框架运行。

3. 代码风格遵循 PEP 8 规范，提交前使用 black 和 isort 进行自动格式化。提交信息采用约定式提交格式：`<type>(<scope>): <subject>`，其中 type 包括 feat、fix、docs、refactor、test 等。

4. 若新增域名识别规则，请在 `config.yaml` 的 domain_mapping 表中添加对应条目，并在 `docs/configuration.md` 中同步更新配置说明。

5. 提交 Pull Request 至主仓库的 main 分支，在 PR 描述中清晰说明改动目的、影响范围以及测试结果。PR 需要至少一位维护者审核通过后方可合并。

## 常见问题

Q: 导入链接时提示“无效的 URL 格式”，但我的链接看起来是正常的。
A: MobileLink 默认要求链接必须包含协议头（http:// 或 https://）且路径中必须包含 /Article/ 段。请检查链接是否以 http:// 或 https:// 开头，并确认 Article 首字母为大写。如果链接来自其他移动子站，可以先将该域名添加到 config.yaml 的 domain_mapping 表中。

Q: 校验功能显示大量链接返回 404 状态码，是否意味着这些链接全部失效？
A: 不一定。部分移动站点会针对非移动端 User-Agent 返回 404 或重定向，建议在 validator.py 中配置与移动端一致的 User-Agent 头后再进行校验。另外，校验结果仅代表当前时刻的 HTTP 响应状态，可能受到临时网络波动或站点维护影响，建议多次校验后取综合结果。

Q: 如何将导出的 Markdown 链接列表直接用于 Hugo 或 Jekyll 站点？
A: 使用 `--format markdown` 导出的文件为标准 Markdown 无序列表，每行一个链接。对于 Hugo 等静态站点生成器，可以直接将导出内容嵌入到 content 目录下的 .md 文件中。若需要额外的标签或分类信息，可以使用 `--include-tags` 选项将标签以注释形式附加在每行链接之后。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
