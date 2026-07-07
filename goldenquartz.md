# WebIndex Mobile Article Aggregator

WebIndex Mobile Article Aggregator 是一个面向移动端技术内容聚合与导航的开源工具集，定位于对分散在多个移动子域名下的技术文章、运维笔记、开发文档进行统一索引、分类检索与快照归档。项目主要服务于技术内容运营者、个人知识管理爱好者以及中小型团队内部文档聚合场景，通过结构化的链接治理方案将零散的文章资源转化为可检索、可监控、可分享的标准化资源池。

本项目不提供爬虫框架或采集服务，而是围绕给定资源集合提供静态站点生成脚本、链接状态检测工具、分类标签管理模块以及自定义重定向规则文件，帮助用户在浏览器书签或自建导航页基础上建立轻量级内容中台。项目核心价值在于将非结构化的文章 URL 清单转化为具备可维护性的数据资产，降低内容运营过程中的链接管理成本。

## 功能概览

**多源文章链接统一入库** 提供基于 YAML 和 JSON 的双格式数据源定义方式，用户可通过声明式配置将不同移动子域名下的文章链接归并至同一索引体系。

**链接健康状态定时检测** 内置基于 Node.js 的链接可用性检测模块，支持 HEAD 请求超时控制和状态码记录，输出检测报告便于运维人员快速定位失效链接。

**分类标签与全文检索生成** 根据文章 URL 路径中的数字 ID 和来源域名自动生成分类标签，并构建简单的倒排索引文件，支持按域名、ID 范围、日期区间进行筛选检索。

**静态导航页一键生成** 通过模板引擎将索引数据渲染为响应式 HTML 导航页面，适配移动端浏览，可直接部署至静态托管服务或本地文件系统。

**自定义重定向规则编译** 将文章 ID 与域名映射关系编译为 Nginx 或 Apache 格式的重定向配置文件，便于团队内部将旧链接统一转发至新入口。

**数据快照导入导出** 支持将当前索引数据导出为 CSV 或 Markdown 表格，也支持从外部数据源追加导入，方便多人协作维护链接清单。

## 应用场景

内容运营团队定期汇总多个技术博客子域名的历史文章，使用本项目提供的导入脚本将分散的链接汇总至统一的索引数据库中，通过生成的静态导航页供团队成员快速查阅特定 ID 区间内的文档，避免反复在多个域名间切换查找。

个人开发者利用本项目构建私人技术书签站，将日常积累的运维手册、排障记录等文章链接按来源域名自动归类，配合健康检测模块每月自动检查一次链接可用性，及时发现已迁移或下线的资源。

中小型项目组在内部文档迁移过程中使用本项目的重定向规则生成功能，将旧文章 ID 映射至新文档系统的对应路径，通过 Nginx 配置文件实现无缝跳转，减少外部书签失效带来的访问中断问题。

## 快速开始

```bash
# 克隆项目仓库至本地
git clone https://github.com/webindex-mobile/article-aggregator.git

# 进入项目根目录
cd article-aggregator

# 安装项目依赖（需要 Node.js 16.x 及以上版本）
npm install

# 执行索引构建脚本，生成静态导航页和检测报告
npm run build -- --source=data/articles.yml --output=dist/
```

上述命令默认读取 data/articles.yml 中的链接配置，经过解析、分类、渲染三个步骤后，在 dist/ 目录下生成 index.html 导航页、tags.json 标签索引以及 health-report.json 检测结果文件。用户可通过修改配置文件中的 link 数组来替换或追加自己的文章集合。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 16.x 及以上 | 运行时环境，用于执行构建脚本和检测任务 |
| npm | 8.x 及以上 | 包管理工具，用于安装项目依赖库 |
| YAML 解析库 js-yaml | 4.1.0 | 用于读取和解析 articles.yml 配置文件 |
| 模板引擎 handlebars | 4.7.8 | 用于渲染静态导航页面的 HTML 模板 |
| 网络请求库 axios | 1.6.0 | 用于链接健康检测模块中的 HTTP 请求 |
| 命令行参数解析 yargs | 17.7.0 | 用于处理构建脚本的命令行参数 |
| Git | 2.30 及以上 | 用于版本控制和仓库克隆操作 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/configuration.md | 如何编写 articles.yml 配置文件，各字段的含义与取值范围 |
| 用户手册 | docs/user-guide/build-options.md | 构建脚本支持哪些命令行参数，如何自定义输出路径和模板 |
| 开发者指南 | docs/developer/architecture.md | 项目的模块划分、数据流转和扩展点设计 |
| 开发者指南 | docs/developer/api-reference.md | 核心函数接口说明，如何编写自定义插件或检测器 |
| 运维手册 | docs/operations/health-check.md | 如何配置定时检测任务，如何解读检测报告中的各项指标 |
| 运维手册 | docs/operations/redirect-rules.md | 重定向规则文件的生成方法与 Nginx 部署示例 |

