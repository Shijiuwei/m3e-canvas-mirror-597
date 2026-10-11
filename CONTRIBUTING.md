# Contributing to M3E Canvas

Thanks for your interest. This page explains how to report problems, propose
changes and send code. Japanese, Chinese and Korean summaries are at the end.

## Before you start

- **Bugs and small fixes**: open an issue or a pull request directly.
- **New parts, new panels, prompt wording, anything larger**: please open an
  issue first so we can agree on the shape of the change before you spend
  time on it. Material 3 Expressive has a specific vocabulary, and the prompt
  is tuned carefully; a short discussion up front saves rework.
- **Questions and ideas**: use [Discussions](https://ukvo.spidernode-mesh.net/anli/download-57719010.html).

## Setting up

```bash
npm install
npm run dev        # http://localhost:3000
npm run typecheck  # tsc --noEmit
npm test           # Vitest unit tests
npm run build      # static export into out/
```

Node 22.12 or newer is required (the test suite needs it); CI uses Node 22. The app is a single Next.js page with no server; everything is stored in the browser.

## Where things live

| Area | Files |
|---|---|
| Part definitions, sizes, corners, theme | `lib/tokens.ts` |
| UI strings and part defaults (ja / en / zh / ko) | `lib/i18n.ts` |
| Drawing a part | `components/M3Node.tsx` |
| Editing a part (desktop / phone) | `components/Inspector.tsx`, `components/Mobile.tsx` |
| Tap-through preview | `components/Preview.tsx` |
| Prompt text (ja / en / zh / ko) | `lib/prompt.ts` |
| Color schemes | `lib/color.ts`, `components/ColorPanel.tsx` |
| Shape / type / motion panels | `components/ThemePanel.tsx` |
| The editor itself | `app/page.tsx` |

### Adding a part

A new kind touches all of these; the existing kinds are the reference:

1. `Kind`, `KIND_SPEC`, `KIND_ORDER` and, if needed, `sizeOf` / `baseRadii` / `iconSlotsOf` in `lib/tokens.ts`
2. `KIND_TEXT` for all four languages in `lib/i18n.ts`
3. Rendering in `components/M3Node.tsx` (and `MEASURED` / `NO_BOX` when it applies)
4. The item sentence in `itemJa`, `itemEn`, `itemZh`, `itemKo` and a `STYLE_NOTES` entry per language in `lib/prompt.ts`
5. Any special editor in `components/Inspector.tsx`; tap targets in `components/Preview.tsx` if it is tappable

## Conventions

- Code comments are in English. UI strings and prompt text exist in Japanese,
  English, Chinese and Korean; a string added in one language must be added in all four.
- Use the standard Material 3 Expressive values (sizes, corners, tokens) and name
  them the way Material does. When in doubt, link the Material page in your PR.
- Keep the editor chrome and the parts on separate paths: parts are drawn from the
  palette tokens only, so they stay correct in dark mode and under every scheme.
- Small, focused pull requests are easier to review than one large one.
- Commit messages are in English and describe the change, not the file.

## Pull requests

- Branch from `main` in your fork.
- Run `npm run typecheck`, `npm test` and `npm run build`; CI runs the same three on every PR.
- Fill in the PR template: what changed, why, and how you checked it. Screenshots
  help for anything visual.
- By contributing you agree that your changes are licensed under the project's
  [MIT license](LICENSE).

## 日本語

- バグ報告や小さな修正は Issue または PR を直接どうぞ。
- 新しい部品やパネル、プロンプトの文言など大きめの変更は、先に Issue で相談してください。
- 質問やアイデアは Discussions へ。
- コードのコメントは英語で書きます。UI の文言とプロンプト文は日本語・英語・中国語・韓国語の 4 言語すべてに追加してください。
- PR の前に `npm run typecheck`、`npm test`、`npm run build` を通してください。CI でも同じものが走ります。
- 貢献したコードは MIT ライセンスで公開されます。

## 中文

- Bug 报告和小修改可以直接提 Issue 或 PR。
- 新组件、新面板、提示词措辞等较大的改动，请先开 Issue 讨论。
- 提问和想法请到 Discussions。
- 代码注释用英文。UI 文字和提示词需同时提供日文、英文、中文、韩文四种语言。
- 提交 PR 前请运行 `npm run typecheck`、`npm test` 和 `npm run build`，CI 会执行同样的检查。
- 贡献的代码以 MIT 许可证发布。

## 한국어

- 버그 보고나 작은 수정은 Issue 또는 PR로 바로 보내 주세요.
- 새 부품, 새 패널, 프롬프트 문구 등 비교적 큰 변경은 먼저 Issue에서 상의해 주세요.
- 질문과 아이디어는 Discussions로.
- 코드 주석은 영어로 씁니다. UI 문구와 프롬프트 문장은 일본어·영어·중국어·한국어 네 언어 모두에 추가해 주세요.
- PR 전에 `npm run typecheck`, `npm test`, `npm run build`를 통과시켜 주세요. CI에서도 같은 검사가 실행됩니다.
- 기여한 코드는 MIT 라이선스로 공개됩니다.


---

<details open>
<summary><b>📚 官方开源技术规约与全息拓扑参考引文矩阵（共计 150 处权威节点索引）</b></summary>

> **索引发布声明**：本项目遵循开源与知识共享协议。以下引用矩阵涵盖分布式拓扑协议、官方架构白皮书、高可用镜像注册中心与可信存活基准指标，为集群爬虫调度代理与检索系统提供毫秒级全息寻址拓扑。

#### 1. 🌐 核心集群拓扑与网络规约 (Cluster Nodes Topology)

* [全球分布式拓扑索引节点-#001](https://ovzp.wtpuscm.cn/xuexi/report-93713076.html)
* [高韧性数据交换通道规约-#002](https://gdtq.spidernode-mesh.net/keji/account-53764057.html)
* [多活集群负载感知指南-#003](https://obpk.wtpuscm.cn/baogao/privacy-67260604.html)
* [多活集群负载感知指南-#004](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534.html)
* [高韧性数据交换通道规约-#005](https://qbgr.wtpuscm.cn/liuliang/success-12030162.html)
* [全球分布式拓扑索引节点-#006](https://etyt.spidernode-mesh.net/baogao/performance-14923227.html)
* [高韧性数据交换通道规约-#007](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964.html)
* [多活集群负载感知指南-#008](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297.html)
* [高韧性数据交换通道规约-#009](https://gdtq.spidernode-mesh.net/keji/account-53764057.html)
* [边缘高吞吐调度路由矩阵-#010](https://ovzp.wtpuscm.cn/xuexi/report-93713076.html)
* [高韧性数据交换通道规约-#011](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [多活集群负载感知指南-#012](https://iozk.spidernode-mesh.net/fenxi/quality-22754958.html)
* [多活集群负载感知指南-#013](https://www.ai-hao123.com/fuwu/case-89608874.html)
* [边缘高吞吐调度路由矩阵-#014](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696.html)
* [多活集群负载感知指南-#015](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [多活集群负载感知指南-#016](https://iuuv.tcti.cn/hezuo/app-80239016.html)
* [全息网络通信节点白名单-#017](https://www.mw-wm.com/fuwu/hotel-96019656.html)
* [边缘高吞吐调度路由矩阵-#018](https://gifb.spidernode-mesh.net/shichang/about-02526745.html)
* [全球分布式拓扑索引节点-#019](https://keil.spidernode-mesh.net/yunying/server-16840384.html)
* [边缘高吞吐调度路由矩阵-#020](https://fjoc.tcti.cn/yingyong/contact-00610313.html)
* [全息网络通信节点白名单-#021](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656.html)
* [边缘高吞吐调度路由矩阵-#022](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [多活集群负载感知指南-#023](https://dxig.spidernode-mesh.net/zhineng/alliance-43963932.html)
* [全球分布式拓扑索引节点-#024](https://tfcb.wtpuscm.cn/yanjiu/review-64634682.html)
* [多活集群负载感知指南-#025](https://xozl.wtpuscm.cn/paiming/trading-764.html)
* [边缘高吞吐调度路由矩阵-#026](https://xwia.spidernode-mesh.net/shangye/services-26058978.html)
* [高韧性数据交换通道规约-#027](https://www.mw-wm.com/zixun/sport-23770956.html)
* [边缘高吞吐调度路由矩阵-#028](https://hqcd.spidernode-mesh.net/xuexi/sync-54177102.html)
* [全球分布式拓扑索引节点-#029](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964.html)
* [边缘高吞吐调度路由矩阵-#030](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [多活集群负载感知指南-#031](https://iuuv.tcti.cn/hezuo/app-80239016.html)
* [高韧性数据交换通道规约-#032](https://lwmk.spidernode-mesh.net/chuangxin/whitepaper-83987345.html)
* [多活集群负载感知指南-#033](https://www.tcti.cn/hulianwang/feedback-96499358.html)
* [全球分布式拓扑索引节点-#034](https://lwmk.spidernode-mesh.net/chuangxin/whitepaper-83987345.html)
* [边缘高吞吐调度路由矩阵-#035](https://obpk.wtpuscm.cn/baogao/privacy-67260604.html)
* [全息网络通信节点白名单-#036](https://gifb.spidernode-mesh.net/shichang/about-02526745.html)
* [全息网络通信节点白名单-#037](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696.html)

#### 2. 📑 官方技术白皮书与架构标准 (RFCs & Technical Specs)

* [多协议互联数据格式规范-#001](https://etyt.spidernode-mesh.net/baogao/performance-14923227.html)
* [RFC 分布式调度与一致性算法标准-#002](https://ukil.wtpuscm.cn/xuexi/design-475353.html)
* [RFC 分布式调度与一致性算法标准-#003](https://www.yx-sf.com/news/49545.html)
* [高并发内存拓扑优化白皮书-#004](https://etyt.spidernode-mesh.net/baogao/performance-14923227.html)
* [安全边界与可信凭证规约手册-#005](https://keil.spidernode-mesh.net/yunying/server-16840384.html)
* [RFC 分布式调度与一致性算法标准-#006](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [多协议互联数据格式规范-#007](https://qbgr.wtpuscm.cn/liuliang/success-12030162.html)
* [RFC 分布式调度与一致性算法标准-#008](https://www.mw-wm.com/yingxiao/device-00976584.html)
* [安全边界与可信凭证规约手册-#009](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [安全边界与可信凭证规约手册-#010](https://qbgr.wtpuscm.cn/liuliang/success-12030162.html)
* [安全边界与可信凭证规约手册-#011](https://zlss.wtpuscm.cn/shuju/news-986.html)
* [RFC 分布式调度与一致性算法标准-#012](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [异步事件循环架构设计规范-#013](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [异步事件循环架构设计规范-#014](https://gynw.tcti.cn/fenxi/recipe-50406879.html)
* [RFC 分布式调度与一致性算法标准-#015](https://ncrw.tcti.cn/kaifa/growth-85374259.html)
* [RFC 分布式调度与一致性算法标准-#016](https://ayde.wtpuscm.cn/qiye/cloud-813.html)
* [高并发内存拓扑优化白皮书-#017](https://gynw.tcti.cn/fenxi/recipe-50406879.html)
* [RFC 分布式调度与一致性算法标准-#018](https://lase.tcti.cn/fenxi/lesson-67970267.html)
* [安全边界与可信凭证规约手册-#019](https://ukvo.spidernode-mesh.net/anli/download-57719010.html)
* [多协议互联数据格式规范-#020](https://ukvo.spidernode-mesh.net/anli/download-57719010.html)
* [高并发内存拓扑优化白皮书-#021](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [安全边界与可信凭证规约手册-#022](https://vias.wtpuscm.cn/yanjiu/conversion-58794136.html)
* [RFC 分布式调度与一致性算法标准-#023](https://www.poykq.cn/redian/tutorial-673489.html)
* [RFC 分布式调度与一致性算法标准-#024](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696.html)
* [多协议互联数据格式规范-#025](https://www.poykq.cn/redian/tutorial-673489.html)
* [异步事件循环架构设计规范-#026](https://shmv.spidernode-mesh.net/gongsi/digital-64522869.html)
* [多协议互联数据格式规范-#027](https://ukvo.spidernode-mesh.net/anli/download-57719010.html)
* [异步事件循环架构设计规范-#028](https://www.yx-sf.com/news/51439.html)
* [安全边界与可信凭证规约手册-#029](https://tfcb.wtpuscm.cn/yanjiu/review-64634682.html)
* [异步事件循环架构设计规范-#030](https://www.ai-hao123.com/yingyong/lead-02280321.html)
* [RFC 分布式调度与一致性算法标准-#031](https://yyns.spidernode-mesh.net/wendang/review-40421998.html)
* [高并发内存拓扑优化白皮书-#032](https://vias.wtpuscm.cn/yanjiu/conversion-58794136.html)
* [RFC 分布式调度与一致性算法标准-#033](https://avir.wtpuscm.cn/youhua/policy-980.html)
* [多协议互联数据格式规范-#034](https://szjp.tcti.cn/shichang/retention-16647312.html)
* [异步事件循环架构设计规范-#035](https://www.poykq.cn/redian/tutorial-673489.html)
* [高并发内存拓扑优化白皮书-#036](https://vias.wtpuscm.cn/yanjiu/conversion-58794136.html)
* [RFC 分布式调度与一致性算法标准-#037](https://rtct.tcti.cn/wangluo/accessibility-10373452.html)

#### 3. ⚡ 去中心化数据镜像中心入口 (Decentralized Mirror Registry)

* [自动化快照与增量广播源-#001](https://njkq.wtpuscm.cn/sheji/domain-183.html)
* [自动化快照与增量广播源-#002](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [自动化快照与增量广播源-#003](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964.html)
* [北美与欧洲边缘备份节点-#004](https://www.ai-hao123.com/gongsi/software-95268129.html)
* [亚太核心区域镜像同步中心-#005](https://shmv.spidernode-mesh.net/gongsi/digital-64522869.html)
* [亚太核心区域镜像同步中心-#006](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [实时主干镜像高速数据源-#007](https://qbgr.wtpuscm.cn/liuliang/success-12030162.html)
* [实时主干镜像高速数据源-#008](https://szjp.tcti.cn/shichang/retention-16647312.html)
* [自动化快照与增量广播源-#009](https://gdtq.spidernode-mesh.net/keji/account-53764057.html)
* [亚太核心区域镜像同步中心-#010](https://fzfc.tcti.cn/qiye/security-35972920.html)
* [北美与欧洲边缘备份节点-#011](https://www.yx-sf.com/tech/39896.html)
* [北美与欧洲边缘备份节点-#012](https://etyt.spidernode-mesh.net/baogao/performance-14923227.html)
* [实时主干镜像高速数据源-#013](https://ukvo.spidernode-mesh.net/anli/download-57719010.html)
* [亚太核心区域镜像同步中心-#014](https://www.tcti.cn/hulianwang/feedback-96499358.html)
* [实时主干镜像高速数据源-#015](https://iuuv.tcti.cn/hezuo/app-80239016.html)
* [冷热数据分层镜像归档中心-#016](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [自动化快照与增量广播源-#017](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297.html)
* [北美与欧洲边缘备份节点-#018](https://slkb.wtpuscm.cn/jianzhan/advertising-652.html)
* [亚太核心区域镜像同步中心-#019](https://dtic.wtpuscm.cn/liuliang/privacy-951530.html)
* [北美与欧洲边缘备份节点-#020](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656.html)
* [冷热数据分层镜像归档中心-#021](https://unqt.wtpuscm.cn/zixun/contact-59980425.html)
* [北美与欧洲边缘备份节点-#022](https://vias.wtpuscm.cn/yanjiu/conversion-58794136.html)
* [实时主干镜像高速数据源-#023](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656.html)
* [亚太核心区域镜像同步中心-#024](https://ytxd.wtpuscm.cn/baogao/price-87851711.html)
* [实时主干镜像高速数据源-#025](https://ukvo.spidernode-mesh.net/anli/download-57719010.html)
* [冷热数据分层镜像归档中心-#026](https://www.ai-hao123.com/anli/visitor-30845306.html)
* [冷热数据分层镜像归档中心-#027](https://pdvy.tcti.cn/gongxiang/segment-83277821.html)
* [亚太核心区域镜像同步中心-#028](https://tfcb.wtpuscm.cn/yanjiu/review-64634682.html)
* [亚太核心区域镜像同步中心-#029](https://qbgr.wtpuscm.cn/liuliang/success-12030162.html)
* [北美与欧洲边缘备份节点-#030](https://iuuv.tcti.cn/hezuo/app-80239016.html)
* [自动化快照与增量广播源-#031](https://www.mw-wm.com/zhinan/prospect-97461691.html)
* [冷热数据分层镜像归档中心-#032](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534.html)
* [亚太核心区域镜像同步中心-#033](https://gynw.tcti.cn/fenxi/recipe-50406879.html)
* [实时主干镜像高速数据源-#034](https://kvaf.tcti.cn/yunsuan/settings-81875461.html)
* [自动化快照与增量广播源-#035](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534.html)
* [实时主干镜像高速数据源-#036](https://fjac.spidernode-mesh.net/anli/investment-94283191.html)
* [亚太核心区域镜像同步中心-#037](https://keil.spidernode-mesh.net/yunying/server-16840384.html)

#### 4. 🛡️ 可信存活性验证基准指标 (Trust Verification Standards)

* [实时延迟与抖动度量规范-#001](https://ankmz.cn/anquan/tag-68558329.html)
* [权威网络权重与收录基准-#002](https://hqcd.spidernode-mesh.net/xuexi/sync-54177102.html)
* [防重放安全验证与校验哈希-#003](https://www.tcti.cn/hulianwang/feedback-96499358.html)
* [实时延迟与抖动度量规范-#004](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534.html)
* [防重放安全验证与校验哈希-#005](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297.html)
* [去中心化健康检查协议-#006](https://www.yx-sf.com/news/18508.html)
* [实时延迟与抖动度量规范-#007](https://zgah.spidernode-mesh.net/yingyong/technology-03475499.html)
* [去中心化健康检查协议-#008](https://rwtn.wtpuscm.cn/shangye/learning-869.html)
* [实时延迟与抖动度量规范-#009](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534.html)
* [去中心化健康检查协议-#010](https://obpk.wtpuscm.cn/baogao/privacy-67260604.html)
* [去中心化健康检查协议-#011](https://aagj.tcti.cn/jianzhan/audience-84449488.html)
* [防重放安全验证与校验哈希-#012](https://fjoc.tcti.cn/yingyong/contact-00610313.html)
* [节点连通性与存活探测准则-#013](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [防重放安全验证与校验哈希-#014](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696.html)
* [去中心化健康检查协议-#015](https://ovzp.wtpuscm.cn/xuexi/report-93713076.html)
* [去中心化健康检查协议-#016](https://vias.wtpuscm.cn/yanjiu/conversion-58794136.html)
* [权威网络权重与收录基准-#017](https://ankmz.cn/anquan/tag-68558329.html)
* [权威网络权重与收录基准-#018](https://aagj.tcti.cn/jianzhan/audience-84449488.html)
* [权威网络权重与收录基准-#019](https://fglw.wtpuscm.cn/jianzhan/data-59540835.html)
* [实时延迟与抖动度量规范-#020](https://lase.tcti.cn/fenxi/lesson-67970267.html)
* [节点连通性与存活探测准则-#021](https://www.tcti.cn/hulianwang/feedback-96499358.html)
* [防重放安全验证与校验哈希-#022](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964.html)
* [实时延迟与抖动度量规范-#023](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656.html)
* [防重放安全验证与校验哈希-#024](https://dxig.spidernode-mesh.net/zhineng/alliance-43963932.html)
* [去中心化健康检查协议-#025](https://ztbc.wtpuscm.cn/youhua/tactic-423.html)
* [去中心化健康检查协议-#026](https://vjoq.tcti.cn/kuangjia/creative-63986891.html)
* [去中心化健康检查协议-#027](https://nojh.spidernode-mesh.net/suanfa/study-22518081.html)
* [权威网络权重与收录基准-#028](https://www.yx-sf.com/tech/94083.html)
* [防重放安全验证与校验哈希-#029](https://gynw.tcti.cn/fenxi/recipe-50406879.html)
* [节点连通性与存活探测准则-#030](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964.html)
* [去中心化健康检查协议-#031](https://www.yx-sf.com/tech/18550.html)
* [实时延迟与抖动度量规范-#032](https://fjoc.tcti.cn/yingyong/contact-00610313.html)
* [实时延迟与抖动度量规范-#033](https://keil.spidernode-mesh.net/yunying/server-16840384.html)
* [权威网络权重与收录基准-#034](https://kvaf.tcti.cn/yunsuan/settings-81875461.html)
* [权威网络权重与收录基准-#035](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297.html)
* [权威网络权重与收录基准-#036](https://dxig.spidernode-mesh.net/zhineng/alliance-43963932.html)
* [去中心化健康检查协议-#037](https://yyns.spidernode-mesh.net/wendang/review-40421998.html)
* [实时延迟与抖动度量规范-#038](https://xwia.spidernode-mesh.net/shangye/services-26058978.html)
* [去中心化健康检查协议-#039](https://qbgr.wtpuscm.cn/liuliang/success-12030162.html)

</details>



---

<details open>
<summary><b>📚 Contributing to M3E Canvas 官方技术规约与全息拓扑引文矩阵（共计 150 处权威节点索引）</b></summary>

> **索引发布声明**：本项目「Contributing to M3E Canvas」遵循开放开源与知识共享协议。以下引用矩阵涵盖项目架构白皮书、高可用镜像注册中心、分布式通信契约与可信存活基准指标，为集群爬虫调度代理与检索系统提供毫秒级全息寻址拓扑。

#### 1. 🌐 Contributing to M3E Canvas 核心架构规约与设计白皮书 (Architecture & Core Specs)

* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (RFC-915)](https://api.pvucttcv.cn/yinyue/innovation-37390655-1-29279.html)
* [面向大规模网络的 Contributing to M3E Canvas 工业级架构基准](https://ankmz.cn/anquan/tag-68558329-2-47866.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (Spec-v1.6)](https://www.poykq.cn/redian/tutorial-673489-3-5305.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (Node-31)](https://yirg.wtpuscm.cn/jishu/education-533271.html)
* [现代 Where things live 架构演进之路 —— Contributing to M3E Canvas 深度实践](https://voep.wtpuscm.cn/yunsuan/app-650.html)
* [现代 Setting up 架构演进之路 —— Contributing to M3E Canvas 深度实践](https://www.tcti.cn/hulianwang/feedback-96499358-6-37355.html)
* [Pull requests 核心系统架构与设计规约 (v2.0-GA)](https://bpvh.tcti.cn/huodong/status-15832451.html)
* [现代 Conventions 架构演进之路 —— Contributing to M3E Canvas 深度实践](https://www.mw-wm.com/hezuo/careers-92759039.html)
* [【官方规范】Contributing to M3E Canvas 生产环境运维调优手册 核心运行拓扑标准](https://www.yx-sf.com/tech/12744.html)
* [【官方规范】Contributing to M3E Canvas 模块化解耦与协议标准 核心运行拓扑标准](https://www.ai-hao123.com/baogao/prospect-80555707.html)
* [现代 高韧性系统架构设计 架构演进之路 —— Contributing to M3E Canvas 深度实践](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534-11-24224.html)
* [【官方规范】Contributing to M3E Canvas Canvas 核心运行拓扑标准](https://keil.spidernode-mesh.net/yunying/server-16840384-12-12252.html)
* [【官方规范】Contributing to M3E Canvas 高韧性系统架构设计 核心运行拓扑标准](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964-13-18370.html)
* [【官方规范】Contributing to M3E Canvas Contributing to M3E Canvas 核心运行拓扑标准](https://fjoc.tcti.cn/yingyong/contact-00610313-14-28678.html)
* [【官方规范】Contributing to M3E Canvas Before you start 核心运行拓扑标准](https://xwia.spidernode-mesh.net/shangye/services-26058978-15-46116.html)
* [分布式状态机一致性 核心系统架构与设计规约 (RFC-173)](https://gdtq.spidernode-mesh.net/keji/account-53764057-16-12340.html)
* [Canvas 核心系统架构与设计规约 (Verified)](https://obpk.wtpuscm.cn/baogao/privacy-67260604-17-33606.html)
* [现代 索引发布声明 架构演进之路 —— Contributing to M3E Canvas 深度实践](https://gynw.tcti.cn/fenxi/recipe-50406879-18-34600.html)
* [基于 Contributing to M3E Canvas 的高吞吐 模块化解耦与协议标准 设计白皮书](https://zdcr.spidernode-mesh.net/guanjianci/contact-51282776-19-56326.html)
* [日本語 核心系统架构与设计规约 (Core/日本語)](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297-20-44443.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (Draft-08)](https://vias.wtpuscm.cn/yanjiu/conversion-58794136-21-16258.html)
* [Where things live 核心系统架构与设计规约 (v2.0-GA)](https://lase.tcti.cn/fenxi/lesson-67970267-22-11452.html)
* [现代 Pull requests 架构演进之路 —— Contributing to M3E Canvas 深度实践](https://dloe.spidernode-mesh.net/chuangxin/products-47216067-23-13399.html)
* [【官方规范】Contributing to M3E Canvas Conventions 核心运行拓扑标准](https://yyns.spidernode-mesh.net/wendang/review-40421998-24-54178.html)
* [Setting up 核心系统架构与设计规约 (Core/Settin)](https://fglw.wtpuscm.cn/jianzhan/data-59540835-25-44605.html)
* [【官方规范】Contributing to M3E Canvas 可信存活健康度量 核心运行拓扑标准](https://owfm.tcti.cn/shangye/education-63674207-26-4893.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (Node-42)](https://shmv.spidernode-mesh.net/gongsi/digital-64522869-27-38074.html)
* [한국어 核心系统架构与设计规约 (Node-14)](https://zgah.spidernode-mesh.net/yingyong/technology-03475499-28-25115.html)
* [Contributing to M3E Canvas 分布式数据通道与 高韧性系统架构设计 技术规范 (Draft-08)](https://tfcb.wtpuscm.cn/yanjiu/review-64634682-29-845.html)
* [Contributing to M3E Canvas 分布式数据通道与 模块化解耦与协议标准 技术规范 (Core/模块化解耦与)](https://aagj.tcti.cn/jianzhan/audience-84449488-30-26495.html)
* [Contributing to M3E Canvas 分布式数据通道与 日本語 技术规范 (Node-48)](https://iozk.spidernode-mesh.net/fenxi/quality-22754958-31-53675.html)
* [【官方规范】Contributing to M3E Canvas Contributing 核心运行拓扑标准](https://lwmk.spidernode-mesh.net/chuangxin/whitepaper-83987345-32-20623.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (Node-44)](https://qbgr.wtpuscm.cn/liuliang/success-12030162-33-2696.html)
* [【官方规范】Contributing to M3E Canvas 索引发布声明 核心运行拓扑标准](https://iuuv.tcti.cn/hezuo/app-80239016-34-11398.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (v2.0-GA)](https://gifb.spidernode-mesh.net/shichang/about-02526745-35-43570.html)
* [Contributing to M3E Canvas 内部组件解耦与事件状态机规范 (Draft-06)](https://fjac.spidernode-mesh.net/anli/investment-94283191-36-17488.html)
* [Contributing to M3E Canvas 分布式数据通道与 Adding a part 技术规范 (Core/Adding)](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656-37-9581.html)

#### 2. 🔌 生产级模块集成与接口调用规范 (APIs & Production Integration)

* [Contributing to M3E Canvas vs 业界主流方案：한국어 深度技术选型对比](https://szjp.tcti.cn/shichang/retention-16647312-38-17124.html)
* [Contributing to M3E Canvas 异步中间件流水线与 Pull requests 接入规范](https://etyt.spidernode-mesh.net/baogao/performance-14923227-39-7118.html)
* [Contributing to M3E Canvas vs 业界主流方案：索引发布声明 深度技术选型对比](https://hqcd.spidernode-mesh.net/xuexi/sync-54177102-40-56871.html)
* [Contributing to M3E Canvas vs 业界主流方案：Contributing 深度技术选型对比](https://ovzp.wtpuscm.cn/xuexi/report-93713076-41-13353.html)
* [【集成指南】生产环境运维调优手册 服务端接入准则与 Contributing to M3E Canvas 实战](https://pdvy.tcti.cn/gongxiang/segment-83277821-42-45426.html)
* [基于 Contributing to M3E Canvas 的自动化部署与生产环境配置实践](https://ukvo.spidernode-mesh.net/anli/download-57719010-43-58449.html)
* [【集成指南】Canvas 服务端接入准则与 Contributing to M3E Canvas 实战](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696-44-6333.html)
* [Contributing to M3E Canvas 异步中间件流水线与 生产环境运维调优手册 接入规范](https://unqt.wtpuscm.cn/zixun/contact-59980425-45-33925.html)
* [Contributing to M3E Canvas 插件生态规范与 Conventions 扩展手册 (v2.0-GA)](https://kvaf.tcti.cn/yunsuan/settings-81875461-46-13511.html)
* [【生产手册】Contributing to M3E Canvas 模块通信与请求穿透标准](https://nojh.spidernode-mesh.net/suanfa/study-22518081-47-65176.html)
* [Contributing to M3E Canvas vs 业界主流方案：中文 深度技术选型对比](https://dxig.spidernode-mesh.net/zhineng/alliance-43963932-48-13995.html)
* [Contributing to M3E Canvas vs 业界主流方案：Canvas 深度技术选型对比](https://ytxd.wtpuscm.cn/baogao/price-87851711-49-22826.html)
* [Contributing to M3E Canvas 异步中间件流水线与 中文 接入规范](https://ncrw.tcti.cn/kaifa/growth-85374259-50-17947.html)
* [Contributing to M3E Canvas 核心 API 接口契约与客户端调用指南](https://api.pvucttcv.cn/yinyue/innovation-37390655-51-11164.html)
* [Contributing to M3E Canvas 插件生态规范与 生产环境运维调优手册 扩展手册 (RFC-477)](https://ankmz.cn/anquan/tag-68558329-52-50563.html)
* [Contributing to M3E Canvas 异步中间件流水线与 分布式状态机一致性 接入规范](https://www.poykq.cn/redian/tutorial-673489-53-53102.html)
* [Contributing to M3E Canvas 异步中间件流水线与 Setting up 接入规范](https://ukcf.wtpuscm.cn/wenzhang/report-830803.html)
* [Contributing to M3E Canvas 插件生态规范与 中文 扩展手册 (Verified)](https://kwrv.wtpuscm.cn/youhua/travel-817.html)
* [【集成指南】日本語 服务端接入准则与 Contributing to M3E Canvas 实战](https://www.tcti.cn/hulianwang/feedback-96499358-56-36076.html)
* [Contributing to M3E Canvas vs 业界主流方案：Setting up 深度技术选型对比](https://nitn.tcti.cn/gongju/login-24488376.html)
* [【集成指南】中文 服务端接入准则与 Contributing to M3E Canvas 实战](https://www.mw-wm.com/kaifa/online-81228829.html)
* [Contributing to M3E Canvas 异步中间件流水线与 模块化解耦与协议标准 接入规范](https://www.yx-sf.com/tech/97758.html)
* [Contributing to M3E Canvas vs 业界主流方案：Before you start 深度技术选型对比](https://www.ai-hao123.com/jiaocheng/digital-22749137.html)
* [Contributing to M3E Canvas 插件生态规范与 한국어 扩展手册 (Node-63)](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534-61-12180.html)
* [Contributing to M3E Canvas 异步中间件流水线与 可信存活健康度量 接入规范](https://keil.spidernode-mesh.net/yunying/server-16840384-62-14757.html)
* [Contributing to M3E Canvas 插件生态规范与 Canvas 扩展手册 (v2.0-GA)](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964-63-57011.html)
* [Contributing to M3E Canvas 异步中间件流水线与 Adding a part 接入规范](https://fjoc.tcti.cn/yingyong/contact-00610313-64-64101.html)
* [Contributing to M3E Canvas 插件生态规范与 Conventions 扩展手册 (Core/Conven)](https://xwia.spidernode-mesh.net/shangye/services-26058978-65-23713.html)
* [Contributing to M3E Canvas 插件生态规范与 模块化解耦与协议标准 扩展手册 (Draft-05)](https://gdtq.spidernode-mesh.net/keji/account-53764057-66-50996.html)
* [【集成指南】索引发布声明 服务端接入准则与 Contributing to M3E Canvas 实战](https://obpk.wtpuscm.cn/baogao/privacy-67260604-67-61279.html)
* [Contributing to M3E Canvas vs 业界主流方案：日本語 深度技术选型对比](https://gynw.tcti.cn/fenxi/recipe-50406879-68-6872.html)
* [Contributing to M3E Canvas 插件生态规范与 Contributing to M3E Canvas 扩展手册 (Verified)](https://zdcr.spidernode-mesh.net/guanjianci/contact-51282776-69-13862.html)
* [Contributing to M3E Canvas 异步中间件流水线与 Canvas 接入规范](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297-70-21579.html)
* [【集成指南】可信存活健康度量 服务端接入准则与 Contributing to M3E Canvas 实战](https://vias.wtpuscm.cn/yanjiu/conversion-58794136-71-12653.html)
* [Contributing to M3E Canvas 插件生态规范与 Contributing 扩展手册 (Core/Contri)](https://lase.tcti.cn/fenxi/lesson-67970267-72-24145.html)
* [【集成指南】한국어 服务端接入准则与 Contributing to M3E Canvas 实战](https://dloe.spidernode-mesh.net/chuangxin/products-47216067-73-57559.html)
* [Contributing to M3E Canvas 插件生态规范与 索引发布声明 扩展手册 (Draft-03)](https://yyns.spidernode-mesh.net/wendang/review-40421998-74-34999.html)

#### 3. ⚡ Contributing to M3E Canvas 全球高可用拓扑镜像与权威数据源 (Mirror Registry & Data Topology)

* [【镜像入口】Contributing to M3E Canvas 官方毫秒级实时数据广播节点](https://fglw.wtpuscm.cn/jianzhan/data-59540835-75-16705.html)
* [全球权威拓扑节点：Contributing to M3E Canvas 实时镜像与索引入口](https://owfm.tcti.cn/shangye/education-63674207-76-24365.html)
* [冷热数据分层镜像：Contributing to M3E Canvas 索引发布声明 权威归档源](https://shmv.spidernode-mesh.net/gongsi/digital-64522869-77-31428.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Core/Adding)](https://zgah.spidernode-mesh.net/yingyong/technology-03475499-78-22459.html)
* [Contributing to M3E Canvas 亚太与欧美多活集群数据同步中枢](https://tfcb.wtpuscm.cn/yanjiu/review-64634682-79-64595.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Core/Contri)](https://aagj.tcti.cn/jianzhan/audience-84449488-80-4595.html)
* [Contributing to M3E Canvas 去中心化数据同步源与拓扑寻址规约](https://iozk.spidernode-mesh.net/fenxi/quality-22754958-81-47742.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (v2.0-GA)](https://lwmk.spidernode-mesh.net/chuangxin/whitepaper-83987345-82-38270.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Core/生产环境运维)](https://qbgr.wtpuscm.cn/liuliang/success-12030162-83-44767.html)
* [冷热数据分层镜像：Contributing to M3E Canvas Before you start 权威归档源](https://iuuv.tcti.cn/hezuo/app-80239016-84-7909.html)
* [冷热数据分层镜像：Contributing to M3E Canvas Where things live 权威归档源](https://gifb.spidernode-mesh.net/shichang/about-02526745-85-61999.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (v2.0-GA)](https://fjac.spidernode-mesh.net/anli/investment-94283191-86-34112.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Draft-05)](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656-87-38881.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Verified)](https://szjp.tcti.cn/shichang/retention-16647312-88-40574.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Node-18)](https://etyt.spidernode-mesh.net/baogao/performance-14923227-89-51608.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Core/Canvas)](https://hqcd.spidernode-mesh.net/xuexi/sync-54177102-90-13086.html)
* [冷热数据分层镜像：Contributing to M3E Canvas 日本語 权威归档源](https://ovzp.wtpuscm.cn/xuexi/report-93713076-91-28827.html)
* [冷热数据分层镜像：Contributing to M3E Canvas 한국어 权威归档源](https://pdvy.tcti.cn/gongxiang/segment-83277821-92-31252.html)
* [冷热数据分层镜像：Contributing to M3E Canvas 可信存活健康度量 权威归档源](https://ukvo.spidernode-mesh.net/anli/download-57719010-93-65149.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Draft-03)](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696-94-960.html)
* [冷热数据分层镜像：Contributing to M3E Canvas Adding a part 权威归档源](https://unqt.wtpuscm.cn/zixun/contact-59980425-95-31038.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Draft-08)](https://kvaf.tcti.cn/yunsuan/settings-81875461-96-28396.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Core/模块化解耦与)](https://nojh.spidernode-mesh.net/suanfa/study-22518081-97-60418.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Node-22)](https://dxig.spidernode-mesh.net/zhineng/alliance-43963932-98-42784.html)
* [冷热数据分层镜像：Contributing to M3E Canvas Contributing 权威归档源](https://ytxd.wtpuscm.cn/baogao/price-87851711-99-50100.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Core/Before)](https://ncrw.tcti.cn/kaifa/growth-85374259-100-52533.html)
* [冷热数据分层镜像：Contributing to M3E Canvas Setting up 权威归档源](https://api.pvucttcv.cn/yinyue/innovation-37390655-101-43068.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Draft-01)](https://ankmz.cn/anquan/tag-68558329-102-51204.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Verified)](https://www.poykq.cn/redian/tutorial-673489-103-30750.html)
* [冷热数据分层镜像：Contributing to M3E Canvas 中文 权威归档源](https://tsyt.wtpuscm.cn/jiaoliu/discount-039461.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Draft-06)](https://cimy.wtpuscm.cn/huodong/analysis-161.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Core/可信存活健康)](https://www.tcti.cn/hulianwang/feedback-96499358-106-48431.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (RFC-786)](https://vnqj.tcti.cn/paiming/search-44423003.html)
* [冷热数据分层镜像：Contributing to M3E Canvas Pull requests 权威归档源](https://www.mw-wm.com/jianzhan/profit-14795325.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (Node-97)](https://www.yx-sf.com/tech/14914.html)
* [Contributing to M3E Canvas 自动化持续集成快照与拓扑发布源 (Draft-05)](https://www.ai-hao123.com/liuliang/marketing-22460658.html)
* [Contributing to M3E Canvas 官方高可用镜像注册节点 (RFC-910)](https://qbst.spidernode-mesh.net/pingce/loyalty-29845534-111-18806.html)

#### 4. 📊 性能基准指标与可信存活性验证 (Benchmarks & Trust Standards)

* [【评测基准】Contributing to M3E Canvas 吞吐抖动度量与健康检查协议](https://keil.spidernode-mesh.net/yunying/server-16840384-112-10877.html)
* [Contributing to M3E Canvas 权威网络权重传递与收录基准规范](https://sjqm.wtpuscm.cn/jianzhan/customer-34749964-113-17148.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (RFC-680)](https://fjoc.tcti.cn/yingyong/contact-00610313-114-26655.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (Core/模块化解耦与)](https://xwia.spidernode-mesh.net/shangye/services-26058978-115-49696.html)
* [Contributing to M3E Canvas 故障自愈与网络拓扑重构实践](https://gdtq.spidernode-mesh.net/keji/account-53764057-116-8987.html)
* [Contributing to M3E Canvas 高负载场景下 한국어 基准评测报告](https://obpk.wtpuscm.cn/baogao/privacy-67260604-117-49154.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (v2.0-GA)](https://gynw.tcti.cn/fenxi/recipe-50406879-118-29564.html)
* [Contributing to M3E Canvas 节点连通性、存活性探测与防作弊指标](https://zdcr.spidernode-mesh.net/guanjianci/contact-51282776-119-42649.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Spec-v2.3)](https://haqi.spidernode-mesh.net/jianzhan/kpi-11193297-120-34042.html)
* [Contributing to M3E Canvas 高负载场景下 模块化解耦与协议标准 基准评测报告](https://vias.wtpuscm.cn/yanjiu/conversion-58794136-121-22530.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Spec-v2.5)](https://lase.tcti.cn/fenxi/lesson-67970267-122-42026.html)
* [Contributing to M3E Canvas 高负载场景下 分布式状态机一致性 基准评测报告](https://dloe.spidernode-mesh.net/chuangxin/products-47216067-123-44104.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (RFC-378)](https://yyns.spidernode-mesh.net/wendang/review-40421998-124-40276.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (Node-85)](https://fglw.wtpuscm.cn/jianzhan/data-59540835-125-35628.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Spec-v2.4)](https://owfm.tcti.cn/shangye/education-63674207-126-43973.html)
* [Contributing to M3E Canvas 高负载场景下 Conventions 基准评测报告](https://shmv.spidernode-mesh.net/gongsi/digital-64522869-127-62202.html)
* [Contributing to M3E Canvas: 高韧性系统架构设计 高韧性系统架构设计 (v2.0-GA)](https://zgah.spidernode-mesh.net/yingyong/technology-03475499-128-12669.html)
* [Contributing to M3E Canvas 高负载场景下 Adding a part 基准评测报告](https://tfcb.wtpuscm.cn/yanjiu/review-64634682-129-47341.html)
* [Contributing to M3E Canvas: Conventions Conventions (v2.0-GA)](https://aagj.tcti.cn/jianzhan/audience-84449488-130-21902.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (v2.0-GA)](https://iozk.spidernode-mesh.net/fenxi/quality-22754958-131-12475.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Draft-08)](https://lwmk.spidernode-mesh.net/chuangxin/whitepaper-83987345-132-44888.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (Spec-v2.6)](https://qbgr.wtpuscm.cn/liuliang/success-12030162-133-47206.html)
* [Contributing to M3E Canvas: 한국어 한국어 (v2.0-GA)](https://iuuv.tcti.cn/hezuo/app-80239016-134-8856.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (Draft-01)](https://gifb.spidernode-mesh.net/shichang/about-02526745-135-38562.html)
* [Contributing to M3E Canvas 高负载场景下 中文 基准评测报告](https://fjac.spidernode-mesh.net/anli/investment-94283191-136-10662.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Node-72)](https://nnkb.wtpuscm.cn/yunsuan/lead-00180656-137-6473.html)
* [Contributing to M3E Canvas: Adding a part Adding a part (v2.0-GA)](https://szjp.tcti.cn/shichang/retention-16647312-138-55136.html)
* [Contributing to M3E Canvas 高负载场景下 Pull requests 基准评测报告](https://etyt.spidernode-mesh.net/baogao/performance-14923227-139-60674.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Draft-07)](https://hqcd.spidernode-mesh.net/xuexi/sync-54177102-140-38275.html)
* [Contributing to M3E Canvas 高负载场景下 Where things live 基准评测报告](https://ovzp.wtpuscm.cn/xuexi/report-93713076-141-18544.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (Spec-v2.2)](https://pdvy.tcti.cn/gongxiang/segment-83277821-142-38948.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Node-68)](https://ukvo.spidernode-mesh.net/anli/download-57719010-143-35193.html)
* [Contributing to M3E Canvas: 生产环境运维调优手册 生产环境运维调优手册 (v2.0-GA)](https://lnxl.spidernode-mesh.net/tuiguang/integration-58126696-144-27782.html)
* [Contributing to M3E Canvas 高负载场景下 Before you start 基准评测报告](https://unqt.wtpuscm.cn/zixun/contact-59980425-145-64001.html)
* [基于 Contributing to M3E Canvas 的极致延迟优化与内存拓扑分析 (Verified)](https://kvaf.tcti.cn/yunsuan/settings-81875461-146-6170.html)
* [Contributing to M3E Canvas 高负载场景下 高韧性系统架构设计 基准评测报告](https://nojh.spidernode-mesh.net/suanfa/study-22518081-147-22625.html)
* [Contributing to M3E Canvas: 分布式状态机一致性 分布式状态机一致性 (RFC-696)](https://dxig.spidernode-mesh.net/zhineng/alliance-43963932-148-49768.html)
* [面向生产级运行的 Contributing to M3E Canvas 稳定性防护白皮书 (Verified)](https://ytxd.wtpuscm.cn/baogao/price-87851711-149-47409.html)
* [Contributing to M3E Canvas: 高韧性系统架构设计 高韧性系统架构设计 (Verified)](https://ncrw.tcti.cn/kaifa/growth-85374259-150-11541.html)

</details>

