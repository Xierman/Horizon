---
layout: default
title: "Horizon Summary: 2026-11-03 (ZH)"
date: 2026-11-03
lang: zh
---

> 从 55 条内容中筛选出 18 条重要资讯。

---

**科技新闻**
1. [Ubuntu LTS 内核近三周未修复 CVE-2026-98432 高危 RCE](#item-tech-news-1) ⭐️ 8.0/10
2. [vLLM v0.33.0rc3 发布：升级 PyTorch 2.14、仅保留 CUDA 13.0 构建](#item-tech-news-2) ⭐️ 7.0/10
3. [SGLang v0.5.23 发布：新增多款模型与低延迟模式](#item-tech-news-3) ⭐️ 7.0/10
4. [Astra 宣称直接读写权重改进 Qwen 小模型](#item-tech-news-4) ⭐️ 7.0/10
5. [Subvocal 展示 RF 智能眼镜：闭口默念转文字](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenAI 如何用 packfile-uri 扩展超大型仓库的 Git](#item-tech-news-6) ⭐️ 7.0/10
7. [陶哲轩谈 AI 时代的“无我数学”](#item-tech-news-7) ⭐️ 7.0/10
8. [一段几乎听不见的飞机声，就能定位视频的拍摄地点](#item-tech-news-8) ⭐️ 7.0/10
9. [阿布扎比与 OpenAI 签四项协议 推进机器可读政府](#item-tech-news-9) ⭐️ 7.0/10
10. [消息称 DeepSeek V5 拟改用华为升腾训练](#item-tech-news-10) ⭐️ 7.0/10
11. [纽约时报起诉 Brave 抓取内容并转售给 AI 公司](#item-tech-news-11) ⭐️ 7.0/10

**科技博客**
1. [LLM 直接读写模型权重并非超人研究能力](#item-tech-blog-1) ⭐️ 7.0/10
2. [受众俘获：参与度不等于真实读者](#item-tech-blog-2) ⭐️ 6.0/10

**财经新闻**
1. [中国证监会据报以“窗口指导”暂停 IPO 与大股东减持](#item-finance-news-1) ⭐️ 9.0/10
2. [黑石总裁呼吁以更多股权融资支持 AI 基础设施建设](#item-finance-news-2) ⭐️ 7.0/10
3. [盘前异动：雅诗兰黛业绩超预期，Marvell 同意以 1150 亿美元收购 Lumentum](#item-finance-news-3) ⭐️ 7.0/10
4. [英国拟将多数移民永久居留等待期从 5 年延至 10 年](#item-finance-news-4) ⭐️ 7.0/10
5. [苹果 2026 财年第四财季营收 1145 亿美元，大中华区创新高](#item-finance-news-5) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Ubuntu LTS 内核近三周未修复 CVE-2026-98432 高危 RCE](https://freenode.net/article/ubuntu-lts-kernels-still-unfixed-for-critical-cve-2026-98432) ⭐️ 8.0/10

据 Hacker News 上提交的报道，Ubuntu LTS 内核在 CVE-2026-98432 披露约三周后仍未发布补丁。该漏洞是 Linux 内核 IPv4 TCP 中的高危释放后使用漏洞，可从网络侧在无需认证和用户交互的情况下利用；Anthropic 已公布针对 MPTCP 监听端口的远程代码执行（RCE）利用示例。Go 官方安全团队提示，自 Go 1.24 起 Linux 上的 listen socket 默认启用 MPTCP，因此相关 Go 服务默认暴露，且即使没有 MPTCP 监听也可能受到同类攻击。

hackernews · majorchord · 11月2日 18:39 · [社区讨论](https://news.ycombinator.com/item?id=50341462)

**「背景」** 该漏洞是 Linux 内核 IPv4 TCP 中的释放后使用问题，可由网络侧在无需认证和用户交互的情况下触发。MPTCP 是允许多条网络路径承载同一条 TCP 连接的扩展；自 Go 1.24 起，Linux 上的监听套接字默认启用 MPTCP，因此相关 Go 服务即使没有显式配置 MPTCP 监听，也可能处于暴露范围。

**「影响与应对」** 对使用 Ubuntu LTS 的运维人员来说，最直接的后果是：在官方内核补丁到位之前，对外暴露的 TCP 服务只能依靠自行检查和临时缓解措施来控制风险。AWS 的安全公告指出，该漏洞位于 Linux 内核的 IPv4 TCP 握手路径中，影响 4.4 及之后的内核版本，远程未认证的第三方可以向受影响的监听端发送带有 IP 选项的构造报文来触发该漏洞；Ubuntu 的 CVE 页面已经记录上游修复（“ipv4: free inet\_opt and ireq\_opt after an RCU grace period”），但按照报道，LTS 内核仍未获得更新。实际应对上，应先核对正在运行的内核版本，并用 \`ss -M\` 检查是否存在 MPTCP 监听，再决定是否缩减对外端口范围，或对入站 TCP 流量加过滤。来源还提到，从 Go 1.24 起，Linux 上的监听 socket 默认启用 MPTCP，因此用 Go 编写的服务不能假定自己不受影响。

**「社区讨论」** 评论中有人提出，可在 raw PREROUTING 用 iptables/nftables 的 U32 规则丢弃相关 TCP 流量，作为内核补丁前的临时缓解；也有人追问 Ubuntu 延迟近三周的原因，并指出 Ubuntu 未提供缓解说明，而 RHEL 的缓解措施被标注为只能降低暴露、不能完全阻止。另有评论提到大量消费级路由器同样运行 Linux 却几乎从不提供内核安全更新，认为这构成更广泛的隐患。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://ubuntu.com/security/CVE-2026-98432">CVE-2026-98432 | Ubuntu</a></li>
<li><a href="https://aws.amazon.com/security/security-bulletins/2026-160-aws/">CVE-2026-98432 - Linux kernel IPv4 TCP use-after-free ...</a></li>
<li><a href="https://computingforgeeks.com/linux-kernel-cve-2026-98432/">CVE-2026-98432: Check and Patch the Linux Kernel TCP Flaw</a></li>

</ul>
</details>

**标签**: `#linux`, `#ubuntu`, `#kernel`, `#security vulnerability`, `#open source`

---

<a id="item-tech-news-2"></a>
### [vLLM v0.33.0rc3 发布：升级 PyTorch 2.14、仅保留 CUDA 13.0 构建](https://github.com/vllm-project/vllm/releases/tag/v0.33.0rc3) ⭐️ 7.0/10

vLLM 发布 v0.33.0rc3，发布说明以 v0.33.0 列出 927 个提交和 389 名贡献者。该版本将运行时升级到 PyTorch 2.14.0（torchvision 0.29.0、Triton 3.8.0），并停止发布 CUDA 12.9 的 wheel 和镜像，默认构建改为 CUDA 13.0，同时 CUDA wheel 现与 libtorch ABI 稳定。它新增 Reflection Beam-1.0、Yandex AliceAI-Foundation-80B-A3B 等模型支持，并包含移除 Medusa、MLP speculator 和旧版 Ray compiled-graph executor 等破坏性变更。

github · khluu · 11月2日 10:10

**「背景」** vLLM 是开源的大语言模型推理与服务引擎，发布时同时提供 Python wheel 和多后端 Docker 镜像。其安装包与镜像需要同 PyTorch、CUDA/ROCm 等底层运行时匹配，因此底层版本升级会直接影响已有部署的安装方式和兼容性。

**「影响」** 使用 CUDA 12.9 的部署无法直接改用新构建，需要切换到默认的 CUDA 13.0 wheel 或镜像，或留在旧版本；依赖 Medusa、MLP speculator 或旧版 Ray compiled-graph executor 的服务也需要在升级前调整。

**标签**: `#vllm`, `#llm-inference`, `#pytorch`, `#cuda`, `#open-source`

---

<a id="item-tech-news-3"></a>
### [SGLang v0.5.23 发布：新增多款模型与低延迟模式](https://github.com/sgl-project/sglang/releases/tag/v0.5.23) ⭐️ 7.0/10

SGLang v0.5.23 已发布，包含 1007 个 PR、257 名贡献者的改动，新增 Muse Spark Open、Beam-1.0、MiniMax-M3.1-Flash、MiniCPM-V 4.7、Kev 等语言/视觉语言模型，以及 Cosmos3-Nano-Sim、FastH3 Omni、FLUX.3 Image Klein、HY-Nomas、MOSS-Image 等扩散模型的支持。发布说明称，DeepSeek-V4.1 在 GB300 上负载下的预填充吞吐最高提升 1.5 倍，32K 至 64K 提示词的首 token 延迟降低约 28%；可选的 NVIDIA megakernel 与 AMD monokernel 插件把 DeepSeek-V4.1-Flash 解码变为融合持久化内核，单用户解码在 GB300 上最高快 44%、在 MI350X 上快 75%。同版本还引入可选的 Paged Experts（让超出显存的 MoE 模型在单张消费级 GPU 上运行，比 CPU offload 快最多 30 倍）、可在 FP8/NVFP4 量化 MoE 上服务 LoRA 适配器的新 LoRA 引擎，以及通过 SGLang-TorchTPU 插件对 Google TPU7x 的支持。安装命令为 uv pip install --prerelease=allow sglang==0.5.23，NVIDIA CUDA 13、AMD MI35x/MI30x、Intel GPU/CPU 均有对应镜像，TPU7x 使用单独的 v0.1.0-tpu 镜像；所给发布说明在 CUDA Graph 章节处被截断，完整改动未全部可见。

github · Fridge003 · 11月2日 22:14

**「背景」** SGLang 是开源的大模型推理服务框架，以版本号发布的镜像和 pip 包形式分发，每个版本通常同时包含新模型接入、内核与调度优化，并提供 NVIDIA、AMD、Intel 及 TPU 等平台的 Docker 镜像。v0.5.23 延续这一模式：升级命令为 \`uv pip install --prerelease=allow sglang==0.5.23\`，Docker 镜像标签与版本号一致。因此，本次发布中列出的模型支持与性能改动都需在对应平台的镜像或该版本包上才能获得。

**「影响」** 对显存受限、想在单卡上跑大 MoE 的团队，Paged Experts 与量化 MoE 上的 LoRA 支持均标注为 opt-in，低延迟 megakernel/monokernel 也需要显式启用，因此升级到 0.5.23 后默认配置不会自动获得这些加速，需按文档开启并验证。部署侧需注意安装带 --prerelease=allow 参数，AMD MI35x/MI30x、Intel GPU/CPU 与 TPU7x 要拉取各自平台的镜像（TPU 镜像标签为 v0.1.0-tpu，而非 0.5.23）。

**标签**: `#SGLang`, `#LLM inference`, `#open-source release`, `#model support`, `#AI infrastructure`

---

<a id="item-tech-news-4"></a>
### [Astra 宣称直接读写权重改进 Qwen 小模型](https://rikiyat.github.io/blog/weight-space-programming/) ⭐️ 7.0/10

一篇博客和 Hacker News 讨论称，Astra 无需借助外部工具即可读取并直接编辑模型权重，并据此改进一个小型 Qwen 模型的数学表现；社区转述提到提升约为 5 倍。当前可核实的信息仅来自博客和社区讨论，尚无独立复现或详细评测，因此这些结果仍属作者声明，而非已确认的能力。熟悉权重空间学习的研究者在评论中反驳称，编辑权重、生成新权重以及定位相关权重并非全新能力，博客和发帖夸大了结果。

hackernews · dbreunig · 11月2日 18:21 · [社区讨论](https://news.ycombinator.com/item?id=50341174)

**「背景」** 这里的“权重空间编程”指不通过提示词或外部程序，而是直接检查并修改模型参数来改变模型行为；相关博客称，LLM 可以原生读取权重。外部报道把这次演示具体描述为 GPT-6 Astra 编辑 Qwen3.5-0.8B 的权重，并把 MATH-500 成绩从 7.9% 提升到 48.1%，Hugging Face 上也有对应的 Qwen3.5-0.8B-Astra-WeightEdit 权重仓库。此前常见做法是用 LLM 优化提示词和围绕模型的程序，因此讨论焦点在于“直接改权重”是否如宣传般新颖且可复现。

**「影响」** 对关注模型编辑和可解释性的开发者而言，实际影响是：在独立复现并与既有权重编辑方法对比之前，不应把 Astra 所称的 5 倍数学提升当作可依赖的工具能力。

**「社区讨论」** 评论区分歧明显：一位自称从事权重空间学习研究的评论者认为，直接编辑、生成和定位权重早已存在，博客与发帖夸大了 Astra 的新颖性和效果；另一位评论者则称其无需工具即可识别小型网络的训练任务，并把小型 Qwen 的数学能力提升约 5 倍，对此表示震惊。这些均为社区观点，不能视为独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026">GPT-6 Astra Edits Qwen Weights: MATH-500 7.9% to... | explainx.ai</a></li>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read...</a></li>
<li><a href="https://huggingface.co/JonathanColetti/Qwen3.5-0.8B-Astra-WeightEdit">JonathanColetti/ Qwen 3.5-0.8B- Astra -WeightEdit · Hugging Face</a></li>

</ul>
</details>

**标签**: `#weight-space learning`, `#LLM interpretability`, `#model editing`, `#Qwen`, `#AI research`

---

<a id="item-tech-news-5"></a>
### [Subvocal 展示 RF 智能眼镜：闭口默念转文字](https://news.ycombinator.com/item?id=50340088) ⭐️ 7.0/10

YC F26 的 Subvocal 在 Hacker News 展示了智能眼镜原型：镜框内嵌天线，发射类似蓝牙的射频信号，信号穿过面部后由舌头、嘴唇和软腭的无声动作调制，再由基础模型解码为文字，公司称其速度可达到正常说话的水平。团队表示，他们用付费参与者佩戴眼镜朗读提示词的数据做大规模预训练，演示者 Dave 经过约 20 句校准后即可使用，并强调用户不必张嘴，可以做“闭口默念”。目前这仍是原型，团队计划在未来数月继续研发，目标是在 2027 年第一季度发货；首批 500 台已开放预订，并提供 200 美元折扣，但帖文未给出最终售价、完整规格或独立验证结果。

hackernews · aarushyadav · 11月2日 17:16

**「技术背景」** 无声语音接口此前已有学术探索，例如 MIT Media Lab 的 AlterEgo 曾用面部肌电（EMG）电极捕捉默读时的肌肉信号。Subvocal 团队最初在黑客松中尝试复刻这条 EMG 路线，但受汗水、电气干扰、电极位置不稳定以及佩戴不适限制，后来转向用射频传感读取舌头、嘴唇和软腭的细微运动。

**「影响」** 对希望避开公共场合语音输入的用户来说，目前通过折扣预订能锁定的是首批 500 台中的一个名额，而不是可以立即使用的成品；发货要等到 2027 年第一季度，且帖文未给出最终售价、完整规格或第三方测试结果，因此这仍是基于原型演示的早期承诺，而非已交付的能力。

**「社区讨论」** 评论者对可行性看法不一：有人质疑闭口默念是否真能区分词句，称闭着嘴发“apple”更像“Ethan”；也有人从大鼻梁、处方眼镜适配和隐私出发提出具体问题，包括推理是在眼镜端还是 App 内完成、能否离线运行。另有评论者认为该技术对无障碍和免手操作很有价值，并希望官网补充原理解释。

**标签**: `#subvocalization`, `#silent speech`, `#smart glasses`, `#human-computer interaction`, `#accessibility`

---

<a id="item-tech-news-6"></a>
### [OpenAI 如何用 packfile-uri 扩展超大型仓库的 Git](https://openai.com/index/scaling-git-at-openai/) ⭐️ 7.0/10

OpenAI 工程博客发布《Scaling Git at OpenAI》，介绍其团队如何为超大型代码仓库扩展 Git，并把 Git 协议中的 packfile-uri 作为关键手段之一。该功能允许服务器返回链接，让客户端单独下载额外的 pack 文件，OpenAI 还为此向上游贡献了多项改进。这篇内容面向需要维护大型 monorepo 的开发者，重点是协议机制和工程实践，而非发布新的 Git 产品或托管服务。

hackernews · makeramen · 11月2日 23:47 · [社区讨论](https://news.ycombinator.com/item?id=50345924)

**「背景」** Git 协议中的 packfile-uri 是一个已有机制：服务器可把部分 packfile 响应以 URI 形式返回，让客户端另行下载，从而避免单次响应过大。OpenAI 的 Pando 是建立在这一机制之上的 Git 兼容后端，目标是支撑 Codex 带来的开发规模；据 Interesting Engineering 报道，OpenAI 用约 10 周构建它，其 monorepo 的季度提交量从 2024 年 Q1 到 2026 年 Q4 增长了 2,442%。

**「影响」** 对维护大型 monorepo 的团队，这篇说明提供了一条可操作的扩容路径：让服务器通过 packfile-uri 返回额外 pack 的下载链接，把部分数据传输从主协商流程中拆出。实际采用前仍需确认所用 Git 服务端和客户端是否支持该协议扩展，因为文章不是可直接部署的产品发布。

**「社区讨论」** 有评论者认为这是近期第五篇大型 Git 扩容文章，并把 OpenAI 这篇与 Cursor、GitHub、Anthropic 的同类文章并列；也有人称赞它没有堆砌 AI 和营销话术，而是用数字、图表和工程师口吻讲清细节。另一条质疑是文章没有给出每秒推送数、并发推送者等基准，因此难以判断这套方案的实际吞吐能力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/scaling-git-at-openai/">Scaling Git at OpenAI | OpenAI</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/openai-pando-git-backend-code-commit-surge">OpenAI builds custom Git backend in 10 weeks after 2,442% commit...</a></li>
<li><a href="https://git-scm.com/docs/packfile-uri">Git - packfile - uri Documentation</a></li>

</ul>
</details>

**标签**: `#git`, `#monorepo`, `#developer-tooling`, `#version-control`, `#engineering-infrastructure`

---

<a id="item-tech-news-7"></a>
### [陶哲轩谈 AI 时代的“无我数学”](https://terrytao.wordpress.com/2026/11/02/egoless-mathematics-in-the-ai-era/) ⭐️ 7.0/10

陶哲轩（Terry Tao）在其博客发表《Egoless Mathematics in the AI Era》，面向数学研究者和关注 AI 的读者，讨论 AI 对数学实践与数学职业的影响。这是一篇评论文章，并非发布新工具或报告实验结果；现有信息显示，它把争论引向数学中的意义、动机与价值。

hackernews · smilelamp · 11月2日 18:54 · [社区讨论](https://news.ycombinator.com/item?id=50341736)

**「背景：何谓“无我数学”」** “无我数学”（egoless mathematics）是这篇评论提出的视角：数学真理独立于发现者，因此在 AI 参与证明和研究时，评价重心应从个人成就转向数学真理本身。该文刊于 Terence Tao 的博客，但被标注为 Amit Sahai、Jie Xue 和 Karthik C. S. 的客座文章，属于哲学论证，并未提出新的 AI 基准、实验结果或机构政策。

**「社区讨论」** 评论中，kzz102 认为数学追求无法与人的理解及意义感分离；GMoromisato 用“喜欢做、擅长做、有人付费”三重交集来担忧数学家的职业前景；j2kun 则批评文章仿佛在说“人无关紧要，只有真理重要”。这些均为评论者观点，不代表文章已证实的主张。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.zeniteq.com/terence-tao-s-blog-hosts-a-call-for-egoless-mathematics-sxv5mh">Terence Tao’s Blog Hosts a Call for Egoless Mathematics</a></li>
<li><a href="https://o-server.main.jp/hacker-news/en/articles/2026/11/02/the-rise-of-egoless-mathematics-in-the-age-of-ai-50341736.html">The Rise of &#x27;Egoless Mathematics&#x27; in the Age of AI | HN Digest</a></li>

</ul>
</details>

**标签**: `#AI and mathematics`, `#research culture`, `#future of work`, `#expert commentary`

---

<a id="item-tech-news-8"></a>
### [一段几乎听不见的飞机声，就能定位视频的拍摄地点](https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/) ⭐️ 7.0/10

Simon Willison 在博客中推荐了 Colsto 的一段 YouTube 视频，后者演示了一种 OSINT 定位方法：从视频音轨中提取几乎不可察觉的飞机背景噪声，还原出各架飞机的多普勒曲线，再与 ADS-B 航班数据交叉比对。通过飞机的速度、距离以及不同航班之间的时间间隔，可以推断出视频拍摄的确切地点。Willison 称这是一次“天才般的 OSINT 操作”。需要注意的是，这一方法目前只是一段演示视频中的技术展示，并非已发布、可供他人直接复用的工具，也没有独立验证的测量结果。

rss · Simon Willison · 11月3日 05:32

**「背景」** 这类定位依赖两个前提：飞机飞过时，其噪声会因多普勒效应形成随时间变化的音高曲线；同时，ADS-B 航班数据能提供飞机的位置和速度。Colsto 的演示会针对候选位置，用插值后的 ADS-B 数据按发声时刻的径向速度建模应听到的多普勒曲线，再与视频音轨中几乎听不见的飞机声匹配，以确定录制地点。

**「影响」** 这一演示说明，仅靠删除位置元数据或避免拍到明显地标，并不足以隐藏拍摄地点：只要视频保留了环境音，其中残留的飞机声就可能成为定位线索。对经常发布户外视频的用户而言，音轨本身因此成为一个需要留意的位置信息载体。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=UytYrhYLOKI">I discovered a sound that leaks your exact location ... - YouTube</a></li>

</ul>
</details>

**标签**: `#OSINT`, `#privacy`, `#signal-processing`, `#ADS-B`, `#geolocation`

---

<a id="item-tech-news-9"></a>
### [阿布扎比与 OpenAI 签四项协议 推进机器可读政府](https://thenextweb.com/news/openai-abu-dhabi-deals-machine-readable-government-mubadala) ⭐️ 7.0/10

阿布扎比与 OpenAI 签署四项协议，覆盖政府服务、投资分析、教育与企业和能源领域。其中“机器可读政府”计划把政策法规转换为 AI 可读格式，以协助官员核查许可与证书申请；该计划已在食品进口场景试点，最终决定权仍由官员保留。穆巴达拉将与 OpenAI 及 G42 旗下 Inception42 合作开展投资分析；Inception42 另签五年协议，向阿联酋政府、企业和学校提供模型。ADNOC 成为首家使用 OpenAI Frontier 平台的能源公司。除食品进口试点外，目前披露的信息未说明其余项目的具体上线时间与部署规模。

telegram · zaihuapd · 11月2日 15:55

**「背景」** 「机器可读政府」并非让 AI 直接作出行政许可决定，而是先把法规和政策转成结构化、可被模型读取的格式，供官员核查申请；来源称食品进口已先行试点，最终决定权仍归官员。此次协议还把这一公共部门试点与穆巴达拉的投资分析、Inception42 的五年模型供给、ADNOC 的能源场景并列，显示阿布扎比正把 OpenAI 的能力嵌入多个政府与国有机构。

**「影响：模型入口与部署位置」** 对阿联酋本地机构来说，最直接的后果是获取模型的渠道和部署地点都已确定：Inception42 的五年协议把 OpenAI 模型提供给政府、企业和学校，而 ADNOC 的 OpenAI Frontier 部署则通过 Inception42 运行在 G42 位于阿联酋境内的主权 AI 基础设施上（据 tech-insider 报道，Frontier 是 OpenAI 于 2026 年 2 月推出的企业智能体平台）。不过，「机器可读政府」目前仅在食品进口许可场景试点，且官员保留最终决定权，因此应把它看作辅助核查工具，而不是把审批决定交给系统自动完成。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://tech-insider.org/adnoc-g42-openai-frontier-first-energy-company-uae-2026/">ADNOC x OpenAI: 1st Energy Firm in Frontier Program [2026]</a></li>
<li><a href="https://explainx.ai/blog/adnoc-openai-frontier-g42-first-energy-company-adipec-2026">ADNOC OpenAI Frontier Deal: First Energy Rollout Explained ...</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#government AI`, `#AI governance`, `#sovereign AI`, `#UAE`

---

<a id="item-tech-news-10"></a>
### [消息称 DeepSeek V5 拟改用华为升腾训练](https://www.eet-china.com/mp/a536460.html) ⭐️ 7.0/10

据产业链人士消息，DeepSeek 下一代大模型 V5 计划基于华为升腾芯片训练，而升腾此前主要用于 DeepSeek 模型的推理任务。该报道还称，DeepSeek 于今年 9 月底开源了面向升腾平台的基础设施组件，包括编译工具、计算库和分布式通信库，与面向英伟达平台开源的组件一一对应。上述训练计划尚未得到 DeepSeek 或华为确认，属于供应链传闻。

telegram · zaihuapd · 11月3日 06:20

**「背景」** 此前 DeepSeek 对升腾芯片的使用主要集中在推理任务。今年 9 月底，DeepSeek 开源了面向升腾的编译工具、计算库和分布式通信库，且这些组件与其面向英伟达平台开源的组件一一对应；这为外界判断其训练栈是否从英伟达转向升腾提供了参照。

**「开发适配」** 若该传闻属实，使用 DeepSeek 模型的开发者需要把兼容性检查从推理部署延伸到训练流程，重点确认升腾软件栈（如 CANN）、编译器及分布式通信库能否覆盖现有工具链。此前报道显示 V4 已可在升腾与英伟达平台双跑，但这不能证明 V5 在升腾上的训练可行性与性能，相关计划也尚未获官方确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://post.smzdm.com/p/a6z6eprz/">2026 年4月24...</a></li>
<li><a href="https://www.ai-insight.org/reports/deepseek-v4-2026">DeepSeek V 4 — 1.6T 参数 MoE 全开源 · 华 为 升 腾 SuperNode...</a></li>

</ul>
</details>

**标签**: `#DeepSeek`, `#Huawei Ascend`, `#AI training hardware`, `#open-source ML infrastructure`, `#unverified report`

---

<a id="item-tech-news-11"></a>
### [纽约时报起诉 Brave 抓取内容并转售给 AI 公司](https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/) ⭐️ 7.0/10

《纽约时报》周一起诉隐私浏览器 Brave，指控其抓取受版权保护的内容、绕过付费墙并屏蔽出版商广告，然后将这些内容出售给 Anthropic、Perplexity、Mistral、xAI、Cohere 等 AI 公司。《纽约每日新闻》《芝加哥论坛报》等媒体同日在曼哈顿联邦法院提起类似诉讼；诉状称 Brave 使用未披露的爬虫建立了超过 300 亿个网页的索引。原告寻求禁令和赔偿，Brave 暂未回应，相关指控尚待法院审理。

telegram · zaihuapd · 11月3日 06:50

**「背景」** Brave 是一款主打隐私的浏览器，广告拦截会直接影响出版商网页广告的展示；出版商则依赖广告和订阅收入。AI 公司对训练语料的需求，使“浏览器抓取内容后转售”成为版权与授权争议的新焦点。

**「直接影响」** 诉讼直接针对 Brave 的内容索引，以及它向 AI 公司提供数据的业务。原告请求禁令和赔偿；如果法院支持原告，Brave 可能被要求停止相关抓取与内容转售并承担赔偿责任，使用其搜索或数据服务的集成方也需要重新评估内容授权来源。

**标签**: `#AI copyright`, `#web scraping`, `#Brave browser`, `#publisher lawsuits`, `#AI training data`

---

## 科技博客

<a id="item-tech-blog-1"></a>
### [LLM 直接读写模型权重并非超人研究能力](https://seangoedecke.com/llms-are-not-superhuman-at-reading-and-writing-neural-network-weights/) ⭐️ 7.0/10

rss · Sean Goedecke · 11月3日 00:00

**「背景」** 近期一篇论文声称，前沿 LLM 能直接操作神经网络权重，其中 GPT-6 Astra 既能识别小网络训练的游戏，也能编辑 0.8B Qwen 的权重来改善数学表现，这被解读为可能推动递归自我改进的超人能力。作者认为，这些结果被误读成了超人级研究能力。

**「方案」** 作者用游戏网络说明，识别任务没有想象中神秘：输入通道逐格监听棋盘并带有“玩家”“移动物体”等语义标签，只需对第一层 32 个权重按输入取 L2 范数，三行 Python 就能生成热图；人看着玩家和移动物体的位置，便能认出前几个游戏。Astra 不执行代码而心算范数确实惊人，但那是超人心算，不是超人科研。更受关注的 Qwen 案例也不是“数学能力差”，而是超过 32k token 后会陷入循环，导致长题自动失败；作者说人类研究者会采用类似 steering 的流程：构造循环与非循环文本、比较残差差异、找出贡献最大的权重再裁剪。Astra 正是写了四对文本、测量导致循环的权重、逐步削减并测试，最终找到补丁，使模型能处理超过 32k token 的数学问题。作者因此把直接改权重类比为 LLM 修改编译后的二进制：技巧很酷，但最佳方式仍是修改源码并重新编译，也就是正常训练模型。

**「启示」** 作者的核心结论是，直接读写权重是令人印象深刻的工程技巧，而非改变 AI 研究方式的超人能力；智能 LLM 若真能帮助研究，更可能通过改进训练来实现，而不是靠神奇地微调权重。

**标签**: `#LLM interpretability`, `#model weight editing`, `#AI research methodology`, `#hype critique`, `#neural network weights`

---

<a id="item-tech-blog-2"></a>
### [受众俘获：参与度不等于真实读者](https://seangoedecke.com/audience-capture/) ⭐️ 6.0/10

rss · Sean Goedecke · 11月3日 00:00

**「背景」** 作者肖恩·戈德克担心网络写作中的“受众俘获”：他自认有工程师的头脑，看到参与度指标就想把它做高，而平台算法、评论排序和变现机制都在强化这种冲动。

**「方案」** 但他指出，浏览量、参与度只是代理指标，真正想要的是让聪明的读者认真考虑观点、获得有经验的反馈、参与有价值的公共讨论、说服他人并建立可靠声誉。问题在于，“点击者”和“读者”在数据上无法区分：一万人点开只读一句就关掉，对作者几乎没有价值。若写微服务之类热门话题能带来流量，他就有动力重复写，数字继续上涨，但认真阅读的读者会流失，点击者又并不真正阅读，于是真实受众被“点击者和嘲讽者”的假受众替代。作者把这一区分推广为“代理游戏”与“真实游戏”：判断标准不是目标本身多崇高，而是你是否真的在意它；Jira 指标、浏览量是前者，赢得自己尊重者的认可、做出让自己骄傲的技术工作、说服他人相信真事是后者。为晋升之类目标玩代理游戏可以是有意识的交易，甚至“出卖一点”也健康，最糟的是出于习惯出卖自己却什么也没换到。他说自己更愿意为那 5% 会阅读、思考并回信的读者写作，因为原始浏览量只能带来曝光，几乎不能告诉他是否真正打动了这些人。

**「启示」** 作者的核心结论是：参与度是引导曝光的有用代理，却不是判断是否打动真实读者的可靠信号；清楚自己玩的是代理游戏还是真实游戏，并有意识地做取舍，才能避免被自己并不想要的受众俘获。

**标签**: `#engineering career`, `#metrics and incentives`, `#online writing`, `#Goodhart&\#x27;s law`, `#software engineering culture`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [中国证监会据报以“窗口指导”暂停 IPO 与大股东减持](https://www.ft.com/content/fec5981d-0c31-4f21-9a37-a1dd1526f530) ⭐️ 9.0/10

据英国《金融时报》报道，中国证监会通过非正式“窗口指导”要求券商暂停首次公开发行（IPO）以及大股东的大规模减持，直至市场恢复。报道称，此举出台之际，沪深 300 指数 10 月下跌 8.5%，为十余年来最差单月表现，今年以来累计下跌约 14%。

telegram · zaihuapd · 11月3日 08:01

**「背景」** 所谓“窗口指导”，是监管机构通过非正式沟通要求券商等机构配合政策方向，不具有正式规则的形式；此前监管层已通过“国家队”买入、限制大股东减持等方式稳定市场，但效果不及预期。

**「影响」** 排队等待上市的企业将推迟股权融资，大股东也暂时无法通过二级市场减持套现。

**标签**: `#China equities`, `#IPO suspension`, `#securities regulation`, `#shareholder selling`, `#market intervention`

---

<a id="item-finance-news-2"></a>
### [黑石总裁呼吁以更多股权融资支持 AI 基础设施建设](https://www.cnbc.com/2026/11/03/equity-ai-debt-blackstone-pimco-financing.html) ⭐️ 7.0/10

黑石总裁乔恩·格雷（Jon Gray）在香港金管局主办的全球金融领袖投资峰会上表示，人工智能基础设施建设需要更多股权融资，因为放贷机构对该行业的敞口正变得过于集中。同场的品浩（Pimco）首席执行官埃马纽埃尔·罗曼援引 General Atlantic 首席执行官 Bill Ford 的估算称，未来五年 AI 相关资本开支可能约达 10 万亿美元；他表示今年迄今已发行约 5500 亿美元各类 AI 债务，而全球公司债市场规模约为 20 万亿美元，并警告“到某个时点，这将变得太多”。

rss · CNBC Finance · 11月3日 06:46

**「背景」** 格雷是黑石集团总裁兼首席运营官，黑石是一家总部位于纽约的资产管理公司。与股东不同，贷款人的回报主要限于利息和本金，难以分享增长收益，这是他主张增加股权融资的背景。

**「影响」** 若 AI 相关债务继续快速累积，持有相关债券的贷款机构和债券投资者将面临更高的行业与单一发行人集中度风险；部分超大规模数据中心企业已通过合资公司或特殊目的实体等表外结构融资。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Jonathan_D._Gray">Jonathan D. Gray - Wikipedia</a></li>
<li><a href="https://www.blackstone.com/people/jonathan-gray/">Jonathan Gray - Blackstone</a></li>
<li><a href="https://www.bis.org/publications/qr-202603/financing-ai-infrastructure-boom-on-and-off-balance-sheet-borrowing">Financing the AI infrastructure boom: on- and off-balance ...</a></li>

</ul>
</details>

**标签**: `#AI infrastructure`, `#debt financing`, `#credit risk`, `#private capital`, `#data centers`

---

<a id="item-finance-news-3"></a>
### [盘前异动：雅诗兰黛业绩超预期，Marvell 同意以 1150 亿美元收购 Lumentum](https://www.cnbc.com/2026/11/02/stocks-making-the-biggest-moves-premarket-crwd-rivn-mu.html) ⭐️ 7.0/10

雅诗兰黛第一财季业绩超出预期并上调全年盈利指引，同时 Marvell 同意以全股票交易收购 Lumentum，对后者估值 1150 亿美元。雅诗兰黛调整后每股收益 72 美分、营收 37.2 亿美元，分别高于 FactSet 分析师预期的 51 美分和 36.5 亿美元；该收购预计 2028 年上半年完成。

rss · CNBC Finance · 11月2日 12:49

**「背景」** 这项全股票交易对 Lumentum 的 1150 亿美元为隐含企业价值，约合每股 1132 美元，较 2026 年 10 月 28 日、即市场出现交易猜测前最后一个交易日的未受影响收盘价溢价约 23.9%。

**「影响」** 若全股票交易完成，Lumentum 股东将换取 Marvell 股票，其最终回报将取决于 Marvell 股价。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://investor.marvell.com/news-events/press-releases/detail/1040/marvell-and-lumentum-to-combine-creating-a-category-leader-in-ai-connectivity">Marvell and Lumentum to Combine, Creating a Category Leader ...</a></li>

</ul>
</details>

**标签**: `#premarket movers`, `#earnings surprise`, `#M&amp;A`, `#analyst upgrades`, `#semiconductors`

---

<a id="item-finance-news-4"></a>
### [英国拟将多数移民永久居留等待期从 5 年延至 10 年](https://www.gov.uk/government/news/home-secretary-unveils-new-rules-for-migrants-settling-in-the-uk) ⭐️ 7.0/10

英国政府向议会提交“earned settlement”定居方案，拟将多数移民申请永久居留的标准年限从 5 年延长至 10 年。年收入超过 50,271 英镑者以及医生、护士、教师等公共服务岗位人员可走 5 年通道，最高收入者最快 3 年申请。

telegram · zaihuapd · 11月2日 23:50

**「背景」** 英国现行永久居留（ILR）的标准等待期为 5 年，政府自 2025 年 11 月起就改革“earned settlement”定居制度公开咨询，此次方案拟按“缴纳贡献”和“良好品行”重新设定年限。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.gov.uk/government/consultations/earned-settlement">Earned settlement - GOV.UK</a></li>

</ul>
</details>

**标签**: `#UK immigration policy`, `#earned settlement`, `#labor market`, `#Home Office`, `#visa policy`

---

<a id="item-finance-news-5"></a>
### [苹果 2026 财年第四财季营收 1145 亿美元，大中华区创新高](https://www.apple.com/newsroom/2026/11/apple-reports-fourth-quarter-results/) ⭐️ 7.0/10

苹果公布截至 9 月 26 日的 2026 财年第四财季业绩，营收 1145 亿美元、同比增长 12%，稀释每股收益 2.10 美元、同比增长 14%，均创历年 9 月季度纪录；大中华区营收同比增长 21%，同样创下 9 月季度新高。公司高管在财报会上表示，内存涨价正在挤压毛利率，并预计内存成本将继续上升；未来 Mac 和 iPad 的供给受限主要源于内存供给紧张。苹果已上调多款产品售价，以部分抵消内存成本上涨的影响。

telegram · zaihuapd · 11月3日 04:00

**「背景」** 苹果财年通常在每年 9 月底结束，因此“第四财季”大致对应 7 月至 9 月，公司口中的“9 月季度”纪录指的就是这一时段（上一财年同期截至 2025 年 9 月 27 日）。2026 年 4 月，苹果宣布蒂姆·库克转任执行董事长、硬件工程负责人约翰·特努斯接任首席执行官，本次业绩会由特努斯等高管出席说明。

**「影响」** 苹果已上调多款产品售价以部分抵消内存成本，并预计下一季度 Mac、iPad 因内存供给紧张而供应受限，这意味着计划购买这些产品的消费者可能面对更高价格和更长等待时间。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.apple.com/newsroom/2025/10/apple-reports-fourth-quarter-results/">Apple reports fourth quarter results - Apple</a></li>
<li><a href="https://www.apple.com/newsroom/2026/04/tim-cook-to-become-apple-executive-chairman-john-ternus-to-become-apple-ceo/">Tim Cook to become Apple Executive Chairman John Ternus to ...</a></li>
<li><a href="https://finance.yahoo.com/markets/stocks/live/apple-earnings-live-apple-beats-q4-estimates-on-strong-iphone-sales-but-misses-on-china-revenue-221806957.html">Apple earnings live: Apple beats Q4 estimates on strong iPhone sales...</a></li>
<li><a href="https://www.youtube.com/watch?v=s4sZdOCsJGw">INTEL CRASHED 29%: Why Apple &#x27;s Earnings Tonight... - YouTube</a></li>

</ul>
</details>

**标签**: `#Apple earnings`, `#Greater China`, `#memory prices`, `#supply constraints`

---