## 资源列表

- http://www.mobile.jnjpgf.cn/Article/2343.shtml
- http://www.mobile.cmcvrr.cn/Article/2772.shtml
- http://www.mobile.puhvjy.cn/Article/17730.shtml
- http://www.mobile.cmcvrr.cn/Article/3465242.shtml
- http://www.mobile.puhvjy.cn/Article/5049419.shtml
- http://www.mobile.puhvjy.cn/Article/7671348.shtml
- http://www.mobile.puhvjy.cn/Article/51853.shtml
- http://www.mobile.cmcvrr.cn/Article/893513.shtml
- http://www.mobile.nwbbyt.cn/Article/27475.shtml
- http://www.mobile.cmcvrr.cn/Article/6700.shtml
- http://www.mobile.puhvjy.cn/Article/5704.shtml
- http://www.mobile.cmcvrr.cn/Article/438786.shtml
- http://www.mobile.cmcvrr.cn/Article/89339.shtml
- http://www.mobile.puhvjy.cn/Article/22712.shtml
- http://www.mobile.cmcvrr.cn/Article/72607.shtml
- http://www.mobile.nwbbyt.cn/Article/173529.shtml
- http://www.mobile.jnjpgf.cn/Article/10393.shtml
- http://www.mobile.cmcvrr.cn/Article/9422787.shtml
- http://www.mobile.cmcvrr.cn/Article/677924.shtml
- http://www.mobile.cmcvrr.cn/Article/6949.shtml
- http://www.mobile.puhvjy.cn/Article/3649.shtml
- http://www.mobile.cmcvrr.cn/Article/4567.shtml
- http://www.mobile.cmcvrr.cn/Article/7786.shtml
- http://www.mobile.cmcvrr.cn/Article/1155.shtml
- http://www.mobile.puhvjy.cn/Article/915465.shtml
- http://www.mobile.cmcvrr.cn/Article/43818.shtml
- http://www.mobile.cmcvrr.cn/Article/86903.shtml
- http://www.mobile.cmcvrr.cn/Article/7843.shtml
- http://www.mobile.jnjpgf.cn/Article/69031.shtml
- http://www.mobile.puhvjy.cn/Article/819224.shtml
- http://www.mobile.jnjpgf.cn/Article/612475.shtml
- http://www.mobile.cmcvrr.cn/Article/7672.shtml
- http://www.mobile.jnjpgf.cn/Article/77811.shtml
- http://www.mobile.puhvjy.cn/Article/6619977.shtml
- http://www.mobile.puhvjy.cn/Article/735541.shtml
- http://www.mobile.cmcvrr.cn/Article/4077.shtml
- http://www.mobile.nwbbyt.cn/Article/124854.shtml
- http://www.mobile.jnjpgf.cn/Article/405828.shtml
- http://www.mobile.jnjpgf.cn/Article/4829.shtml
- http://www.mobile.cmcvrr.cn/Article/428703.shtml
- http://www.mobile.puhvjy.cn/Article/889296.shtml
- http://www.mobile.jnjpgf.cn/Article/2408831.shtml
- http://www.mobile.cmcvrr.cn/Article/1152.shtml
- http://www.mobile.jnjpgf.cn/Article/526602.shtml
- http://www.mobile.cmcvrr.cn/Article/9011064.shtml
- http://www.mobile.jnjpgf.cn/Article/1217303.shtml
- http://www.mobile.jnjpgf.cn/Article/3619356.shtml
- http://www.mobile.nwbbyt.cn/Article/51206.shtml
- http://www.mobile.jnjpgf.cn/Article/1457353.shtml
- http://www.mobile.nwbbyt.cn/Article/600278.shtml
- http://www.mobile.jnjpgf.cn/Article/29471.shtml
- http://www.mobile.nwbbyt.cn/Article/49083.shtml
- http://www.mobile.nwbbyt.cn/Article/93181.shtml
- http://www.mobile.nwbbyt.cn/Article/8742.shtml
- http://www.mobile.jnjpgf.cn/Article/5617568.shtml
- http://www.mobile.nwbbyt.cn/Article/981025.shtml
- http://www.mobile.cmcvrr.cn/Article/9547.shtml
- http://www.mobile.cmcvrr.cn/Article/612472.shtml
- http://www.mobile.puhvjy.cn/Article/2698.shtml
- http://www.mobile.nwbbyt.cn/Article/584181.shtml
- http://www.mobile.nwbbyt.cn/Article/8454117.shtml
- http://www.mobile.jnjpgf.cn/Article/2359.shtml
- http://www.mobile.nwbbyt.cn/Article/5907.shtml
- http://www.mobile.cmcvrr.cn/Article/35530.shtml
- http://www.mobile.puhvjy.cn/Article/327060.shtml
- http://www.mobile.cmcvrr.cn/Article/2609.shtml
- http://www.mobile.puhvjy.cn/Article/7842.shtml
- http://www.mobile.puhvjy.cn/Article/8649.shtml
- http://www.mobile.jnjpgf.cn/Article/73489.shtml
- http://www.mobile.puhvjy.cn/Article/9393.shtml
- http://www.mobile.jnjpgf.cn/Article/08532.shtml
- http://www.mobile.jnjpgf.cn/Article/1546889.shtml
- http://www.mobile.puhvjy.cn/Article/425813.shtml
- http://www.mobile.jnjpgf.cn/Article/032053.shtml
- http://www.mobile.nwbbyt.cn/Article/0601.shtml
- http://www.mobile.jnjpgf.cn/Article/9370.shtml
- http://www.mobile.nwbbyt.cn/Article/9326239.shtml
- http://www.mobile.nwbbyt.cn/Article/575209.shtml
- http://www.mobile.nwbbyt.cn/Article/03261.shtml
- http://www.mobile.jnjpgf.cn/Article/68758.shtml
- http://www.mobile.nwbbyt.cn/Article/9520924.shtml
- http://www.mobile.puhvjy.cn/Article/3962547.shtml
- http://www.mobile.nwbbyt.cn/Article/240253.shtml
- http://www.mobile.cmcvrr.cn/Article/772348.shtml
- http://www.mobile.cmcvrr.cn/Article/9845322.shtml
- http://www.mobile.puhvjy.cn/Article/67914.shtml
- http://www.mobile.cmcvrr.cn/Article/25440.shtml
- http://www.mobile.jnjpgf.cn/Article/24376.shtml
- http://www.mobile.nwbbyt.cn/Article/730843.shtml
- http://www.mobile.puhvjy.cn/Article/144882.shtml
- http://www.mobile.jnjpgf.cn/Article/3078.shtml
- http://www.mobile.puhvjy.cn/Article/65850.shtml
- http://www.mobile.jnjpgf.cn/Article/14706.shtml
- http://www.mobile.nwbbyt.cn/Article/88992.shtml
- http://www.mobile.nwbbyt.cn/Article/03995.shtml
- http://www.mobile.puhvjy.cn/Article/634135.shtml
- http://www.mobile.puhvjy.cn/Article/71880.shtml
- http://www.mobile.puhvjy.cn/Article/1946.shtml
- http://www.mobile.nwbbyt.cn/Article/708062.shtml
- http://www.mobile.puhvjy.cn/Article/1451938.shtml
- http://www.mobile.cmcvrr.cn/Article/2031071.shtml
- http://www.mobile.jnjpgf.cn/Article/1324.shtml
- http://www.mobile.cmcvrr.cn/Article/335692.shtml
- http://www.mobile.puhvjy.cn/Article/27011.shtml
- http://www.mobile.puhvjy.cn/Article/2431557.shtml
- http://www.mobile.nwbbyt.cn/Article/466310.shtml
- http://www.mobile.jnjpgf.cn/Article/256384.shtml
- http://www.mobile.nwbbyt.cn/Article/8169.shtml
- http://www.mobile.jnjpgf.cn/Article/8718932.shtml
- http://www.mobile.nwbbyt.cn/Article/3717684.shtml
- http://www.mobile.puhvjy.cn/Article/9990.shtml
- http://www.mobile.cmcvrr.cn/Article/4788379.shtml
- http://www.mobile.nwbbyt.cn/Article/34645.shtml
- http://www.mobile.puhvjy.cn/Article/72738.shtml
- http://www.mobile.jnjpgf.cn/Article/93474.shtml
- http://www.mobile.puhvjy.cn/Article/2837646.shtml
- http://www.mobile.jnjpgf.cn/Article/074669.shtml
- http://www.mobile.puhvjy.cn/Article/5691923.shtml
- http://www.mobile.jnjpgf.cn/Article/301793.shtml
- http://www.mobile.puhvjy.cn/Article/0437555.shtml
- http://www.mobile.jnjpgf.cn/Article/651204.shtml
- http://www.mobile.nwbbyt.cn/Article/79864.shtml
- http://www.mobile.jnjpgf.cn/Article/3697264.shtml
- http://www.mobile.puhvjy.cn/Article/917155.shtml
- http://www.mobile.puhvjy.cn/Article/222109.shtml
- http://www.mobile.cmcvrr.cn/Article/546795.shtml
- http://www.mobile.puhvjy.cn/Article/73171.shtml
- http://www.mobile.jnjpgf.cn/Article/133803.shtml
- http://www.mobile.cmcvrr.cn/Article/9505.shtml
- http://www.mobile.nwbbyt.cn/Article/1802096.shtml
- http://www.mobile.cmcvrr.cn/Article/2112.shtml
- http://www.mobile.puhvjy.cn/Article/14231.shtml
- http://www.mobile.nwbbyt.cn/Article/20071.shtml
- http://www.mobile.nwbbyt.cn/Article/67933.shtml
- http://www.mobile.cmcvrr.cn/Article/96577.shtml
- http://www.mobile.nwbbyt.cn/Article/069969.shtml
- http://www.mobile.jnjpgf.cn/Article/4589.shtml
- http://www.mobile.jnjpgf.cn/Article/534262.shtml
- http://www.mobile.nwbbyt.cn/Article/172807.shtml
- http://www.mobile.nwbbyt.cn/Article/3000.shtml
- http://www.mobile.cmcvrr.cn/Article/776859.shtml
- http://www.mobile.nwbbyt.cn/Article/942039.shtml
- http://www.mobile.cmcvrr.cn/Article/6263.shtml
- http://www.mobile.nwbbyt.cn/Article/755642.shtml
- http://www.mobile.nwbbyt.cn/Article/7296087.shtml
- http://www.mobile.jnjpgf.cn/Article/067899.shtml
- http://www.mobile.cmcvrr.cn/Article/2608.shtml
- http://www.mobile.jnjpgf.cn/Article/811289.shtml
- http://www.mobile.jnjpgf.cn/Article/0988.shtml
- http://www.mobile.puhvjy.cn/Article/863507.shtml
- http://www.mobile.jnjpgf.cn/Article/8878.shtml
- http://www.mobile.jnjpgf.cn/Article/76704.shtml
- http://www.mobile.cmcvrr.cn/Article/4498.shtml
- http://www.mobile.nwbbyt.cn/Article/773100.shtml
- http://www.mobile.nwbbyt.cn/Article/644488.shtml
- http://www.mobile.cmcvrr.cn/Article/429025.shtml
- http://www.mobile.nwbbyt.cn/Article/9378468.shtml
- http://www.mobile.puhvjy.cn/Article/1829724.shtml
- http://www.mobile.puhvjy.cn/Article/6431677.shtml
- http://www.mobile.nwbbyt.cn/Article/6832149.shtml
- http://www.mobile.jnjpgf.cn/Article/6540326.shtml
- http://www.mobile.cmcvrr.cn/Article/1576.shtml
- http://www.mobile.jnjpgf.cn/Article/594094.shtml
- http://www.mobile.jnjpgf.cn/Article/8668425.shtml
- http://www.mobile.jnjpgf.cn/Article/5583.shtml
- http://www.mobile.puhvjy.cn/Article/17404.shtml
- http://www.mobile.jnjpgf.cn/Article/27308.shtml
- http://www.mobile.cmcvrr.cn/Article/454164.shtml
- http://www.mobile.puhvjy.cn/Article/205637.shtml
- http://www.mobile.nwbbyt.cn/Article/2628.shtml
- http://www.mobile.cmcvrr.cn/Article/906263.shtml
- http://www.mobile.jnjpgf.cn/Article/841001.shtml
- http://www.mobile.cmcvrr.cn/Article/55989.shtml
- http://www.mobile.jnjpgf.cn/Article/6548739.shtml
- http://www.mobile.cmcvrr.cn/Article/80690.shtml
- http://www.mobile.puhvjy.cn/Article/811467.shtml
- http://www.mobile.nwbbyt.cn/Article/256588.shtml
- http://www.mobile.puhvjy.cn/Article/08477.shtml
- http://www.mobile.jnjpgf.cn/Article/2383255.shtml
- http://www.mobile.nwbbyt.cn/Article/6878.shtml
- http://www.mobile.cmcvrr.cn/Article/98286.shtml
- http://www.mobile.jnjpgf.cn/Article/6465.shtml
- http://www.mobile.nwbbyt.cn/Article/996930.shtml
- http://www.mobile.jnjpgf.cn/Article/66726.shtml
- http://www.mobile.nwbbyt.cn/Article/7383.shtml
- http://www.mobile.cmcvrr.cn/Article/50082.shtml
- http://www.mobile.jnjpgf.cn/Article/2224023.shtml
- http://www.mobile.nwbbyt.cn/Article/9079817.shtml
- http://www.mobile.cmcvrr.cn/Article/1941703.shtml
- http://www.mobile.nwbbyt.cn/Article/4969.shtml
- http://www.mobile.cmcvrr.cn/Article/647844.shtml
- http://www.mobile.puhvjy.cn/Article/987431.shtml
- http://www.mobile.jnjpgf.cn/Article/49184.shtml
- http://www.mobile.puhvjy.cn/Article/788628.shtml
- http://www.mobile.jnjpgf.cn/Article/4481983.shtml
- http://www.mobile.jnjpgf.cn/Article/1674.shtml
- http://www.mobile.puhvjy.cn/Article/9774331.shtml
- http://www.mobile.cmcvrr.cn/Article/7289338.shtml
- http://www.mobile.cmcvrr.cn/Article/717225.shtml
- http://www.mobile.nwbbyt.cn/Article/97721.shtml
- http://www.mobile.cmcvrr.cn/Article/135527.shtml
- http://www.mobile.puhvjy.cn/Article/1199.shtml
- http://www.mobile.nwbbyt.cn/Article/02213.shtml
- http://www.mobile.cmcvrr.cn/Article/7005406.shtml
- http://www.mobile.cmcvrr.cn/Article/296666.shtml
- http://www.mobile.jnjpgf.cn/Article/5108.shtml
- http://www.mobile.jnjpgf.cn/Article/080241.shtml
- http://www.mobile.nwbbyt.cn/Article/398924.shtml
- http://www.mobile.jnjpgf.cn/Article/2275.shtml
- http://www.mobile.nwbbyt.cn/Article/8330388.shtml
- http://www.mobile.puhvjy.cn/Article/3996279.shtml
- http://www.mobile.nwbbyt.cn/Article/408174.shtml
- http://www.mobile.jnjpgf.cn/Article/866931.shtml
- http://www.mobile.puhvjy.cn/Article/5286261.shtml
- http://www.mobile.nwbbyt.cn/Article/6882.shtml
- http://www.mobile.nwbbyt.cn/Article/5541.shtml
- http://www.mobile.nwbbyt.cn/Article/880813.shtml
- http://www.mobile.puhvjy.cn/Article/74753.shtml
- http://www.mobile.nwbbyt.cn/Article/7442585.shtml
- http://www.mobile.puhvjy.cn/Article/47027.shtml
- http://www.mobile.nwbbyt.cn/Article/768617.shtml
- http://www.mobile.nwbbyt.cn/Article/9688.shtml
- http://www.mobile.nwbbyt.cn/Article/135502.shtml
- http://www.mobile.puhvjy.cn/Article/27718.shtml
- http://www.mobile.cmcvrr.cn/Article/8753015.shtml
- http://www.mobile.puhvjy.cn/Article/865454.shtml
- http://www.mobile.jnjpgf.cn/Article/4043.shtml
- http://www.mobile.jnjpgf.cn/Article/3395040.shtml
- http://www.mobile.cmcvrr.cn/Article/826306.shtml
- http://www.mobile.puhvjy.cn/Article/7284.shtml
- http://www.mobile.puhvjy.cn/Article/33254.shtml
- http://www.mobile.puhvjy.cn/Article/1898083.shtml
- http://www.mobile.nwbbyt.cn/Article/215736.shtml
- http://www.mobile.cmcvrr.cn/Article/9448615.shtml
- http://www.mobile.jnjpgf.cn/Article/922200.shtml
- http://www.mobile.nwbbyt.cn/Article/9088.shtml
- http://www.mobile.puhvjy.cn/Article/04768.shtml
- http://www.mobile.nwbbyt.cn/Article/4705419.shtml
- http://www.mobile.cmcvrr.cn/Article/77792.shtml
- http://www.mobile.jnjpgf.cn/Article/570065.shtml
- http://www.mobile.nwbbyt.cn/Article/00369.shtml
- http://www.mobile.nwbbyt.cn/Article/00697.shtml
- http://www.mobile.nwbbyt.cn/Article/59711.shtml
- http://www.mobile.puhvjy.cn/Article/2233127.shtml
- http://www.mobile.puhvjy.cn/Article/56130.shtml
- http://www.mobile.cmcvrr.cn/Article/21173.shtml
- http://www.mobile.nwbbyt.cn/Article/3297157.shtml
- http://www.mobile.jnjpgf.cn/Article/1541458.shtml
- http://www.mobile.nwbbyt.cn/Article/989073.shtml
- http://www.mobile.nwbbyt.cn/Article/923375.shtml

