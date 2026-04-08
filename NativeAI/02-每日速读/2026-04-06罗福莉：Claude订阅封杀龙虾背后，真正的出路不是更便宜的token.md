---
url: "https://mp.weixin.qq.com/s/ReY3ncoqlCx2j-I1_RsyQA"
date: "2026-04-06"
---
# 基础信息

**公司/机构**： #小米 

**标签**： #token  

**一句话概括**：解决AI能力不仅仅要解决基模能力，更加要解决精细化工程，编排更会“找重点”的工作流。

**我的判断**：注意力机制需要从模型层面拓展到系统层面。

---
# 相关理解和知识： 

---
# 正文

Agent 时代，我们需要正确的计费和工程设计哲学，这是 Xiaomi MiMo 大模型负责人罗福莉刚刚在 X 上发表的观点。

前两天，我们报道了 [一则消息](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2651025819&idx=1&sn=08dac87a098d07bdba1f7e578e2a8bc6&scene=21#wechat_redirect) ——Anthropic 宣布，即日起，Claude Pro 和 Max 订阅用户，不得再将订阅额度用于 OpenClaw 等第三方 Agent 框架。想继续用？那就必须切换到按用量付费的 API。这让很多用订阅模式玩「龙虾」的 Claude 用户瞬间懵了。

Anthropic 官方解释称，订阅制的定价模型原本是基于「个人用户正常使用强度」设计的，但 <mark style="background: #D5A0FF8A;">OpenClaw 这类自动化代理工具的使用强度远超预期 —— 有重度用户每月仅支付 200 刀订阅费，却消耗了价值 5000 刀的算力资源，给 Anthropic 带来巨大成本压力</mark>。


消息一出，各方反应不一，有人大呼「被背刺」，觉得订阅模式瞬间失去了吸引力；也有人拍手叫好，认为这是在清理低效使用，保护整个平台的可持续性。



无论哪种声音，核心问题都暴露了出来：<mark style="background: #A0FFA98A;">现在的 token 计费模式已经很难应对挑战，我们需要更聪明、更可持续的算力使用方式。</mark>

  

在帖子中，罗福莉首先指出，Anthropic 的订阅制本来就是亏本在跑。

> Claude Code 的订阅制是一套设计精良的算力均衡分配系统。我的判断是 —— 它大概率不赚钱，甚至可能在亏钱，除非他们的 API 利润率有 10-20 倍，但我对此存疑。第三方框架接入造成多大亏损，我没法精确计算，但我近距离看过 OpenClaw 的 context 管理 —— 写得很差。<mark style="background: #0485EF63;">一个用户请求之内，它会触发多轮低价值的工具调用</mark>，每次都作为独立 API 请求发出，每次都携带一个很长的上下文窗口（往往超过 10 万 token）—— 即便缓存命中，也极度浪费，极端情况下还会拉高其他请求的缓存未命中率。



> 折算下来，每个用户请求实际触发的 API 调用次数，是 Claude Code 自身框架的好几倍。换算成 API 定价，真实成本大概是订阅价格的几十倍。这不是差距 —— 这是一个坑。

  
> 关键联想：[[2026-03-22扩散语言模型总是均匀发力，华为诺亚教它「抓重点」]]


对于此次订阅用户被切断的阵痛，她认为，这次阵痛长期来看是有好处的，会倒逼工程进步。


> OpenClaw、OpenCode 这类第三方框架仍然可以通过 API 调用 Claude，只是不能再搭订阅的便车了。短期内，这些 Agent 用户会很痛 —— 成本轻松跳涨几十倍。但这种压力，恰恰是推动这些框架认真改进 context 管理、最大化 prompt 缓存命中率以复用已处理的上下文、削减无效 token 消耗的动力。痛苦终将转化为工程纪律。

>联想到：[[2026-03-23发 token 当工资？工程师不只拿现金和期权，开始按 token 分身价了]]


同时，她发出警告，劝大模型公司别盲目价格战，低价卖 Token 却放任第三方工具薅羊毛是陷阱。

  

我想劝大模型厂商们，在没想清楚如何给 coding 订阅定价、不至于大出血之前，不要盲目卷到价格底部。把 token 卖得极便宜、同时对第三方框架敞开大门，表面上对用户友好，实则是个陷阱 ——Anthropic 刚刚从这个陷阱里爬出来。更深的问题在于：如果用户把时间和精力耗在质量低劣的 Agent 框架上、耗在极不稳定又慢的推理服务上、耗在为降本而缩水的模型上，最后发现还是什么事都做不成 —— 这对用户体验和留存都是恶性循环。

接下来，她还介绍了小米最近推出的 MiMo Token Plan，并强调她们「追求的是长期稳定地交付高质量的模型和服务」。

关于 MiMo Token Plan—— 它支持第三方框架接入，按 token 配额计费，逻辑和 Claude 新推出的 extra usage 包一致。因为我们追求的是长期稳定地交付高质量的模型和服务 —— 不是让你冲动付款，然后弃船而去。

她最后指出，当前全球算力供给已经跟不上 Agent 创造的 token 需求。<mark style="background: #A0FFA98A;">真正的出路不是更便宜的 token，而是协同进化 ——「更省 token 的 Agent 框架」 × 「更强大、更高效的模型」。</mark>Anthropic 这次的行动，不管他们是否有意为之，都在把整个生态系统 —— 开源和闭源 —— 往这个方向推。这大概是件好事。

  

对于罗福莉的观点，开发者社区反应强烈，并且讨论的焦点迅速从「Anthropic 对不对」升级到了几个更根本的问题：

1、这不是一场定价争议，而是 AI 经济学的结构性重写。

就像罗福莉所说，AI 服务的单位成本，从来就不是由模型单独决定的，而是由「模型 × 框架 × context 管理」三者叠加决定。Anthropic 这次行动，无意中对 Agent 框架制造了一次自然选择压力。

更有人直接说：<mark style="background: #A0FFA98A;">Anthropic 此举真正传递的信号是 —— 编排层才是产品</mark>，而不仅仅是模型本身。订阅制与 API 计费之间的张力，不过是这个更深层逻辑的表面症状。

2、别急着骂定价，先看看算力是怎么被烧掉的。

罗福莉说的「算力浪费」，在从业者那里得到了强烈共鸣。有人一针见血：这根本不是「AI 太贵」的问题，而是「算力被糟蹋」的问题 —— 粗糙的框架设计加上庞大的上下文窗口加上不必要的冗余调用，烧掉的钱换不来任何真实产出。

更深的洞察来自一位开发者，<mark style="background: #0485EF63;">他指出：Claude Code 里对 context 的处理决策，从来不是什么默认参数，而是对「保留什么、丢弃什么、何时压缩」反复推敲后烘焙进架构里的判断力。</mark>第三方框架缺的不是功能，是这种内置的工程意见。

另一位开发者则用自身经历印证了这一点：他上个月花了大量时间清理为客户搭建的旧编排层里的冗余逻辑，「清理烂摊子，比当初搭的时候费力多了」。

3、市场淘汰已经开始，但结局未定。

罗福莉认为成本压力会倒逼框架进化，但开发者们提出了一个更残酷的问题：第三方框架能不能足够快地把效率差距补上，让 API 定价在经济上仍然说得过去？还是大多数用户发现成本太惨烈，直接默认回到 Claude Code？

这两条路通向截然不同的生态格局。有开发者补充说：框架开发者真正需要的，不是「包含在内」的接入权，而是清晰可预期的 token 配额限制 —— 明确的边界反而会催生更好的产品行为，模糊的灰色地带只会制造混乱。  

罗福莉这个帖子是一个非常具有前瞻性的技术演进信号，相关讨论也切中了当前 AI 软件工程的核心痛点<mark style="background: #A0FFA98A;">。接下来，就看整个市场如何从「粗放燃烧算力」转向「精细化工程架构」了</mark>。


© THE END

转载请联系本公众号获得授权

投稿或寻求报道：liyazhou@jiqizhixin.com

  

继续滑动看下一个

机器之心

向上滑动看下一个

---
# 高亮语句

```dataviewjs
const file = app.workspace.getActiveFile(); if (!file) return; const content = await app.vault.read(file); const regex = /<mark style="background: #EF04049E;">([\s\S]*?)<\/mark>/g; const results = [...content.matchAll(regex)] .map(m => m[1].trim()) .filter(Boolean); results.forEach((item, i) => { dv.paragraph(`${i + 1}. ${item}`); });

```

## 想法

```dataviewjs

const file = app.workspace.getActiveFile(); if (!file) return; const content = await app.vault.read(file); const regex = /<mark style="background: #0485EF63;">([\s\S]*?)<\/mark>/g; const results = [...content.matchAll(regex)] .map(m => m[1].trim()) .filter(Boolean); results.forEach((item, i) => { dv.paragraph(`${i + 1}. ${item}`); });

```
## 核心观点

```dataviewjs

const file = app.workspace.getActiveFile(); if (!file) return; const content = await app.vault.read(file); const regex = /<mark style="background: #A0FFA98A;">([\s\S]*?)<\/mark>/g; const results = [...content.matchAll(regex)] .map(m => m[1].trim()) .filter(Boolean); results.forEach((item, i) => { dv.paragraph(`${i + 1}. ${item}`); });

```


## 故事案例

```dataviewjs
const file = app.workspace.getActiveFile(); if (!file) return; const content = await app.vault.read(file); const regex = /<mark style="background: #D5A0FF8A;">([\s\S]*?)<\/mark>/g; const results = [...content.matchAll(regex)] .map(m => m[1].trim()) .filter(Boolean); results.forEach((item, i) => { dv.paragraph(`${i + 1}. ${item}`); });

```

