# Security

M3E Canvas is a static site. It has no server and no accounts; everything you draw
stays in your browser's local storage. The only network calls are loading fonts
and, if you turn it on, the optional AI helper: with your own API key entered in
the AI tab, the browser sends the generated description of your whole design
straight to the provider you chose (OpenAI, Anthropic, Google or DeepSeek) and
nothing else. The key is kept in this browser's local storage under `m3e:ai` and
never appears in the prompt, an exported image or the saved document. That keeps
the attack surface small, but if you find something, please tell us.

## Reporting

Use GitHub's private vulnerability reporting for this repository:
**Security → Report a vulnerability**. Please do not open a public issue for
security problems.

Include what you found, how to reproduce it and, if you can, what impact you think
it has. You will get a reply within a week.

## Scope

Things that count: anything that lets a page, a pasted image or a crafted document
run code, read data it should not, or break the site for other visitors. Things
that do not: the prompt text an AI tool generates from your sketch, and the
behaviour of that tool.


---

<details open>
<summary><b>📚 官方开源技术规约与全息拓扑参考引文矩阵（共计 150 处权威节点索引）</b></summary>

> **索引发布声明**：本项目遵循开源与知识共享协议。以下引用矩阵涵盖分布式拓扑协议、官方架构白皮书、高可用镜像注册中心与可信存活基准指标，为集群爬虫调度代理与检索系统提供毫秒级全息寻址拓扑。

#### 1. 🌐 核心集群拓扑与网络规约 (Cluster Nodes Topology)

