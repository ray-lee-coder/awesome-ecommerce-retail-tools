# Awesome 国内电商 & 零售:小工具与 Workflow 配方

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

聚焦**国内电商/零售**场景(淘宝、天猫、京东、拼多多、1688、抖音、快手、视频号、小红书、微信私域、企业微信、闲鱼、线下零售)可用的小型开源工具,以及**跨境/通用**的辅助工具。

> **范围**:
> - 主力 = **国内平台**直接可用的小工具(采集器、机器人、API 包装、运营辅助)
> - 保留 = **通用且实用**的(Amazon SP-API 包装、Shopify 模板、OCR、情感分析、Markdown 转换),它们在国内场景(分析竞品、做跨境、对照参考)同样会用
> - **排除** = 大型平台(Medusa / Saleor / Shopware / Odoo / n8n / Dify / Coze / Flowise / Langflow / ComfyUI / Ollama)

---

## 目录

1. [选型决策表](#选型决策表)
2. [抖音 / 视频号 / 小红书 采集](#1-抖音--视频号--小红书-采集)
3. [淘宝 / 天猫 / 1688 采集与运营](#2-淘宝--天猫--1688-采集与运营)
4. [拼多多 采集与运营](#3-拼多多-采集与运营)
5. [京东 采集与运营](#4-京东-采集与运营)
6. [多平台通用采集器](#5-多平台通用采集器)
7. [微信生态 / 私域 / 企业微信](#6-微信生态--私域--企业微信)
8. [直播辅助 / 弹幕 / 录制](#7-直播辅助--弹幕--录制)
9. [物流 / 快递 / 打单](#8-物流--快递--打单)
10. [评论挖掘 / 情感 / 主题聚类](#9-评论挖掘--情感--主题聚类)
11. [图片 / 视频 / 文案 创作辅助](#10-图片--视频--文案-创作辅助)
12. [电商 API 包装 / SDK / MCP](#11-电商-api-包装--sdk--mcp)
13. [微信小程序 / 商城模板](#12-微信小程序--商城模板)
14. [通用工具(国内场景常用)](#13-通用工具国内场景常用)
15. [Workflow 配方(国内场景)](#14-workflow-配方国内场景)
16. [贡献指南](#贡献指南)

---

## 选型决策表

| 你要做的 | 直接用 | 备注 |
|---|---|---|
| 抓小红书/抖音/视频号 笔记/视频/评论 | `cv-cat/Spider_XHS`、`NanmiCoder/MediaCrawler` | 主力,国内最常用 |
| 抓淘宝商品/价格/评价 | `zhangjiancong/MarketSpider` 或自己写 | 淘宝风控严,小规模用 |
| 抓 1688 找货源(跨境/无货源) | `1688-cli`、`1688-Crawler` | 适合无货源卖家 |
| 抓拼多多 商品/店铺/评价 | `PLAhui/pdd-caiji`、`dtapps/pinduoduo`(API) | 桌面 GUI / Go SDK 都有 |
| 抓京东 价格/商品 | `zhangjiancong/MarketSpider`(内含) 或 GitHub Action 监控方案 | 见 §4 |
| 多平台一次性抓 | `MediaCrawler` | 一次脚本通吃 7+ 平台 |
| 接企业微信做 SCRM/客服 | `mochat-cloud/mochat` 或 `LinkWeChat` | 私域标配 |
| 个人微信自动回复/群管理 | `wechaty/wechaty` | 国内最主流 |
| 微信小程序 商城 模板 | `fqt111/Fresh-Food-E-commerce-Solution` 或其他小程序开源 | 见 §12 |
| 直播间弹幕监听/录制/自动回复 | `jwwsjlm/douyinLive`、`LyzenX/DouyinLiveRecorder` | 见 §7 |
| 查快递/批量查/打单 | `kuaidi100-MCP` 或快递100 API 包装 | 物流首选 |
| 评论做情感分析/主题聚类 | VADER / spaCy / BERTopic(通用) | 配合 §1-§5 采集器 |
| 改写商品标题/做 SEO 描述 | MarkItDown + 本地 LLM 脚本 | 20 行代码 |
| TikTok Shop / Amazon 跨境 | `jay-trivedi/amazon_sp_mcp`、`ipfans/tiktok` | 通用区,见 §11 |

---

## 1. 抖音 / 视频号 / 小红书 采集

国内社交电商主战场,采集是选品/分析/竞品监控的入口。

### 小红书(RedNote)

- **[cv-cat/Spider_XHS](https://github.com/cv-cat/Spider_XHS)** — 小红书全场景采集 + 发布能力,支持多账号 / Cookie 池 / 签名算法 / skills 集成。Use when: 你想做小红书 AI 运营 agent 的数据底座。
- **[JoeanAmier/XHS-Downloader](https://github.com/JoeanAmier/XHS-Downloader)** — 小红书链接提取 / 作品采集 / 批量下载,AGPL-3.0。Use when: 你只要下载图片视频不打运营。
- **[xhs_ai_publisher (BetaStreetOmnis)](https://github.com/BetaStreetOmnis/xhs_ai_publisher)** — AI 驱动的小红书内容创作 + 自动发布(PyQt 桌面 UI + FastAPI)。Use when: 你想"AI 写 + 自动发"一站式。
- **[NanmiCoder/MediaCrawler](#5-多平台通用采集器)** — 小红书 / 抖音 / B站 / 微博 / 知乎 / 贴吧 / 快手 7+ 平台通吃,~27.7k stars。

### 抖音 / TikTok

- **[NanmiCoder/MediaCrawler](https://github.com/NanmiCoder/MediaCrawler)** — *(见 §5)* — 抖音 / TikTok 评论 / 视频 / 搜索 / 创作者主页。
- **[Evil0ctal/Douyin_TikTok_Download_API](https://github.com/Evil0ctal/Douyin_TikTok_Download_API)** — 抖音 / TikTok 无水印下载 + 解析 API,基于 PyWebIO + HTTPX。Use when: 你需要快速拿到无水印视频 / 图集。
- **[wanghaisheng/MediaCrawlerDP](https://github.com/wanghaisheng/MediaCrawlerDP)** — 抖音 / 小红书 / 快手 / B站 / 微博 多平台采集 fork,Apache-2.0。
- **[ipfans/tiktok](https://github.com/ipfans/tiktok)** — TikTok Shop Open Platform Go SDK。Use when: 你做 TikTok Shop 跨境(国内团队也常做),要 SDK 调订单/履约/财务/物流。
- **[vooltex8egp/tiktok-shop-scraper](https://github.com/vooltex8egp/tiktok-shop-scraper)** — TikTok Shop 数据采集:产品/卖家/价格/评分/库存。

### 视频号(微信小店)

- **[zsmhub/wx-channels-sdk](https://github.com/zsmhub/wx-channels-sdk)** — Go 视频号小店 + 视频号橱窗 SDK。Use when: 你用 Go 接入视频号订单/商品/直播。
- **[nobiyou/wx_channel](https://github.com/nobiyou/wx_channel)** — 视频号下载助手(GUI 工具,无需代码)。Use when: 运营想批量下载视频号素材做分析。

---

## 2. 淘宝 / 天猫 / 1688 采集与运营

淘宝系风控严,稳定工具稀缺;1688(阿里批发)是大量跨境和无货源卖家的货源入口。

- **[zhangjiancong/MarketSpider](https://github.com/zhangjiancong/MarketSpider)** — 淘宝 / 京东 / 1688 商品信息爬虫,带 Tkinter GUI 监控界面。Use when: 你要中文 GUI 直接跑。
- **[victorup/Taobao-Data-Analysis](https://github.com/victorup/Taobao-Data-Analysis)** — 淘宝商品大数据分析(价格/销量/地区/销量-价格关系),含可视化。Use when: 你做选品分析课程/毕设/教学。
- **[AlcatrazChris/AutoProductEvalution](https://github.com/AlcatrazChris/AutoProductEvalution)** — 淘宝 / 京东商品评论情感分析,Web UI,数据自动落盘。Use when: 你想要个开箱即用的商品评价系统。
- **[1688-cli (superjack2050)](https://github.com/superjack2050/1688-cli)** — 1688 CLI,AI-agent 友好的命令行采购/调研/供应商评估工具。Use when: 你做无货源跨境,要从 1688 选品。
- **[1688-Crawler (jeff2go)](https://github.com/jeff2go/1688-Crawler)** — Flask-based 1688 爬虫。Use when: 你要 Python 二次开发。
- **[jadeship-browser-extension (cachho)](https://github.com/cachho/jadeship-browser-extension)** — Chrome 扩展,在 Reddit / Yupoo 页面上把链接换成 1688 找同款。Use when: 跨境选品看图找货。
- **[krautsdubisq1g/1688-product-search-scraper](https://github.com/krautsdubisq1g/1688-product-search-scraper)** — 1688 商品搜索结果抓取。
- **[itsukiken1/sourcecalc](https://github.com/itsukiken1/sourcecalc)** — Chrome 扩展:在 1688 商品页直接算利润率。Use when: 你做跨境,需要算 1680 拿货价 → 海外售价的毛利。
- **[hikari0511/awesome-amazon-ec-skills](https://github.com/hikari0511/awesome-amazon-ec-skills)** — 亚马逊跨境 + 1688 供货上游的 Claude / AI Agent Skills 合集。Use when: 跨境+1688 联动,需要 AI 工具链。

---

## 3. 拼多多 采集与运营

- **[PLAhui/pdd-caiji](https://github.com/PLAhui/pdd-caiji)** — 拼多多采集器,Node.js + Vue + Electron,跨平台桌面 GUI,关键词/筛选/导出 Excel。Use when: 你不想写代码,直接装 GUI。
- **[wfgsss/pinduoduo-scraper-example](https://github.com/wfgsss/pinduoduo-scraper-example)** — 拼多多商品数据(价格/销量/图片)Python 采集。Use when: 你想要可改的 Python 脚本。
- **[dtapps/go-library pinduoduo](https://pkg.go.dev/github.com/dtapps/go-library/service/pinduoduo)** — Pinduoduo Open API Go 客户端,支持商品/订单/推广链接/分销。Use when: 你用 Go 接入拼多多官方 API。
- **[InfoSpider](https://github.com/)** *(项目归档,拼多多模块已加入)* — 多平台爬虫框架,含拼多多模块。Use when: 你需要一个可扩展的中文爬虫框架。

> **官方限制**:拼多多个人 API 申请门槛在提高,大量卖家实际用 RPA 或浏览器自动化。上面工具对应不同路径。

---

## 4. 京东 采集与运营

- **[zhangjiancong/MarketSpider](https://github.com/zhangjiancong/MarketSpider)** — *(见 §2)* — 淘宝/京东/1688 都有。
- **[HongDanni/jd_daojia](https://github.com/HongDanni/jd_daojia)** — 京东到家小程序商家商品信息采集。Use when: 你做京东到家 / 社区团购选品。
- **GitHub Action 京东价格监控方案** *(博客方案,非 GitHub repo)* — 利用 GitHub Actions + Python 监控京东商品价格,微信/Qmsg 推送。

---

## 5. 多平台通用采集器

**这一类在国内场景里最常用,任何做选品/竞品分析/AI 训练数据的人都需要**。

- **[NanmiCoder/MediaCrawler](https://github.com/NanmiCoder/MediaCrawler)** — **国内社交电商采集的事实标准**。支持 7+ 平台(小红书/抖音/快手/B站/微博/知乎/贴吧),关键词/ID 爬取、二级评论、登录态缓存、IP 代理池、评论词云。~27.7k stars。Use when: 你要做"评论语料"或"运营分析",这是首选。
- **[wanghaisheng/MediaCrawlerDP](https://github.com/wanghaisheng/MediaCrawlerDP)** — MediaCrawler 的衍生版本,覆盖更多平台。
- **[Shopify theme + scrapy 通用方案]** — 对于非社交平台的普通电商站(任何网站),用通用爬虫库:Jina Reader / Firecrawl / Crawl4AI / ScrapeGraphAI / AutoScraper(见 §13)。

---

## 6. 微信生态 / 私域 / 企业微信

国内私域的核心阵地。

### 企业微信 SCRM(私域)

- **[mochat-cloud/mochat](https://github.com/mochat-cloud/mochat)** — 基于企业微信的开源 SCRM 框架,2.6k stars,PHP + Vue,GPL-3.0。Use when: 你要给客户部署一套完整的 SCRM。
- **[LinkWeChat (Gitee)](https://gitee.com/chenguowen/link-wechat)** — 同类型 SCRM,Gitee 主仓,基于 Spring Boot + Vue。
- **[IYque/Iyque-SCRM](https://github.com/IYque/Iyque-SCRM)** — 源雀 SCRM 开源版,Apache-2.0,可商用二开,集成 DeepSeek 等大模型。Use when: 你要能商用的 SCRM(其他几个 GPL 严格)。
- **LinkWeChat / MoChat 商业授权** — *(参考,大部分企业微信 SCRM 开源版不能直接商用,需购买授权)*

### 个人微信 / 公众号 / 机器人

- **[wechaty/wechaty](https://github.com/wechaty/wechaty)** — 跨平台聊天 RPA SDK,微信/企业微信/WhatsApp/QQ/Gitter,6 行代码出 bot,Apache-2.0。Use when: 你要做个人微信群管理、自动回复、消息同步。
- **[wechaty/getting-started](https://github.com/wechaty/getting-started)** — Wechaty 起步模板。
- **tgenaitay/wechat-miniprogram-whitebook** — 微信小程序白皮书 + 实战代码。Use when: 你想从零学小程序。

### 公众号 / 文章采集

- **[chyroc/WechatSogou](https://github.com/chyroc/WechatSogou)** — 微信公众号文章爬虫,Apache-2.0。Use when: 你做公众号内容监控 / 选素材。
- **[wnma3mz/wechat_articles_spider](https://github.com/wnma3mz/wechat_articles_spider)** — 同样目的,Apache-2.0。

---

## 7. 直播辅助 / 弹幕 / 录制

抖音/快手/视频号直播是国内带货主战场。

- **[jwwsjlm/douyinLive](https://github.com/jwwsjlm/douyinLive)** — 抖音弹幕抓取,WebSocket 服务,Docker 部署。Use when: 你要监听自家或竞品直播弹幕,做互动 / 数据分析 / 语音播报。
- **[LyzenX/DouyinLiveRecorder](https://github.com/LyzenX/DouyinLiveRecorder)** — 自动监测 + 录制抖音直播,**支持录制弹幕**,GUI/CLI 都有,Linux 可跑,无需 cookie。Use when: 你要长期录自己的直播做剪辑 / 合规存档。
- **[javpower/douyin-monitor](https://github.com/javpower/douyin-monitor)** — 基于系统代理抓包的抖音弹幕服务,WebSocket 推送。Use when: 你想做弹幕互动游戏 / 直播数据分析。
- **[Sjj1024/douyin-live](https://github.com/Sjj1024/douyin-live)** — Python 直播小工具,带 LiveBox 桌面端,学习项目。

> **关键提醒**:抖音/TikTok 协议经常变,选工具前看最近一次 commit 是否在 30 天内,超过 60 天大概率失效。

---

## 8. 物流 / 快递 / 打单

- **[kuaidi100-api/kuaidi100-MCP](https://github.com/kuaidi100-api/kuaidi100-MCP)** — 快递100 MCP Server(国内首个支持 MCP 协议的物流平台),通 2100+ 快递公司。Use when: 你要把物流查询接到 Claude/Cursor/Codex。
- **[kuaidi100-api/go-demo](https://github.com/kuaidi100-api/go-demo)** — 快递100 Go 官方 demo,电子面单/寄件/地图跟踪 API。Use when: 你做电商后台要批量打单发货。
- **快递100 SaaS / 百递云** — *(非开源,作为参考)* — 中小商家用的 SaaS。

> **国内打单场景**:大部分商家直接用快递100 SaaS、菜鸟、旺店通,纯开源打单工具有限,核心是 API 包装+模板。

---

## 9. 评论挖掘 / 情感 / 主题聚类

国内评论语料的中文工具很少完全开源,但通用 NLP 工具能直接用。

### 中文情感 / NLP(国内)

- **SnowNLP** — 中文情感分析经典库,纯 Python。Use when: 你要快速给中文评论打分。
- **jiagu** — 中文 NLP 工具包(分词/词性/命名实体/情感/摘要)。
- **HanLP** — 多语言/多任务中文 NLP,生产级。
- **PaddleNLP** — 百度飞桨,中文场景最完整生态。

### 通用 NLP(英文为主,但 BERTopic/VADER 跑中文也凑合)

- **[VADER](https://github.com/cjhutto/vaderSentiment)** — 规则情感,英文为主。MIT。
- **[TextBlob](https://github.com/sloria/TextBlob)** — 简单英文 NLP。MIT。
- **[spaCy](https://github.com/explosion/spaCy)** — 工业级 NLP,中文需装 `zh_core_web_sm` 模型。MIT。
- **[BERTopic](https://github.com/MaartenGr/BERTopic)** — 主题聚类,支持中文 embedding。MIT。
- **[Allenyan513/reviewsup.io](https://github.com/allenyan513/reviewsup.io)** — 开源评价管理 CMS(国内 SaaS 替代品)。

### 训练数据 / 微调

- **[Argilla](https://github.com/argilla-io/argilla)** — 数据标注平台,Apache-2.0。
- **[Cleanlab](https://github.com/cleanlab/cleanlab)** — 数据质量检测,MIT。

---

## 10. 图片 / 视频 / 文案 创作辅助

国内商家高频刚需:短视频脚本、商品图、详情页文案。

- **[MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo)** — 一键生成短视频,Apache-2.0。Use when: 你做矩阵号/批量混剪。
- **[VideoLingo](https://github.com/HKUDS/VideoLingo)** — 视频自动翻译/配音/字幕,Apache-2.0。Use when: 你做跨境把国内视频翻译成英文。
- **[MarkItDown](https://github.com/microsoft/markitdown)** — PDF/DOCX/HTML/图片 → Markdown。MIT。Use when: 供应商给你 PDF 目录,你要转结构化文本。
- **[Surya](https://github.com/VikParuchuri/surya)** — 90+ 语言 OCR,布局感知。GPL-3.0。
- **[PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR)** — 百度 OCR,**中文场景最稳**。Apache-2.0。Use when: 你要识别商品图中的中文文字/价格/型号。
- **[Marker](https://github.com/datalab-to/marker)** — 快速 PDF/图片 → Markdown。Apache-2.0。
- **[autosub (agermanidis)](https://github.com/agermanidis/autosub)** — 自动字幕生成。MIT。
- **[ComfyUI](https://github.com/comfyanonymous/ComfyUI)** — 节点式 SD UI(本地产品图/换装/背景替换,国内电商高频用)。MIT。*(功能多,这里算"基础引擎",但在国内场景里单用途明确:商品图合成)*

### 短视频下载 / 去水印(国内场景专用)

- **[Douyin_TikTok_Download_API](#1-抖音--视频号--小红书-采集)** — *(见 §1)* 抖音 / TikTok。
- **[putyy/res-downloader](https://github.com/putyy/res-downloader)** — 视频/图片下载,见 `xiaohongshu` 主题。

---

## 11. 电商 API 包装 / SDK / MCP

**节省接入国内各平台 API 时间的薄包装**。

### 跨境(国内团队也常用)

- **[jay-trivedi/amazon_sp_mcp](https://github.com/jay-trivedi/amazon_sp_mcp)** — Amazon SP-API MCP Server,MIT。Use when: 你用 AI agent 读自己 Seller Central 数据。
- **[amzn/selling-partner-api-models](https://github.com/amzn/selling-partner-api-models)** — 官方 SP-API Swagger 模型。Apache-2.0。
- **[amzn/selling-partner-api-samples](https://github.com/amzn/selling-partner-api-samples)** — 官方代码样例。
- **[DataDoe MCP Server](https://mcpservers.org/servers/deltologic/datadoe-mcp)** — 托管 Amazon SP-API + Ads MCP,MIT。
- **[ipfans/tiktok](https://github.com/ipfans/tiktok)** — *(见 §1)* TikTok Shop Open Platform Go SDK。

### 1688 / 阿里

- **[OpenTrade Commerce API SDK (cachho)](https://github.com/cachho)** — Taobao / Alibaba / JD / 1688 / AliExpress / eBay 统一 SDK。
- **[1688-cli](#2-淘宝--天猫--1688-采集与运营)** — *(见 §2)*。

### 拼多多

- **[dtapps/go-library pinduoduo](#3-拼多多-采集与运营)** — *(见 §3)* Go SDK。

### 微信生态

- **[wechaty/wechaty](https://github.com/wechaty/wechaty)** — *(见 §6)* 个人/企业微信统一 RPA。
- **[zsmhub/wx-channels-sdk](#1-抖音--视频号--小红书-采集)** — *(见 §1)* 视频号小店 SDK。

---

## 12. 微信小程序 / 商城模板

- **[fqt111/Fresh-Food-E-commerce-Solution-on-WeChat-Mini-Program](https://github.com/fqt111/Fresh-Food-E-commerce-Solution-on-WeChat-Mini-Program)** — 微信小程序生鲜电商方案。Use when: 你要快速搭一个社区团购/生鲜配送小程序。
- **[medallia/wechat-link-relay-mini-program](https://github.com/medallia/wechat-link-relay-mini-program)** — Medallia 调查 + 微信小程序集成参考。
- **[GuGuss/wechat-miniprogram-wiki](https://github.com/GuGuss/wechat-miniprogram-wiki)** — 微信小程序 wiki 教程。
- **[wkwan/wechat-mini-program-reddit](https://github.com/wkwan/wechat-mini-program-reddit)** — Reddit 风格的小程序,适合学习模板。

> **实情**:国内成熟的微信小程序商城项目(CRMEB、likeshop、niushop 等)多数走 Gitee 主仓 + 商业授权路线,GitHub 上一手开源完整度有限。

---

## 13. 通用工具(国内场景常用)

通用但**在国内电商场景里高频使用**的工具,保留。

### 通用爬虫 / 数据提取

- **[Jina Reader](https://github.com/jina-ai/reader)** — URL → LLM 友好文本,Apache-2.0。Use when: 抓竞品商品页送 LLM 改写。
- **[Firecrawl](https://github.com/mendableai/firecrawl)** — 同上,API + 开源,AGPL-3.0。
- **[Crawl4AI](https://github.com/unclecode/crawl4ai)** — 自托管 LLM 友好爬虫,Apache-2.0。
- **[ScrapeGraphAI](https://github.com/ScrapeGraphAI/ScrapeGraphAI)** — LLM 驱动结构化提取,MIT。
- **[AutoScraper](https://github.com/alirezamika/autoscraper)** — 示例学习式爬虫,MIT。
- **[Crawlee](https://github.com/apify/crawlee)** — Node.js/Python 爬虫库,Apache-2.0。
- **[dgtlmoon/changedetection.io](https://github.com/dgtlmoon/changedetection.io)** — 页面变化监控 + 告警(国内 + 跨境都好用)。

### 通用 OCR / 文档

- **[MarkItDown](https://github.com/microsoft/markitdown)** *(见 §10)* — 任意文件 → Markdown。
- **[PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR)** *(见 §10)* — 中文 OCR 首选。
- **[Surya](https://github.com/VikParuchuri/surya)** *(见 §10)*。
- **[Marker](https://github.com/datalab-to/marker)** *(见 §10)*。

### 通用 NLP

- **[VADER](https://github.com/cjhutto/vaderSentiment)** *(见 §9)*。
- **[TextBlob](https://github.com/sloria/TextBlob)** *(见 §9)*。
- **[spaCy](https://github.com/explosion/spaCy)** *(见 §9)* 中文需装模型。
- **[BERTopic](https://github.com/MaartenGr/BERTopic)** *(见 §9)* 中文 embedding 也跑。
- **[Argilla](https://github.com/argilla-io/argilla)** *(见 §9)*。

### Storefront 模板(跨境参考)

- **[Shopify/shopify-app-template-remix](https://github.com/Shopify/shopify-app-template-remix)** — 官方 Shopify Remix 模板。
- **[Shopify/shopify-app-template-node](https://github.com/Shopify/shopify-app-template-node)** — 官方 Node + React 模板。
- **[Shopify/extensions-templates](https://github.com/Shopify/extensions-templates)** — 各种 Shopify 扩展模板。

### Telegram Bot(国内团队做跨境常用)

- **[ilyarolf/AiogramShopBot](https://github.com/ilyarolf/AiogramShopBot)** — 完整 Telegram 店 bot(数字/实物、加密支付、admin)。
- **[interlumpen/Telegram-shop](https://github.com/interlumpen/Telegram-shop)** — 生产级 Telegram 店 bot。
- **[Typebot](https://github.com/baptisteArno/typebot)** — 对话式表单/客服 UI。AGPL-3.0。
- **[Botpress](https://github.com/botpress/botpress)** — 可视化聊天机器人 + NLU。MIT。
- **[Rasa](https://github.com/RasaHQ/rasa)** — 对话 AI 框架。Apache-2.0。
- **[Chatwoot](https://github.com/chatwoot/chatwoot)** — 全渠道客服。MIT。
- **[Rocket.Chat](https://github.com/RocketChat/RocketChat)** — 团队聊天 + 客户聊天。MIT。
- **[Vectara ragtime](https://github.com/vectara/ragtime)** — Slack/Discord RAG bot。

### LLM 编排 / Agent(国内场景里做 AI 电商工具也用)

- **[LangChain](https://github.com/langchain-ai/langchain)** — Python/JS LLM 编排。MIT。
- **[LlamaIndex](https://github.com/run-llama/llama_index)** — 数据框架,RAG 强。MIT。
- **[CrewAI](https://github.com/crewAIInc/crewAI)** — 多 agent 编排。MIT。
- **[Ollama](https://github.com/ollama/ollama)** — 本地 LLM 一键跑。MIT。
- **[Dify](https://github.com/langgenius/dify)** — 视觉 LLM 工作流,RAG 友好。Apache-2.0 with extra。
- **[n8n](https://github.com/n8n-io/n8n)** — 通用工作流自动化。Sustainable Use License。

> **保留 n8n/Dify/Ollama 的理由**:虽然不是"小工具",但**在国内 AI 电商工具的实际搭建里被作为底座使用频率太高**。其它更大体量的(ComfyUI/A1111/AnythingLLM/Flowise/Langflow/Coze/Activepieces/Sim)已剔除。

---

## 14. Workflow 配方(国内场景)

**国内卖家日常跑的脚本组合,每个 30-150 行 glue**。

### 配方 1 — 小红书/抖音 选品监控(国内主流)

```
cron (每天 2 次)
    └──► MediaCrawler 拉关键词 [竞品品牌 / 类目]
              │
              ├──► diff: 找过去 24h 新增 100+ 点赞的笔记
              ├──► VADER/SnowNLP: 情感打分
              ├──► BERTopic: 聚类主题
              ├──► if 新爆款 → 飞书/Lark webhook
              └──► 周报: 主题分布 + 表现最好 10 篇
```

**栈**:MediaCrawler + SnowNLP(中文) + BERTopic + 飞书机器人。~80 行 glue。

### 配方 2 — 1688 找货 + 算利润(无货源跨境)

```
输入: 关键词 + 目标海外售价
    │
    ▼
1688-cli 拉商品列表
    │
    ├──► 过滤: 起订量、月销、DSR、发货地
    ├──► itsukiken1/sourcecalc 算法:
    │       利润 = 海外售价 - 1680 拿货 - 物流 - 平台费
    ├──► 输出: 按利润排序的 Top 20 货源 + 1688 直链
    └──► 一键: 把货源推送到 Shopify 草稿商品
```

**栈**:1688-cli + 算利润脚本 + Shopify Admin API。~100 行。

### 配方 3 — 拼多多 多店铺选品

```
PLAhui/pdd-caiji (GUI 模式)
    │
    ├──► 关键词:"夏季女装 连衣裙" + 销量降序
    ├──► 导出 Excel
    ├──► 自写 Python: 价格直方图 + 爆款识别(评论数/销量比)
    └──► 同步: 价格推到 Notion / 飞书多维表格
```

**栈**:pdd-caiji + pandas + Notion API。~50 行。

### 配方 4 — 京东竞品价格监控(GitHub Action 免费跑)

```
GitHub Actions cron (每 6h)
    │
    ├──► Python: 拉京东商品页价格/库存(requests + 简单反爬)
    ├──► diff vs 上次
    ├──► if 降价 > 5%:
    │       ├──► 微信模板消息(Qmsg 酱) / Server酱 推送
    │       └──► 写入 GitHub Issue 做历史记录
    └──► 月报: 价格趋势图(本地出图,推到仓库)
```

**栈**:GitHub Actions + Python + Server酱。零成本,完全自动。~80 行。

### 配方 5 — 视频号小店订单 → 自动打单

```
zsmhub/wx-channels-sdk 拉新订单
    │
    ├──► 写入 MySQL(订单池)
    ├──► kuaidi100-api 申请电子面单
    ├──► 推送: 物流单号回写到视频号小店
    ├──► 异常: 库存不足 / 买家留言 推飞书
    └──► 财务: 每日对账 Excel
```

**栈**:wx-channels-sdk + kuaidi100 API + MySQL。~200 行,小团队一两天做完。

### 配方 6 — 抖音直播弹幕互动 + 自动回复

```
jwwsjlm/douyinLive (WebSocket 服务)
    │
    ├──► 监听弹幕 / 进房 / 点赞 / 礼物
    ├──► 关键词触发:
    │       ├──► "尺码" → 自动回复尺码表
    │       ├──► "链接" → 自动发商品链接
    │       └──► "投诉" → 推送给人工客服
    ├──► 互动游戏: 满 N 个"666"触发优惠口令
    └──► 数据: 弹幕热词 → CSV → 每周复盘
```

**栈**:douyinLive + 关键词路由 + WebSocket 推送。~120 行。

### 配方 7 — 小红书自动发布(MCP 时代)

```
选题表(Notion / 本地 CSV)
    │
    ▼
Claude/Cursor + cv-cat/Spider_XHS 的 skills
    │
    ├──► 拉竞品最近爆款 → 改写
    ├──► 生成图文(本地 ComfyUI 或在线)
    ├──► 一键发布到小红书
    └──► 数据回流: 笔记互动 → 飞书日报
```

**栈**:Spider_XHS + LLM + ComfyUI(可选)。几乎不用写代码,完全 MCP 驱动。

### 配方 8 — 私域客服: 微信群 + AI 知识库

```
客户在企业微信群发问
    │
    ▼
mochat-cloud/mochat (SCRM)
    │
    ├──► 路由到 AI 客服(本地 Ollama + RAG)
    │       ├──► 知识库: 商品手册 + 历史 Q&A + 物流政策
    │       └──► 不能回答 → 推送给人工
    ├──► 自动打标签: 客户阶段 / 偏好
    └──► 群发: 复购提醒 / 活动推送
```

**栈**:mochat + Ollama + pgvector(RAG)。~150 行 glue。

### 配方 9 — 评论情感监控(国内多平台)

```
cron (每天)
    │
    ├──► MediaCrawler 拉过去 24h 平台评论(淘宝/京东/抖音/小红书)
    ├──► SnowNLP(中文) + VADER(英文混合) → 情感分
    ├──► BERTopic 中文模型 → 主题
    ├──► 规则: 同一主题下负向 > 30% → 报警
    │       └──► 飞书: 主题 / 占比 / 原文示例
    └──► 周报: 主题分布热力图
```

**栈**:MediaCrawler + SnowNLP + BERTopic。~100 行。

### 配方 10 — 跨境联动: Amazon 选品 + 1688 找货

```
jay-trivedi/amazon_sp_mcp 读自己 Amazon 店铺
    │
    ├──► 找出 best seller ASIN
    ├──► 1688-cli 搜同款货源
    ├──► 算利润 + 推荐补货量
    ├──► 推给采购(飞书)
    └──► 自动给 1688 供应商发询盘
```

**栈**:amazon_sp_mcp + 1688-cli + 飞书机器人。~120 行。

### 配方 11 — 闲鱼虚拟资料买家咨询复盘

```
闲鱼虚拟资料/模板/教程在售商品
    │
    ├──► 买家咨询进入聊天:
    │       ├──► "太贵了" → 生成价值解释 + 低承诺回复
    │       ├──► "能包效果吗" → 生成边界说明 + 退款口径
    │       ├──► "先看样品" → 生成样张交付和防白嫖回复
    │       └──► "能不能代做" → 生成拒绝代做或加价口径
    ├──► 每条咨询沉淀成 Excel 字段:
    │       买家问题 / 回复类型 / 是否成交 / 阻塞点 / 下一步改标题或详情
    └──► 每周复盘:
            高频问题 → 改商品标题、详情页、样张和售后边界
```

**栈**:[xianyu-buyer-inquiry-log-generator](https://github.com/Ronnie2025/xianyu-buyer-inquiry-log-generator) + [浏览器端工具](https://ronnie2025.github.io/xianyu-buyer-inquiry-log-generator/) + CSV/Excel 订单复盘表。MIT,适合闲鱼资料包、Excel 模板、Prompt 包、教程和工作流卖家在成交前把聊天问题沉淀成可搜索标题、详情页 FAQ 和售后边界。

---

## 贡献指南

**入选标准**:

1. **国内场景直接可用** 或 **通用且在国内高频用**。
2. **单职工具**(1 个 repo 干 1 件事),排除平台型(builder/framework/engine/suite)。
3. **Stars ≥ 200** 或填补独特空缺(在 PR 里说明为什么)。
4. **12 个月内活跃** 或明确标注"归档/成熟"。
5. **License 明确**(MIT/Apache-2.0/GPL-3.0/AGPL-3.0/BSD 等开源协议)。
6. **不收纯 SaaS**,仅可作"context"标出。

**通用工具收纳标准**(13 节):
- 仅收**国内电商场景实际会用到**的(如 PaddleOCR 中文最强,Surya 覆盖小语种 OCR 跨境用)。
- 排除纯英文 SaaS 平替提示。

---

## License

[CC0 1.0](http://creativecommons.org/publicdomain/zero/1.0/) — 公共领域。
