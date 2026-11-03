---
layout: default
title: "Horizon Summary: 2026-11-03 (EN)"
date: 2026-11-03
lang: en
---

> From 55 items, 18 important content pieces were selected

---

**Technology News**
1. [Ubuntu LTS kernels remain unpatched for critical Linux RCE CVE-2026-98432](#item-tech-news-1) ⭐️ 8.0/10
2. [vLLM v0.33.0rc3 moves to PyTorch 2.14 and CUDA 13.0-only builds](#item-tech-news-2) ⭐️ 7.0/10
3. [SGLang v0.5.23 Adds Model Support and Opt-In Speedups](#item-tech-news-3) ⭐️ 7.0/10
4. [Astra claimed to read and edit Qwen weights amid disputed results](#item-tech-news-4) ⭐️ 7.0/10
5. [Subvocal opens preorders for RF silent-speech smart glasses](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenAI Details Scaling Git for Very Large Repositories](#item-tech-news-6) ⭐️ 7.0/10
7. [Terry Tao Explores &\#x27;Egoless Mathematics&\#x27; in the AI Era](#item-tech-news-7) ⭐️ 7.0/10
8. [OSINT Technique Uses Aircraft Noise and ADS-B to Geolocate Video](#item-tech-news-8) ⭐️ 7.0/10
9. [Abu Dhabi Signs Four OpenAI Agreements, Including Machine-Readable Government](#item-tech-news-9) ⭐️ 7.0/10
10. [Report: DeepSeek V5 may train on Huawei Ascend chips](#item-tech-news-10) ⭐️ 7.0/10
11. [New York Times sues Brave over alleged scraping for AI resale](#item-tech-news-11) ⭐️ 7.0/10

**Technology Blog**
1. [LLM Weight Editing Is a Trick, Not Superhuman Research](#item-tech-blog-1) ⭐️ 7.0/10
2. [Audience Capture: When Engagement Metrics Replace Real Readers](#item-tech-blog-2) ⭐️ 6.0/10

**Financial News**
1. [China regulator reportedly pauses IPOs and big shareholder sales to steady slumping stock market](#item-finance-news-1) ⭐️ 9.0/10
2. [Blackstone president calls for more equity financing in AI buildout](#item-finance-news-2) ⭐️ 7.0/10
3. [Estée Lauder tops estimates and raises outlook; Marvell to buy Lumentum for $115 billion](#item-finance-news-3) ⭐️ 7.0/10
4. [UK proposes 10-year settlement wait for most migrants](#item-finance-news-4) ⭐️ 7.0/10
5. [Apple posts record September-quarter revenue, warns memory costs are squeezing margins](#item-finance-news-5) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Ubuntu LTS kernels remain unpatched for critical Linux RCE CVE-2026-98432](https://freenode.net/article/ubuntu-lts-kernels-still-unfixed-for-critical-cve-2026-98432) ⭐️ 8.0/10

The report says Ubuntu LTS kernels remain unpatched for the critical Linux IPv4 TCP use-after-free CVE-2026-98432 nearly three weeks after disclosure. The flaw is remotely exploitable without authentication or user interaction, and Anthropic has published an RCE example targeting an MPTCP listening port. Go&\#x27;s security team says Linux listen sockets have enabled MPTCP by default since Go 1.24, putting Go services on exposed hosts at risk by default; the issue is not limited to MPTCP configurations.

hackernews · majorchord · Nov 2, 18:39 · [Discussion](https://news.ycombinator.com/item?id=50341462)

**「Background」** CVE-2026-98432 is a high-severity use-after-free in the Linux kernel&\#x27;s IPv4 TCP handling that can be triggered from the network without authentication or user interaction. The exposure extends beyond MPTCP: Go&\#x27;s security team says Linux listen sockets have enabled MPTCP by default since Go 1.24, so Go services are exposed by default, and similar attacks may work even without an MPTCP listener.

**「Exposure and action」** Ubuntu LTS operators with internet-facing TCP services remain exposed until a fixed kernel is available: Ubuntu&\#x27;s CVE tracker lists CVE-2026-98432 as an IPv4 TCP use-after-free, and AWS says the affected path covers kernel versions 4.4 and later under specific IP-option conditions. Check the running kernel against Ubuntu&\#x27;s advisory and use \`ss -M\` to identify MPTCP listeners, because Go 1.24+ enables MPTCP by default for Linux listen sockets, so Go services may need review even when MPTCP was not configured explicitly.

**「Community discussion」** Commenters focused on workarounds and accountability: one proposed an iptables/nftables raw PREROUTING u32 drop rule as a pre-patch mitigation, while others asked why Ubuntu has not explained the delay and criticized the absence of Ubuntu mitigation instructions; another noted RHEL offers a mitigation that it says only reduces exposure. A separate commenter raised concern about consumer routers running Linux kernels that never receive security updates, arguing LLMs are lowering the barrier to exploiting known bugs.

<details><summary>References</summary>
<ul>
<li><a href="https://ubuntu.com/security/CVE-2026-98432">CVE-2026-98432 | Ubuntu</a></li>
<li><a href="https://aws.amazon.com/security/security-bulletins/2026-160-aws/">CVE-2026-98432 - Linux kernel IPv4 TCP use-after-free ...</a></li>
<li><a href="https://computingforgeeks.com/linux-kernel-cve-2026-98432/">CVE-2026-98432: Check and Patch the Linux Kernel TCP Flaw</a></li>

</ul>
</details>

**Tags**: `#linux`, `#ubuntu`, `#kernel`, `#security vulnerability`, `#open source`

---

<a id="item-tech-news-2"></a>
### [vLLM v0.33.0rc3 moves to PyTorch 2.14 and CUDA 13.0-only builds](https://github.com/vllm-project/vllm/releases/tag/v0.33.0rc3) ⭐️ 7.0/10

vLLM published v0.33.0rc3, a release-candidate changelog covering 927 commits from 389 contributors. The release upgrades to PyTorch 2.14.0 with torchvision 0.29.0 and Triton 3.8.0, drops CUDA 12.9 so release wheels and images are CUDA 13.0-only, and adds a CUDA wheel that is ABI-stable with libtorch. It also adds day-0 support for Reflection Beam-1.0 and other models, an AWS EFA image for KV transfer, speculative-decoding changes, and ROCm 10.0 as the default while publishing ROCm 7.2 as \`-rocm72\`.

github · khluu · Nov 2, 10:10

**「Background」** vLLM is an open-source LLM inference and serving engine distributed as versioned Python wheels and Docker images for CUDA, ROCm, CPU, and XPU. Its CUDA artifacts bundle a specific PyTorch and CUDA stack, so upgrading PyTorch and dropping CUDA 12.9 changes which prebuilt runtime users can install.

**「Impact」** Users running CUDA 12.9 deployments must move to the CUDA 13.0 wheels or images because the \`-cu129\` artifacts are no longer published. Upgraders also need to remove Medusa and MLP-speculator configurations and the legacy Ray compiled-graph executor, and ensure any NIXL connector installation is version 1.5 or newer.

**Tags**: `#vllm`, `#llm-inference`, `#pytorch`, `#cuda`, `#open-source`

---

<a id="item-tech-news-3"></a>
### [SGLang v0.5.23 Adds Model Support and Opt-In Speedups](https://github.com/sgl-project/sglang/releases/tag/v0.5.23) ⭐️ 7.0/10

SGLang v0.5.23, a community release with 1,007 pull requests from 257 contributors, adds support for new language, vision-language, and diffusion models including Muse Spark Open, MiniMax-M3.1-Flash, MiniCPM-V 4.7, FLUX.3 Image Klein, and MOSS-Image. The release notes claim DeepSeek-V4.1 on GB300 reaches up to 1.5x more prefill throughput under load and about 28% lower first-token latency on 32K–64K prompts, while opt-in low-latency NVIDIA megakernel and AMD monokernel plugins target DeepSeek-V4.1-Flash decode with up to 44% faster single-user decode on GB300 and 75% on MI350X. It also adds opt-in Paged Experts for serving MoE models larger than GPU memory on one consumer GPU, opt-in LoRA serving on FP8 and NVFP4 quantized MoE models, and TPU7x support through the separate SGLang-TorchTPU plugin. Installation uses \`uv pip install --prerelease=allow sglang==0.5.23\`, with Docker images for NVIDIA CUDA 13, AMD MI35x/MI30x, Intel GPU/CPU, and a TPU7x image tagged \`v0.1.0-tpu\`.

github · Fridge003 · Nov 2, 22:14

**「Background」** SGLang is an open-source serving framework for LLMs, vision-language models, and diffusion models, with release notes organized by model support and backend subsystems such as speculative decoding and CUDA graphs. The v0.5.23 package is distributed via PyPI and platform-specific Docker images for NVIDIA CUDA 13, AMD MI35x/MI30x, Intel GPU/CPU, and Google TPU7x.

**「Impact」** Teams upgrading need to account for the prerelease install flag and platform-specific Docker tags; the Google TPU7x path uses the separate \`lmsysorg/sglang:v0.1.0-tpu\` image rather than the \`v0.5.23\` tags used for NVIDIA, AMD, and Intel platforms.

**Tags**: `#SGLang`, `#LLM inference`, `#open-source release`, `#model support`, `#AI infrastructure`

---

<a id="item-tech-news-4"></a>
### [Astra claimed to read and edit Qwen weights amid disputed results](https://rikiyat.github.io/blog/weight-space-programming/) ⭐️ 7.0/10

A blog post and its Hacker News thread describe Astra, a system claimed to inspect and directly edit the weights of a small Qwen model to improve its performance. The supplied material gives no model version, code release, evaluation protocol, or independent measurement, so the reported gains remain an author claim rather than a verified capability. One commenter who says their research is in weight-space learning argues that the blog and discussion overstate the results, noting that editing, generating, and identifying weights are already established techniques.

hackernews · dbreunig · Nov 2, 18:21 · [Discussion](https://news.ycombinator.com/item?id=50341174)

**「What weight-space programming means」** The post frames Astra within weight-space programming: rather than only optimizing prompts and the text programs around them, an LLM is asked to inspect and edit another model’s weights directly. The reported target is Qwen 3.5-0.8B, and an edited artifact has been published as Qwen3.5-0.8B-Astra-WeightEdit.

**「Impact」** On the supplied evidence, developers cannot reproduce or benchmark Astra; teams evaluating model-editing methods should wait for code, model-version details, and an evaluation protocol before relying on the claimed gains.

**「Community discussion」** Commenters are divided between astonishment at Astra’s claimed ability to determine training data and edit weights without tooling, and skepticism about whether the capability is new. yurimo, who says their research is in weight-space learning, argues that the blog and discussion overstate the results because weight editing, generation, and identification are established; vanyle speculates Astra was trained on neural-weight data, while xg15 frames the behavior as LLMs rapidly grasping complex systems.

<details><summary>References</summary>
<ul>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight - Space Programming : LLMs can natively read...</a></li>
<li><a href="https://huggingface.co/JonathanColetti/Qwen3.5-0.8B-Astra-WeightEdit">JonathanColetti/ Qwen 3.5-0.8B- Astra -WeightEdit · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#weight-space learning`, `#LLM interpretability`, `#model editing`, `#Qwen`, `#AI research`

---

<a id="item-tech-news-5"></a>
### [Subvocal opens preorders for RF silent-speech smart glasses](https://news.ycombinator.com/item?id=50340088) ⭐️ 7.0/10

Subvocal, a YC F26 startup, has opened preorders for a first batch of 500 units of smart glasses that it says decode silently mouthed words into text using RF sensing, with shipments planned for Q1 2027 and a $200 discount off the final price. The glasses emit Bluetooth-like radio waves through the face and use foundation models trained on the resulting tongue, lip, and soft-palate perturbations; the company says the system works with lips closed and that a demo subject needed only a 20-sentence calibration. The hardware is still a prototype, and the accuracy, latency, and cross-user performance claims come from the company and its demo rather than independent testing.

hackernews · aarushyadav · Nov 2, 17:16

**「Earlier silent-speech work」** Subvocal&\#x27;s founders began from MIT Media Lab&\#x27;s AlterEgo, an earlier silent-speech system that used facial EMG electrodes to read muscle activity. They first tried to recreate that setup in a 36-hour hackathon prototype, then abandoned EMG because of sweat, electrical interference, placement variability, and the need to attach electrodes to the face.

**「Impact」** For buyers, a discounted preorder reserves a device whose core input accuracy has not yet been independently established; the source reports only a company demo and a short calibration, so anyone considering silent dictation for work or accessibility should treat Q1 2027 and the performance claims as targets rather than shipped guarantees.

**「Community discussion」** Commenters were divided on whether silent mouthing can produce reliable words—one doubted that “apple” is distinguishable with the mouth closed—while others welcomed the accessibility and hands-free potential. A preorder customer asked Subvocal to keep adjustable nose pads and clarify whether signal processing runs on the glasses or an app, and another commenter raised offline inference and privacy concerns.

**Tags**: `#subvocalization`, `#silent speech`, `#smart glasses`, `#human-computer interaction`, `#accessibility`

---

<a id="item-tech-news-6"></a>
### [OpenAI Details Scaling Git for Very Large Repositories](https://openai.com/index/scaling-git-at-openai/) ⭐️ 7.0/10

OpenAI&\#x27;s engineering blog describes how the company scaled Git for its own very large repositories, using Git&\#x27;s packfile-uri protocol feature and contributing improvements upstream. The post is a vendor engineering account, not an independently benchmarked product release. Commenters add that OpenAI&\#x27;s Pando system relies on packfile-uri and that OpenAI contributed changes to the feature.

hackernews · makeramen · Nov 2, 23:47 · [Discussion](https://news.ycombinator.com/item?id=50345924)

**「Background」** OpenAI&\#x27;s Pando is a Git-compatible backend built for the scale of its monorepo, where quarterly commits rose 2,442% between Q1 2024 and Q4 2026; OpenAI says it built the system in 10 weeks. The design relies on Git&\#x27;s \`packfile-uri\` protocol feature, which lets a server return links to additional packs that clients download separately instead of sending one monolithic packfile response.

**「Impact」** For teams running very large monorepos, OpenAI&\#x27;s write-up offers a concrete pattern—using packfile-uri to serve additional pack downloads separately—and its upstream Git contributions may make that pattern available to other server implementations.

**「Community Discussion」** Commenters welcomed the detailed, low-hype engineering write-up, with one counting it as the fifth recent major post on Git scaling alongside Cursor, GitHub, and Anthropic, and another praising the reuse of packfile-uri. A dissenting comment asked for throughput and concurrency benchmarks, such as pushes per second, which the post does not appear to provide.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/scaling-git-at-openai/">Scaling Git at OpenAI | OpenAI</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/openai-pando-git-backend-code-commit-surge">OpenAI builds custom Git backend in 10 weeks after 2,442% commit...</a></li>
<li><a href="https://git-scm.com/docs/packfile-uri">Git - packfile - uri Documentation</a></li>

</ul>
</details>

**Tags**: `#git`, `#monorepo`, `#developer-tooling`, `#version-control`, `#engineering-infrastructure`

---

<a id="item-tech-news-7"></a>
### [Terry Tao Explores &\#x27;Egoless Mathematics&\#x27; in the AI Era](https://terrytao.wordpress.com/2026/11/02/egoless-mathematics-in-the-ai-era/) ⭐️ 7.0/10

Terry Tao published a blog essay, “Egoless Mathematics in the AI Era,” on November 2, 2026, examining how AI could affect mathematical practice and the profession. The essay is commentary rather than a report of a new technical result, and it focuses on questions of meaning, motivation, and value in mathematics. Its appearance drew discussion on Hacker News about whether mathematics can be separated from the people who practice it.

hackernews · smilelamp · Nov 2, 18:54 · [Discussion](https://news.ycombinator.com/item?id=50341736)

**「Context of the essay」** The essay appeared as a guest post on Terence Tao&\#x27;s blog, credited to Amit Sahai, Jie Xue, and Karthik C. S., rather than as Tao&\#x27;s own writing. It is a philosophical argument about how mathematical work should be valued—shifting emphasis from individual discoverers toward mathematical truth itself—and offers no new AI benchmark, experimental finding, or institutional policy.

**「Community discussion」** Commenters disputed whether mathematics can be separated from human mathematicians: kzz102 argued that human pursuits are shaped by what people can understand and by the opinions they value, while GMoromisato said an “egoless” framing overlooks the overlap between what mathematicians like, what they are good at, and what they can be paid to do. j2kun read the essay as implying that people do not matter and that only truth does.

<details><summary>References</summary>
<ul>
<li><a href="https://terrytao.wordpress.com/2026/11/02/egoless-mathematics-in-the-ai-era/">Egoless Mathematics in the AI Era | What&#x27;s new</a></li>
<li><a href="https://www.zeniteq.com/terence-tao-s-blog-hosts-a-call-for-egoless-mathematics-sxv5mh">Terence Tao’s Blog Hosts a Call for Egoless Mathematics</a></li>

</ul>
</details>

**Tags**: `#AI and mathematics`, `#research culture`, `#future of work`, `#expert commentary`

---

<a id="item-tech-news-8"></a>
### [OSINT Technique Uses Aircraft Noise and ADS-B to Geolocate Video](https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/) ⭐️ 7.0/10

Simon Willison highlighted a YouTube demonstration by Colsto that uses almost imperceptible aircraft noise in a video soundtrack to determine where the video was recorded. The method derives Doppler curves from the plane sounds and cross-references them against ADS-B flight data, using aircraft speed, distance, and the gaps between different flights to locate the recording. The source is a short link summary rather than a technical write-up, so the method&\#x27;s accuracy and limits are not independently detailed.

rss · Simon Willison · Nov 3, 05:32

**「How the technique works」** The method relies on ADS-B, the flight-tracking data that records aircraft positions and velocities, and on the Doppler effect: as a plane passes, its engine noise shifts slightly in pitch. By modelling the Doppler curve each candidate flight path would produce and comparing it with the faint aircraft sounds in a recording, an analyst can narrow down where the video was made.

**「Impact」** For anyone publishing video with background audio, the demonstration shows that faint aircraft sounds can act as a location side channel; removing or altering that audio is the apparent mitigation if the recording location is sensitive.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=UytYrhYLOKI">I discovered a sound that leaks your exact location ... - YouTube</a></li>

</ul>
</details>

**Tags**: `#OSINT`, `#privacy`, `#signal-processing`, `#ADS-B`, `#geolocation`

---

<a id="item-tech-news-9"></a>
### [Abu Dhabi Signs Four OpenAI Agreements, Including Machine-Readable Government](https://thenextweb.com/news/openai-abu-dhabi-deals-machine-readable-government-mubadala) ⭐️ 7.0/10

Abu Dhabi signed four agreements with OpenAI on Monday, including a “machine-readable government” initiative that would convert policies and regulations into AI-readable formats to help officials check licensing and certification applications. The effort has been piloted on food imports, with officials retaining final decision authority. Separately, Mubadala is working with OpenAI and G42’s Inception42 on investment analysis; Inception42 also signed a five-year agreement to provide models to UAE government, enterprise and school users, while ADNOC became the first energy company to use OpenAI’s Frontier platform.

telegram · zaihuapd · Nov 2, 15:55

**「Background」** “Machine-readable government” means publishing laws, regulations and administrative rules in structured, computer-parsable formats rather than only prose or PDF documents, so software can search, compare and apply them. That requires legal text to be translated into maintained data schemas, with human officials still responsible for final decisions.

**「Sovereign hosting condition」** ADNOC’s multi-year deployment of OpenAI Frontier is to run through G42 subsidiary Inception42 on sovereign AI infrastructure inside the UAE, making in-country hosting part of the first energy-sector rollout.

<details><summary>References</summary>
<ul>
<li><a href="https://tech-insider.org/adnoc-g42-openai-frontier-first-energy-company-uae-2026/">ADNOC x OpenAI: 1st Energy Firm in Frontier Program [2026]</a></li>
<li><a href="https://explainx.ai/blog/adnoc-openai-frontier-g42-first-energy-company-adipec-2026">ADNOC OpenAI Frontier Deal: First Energy Rollout Explained ...</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#government AI`, `#AI governance`, `#sovereign AI`, `#UAE`

---

<a id="item-tech-news-10"></a>
### [Report: DeepSeek V5 may train on Huawei Ascend chips](https://www.eet-china.com/mp/a536460.html) ⭐️ 7.0/10

An unverified supply-chain report claims DeepSeek plans to train its next-generation V5 model on Huawei Ascend chips, shifting from Ascend&\#x27;s prior use for inference. The report provides no technical details, timeline, or confirmation from DeepSeek or Huawei. It follows DeepSeek&\#x27;s late-September open-sourcing of Ascend-oriented infrastructure components—compiler tools, compute libraries, and a distributed communication library—each corresponding to earlier Nvidia-platform releases.

telegram · zaihuapd · Nov 3, 06:20

**「Prior context」** Huawei&\#x27;s Ascend line is its domestic AI accelerator family, and the report notes that Ascend chips had until now been used mainly for running DeepSeek models \(inference\) rather than for training them. According to the same account, DeepSeek open-sourced Ascend-oriented infrastructure components in late September — including a compiler toolchain, compute libraries and a distributed communication library — released as one-to-one counterparts to the components it had previously open-sourced for Nvidia platforms. Those earlier releases are what make a reported training shift technically conceivable, though the V5 claim itself remains an unverified supply-chain report with no published details on scale, chip models or timelines.

**「Toolchain shift for DeepSeek deployers」** The practical consequence lands on teams deploying DeepSeek models: the Ascend-targeted compiler, compute, and distributed-communication libraries open-sourced in late September give them a first-party, non-CUDA path, and a V5 trained on Ascend would extend that support from inference into training. Until DeepSeek confirms the plan, Ascend is best treated as a supported deployment target rather than a validated training platform — external reports describe V4 as dual-running on Ascend and NVIDIA, not as trained on Ascend.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ai-insight.org/reports/deepseek-v4-2026">DeepSeek V 4 — 1.6T 参数 MoE 全开源 · 华 为 昇 腾 SuperNode...</a></li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#Huawei Ascend`, `#AI training hardware`, `#open-source ML infrastructure`, `#unverified report`

---

<a id="item-tech-news-11"></a>
### [New York Times sues Brave over alleged scraping for AI resale](https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/) ⭐️ 7.0/10

The New York Times and other outlets sued Brave in Manhattan federal court on Monday, alleging the privacy browser scraped copyrighted content, bypassed paywalls, blocked publisher ads, and sold the material to AI companies including Anthropic, Perplexity, Mistral, xAI and Cohere. The complaint says Brave used undisclosed crawlers to build an index of more than 30 billion web pages, and it seeks an injunction and damages; Brave had not responded at the time of the report.

telegram · zaihuapd · Nov 3, 06:50

**「Background」** The complaint centers on a web index that Brave allegedly built with an undisclosed crawler; such an index is the infrastructure that search and AI data products rely on. Publishers generally fund content through subscriptions and advertising, so alleged paywall bypass and ad blocking are part of the claimed economic harm alongside scraping and resale.

**「Impact」** For publishers, the case provides a concrete legal test of whether browser-level crawling and paywall circumvention can be treated as copyright infringement; for Brave, the immediate risk is an injunction against the indexing and data-licensing practices named in the complaint.

**Tags**: `#AI copyright`, `#web scraping`, `#Brave browser`, `#publisher lawsuits`, `#AI training data`

---

## Technology Blog

<a id="item-tech-blog-1"></a>
### [LLM Weight Editing Is a Trick, Not Superhuman Research](https://seangoedecke.com/llms-are-not-superhuman-at-reading-and-writing-neural-network-weights/) ⭐️ 7.0/10

rss · Sean Goedecke · Nov 3, 00:00

**「Background」** A recent paper claims that GPT-6 Astra can inspect and directly edit neural-network weights, including improving a 0.8B Qwen model’s mathematics performance — a result presented as evidence of superhuman model-improvement ability, which author Sean Goedecke argues is overstated.

**「Solution」** For the toy game networks, he notes that the input channels are labeled and mapped directly to 8x8 grid cells, so a human can compute which cells the first layer attends to by taking an L2 norm across the 32 first-layer weights per channel — a three-line Python calculation whose heatmap makes several games identifiable from player and object positions. Astra computing those norms “in its head” is superhuman mental arithmetic, the author says, not superhuman research. He then reframes the Qwen result: the model was not broadly bad at mathematics but looped after 32k tokens, so longer problems failed. The author would attack that with a steering/abliteration-style method: collect looping and non-looping reasoning texts, measure each weight’s contribution to the residual difference, then trim the top contributors. He says Astra did essentially this with four text pairs, cutting and testing weights until it found a patch that stopped the looping and let long math problems proceed — work a competent human researcher could have done.

**「Takeaway」** The author concludes that direct weight editing is an impressive engineering trick, analogous to an LLM patching a compiled binary rather than writing source code, but not a radically new research capability. If LLMs accelerate AI research, he expects the gains to come through better training, not magical direct weight tweaks.

**Tags**: `#LLM interpretability`, `#model weight editing`, `#AI research methodology`, `#hype critique`, `#neural network weights`

---

<a id="item-tech-blog-2"></a>
### [Audience Capture: When Engagement Metrics Replace Real Readers](https://seangoedecke.com/audience-capture/) ⭐️ 6.0/10

rss · Sean Goedecke · Nov 3, 00:00

**「Background」** Writing online comes with a dense apparatus for making engagement numbers rise—view counts, aggregator algorithms, upvote-sorted comments, and sometimes ad or platform payouts—and Sean Goedecke says his engineer’s instinct is to optimize them. The trouble is that engagement is only a proxy for what he actually wants from writing.

**「Solution」** His central worry is audience capture: optimizing the proxy can replace the audience he wants with one he does not. He values smart readers who consider his ideas, knowledgeable feedback, participation in industry conversations, persuasion, and a reputation as a careful thinker, but metrics cannot distinguish those readers from “clickers” who open a post, scan a sentence, and leave—or who comment on a Hacker News thread without reading it. If a hot-button post about microservices draws views, the numbers reward more of the same, while the careful readers he cares about may drift away; the clickers will not notice because they were not reading. Goedecke generalizes this to a distinction between proxy games, such as pageviews or strong Jira ticket metrics, and real games, such as earning the respect of people you respect or doing technical work you are proud of. The difference is whether you care about the goal, not whether it is objectively valuable; a proxy can be worth playing, but winning it at the expense of the real game is a loss, and selling out by habit is worse than making a deliberate tradeoff. He notes that some of his favorite, more philosophical or dryly technical posts got little attention, while popular laments succeeded by giving readers an outlet, and he chooses to write for the roughly 5% who read, think, and correspond, using taste and thin feedback rather than raw views as his signal.

**「Takeaway」** Goedecke’s conclusion is that engagement metrics are useful for exposure but dangerous as a definition of success: once you optimize for clickers, you can lose the readers, conversations, and reputation you actually wanted. The broader lesson is to know which game you are playing—and not to sacrifice the real one by habit.

**Tags**: `#engineering career`, `#metrics and incentives`, `#online writing`, `#Goodhart&\#x27;s law`, `#software engineering culture`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China regulator reportedly pauses IPOs and big shareholder sales to steady slumping stock market](https://www.ft.com/content/fec5981d-0c31-4f21-9a37-a1dd1526f530) ⭐️ 9.0/10

China&\#x27;s securities regulator has reportedly used informal &quot;window guidance&quot; to tell brokers to pause initial public offerings and large shareholder share sales until the market recovers, according to the Financial Times. The reported move followed an 8.5% fall in the CSI 300 index in October — its worst month in more than a decade — leaving the benchmark down about 14% so far this year.

telegram · zaihuapd · Nov 3, 08:01

**「Background」** “Window guidance” is an informal instruction from regulators rather than a published rule, and the reported pause follows earlier stabilization efforts such as state-fund purchases and restrictions on shareholder sales.

**「Impact」** The suspension directly delays equity fundraising for companies preparing to list and temporarily prevents large shareholders from selling, making it harder for those holders to exit their positions.

**Tags**: `#China equities`, `#IPO suspension`, `#securities regulation`, `#shareholder selling`, `#market intervention`

---

<a id="item-finance-news-2"></a>
### [Blackstone president calls for more equity financing in AI buildout](https://www.cnbc.com/2026/11/03/equity-ai-debt-blackstone-pimco-financing.html) ⭐️ 7.0/10

Blackstone President Jon Gray said the AI infrastructure buildout will need more equity financing to limit concentration risks for lenders, speaking at the Hong Kong Monetary Authority&\#x27;s Global Financial Leaders&\#x27; Investment Summit. On the same panel, Pimco CEO Emmanuel Roman warned that AI-related capital spending—estimated at about $10 trillion over five years, citing General Atlantic CEO Bill Ford—could be too much for markets to absorb, with roughly $550 billion of AI debt issued so far this year.

rss · CNBC Finance · Nov 3, 06:46

**「Background」** Jon Gray is president and chief operating officer of Blackstone, the New York-based asset manager, and was speaking at the Hong Kong Monetary Authority’s Global Financial Leaders’ Investment Summit. The panel focused on the financing mix: the AI infrastructure buildout is drawing heavily on debt, but lenders’ returns are capped at interest and principal, so they bear concentration risk without the upside available to shareholders.

**「Who is exposed」** Debt investors and lenders financing AI developers and data-center projects would bear the concentration risk Gray described, since their returns are capped at interest and principal while their exposure to one fast-growing sector grows; companies are increasingly turning to structured transactions to limit the debt they take on.

<details><summary>References</summary>
<ul>
<li><a href="https://www.blackstone.com/people/jonathan-gray/">Jonathan Gray - Blackstone</a></li>
<li><a href="https://www.cnbc.com/2026/08/14/ai-infrastructure-debt-leverage-risks.html">AI infrastructure debt and leverage draw market scrutiny - CNBC</a></li>
<li><a href="https://www.bis.org/publications/qr-202603/financing-ai-infrastructure-boom-on-and-off-balance-sheet-borrowing">Financing the AI infrastructure boom: on- and off-balance ...</a></li>

</ul>
</details>

**Tags**: `#AI infrastructure`, `#debt financing`, `#credit risk`, `#private capital`, `#data centers`

---

<a id="item-finance-news-3"></a>
### [Estée Lauder tops estimates and raises outlook; Marvell to buy Lumentum for $115 billion](https://www.cnbc.com/2026/11/02/stocks-making-the-biggest-moves-premarket-crwd-rivn-mu.html) ⭐️ 7.0/10

Estée Lauder reported adjusted earnings of 72 cents per share on revenue of $3.72 billion for its fiscal first quarter, beating FactSet analyst expectations of 51 cents and $3.65 billion, and raised its full-year earnings outlook. Separately, Marvell Technology agreed to acquire Lumentum in an all-stock deal that values Lumentum at $115 billion, with the transaction expected to close in the first half of 2028.

rss · CNBC Finance · Nov 2, 12:49

**「Background」** Marvell&\#x27;s all-stock offer values Lumentum at roughly $1,132 per share, about a 23.9% premium to Lumentum&\#x27;s Oct. 28 closing price, the last trading day before market speculation about a deal, according to Marvell&\#x27;s announcement. Marvell supplies semiconductors for data infrastructure and Lumentum makes optical and photonic components used in AI and cloud computing networks.

<details><summary>References</summary>
<ul>
<li><a href="https://investor.marvell.com/news-events/press-releases/detail/1040/marvell-and-lumentum-to-combine-creating-a-category-leader-in-ai-connectivity">Marvell and Lumentum to Combine, Creating a Category Leader ...</a></li>
<li><a href="https://www.wsgr.com/en/insights/firm-advises-marvell-on-dollar115-billion-acquisition-of-lumentum.html">Firm Advises Marvell on $115 Billion Acquisition of Lumentum</a></li>

</ul>
</details>

**Tags**: `#premarket movers`, `#earnings surprise`, `#M&amp;A`, `#analyst upgrades`, `#semiconductors`

---

<a id="item-finance-news-4"></a>
### [UK proposes 10-year settlement wait for most migrants](https://www.gov.uk/government/news/home-secretary-unveils-new-rules-for-migrants-settling-in-the-uk) ⭐️ 7.0/10

The UK government has proposed extending the standard waiting period for most migrants to apply for permanent settlement from five to 10 years, while allowing the highest earners to apply after three years and people earning over £50,271 a year or working in public-service roles such as doctor, nurse or teacher to use a five-year route. Applicants would also need no criminal record, English at A-Level standard, no unpaid tax and continuous National Insurance payments; the plan is a proposal, not yet law.

telegram · zaihuapd · Nov 2, 23:50

**「Background」** Most migrants can currently apply for indefinite leave to remain—permanent residency—after five years, and the Home Office ran a consultation dated November 2025 on replacing that system with a contribution-based “earned settlement” model.

**「Impact」** If enacted, the change would lengthen the path to permanent status for most migrants and give public-service employers a faster five-year route for recruited doctors, nurses and teachers.

<details><summary>References</summary>
<ul>
<li><a href="https://www.gov.uk/government/consultations/earned-settlement">Earned settlement - GOV.UK</a></li>

</ul>
</details>

**Tags**: `#UK immigration policy`, `#earned settlement`, `#labor market`, `#Home Office`, `#visa policy`

---

<a id="item-finance-news-5"></a>
### [Apple posts record September-quarter revenue, warns memory costs are squeezing margins](https://www.apple.com/newsroom/2026/11/apple-reports-fourth-quarter-results/) ⭐️ 7.0/10

Apple reported fiscal 2026 fourth-quarter revenue of $114.5 billion, up 12% from a year earlier and a record for the September quarter, while executives said rising memory prices are pressuring gross margins and expect further cost increases. Greater China revenue rose 21% year over year to a September-quarter record, and Apple said memory shortages are the main constraint on future Mac and iPad supply.

telegram · zaihuapd · Nov 3, 04:00

**「Background」** Apple&\#x27;s fiscal year ends in late September, and a year earlier its September-quarter Greater China revenue had fallen short of analyst estimates at $17.54 billion versus $18.75 billion expected, according to Yahoo Finance. John Ternus, who became CEO in September 2026 when Tim Cook moved to executive chairman, spoke on the earnings call.

**「Impact」** Prospective Mac and iPad buyers face tighter availability in the December quarter and higher prices, as Apple said memory-supply constraints are limiting output and it has raised product prices to offset rising memory costs.

<details><summary>References</summary>
<ul>
<li><a href="https://finance.yahoo.com/markets/stocks/live/apple-earnings-live-apple-beats-q4-estimates-on-strong-iphone-sales-but-misses-on-china-revenue-221806957.html">Apple earnings live: Apple beats Q4 estimates on strong iPhone sales...</a></li>
<li><a href="https://en.wikipedia.org/wiki/John_Ternus">John Ternus - Wikipedia</a></li>
<li><a href="https://www.apple.com/newsroom/2026/04/tim-cook-to-become-apple-executive-chairman-john-ternus-to-become-apple-ceo/">Tim Cook to become Apple Executive Chairman John Ternus to ...</a></li>
<li><a href="https://finance.yahoo.com/markets/stocks/live/apple-earnings-live-apple-beats-q4-estimates-on-strong-iphone-sales-but-misses-on-china-revenue-221806957.html">Apple earnings live: Apple beats Q4 estimates on strong iPhone sales...</a></li>

</ul>
</details>

**Tags**: `#Apple earnings`, `#Greater China`, `#memory prices`, `#supply constraints`

---