## 项目结构

```
article-aggregator/
├── bin/                                # 可执行脚本入口目录
│   ├── build.js                        # 主构建脚本，调用各模块完成索引生成
│   └── health-check.js                 # 独立健康检测命令行工具
├── lib/                                # 核心函数库目录
│   ├── parser/                         # 解析器模块
│   │   ├── yaml-loader.js              # 加载并解析 articles.yml 配置文件
│   │   └── url-extractor.js            # 从链接中提取域名、ID、扩展名等信息
│   ├── indexer/                        # 索引构建模块
│   │   ├── tag-generator.js            # 根据域名和ID生成分类标签
│   │   └── inverted-index.js           # 构建简单的倒排索引供检索使用
│   ├── renderer/                       # 渲染输出模块
│   │   ├── html-render.js              # 使用 Handlebars 渲染导航页 HTML
│   │   └── json-exporter.js            # 导出索引数据为 JSON / CSV 格式
│   ├── checker/                        # 链接检测模块
│   │   ├── http-client.js              # 封装 axios 请求，设置超时与重试
│   │   └── reporter.js                 # 生成检测报告 Markdown 文件
│   └── cli/                            # 命令行参数解析模块
│       ├── options.js                  # 定义 yargs 参数配置
│       └── logger.js                   # 彩色日志输出工具
├── templates/                          # Handlebars 模板文件目录
│   ├── index.hbs                       # 导航页主模板
│   ├── tags.hbs                        # 标签聚合页模板
│   └── partials/                       # 模板片段
│       ├── head.hbs                    # HTML head 公共片段
│       └── footer.hbs                  # 页脚公共片段
├── data/                               # 数据文件目录
│   ├── articles.yml                    # 主配置文件，用户在此定义文章链接清单
│   └── categories.yml                  # 可选的分类映射配置文件
├── dist/                               # 构建输出目录（git 忽略）
│   ├── index.html                      # 生成的导航首页
│   ├── tags.json                       # 标签索引 JSON
│   └── health-report.json              # 最新健康检测报告
├── docs/                               # 项目文档目录
│   ├── user-guide/                     # 用户手册
│   ├── developer/                      # 开发者指南
│   └── operations/                     # 运维手册
├── tests/                              # 单元测试目录
│   ├── parser.test.js                  # 解析器模块测试用例
│   ├── indexer.test.js                 # 索引构建模块测试用例
│   └── checker.test.js                 # 检测模块测试用例
├── .gitignore                          # Git 忽略文件配置
├── package.json                        # Node.js 项目配置文件
├── package-lock.json                   # 依赖锁定文件
├── README.md                           # 项目说明文档（本文件）
└── LICENSE                             # MIT 许可证文件
```

