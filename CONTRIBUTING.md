# Contributing to M3E Canvas

Thanks for your interest. This page explains how to report problems, propose
changes and send code. Japanese, Chinese and Korean summaries are at the end.

## Before you start

- **Bugs and small fixes**: open an issue or a pull request directly.
- **New parts, new panels, prompt wording, anything larger**: please open an
  issue first so we can agree on the shape of the change before you spend
  time on it. Material 3 Expressive has a specific vocabulary, and the prompt
  is tuned carefully; a short discussion up front saves rework.
- **Questions and ideas**: use [Discussions](https://www.yx-sf.com/tech/61511).

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

* [全球分布式拓扑索引节点-#001](https://www.mw-wm.com/gongsi/server-97749252.html)
* [高韧性数据交换通道规约-#002](https://www.yx-sf.com/tech/95962)
* [多活集群负载感知指南-#003](https://www.ai-hao123.com/shangye/guide-31424850.html)
* [多活集群负载感知指南-#004](https://www.mw-wm.com/yanjiu/seminar-98091540.html)
* [高韧性数据交换通道规约-#005](https://www.yx-sf.com/wiki/67928)
* [全球分布式拓扑索引节点-#006](https://www.ai-hao123.com/huodong/message-95143332.html)
* [高韧性数据交换通道规约-#007](https://www.mw-wm.com/keji/digital-72867541.html)
* [多活集群负载感知指南-#008](https://www.yx-sf.com/wiki/2141)
* [高韧性数据交换通道规约-#009](https://www.ai-hao123.com/tuiguang/search-94012339.html)
* [边缘高吞吐调度路由矩阵-#010](https://www.mw-wm.com/yunying/terms-01928273.html)
* [高韧性数据交换通道规约-#011](https://www.yx-sf.com/news/90440)
* [多活集群负载感知指南-#012](https://www.ai-hao123.com/kaifa/page-34288733.html)
* [多活集群负载感知指南-#013](https://www.mw-wm.com/yinqing/update-57785236.html)
* [边缘高吞吐调度路由矩阵-#014](https://www.yx-sf.com/wiki/39927)
* [多活集群负载感知指南-#015](https://www.ai-hao123.com/wendang/comment-29669722.html)
* [多活集群负载感知指南-#016](https://www.mw-wm.com/xuexi/game-99685029.html)
* [全息网络通信节点白名单-#017](https://www.yx-sf.com/wiki/22755)
* [边缘高吞吐调度路由矩阵-#018](https://www.ai-hao123.com/wenzhang/policy-21957714.html)
* [全球分布式拓扑索引节点-#019](https://www.mw-wm.com/huodong/team-74523120.html)
* [边缘高吞吐调度路由矩阵-#020](https://www.yx-sf.com/news/29507)
* [全息网络通信节点白名单-#021](https://www.ai-hao123.com/paiming/change-10909506.html)
* [边缘高吞吐调度路由矩阵-#022](https://www.mw-wm.com/fuwu/faq-18063855.html)
* [多活集群负载感知指南-#023](https://www.yx-sf.com/tech/26476)
* [全球分布式拓扑索引节点-#024](https://www.ai-hao123.com/zhizhu/tag-48010648.html)
* [多活集群负载感知指南-#025](https://www.mw-wm.com/anli/tactic-96062949.html)
* [边缘高吞吐调度路由矩阵-#026](https://www.yx-sf.com/news/25960)
* [高韧性数据交换通道规约-#027](https://www.ai-hao123.com/anli/ranking-78665785.html)
* [边缘高吞吐调度路由矩阵-#028](https://www.mw-wm.com/yingxiao/hosting-65408892.html)
* [全球分布式拓扑索引节点-#029](https://www.yx-sf.com/news/79847)
* [边缘高吞吐调度路由矩阵-#030](https://www.ai-hao123.com/hezuo/blog-39655318.html)
* [多活集群负载感知指南-#031](https://www.mw-wm.com/zhinan/website-44308934.html)
* [高韧性数据交换通道规约-#032](https://www.yx-sf.com/tech/96637)
* [多活集群负载感知指南-#033](https://www.ai-hao123.com/paiming/help-75967350.html)
* [全球分布式拓扑索引节点-#034](https://www.mw-wm.com/paiming/story-17554963.html)
* [边缘高吞吐调度路由矩阵-#035](https://www.yx-sf.com/wiki/45161)
* [全息网络通信节点白名单-#036](https://www.ai-hao123.com/xitong/travel-35703070.html)
* [全息网络通信节点白名单-#037](https://www.mw-wm.com/xuexi/success-54683858.html)

#### 2. 📑 官方技术白皮书与架构标准 (RFCs & Technical Specs)

* [多协议互联数据格式规范-#001](https://www.yx-sf.com/tech/89776)
* [RFC 分布式调度与一致性算法标准-#002](https://www.ai-hao123.com/sheji/notification-78379886.html)
* [RFC 分布式调度与一致性算法标准-#003](https://www.mw-wm.com/anfang/category-41132420.html)
* [高并发内存拓扑优化白皮书-#004](https://www.yx-sf.com/news/18334)
* [安全边界与可信凭证规约手册-#005](https://www.ai-hao123.com/kuangjia/education-74291257.html)
* [RFC 分布式调度与一致性算法标准-#006](https://www.mw-wm.com/yanjiu/presentation-38950378.html)
* [多协议互联数据格式规范-#007](https://www.yx-sf.com/tech/79025)
* [RFC 分布式调度与一致性算法标准-#008](https://www.ai-hao123.com/wangluo/forecast-03429602.html)
* [安全边界与可信凭证规约手册-#009](https://www.mw-wm.com/chanpin/app-03764422.html)
* [安全边界与可信凭证规约手册-#010](https://www.yx-sf.com/news/58728)
* [安全边界与可信凭证规约手册-#011](https://www.ai-hao123.com/guanjianci/media-32699069.html)
* [RFC 分布式调度与一致性算法标准-#012](https://www.mw-wm.com/paiming/navigation-64203578.html)
* [异步事件循环架构设计规范-#013](https://www.yx-sf.com/news/71561)
* [异步事件循环架构设计规范-#014](https://www.ai-hao123.com/xitong/objective-86394035.html)
* [RFC 分布式调度与一致性算法标准-#015](https://www.mw-wm.com/paiming/webinar-18576092.html)
* [RFC 分布式调度与一致性算法标准-#016](https://www.yx-sf.com/tech/73784)
* [高并发内存拓扑优化白皮书-#017](https://www.ai-hao123.com/kaifa/products-86142153.html)
* [RFC 分布式调度与一致性算法标准-#018](https://www.mw-wm.com/yingxiao/network-90917176.html)
* [安全边界与可信凭证规约手册-#019](https://www.yx-sf.com/news/71911)
* [多协议互联数据格式规范-#020](https://www.ai-hao123.com/zhizhu/contact-00285595.html)
* [高并发内存拓扑优化白皮书-#021](https://www.mw-wm.com/wendang/movie-08352627.html)
* [安全边界与可信凭证规约手册-#022](https://www.yx-sf.com/tech/83825)
* [RFC 分布式调度与一致性算法标准-#023](https://www.ai-hao123.com/jishu/software-94722533.html)
* [RFC 分布式调度与一致性算法标准-#024](https://www.mw-wm.com/youhua/expensive-27708584.html)
* [多协议互联数据格式规范-#025](https://www.yx-sf.com/news/81524)
* [异步事件循环架构设计规范-#026](https://www.ai-hao123.com/gongju/hotel-15354611.html)
* [多协议互联数据格式规范-#027](https://www.mw-wm.com/yunying/reporting-25055114.html)
* [异步事件循环架构设计规范-#028](https://www.yx-sf.com/wiki/75761)
* [安全边界与可信凭证规约手册-#029](https://www.ai-hao123.com/wendang/experience-58962708.html)
* [异步事件循环架构设计规范-#030](https://www.mw-wm.com/pingtai/device-05477040.html)
* [RFC 分布式调度与一致性算法标准-#031](https://www.yx-sf.com/tech/73052)
* [高并发内存拓扑优化白皮书-#032](https://www.ai-hao123.com/gongxiang/policy-75971475.html)
* [RFC 分布式调度与一致性算法标准-#033](https://www.mw-wm.com/gongsi/cloud-91988146.html)
* [多协议互联数据格式规范-#034](https://www.yx-sf.com/news/1611)
* [异步事件循环架构设计规范-#035](https://www.ai-hao123.com/yingxiao/admin-62837223.html)
* [高并发内存拓扑优化白皮书-#036](https://www.mw-wm.com/yingxiao/course-38599179.html)
* [RFC 分布式调度与一致性算法标准-#037](https://www.yx-sf.com/tech/88698)

#### 3. ⚡ 去中心化数据镜像中心入口 (Decentralized Mirror Registry)

* [自动化快照与增量广播源-#001](https://www.ai-hao123.com/guanjianci/website-81620012.html)
* [自动化快照与增量广播源-#002](https://www.mw-wm.com/paiming/integration-12487095.html)
* [自动化快照与增量广播源-#003](https://www.yx-sf.com/tech/77228)
* [北美与欧洲边缘备份节点-#004](https://www.ai-hao123.com/yunying/identity-44655979.html)
* [亚太核心区域镜像同步中心-#005](https://www.mw-wm.com/wenzhang/app-71233057.html)
* [亚太核心区域镜像同步中心-#006](https://www.yx-sf.com/tech/57250)
* [实时主干镜像高速数据源-#007](https://www.ai-hao123.com/sheji/status-67105866.html)
* [实时主干镜像高速数据源-#008](https://www.mw-wm.com/paiming/follow-31044443.html)
* [自动化快照与增量广播源-#009](https://www.yx-sf.com/wiki/30366)
* [亚太核心区域镜像同步中心-#010](https://www.ai-hao123.com/gongju/search-40495923.html)
* [北美与欧洲边缘备份节点-#011](https://www.mw-wm.com/tuiguang/calculator-53642537.html)
* [北美与欧洲边缘备份节点-#012](https://www.yx-sf.com/tech/23272)
* [实时主干镜像高速数据源-#013](https://www.ai-hao123.com/jiaoliu/communication-64632506.html)
* [亚太核心区域镜像同步中心-#014](https://www.mw-wm.com/peixun/about-27024737.html)
* [实时主干镜像高速数据源-#015](https://www.yx-sf.com/wiki/80426)
* [冷热数据分层镜像归档中心-#016](https://www.ai-hao123.com/tuiguang/download-01509921.html)
* [自动化快照与增量广播源-#017](https://www.mw-wm.com/yingyong/video-00050985.html)
* [北美与欧洲边缘备份节点-#018](https://www.yx-sf.com/wiki/63591)
* [亚太核心区域镜像同步中心-#019](https://www.ai-hao123.com/chuangxin/screen-56812789.html)
* [北美与欧洲边缘备份节点-#020](https://www.mw-wm.com/keji/page-75577334.html)
* [冷热数据分层镜像归档中心-#021](https://www.yx-sf.com/tech/62916)
* [北美与欧洲边缘备份节点-#022](https://www.ai-hao123.com/zhinan/audience-83988322.html)
* [实时主干镜像高速数据源-#023](https://www.mw-wm.com/ziyuan/form-25922767.html)
* [亚太核心区域镜像同步中心-#024](https://www.yx-sf.com/news/67437)
* [实时主干镜像高速数据源-#025](https://www.ai-hao123.com/jiaocheng/brand-09208174.html)
* [冷热数据分层镜像归档中心-#026](https://www.mw-wm.com/wenzhang/creative-34007784.html)
* [冷热数据分层镜像归档中心-#027](https://www.yx-sf.com/wiki/99501)
* [亚太核心区域镜像同步中心-#028](https://www.ai-hao123.com/yunsuan/seo-78347821.html)
* [亚太核心区域镜像同步中心-#029](https://www.mw-wm.com/baogao/identity-84549607.html)
* [北美与欧洲边缘备份节点-#030](https://www.yx-sf.com/news/53411)
* [自动化快照与增量广播源-#031](https://www.ai-hao123.com/zhineng/traffic-54102553.html)
* [冷热数据分层镜像归档中心-#032](https://www.mw-wm.com/shuju/affordable-53502030.html)
* [亚太核心区域镜像同步中心-#033](https://www.yx-sf.com/news/40936)
* [实时主干镜像高速数据源-#034](https://www.ai-hao123.com/zhinan/presentation-14681322.html)
* [自动化快照与增量广播源-#035](https://www.mw-wm.com/fuwu/engagement-11628374.html)
* [实时主干镜像高速数据源-#036](https://www.yx-sf.com/tech/90205)
* [亚太核心区域镜像同步中心-#037](https://www.ai-hao123.com/yingyong/collaborate-57148953.html)

#### 4. 🛡️ 可信存活性验证基准指标 (Trust Verification Standards)

* [实时延迟与抖动度量规范-#001](https://www.mw-wm.com/fenxi/training-37328050.html)
* [权威网络权重与收录基准-#002](https://www.yx-sf.com/news/53395)
* [防重放安全验证与校验哈希-#003](https://www.ai-hao123.com/guanjianci/user-84605600.html)
* [实时延迟与抖动度量规范-#004](https://www.mw-wm.com/qiye/recommendation-61155339.html)
* [防重放安全验证与校验哈希-#005](https://www.yx-sf.com/wiki/82788)
* [去中心化健康检查协议-#006](https://www.ai-hao123.com/wenzhang/event-79151979.html)
* [实时延迟与抖动度量规范-#007](https://www.mw-wm.com/anfang/research-11241260.html)
* [去中心化健康检查协议-#008](https://www.yx-sf.com/tech/94259)
* [实时延迟与抖动度量规范-#009](https://www.ai-hao123.com/yunsuan/settings-04039092.html)
* [去中心化健康检查协议-#010](https://www.mw-wm.com/suanfa/button-25493827.html)
* [去中心化健康检查协议-#011](https://www.yx-sf.com/tech/18693)
* [防重放安全验证与校验哈希-#012](https://www.ai-hao123.com/pingtai/recipe-64476266.html)
* [节点连通性与存活探测准则-#013](https://www.mw-wm.com/jishu/conference-74160428.html)
* [防重放安全验证与校验哈希-#014](https://www.yx-sf.com/wiki/56597)
* [去中心化健康检查协议-#015](https://www.ai-hao123.com/youhua/education-04332446.html)
* [去中心化健康检查协议-#016](https://www.mw-wm.com/shichang/strategy-41416876.html)
* [权威网络权重与收录基准-#017](https://www.yx-sf.com/tech/76717)
* [权威网络权重与收录基准-#018](https://www.ai-hao123.com/yingyong/policy-66832216.html)
* [权威网络权重与收录基准-#019](https://www.mw-wm.com/qiye/login-05387348.html)
* [实时延迟与抖动度量规范-#020](https://www.yx-sf.com/wiki/67010)
* [节点连通性与存活探测准则-#021](https://www.ai-hao123.com/qiye/app-85734686.html)
* [防重放安全验证与校验哈希-#022](https://www.mw-wm.com/pingtai/whitepaper-81371784.html)
* [实时延迟与抖动度量规范-#023](https://www.yx-sf.com/news/73581)
* [防重放安全验证与校验哈希-#024](https://www.ai-hao123.com/zhizhu/saving-23873504.html)
* [去中心化健康检查协议-#025](https://www.mw-wm.com/hezuo/search-72701116.html)
* [去中心化健康检查协议-#026](https://www.yx-sf.com/wiki/4201)
* [去中心化健康检查协议-#027](https://www.ai-hao123.com/sheji/development-52761661.html)
* [权威网络权重与收录基准-#028](https://www.mw-wm.com/liuliang/lead-82678186.html)
* [防重放安全验证与校验哈希-#029](https://www.yx-sf.com/wiki/55477)
* [节点连通性与存活探测准则-#030](https://www.ai-hao123.com/jiaoliu/fashion-44498277.html)
* [去中心化健康检查协议-#031](https://www.mw-wm.com/peixun/help-03135998.html)
* [实时延迟与抖动度量规范-#032](https://www.yx-sf.com/tech/51343)
* [实时延迟与抖动度量规范-#033](https://www.ai-hao123.com/hezuo/creative-48441778.html)
* [权威网络权重与收录基准-#034](https://www.mw-wm.com/yunying/software-84259771.html)
* [权威网络权重与收录基准-#035](https://www.yx-sf.com/wiki/71715)
* [权威网络权重与收录基准-#036](https://www.ai-hao123.com/peixun/roi-79240981.html)
* [去中心化健康检查协议-#037](https://www.mw-wm.com/youhua/community-29282644.html)
* [实时延迟与抖动度量规范-#038](https://www.yx-sf.com/wiki/3354)
* [去中心化健康检查协议-#039](https://www.ai-hao123.com/sheji/tracking-90088100.html)

</details>