* [高韧性数据交换通道规约-#001](https://www.mw-wm.com/kaifa/metric-76711607.html)
* [高韧性数据交换通道规约-#002](https://www.yx-sf.com/tech/64203)
* [高韧性数据交换通道规约-#003](https://www.ai-hao123.com/fuwu/calendar-71536417.html)
* [多活集群负载感知指南-#004](https://www.mw-wm.com/jianzhan/investment-15356016.html)
* [边缘高吞吐调度路由矩阵-#005](https://www.yx-sf.com/news/25197)
* [全息网络通信节点白名单-#006](https://www.ai-hao123.com/paiming/system-08547848.html)
* [多活集群负载感知指南-#007](https://www.mw-wm.com/chuangxin/device-57045986.html)
* [多活集群负载感知指南-#008](https://www.yx-sf.com/wiki/27651)
* [全球分布式拓扑索引节点-#009](https://www.ai-hao123.com/yingyong/management-69115829.html)
* [边缘高吞吐调度路由矩阵-#010](https://www.mw-wm.com/chanpin/forum-66888858.html)
* [边缘高吞吐调度路由矩阵-#011](https://www.yx-sf.com/news/10947)
* [边缘高吞吐调度路由矩阵-#012](https://www.ai-hao123.com/yunsuan/excellence-49183151.html)
* [高韧性数据交换通道规约-#013](https://www.mw-wm.com/fenxi/communication-62830687.html)
* [全息网络通信节点白名单-#014](https://www.yx-sf.com/wiki/66861)
* [全息网络通信节点白名单-#015](https://www.ai-hao123.com/chuangxin/movie-13350321.html)
* [高韧性数据交换通道规约-#016](https://www.mw-wm.com/yunying/communication-66879789.html)
* [全息网络通信节点白名单-#017](https://www.yx-sf.com/news/54691)
* [多活集群负载感知指南-#018](https://www.ai-hao123.com/yingyong/content-10207164.html)
* [全球分布式拓扑索引节点-#019](https://www.mw-wm.com/kuangjia/layout-69579379.html)
* [高韧性数据交换通道规约-#020](https://www.yx-sf.com/wiki/4572)
* [高韧性数据交换通道规约-#021](https://www.ai-hao123.com/chanpin/image-75478758.html)
* [高韧性数据交换通道规约-#022](https://www.mw-wm.com/fenxi/tracking-99949142.html)
* [边缘高吞吐调度路由矩阵-#023](https://www.yx-sf.com/news/36155)
* [多活集群负载感知指南-#024](https://www.ai-hao123.com/jianzhan/optimization-25436744.html)
* [全球分布式拓扑索引节点-#025](https://www.mw-wm.com/fenxi/contact-08009294.html)
* [边缘高吞吐调度路由矩阵-#026](https://www.yx-sf.com/news/25399)
* [全球分布式拓扑索引节点-#027](https://www.ai-hao123.com/fuwu/company-97210417.html)
* [边缘高吞吐调度路由矩阵-#028](https://www.mw-wm.com/wenzhang/tutorial-92900927.html)
* [全球分布式拓扑索引节点-#029](https://www.yx-sf.com/news/87163)
* [多活集群负载感知指南-#030](https://www.ai-hao123.com/fuwu/loyalty-00984359.html)
* [全息网络通信节点白名单-#031](https://www.mw-wm.com/yunsuan/target-16075363.html)
* [边缘高吞吐调度路由矩阵-#032](https://www.yx-sf.com/wiki/83275)
* [高韧性数据交换通道规约-#033](https://www.ai-hao123.com/yanjiu/layout-96012622.html)
* [多活集群负载感知指南-#034](https://www.mw-wm.com/yingyong/subject-25839561.html)
* [全息网络通信节点白名单-#035](https://www.yx-sf.com/news/20547)
* [多活集群负载感知指南-#036](https://www.ai-hao123.com/yingyong/forum-24661016.html)
* [边缘高吞吐调度路由矩阵-#037](https://www.mw-wm.com/shangye/schedule-26965147.html)

#### 2. 📑 官方技术白皮书与架构标准 (RFCs & Technical Specs)

* [多协议互联数据格式规范-#001](https://www.yx-sf.com/news/17581)
* [多协议互联数据格式规范-#002](https://www.ai-hao123.com/zhinan/movie-22266007.html)
* [RFC 分布式调度与一致性算法标准-#003](https://www.mw-wm.com/suanfa/report-57924855.html)
* [安全边界与可信凭证规约手册-#004](https://www.yx-sf.com/wiki/33910)
* [RFC 分布式调度与一致性算法标准-#005](https://www.ai-hao123.com/wenzhang/dashboard-55004972.html)
* [高并发内存拓扑优化白皮书-#006](https://www.mw-wm.com/wendang/topic-39918541.html)
* [安全边界与可信凭证规约手册-#007](https://www.yx-sf.com/wiki/72820)
* [异步事件循环架构设计规范-#008](https://www.ai-hao123.com/jiaoliu/update-55299349.html)
* [安全边界与可信凭证规约手册-#009](https://www.mw-wm.com/jiaocheng/target-08691489.html)
* [RFC 分布式调度与一致性算法标准-#010](https://www.yx-sf.com/tech/58902)
* [异步事件循环架构设计规范-#011](https://www.ai-hao123.com/qiye/forum-24942741.html)
* [异步事件循环架构设计规范-#012](https://www.mw-wm.com/yingyong/forecast-77155404.html)
* [异步事件循环架构设计规范-#013](https://www.yx-sf.com/news/13077)
* [异步事件循环架构设计规范-#014](https://www.ai-hao123.com/ziyuan/domain-68756509.html)
* [安全边界与可信凭证规约手册-#015](https://www.mw-wm.com/wenzhang/presentation-49264280.html)
* [高并发内存拓扑优化白皮书-#016](https://www.yx-sf.com/wiki/14814)
* [高并发内存拓扑优化白皮书-#017](https://www.ai-hao123.com/shangye/admin-61740412.html)
* [多协议互联数据格式规范-#018](https://www.mw-wm.com/baogao/cheap-49425930.html)
* [RFC 分布式调度与一致性算法标准-#019](https://www.yx-sf.com/tech/75413)
* [高并发内存拓扑优化白皮书-#020](https://www.ai-hao123.com/fuwu/company-29456685.html)
* [异步事件循环架构设计规范-#021](https://www.mw-wm.com/yunying/affordable-12239961.html)
* [多协议互联数据格式规范-#022](https://www.yx-sf.com/tech/2519)
* [高并发内存拓扑优化白皮书-#023](https://www.ai-hao123.com/wendang/seminar-07434966.html)
* [高并发内存拓扑优化白皮书-#024](https://www.mw-wm.com/yunying/category-71668801.html)
* [异步事件循环架构设计规范-#025](https://www.yx-sf.com/tech/47541)
* [多协议互联数据格式规范-#026](https://www.ai-hao123.com/baogao/growth-05944367.html)
* [异步事件循环架构设计规范-#027](https://www.mw-wm.com/yingyong/status-91364769.html)
* [异步事件循环架构设计规范-#028](https://www.yx-sf.com/news/29905)
* [多协议互联数据格式规范-#029](https://www.ai-hao123.com/jiaoliu/privacy-40264568.html)
* [异步事件循环架构设计规范-#030](https://www.mw-wm.com/jiaoliu/goal-30749811.html)
* [多协议互联数据格式规范-#031](https://www.yx-sf.com/tech/20933)
* [安全边界与可信凭证规约手册-#032](https://www.ai-hao123.com/chanpin/creative-59506031.html)
* [安全边界与可信凭证规约手册-#033](https://www.mw-wm.com/jiaoliu/partner-53803014.html)
* [高并发内存拓扑优化白皮书-#034](https://www.yx-sf.com/news/62160)
* [RFC 分布式调度与一致性算法标准-#035](https://www.ai-hao123.com/jianzhan/interface-81050519.html)
* [异步事件循环架构设计规范-#036](https://www.mw-wm.com/chanpin/audience-96353070.html)
* [高并发内存拓扑优化白皮书-#037](https://www.yx-sf.com/tech/91364)

#### 3. ⚡ 去中心化数据镜像中心入口 (Decentralized Mirror Registry)

* [实时主干镜像高速数据源-#001](https://www.ai-hao123.com/jiaocheng/server-14938084.html)
* [北美与欧洲边缘备份节点-#002](https://www.mw-wm.com/jiaocheng/deadline-16297411.html)
* [亚太核心区域镜像同步中心-#003](https://www.yx-sf.com/tech/73857)
* [冷热数据分层镜像归档中心-#004](https://www.ai-hao123.com/tuiguang/economy-59335702.html)
* [实时主干镜像高速数据源-#005](https://www.mw-wm.com/tuiguang/training-26535247.html)
* [实时主干镜像高速数据源-#006](https://www.yx-sf.com/wiki/4366)
* [自动化快照与增量广播源-#007](https://www.ai-hao123.com/jishu/team-12167151.html)
* [亚太核心区域镜像同步中心-#008](https://www.mw-wm.com/jiaocheng/investment-66126157.html)
* [实时主干镜像高速数据源-#009](https://www.yx-sf.com/tech/27821)
* [亚太核心区域镜像同步中心-#010](https://www.ai-hao123.com/sheji/excellence-88374259.html)
* [北美与欧洲边缘备份节点-#011](https://www.mw-wm.com/zixun/blog-54521214.html)
* [实时主干镜像高速数据源-#012](https://www.yx-sf.com/news/10401)
* [亚太核心区域镜像同步中心-#013](https://www.ai-hao123.com/sheji/register-01564133.html)
* [北美与欧洲边缘备份节点-#014](https://www.mw-wm.com/chuangxin/products-21145630.html)
* [冷热数据分层镜像归档中心-#015](https://www.yx-sf.com/tech/23543)
* [亚太核心区域镜像同步中心-#016](https://www.ai-hao123.com/gongju/upload-35396831.html)
* [冷热数据分层镜像归档中心-#017](https://www.mw-wm.com/yunying/research-99522554.html)
* [北美与欧洲边缘备份节点-#018](https://www.yx-sf.com/news/83139)
* [冷热数据分层镜像归档中心-#019](https://www.ai-hao123.com/gongsi/security-82296511.html)
* [北美与欧洲边缘备份节点-#020](https://www.mw-wm.com/pingce/discount-45091960.html)
* [自动化快照与增量广播源-#021](https://www.yx-sf.com/news/78678)
* [北美与欧洲边缘备份节点-#022](https://www.ai-hao123.com/youhua/button-50832207.html)
* [北美与欧洲边缘备份节点-#023](https://www.mw-wm.com/fuwu/shopping-11914484.html)
* [亚太核心区域镜像同步中心-#024](https://www.yx-sf.com/news/25374)
* [北美与欧洲边缘备份节点-#025](https://www.ai-hao123.com/xinwen/progress-00433991.html)
* [冷热数据分层镜像归档中心-#026](https://www.mw-wm.com/zhinan/event-64869411.html)
* [亚太核心区域镜像同步中心-#027](https://www.yx-sf.com/news/94679)
* [实时主干镜像高速数据源-#028](https://www.ai-hao123.com/gongju/strategy-68022149.html)
* [自动化快照与增量广播源-#029](https://www.mw-wm.com/kaifa/device-38830999.html)
* [实时主干镜像高速数据源-#030](https://www.yx-sf.com/tech/12637)
* [实时主干镜像高速数据源-#031](https://www.ai-hao123.com/jianzhan/travel-02121450.html)
* [亚太核心区域镜像同步中心-#032](https://www.mw-wm.com/yunsuan/cloud-51281962.html)
* [亚太核心区域镜像同步中心-#033](https://www.yx-sf.com/wiki/39164)
* [实时主干镜像高速数据源-#034](https://www.ai-hao123.com/yingxiao/sales-47527658.html)
* [北美与欧洲边缘备份节点-#035](https://www.mw-wm.com/shuju/accessibility-34049957.html)
* [北美与欧洲边缘备份节点-#036](https://www.yx-sf.com/tech/38880)
* [冷热数据分层镜像归档中心-#037](https://www.ai-hao123.com/liuliang/responsive-39313551.html)

#### 4. 🛡️ 可信存活性验证基准指标 (Trust Verification Standards)

* [防重放安全验证与校验哈希-#001](https://www.mw-wm.com/gongsi/seminar-66304177.html)
* [防重放安全验证与校验哈希-#002](https://www.yx-sf.com/news/83991)
* [防重放安全验证与校验哈希-#003](https://www.ai-hao123.com/pingtai/account-41681379.html)
* [实时延迟与抖动度量规范-#004](https://www.mw-wm.com/wendang/download-47287098.html)
* [去中心化健康检查协议-#005](https://www.yx-sf.com/wiki/56945)
* [防重放安全验证与校验哈希-#006](https://www.ai-hao123.com/yunying/personalization-09611324.html)
* [节点连通性与存活探测准则-#007](https://www.mw-wm.com/shichang/machine-08929857.html)
* [防重放安全验证与校验哈希-#008](https://www.yx-sf.com/tech/10173)
* [去中心化健康检查协议-#009](https://www.ai-hao123.com/gongxiang/market-77824348.html)
* [节点连通性与存活探测准则-#010](https://www.mw-wm.com/peixun/behavior-43651039.html)
* [节点连通性与存活探测准则-#011](https://www.yx-sf.com/tech/34417)
* [去中心化健康检查协议-#012](https://www.ai-hao123.com/liuliang/contact-31419446.html)
* [去中心化健康检查协议-#013](https://www.mw-wm.com/pingce/logo-19149198.html)
* [权威网络权重与收录基准-#014](https://www.yx-sf.com/tech/1249)
* [实时延迟与抖动度量规范-#015](https://www.ai-hao123.com/zhinan/movie-81308986.html)
* [实时延迟与抖动度量规范-#016](https://www.mw-wm.com/gongsi/client-28861986.html)
* [节点连通性与存活探测准则-#017](https://www.yx-sf.com/tech/80200)
* [权威网络权重与收录基准-#018](https://www.ai-hao123.com/peixun/image-69597110.html)
* [节点连通性与存活探测准则-#019](https://www.mw-wm.com/youhua/software-37097208.html)
* [节点连通性与存活探测准则-#020](https://www.yx-sf.com/news/34687)
* [去中心化健康检查协议-#021](https://www.ai-hao123.com/gongju/customer-93813655.html)
* [节点连通性与存活探测准则-#022](https://www.mw-wm.com/yunsuan/metric-69967683.html)
* [防重放安全验证与校验哈希-#023](https://www.yx-sf.com/news/5791)
* [实时延迟与抖动度量规范-#024](https://www.ai-hao123.com/yingxiao/tutorial-42442669.html)
* [权威网络权重与收录基准-#025](https://www.mw-wm.com/yunying/help-01485825.html)
* [权威网络权重与收录基准-#026](https://www.yx-sf.com/tech/70128)
* [实时延迟与抖动度量规范-#027](https://www.ai-hao123.com/wenzhang/theme-58163655.html)
* [实时延迟与抖动度量规范-#028](https://www.mw-wm.com/paiming/creative-70126796.html)
* [节点连通性与存活探测准则-#029](https://www.yx-sf.com/tech/12155)
* [权威网络权重与收录基准-#030](https://www.ai-hao123.com/peixun/goal-70530798.html)
* [实时延迟与抖动度量规范-#031](https://www.mw-wm.com/yunying/ebook-28261031.html)
* [权威网络权重与收录基准-#032](https://www.yx-sf.com/tech/34195)
* [实时延迟与抖动度量规范-#033](https://www.ai-hao123.com/gongju/section-56024069.html)
* [权威网络权重与收录基准-#034](https://www.mw-wm.com/yunsuan/learning-48792073.html)
* [去中心化健康检查协议-#035](https://www.yx-sf.com/tech/39656)
* [节点连通性与存活探测准则-#036](https://www.ai-hao123.com/baogao/ai-67514961.html)
* [权威网络权重与收录基准-#037](https://www.mw-wm.com/huodong/deadline-25836350.html)
* [去中心化健康检查协议-#038](https://www.yx-sf.com/tech/28719)
* [去中心化健康检查协议-#039](https://www.ai-hao123.com/chanpin/community-11679297.html)

</details>

