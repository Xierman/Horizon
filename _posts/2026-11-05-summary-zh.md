---
layout: default
title: "Horizon Summary: 2026-11-05 (ZH)"
date: 2026-11-05
lang: zh
---

> 从 54 条内容中筛选出 14 条重要资讯。

---

**科技新闻**
1. [OpenAI 研究：减少 Linux 内核提权路径](#item-tech-news-1) ⭐️ 8.0/10
2. [腾讯发布开放权重模型 Hy4](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic 开源 FlashProve：用加密证明核验模型输出](#item-tech-news-3) ⭐️ 8.0/10
4. [OpenAI 宣布收购 Pierre Computer Company](#item-tech-news-4) ⭐️ 7.0/10
5. [Go 发布新 JSON API 提案：encoding/json/v2 引发迁移讨论](#item-tech-news-5) ⭐️ 7.0/10
6. [IEEE Spectrum：AI 漏洞发现被指迫使软件业偿还技术债](#item-tech-news-6) ⭐️ 7.0/10
7. [Ripple-65B 预览版宣称美国开源权重模型代理编程 SOTA](#item-tech-news-7) ⭐️ 7.0/10
8. [Moonshot AI 发布 Kimi K3.1 Pro 开放权重](#item-tech-news-8) ⭐️ 7.0/10
9. [AMD 第四季度营收指引或首次超过英特尔](#item-tech-news-9) ⭐️ 7.0/10
10. [Calif 演示绕过 iPhone 锁定模式并保留越狱](#item-tech-news-10) ⭐️ 7.0/10
11. [华为据报要求客户自行采购升腾 960DT 的 HBM](#item-tech-news-11) ⭐️ 7.0/10
12. [蓝牙 HDT 标准发布：LE 峰值速率提升至 7.5 Mbps](#item-tech-news-12) ⭐️ 7.0/10

**财经新闻**
1. [甲骨文取消与腾讯约 70 亿美元 AI 芯片租赁协议](#item-finance-news-1) ⭐️ 8.0/10
2. [民主党赢得国会两院后，10 年期美债收益率下跌](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 研究：减少 Linux 内核提权路径](https://openai.com/index/a-thousand-fewer-paths-to-root/) ⭐️ 8.0/10

OpenAI 网络安全团队发布研究文章《A Thousand Fewer Paths to Root》，提出减少 Linux 内核中可导致本地提权的一千条路径；这面向需要评估内核攻击面的维护者和安全团队，但现有材料未提供具体方法、适用内核版本或独立验证结果。Hacker News 讨论中，评论者以 948 个漏洞为参照，追问内核是否已复杂到难以推理，以及问题是否出在安全模型或语言实现。就现有信息看，“少了一千条路径”仍是该团队的主张，不能当作已复现的测量结论。

hackernews · dangelosaurus · 11月4日 23:33 · [社区讨论](https://news.ycombinator.com/item?id=50372929)

**「背景」** 本地提权（LPE）的威胁模型是：攻击者已经能以普通用户身份在机器上执行代码，再借助内核缺陷越过权限边界取得 root；这类漏洞是否成立，关键在于能否实际复现利用，而不只是发现可疑代码。OpenAI 表示其自动化管线会对候选问题做验证并生成补丁，因此这次公布的是经过利用验证的结果，而非仅靠模式匹配给出的告警。

**「社区讨论」** 评论者质疑，内核存在上千条提权路径是否说明其复杂度已超出可推理范围，或暴露了安全模型与语言实现的根本缺陷；也有人反问，既然漏洞如此多，互联网和关键基础设施为何仍能运行、哪些缓解因素避免了系统性灾难。另有评论者表示，本地提权在 Linux 上一直被视为很可能发生，但 948 个漏洞仍令人震惊，并希望最糟糕的阶段已经过去。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/a-thousand-fewer-paths-to-root/">A thousand fewer paths to root - OpenAI</a></li>
<li><a href="https://cybersecuritynews.com/openai-uncovers-948-linux-kernel-vulnerabilities/">OpenAI Cyber Model Uncovers 948 Linux Kernel Privilege ...</a></li>
<li><a href="https://explainx.ai/blog/openai-linux-kernel-948-local-privilege-escalation-exploits-1-2-million-api-cost-pipeline-patch-the-planet-2026">OpenAI Linux Kernel Pipeline: 948 Root Exploits, $1.2M ...</a></li>

</ul>
</details>

**标签**: `#Linux kernel security`, `#privilege escalation`, `#vulnerability discovery`, `#AI security`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [腾讯发布开放权重模型 Hy4](https://hy.tencent.ai/research/hy4) ⭐️ 8.0/10

腾讯发布开放权重模型 Hy4，面向科研与游戏开发等场景。腾讯还称将开源两个科学基础模型：用于单细胞表征的 HyCell 和用于物理场建模的 HyPDE。面向游戏开发，Hy4 针对 Unreal Engine、Unity 和 Godot 做了适配，训练与评测覆盖功能实现、玩法逻辑、状态跟踪和资产管线，并扩展到多人游戏开发；腾讯同时承认，它在研究级数学、长程编码、模型自我改进和高级视觉问答等内部基准上仍落后于顶级闭源模型。

hackernews · Philpax · 11月4日 14:11 · [社区讨论](https://news.ycombinator.com/item?id=50365780)

**「背景」** Hy4 属于腾讯的 Hy 模型家族。此前的 Hy4-preview 是一款混合专家（MoE）旗舰模型，总参数为 770B，每个 token 激活 49B；据现有报道，Hy4 是该家族中首次加入视觉理解能力的模型，也被视为腾讯追赶领先开源模型的最新尝试。

**「影响」** 使用 Unreal Engine、Unity 或 Godot 的开发者多了一个针对功能实现、玩法逻辑、状态跟踪和资产管线调优的开放权重选项，且覆盖多人游戏开发；但腾讯承认其在长程编码等任务上落后于顶级闭源模型，复杂项目仍需人工复核。

**「社区讨论」** 评论者一方面赞赏腾讯把 HyCell、HyPDE 开源给科研使用，areoform 认为这与一些美国初创公司限制研究用途形成对比；frangonf 也认可官方坦承 Hy4 与顶级闭源模型在难题上的差距。chriddyp 报告的基准体验是，Hy4 在 Plotly 数据分析基准上的性价比位于 GPT-6.1 Sol 与 Terra 之间，但响应很慢：每题平均约 26 次查询、部分达 64 次，个别查询耗时约一小时。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://interestingengineering.com/ai-robotics/tencent-hy4-open-source-model">China&#x27;s Tencent Hy 4 challenges world&#x27;s top models with 7.2% error rate</a></li>
<li><a href="https://huggingface.co/tencent/Hy4-preview">tencent / Hy 4 -preview · Hugging Face</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#Tencent`, `#AI research`, `#game development`, `#scientific foundation models`

---

<a id="item-tech-news-3"></a>
### [Anthropic 开源 FlashProve：用加密证明核验模型输出](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic 正在开发并开源 FlashProve，用加密证明核验某段输出是否由指定模型生成。研究人员称，它可帮助用户识别模型替换，也可核实第三方关于模型执行任务的说法；发布模型的实验室需公开不披露权重的指纹，验证可在本地设备进行。Anthropic 已发布技术规范和代码，但研究仍在进行，目前没有部署计划。

hackernews · ltononro · 11月4日 17:17 · [社区讨论](https://news.ycombinator.com/item?id=50368626)

**「背景」** 可验证推理要解决的是一个信任缺口：模型提供方声称某段输出由指定模型生成，但用户看不到权重，也难以自行复算。此前 VerInf 已对完整的 48 层 Llama 4 Maverick（400B 参数 MoE）前向传播生成 Ligero 证明，但单次证明在单台 DGX Spark 上耗时约 19.3 小时，表明全模型证明可行，但证明成本仍是实用化的主要障碍。

**「影响」** 对 API 用户和审计方而言，这提供了一种不接触模型权重、仅凭公开指纹和证明核验模型身份的路径；但由于尚无部署计划，当前不能把它当作生产环境可依赖的验证机制。开发者目前能做的是审阅已发布规范和代码，并关注模型方是否会公开指纹。

**「社区讨论」** 评论中，neuwirth 称 FlashProve 建立在其 VerInf 工作之上但署名不足；nemo1618 认为开放权重模型只需确定性重算即可验证，比零知识证明更便宜，而 gopalv 提到单份证明验证约需 17 秒（24 线程）、承诺约 6.5 MB、覆盖约 1600 万次请求。vessenes 则认为这是相较此前 zk 结果的明显改进，但闭源模型提供商的推理证明更难，也可考虑让多个独立提供商重跑同一提示来获得更便宜的概率性证明。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/JamesPetrie/VerInf">GitHub - JamesPetrie/VerInf</a></li>
<li><a href="https://github.com/JamesPetrie/VerInf/blob/main/README.md">VerInf/README.md at main · JamesPetrie/VerInf · GitHub</a></li>

</ul>
</details>

**标签**: `#verifiable inference`, `#large language models`, `#zero-knowledge proofs`, `#AI security`, `#cryptography`

---

<a id="item-tech-news-4"></a>
### [OpenAI 宣布收购 Pierre Computer Company](https://openai.com/index/openai-to-acquire-pierre/) ⭐️ 7.0/10

OpenAI 宣布将收购 Pierre Computer Company，现有材料未披露交易金额或预计完成时间。据 Hacker News 讨论，Pierre 由 Bootstrap 最初的开发者 Jacob Thornton 和 Mark Otto 创立，其产品涉及 git/diff 开发者工具以及用于存储生成代码的 Code.Storage。此次公告目前只是收购计划，尚不等同于已完成的整合或已公布的产品路线。

hackernews · itunpredictable · 11月4日 15:21 · [社区讨论](https://news.ycombinator.com/item?id=50366863)

**「背景」** Pierre Computer 开发 Code Storage，以及用于浏览项目文件的 Trees 和审查改动的 Diffs；据 Tech Insider 报道，Codex 用户此前已在文件浏览和变更审查中使用后两项工具。Modeldex 的报道还称，Pierre 由 Bootstrap 共同创造者 Jacob Thornton 与 Ian Ownbey 创立，OpenAI 未披露交易金额。

**「对现有用户的影响」** 对使用 Pierre Code.Storage 的团队而言，OpenAI 表示交易完成后仍可继续使用该服务，但同时会将其功能整合进 Codex；这意味着相关 git 与代码审查工具的中长期形态可能从独立产品转为 Codex 的一部分，依赖它的开发者应评估迁移与集成安排。由于交易尚未完成，当前可确认的只是这一过渡承诺，具体时间表和兼容性细节尚未公布。

**「社区讨论」** 有评论者猜测，这笔收购与 OpenAI 的 git 规模化需求有关，并指出 Pierre 的 Code.Storage 已被 Lovable、Bolt、Amp 等代理式编码产品用于存储生成代码；也有人质疑，收购团队是否同时意在获取构建这类工具的过程数据。上述说法均属社区推测，公告未说明收购的战略理由。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://tech-insider.org/openai-to-acquire-pierre-codex-code-storage-trees-diffs-2026/">OpenAI Pierre Acquisition: 3 Tools for Codex [2026]</a></li>
<li><a href="https://modeldex.substack.com/p/openai-acquires-pierre-codex-git">OpenAI to Buy Pierre, the Startup Behind Code Tools Already ...</a></li>
<li><a href="https://openai.com/index/openai-to-acquire-pierre/">OpenAI to acquire Pierre Computer Company, Inc. | OpenAI</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#acquisitions`, `#developer tools`, `#AI coding`, `#git infrastructure`

---

<a id="item-tech-news-5"></a>
### [Go 发布新 JSON API 提案：encoding/json/v2 引发迁移讨论](https://go.dev/blog/jsonv2) ⭐️ 7.0/10

Go 官方博客介绍了新的 JSON API——encoding/json/v2，重点是对标准库 JSON 编解码接口进行重新设计；根据现有信息，这仍是提案与设计说明，而非已经落地的标准库变更。对使用 encoding/json 的 Go 开发者而言，直接影响是需要评估未来迁移的成本与兼容性问题。

hackernews · olexsmir · 11月4日 17:52 · [社区讨论](https://news.ycombinator.com/item?id=50369106)

**「背景」** Go 现有的 encoding/json 长期是标准库的 JSON 编解码入口，但其 API 与行为已积累了一些难以在不破坏兼容性的前提下修正的问题。为此，新的 encoding/json/v2 被放在独立的 v2 命名空间中，与 encoding/json（v1）并存，并建立在负责纯语法层处理的 encoding/json/jsontext 之上。

**「对现有代码的影响」** 对存量项目来说，encoding/json 仍以 v1 形式保留，官方包文档只是“鼓励”新用法改用 encoding/json/v2，并没有强制立刻迁移；同时新增的 encoding/json/jsontext 提供不依赖反射的纯语法层解析，面向需要自定义错误信息和更高性能的场景。有第三方把 v1 与 v2 跑在同一批结构体上对比后指出，部分默认输出会发生变化，需要靠选项或 tag 修正，因此升级到随附 v2 的 Go 版本（据报道为 Go 1.27）时，团队应先用测试比对两种实现的序列化结果，再决定迁移范围。

**「社区讨论」** 评论中，CamouflagedKiwi 认可 encoding/json/v2 的方向，但认为移除 MarshalIndent 会让迁移和快速输出可读 JSON 变得更麻烦；txomon 则分享了在公司使用 jsontext 为要求细粒度错误信息的客户编写解析器的正面经验。这些属于个人使用体验与意见，不代表社区共识。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2">A new Go API for JSON - The Go Programming Language</a></li>
<li><a href="https://github.com/golang/go/issues/71497">encoding / json / v 2 : new API for encoding / json · Issue #71497...</a></li>
<li><a href="https://importstatic.com/go/go-json-v2-migration">Go JSON v 2 Migration : What Breaks in Go 1.27 | ImportStatic</a></li>
<li><a href="https://pkg.go.dev/encoding/json">json package - encoding / json - Go Packages</a></li>
<li><a href="https://github.com/golang/go/issues/71497">encoding / json / v 2 : new API for encoding / json · Issue #71497...</a></li>

</ul>
</details>

**标签**: `#Go`, `#JSON`, `#standard library`, `#API design`, `#encoding/json/v2`

---

<a id="item-tech-news-6"></a>
### [IEEE Spectrum：AI 漏洞发现被指迫使软件业偿还技术债](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

IEEE Spectrum 的一篇分析以 PHP-to-shell 漏洞为案例，主张 AI 驱动的漏洞发现正在迫使软件团队面对并清理过去四十年积累的技术债；文章提出的是行业论点，而不是已发布的工具、版本或独立测量结果。对依赖遗留代码和开源组件的开发与安全团队而言，文章所描述的压力是更多漏洞被更快暴露并进入修复流程，但文中没有给出漏洞数量、修复成本或时间表等量化数据。因此，“偿还技术债”目前是文章的解释框架，尚不能视为已被验证的行业结果。

hackernews · pseudolus · 11月4日 11:52 · [社区讨论](https://news.ycombinator.com/item?id=50364336)

**「背景：PHP2Shell 漏洞与 AI 漏洞挖掘」** 这篇文章以 PHP2Shell 漏洞为切入点：该漏洞影响 WordPress、Drupal 等基于 PHP 的站点，包括 NASA、Wikipedia 和白宫相关网站，可导致数据窃取与远程代码执行；研究者向 PHP Foundation 报告后，补丁在漏洞遭到实际利用之前就已发布（据 tool-1-3）。IEEE Spectrum 在 2026 年 11 月 2 日由 Dina Genkina 发表的这篇文章，把这类由 AI 辅助发现、快速修补的漏洞作为论据，主张业界正被迫处理过去四十年积累下来的遗留代码与安全债（据 tool-1-1）。

**「对维护者的直接影响」** 对仍在维护 PHP 遗留代码和 WordPress 站点的团队来说，直接后果是修复节奏被 AI 的发现速度牵着走：相关论文把协同漏洞披露、证据溯源、人工复核和受限审计列为 AI 安全代理投入实用的前置条件，面向站点的解读也把重点放在站主如何应急处置与修复上。因此维护者当下的可操作事项是建立能核验报告来源的分诊与披露流程，而不是假定每个问题都能用一处窄补丁解决——后者是评论者提出的担忧，尚非已证实的结论。

**「社区讨论」** 评论区围绕这究竟是“还债”还是“无休止的修复跑步机”展开争论：swatcoder 认为许多问题需要重构而非窄补丁，xbmcuser 则认为 AI 审计会让开源“总有人审过”的假设真正落地。另有评论者预期短期漏洞披露会增加，但长期软件可能更稳健。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability">PHP2Shell Is a Wakeup Call for AI in Cybersecurity - IEEE ...</a></li>
<li><a href="https://aibriefs.news/card/37894e93-595e-40f9-a8a5-1e6ae4f75f9f">IEEE Spectrum: AI is forcing a payoff of 40 years of ...</a></li>
<li><a href="https://www.youtube.com/watch?v=G0FrekAkeFY">The PHP vulnerability that locked the internet: AI found it... - YouTube</a></li>
<li><a href="https://arxiv.org/pdf/2610.36334">PHP 2 Shell and the Future of AI - Discovered Vulnerability Disclosure...</a></li>
<li><a href="https://kcwebspecialists.com/php2shell-vulnerabilities-wordpress-security/">PHP 2 Shell Vulnerabilities : AI Discovery , Risks &amp; Fixes In Plain English</a></li>

</ul>
</details>

**标签**: `#ai-security`, `#technical-debt`, `#vulnerability-discovery`, `#open-source-security`, `#legacy-code`

---

<a id="item-tech-news-7"></a>
### [Ripple-65B 预览版宣称美国开源权重模型代理编程 SOTA](https://www.ricursive.com/ripple) ⭐️ 7.0/10

Ripple-65B Preview 宣称自己是美国开源权重模型中在代理编程任务上的最先进模型，模型规模为 65B，目前以预览形式发布。现有信息只覆盖范围较窄的代理编程基准，未披露许可条款、推理成本或实际部署方式，因此这一“SOTA”不能等同于整体能力或全球范围领先。

hackernews · Philpax · 11月4日 18:53 · [社区讨论](https://news.ycombinator.com/item?id=50369925)

**「背景」** “开放权重”指模型权重可供下载并自行部署；Ripple-65B Preview 的模型卡显示，它是 65B 参数的稠密 Transformer，预训练使用 12 万亿 token，并支持最长 100 万 token 的上下文。与混合专家（MoE）模型相比，稠密模型在推理时通常需要调用更多参数，这也是讨论其部署成本和本地运行可行性时的重要技术背景。

**「影响」** 对于受美国司法辖区采购限制、不能使用非美国公司模型的团队，Ripple-65B 的美国开源权重身份本身可能构成选择理由，但在许可条款和部署方式公布前，这一选项仍不确定。

**「社区讨论」** 评论者质疑“SOTA”的限定过窄：有人讽刺把范围缩到美国开源权重、特定基准和特定规模后，这个称号已难以比较；也有人批评发布页没有提及其他开源权重模型。另有人指出 65B 稠密模型在消费级硬件上推理会过慢，并称其 Terminal Bench 2.1 得分为 80.5，低于其引用的 Qwen 3.8 Flash Next 的 84.3，因此实际竞争力仍取决于基准是否被过度优化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/ricursiveAI/Ripple-65B-Preview">ricursiveAI/ Ripple - 65 B - Preview · Hugging Face</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#agentic coding`, `#LLM benchmarks`, `#model release`, `#AI infrastructure`

---

<a id="item-tech-news-8"></a>
### [Moonshot AI 发布 Kimi K3.1 Pro 开放权重](https://huggingface.co/moonshotai/Kimi-K3.1-Pro) ⭐️ 7.0/10

Moonshot AI 已在 Hugging Face 发布 Kimi K3.1 Pro 的模型权重，开发者可获取权重用于自托管；据评论，OpenRouter 等第三方推理服务也已提供托管入口。现有材料未包含官方基准分数或明确的硬件门槛，有评论估算运行可能需要类似 8×B300 的节点，但这一说法未获独立确认。社区对性能评价并不一致，有人质疑该模型“为榜单优化”，也有人称在实际测试中表现很强。

hackernews · abrarthought · 11月4日 15:30 · [社区讨论](https://news.ycombinator.com/item?id=50366999)

**「背景」** Kimi K3.1 Pro 是 K3.1 系列的首个模型；据其 Hugging Face 模型卡介绍，它由 Kimi K3 经过覆盖数百个下游领域的大规模联合强化学习后训练而来，并保留 100 万 token 的上下文窗口。其前代 Kimi K3 以 2.8 万亿参数、约 1.56 TB 的下载体积和 1M 上下文开放权重，这也解释了为何围绕该系列的讨论集中在部署所需的硬件规模上。

**「部署与成本影响」** 对打算实际部署的团队来说，可行路径更可能是托管推理而非自托管：社区讨论提到在本地运行这类模型需要约 8 块 B300 级别的算力，而 OpenRouter、Together、Modal 等第三方服务已提供同价位接入，且吞吐差异明显（有用户称 Together 约为 Moonshot 官方端点的两倍）。据 eesel 的评测，K3.1 Pro 在 Kimi API 上的标价为每百万输入 token 2 美元、缓存输入 0.2 美元、输出 10 美元，比 K3 低约三分之一，与 Sonnet 5.5 同价。因此做成本评估时，需要把缓存命中率和供应商吞吐一并折算，而不能只比较标价。

**「社区讨论」** 评论对基准可信度存在分歧：有人称 K3.1 Pro 是“benchmaxxed”、未明显超过 DeepSeekV4.1-Flash，也有人表示自家测试未观察到该问题，认为它是很强的开放模型。另有用户估算运行可能需要类似 8×B300 的节点，并称 Together 和 Modal 的吞吐高于 Moonshot AI 端点。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/moonshotai/Kimi-K3.1-Pro">moonshotai/Kimi-K3.1-Pro - Hugging Face</a></li>
<li><a href="https://www.yottalabs.ai/post/kimi-k3-specs-benchmarks-how-to-access-2026">Kimi K3 Model Size, Open Weights, and Hardware Requirements ...</a></li>
<li><a href="https://www.eesel.ai/blog/kimi-k3-1-pro-review">Kimi K 3 . 1 Pro review: smart and cheap per token, but slow | eesel AI</a></li>
<li><a href="https://iadecider.com/inference-providers">Inference Providers | IADecider</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#LLM releases`, `#Moonshot AI`, `#model benchmarks`, `#inference serving`

---

<a id="item-tech-news-9"></a>
### [AMD 第四季度营收指引或首次超过英特尔](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

AMD 给出的第四季度营收指引约为 170 亿美元；如果实际业绩达到这一水平，就会高于英特尔对同一季度的预测，并可能使 AMD 首次在季度营收上超过英特尔。AMD 将部分增长归因于 Instinct AI 加速器的销售。上述数字来自公司指引和媒体基于指引作出的预测，并不代表已经实现的业绩。

hackernews · rbanffy · 11月4日 15:38 · [社区讨论](https://news.ycombinator.com/item?id=50367125)

**「营收规模对比」** 历史上英特尔的季度营收长期高于 AMD，因此若 AMD 的 Q4 指引兑现，将是其首次在季度营收上超过英特尔。当前两家公司的 Q4 展望为：AMD 约 170 亿美元（±3%），英特尔为 150 亿至 160 亿美元；相关报道以约 155 亿美元作为英特尔指引中点进行比较。上述数字都是公司指引而非最终财报。

**「对采购格局的实际影响」** 即便 AMD 的约 170 亿美元 Q4 营收指引兑现、从而在总营收上超过英特尔，这也主要是 Instinct 加速器拉动的结果，并不代表 AI 加速器市场格局发生对等变化：第三方估算显示 Nvidia 仍占该市场约 75%–81% 的营收，AMD 约占 5%–7%，英特尔仅约 1%。对数据中心买家而言，这意味着 AMD 仍是有限的第二供应源而非 Nvidia 的等价替代，英特尔的加速器产品线在短期内也难以成为可行的备选；同时需注意，超越英特尔目前仍只是基于公司指引的预测，上述份额数字也属第三方估算。

**「社区讨论」** 有评论者认为，这一变化更多反映英特尔自身的执行失误，例如有用户称曾受到第 13、14 代酷睿电压问题影响，而不是 AMD 在 AI 领域已取得决定性优势。也有人指出，AMD 的 Instinct 销量仍远不及英伟达，AMD 超过英特尔可能主要因为英特尔的加速器产品缺乏市场，并质疑双方 Epyc/Ryzen 与 Xeon/Core 产品线的实际表现对比。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://wccftech.com/amd-is-set-to-out-earn-intel-for-the-first-time-in-its-history-guiding-to-17-billion-in-q4-revenue-against-intels-15-5-billion-midpoint-projection/">AMD Is Set To Out-Earn Intel For The First Time In Its ...</a></li>
<li><a href="https://braindetox.kr/en/posts/amd_q4_revenue_surpass_intel_forecast.html">AMD Q4 Revenue Guidance: $17B vs Intel’s $15B–$16B Outlook</a></li>
<li><a href="https://commandlinux.com/statistics/ai-gpu-market-share-nvidia-vs-amd-vs-intel/">AI GPU Market Share NVIDIA vs AMD vs Intel: 2026 Statistics</a></li>
<li><a href="https://www.companieshistory.com/ai-market-share-by-company/">AI Market Share By Company Statistics 2026</a></li>

</ul>
</details>

**标签**: `#AMD`, `#Intel`, `#semiconductors`, `#CPUs`, `#AI accelerators`

---

<a id="item-tech-news-10"></a>
### [Calif 演示绕过 iPhone 锁定模式并保留越狱](https://appleinsider.com/articles/26/11/04/apples-lockdown-mode-thwarted-by-a-new-persistent-iphone-jailbreak) ⭐️ 7.0/10

黑客团队 Calif 发布视频，演示一台开启锁定模式的 iPhone 18 Pro 被越狱，并在升级到 iOS 27.2 后仍保持越狱状态。视频显示操作者先通过 AirDrop 传送 PDF，再进入设置完成系统更新。Calif 未公开技术细节，称正向苹果披露漏洞，且不会发布越狱工具；因此这目前是未经独立验证的演示，而非可获取的攻击工具。苹果曾于 2026 年 3 月宣称，锁定模式自 2022 年以来的防护成功率达 100%。

telegram · zaihuapd · 11月4日 14:38

**「背景」** 锁定模式是 iOS 面向可能遭遇定向攻击的高风险用户提供的可选强化防护，会通过限制部分功能来缩小攻击面。苹果曾在 2026 年 3 月称，该模式自 2022 年以来的防护成功率达到 100%；此次演示若获证实，将与这一说法形成直接冲突。

**「对高风险用户的实际影响」** 对记者、活动人士等依赖锁定模式抵御定向攻击的用户来说，这段演示说明该模式存在被绕过的可能，而且演示中设备升级到 iOS 27.2 后越狱状态仍然保留，因此仅靠一次系统更新未必能让设备恢复到未被入侵的状态。不过 Calif 没有公布技术细节，也没有发布工具，并称正在向苹果披露漏洞，目前不存在可复现的攻击路径，普通用户面临的实际风险无法量化，也还没有可执行的针对性缓解措施。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.iphones.ru/iNotes/hakery-vzlomali-iphone-18-pro-s-vklyuchyonnym-rezhimom-maksimalnoy-zashchity-lockdown-mode-i-dzheylbreyk-perezhil-obnovlenie-ios">Хакеры взломали iPhone 18 Pro с включённым режимом...</a></li>
<li><a href="https://tech.onliner.by/2026/11/04/specialisty-vzlomali-iphone-18-pro-s-rezhimom-maksimalnoj-zashhity-lockdown-mode">Специалисты взломали iPhone 18 Pro с режимом максимальной...</a></li>

</ul>
</details>

**标签**: `#iOS security`, `#Lockdown Mode`, `#jailbreak`, `#vulnerability disclosure`, `#Apple`

---

<a id="item-tech-news-11"></a>
### [华为据报要求客户自行采购升腾 960DT 的 HBM](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

据 The Information 报道，华为已告知部分客户，下一代旗舰 AI 芯片升腾 960DT 将主要采用三星和 SK 海力士的 HBM，并要求客户自行解决内存来源，原因是国内厂商的 HBM 产能不足。报道还称，这些 HBM 被焊在性能很弱的处理器上，按处理器编码报关运至香港，再由人携带入境并加热拆下。深圳一名芯片经纪人表示，单颗 HBM3E 的价格已从一年前的数百美元涨到约 4000 美元；该消息经 Telegram 摘要转述，相关说法尚未获得独立确认。

telegram · zaihuapd · 11月4日 14:52

**「背景」** 高带宽内存（HBM）通过堆叠 DRAM 和宽接口提供远高于普通内存的带宽，是 AI 加速器的重要配套部件；三星、SK 海力士和美光都参与了相关标准制定。由于中国厂商的 HBM 产能不足，华为在升腾 960DT 上依赖三星和 SK 海力士，TrendForce 也报道该芯片面临国产 HBM 短缺。

**「影响」** 对计划采用升腾 960DT 的客户而言，内存不再是随芯片交付的配套件，而是必须自行落实的独立采购项。在国产 HBM 产能不足、灰色市场 HBM3E 单栈价格已被推到约 4000 美元的情况下，这会直接抬高整机物料成本，并把供应连续性和合规风险转移给采购方。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/High_Bandwidth_Memory">High Bandwidth Memory - Wikipedia</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server Packages...</a></li>
<li><a href="https://xenospectrum.com/en/hbm-smuggling-copackaged-export-control/">China&#x27;s Gray Market HBM3E Trades at About $4,000 Per Unit as ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/the-information-investigates-hbm-smuggling-chain-from-south-korea-to-china">The Investigation Examines the HBM Smuggling Chain ... - KuCoin</a></li>

</ul>
</details>

**标签**: `#Huawei Ascend`, `#HBM supply`, `#AI chips`, `#semiconductor supply chain`, `#export controls`

---

<a id="item-tech-news-12"></a>
### [蓝牙 HDT 标准发布：LE 峰值速率提升至 7.5 Mbps](https://www.bluetooth.com/press/bluetooth-high-data-throughput-opens-a-new-chapter-in-wireless-performance/) ⭐️ 7.0/10

蓝牙技术联盟（SIG）宣布采纳 Bluetooth HDT（High Data Throughput），将蓝牙 LE 的最高速率从 2 Mbps 提升至 7.5 Mbps，接近四倍，并改善容量、能效和可靠性。HDT 是蓝牙 Core 7.0 的可选特性，可与旧设备兼容共存，因此并非所有设备都会立即支持。首个标准化应用面向高端无线音频，支持无损和高解析度音频，相关产品预计 2027 年推出。

telegram · zaihuapd · 11月5日 01:39

**「背景」** 蓝牙 LE 此前的最高速率由 2M PHY 提供，理论上限为 2 Mbps；HDT 将该上限提升至 7.5 Mbps，约为原来的四倍。HDT 是已采纳的 Bluetooth Core 7.0 中的可选特性，并非所有蓝牙 LE 设备都会默认具备。

**「影响」** 对高端耳机和音箱厂商而言，要提供基于蓝牙的无损或高解析度音频，需要在新品中引入 HDT 支持；在首批产品预计 2027 年推出前，现有蓝牙 LE 设备仍可按原标准工作。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.techpowerup.com/354478/bluetooth-sig-announces-bluetooth-high-data-throughput">Bluetooth SIG Announces Bluetooth High Data Throughput</a></li>
<li><a href="https://www.androidauthority.com/bluetooth-hdt-lossless-wireless-audio-3731705/">Bluetooth HDT could standardize lossless wireless audio</a></li>

</ul>
</details>

**标签**: `#Bluetooth`, `#wireless standards`, `#Bluetooth LE`, `#lossless audio`, `#hardware`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [甲骨文取消与腾讯约 70 亿美元 AI 芯片租赁协议](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 8.0/10

据媒体报道，甲骨文已取消与腾讯约 70 亿美元的 AI 芯片租赁协议；该五年期协议原计划让腾讯租用约 10 万枚先进 AI 芯片，首付款约占 30%，此前美国官员曾向甲骨文表达担忧。

telegram · zaihuapd · 11月4日 11:01

**「背景」** 美国出口管制禁止向中国企业出售英伟达最先进的 AI 芯片，促使腾讯等中国公司转向海外数据中心租用算力。

**「影响」** 协议取消意味着腾讯失去了原计划经由甲骨文在东南亚的数据中心获取约 10 万枚在华无法使用的先进 AI 芯片的途径，而甲骨文则无缘这笔约 70 亿美元、为期五年的租赁收入。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://nypost.com/2026/11/04/business/oracle-nixes-7b-chip-leasing-deal-with-chinas-tencent-after-trump-admin-pushback-report/">Oracle nixes $ 7 B chip leasing deal with China&#x27;s Tencent after Trump...</a></li>
<li><a href="https://finance.yahoo.com/technology/ai/articles/oracle-cancels-7-billion-tencent-113659321.html?fr=sycsrp_catchall">Oracle Cancels $7 Billion Tencent AI Chip Leasing Agreement ...</a></li>
<li><a href="https://www.reuters.com/world/china/oracle-abandons-7-billion-tencent-ai-deal-under-trump-pressure-ft-reports-2026-11-04/">Oracle abandons $7 billion Tencent AI deal under Trump ...</a></li>

</ul>
</details>

**标签**: `#Oracle`, `#Tencent`, `#AI chips`, `#US-China tech policy`, `#data centers`

---

<a id="item-finance-news-2"></a>
### [民主党赢得国会两院后，10 年期美债收益率下跌](https://www.cnbc.com/2026/11/03/treasury-yields-fall-as-democrats-win-big-in-us-midterm-elections.html) ⭐️ 7.0/10

美国中期选举中民主党赢得国会两院多数后，基准 10 年期美国国债收益率周三下跌逾 6 个基点（0.06 个百分点）至 4.884%，投资者正在评估分裂政府可能对赤字支出形成的约束。

rss · CNBC Finance · 11月4日 21:18

**「背景」** 此前共和党同时掌控国会参众两院，民主党在 11 月 3 日中期选举中赢下两院，意味着白宫推动立法将更困难。摩根大通在选前指出，中期选举可能影响哪些行业获得联邦资金，但难以改变美国长期财政轨迹，赤字、强制性支出和利息成本仍在推高联邦借款。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://privatebank.jpmorgan.com/nam/en/insights/markets-and-investing/ideas-and-insights/the-midterms-can-change-spending-but-not-americas-fiscal-path">The Midterms can change spending, but not America’s fiscal ...</a></li>
<li><a href="https://am.jpmorgan.com/wr/en/asset-management/institutional/insights/market-insights/market-updates/on-the-minds-of-investors/us-midterm-elections-2026-divided-government/">US midterm elections: More of the same, for now</a></li>

</ul>
</details>

**标签**: `#US Treasury yields`, `#US midterm elections`, `#oil prices`, `#fiscal policy`, `#market reaction`

---