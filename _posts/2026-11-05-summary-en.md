---
layout: default
title: "Horizon Summary: 2026-11-05 (EN)"
date: 2026-11-05
lang: en
---

> From 54 items, 14 important content pieces were selected

---

**Technology News**
1. [OpenAI cyber team claims about a thousand fewer Linux root paths](#item-tech-news-1) ⭐️ 8.0/10
2. [Tencent Releases Open-Weight Hy4 for Science and Game Development](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic releases FlashProve code, spec for provable LLM inference](#item-tech-news-3) ⭐️ 8.0/10
4. [OpenAI to acquire Pierre Computer Company](#item-tech-news-4) ⭐️ 7.0/10
5. [Go Proposes New JSON API With encoding/json/v2](#item-tech-news-5) ⭐️ 7.0/10
6. [AI Vulnerability Discovery Is Forcing a Technical-Debt Reckoning](#item-tech-news-6) ⭐️ 7.0/10
7. [Ripple-65B Preview Claims U.S. Open-Weight Agentic Coding SOTA](#item-tech-news-7) ⭐️ 7.0/10
8. [Moonshot AI publishes Kimi K3.1 Pro weights on Hugging Face](#item-tech-news-8) ⭐️ 7.0/10
9. [AMD Q4 guidance points to first revenue lead over Intel](#item-tech-news-9) ⭐️ 7.0/10
10. [Calif Demos Persistent Lockdown Mode Jailbreak on iPhone 18 Pro](#item-tech-news-10) ⭐️ 7.0/10
11. [Huawei Reportedly Tells Customers to Source Ascend 960DT HBM](#item-tech-news-11) ⭐️ 7.0/10
12. [Bluetooth HDT adopted: LE peak throughput reaches 7.5 Mbps](#item-tech-news-12) ⭐️ 7.0/10

**Financial News**
1. [甲骨文取消与腾讯70亿美元AI芯片租赁协议](#item-finance-news-1) ⭐️ 8.0/10
2. [10-year Treasury yield falls after Democrats win Congress](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI cyber team claims about a thousand fewer Linux root paths](https://openai.com/index/a-thousand-fewer-paths-to-root/) ⭐️ 8.0/10

OpenAI&\#x27;s cyber team has published research framed as reducing by roughly a thousand the privilege-escalation paths to root in the Linux kernel, a claim aimed at the kernel maintainers and distribution vendors who must assess and ship such fixes. The supplied item contains no technical detail — no discovery method, affected versions, patch status, or disclosure timeline — so the headline count is vendor framing rather than an independently verified result. Hacker News commenters cited 948 issues in connection with the work, a figure that appears in the discussion rather than in the supplied source material.

hackernews · dangelosaurus · Nov 4, 23:33 · [Discussion](https://news.ycombinator.com/item?id=50372929)

**「Background」** Local privilege escalation is a Linux kernel bug class in which an unprivileged local user can gain root access. OpenAI&\#x27;s November 4, 2026 research post claims an autonomous pipeline reproduced 1,724 kernel vulnerabilities in a single October run and validated 948 of them as working local privilege-escalation exploits, at a reported $1,213,430 in API credits.

**「Impact」** Because the work is presented as many separate privilege-escalation paths rather than a single bug, any risk reduction for Linux users depends on individual fixes being accepted upstream and reaching the kernel versions that distributions actually ship.

**「Community discussion」** Commenters debated whether the count reflects a kernel too complex to reason about or a security model in which local access is assumed to lead to root; one called 948 vulnerabilities &quot;kind of shocking,&quot; while another asked why critical infrastructure keeps running if such flaws are widespread. The OpenAI team member who posted the work invited questions but, in the supplied thread, did not address those concerns.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/a-thousand-fewer-paths-to-root/">A thousand fewer paths to root - OpenAI</a></li>
<li><a href="https://cybersecuritynews.com/openai-uncovers-948-linux-kernel-vulnerabilities/">OpenAI Cyber Model Uncovers 948 Linux Kernel Privilege ...</a></li>
<li><a href="https://explainx.ai/blog/openai-linux-kernel-948-local-privilege-escalation-exploits-1-2-million-api-cost-pipeline-patch-the-planet-2026">OpenAI Linux Kernel Pipeline: 948 Root Exploits, $1.2M ...</a></li>

</ul>
</details>

**Tags**: `#Linux kernel security`, `#privilege escalation`, `#vulnerability discovery`, `#AI security`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [Tencent Releases Open-Weight Hy4 for Science and Game Development](https://hy.tencent.ai/research/hy4) ⭐️ 8.0/10

Tencent has released Hy4, an open-weight AI model positioned for scientific research and game development. The release also open-sources HyCell for single-cell representation and HyPDE for physical field modeling. For games, Tencent says it worked with its Interactive Entertainment Group on training data and evaluations, adapted Hy4 for Unreal Engine, Unity, and Godot, and extended it to multiplayer development. Tencent acknowledges that Hy4 remains behind top proprietary models on its internal benchmarks for research-level mathematics, long-horizon coding, model self-improvement, and advanced visual question answering.

hackernews · Philpax · Nov 4, 14:11 · [Discussion](https://news.ycombinator.com/item?id=50365780)

**「Prior Hy4 preview」** Hy4 builds on a preview release that Hugging Face lists as a 770B-parameter Mixture-of-Experts model activating 49B parameters per token. Coverage of the launch also describes Hy4 as the first model in Tencent&\#x27;s Hy family to add visual understanding.

**「Impact」** Game teams and researchers can evaluate open weights for engine-specific and scientific workflows, but they should treat the engine integrations and comparative positioning as Tencent&\#x27;s claims until independent testing is available. Tencent&\#x27;s own caveat means long-horizon coding tasks may still require a proprietary fallback.

**「Community discussion」** Commenters welcomed the open sourcing of HyCell and HyPDE as a contrast to closed commercial AI research and credited Tencent for stating the remaining gap to proprietary models. One commenter reported that, in a Plotly data-analytics benchmark, Hy4 landed between GPT-6.1 Sol and GPT-6.1 Terra on cost and accuracy but was very slow, running about 26 queries per question and sometimes 64.

<details><summary>References</summary>
<ul>
<li><a href="https://interestingengineering.com/ai-robotics/tencent-hy4-open-source-model">China&#x27;s Tencent Hy 4 challenges world&#x27;s top models with 7.2% error rate</a></li>
<li><a href="https://huggingface.co/tencent/Hy4-preview">tencent / Hy 4 -preview · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#Tencent`, `#AI research`, `#game development`, `#scientific foundation models`

---

<a id="item-tech-news-3"></a>
### [Anthropic releases FlashProve code, spec for provable LLM inference](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic has released a technical specification and code for FlashProve, an in-development cryptographic system for proving that a given LLM output was produced by a specified model. The approach relies on model providers publishing a fingerprint that does not reveal weights; users can then match outputs and verify claims locally, which Anthropic says could expose model substitution or false third-party claims. Anthropic says research is ongoing and has no deployment plans, so this is a research release rather than a shipped verification service.

hackernews · ltononro · Nov 4, 17:17 · [Discussion](https://news.ycombinator.com/item?id=50368626)

**「Earlier verifiable-inference work」** Provable inference addresses a concrete trust gap: a provider can return text while claiming it came from a particular model, and a cryptographic proof can bind the output to committed weights without revealing them. An earlier system, VerInf, reported a sound four-round Ligero proof for a 1,093-token forward pass of the full 48-layer Llama 4 Maverick 400B mixture-of-experts model, but proving took 19.3 hours on a single DGX Spark and peaked at 77.6 GB of GPU memory. FlashProve&\#x27;s documentation describes running the same model at full size with a 1,024-token context on one H100 and reaching about 110 tokens per second of prefill at a batch of 24, illustrating the performance gap the new work targets.

**「Impact」** For developers and auditors, the design would enable model-identity checks only if providers publish fingerprints for released models; because Anthropic has announced no deployment, there is no API or compatibility change to rely on yet.

**「Community discussion」** Commenters debated the approach’s novelty and practicality: one researcher said FlashProve builds on their VerInf work with little attribution, while another called it a significant improvement over prior zk results but argued closed-model proofs remain harder and could be cheaper through independent inference providers. Others noted that open-weight models can be checked by deterministic re-execution and questioned proof-checking costs, citing a commitment good for about 16 million requests and 17–21 seconds to check a proof.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/anthropics/FlashProve">GitHub - anthropics/ FlashProve : A research prototype for...</a></li>
<li><a href="https://github.com/JamesPetrie/VerInf/blob/main/README.md">VerInf/README.md at main · JamesPetrie/VerInf · GitHub</a></li>

</ul>
</details>

**Tags**: `#verifiable inference`, `#large language models`, `#zero-knowledge proofs`, `#AI security`, `#cryptography`

---

<a id="item-tech-news-4"></a>
### [OpenAI to acquire Pierre Computer Company](https://openai.com/index/openai-to-acquire-pierre/) ⭐️ 7.0/10

OpenAI announced that it will acquire Pierre Computer Company, a startup associated with git- and diff-oriented developer tooling. The supplied announcement does not disclose the purchase price, closing timeline, or how Pierre&\#x27;s products will be integrated into OpenAI. Commenters link the deal to OpenAI&\#x27;s existing work on scaling Git and to Pierre&\#x27;s Code.Storage service, which one commenter says stores generated code and other machine-made artifacts for agentic workloads.

hackernews · itunpredictable · Nov 4, 15:21 · [Discussion](https://news.ycombinator.com/item?id=50366863)

**「What Pierre brings to Codex」** Pierre Computer Company develops Code Storage, a code-storage service, and maintains open-source libraries including Trees for browsing project files and Diffs for reviewing changes \(tool-1-1, tool-1-3\). OpenAI said Codex users were already relying on those tools and that, following the acquisition, Pierre&\#x27;s open-source projects would remain freely available while Code Storage customers could continue using the service as it is integrated into Codex \(tool-1-2, tool-1-3\).

**「Impact」** Pierre&\#x27;s Code Storage customers are promised continued access after the acquisition closes, but OpenAI says it plans to bring Code Storage&\#x27;s features and functionality into Codex. With no migration timeline or compatibility details provided, teams building on Code Storage should plan for the product surface to change as it is absorbed into Codex.

**「Community discussion」** Commenters highlighted Pierre&\#x27;s diffs library and Code.Storage, with one raising the speculative concern that AI labs may also use acquired developer-tool teams to learn how such products are built. Others noted that Pierre was founded by Bootstrap creators Jacob Thornton and Mark Otto, while one commenter suggested a term for buying a company because it is cheaper than subscribing to its product.

<details><summary>References</summary>
<ul>
<li><a href="https://tech-insider.org/openai-to-acquire-pierre-codex-code-storage-trees-diffs-2026/">OpenAI Pierre Acquisition: 3 Tools for Codex [2026]</a></li>
<li><a href="https://www.wsj.com/tech/ai/openai-to-bring-pierre-computers-code-storage-to-codex-through-acquisition-05f53582">OpenAI to Bring Pierre Computer’s Code Storage to Codex ...</a></li>
<li><a href="https://modeldex.substack.com/p/openai-acquires-pierre-codex-git">OpenAI to Buy Pierre, the Startup Behind Code Tools Already ...</a></li>
<li><a href="https://openai.com/index/openai-to-acquire-pierre/">OpenAI to acquire Pierre Computer Company, Inc. | OpenAI</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#acquisitions`, `#developer tools`, `#AI coding`, `#git infrastructure`

---

<a id="item-tech-news-5"></a>
### [Go Proposes New JSON API With encoding/json/v2](https://go.dev/blog/jsonv2) ⭐️ 7.0/10

Go has published a proposal and blog post for a new JSON API aimed at Go developers who rely on the standard library&\#x27;s \`encoding/json\` package. Discussion in the supplied comments refers to an \`encoding/json/v2\` package and a lower-level \`jsontext\` package, but the material does not establish a release date, compatibility guarantees, or whether the API has shipped. The proposal is therefore an announced design direction rather than a confirmed standard-library replacement.

hackernews · olexsmir · Nov 4, 17:52 · [Discussion](https://news.ycombinator.com/item?id=50369106)

**「Background」** Go&\#x27;s existing \`encoding/json\` package is referred to as v1 in the proposal, and the new API is being introduced under a separate \`encoding/json/v2\` namespace rather than changing v1 in place. The v2 design builds on \`encoding/json/jsontext\`, a lower-level package that processes JSON syntax without depending on Go reflection.

**「Migration impact」** Go 1.27 ships \`encoding/json/v2\`, while the existing \`encoding/json\` package remains available as v1 and new JSON usage is encouraged to adopt v2. Because side-by-side testing found cases where v1 and v2 produce different output for the same structs, developers should audit marshaled output and apply the documented option or tag fixes before migrating; custom parsers can instead target the lower-level \`encoding/json/jsontext\` package.

**「Community Discussion」** Commenters largely welcome \`encoding/json/v2\`, but CamouflagedKiwi argues that the replacement for \`MarshalIndent\` is complicated and non-obvious, making both migration and quick readable-JSON output harder. txomon reports using the \`jsontext\` package at their company for client-specific parse errors while retaining strong performance.

<details><summary>References</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2">A new Go API for JSON - The Go Programming Language</a></li>
<li><a href="https://github.com/golang/go/issues/71497">encoding / json / v 2 : new API for encoding / json · Issue #71497...</a></li>
<li><a href="https://importstatic.com/go/go-json-v2-migration">Go JSON v 2 Migration : What Breaks in Go 1.27 | ImportStatic</a></li>
<li><a href="https://pkg.go.dev/encoding/json">json package - encoding / json - Go Packages</a></li>
<li><a href="https://github.com/golang/go/issues/71497">encoding / json / v 2 : new API for encoding / json · Issue #71497...</a></li>

</ul>
</details>

**Tags**: `#Go`, `#JSON`, `#standard library`, `#API design`, `#encoding/json/v2`

---

<a id="item-tech-news-6"></a>
### [AI Vulnerability Discovery Is Forcing a Technical-Debt Reckoning](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

An IEEE Spectrum analysis argues that AI-assisted vulnerability discovery is forcing software teams to confront technical debt accumulated over decades, using a PHP-to-shell vulnerability as a framing example. The piece is an argument about maintenance priorities rather than a new release or an independently measured remediation result. Its core claim is that AI vulnerability discovery makes accumulated security weaknesses into remediation work teams can no longer defer.

hackernews · pseudolus · Nov 4, 11:52 · [Discussion](https://news.ycombinator.com/item?id=50364336)

**「Background」** PHP2Shell is the vulnerability case behind the IEEE Spectrum article: it affected WordPress, Drupal, and other PHP-based sites—including NASA, Wikipedia, and the White House—and exposed them to data theft and remote code execution. A summary of the report says researchers disclosed it to the PHP Foundation and a patch shipped before exploitation, making the incident a concrete example of the patching burden that the article links to accumulated technical debt.

**「Patch-management burden」** For PHP site operators, AI-assisted discovery of the PHP2Shell flaw turns the technical-debt debate into an immediate patch-management problem: reports describe leaked patches and crisis response, and the case shows AI finding weaknesses in longstanding code. Teams should inventory PHP-facing components, monitor coordinated disclosure channels, and apply vendor fixes promptly rather than waiting for routine maintenance.

**「Community Discussion」** Commenters challenged the debt-payoff framing: swatcoder argued that many findings require restructuring rather than narrow patches, so the work may become a compulsory treadmill of feature-neutral fixes. xbmcuser argued that AI auditing makes open source&\#x27;s implicit &quot;someone else audited it&quot; assurance more real, while Arbortheus hoped the same discovery effort would incidentally surface state-held or commercial zero-days and yield more robust software over time.

<details><summary>References</summary>
<ul>
<li><a href="https://aibriefs.news/card/37894e93-595e-40f9-a8a5-1e6ae4f75f9f">IEEE Spectrum: AI is forcing a payoff of 40 years of ...</a></li>
<li><a href="https://www.youtube.com/watch?v=G0FrekAkeFY">The PHP vulnerability that locked the internet: AI found it... - YouTube</a></li>
<li><a href="https://arxiv.org/pdf/2610.36334">PHP 2 Shell and the Future of AI - Discovered Vulnerability Disclosure...</a></li>
<li><a href="https://kcwebspecialists.com/php2shell-vulnerabilities-wordpress-security/">PHP 2 Shell Vulnerabilities : AI Discovery , Risks &amp; Fixes In Plain English</a></li>

</ul>
</details>

**Tags**: `#ai-security`, `#technical-debt`, `#vulnerability-discovery`, `#open-source-security`, `#legacy-code`

---

<a id="item-tech-news-7"></a>
### [Ripple-65B Preview Claims U.S. Open-Weight Agentic Coding SOTA](https://www.ricursive.com/ripple) ⭐️ 7.0/10

Ricursive has published a preview of Ripple-65B, a 65B dense open-weight model that it claims is U.S. state of the art on agentic coding. The claim is scoped to U.S. open-weight models, and the supplied announcement provides no deployment details or independent benchmark results. For developers evaluating open-weight coding agents, it is therefore a claim to verify rather than a documented, broadly available model.

hackernews · Philpax · Nov 4, 18:53 · [Discussion](https://news.ycombinator.com/item?id=50369925)

**「Background」** Ripple-65B Preview is Ricursive Intelligence&\#x27;s 65-billion-parameter dense Transformer, pretrained on 12 trillion tokens with support for up to a 1M-token context and released under Apache 2.0. Its 80.5 score is on Terminal-Bench 2.1; for comparison, the same benchmark has Qwen 3.8 Flash Next at 84.3 and Qwen 3.8-27B at 73.0, with the former&\#x27;s mixture-of-experts design making inference-cost comparisons part of the discussion.

**「Impact」** For local-model users, the 65B dense architecture is likely to make inference slow on consumer-grade hardware, so practical use would depend on hosted access or higher-end GPUs; the preview does not specify either.

**「Community Discussion」** Commenters pushed back on the breadth of the SOTA label, noting that it is narrowed to U.S. open-weight models and that the announcement does not mention other open-weight competitors. One commenter reported Terminal Bench 2.1 scores of 80.5 for Ripple-65B versus 84.3 for Qwen 3.8 Flash Next and 73.0 for Qwen 3.8-27B, while others focused on the cost of running a 65B dense model and on U.S.-only procurement constraints.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/ricursiveAI/Ripple-65B-Preview">ricursiveAI/ Ripple - 65 B - Preview · Hugging Face</a></li>
<li><a href="https://iamag.it/en/news/ripple-65b-preview-open-weight-agentic-coding-model">Ripple - 65 B Preview : Dense 65 B Model Tops US Agentic Coding</a></li>
<li><a href="https://news.ycombinator.com/item?id=50369925">Ripple - 65 B Preview : U.S. Open-Weight SOTA on... | Hacker News</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#agentic coding`, `#LLM benchmarks`, `#model release`, `#AI infrastructure`

---

<a id="item-tech-news-8"></a>
### [Moonshot AI publishes Kimi K3.1 Pro weights on Hugging Face](https://huggingface.co/moonshotai/Kimi-K3.1-Pro) ⭐️ 7.0/10

Moonshot AI has published the weights for Kimi K3.1 Pro on Hugging Face, making the model available for self-hosting and third-party inference. The available account does not specify parameter count, license terms, or benchmark figures, leaving the model&\#x27;s hardware requirements and usage constraints unclear. For developers and organizations, the release provides a downloadable model that can be run on their own infrastructure or through third-party hosts.

hackernews · abrarthought · Nov 4, 15:30 · [Discussion](https://news.ycombinator.com/item?id=50366999)

**「Prior context」** Kimi K3.1 Pro is post-trained from Kimi K3 via large-scale joint reinforcement learning across downstream domains, and its model card describes it as the first entry in the K3.1 series with a 1-million-token context window. Moonshot&\#x27;s earlier Kimi K3 open-weights release, covered in third-party spec writeups in July 2026, was reported at 2.8T parameters with a roughly 1.56 TB download, which is why the size of the new checkpoint dominates discussion of local deployment.

**「Deployment and cost trade-offs」** Self-hosting is impractical for most teams: one commenter estimates K3.1 Pro needs something like an 8x B300 node, so the practical path is a hosted endpoint, and a reviewer lists Kimi API pricing at $2 per million input tokens \($0.20 cached\) and $10 per million output tokens — about one third less than Kimi K3 and level with Sonnet 5.5. Because throughput varies by provider, with Together and Modal reported as faster than Moonshot&\#x27;s own endpoint at the same price, developers should benchmark the specific endpoint they choose rather than assume uniform performance.

**「Community Discussion」** Commenters disagreed over benchmark credibility: one said Kimi K3.1 Pro does not clearly beat DeepSeek V4.1-Flash and looks &quot;benchmaxxed,&quot; while another reported testing that did not show this and described it as a strong open release that is a bit off the frontier. A separate discussion focused on serving economics, with one commenter estimating an 8x B300-class node would be needed to run the weights and another reporting that third-party providers such as OpenRouter already host it, with throughput varying by provider.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/moonshotai/Kimi-K3.1-Pro">moonshotai/Kimi-K3.1-Pro - Hugging Face</a></li>
<li><a href="https://www.yottalabs.ai/post/kimi-k3-specs-benchmarks-how-to-access-2026">Kimi K3 Model Size, Open Weights, and Hardware Requirements ...</a></li>
<li><a href="https://www.eesel.ai/blog/kimi-k3-1-pro-review">Kimi K 3 . 1 Pro review: smart and cheap per token, but slow | eesel AI</a></li>
<li><a href="https://iadecider.com/inference-providers">Inference Providers | IADecider</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#LLM releases`, `#Moonshot AI`, `#model benchmarks`, `#inference serving`

---

<a id="item-tech-news-9"></a>
### [AMD Q4 guidance points to first revenue lead over Intel](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

AMD&\#x27;s Q4 revenue guidance points to the company reporting higher quarterly revenue than Intel for the first time, according to Tom&\#x27;s Hardware—a forecast, not a completed sales result. The report cites $17 billion in AMD guidance, which would exceed Intel&\#x27;s own projection, with Instinct AI accelerator sales named as a growth driver. The comparison is by revenue rather than CPU unit shipments, and AMD&\#x27;s lead remains contingent on hitting its guidance.

hackernews · rbanffy · Nov 4, 15:38 · [Discussion](https://news.ycombinator.com/item?id=50367125)

**「The guidance gap」** According to the report, AMD has never previously posted higher quarterly revenue than Intel, the far larger x86 vendor for most of the PC era. The comparison rests on forward guidance rather than reported results: AMD guided Q4 2026 revenue to roughly $17 billion, plus or minus 3 percent \(about $16.49–17.51 billion\), while Intel&\#x27;s outlook sits at a $15–16 billion range with a $15.5 billion midpoint. AMD attributes part of that growth to Instinct accelerator sales, an area where its volume remains small next to Nvidia&\#x27;s.

**「A wider second source, not a shift in allocations」** For data center buyers, the practical effect is a marginally broader second source: AMD&\#x27;s expected Q4 growth is attributed to Instinct accelerators rather than Epyc CPUs alone, yet third-party 2026 estimates still place AMD at roughly 5–10% of AI accelerator revenue against Nvidia&\#x27;s 75–80%+, so near-term procurement allocations are unlikely to move away from Nvidia on the strength of this guidance.

**「Community discussion」** Commenters treated the forecast less as proof of AMD strength than as a sign of Intel&\#x27;s execution problems, citing Intel&\#x27;s 13th- and 14th-generation voltage issues and questioning both companies&\#x27; AI credibility. Others debated whether x86 has a long-term future as Arm-based laptops gain share, while one user said they prefer AMD for anti-forensics-tuned Linux kernels despite uncertainty about its platform security.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections">AMD expects to outsell Intel in Q4 for the first time in ...</a></li>
<li><a href="https://wccftech.com/amd-is-set-to-out-earn-intel-for-the-first-time-in-its-history-guiding-to-17-billion-in-q4-revenue-against-intels-15-5-billion-midpoint-projection/">AMD Is Set To Out-Earn Intel For The First Time In Its ...</a></li>
<li><a href="https://braindetox.kr/en/posts/amd_q4_revenue_surpass_intel_forecast.html">AMD Q4 Revenue Guidance: $17B vs Intel’s $15B–$16B Outlook</a></li>
<li><a href="https://commandlinux.com/statistics/ai-gpu-market-share-nvidia-vs-amd-vs-intel/">AI GPU Market Share NVIDIA vs AMD vs Intel: 2026 Statistics</a></li>
<li><a href="https://www.companieshistory.com/ai-market-share-by-company/">AI Market Share By Company Statistics 2026</a></li>

</ul>
</details>

**Tags**: `#AMD`, `#Intel`, `#semiconductors`, `#CPUs`, `#AI accelerators`

---

<a id="item-tech-news-10"></a>
### [Calif Demos Persistent Lockdown Mode Jailbreak on iPhone 18 Pro](https://appleinsider.com/articles/26/11/04/apples-lockdown-mode-thwarted-by-a-new-persistent-iphone-jailbreak) ⭐️ 7.0/10

Hacker team Calif posted a video showing a Lockdown Mode-enabled iPhone 18 Pro jailbroken and still jailbroken after updating to iOS 27.2; the video shows a PDF sent via AirDrop and the update performed through Settings. Calif did not disclose technical details or release a jailbreak tool, saying it is reporting the vulnerability to Apple. The demonstration has not been independently verified and contrasts with Apple&\#x27;s March 2026 claim that Lockdown Mode had a 100% protection rate since 2022.

telegram · zaihuapd · Nov 4, 14:38

**「Background」** Lockdown Mode is Apple’s optional high-security setting for users at elevated risk of targeted attacks, intended to reduce the device’s attack surface by disabling or limiting selected features. Apple said in March 2026 that the mode had maintained a 100% protection rate since 2022; Calif’s video is presented as a demonstration that this protection can be bypassed.

**「Limited near-term exposure, but Lockdown Mode is no longer a guaranteed ceiling」** For high-risk users who depend on Lockdown Mode, the demo undercuts Apple&\#x27;s March 2026 claim of a 100% protection rate since 2022: a single device was shown jailbroken with the setting enabled and still jailbroken after updating to iOS 27.2. The immediate exposure is narrower than that implies, because Calif released no jailbreak tool and withheld technical details while disclosing the flaw to Apple, so the concrete action for these users is to watch for a patch rather than change configurations now.

<details><summary>References</summary>
<ul>
<li><a href="https://www.iphones.ru/iNotes/hakery-vzlomali-iphone-18-pro-s-vklyuchyonnym-rezhimom-maksimalnoy-zashchity-lockdown-mode-i-dzheylbreyk-perezhil-obnovlenie-ios">Хакеры взломали iPhone 18 Pro с включённым режимом...</a></li>
<li><a href="https://tech.onliner.by/2026/11/04/specialisty-vzlomali-iphone-18-pro-s-rezhimom-maksimalnoj-zashhity-lockdown-mode">Специалисты взломали iPhone 18 Pro с режимом максимальной...</a></li>

</ul>
</details>

**Tags**: `#iOS security`, `#Lockdown Mode`, `#jailbreak`, `#vulnerability disclosure`, `#Apple`

---

<a id="item-tech-news-11"></a>
### [Huawei Reportedly Tells Customers to Source Ascend 960DT HBM](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

Huawei has reportedly told some customers that its next flagship AI chip, the Ascend 960DT, will mainly use high-bandwidth memory \(HBM\) from Samsung and SK Hynix, and that customers must secure the memory themselves because Chinese HBM capacity is insufficient. The report, attributed to The Information and relayed by The Next Web, describes HBM being soldered onto very low-performance processors, shipped to Hong Kong under processor customs codes, carried into mainland China, and removed by heating; a Shenzhen chip broker said one HBM3E device now costs about $4,000, up from hundreds of dollars a year earlier. The supplied account gives no volumes, timeline, or Huawei confirmation, and the claims were not independently verified.

telegram · zaihuapd · Nov 4, 14:52

**「HBM supply context」** High-bandwidth memory \(HBM\) is stacked DRAM built to feed AI accelerators; Samsung, SK hynix and Micron contributed to the standard and are among its main suppliers. Reporting on China&\#x27;s HBM shortage describes smuggled memory reaching Huawei&\#x27;s customers, with the upcoming Ascend 960DT expected to depend heavily on Samsung and SK hynix parts.

**「Procurement burden」** Customers planning Ascend 960DT deployments must source HBM separately from Huawei, so system cost and deployment timing will hinge on memory they procure; HBM3E was already quoted at about $4,000 per unit in the gray market, up from hundreds of dollars a year earlier. Quick domestic relief is not assured: CXMT was reported in September 2026 to be about two months from limited HBM3E production, so buyers should plan for continued exposure to external or gray-market supply and its pricing and provenance risk.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/High_Bandwidth_Memory">High Bandwidth Memory - Wikipedia</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server Packages...</a></li>
<li><a href="https://xenospectrum.com/en/hbm-smuggling-copackaged-export-control/">China&#x27;s Gray Market HBM3E Trades at About $4,000 Per Unit as ...</a></li>
<li><a href="https://www.kucoin.com/news/flash/the-information-investigates-hbm-smuggling-chain-from-south-korea-to-china">The Investigation Examines the HBM Smuggling Chain ... - KuCoin</a></li>

</ul>
</details>

**Tags**: `#Huawei Ascend`, `#HBM supply`, `#AI chips`, `#semiconductor supply chain`, `#export controls`

---

<a id="item-tech-news-12"></a>
### [Bluetooth HDT adopted: LE peak throughput reaches 7.5 Mbps](https://www.bluetooth.com/press/bluetooth-high-data-throughput-opens-a-new-chapter-in-wireless-performance/) ⭐️ 7.0/10

The Bluetooth SIG announced on November 4 that it has adopted Bluetooth HDT \(High Data Throughput\), raising the maximum Bluetooth LE rate from 2 Mbps to 7.5 Mbps—nearly fourfold—while also improving capacity, energy efficiency, and reliability. HDT is an optional feature of Bluetooth Core 7.0 and is designed to coexist compatibly with older devices. Its first standardized application is high-end wireless audio with lossless and high-resolution support, with initial products expected in 2027.

telegram · zaihuapd · Nov 5, 01:39

**「Bluetooth LE&\#x27;s previous 2 Mbps ceiling」** Bluetooth LE&\#x27;s previous maximum supported bit rate was 2 Mbps, provided by the 2M PHY. Bluetooth HDT is an optional feature in the recently adopted Bluetooth Core 7.0, so it raises the ceiling to 7.5 Mbps without making the higher rate mandatory across all LE devices.

**「Impact」** Device makers will need to choose to implement the optional Core 7.0 feature to use HDT, and current devices will not gain the higher rate through the standard alone; the first products using it are expected in 2027.

<details><summary>References</summary>
<ul>
<li><a href="https://www.techpowerup.com/354478/bluetooth-sig-announces-bluetooth-high-data-throughput">Bluetooth SIG Announces Bluetooth High Data Throughput</a></li>
<li><a href="https://www.bluetooth.com/blog/bluetooth-le-will-soon-get-a-major-boost-in-speed-introducing-bluetooth-high-data-throughput-hdt/">Bluetooth ® connectivity will soon... | Bluetooth ® Technology Website</a></li>

</ul>
</details>

**Tags**: `#Bluetooth`, `#wireless standards`, `#Bluetooth LE`, `#lossless audio`, `#hardware`

---

## Financial News

<a id="item-finance-news-1"></a>
### [甲骨文取消与腾讯70亿美元AI芯片租赁协议](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 8.0/10

据《金融时报》援引的报道，甲骨文在特朗普政府官员提出关切后，取消了一项与腾讯价值约70亿美元的AI芯片租赁协议。报道称，该五年期协议原定让腾讯通过甲骨文在东南亚的数据中心租用约10万枚先进AI芯片，腾讯今年签署该协议，并支付了约占总额30%的首付款；甲骨文和腾讯均未公开确认这些细节。

telegram · zaihuapd · Nov 4, 11:01

**「Background」** Because US export rules bar Nvidia from selling its most advanced AI chips to Chinese companies, Tencent had signed a five-year lease for capacity in Oracle’s Southeast Asian data centers instead.

**「Impact」** Tencent loses its planned route to roughly 100,000 advanced AI chips through Oracle’s Southeast Asian data centers, while Oracle forgoes the roughly $7 billion five-year lease.

<details><summary>References</summary>
<ul>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-04/oracle-scraps-7-billion-deal-to-lease-chips-to-tencent-ft-says">Oracle Scraps $ 7 Billion Deal to Lease Chips to Tencent , FT Says</a></li>
<li><a href="https://nypost.com/2026/11/04/business/oracle-nixes-7b-chip-leasing-deal-with-chinas-tencent-after-trump-admin-pushback-report/">Oracle nixes $ 7 B chip leasing deal with China&#x27;s Tencent after Trump...</a></li>
<li><a href="https://finance.yahoo.com/technology/ai/articles/oracle-cancels-7-billion-tencent-113659321.html?fr=sycsrp_catchall">Oracle Cancels $7 Billion Tencent AI Chip Leasing Agreement ...</a></li>
<li><a href="https://www.reuters.com/world/china/oracle-abandons-7-billion-tencent-ai-deal-under-trump-pressure-ft-reports-2026-11-04/">Oracle abandons $7 billion Tencent AI deal under Trump ...</a></li>

</ul>
</details>

**Tags**: `#Oracle`, `#Tencent`, `#AI chips`, `#US-China tech policy`, `#data centers`

---

<a id="item-finance-news-2"></a>
### [10-year Treasury yield falls after Democrats win Congress](https://www.cnbc.com/2026/11/03/treasury-yields-fall-as-democrats-win-big-in-us-midterm-elections.html) ⭐️ 7.0/10

The 10-year U.S. Treasury yield fell more than 6 basis points \(0.06 percentage points\) to 4.884% on Wednesday as Democrats won both chambers of Congress, while oil prices also dropped.

rss · CNBC Finance · Nov 4, 21:18

**「Background」** Republicans entered the Nov. 3 midterms holding both chambers of Congress, with President Trump not on the ballot; the vote instead determined which party controls Congress. JPMorgan had said ahead of the vote that midterms can shift which sectors receive federal funding but are unlikely to change the long-run fiscal trajectory, as persistent deficits and rising interest costs keep driving federal borrowing.

<details><summary>References</summary>
<ul>
<li><a href="https://privatebank.jpmorgan.com/nam/en/insights/markets-and-investing/ideas-and-insights/the-midterms-can-change-spending-but-not-americas-fiscal-path">The Midterms can change spending, but not America’s fiscal ...</a></li>
<li><a href="https://am.jpmorgan.com/wr/en/asset-management/institutional/insights/market-insights/market-updates/on-the-minds-of-investors/us-midterm-elections-2026-divided-government/">US midterm elections: More of the same, for now</a></li>

</ul>
</details>

**Tags**: `#US Treasury yields`, `#US midterm elections`, `#oil prices`, `#fiscal policy`, `#market reaction`

---