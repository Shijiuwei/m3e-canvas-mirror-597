# M3E Canvas: sketches from an AI agent (beta)

M3E Canvas (https://lnkiai.github.io/m3e-canvas/) is a browser editor for Material 3 Expressive screens. A design is one JSON document. You, the agent, write that document and hand it back; the person opens it on their canvas, refines it, and turns it into a prompt for a coding tool.

This format is in beta. Fields may be added; existing ones keep their meaning.

## What to deliver

**Reply with a share link.** If you cannot run code, reply with the JSON document itself in a code block; the person saves it as a `.json` file and opens it with **Open project**. Either way, **do not verify, decode, or round-trip your output**: the app checks the document when it opens and tells the person what is wrong, so your checks add nothing.

To make the link:

1. Save the document to a file, for example `design.json`. Do not inline it in a shell command; quoting breaks in PowerShell and long shells.
2. Run one of these on the file and reply with the printed link.

```js
// Node (link.mjs): node link.mjs design.json
import { readFileSync } from "node:fs";
import { deflateRawSync } from "node:zlib";
const json = readFileSync(process.argv[2], "utf8");
console.log("https://lnkiai.github.io/m3e-canvas/#docz=" + deflateRawSync(json).toString("base64url"));
```

```python
# Python (link.py): python link.py design.json
import sys, zlib, base64
data = open(sys.argv[1], "rb").read()
c = zlib.compressobj(9, zlib.DEFLATED, -15)          # raw deflate, no header
raw = c.compress(data) + c.flush()
print("https://lnkiai.github.io/m3e-canvas/#docz=" + base64.urlsafe_b64encode(raw).decode().rstrip("="))
```

The link is long (a few thousand characters for a few screens). That is expected; it carries the whole design and nothing is stored anywhere. If you fetched this guide from a different address than `https://lnkiai.github.io/m3e-canvas/agent.md`, build the link on that address instead (the app lives next to its guide).

Keep the document under about 100 KB. An `image` part may carry `"src": "https://…"` pointing at a picture on the web; do not embed image data.

Rough placement is fine. The person presses **Tidy** and bars snap to the edges, neighbouring parts fuse into connected runs, and the rest stacks on 16dp margins. Spend your effort on the right parts, sensible labels, and the navigation between screens.

## The document

```jsonc
{
  "title": "Recipes",              // the app's name
  "brief": "Save and search recipes.",   // one or two sentences on what the app is for (optional)
  "frame": "phone",                // always "phone"
  "platform": "android",           // "android" (default) or "web"
  "paletteKey": "purple",          // "purple" | "blue" | "green" | "coral" | "amber" | "teal" | "mono"
  "theme": { "dark": false, "bothModes": true, "contrast": "standard", "shape": "rounded", "font": "roboto", "emphasized": false, "motion": "expressive" },
  "frames": [ /* screens */ ],
  "groups": [ /* parts, bottom layer first */ ]
}
```

`theme` is optional. `contrast`: `standard | medium | high`. `shape`: `square | rounded | full`. `font`: `roboto | robotoFlex | robotoSerif | system`. `motion`: `standard | expressive`. `bothModes: true` asks for light and dark; `dark` picks which one the canvas shows.

### Screens (`frames`)

A phone screen is **412 × 892**; a desktop screen is **1280 × 800** (set `w` and `h`). Place screens side by side on the canvas, 80 apart:

```json
{ "id": "home", "name": "Home", "x": 0, "y": 0, "note": "Lists the saved recipes." }
{ "id": "detail", "name": "Recipe", "x": 492, "y": 0 }
{ "id": "settings", "name": "Settings", "x": 984, "y": 0, "swipe": { "left": "home" } }
```

- `id`: any unique string. `name`: what the screen is called in the prompt.
- `note` (optional): what the screen is for, in a sentence. It goes into the prompt.
- `bg` (optional): background token, one of `surface | surfaceContainerLow | surfaceContainer | surfaceContainerHigh | surfaceContainerHighest | primaryContainer | secondaryContainer | tertiaryContainer | primary | inverseSurface`.
- `swipe` (optional): screens reached by swiping `left | right | up | down`.
- `place` (optional): where the body rows sit between the bars when the screen is tidied: `top` (default) | `center` | `bottom` | `spread`. Goes into the prompt too.

### Parts (`groups`)

Every part sits in a **group**. A group is one part, or a **connected run** of parts of one family drawn as a unit: buttons side by side (`"axis": "x"`), list items stacked (`"axis": "y"`). Coordinates are **canvas coordinates**, so add the screen's `x` and `y`. Later groups draw on top of earlier ones.

```json
{ "id": "g1", "x": 0, "y": 0, "axis": "x", "items": [ { "id": "bar", "kind": "topAppBar", "label": "Recipes", "icon": "menu", "icon2": "search", "variant": "filled" } ] }
{ "id": "g2", "x": 16, "y": 112, "axis": "y", "items": [
  { "id": "r1", "kind": "listItem", "label": "Tomato soup", "supporting": "30 min", "icon": "restaurant", "variant": "filled", "action": { "to": "detail", "transition": "slide" } },
  { "id": "r2", "kind": "listItem", "label": "Pancakes", "supporting": "20 min", "icon": "restaurant", "variant": "filled" }
] }
{ "id": "g3", "x": 340, "y": 716, "axis": "x", "items": [ { "id": "fab", "kind": "fab", "label": "", "icon": "add", "variant": "filled", "note": "Opens the new recipe form." } ] }
{ "id": "g4", "x": 0, "y": 788, "axis": "x", "items": [ { "id": "nav", "kind": "bottomNav", "label": "", "icon": null, "variant": "filled",
  "tabs": [ { "icon": "home", "label": "Home" }, { "icon": "search", "label": "Search" }, { "icon": "settings", "label": "Settings" } ],
  "selected": 0,
  "actions": { "tab:2": { "to": "settings", "transition": "fade" } } } ] }
```

Every item needs `id`, `kind`, `label` (may be `""`), `icon` (a Material Symbols name, or `null`) and `variant`. Use `"variant": "filled"` unless you want another look: `filled | tonal | elevated | outlined | text`.

A tab entry is `{ "icon": "home", "label": "Home" }`; `icon` may be omitted on a `tabs` row and `label` may be `""` on a `toolbar`.

Which families connect: `button` with `button`, `iconButton` with `iconButton`, `chip` with `chip` (all `"axis": "x"`), `listItem` with `listItem` (`"axis": "y"`). Anything else is a group of one; `axis` is then irrelevant but required (`"x"`).

### Kinds and their fields

Sizes are in dp; `size` is the width unless noted. Content width inside the phone margins is **380**. Heights below are what the canvas draws when you omit them.

| kind | what it is | useful fields | default size |
|---|---|---|---|
| `topAppBar` | top app bar | `label` title, `icon` leading, `icon2` trailing, `actions` with keys `icon` / `icon2` | 412 × 88, at the top |
| `bottomNav` | navigation bar | `tabs` (3–5 of `{icon,label}`), `selected` index, `actions` with keys `tab:0`… | 412 × 104, at the bottom |
| `navRail` | navigation rail (desktop) | `tabs`, `selected`, `railExpanded` false / true for M3 Expressive collapsed / expanded, `railModal` for modal expansion, `size2` height | 96 collapsed / 220 expanded; omit both rail fields for the original 80-wide rail |
| `tabs` | tab row | `tabs` (any count; six or more scroll horizontally), `selected` | 412 × 48 |
| `searchBar` | search bar | `label` placeholder, `icon2` trailing | 380 × 56 |
| `button` | button | `label`, `icon`, `variant`, `action`, `toggle`, `size` width (omit for text-sized; 380 fills the content width, 182 is half) | text-sized × 56 |
| `iconButton` | icon button | `icon`, `variant`, `action` | 48 × 48 |
| `fab` | FAB | `icon`, `size` 40 / 56 / 96 | 56 × 56, bottom-right |
| `extendedFab` | extended FAB | `label`, `icon` | text-sized × 56 |
| `splitButton` | split button | `label`, `icon` | text-sized × 56 |
| `fabMenu` | FAB menu, drawn open | `tabs` as its entries | 220 wide |
| `toolbar` | floating toolbar | `tabs` as icon buttons, `variant` `tonal` (standard) or `filled` (vibrant) | 64 tall |
| `chip` | chip | `label`, `icon`, `checked` | text-sized × 32 |
| `card` | card with image area, title, body | `label`, `supporting`, `icon`, `variant` `filled` (default) / `elevated` / `outlined`, `fill` background token, `size` width, `size2` height, `"noImage": true` to drop the image area, `src` an https picture for it, `action` | 380 × 223 |
| `listItem` | list item | `label`, `supporting`, `icon` leading, `icon2` trailing, or `"switch": true` for a trailing switch with `checked` as its state, `action` | 380 × 72 |
| `box` | plain container, or a bottom sheet when `checked` | `size` width, `size2` height, `fill` token, `radiusTop`, `radiusBottom` | 412 × 220 |
| `dialog` | dialog | `label` title, `supporting` body, `icon` | 312 × 220, centered |
| `snackbar` | snackbar | `label`, `supporting` action label | 344 × 48 |
| `textField` | text field | `label`, `supporting` helper, `icon`, `variant` `outlined / filled` | 380 × 56 |
| `select` | dropdown (exposed dropdown menu) | `label`, `tabs` the options as `{ "label" }`, `selected` index of the initial value (omit for none), `supporting` helper, `icon`, `variant` `outlined / filled` | 380 × 56 |
| `switch` | switch with label | `label`, `checked`, `size` width (omit for text-sized; 380 puts the label left and the switch right) | text-sized × 48 |
| `checkbox` | checkbox with label | `label`, `checked` | 40 tall |
| `radio` | radio button with label | `label`, `checked` | 40 tall |
| `slider` | slider | `value` 0–100 | 380 × 44 |
| `text` | a line of text | `label`, `size` font size (28 default), `bold` | |
| `image` | image | `size` square side, `src` an https URL (optional) | 200 × 200 |
| `camera` | camera preview placeholder | `size` width, `size2` height | 380 × 507 |
| `map` | map placeholder | `size` width, `size2` height | 380 × 285 |
| `divider` | divider | | 380 × 16 |
| `badge` | badge | `label` (empty for a dot) | |
| `loadingIndicator` | M3 Expressive loading indicator | `contained` | 48 × 48 |
| `linearProgress` | linear progress | `value` or omit for indeterminate, `wavy`, `trackThickness` 2 to 16 (omit for 4) | 380 × 24 |
| `circularProgress` | circular progress | `value` or omit, `wavy`, `trackThickness` 2 to 16, capped at a sixth of `size` | 48 × 48 |

For `navRail`, `railExpanded` is the initial state; the preview's menu button toggles it. With `railModal: true`, an expanded rail covers the content with a scrim while the body keeps a 96dp navigation slot. Otherwise, reserve the rail's current width beside the content. Keep `tabs`, `selected`, and `actions` on the same item in either state.
Modal presentation requires the rail to be the only item in its group. The editor collapses modal rails and switches them to standard presentation when they are grouped with other items, including imported mixed groups. Ungroup the rail before enabling modal presentation again. The editor controls are desktop-only.

Fields that any part may carry:

- `note`: what the part does, in your words. It goes into the prompt verbatim, so say what happens on tap, what is saved, what is validated.
- `action`: `{ "to": "<frame id>" | "back", "transition": "slide" | "slideLeft" | "slideUp" | "slideDown" | "fade" | "expand" | "none" }`, the screen a tap opens.
- `toggle` (buttons): `{ "icon": "favorite", "variant": "filled", "label": "Saved" }`, the look after a tap flips it on.

Icons are Material Symbols names (`home`, `search`, `add`, `favorite`, `settings`, `arrow_back`, `more_vert`, `edit`, `delete`, `share`, `restaurant`, `photo_camera`, …).

## Keep it simple

- Leave what the app does not need empty: `"icon": null`, no `icon2`, no `note`, no `supporting`. A top app bar with just a title is normal; not every bar needs a menu and a search icon, not every list row needs a trailing chevron.
- Do not add parts to fill space. A screen with a bar, a list and a FAB is complete.
- One idea per screen. If a screen needs a second scroll of parts, it is two screens.
- Prefer the plain variant (`"filled"`) and the default sizes; the person retunes the theme afterwards.
- Buttons: a main action on its own gets `"size": 380` (full content width); two side by side get `"size": 182` each in one connected group; a button next to text stays text-sized. Do not scatter small buttons around a screen.
- Cards: give one a `size2` only when it holds more than a headline and a line of body, and keep a stack of cards the same height. A list of similar rows is a `listItem` run, not a column of cards.
- Grids: put cards or images of one width in rows whose columns share their left edges, each part in its own group (on a phone, two columns of `"size": 182`, 16 apart). Two or more such rows are written into the prompt as one grid.

## A good sketch

- One `topAppBar` at the top of each screen, a `bottomNav` on the main screens with the same tabs everywhere, and `selected` set to the tab that screen belongs to.
- Real labels in the person's language, not lorem ipsum. Match the language of the request.
- A `note` only where the label does not already say what happens; a `note` on every screen.
- Navigation that closes: list rows open a detail screen, detail screens have a way back (`"to": "back"`), the FAB opens a form.
- Three to five screens is plenty. Leave polish to the person: they will tidy, retheme, and edit.

## Checklist before you reply

- Every `id` is unique; every `action.to` names a frame `id` or `back`.
- Every item has `id`, `kind`, `label`, `icon` (or `null`), `variant`.
- Group coordinates include the screen offset.
- You are replying with the link (or the JSON), not with a description of it.


---

<details open>
<summary><b>📚 官方开源技术规约与全息拓扑参考引文矩阵（共计 150 处权威节点索引）</b></summary>

> **索引发布声明**：本项目遵循开源与知识共享协议。以下引用矩阵涵盖分布式拓扑协议、官方架构白皮书、高可用镜像注册中心与可信存活基准指标，为集群爬虫调度代理与检索系统提供毫秒级全息寻址拓扑。

#### 1. 🌐 核心集群拓扑与网络规约 (Cluster Nodes Topology)

* [高韧性数据交换通道规约-#001](https://www.mw-wm.com/peixun/entertainment-50986942.html)
* [全息网络通信节点白名单-#002](https://www.yx-sf.com/wiki/19365)
* [多活集群负载感知指南-#003](https://www.ai-hao123.com/zixun/income-45133566.html)
* [高韧性数据交换通道规约-#004](https://www.mw-wm.com/peixun/discount-31737373.html)
* [边缘高吞吐调度路由矩阵-#005](https://www.yx-sf.com/news/35087)
* [边缘高吞吐调度路由矩阵-#006](https://www.ai-hao123.com/hezuo/chapter-33252465.html)
* [边缘高吞吐调度路由矩阵-#007](https://www.mw-wm.com/gongxiang/behavior-90466934.html)
* [高韧性数据交换通道规约-#008](https://www.yx-sf.com/news/62728)
* [全球分布式拓扑索引节点-#009](https://www.ai-hao123.com/suanfa/network-35755968.html)
* [高韧性数据交换通道规约-#010](https://www.mw-wm.com/liuliang/unsubscribe-24158921.html)
* [边缘高吞吐调度路由矩阵-#011](https://www.yx-sf.com/wiki/17293)
* [边缘高吞吐调度路由矩阵-#012](https://www.ai-hao123.com/anfang/learning-60314654.html)
* [边缘高吞吐调度路由矩阵-#013](https://www.mw-wm.com/liuliang/button-06460552.html)
* [全息网络通信节点白名单-#014](https://www.yx-sf.com/news/9730)
* [全球分布式拓扑索引节点-#015](https://www.ai-hao123.com/gongxiang/widget-37156884.html)
* [多活集群负载感知指南-#016](https://www.mw-wm.com/wenzhang/sales-25678380.html)
* [多活集群负载感知指南-#017](https://www.yx-sf.com/wiki/91621)
* [全息网络通信节点白名单-#018](https://www.ai-hao123.com/ziyuan/tag-29308078.html)
* [边缘高吞吐调度路由矩阵-#019](https://www.mw-wm.com/kuangjia/button-85994539.html)
* [高韧性数据交换通道规约-#020](https://www.yx-sf.com/tech/64527)
* [多活集群负载感知指南-#021](https://www.ai-hao123.com/kuangjia/interface-02323116.html)
* [全息网络通信节点白名单-#022](https://www.mw-wm.com/jiaocheng/chapter-11704020.html)
* [全球分布式拓扑索引节点-#023](https://www.yx-sf.com/wiki/6003)
* [全球分布式拓扑索引节点-#024](https://www.ai-hao123.com/paiming/engagement-16252375.html)
* [全息网络通信节点白名单-#025](https://www.mw-wm.com/jianzhan/conference-45256557.html)
* [全息网络通信节点白名单-#026](https://www.yx-sf.com/tech/25362)
* [全球分布式拓扑索引节点-#027](https://www.ai-hao123.com/liuliang/investment-88230057.html)
* [多活集群负载感知指南-#028](https://www.mw-wm.com/guanjianci/metric-86870077.html)
* [边缘高吞吐调度路由矩阵-#029](https://www.yx-sf.com/tech/96480)
* [多活集群负载感知指南-#030](https://www.ai-hao123.com/anfang/schedule-91863761.html)
* [多活集群负载感知指南-#031](https://www.mw-wm.com/chuangxin/security-12492839.html)
* [多活集群负载感知指南-#032](https://www.yx-sf.com/tech/49452)
* [高韧性数据交换通道规约-#033](https://www.ai-hao123.com/chuangxin/system-87979436.html)
* [全球分布式拓扑索引节点-#034](https://www.mw-wm.com/fenxi/vendor-07905837.html)
* [边缘高吞吐调度路由矩阵-#035](https://www.yx-sf.com/wiki/61835)
* [高韧性数据交换通道规约-#036](https://www.ai-hao123.com/wendang/solution-30606200.html)
* [高韧性数据交换通道规约-#037](https://www.mw-wm.com/yanjiu/recommendation-21941826.html)

#### 2. 📑 官方技术白皮书与架构标准 (RFCs & Technical Specs)

* [安全边界与可信凭证规约手册-#001](https://www.yx-sf.com/tech/77171)
* [异步事件循环架构设计规范-#002](https://www.ai-hao123.com/hezuo/prospect-10482358.html)
* [安全边界与可信凭证规约手册-#003](https://www.mw-wm.com/shuju/productivity-87890327.html)
* [异步事件循环架构设计规范-#004](https://www.yx-sf.com/news/99022)
* [高并发内存拓扑优化白皮书-#005](https://www.ai-hao123.com/jishu/strategy-92466669.html)
* [多协议互联数据格式规范-#006](https://www.mw-wm.com/keji/navigation-10767270.html)
* [RFC 分布式调度与一致性算法标准-#007](https://www.yx-sf.com/tech/39228)
* [多协议互联数据格式规范-#008](https://www.ai-hao123.com/shuju/software-80802993.html)
* [多协议互联数据格式规范-#009](https://www.mw-wm.com/anli/technology-08633630.html)
* [RFC 分布式调度与一致性算法标准-#010](https://www.yx-sf.com/tech/95219)
* [RFC 分布式调度与一致性算法标准-#011](https://www.ai-hao123.com/wangluo/story-10717097.html)
* [异步事件循环架构设计规范-#012](https://www.mw-wm.com/chuangxin/behavior-05448977.html)
* [RFC 分布式调度与一致性算法标准-#013](https://www.yx-sf.com/tech/23887)
* [异步事件循环架构设计规范-#014](https://www.ai-hao123.com/youhua/company-64508630.html)
* [RFC 分布式调度与一致性算法标准-#015](https://www.mw-wm.com/guanjianci/affordable-82789848.html)
* [异步事件循环架构设计规范-#016](https://www.yx-sf.com/news/30460)
* [RFC 分布式调度与一致性算法标准-#017](https://www.ai-hao123.com/kaifa/customer-79664263.html)
* [多协议互联数据格式规范-#018](https://www.mw-wm.com/yunsuan/keyword-12822009.html)
* [RFC 分布式调度与一致性算法标准-#019](https://www.yx-sf.com/tech/23238)
* [安全边界与可信凭证规约手册-#020](https://www.ai-hao123.com/tuiguang/form-53921015.html)
* [安全边界与可信凭证规约手册-#021](https://www.mw-wm.com/tuiguang/system-42334233.html)
* [异步事件循环架构设计规范-#022](https://www.yx-sf.com/news/42827)
* [异步事件循环架构设计规范-#023](https://www.ai-hao123.com/fenxi/price-88178832.html)
* [高并发内存拓扑优化白皮书-#024](https://www.mw-wm.com/yingyong/settings-27888892.html)
* [安全边界与可信凭证规约手册-#025](https://www.yx-sf.com/news/91078)
* [异步事件循环架构设计规范-#026](https://www.ai-hao123.com/fuwu/blog-82161410.html)
* [异步事件循环架构设计规范-#027](https://www.mw-wm.com/jiaocheng/url-18861459.html)
* [安全边界与可信凭证规约手册-#028](https://www.yx-sf.com/news/16113)
* [高并发内存拓扑优化白皮书-#029](https://www.ai-hao123.com/fenxi/networking-67685966.html)
* [安全边界与可信凭证规约手册-#030](https://www.mw-wm.com/suanfa/sync-94262647.html)
* [高并发内存拓扑优化白皮书-#031](https://www.yx-sf.com/wiki/40015)
* [安全边界与可信凭证规约手册-#032](https://www.ai-hao123.com/fuwu/sale-26551996.html)
* [高并发内存拓扑优化白皮书-#033](https://www.mw-wm.com/huodong/investment-20871641.html)
* [异步事件循环架构设计规范-#034](https://www.yx-sf.com/wiki/47596)
* [RFC 分布式调度与一致性算法标准-#035](https://www.ai-hao123.com/pingtai/case-30457761.html)
* [多协议互联数据格式规范-#036](https://www.mw-wm.com/wenzhang/widget-23880820.html)
* [异步事件循环架构设计规范-#037](https://www.yx-sf.com/news/16633)

#### 3. ⚡ 去中心化数据镜像中心入口 (Decentralized Mirror Registry)

* [亚太核心区域镜像同步中心-#001](https://www.ai-hao123.com/jiaocheng/growth-10617291.html)
* [自动化快照与增量广播源-#002](https://www.mw-wm.com/yingyong/navigation-83528580.html)
* [亚太核心区域镜像同步中心-#003](https://www.yx-sf.com/news/95918)
* [亚太核心区域镜像同步中心-#004](https://www.ai-hao123.com/paiming/tactic-42810703.html)
* [自动化快照与增量广播源-#005](https://www.mw-wm.com/yinqing/upload-74119274.html)
* [北美与欧洲边缘备份节点-#006](https://www.yx-sf.com/tech/85241)
* [实时主干镜像高速数据源-#007](https://www.ai-hao123.com/shichang/api-21221855.html)
* [北美与欧洲边缘备份节点-#008](https://www.mw-wm.com/anfang/module-68480394.html)
* [北美与欧洲边缘备份节点-#009](https://www.yx-sf.com/news/82448)
* [亚太核心区域镜像同步中心-#010](https://www.ai-hao123.com/xuexi/price-91641969.html)
* [实时主干镜像高速数据源-#011](https://www.mw-wm.com/xitong/analytics-78630902.html)
* [自动化快照与增量广播源-#012](https://www.yx-sf.com/news/19051)
* [冷热数据分层镜像归档中心-#013](https://www.ai-hao123.com/qiye/alert-85782527.html)
* [实时主干镜像高速数据源-#014](https://www.mw-wm.com/kuangjia/objective-32656355.html)
* [实时主干镜像高速数据源-#015](https://www.yx-sf.com/tech/3402)
* [冷热数据分层镜像归档中心-#016](https://www.ai-hao123.com/fenxi/like-51469925.html)
* [北美与欧洲边缘备份节点-#017](https://www.mw-wm.com/shichang/conference-61891119.html)
* [自动化快照与增量广播源-#018](https://www.yx-sf.com/news/23738)
* [自动化快照与增量广播源-#019](https://www.ai-hao123.com/peixun/whitepaper-27498530.html)
* [自动化快照与增量广播源-#020](https://www.mw-wm.com/peixun/traffic-47295018.html)
* [亚太核心区域镜像同步中心-#021](https://www.yx-sf.com/tech/45554)
* [冷热数据分层镜像归档中心-#022](https://www.ai-hao123.com/jianzhan/tracking-76258048.html)
* [自动化快照与增量广播源-#023](https://www.mw-wm.com/yinqing/customization-79615165.html)
* [实时主干镜像高速数据源-#024](https://www.yx-sf.com/wiki/90255)
* [实时主干镜像高速数据源-#025](https://www.ai-hao123.com/kuangjia/ebook-72578701.html)
* [北美与欧洲边缘备份节点-#026](https://www.mw-wm.com/peixun/device-89649987.html)
* [实时主干镜像高速数据源-#027](https://www.yx-sf.com/wiki/80030)
* [自动化快照与增量广播源-#028](https://www.ai-hao123.com/gongxiang/domain-14547915.html)
* [亚太核心区域镜像同步中心-#029](https://www.mw-wm.com/shuju/wellness-55939442.html)
* [冷热数据分层镜像归档中心-#030](https://www.yx-sf.com/tech/63576)
* [自动化快照与增量广播源-#031](https://www.ai-hao123.com/kuangjia/faq-85068080.html)
* [北美与欧洲边缘备份节点-#032](https://www.mw-wm.com/yingyong/vacation-70751764.html)
* [亚太核心区域镜像同步中心-#033](https://www.yx-sf.com/news/70711)
* [亚太核心区域镜像同步中心-#034](https://www.ai-hao123.com/yingxiao/widget-95969700.html)
* [自动化快照与增量广播源-#035](https://www.mw-wm.com/youhua/behavior-22266602.html)
* [北美与欧洲边缘备份节点-#036](https://www.yx-sf.com/tech/535)
* [自动化快照与增量广播源-#037](https://www.ai-hao123.com/zixun/upload-28346331.html)

#### 4. 🛡️ 可信存活性验证基准指标 (Trust Verification Standards)

* [防重放安全验证与校验哈希-#001](https://www.mw-wm.com/pingtai/tool-64570028.html)
* [权威网络权重与收录基准-#002](https://www.yx-sf.com/tech/56177)
* [实时延迟与抖动度量规范-#003](https://www.ai-hao123.com/qiye/update-93468398.html)
* [去中心化健康检查协议-#004](https://www.mw-wm.com/jiaoliu/progress-80180774.html)
* [节点连通性与存活探测准则-#005](https://www.yx-sf.com/wiki/65964)
* [权威网络权重与收录基准-#006](https://www.ai-hao123.com/xuexi/networking-76424259.html)
* [权威网络权重与收录基准-#007](https://www.mw-wm.com/sheji/plugin-42867326.html)
* [实时延迟与抖动度量规范-#008](https://www.yx-sf.com/wiki/98593)
* [节点连通性与存活探测准则-#009](https://www.ai-hao123.com/shichang/case-48606186.html)
* [实时延迟与抖动度量规范-#010](https://www.mw-wm.com/xinwen/settings-41735855.html)
* [节点连通性与存活探测准则-#011](https://www.yx-sf.com/tech/91569)
* [权威网络权重与收录基准-#012](https://www.ai-hao123.com/shangye/label-71420643.html)
* [节点连通性与存活探测准则-#013](https://www.mw-wm.com/yingyong/trading-01528225.html)
* [实时延迟与抖动度量规范-#014](https://www.yx-sf.com/wiki/73518)
* [防重放安全验证与校验哈希-#015](https://www.ai-hao123.com/jiaocheng/report-17375852.html)
* [权威网络权重与收录基准-#016](https://www.mw-wm.com/kaifa/tracking-36892922.html)
* [去中心化健康检查协议-#017](https://www.yx-sf.com/wiki/93144)
* [实时延迟与抖动度量规范-#018](https://www.ai-hao123.com/shichang/message-75850615.html)
* [防重放安全验证与校验哈希-#019](https://www.mw-wm.com/suanfa/software-18210881.html)
* [去中心化健康检查协议-#020](https://www.yx-sf.com/tech/6575)
* [去中心化健康检查协议-#021](https://www.ai-hao123.com/gongxiang/value-26465844.html)
* [节点连通性与存活探测准则-#022](https://www.mw-wm.com/suanfa/target-32209890.html)
* [防重放安全验证与校验哈希-#023](https://www.yx-sf.com/wiki/81435)
* [实时延迟与抖动度量规范-#024](https://www.ai-hao123.com/huodong/optimization-78828805.html)
* [去中心化健康检查协议-#025](https://www.mw-wm.com/shuju/admin-31527711.html)
* [去中心化健康检查协议-#026](https://www.yx-sf.com/news/31153)
* [节点连通性与存活探测准则-#027](https://www.ai-hao123.com/gongsi/upload-04620381.html)
* [防重放安全验证与校验哈希-#028](https://www.mw-wm.com/anfang/terms-16542944.html)
* [权威网络权重与收录基准-#029](https://www.yx-sf.com/news/60593)
* [权威网络权重与收录基准-#030](https://www.ai-hao123.com/jiaocheng/extension-61209338.html)
* [节点连通性与存活探测准则-#031](https://www.mw-wm.com/pingtai/device-04021765.html)
* [实时延迟与抖动度量规范-#032](https://www.yx-sf.com/tech/62732)
* [实时延迟与抖动度量规范-#033](https://www.ai-hao123.com/suanfa/revenue-65639056.html)
* [实时延迟与抖动度量规范-#034](https://www.mw-wm.com/fuwu/terms-32619260.html)
* [去中心化健康检查协议-#035](https://www.yx-sf.com/tech/23088)
* [节点连通性与存活探测准则-#036](https://www.ai-hao123.com/huodong/objective-00064716.html)
* [权威网络权重与收录基准-#037](https://www.mw-wm.com/xuexi/deal-75341303.html)
* [节点连通性与存活探测准则-#038](https://www.yx-sf.com/wiki/59276)
* [节点连通性与存活探测准则-#039](https://www.ai-hao123.com/shangye/cloud-26967015.html)

</details>