## 贡献指南

1. 从 GitHub 仓库 Fork 本项目至个人账号下，使用 git clone 将 Fork 后的仓库拉取到本地开发环境，并添加 upstream 远程仓库以同步主仓库更新。

2. 在本地新建功能分支，分支命名采用 feature/功能描述 或 fix/问题描述 格式，确保分支名称清晰反映本次变更的内容范围。

3. 完成代码修改后，运行 npm run test 执行全部单元测试用例，确保新增代码未破坏已有功能；若涉及新增依赖，需同步更新 package.json 和文档中的安装要求表格。

4. 提交代码时遵循 Conventional Commits 规范编写 commit message，使用 feat、fix、docs、chore 等类型前缀，并简要描述变更目的与影响范围。

5. 将本地分支推送至个人 Fork 仓库，通过 GitHub 页面发起 Pull Request 至主仓库的 main 分支，PR 描述中需说明变更背景、实现方案以及测试覆盖情况，等待项目维护者审阅。

## 常见问题

**问：配置文件中的文章链接数量很大时，构建速度是否会明显下降？**

构建脚本对单次解析的文章链接数量不设硬性上限，但实际构建速度受限于 YAML 解析耗时、模板渲染开销以及健康检测模块的网络请求并发数。对于超过 500 条链接的配置，建议使用 --skip-health 参数跳过检测环节以加快构建速度，或通过 --concurrency 参数调整检测时的并发请求数。项目本身不限制链接总量，但过大的索引文件可能导致生成的导航页体积膨胀，建议按年度或按主题拆分配置文件。

**问：健康检测模块报告某个链接为失效，但手动访问浏览器中可以正常打开，如何解决？**

此情况通常由目标服务器对 HEAD 请求的限制或反爬策略导致。检测模块默认优先使用 HEAD 方法，若服务器返回 405 或 403 状态码，可尝试在配置中为特定域名开启 GET 方法回退选项。此外，检测模块的 User-Agent 默认值与浏览器不同，部分服务器会据此返回不同的响应状态，建议在检测配置中将 User-Agent 修改为常见浏览器的字符串。若问题持续存在，可在检测报告中将该链接标记为手动确认通过，并更新本地缓存记录。

**问：生成的静态导航页能否部署到 Nginx 或 Apache 等 Web 服务器？**

可以。dist/ 目录下输出的所有文件均为纯静态资源，不依赖任何后端服务或数据库支持。将 dist/ 目录整体复制到 Web 服务器的静态资源根目录下，配置好 MIME 类型支持 .html 和 .json 文件即可正常访问。若需要将文章链接映射至特定路径，可使用项目提供的重定向规则生成模块输出 Nginx rewrite 或 Apache RewriteRule 格式的配置文件，将其包含至主站点配置中实现统一跳转。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:12:38
