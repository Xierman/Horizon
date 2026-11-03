---
layout: default
title: "Horizon Summary: 2026-11-03 (EN)"
date: 2026-11-03
lang: en
---

> From 55 items, 13 important content pieces were selected

---

**Technology News**
1. [Telegram alert flags Linux IPv4 TCP use-after-free CVE-2026-98432](#item-tech-news-1) ⭐️ 8.0/10
2. [vLLM v0.33.0rc3 moves to PyTorch 2.14 and CUDA 13.0-only artifacts](#item-tech-news-2) ⭐️ 7.0/10
3. [SGLang v0.5.23 Adds Models and DeepSeek-V4.1 Speedups](#item-tech-news-3) ⭐️ 7.0/10
4. [Astra Reportedly Reads and Edits Qwen Weights to Improve Math](#item-tech-news-4) ⭐️ 7.0/10
5. [OpenAI Details Git Scaling Work and packfile-uri Improvements](#item-tech-news-5) ⭐️ 7.0/10
6. [Ubuntu LTS kernels remain unpatched against critical RCE flaw](#item-tech-news-6) ⭐️ 7.0/10
7. [Abu Dhabi signs four OpenAI deals, including machine-readable government pilot](#item-tech-news-7) ⭐️ 7.0/10
8. [New York Times sues Brave over scraping and AI data sales](#item-tech-news-8) ⭐️ 7.0/10

**Technology Blog**
1. [Weight-Editing LLM Results Are Tricks, Not Superhuman Research](#item-tech-blog-1) ⭐️ 7.0/10
2. [Audience Capture and the Danger of Proxy Metrics](#item-tech-blog-2) ⭐️ 6.0/10

**Financial News**
1. [China Securities Regulator Reportedly Pauses IPOs and Major Shareholder Sales](#item-finance-news-1) ⭐️ 8.0/10
2. [Oracle falls on $20 billion financing; Marvell to buy Lumentum for $115 billion](#item-finance-news-2) ⭐️ 7.0/10
3. [UK proposes 10-year settlement path for most migrants](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Telegram alert flags Linux IPv4 TCP use-after-free CVE-2026-98432](https://telegram.me/zaihuapd/44866) ⭐️ 8.0/10

A Telegram alert claims a high-severity, remotely exploitable use-after-free in the Linux kernel&\#x27;s IPv4 TCP stack, tracked as CVE-2026-98432, that requires neither authentication nor user interaction. The post says Anthropic has published a remote-code-execution example against MPTCP listening ports and that the flaw is not limited to MPTCP. It also cites Go&\#x27;s security team as warning that Linux listen sockets have enabled MPTCP by default since Go 1.24, leaving Go services exposed by default; the alert gives no affected kernel versions, fixed release, or primary advisory, so those details remain unverified.

telegram · zaihuapd · Nov 3, 02:37

**「Background」** The flaw is a race-condition use-after-free in the Linux kernel&\#x27;s IPv4 TCP connection-request path, affecting kernel versions 4.4 and later; AWS says a remote, unauthenticated sender can reach it with crafted IPv4 TCP packets carrying IP options \(tool-1-1, tool-1-2\). The Go-specific exposure comes from a default change in Go 1.24: Linux listen sockets now request MPTCP by default, so Go 1.24+ services can present the MPTCP listener path that the published exploit targets unless MPTCP is disabled at runtime with GODEBUG=multipathtcp=0 or at build time in go.mod \(tool-2-1, tool-2-3\).

**「Impact」** The alert&\#x27;s immediate action is to update the kernel, with priority for internet-facing Linux hosts and Go 1.24+ services that use default MPTCP listen sockets. Because the post names no fixed kernel version or patch, administrators must confirm remediation status with their distribution rather than assume an update is available.

<details><summary>References</summary>
<ul>
<li><a href="https://aws.amazon.com/security/security-bulletins/2026-160-aws/">CVE-2026-98432 - Linux kernel IPv4 TCP use-after-free ...</a></li>
<li><a href="https://access.redhat.com/security/vulnerabilities/RHSB-2026-016">RHSB-2026-016 Use-after-free - kernel IPv4 (CVE-2026-98432 ...</a></li>
<li><a href="https://dev.to/gabrielanhaia/go-124-servers-ask-linux-for-mptcp-the-precondition-for-claudes-root-exploit-41f7">Go 1.24+ Servers Ask Linux for MPTCP: the Precondition for ...</a></li>
<li><a href="https://www.openwall.com/lists/oss-security/2026/10/30/1">oss-security - Fwd: Protecting against CVE-2026-98432 when ...</a></li>

</ul>
</details>

**Tags**: `#Linux kernel security`, `#CVE-2026-98432`, `#TCP/IP`, `#MPTCP`, `#Go security`

---

<a id="item-tech-news-2"></a>
### [vLLM v0.33.0rc3 moves to PyTorch 2.14 and CUDA 13.0-only artifacts](https://github.com/vllm-project/vllm/releases/tag/v0.33.0rc3) ⭐️ 7.0/10

vLLM v0.33.0rc3, a release candidate for LLM serving deployments, includes 927 commits from 389 contributors and upgrades the stack to PyTorch 2.14.0 with torchvision 0.29.0 and Triton 3.8.0. CUDA wheels and images are now CUDA 13.0-only—the CUDA 12.9 wheels and \`-cu129\` images are no longer published—and the CUDA wheel is now ABI-stable with libtorch. The candidate adds support for models including Reflection Beam-1.0, Yandex AliceAI-Foundation-80B-A3B, Recursive Flint, Muse Spark Open, and Step-5 Preview, and makes ROCm 10.0 the default while still publishing ROCm 7.2 as \`-rocm72\`. It also carries breaking changes: Medusa and the MLP speculator are removed, requests made while generation is paused now receive HTTP 503, and the NIXL connector requires NIXL 1.5 or newer.

github · khluu · Nov 2, 10:10

**「Background」** vLLM is an open-source inference and serving engine that batches LLM requests for higher throughput, distributed as Python wheels and Docker images for CUDA, ROCm, CPU, and XPU. Its artifacts are tied to particular PyTorch and accelerator stack versions, so changes such as a CUDA major-version baseline determine which existing environments can run the new release directly.

**「Impact」** Deployments pinned to CUDA 12.9 must move to the CUDA 13.0 artifacts or stay on an older vLLM release, and teams using Medusa or the MLP speculator need a migration plan because those speculative-decoding paths are removed in this candidate.

**Tags**: `#vLLM`, `#LLM inference`, `#PyTorch`, `#CUDA`, `#open source`

---

<a id="item-tech-news-3"></a>
### [SGLang v0.5.23 Adds Models and DeepSeek-V4.1 Speedups](https://github.com/sgl-project/sglang/releases/tag/v0.5.23) ⭐️ 7.0/10

SGLang v0.5.23 is available via \`uv pip install --prerelease=allow sglang==0.5.23\`, with Docker images for NVIDIA CUDA 13, AMD MI35x/MI30x, Intel GPU/CPU, and Google TPU7x. The release spans 1,007 PRs from 257 contributors and adds LLM/VLM support for Muse Spark Open, Beam-1.0, MiniMax-M3.1-Flash, MiniCPM-V 4.7, and Kev, plus diffusion support for Cosmos3-Nano-Sim, FastH3 Omni, FLUX.3 Image Klein, HY-Nomas, and MOSS-Image. The project reports up to 1.5x higher prefill throughput and about 28% lower first-token latency for DeepSeek-V4.1 on GB300 for 32K-64K prompts, and 30%-58% lower time to first token for MoE models including DeepSeek-V4.1-Flash, GLM-5.3-Flash, and gpt-oss on 8K prompts on H200. It also introduces opt-in low-latency NVIDIA megakernel and AMD monokernel plugins, reporting up to 44% faster single-user decode on GB300 and 75% on MI350X, alongside opt-in Paged Experts for MoE models larger than GPU memory.

github · Fridge003 · Nov 2, 22:14

**「Context」** SGLang is an open-source serving and inference framework for LLM, VLM and diffusion workloads, distributed as a versioned pip package alongside per-platform Docker images for CUDA, ROCm \(MI35x/MI30x\), Intel XPU/Xeon and Google TPU. Its releases bundle new model support together with kernel- and scheduler-level work such as speculative decoding, breakable CUDA graphs and hierarchical KV caching, which is why a single version bump can span more than a thousand pull requests.

**「Impact」** For DeepSeek-V4.1 on GB300 or MI350X, the reported decode gains require enabling the opt-in megakernel or monokernel low-latency plugins; similarly, running an MoE model larger than GPU memory on one consumer GPU requires opting into Paged Experts. Operators should validate those non-default paths before changing production configurations.

**Tags**: `#sglang`, `#LLM inference`, `#model support`, `#open source`, `#diffusion models`

---

<a id="item-tech-news-4"></a>
### [Astra Reportedly Reads and Edits Qwen Weights to Improve Math](https://rikiyat.github.io/blog/weight-space-programming/) ⭐️ 7.0/10

A blog post describes Astra, a system that reportedly reads and directly edits neural-network weights, including editing a small Qwen model to improve its math performance. A Hacker News commenter characterizes that math gain as roughly 5x, but the supplied material contains no paper text, peer-reviewed result, or independent replication. The capability and the size of the improvement therefore remain unverified claims rather than a confirmed result.

hackernews · dbreunig · Nov 2, 18:21 · [Discussion](https://news.ycombinator.com/item?id=50341174)

**「Prior work on direct weight editing」** Directly editing or generating a network&\#x27;s parameters — often called weight-space learning — is an established research direction, and commenters familiar with the subfield note that the ability to edit weights and generate new ones for existing models predates this project. The Astra write-up applies that idea with an LLM as the editor: secondary coverage reports that GPT-6 Astra modified about 0.016% of Qwen3.5-0.8B&\#x27;s weights and lifted MATH-500 accuracy from 7.9% to 48.1% in author-run tests, results that have not been independently replicated.

**「Impact」** For developers weighing weight editing against conventional fine-tuning on small models, the claimed Qwen3.5-0.8B gain \(MATH-500 7.9% to 48.1%\) remains a single unreviewed result: the public write-up states there is no peer review or independent replication, and the accompanying Hugging Face weight-edit release lists its independent MATH-500 benchmark section as &quot;TODO.&quot; Teams should therefore reproduce the evaluation on their own tasks and check the published logs before treating direct weight edits as a substitute for training runs.

**「Community Discussion」** A commenter working in weight-space learning argues that the blog and Hacker News submission overstate the results, noting that editing and generating weights and identifying relevant weights are established techniques. Other commenters describe the result as striking but not wholly unprecedented, with one speculating—without supplied evidence—that Astra was trained on neural-weight data as an attempt at recursive self-improvement.

<details><summary>References</summary>
<ul>
<li><a href="https://kingy.ai/blog/weight-space-programming-ai-agent-model-weights/">Weight-Space Programming: GPT-6 Astra Edits Qwen - kingy.ai</a></li>
<li><a href="https://elsolitario.org/en/2026/11/02/mit-csail-astra-edits-0-016-of-qwen3-weights/">Weight-Space Programming: How Astra Edits Weights</a></li>
<li><a href="https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026">GPT-6 Astra Edits Qwen Weights: MATH-500 7.9% to 48.1% ...</a></li>
<li><a href="https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026">GPT-6 Astra Edits Qwen Weights : MATH-500 7.9% to... | explainx.ai</a></li>
<li><a href="https://huggingface.co/JonathanColetti/Qwen3.5-0.8B-Astra-WeightEdit">JonathanColetti/Qwen3.5-0.8B- Astra -WeightEdit · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#weight-space learning`, `#model editing`, `#LLM capabilities`, `#Qwen`, `#research claims`

---

<a id="item-tech-news-5"></a>
### [OpenAI Details Git Scaling Work and packfile-uri Improvements](https://openai.com/index/scaling-git-at-openai/) ⭐️ 7.0/10

OpenAI published an engineering post describing how it scaled Git for very large repositories, including custom tooling and improvements to the Git protocol&\#x27;s \`packfile-uri\` feature. The post describes \`packfile-uri\` as an under-appreciated mechanism that lets a server return links to download additional packs separately, and says OpenAI contributed several improvements to it. It is an internal engineering account rather than a product release; the available material does not establish upstream availability or independent performance results.

hackernews · makeramen · Nov 2, 23:47 · [Discussion](https://news.ycombinator.com/item?id=50345924)

**「Background」** Git&\#x27;s \`packfile-uri\` extension lets a server return links for downloading additional packs separately from the main pack. The post calls it an under-appreciated protocol feature, and a quoted excerpt in the discussion says Pando uses it exclusively and that OpenAI contributed improvements to it.

**「Community discussion」** Commenters framed the post as the fifth recent major engineering article on scaling Git, after pieces from Cursor, GitHub, and Anthropic, and praised it for a detailed, low-hype explanation with numbers, charts, and visualizations. One reader asked for benchmarks such as pushes per second and concurrent pushers, while another highlighted OpenAI&\#x27;s use of and contributions to the existing \`packfile-uri\` protocol as a good example of open-source adaptation.

**Tags**: `#git`, `#developer-infrastructure`, `#version-control`, `#engineering`, `#openai`

---

<a id="item-tech-news-6"></a>
### [Ubuntu LTS kernels remain unpatched against critical RCE flaw](https://freenode.net/article/ubuntu-lts-kernels-still-unfixed-for-critical-cve-2026-98432) ⭐️ 7.0/10

Nearly three weeks after disclosure, Ubuntu still has not released a kernel patch for a critical remote-code-execution flaw in its LTS kernels, according to the report. The item identifies the flaw as CVE-2026-98432 but provides no affected kernel versions, patch schedule, official explanation, or technical detail, so the scope and exploitability remain unconfirmed here. Commenters describe an iptables/nftables u32 filter as a temporary workaround and cite a RHEL mitigation page, but those are community claims rather than a vendor-confirmed fix.

hackernews · majorchord · Nov 2, 18:39 · [Discussion](https://news.ycombinator.com/item?id=50341462)

**「What the flaw is and where the fix stands」** CVE-2026-98432 is a remote use-after-free in how the Linux kernel sets up IPv4 TCP connections, present in kernel versions 4.4 and later and rated a CVSS 3.1 base score of 9.8, according to Ubuntu&\#x27;s own write-up and Akamai&\#x27;s analysis. Ubuntu&\#x27;s CVE tracker entry is dated Oct 15, 2026, and the fixes so far sit only in the -proposed pocket — the staging area for packages still being tested — for Ubuntu 22.04 LTS and other releases, not in stable updates.

**「Mitigation gap for Ubuntu LTS operators」** Ubuntu LTS operators have neither a vendor kernel patch nor Ubuntu-published mitigation, unlike RHEL and AlmaLinux users who already have fixes for the CVSS 9.8 use-after-free in the IPv4 TCP handshake that was fixed upstream on Oct 15, so any internet-facing TCP service on an unpatched Ubuntu kernel stays exposed until Canonical ships an update. The practical interim step is self-applied filtering: Red Hat&\#x27;s advisory for the same CVE includes an nftables rule that drops TCP packets carrying IPv4 header options, and a community script automates assessing, applying and verifying such a rule — measures that narrow exposure but do not substitute for a patched kernel.

**「Community discussion」** Commenters criticized Ubuntu for not explaining the delay or publishing mitigation instructions, contrasting that with a RHEL mitigation page cited by one poster. Another commenter proposed a raw PREROUTING u32 drop rule as a pre-patch workaround, while a separate thread raised concern that consumer routers running Linux rarely receive kernel security updates.

<details><summary>References</summary>
<ul>
<li><a href="https://ubuntu.com/security/CVE-2026-98432">CVE-2026-98432 | Ubuntu</a></li>
<li><a href="https://ubuntu.com/blog/fixes-available-in-proposed-pocket-for-cve-2026-98432">Fixes available in -proposed pocket for CVE-2026-98432 - Ubuntu</a></li>
<li><a href="https://www.akamai.com/blog/security-research/cve-2026-98432-remote-uaf-linux-kernels-tcp-stack">CVE-2026-98432: A Remote Use-After-Free in the Linux Kernel&#x27;s ...</a></li>
<li><a href="https://github.com/soroushneshati/cve-2026-98432-ubuntu-mitigation">GitHub - soroushneshati/ cve - 2026 - 98432 - ubuntu - mitigation : Check...</a></li>
<li><a href="https://atlasum.net/blog/cve-2026-98432-linux-ipv4-tcp-uaf">Linux&#x27;s October 2026 TCP Use-After-Free: CVE - 2026 - 98432 — Atlas</a></li>
<li><a href="https://access.redhat.com/security/vulnerabilities/RHSB-2026-016">RHSB - 2026 -016 Use-after-free - kernel IPv4 ( CVE - 2026 - 98432 )</a></li>

</ul>
</details>

**Tags**: `#linux-kernel`, `#security-vulnerability`, `#ubuntu`, `#cve`, `#patching`

---

<a id="item-tech-news-7"></a>
### [Abu Dhabi signs four OpenAI deals, including machine-readable government pilot](https://thenextweb.com/news/openai-abu-dhabi-deals-machine-readable-government-mubadala) ⭐️ 7.0/10

Abu Dhabi signed four agreements with OpenAI, including a &quot;machine-readable government&quot; pilot that converts policies and regulations into an AI-readable format to help officials check permit and license applications. The pilot has been tested on food imports, with officials retaining final decision-making authority. Mubadala is collaborating with OpenAI and G42&\#x27;s Inception42 on investment analysis, while Inception42 separately signed a five-year agreement to provide models to the UAE government, enterprises, and schools. ADNOC became the first energy company to use OpenAI&\#x27;s Frontier platform.

telegram · zaihuapd · Nov 2, 15:55

**「Background」** OpenAI Frontier, the platform ADNOC is adopting, is described as a system for building and coordinating AI agents across large organizations, and the ADNOC agreement is a multi-year deal signed with both OpenAI and G42 rather than OpenAI alone. That makes the energy announcement one piece of a wider Abu Dhabi–OpenAI–G42 arrangement that also covers investment analysis and model provisioning to government, enterprises, and schools.

**「What it means」** Abu Dhabi agencies adopting the machine-readable government pilot will need to maintain regulations and permit criteria in a structured, AI-readable form, since officials will use that format to check applications such as food-import licenses while retaining final approval authority.

<details><summary>References</summary>
<ul>
<li><a href="https://www.thenationalnews.com/business/energy/2026/11/02/adnoc-signs-agreement-with-openai-and-g42-to-deploy-frontier-ai/">Adnoc becomes first energy company to deploy OpenAI Frontier</a></li>
<li><a href="https://www.analyticsinsight.ae/news/openai-enters-oil-and-gas-adnoc-signs-landmark-ai-pact-with-g42">OpenAI Enters Oil and Gas: ADNOC Signs Landmark AI Pact with G42</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#government AI`, `#AI governance`, `#UAE`, `#machine-readable policy`

---

<a id="item-tech-news-8"></a>
### [New York Times sues Brave over scraping and AI data sales](https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/) ⭐️ 7.0/10

The New York Times sued Brave on Monday, alleging that the privacy browser scraped copyrighted publisher content, bypassed paywalls, and sold access to AI companies including Anthropic, Perplexity, Mistral, xAI, and Cohere. According to TechCrunch, the suit says Brave used an undisclosed crawler to build an index of more than 30 billion web pages and blocked publishers&\#x27; ads. The Times is seeking an injunction and damages; Brave had not responded at the time of the report. The New York Daily News, Chicago Tribune, and other outlets filed similar suits the same day in Manhattan federal court.

telegram · zaihuapd · Nov 3, 06:50

**「Background」** Brave is a privacy-oriented browser, and the dispute turns on how its crawler and index handle publisher content. The complaint also challenges features that allegedly bypass paywalls and block publisher ads, practices that directly affect how news sites fund their work.

**「Impact」** For publishers, the case tests whether an index built by an undisclosed crawler and resold to AI developers can be treated as infringing rather than ordinary search indexing. If granted, the requested injunction could restrict Brave&\#x27;s ability to crawl and supply that data.

**Tags**: `#AI copyright`, `#web scraping`, `#Brave browser`, `#publishing industry`, `#lawsuits`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [Weight-Editing LLM Results Are Tricks, Not Superhuman Research](https://seangoedecke.com/llms-are-not-superhuman-at-reading-and-writing-neural-network-weights/) ⭐️ 7.0/10

rss · Sean Goedecke · Nov 3, 00:00

**「Background」** A recent paper reports that a frontier model can inspect and directly edit neural-network weights—including improving a 0.8B Qwen model’s mathematics performance—and presents this as superhuman, with possible implications for recursive self-improvement.

**「Solution」** Sean Goedecke argues that the demonstrations reduce to established interpretability and ablation techniques that a competent human ML researcher could apply. In the toy-game example, the network’s 8×8 input channels are labeled by role, so taking an L2 norm across the first layer’s 32 weights produces a heatmap showing where the player and moving objects are; a human can identify games such as Breakout or Pac-Man from that map. Astra’s feat is therefore impressive mental arithmetic, not superhuman research. The Qwen case, he argues, is also narrower than it sounds: the model was not broadly bad at math but fell into loops after 32k tokens. The author would have compared looping and non-looping residuals, measured which weights contributed, trimmed them, and tested—the abliteration playbook. Astra reportedly did essentially this, using four pairs of texts and Python to find a patch. Goedecke compares the capability to LLMs patching compiled binaries: clever, but inferior to editing source and recompiling; for models, normal training remains the better way to change weights.

**「Takeaway」** The author’s conclusion is that these results demonstrate impressive mechanical manipulation inside known workflows, not a new superhuman route to AI self-improvement; LLMs will most plausibly aid research by improving training rather than by directly tweaking weights.

**Tags**: `#LLM interpretability`, `#neural network weights`, `#model editing`, `#critical analysis`, `#AI research claims`

---

<a id="item-tech-blog-2"></a>
### [Audience Capture and the Danger of Proxy Metrics](https://seangoedecke.com/audience-capture/) ⭐️ 6.0/10

rss · Sean Goedecke · Nov 3, 00:00

**「Background」** Sean Goedecke worries that the metric-chasing instinct that serves engineers can corrupt online writing: engagement is easy to measure, but it is not the thing he actually wants.

**「Solution」** Goedecke notes that online writing is built to push engagement up: link aggregators amplify engagement-friendly posts, comments are sorted by upvotes, and platforms often pay for attention. The danger is that clickers—people who click, scan, and leave—and readers who actually consider ideas are indistinguishable in the metrics, so optimizing the proxy can replace the audience he wants with a fake one; a hot microservices post might raise views while driving thoughtful readers away. Goedecke extends this to engineering careers, distinguishing proxy games such as Jira metrics or promotion from real games such as respected technical work, and warns that selling out is sometimes reasonable but doing it by habit is worst. He says some of his favorite posts got little attention, while popular industry laments succeeded because they gave people an outlet, and he writes for the 5% who think, discuss, and email him.

**「Takeaway」** The larger point is that metrics are useful only as proxies, and the real goal is to know which game you are playing and avoid sacrificing the work and audience you value for numbers that do not measure them. That requires taste and thin direct feedback rather than raw view counts.

**Tags**: `#audience capture`, `#proxy metrics`, `#engineering career`, `#online writing`, `#engagement metrics`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China Securities Regulator Reportedly Pauses IPOs and Major Shareholder Sales](https://www.ft.com/content/fec5981d-0c31-4f21-9a37-a1dd1526f530) ⭐️ 8.0/10

China’s securities regulator has reportedly told brokers to pause initial public offerings and large shareholder stock sales until the market recovers, as the CSI 300 fell 8.5% in October and about 14% year to date.

telegram · zaihuapd · Nov 3, 08:01

**「Background」** &quot;Window guidance&quot; means regulators informally direct brokers to act rather than issuing a formal rule. The CSI 300 had already fallen 20% from its June peak by 22 October, entering bear-market territory, after earlier stabilization steps that included state &quot;national team&quot; buying and restrictions on share sales.

**「Impact」** The reported guidance would delay companies planning listings and prevent major shareholders from selling large stakes, affecting IPO candidates such as Yangtze Memory Technologies, which the report said the market had expected to pursue a listing.

<details><summary>References</summary>
<ul>
<li><a href="https://www.citynewsservice.cn/articles/china-biz-buzz/daily-buzz/daily-buzz-23-october-2026-3n70vxlm">Daily Buzz: 23 October 2026 - City News Service</a></li>

</ul>
</details>

**Tags**: `#China stocks`, `#IPO suspension`, `#shareholder selling`, `#CSRC`, `#market intervention`

---

<a id="item-finance-news-2"></a>
### [Oracle falls on $20 billion financing; Marvell to buy Lumentum for $115 billion](https://www.cnbc.com/2026/11/02/stocks-making-the-biggest-moves-midday-orcl-spcx-tem-rivn.html) ⭐️ 7.0/10

Oracle shares fell another 6% after the company filed plans to sell $10 billion in common stock and $10 billion in senior notes to fund its artificial intelligence buildout. Marvell shares fell 9% and Lumentum fell 15% after Marvell agreed to buy Lumentum in a $115 billion all-stock deal.

rss · CNBC Finance · Nov 2, 20:00

**「Background」** Oracle’s AI data-center buildout has raised concerns about capital availability, making the company’s funding plans a focus for investors.

**「Impact」** Oracle&\#x27;s $10 billion stock sale would reduce existing shareholders&\#x27; ownership stakes, while the $10 billion in senior notes adds debt.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/01/stock-market-today-live-updates.html">Stock market news for Nov . 2, 2026</a></li>

</ul>
</details>

**Tags**: `#market movers`, `#earnings`, `#M&amp;A`, `#AI infrastructure`, `#equities`

---

<a id="item-finance-news-3"></a>
### [UK proposes 10-year settlement path for most migrants](https://www.gov.uk/government/news/home-secretary-unveils-new-rules-for-migrants-settling-in-the-uk) ⭐️ 7.0/10

The UK government has proposed &quot;earned settlement&quot; rules extending most migrants&\#x27; standard path to permanent residence from five to 10 years. The highest earners could apply after three years, while people earning over £50,271 or in public-service roles such as doctors, nurses and teachers would use a five-year route.

telegram · zaihuapd · Nov 2, 23:50

**「Background」** Under existing rules, most migrants on work visas can apply for permanent residence, known as settlement, after five years of continuous residence; the proposed “earned settlement” system would double that standard wait to 10 years for most applicants while keeping a five-year route for certain high earners and public-service workers.

**「Impact」** Employers that sponsor overseas workers would need to plan around a longer path to settlement for most staff, affecting retention and workforce planning, while high earners and certain public-service workers would keep faster routes.

<details><summary>References</summary>
<ul>
<li><a href="https://www.visaverge.com/news/indians-dismayed-as-uk-settled-status-proposals-extend-wait-times/">Indians Dismayed as UK Settled Status Proposals Extend Wait Times</a></li>
<li><a href="https://chambers.com/articles/10-year-settlement-uk-what-employers-need-to-plan-immediately-in-2026">10-Year Settlement UK: What Employers Need to Plan ...</a></li>

</ul>
</details>

**Tags**: `#UK immigration policy`, `#settlement rules`, `#labour market`, `#public services`, `#policy proposal`

---