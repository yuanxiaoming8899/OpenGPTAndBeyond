<div class="Box-sc-g0xbh4-0 bJMeLZ js-snippet-clipboard-copy-unpositioned" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开源 ChatGPT 及其他</font></font></h1><a id="user-content-open-source-chatgpt-and-beyond" class="anchor" aria-label="永久链接：开源 ChatGPT 及其他" href="#open-source-chatgpt-and-beyond"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">致力于实现类似 ChatGPT 的开源模型及其他模型。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自从 LLaMA 模型权重意外泄漏，以及斯坦福羊驼 (Stanford Alpaca 使用 GPT-3 api 生成的数据和自指导技术在 LLaMA 上进行训练) 的令人印象深刻的性能以来，开源社区对 LLaMA 的光明前景感到兴奋。以开放的方式再现ChatGPT。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本存储库旨在记录此过程，并提供如何参与的概述。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包括：基础模型、技术、数据、领域模型、训练管道、加速技术、多语言、多模式等等。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">感谢</font></font><a href="https://github.com/FunnySaltyFish"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@FunnySaltyFish</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供</font></font><a href="https://llm.best/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">网站版本</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这是</font></font><a href="https://github.com/FunnySaltyFish/best_llm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">感谢对此项目和网站的任何贡献！ （我们缺人手……）</font></font></p>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">目录</font></font></h1><a id="user-content-table-of-contents" class="anchor" aria-label="固定链接：目录" href="#table-of-contents"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li><a href="#base-models"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础型号</font></font></a></li>
<li><a href="#domain-models"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">领域模型</font></font></a></li>
<li><a href="#general-domain-instruction-models"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通用领域指令模型</font></font></a></li>
<li><a href="#model-merging"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型合并</font></font></a></li>
<li><a href="#alternatives-to-transformer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变压器的替代品</font></font></a></li>
<li><a href="#multi-modal"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多式联运</font></font></a></li>
<li><a href="#moe"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">教育部</font></font></a></li>
<li><a href="#data"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据  </font></font></a>
<ul dir="auto">
<li><a href="#pretrain-data"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">预训练数据</font></font></a></li>
<li><a href="#instruction-data"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令数据</font></font></a></li>
<li><a href="#synthetic-data-generation"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">综合数据生成</font></font></a></li>
</ul>
</li>
<li><a href="#evaluation"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">评估</font></font></a>
<ul dir="auto">
<li><a href="#enchmark"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基准</font></font></a></li>
<li><a href="#leaderboard"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">排行榜</font></font></a></li>
</ul>
</li>
<li><a href="#frameworktoolkitplatform"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">框架/工具包/平台</font></font></a></li>
<li><a href="#alignment"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结盟</font></font></a></li>
<li><a href="#multi-language"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多语言</font></font></a>
<ul dir="auto">
<li><a href="#vocabulary-expansion"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">词汇扩展</font></font></a></li>
</ul>
</li>
<li><a href="#efficient-trainingfine-tuning"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高效训练/微调</font></font></a></li>
<li><a href="#low-cost-inference"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">低成本推理</font></font></a>
<ul dir="auto">
<li><a href="#quantization"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">量化</font></font></a></li>
<li><a href="#projects"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></a></li>
<li><a href="#prompt-compression"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即时压缩</font></font></a></li>
</ul>
</li>
<li><a href="#prompting"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提示</font></font></a></li>
<li><a href="#safety"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安全</font></font></a></li>
<li><a href="#truthfulness"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">诚实</font></font></a></li>
<li><a href="#exceeding-context-window"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超出上下文窗口</font></font></a></li>
<li><a href="#knowledge-editing"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知识编辑</font></font></a>
<ul dir="auto">
<li><a href="#implementations"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实施</font></font></a></li>
</ul>
</li>
<li><a href="#external-knowledge"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">外部知识</font></font></a>
<ul dir="auto">
<li><a href="/SunLemuria/OpenGPTAndBeyond/blob/main/chat-with-docs"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与文档聊天</font></font></a></li>
<li><a href="/SunLemuria/OpenGPTAndBeyond/blob/main/vector-database"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">矢量数据库</font></font></a></li>
</ul>
</li>
<li><a href="#external-tools"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">外部工具</font></font></a>
<ul dir="auto">
<li><a href="/SunLemuria/OpenGPTAndBeyond/blob/main/using-existing-tools"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用现有工具</font></font></a></li>
<li><a href="/SunLemuria/OpenGPTAndBeyond/blob/main/make-new-tools"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">制作新工具</font></font></a></li>
</ul>
</li>
<li><a href="#agent"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代理人</font></font></a></li>
<li><a href="#llms-as-xxx"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士 XXX</font></font></a></li>
<li><a href="#similar-collections"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类似系列</font></font></a></li>
</ul>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础型号</font></font></h1><a id="user-content-base-models" class="anchor" aria-label="永久链接：基本模型" href="#base-models"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型/项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">执照</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元</font></font></td>
<td><a href="https://github.com/facebookresearch/llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/骆驼2</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA-13B 优于 GPT-3(175B)，LLaMA-65B 与 PaLM-540M 具有竞争力。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大多数后续作品的基础模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱脸-大科学</font></font></td>
<td><a href="https://huggingface.co/bigscience/bloom" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">盛开</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由 HuggingFace BigScience 训练的自回归大型语言模型 (LLM)。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱脸-大科学</font></font></td>
<td><a href="https://huggingface.co/bigscience/bloomz" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆兹</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">针对跨语言任务混合的 BLOOM 和 mT5 预训练多语言语言模型的指令微调版本。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">埃鲁瑟人工智能</font></font></td>
<td><a href="https://huggingface.co/EleutherAI/gpt-j-6b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-J</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 Ben Wang 的</font></font><a href="https://github.com/kingoflolz/mesh-transformer-jax/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mesh Transformer JAX</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">训练的 Transformer 模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元</font></font></td>
<td><a href="https://huggingface.co/facebook/opt-66b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">选择</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Open Pre-trained Transformer Language Models 开发这套 OPT 模型的目的是实现</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大规模的可重复且负责任的研究，并在研究这些法学硕士的影响方面带来更多的声音。</font></font></td>
</tr>
<tr>
<td><a href="https://www.cerebras.net/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大脑系统公司</font></font></a></td>
<td><a href="https://huggingface.co/cerebras/Cerebras-GPT-13B" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Cerebras-GPT</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">预训练的 LLM、GPT-3 等，可商用，在</font></font><a href="https://www.cerebras.net/andromeda/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Andromeda</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> AI 超级计算机上进行有效训练，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据</font><font style="vertical-align: inherit;">计算最优的</font></font><a href="https://arxiv.org/abs/2203.15556" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Chinchilla 缩放定律（每个模型参数 20 个令牌）进行训练。</font></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">埃鲁瑟人工智能</font></font></td>
<td><a href="https://github.com/EleutherAI/pythia"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">皮提亚</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结合可解释性分析和缩放定律来了解知识</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在自回归变压器训练期间如何发展和演变。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稳定性-AI</font></font></td>
<td><a href="https://github.com/Stability-AI/StableLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稳定LM</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稳定性人工智能语言模型</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">佛得角</font></font></td>
<td><a href="https://github.com/OpenLMLab/MOSS"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">苔藓</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">复旦大学开源工具增强会话语言模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对称性和 FDU</font></font></td>
<td><a href="https://bbt.ssymmetry.com/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BBT-2</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">12B 开源LM。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@mlfoundations</font></font></td>
<td><a href="https://github.com/mlfoundations/open_flamingo"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放火烈鸟</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于训练大型多模式模型的开源框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">埃鲁瑟人工智能</font></font></td>
<td><a href="https://huggingface.co/EleutherAI/gpt-neox-20b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-NeoX-20B</font></font></a></td>
<td></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其架构有意类似于 GPT-3，并且与</font></font><a href="https://huggingface.co/EleutherAI/gpt-j-6B" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-J-6B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">几乎相同。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/openlm-research/open_llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA 的公开复制品。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">马赛克ML</font></font></td>
<td><a href="https://github.com/mosaicml/llm-foundry"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MPT-7B 是 GPT 风格的模型，也是 MosaicML 基础系列模型中的第一个模型。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MPT-7B 在 MosaicML 策划的数据集的 1T 代币上进行训练，是开源的、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可商业使用的，并且在评估指标上与 LLaMa 7B 相当。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起电脑</font></font></td>
<td><a href="https://huggingface.co/togethercomputer/RedPajama-INCITE-Base-3B-v1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">红色睡衣-INCITE-Base-3B-v1</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2.8B 参数预训练语言模型，在</font></font><a href="https://huggingface.co/models?dataset=dataset:togethercomputer/RedPajama-Data-1T" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RedPajama-Data-1T</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上预训练，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以及&nbsp;</font></font><a href="https://huggingface.co/togethercomputer/RedPajama-INCITE-Instruct-3B-v1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令调整版本</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;和</font></font><a href="https://huggingface.co/togethercomputer/RedPajama-INCITE-Chat-3B-v1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天版本</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">闪电AI</font></font></td>
<td><a href="https://github.com/Lightning-AI/lit-llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">利特-美洲驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/facebookresearch/llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的独立实现，在</font><strong><font style="vertical-align: inherit;">Apache 2.0 许可证</font></strong><font style="vertical-align: inherit;">下完全开源。</font></font><strong><font style="vertical-align: inherit;"></font></strong></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@概念思维</font></font></td>
<td><a href="https://github.com/conceptofmind/PaLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">棕榈</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省理工学院许可证</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Google PaLM 模型的开源实现。</font></font></td>
</tr>
<tr>
<td><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII</font></font></a></td>
<td><a href="https://huggingface.co/tiiuae/falcon-7b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">猎鹰7B</font></font></a></td>
<td><a href="https://huggingface.co/tiiuae/falcon-7b/blob/main/LICENSE.txt" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII Falcon 法学硕士许可证</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由TII</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建的 7B 参数因果解码器模型，并在</font></font><a href="https://huggingface.co/datasets/tiiuae/falcon-refinedweb" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RefinedWeb</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的 1,500B 令牌上进行训练，</font><font style="vertical-align: inherit;">并使用精选语料库进行了增强。</font></font></td>
</tr>
<tr>
<td><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII</font></font></a></td>
<td><a href="https://huggingface.co/tiiuae/falcon-40b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">猎鹰40B</font></font></a></td>
<td><a href="https://huggingface.co/tiiuae/falcon-7b/blob/main/LICENSE.txt" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII Falcon 法学硕士许可证</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由TII</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建的 40B 参数因果解码器模型，</font><font style="vertical-align: inherit;">并在</font><font style="vertical-align: inherit;">使用精选语料库增强的</font></font><a href="https://huggingface.co/datasets/tiiuae/falcon-refinedweb" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RefinedWeb的 1,000B 令牌上进行训练。</font></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">老虎研究公司</font></font></td>
<td><a href="https://github.com/TigerResearch/TigerBot"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">老虎机器人</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多语言和多任务法学硕士。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巴艾</font></font></td>
<td><a href="https://github.com/FlagAI-Open/FlagAI/tree/master/examples/Aquila"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">天鹰座</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;/&nbsp;</font></font><a href="https://github.com/FlagAI-Open/Aquila2"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">天鹰座2</font></font></a></td>
<td><a href="https://github.com/FlagAI-Open/FlagAI/blob/master/BAAI_Aquila_Model_License.pdf"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BAAI_Aquila_Model_License</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Aquila语言模型继承了GPT-3和LLaMA的架构设计优势，替换了一批更高效的底层</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">算子实现，并重新设计了中英双语支持的分词器。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放BMB</font></font></td>
<td><a href="https://github.com/OpenBMB/CPM-Bee"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CPM-蜜蜂</font></font></a></td>
<td><a href="https://github.com/OpenBMB/General-Model-License/blob/main/%E9%80%9A%E7%94%A8%E6%A8%A1%E5%9E%8B%E8%AE%B8%E5%8F%AF%E5%8D%8F%E8%AE%AE-%E6%9D%A5%E6%BA%90%E8%AF%B4%E6%98%8E-%E5%AE%A3%E4%BC%A0%E9%99%90%E5%88%B6-%E5%95%86%E4%B8%9A%E6%8E%88%E6%9D%83.md"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通用模型许可协议-来源说明-宣传限制-商业授权</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CPM-Bee</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是完全开源、可商用的中英双语基础模型，参数容量达百亿级。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且已经在万亿级代币的广泛语料库上进行了预训练。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">百川</font></font></td>
<td><a href="https://github.com/baichuan-inc/baichuan-7B"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">百川7B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在标准中英文权威基准测试（C-EVAL、MMLU等）</font><font style="vertical-align: inherit;">上取得了同尺寸模型中最好的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">腾讯</font></font></td>
<td><a href="https://huggingface.co/TMElyralab/lyraChatGLM" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">lyraChatGLM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省理工学院许可证</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">据我们所知，这是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ChatGLM-6B 的第一个加速版本</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">lyraChatGLM的推理速度</font><font style="vertical-align: inherit;">较早期原始版本实现了</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">300倍的</font></font></strong><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加速。我们仍在努力进一步提高性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">销售队伍</font></font></td>
<td><a href="https://github.com/salesforce/xgen"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">XGen</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Salesforce 开源法学硕士，序列长度为 8k</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海人工智能实验室</font></font></td>
<td><a href="https://github.com/InternLM/InternLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实习生LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">InternLM开源了70亿参数的基础模型和针对实际场景量身定制的聊天模型。该模型具有以下特点：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">利用数万亿优质代币进行训练，建立强大的知识库。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它支持8k上下文窗口长度，可实现更长的输入序列和更强的推理能力。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它提供了一个多功能的工具集，供用户灵活地构建自己的工作流程。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">xverse-ai</font></font></td>
<td><a href="https://github.com/xverse-ai"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">XVERSE</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">XVERSE Technology Inc. 开发的多语言法学硕士</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作家</font></font></td>
<td><a href="https://huggingface.co/Writer/palmyra-base" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巴尔米拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">极其强大，同时速度极快。该模型擅长许多细致入微的任务</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，例如情感分类和摘要。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">米斯特拉尔人工智能</font></font></td>
<td><a href="https://huggingface.co/mistralai/Mistral-7B-v0.1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">米斯特拉尔</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mistral 7B 是一个 7.3B 参数模型，它：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1. 在所有基准测试中优于 Llama 2 13B </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2. 在许多基准测试中优于 Llama 1 34B </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3. 接近 CodeLlama 7B 的代码性能，同时在英语任务上保持良好状态</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">4. 使用分组查询注意力(GQA) 实现更快的推理</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">5. 使用滑动窗口注意 (SWA) 以更小的成本处理更长的序列</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">天工人工智能</font></font></td>
<td><a href="https://github.com/SkyworkAI/Skywork"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">思凯沃</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在主要评测基准中，Skywork-13B处于中国开源模型的前列，是相同参数尺度下的最优水平；</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需申请即可商用；它还开源了600G（1500亿代币）的中文数据集。</font></font></td>
</tr>
<tr>
<td><a href="https://01.ai/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">01.人工智能</font></font></a></td>
<td><a href="https://github.com/01-ai/Yi"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">义</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Yi系列模型是由</font><a href="https://01.ai/" rel="nofollow"><font style="vertical-align: inherit;">01.AI</font></a></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开发人员从头开始训练的大型语言模型</font><font style="vertical-align: inherit;">。</font></font><a href="https://01.ai/" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">IEIT系统</font></font></td>
<td><a href="https://github.com/IEIT-Yuan/Yuan-2.0"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元-2.0</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这项工作中，引入了基于局部过滤的注意力（LFA），将自然语言局部依赖性的先验知识纳入注意力中。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于LFA，我们开发并发布了参数范围从21亿到1026亿的大型语言模型Yuan 2.0。提出了</font><font style="vertical-align: inherit;">一种数据过滤和生成方法</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来构建高质量的预训练和微调数据集。提出了非均匀管道并行、数据并行、优化器并行的分布式训练方法，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大大降低了节点内通信的带宽需求，在大规模分布式训练中取得了良好的性能。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与现有模型相比，Yuan 2.0 模型在代码生成、数学问题解决和聊天方面表现出了令人印象深刻的能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">南贝格</font></font></td>
<td><a href="https://github.com/Nanbeige/Nanbeige"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">南贝格</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿帕奇-2.0</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Nanbeige-16B是Nanbeige LLM实验室开发的160亿参数语言模型。它使用 2.5T Token 进行预训练。训练数据包括大量优质互联网语料、各类书籍、代码等，在各种权威评测数据集上取得了良好的效果。此版本包括 Base、Chat、Base-32k 和 Chat-32k。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Deepseek-ai</font></font></td>
<td><a href="https://github.com/deepseek-ai/deepseek-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省理工学院许可证</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包含 670 亿个参数的高级语言模型。它是在包含 2 万亿个英文和中文标记的庞大数据集上从头开始训练的。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士360</font></font></td>
<td><a href="https://github.com/LLM360"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士360</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大多数开源法学硕士版本都包含模型权重和评估结果。然而，通常需要额外的信息才能真正理解模型的行为，而大多数研究人员通常无法获得这些信息。因此，我们承诺发布训练期间收集的所有中间检查点（最多 360 个！）、所有训练数据（及其到检查点的映射）、所有收集的指标（例如损失、梯度范数、评估结果）以及用于预处理数据和模型训练的所有源代码。这些额外的工件可以帮助研究人员和从业者更深入地了解LLM的构建过程并进行分析模型动力学等研究。我们希望LLM360能够帮助高级法学硕士更加透明，促进小规模实验室的研究，并提高人工智能研究的可重复性。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">福州大学等</font></font></td>
<td><a href="https://github.com/Chinese-Tiny-LLM/Chinese-Tiny-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中文/英文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">专注于中文。 CT-LLM从零开始，主要使用1.2万亿个token语料库中的中文数据，其中中文8000亿个，英语3000亿个，代码token1000亿个。通过开源CT-LLM的训练流程，包括数据处理和大规模适当预训练中文语料库（MAP-CC），并引入中文硬例基准（CHC-Bench），我们鼓励进一步的研究和创新，旨在更具包容性和适应性强的语言模型。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">领域模型</font></font></h1><a id="user-content-domain-models" class="anchor" aria-label="永久链接：领域模型" href="#domain-models"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">领域</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础模型</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">德克萨斯大学西南分校/</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">伊利诺伊大学香槟分校/俄勒冈州立大学/HDU</font></font></td>
<td><a href="https://github.com/Kent0n-Li/ChatDoctor"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天医生</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也许是第一个在 LLaMA 上调整的特定领域聊天模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">剑桥</font></font></td>
<td><a href="https://github.com/cambridgeltl/visual-med-alpaca"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">视觉医学-羊驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生物医学</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">专为生物医学领域设计的多模态基础模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">打</font></font></td>
<td><a href="https://github.com/SCIR-HI/Huatuo-Llama-Med-Chinese"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BenTsao</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> &nbsp;/&nbsp; </font></font><a href="https://github.com/SCIR-HI/Med-ChatGLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ChatGLM-Med</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/ChatGLM</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用gpt3.5 api生成的中医知识数据集进行微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海科技大学等</font></font></td>
<td><a href="https://github.com/xionghonglin/DoctorGLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">博士GLM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ChatGLM-6B 上微调的中文医疗咨询模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四航空</font></font></td>
<td><a href="https://github.com/BioFM/OpenBioMed"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生物医学GPT-1.6B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生物医学</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">具有 1.6B 参数的预训练多模态分子基础模型，可将 2D 分子图与文本相关联。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@刘HC0428</font></font></td>
<td><a href="https://github.com/LiuHC0428/LAW-GPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LawGPT_zh</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合法的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国法律领域的通用模型，通过可靠自我指令生成的数据进行训练。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海交通大学</font></font></td>
<td><a href="https://github.com/MediaBrain-SJTU/MedicalGPT-zh"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医学GPT-zh</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中医领域的通用模型，自指导生成的多样化数据。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海交通大学</font></font></td>
<td><a href="https://github.com/chaoyi-wu/PMC-LLaMA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PMC-美洲驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">继续对 LLaMA 进行医学论文培训。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">抱脸</font></font></td>
<td><a href="https://github.com/bigcode-project/starcoder"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">星码器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在源代码和自然语言文本上训练的语言模型（LM）。其训练数据包含 80 多种</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不同的编程语言以及从 GitHub 问题和提交以及笔记本中提取的文本。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@CogStack</font></font></td>
<td><a href="https://github.com/CogStack/opengpt#nhs-llm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NHS法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不清楚</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/CogStack/opengpt"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用OpenGPT</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">训练的医疗保健对话模型</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@pengxiao-song</font></font></td>
<td><a href="https://github.com/pengxiao-song/LaWGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉维格PT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合法的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/ChatGLM</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用中文法律术语扩展词汇，根据自学生成的数据对教学进行微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">杜小曼</font></font></td>
<td><a href="https://github.com/Duxiaoman-DI/XuanYuan"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轩辕</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆-176B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">千亿参数的中国大型金融聊天模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港中文大学</font></font></td>
<td><a href="https://github.com/FreedomIntelligence/HuatuoGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华佗GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不清楚</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HuatuoGPT，一个在庞大的中文医学语料库上训练的大型语言模型（LLM）。我们与HuatuoGPT的目标是</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为医疗咨询场景构建一个更专业的“ChatGPT”。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学</font></font></td>
<td><a href="https://github.com/AndrewZhe/lawyer-llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆马律师</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合法的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">继续进行中国法律数据预培训、法律考试指导和法律咨询问答对。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/CSHaitao/LexiLaw"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法律法律</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合法的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/LianjiaTech/BELLE"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对一般数据 ( BELLE</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 1.5M) 和法律数据</font><font style="vertical-align: inherit;">的混合进行训练</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四等</font></font></td>
<td><a href="https://github.com/blcuicall/taoli"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">桃李</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">教育</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">国际汉语教育的大型典范。它在基本模型上扩展了特定词汇，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并使用该领域的专有数据集进行指令微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新加坡国立大学</font></font></td>
<td><a href="https://github.com/liutiedong/goat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">山羊</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">算术</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">经过微调的 LLaMA 模型，在一系列算术任务上显着优于 GPT-4。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Goat 在综合生成的数据集上进行了微调，在 BIG-bench 算术子任务上实现了最先进的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">纽约大学/纽约大学</font></font></td>
<td><a href="https://github.com/AI4Finance-Foundation/FinGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">芬GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融大语言模型 (FinLLM) 的端到端开源框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/nlpxucan/WizardLM/tree/main/WizardCoder"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">向导编码器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">星码器</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">78k</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进化代码指令进行训练。</font><font style="vertical-align: inherit;">在</font><a href="https://github.com/openai/human-eval"><font style="vertical-align: inherit;">HumanEval 基准测试</font></a><font style="vertical-align: inherit;">中超过了  </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Claude-Plus (+6.8)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Bard (+15.3)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">InstructCodeT5+ (+22.3)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><a href="https://github.com/openai/human-eval"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国科学院大学</font></font></td>
<td><a href="https://github.com/jerry1993-tech/Cornucopia-LLaMA-Fin-Chinese"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聚宝盆</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微调LLaMA中国金融知识，</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学</font></font></td>
<td><a href="https://github.com/PKU-YuanGroup/ChatLaw"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天法</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合法的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><a href="https://huggingface.co/IDEA-CCNL/Ziya-LLaMA-13B-Pretrain-v1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子牙</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;/&nbsp;</font></font><a href="https://github.com/lyogavin/Anima"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿尼玛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国法律域名模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@迈克尔-wzhu</font></font></td>
<td><a href="https://github.com/michael-wzhu/ChatMed"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天医学</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于LLaMA-7B的中国医学法学硕士。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华南理工大学</font></font></td>
<td><a href="https://github.com/scutcyr/SoulChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">灵魂聊天</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">精神健康</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">心理健康领域中文对话法学硕士，基于ChatGLM-6B。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@shibing624</font></font></td>
<td><a href="https://github.com/shibing624/MedicalGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">医疗的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 ChatGPT 训练管道训练您自己的医疗 GPT 模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京交通大学</font></font></td>
<td><a href="https://github.com/DUOMO/TransGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">转GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运输</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国交通模式。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巴艾</font></font></td>
<td><a href="https://github.com/FlagAI-Open/FlagAI/tree/master/examples/Aquila/Aquila-code"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">天鹰法典</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">天鹰座</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AquilaCode-multi是一个多语言模型，支持多种编程语言的高精度代码生成，包括Python/C++/Java/Javascript/Go等。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在HumanEval（Python）评估中取得了骄人的成绩，通过@1 、Pass@10 和 Pass@100 分数分别为 26/45.7/71.6。在HumanEval-X</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多语言代码生成评估中，它显着优于具有相似参数的其他开源模型（截至2023年7月19日）。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一方面，AquilaCode-py 是该模型的单语言 Python 版本，专注于 Python 代码生成。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它还在HumanEval评估中表现出色，Pass@1、Pass@10和Pass@100得分为28.8/50.6/76.9（截至2023年7月19日）。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元</font></font></td>
<td><a href="https://github.com/facebookresearch/codellama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛-2</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/facebookresearch/llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于Llama 2</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的一系列大型代码语言模型，在开放模型、填充功能、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对大型输入上下文的支持以及编程任务的零样本指令跟踪能力中</font><font style="vertical-align: inherit;">提供最先进的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新南威尔士大学等</font></font></td>
<td><a href="https://github.com/MasterAI-EAM/Darwin"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">达尔文</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自然科学</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一个自然科学开源法学硕士，主要领域为物理、化学和材料科学。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/Alibaba-NLP/EcomGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生态GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">电子商务</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆兹</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于电子商务的指令调整大型语言模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">老虎人工智能实验室</font></font></td>
<td><a href="https://github.com/TIGER-AI-Lab/MAmmoTH"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">长毛象</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数学</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA2/代码LLaMA</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一系列专为解决一般数学问题而定制的开源大型语言模型 (LLM)。 MAmmoTH 模型在 MathInstruct 上进行训练，MathInstruct</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个精心策划的轻量级且可推广的指令调整数据集。 MathInstruct 由 13 个数学原理数据集编译而成，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中 6 个数据集是本工作新整理的。它独特地关注思想链（CoT）和思想计划（PoT）原理的混合使用，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并确保广泛覆盖不同的数学领域。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海交通大学</font></font></td>
<td><a href="https://github.com/GAIR-NLP/abel"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿贝尔</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数学</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛2</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们提出</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">家长监督</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">*，一种</font><font style="vertical-align: inherit;">监督微调的</font></font><em><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">保姆策略</font></font></strong></em><font style="vertical-align: inherit;"></font><code>Parental Oversight</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，不限于任何特定的数据处理方法。相反，它定义了数据处理哲学，应该指导生成式人工智能（GAI）时代的监督微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">佛得角</font></font></td>
<td><a href="https://github.com/FudanDISC/DISC-LawLLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DISC法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合法的</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">百川13B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">复旦DISC发布大语言模型驱动的中文智能法律系统DISC-LawLLM。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">系统可以为不同的用户群体提供多种法律服务。此外，构建DISC-Law-Eval是为了从客观和主观两个方面评估大型法律语言模型。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该模型与现有的大型法律模型相比具有明显的优势。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该团队还提供了 300,000 个高质量的监督微调 (SFT) 数据集 DISC-Law-SFT。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港大学等</font></font></td>
<td><a href="https://github.com/EmoCareAI/ChatPsychiatrist"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天精神科医生</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">精神健康</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该存储库开源了经过指令调整的 LLaMA-7B 模型，该模型已使用咨询领域指令数据进行了微调。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了构建 8K 大小的指令调整数据集，我们收集了真实世界的咨询对话示例，并使用 GPT-4 作为提取器和过滤器。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，我们还引入了一套全面的指标，通过纳入咨询领域评估标准，专门针对法学硕士+咨询领域量身定制。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这些指标可以评估生成涉及多维咨询技能的语言内容的表现。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中科院</font></font></td>
<td><a href="https://wisemodel.cn/models/LiYuYang/StarWhisper" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">星语</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">天文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大型天文模型StarWhisper通过专家标注的天体物理语料库的微调、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">逻辑长文本训练以及直接偏好优化，显着提高了模型的推理逻辑和完整性。在科圭AI研究院与LanguageX AI Lab联合发布的CG-Eval中，其整体排名第二，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅低于GPT-4，数学推理和天文能力接近或超过GPT 3.5 Turbo。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">智普爱</font></font></td>
<td><a href="https://github.com/MetaGLM/FinGLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">芬GLM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SMP2023-ELMFT（金融科技大模型评估）解决方案。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学等</font></font></td>
<td><a href="https://github.com/WisdomShell/codeshell"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码外壳</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"></font><a href="http://se.pku.edu.cn/kcl/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CodeShell是北京大学知识计算实验室</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与四川天府银行AI团队</font><font style="vertical-align: inherit;">联合开发的代码大语言模型（LLM） 。 </font><font style="vertical-align: inherit;">CodeShell 拥有 70 亿个参数，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">接受过 5000 亿个 token 的训练，上下文窗口长度为 8192。在权威代码评估基准（HumanEval 和 MBPP）上，CodeShell 在其规模的模型中实现了最佳性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">佛得角</font></font></td>
<td><a href="https://github.com/FudanDISC/DISC-FinLLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DISC金融法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">百川-13B-聊天</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DISC-FinLLM是金融领域的大型语言模型。它是针对不同金融场景，由金融咨询、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">金融文本分析、金融计算、金融知识检索与问答</font><font style="vertical-align: inherit;">四大模块组成的多专家智能金融系统。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深度搜索</font></font></td>
<td><a href="https://huggingface.co/deepseek-ai/deepseek-coder-33b-instruct" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深度搜索编码器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Deepseek Coder 包含一系列代码语言模型，这些模型在 87% 的代码和 13% 的英语和中文自然语言上进行了训练，每个模型都在 2T 令牌上进行了预训练。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在编码能力方面，Deepseek Coder 在多种编程语言和各种基准测试的开源代码模型中实现了最先进的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/MathOctopus"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数学章鱼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数学</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛2</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这项工作开创了探索和建立强大的多语言数学推理 (xMR) 法学硕士的先河。为了实现这一目标，我们做了以下工作：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1.&nbsp; </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MGSM8KInstruct</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，第一个多语言数学推理指令数据集，包含十种不同的语言，从而解决 xMR 任务中训练数据稀缺的问题。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2.&nbsp; </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MSVAMP</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，域外xMR测试数据集，对模型的多语言数学能力进行更详尽、更全面的评估。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3.&nbsp; </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MathOctopus</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，我们有效的多语言数学推理法学硕士，采用不同的策略进行训练，其性能明显优于传统的开源法学硕士，并在少量场景中表现出优于 ChatGPT 的优势。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">信息技术研究中心</font></font></td>
<td><a href="https://github.com/ITRECLab/Zh-MT-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">海上</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM3-6b</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">训练数据使用分为三个主要部分的海事领域数据 Zh-mt-sft 和 30w 个通用对话数据</font></font><a href="https://huggingface.co/datasets/fnlp/moss-003-sft-data" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">moss-003-sft-data</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。 zh-mt-sft具体包含与海事法律法规相关的CrimeKgAssitant-1.8w、Zh-law-qa、Zh-law-court等与海事教育培训相关的Zh-edu-qa、Zh-edu-qb，和Zh-mt-qa涉及海事专业知识问答。</font></font></td>
</tr>
</tbody>
</table>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一些医学模型：</font></font><a href="https://mp.weixin.qq.com/s/c6aPU2FALAaa4LWKQ8W1uA" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里</font></font></a></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一些领域的LLM：</font></font><a href="https://github.com/luban-agi/Awesome-Domain-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Awesome-Domain-LLM</font></font></a></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">治疗模型：</font></font><a href="https://github.com/Jianing-Qiu/Awesome-Healthcare-Foundation-Models"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Awesome-Healthcare-Foundation-Models</font></font></a></p>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通用领域指令模型</font></font></h1><a id="user-content-general-domain-instruction-models" class="anchor" aria-label="永久链接：通用领域指令模型" href="#general-domain-instruction-models"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型/项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础模型</font></font></th>
<th align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td align="left"><a href="https://github.com/tatsu-lab/stanford_alpaca"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">羊驼毛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/选择</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 Self-Instructt 技术生成的 52K 指令跟踪数据来微调 7B LLaMA，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所得模型 Alpaca 的行为与</font></font><code>text-davinci-003</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Self-Instruct 指令跟踪评估套件上的模型类似。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">羊驼毛启发了许多后续款式。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">链嘉科技</font></font></td>
<td align="left"><a href="https://github.com/LianjiaTech/BELLE"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">美女</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BLOOMZ-7B1-mt</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也许是第一个效仿羊驼的中国模特。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td align="left"><a href="https://github.com/THUDM/ChatGLM-6B"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国知名模特。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据块</font></font></td>
<td align="left"><a href="https://github.com/databrickslabs/dolly"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多莉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-J 6B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用羊驼数据来微调一个 2 年前的模型：GPT-J，该模型表现出令人惊讶的高质量</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令遵循行为，而不是其所基于的基础模型的特征。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@tloen</font></font></td>
<td align="left"><a href="https://github.com/tloen/alpaca-lora"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">羊驼-LoRA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在单个 RTX 4090 上进行数小时内的训练，</font><font style="vertical-align: inherit;">使用</font><a href="https://arxiv.org/pdf/2106.09685.pdf" rel="nofollow"><font style="vertical-align: inherit;">低秩适应 (LoRA)</font></a></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重现&nbsp;</font></font><a href="https://github.com/tatsu-lab/stanford_alpaca"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福羊驼</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结果，</font><font style="vertical-align: inherit;">并且可以在 Raspberry pi 上运行。</font></font><a href="https://arxiv.org/pdf/2106.09685.pdf" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巨型人工智能</font></font></td>
<td align="left"><a href="/SunLemuria/OpenGPTAndBeyond/blob/main"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浣熊7B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ColossalChat 项目开发的大型语言模型</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海人工智能实验室</font></font></td>
<td align="left"><a href="https://github.com/ZrrSkywalker/LLaMA-Adapter"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA 适配器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微调 LLaMA 以在 1 小时内遵循指令并使用 1.2M 参数</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以太皮质</font></font></td>
<td align="left"><a href="https://github.com/AetherCortex/Llama-X"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">美洲驼-X</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关于将 LLaMA 提高到 SOTA LLM 的开放学术研究。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起电脑</font></font></td>
<td align="left"><a href="https://github.com/togethercomputer/OpenChatKit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放聊天工具包</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-NeoX-20B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenChatKit 提供了强大的开源基础，可以为各种应用程序创建专用和通用聊天机器人。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该套件包括一个指令调整的语言模型、一个审核模型和一个可扩展的检索系统，用于包含</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来自自定义存储库的最新响应。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">经济人工智能</font></font></td>
<td align="left"><a href="https://github.com/nomic-ai/gpt4all"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT4All</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对大量干净的助理数据进行训练，包括代码、故事和对话</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ymcui</font></font></td>
<td align="left"><a href="https://github.com/ymcui/Chinese-LLaMA-Alpaca"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国-美洲驼-羊驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA-7B/13B</font></font></td>
<td align="left"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在原LLaMA的基础上扩展中文词汇</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并利用中文数据进行二次预训练，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进一步增强中文基本语义理解。此外，该项目</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在中文LLaMA的基础上使用中文指令数据进行微调，显着提高了模型对指令的理解和执行。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加州大学伯克利</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">分校 斯坦福大学</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CMU</font></font></td>
<td align="left"><a href="https://github.com/lm-sys/FastChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼毛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA-13B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">90% 的 ChatGPT 质量给 GPT-4 留下了深刻的印象。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加州大学圣地亚哥分校/中山大学</font></font></td>
<td align="left"><a href="https://github.com/project-baize/baize"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">白泽</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"></font><a href="https://github.com/microsoft/LoRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用LoRA</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行微调</font><font style="vertical-align: inherit;">。它使用由 ChatGPT 与自身聊天生成的 100k 个对话框。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Alpaca 的数据也用于提高其性能。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加州大学伯克利分校</font></font></td>
<td align="left"><a href="https://github.com/young-geng/EasyLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">考拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该团队并没有</font><font style="vertical-align: inherit;">通过抓取尽可能多的网络数据来最大化</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数量，而是专注于收集小型</font></font></em><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高质量</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据集。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@imClumsyPanda</font></font></td>
<td align="left"><a href="https://github.com/imClumsyPanda/langchain-ChatGLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">langchain-ChatGLM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于本地知识的 ChatGLM 和 langchain。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@yangjianxin1</font></font></td>
<td align="left"><a href="https://github.com/yangjianxin1/Firefly"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">萤火虫</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆-1b4-zh</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆-2b6-zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国数据集的指令调优。采用</font><font style="vertical-align: inherit;">词汇剪枝、ZeRO、张量并行等技术</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，有效降低内存消耗，提高训练效率。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td align="left"><a href="https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-4-法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旨在共享 GPT-4 生成的数据，以构建具有监督学习和强化学习的遵循指令的法学硕士。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">抱脸</font></font></td>
<td align="left"><a href="https://huggingface.co/trl-lib/llama-7b-se-rl-peft" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">堆栈LLaMA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在 StackExchange 数据上进行训练，主要目标是作为</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用 RLHF 训练模型的教程和演练，而不是主要模型性能。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">星云</font></font></td>
<td align="left"><a href="https://github.com/nebuly-ai/nebullvm/tree/main/apps/accelerate/chatllam"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查拉玛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个库，允许您使用自己的数据和尽可能少的计算量创建超个性化的类似 ChatGPT 的助手。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@juncongmoo</font></font></td>
<td align="left"><a href="https://github.com/juncongmoo/chatllama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查拉玛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于 LLaMA 的 RLHF 模型，可在单个 GPU 中运行。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@juncongmoo</font></font></td>
<td align="left"><a href="https://github.com/juncongmoo/minichatgpt"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">迷你聊天室</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT/OPT ...</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 ColossalAI 在 5 分钟内训练 ChatGPT。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@LC1332</font></font></td>
<td align="left"><a href="https://github.com/LC1332/Luotuo-Chinese-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼-中文-法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/ChatGLM</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指导微调的中文语言模型，并提供 colab！</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@法西科</font></font></td>
<td align="left"><a href="https://github.com/Facico/Chinese-Vicuna"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国骆驼毛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于LLaMA的中文指令模型，使用Lora进行微调，支持cpp推理，提供colab。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@yanqiangmiffy</font></font></td>
<td align="left"><a href="https://github.com/yanqiangmiffy/InstructGLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指导GLM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于 ChatGLM 的指令跟踪模型，在各种数据源上进行微调，支持 Deepspeed 加速和 LoRA。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td align="left"><a href="https://github.com/GanjinZero/RRHF"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">袋熊</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提出了一种称为 RRHF 的新颖学习范式，作为 RLHF 的替代方案，该范式对</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不同采样策略生成的响应进行评分，并学习通过排名损失使它们与人类偏好保持一致。并且性能</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与RLHF相当，过程中使用的模型更少。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@吴俊德</font></font></td>
<td align="left"><a href="https://github.com/WuJunde/alpaca-glassoff"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">羊驼毛-格拉索夫</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"></font><a href="https://github.com/tatsu-lab/stanford_alpaca"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于stanford-alpaca</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/tloen/alpaca-lora"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">alpaca-lora</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的迷你图像可接受的聊天 AI 可以在您自己的笔记本电脑上运行</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@JosephusCheung</font></font></td>
<td align="left"><a href="https://huggingface.co/datasets/JosephusCheung/GuanacoDataset" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多语言指令跟随语言模型。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@自由情报</font></font></td>
<td align="left"><a href="https://github.com/FreedomIntelligence/LLMZoo"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士动物园</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆兹/骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个为大型语言模型提供数据、模型和评估基准的项目。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发布型号：凤凰、奇美拉</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深圳大学</font></font></td>
<td align="left"><a href="https://github.com/CVI-SZU/Linly"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">林利</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">扩大中文词汇量</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，全微调模型，基于LLaMA的最大中文模型，聚合中文教学数据，可重现细节..</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@lamini-ai</font></font></td>
<td align="left"><a href="https://github.com/lamini-ai/lamini/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉米尼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据生成器，用于生成指令来训练遵循指令的 LLM。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稳定性-AI</font></font></td>
<td align="left"><a href="https://stability.ai/blog/stablevicuna-open-source-rlhf-chatbot" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">马厩骆驼毛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vicuna v0 13b 的进一步指令微调和 RLHF 训练版本，性能比 Vicuna 更好。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">抱脸</font></font></td>
<td align="left"><a href="https://huggingface.co/chat/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱聊天</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">似乎是第一个可作为类似于 ChatGPT 的平台进行访问的平台。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td align="left"><a href="https://github.com/nlpxucan/WizardLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">向导LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"></font><a href="https://github.com/nlpxucan/evol-instruct"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Evol-Instruct</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">采用 70k 条进化指令进行训练，</font><font style="vertical-align: inherit;">是一种使用 LLM 代替人类自动批量生产</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">各种难度级别和技能范围的开放域指令的新颖方法，以提高 LLM 的性能。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">佛得角</font></font></td>
<td align="left"><a href="https://github.com/OpenLMLab/OpenChineseLLaMA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenChinese骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进一步在中文数据上预训练 LLaMA，提高 LLaMA 在中文任务上的表现。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@chenfeng357</font></font></td>
<td align="left"><a href="https://github.com/chenfeng357/open-Chinese-ChatLLaMA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">open-Chinese-ChatLLaMA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开源Chinese-Llama模型的完整训练代码，包括从预训练指导到RLHF的全流程。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@FSoft-AI4Code</font></font></td>
<td align="left"><a href="https://github.com/FSoft-AI4Code/CodeCapybara"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码水豚</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">遵循代码生成指令调整的开源 LLaMA 模型。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@mbzuai-nlp</font></font></td>
<td align="left"><a href="https://github.com/mbzuai-nlp/LaMini-LM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LaMini-LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA/Flan-T5 ...</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从大规模指令中提取出的多样化模型。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">南洋理工大学</font></font></td>
<td align="left"><a href="https://github.com/dandelionsllm/pandallm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">熊猫</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对中国数据、全尺寸 LLaMA 模型进行进一步预训练。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">IBM/卡内基梅隆大学/麻省理工学院</font></font></td>
<td align="left"><a href="https://github.com/IBM/Dromedary"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单峰骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛-65B</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从头开始以最少的人类监督进行原则驱动的语言模型自我调整。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@melodysdreamj</font></font></td>
<td align="left"><a href="https://github.com/melodysdreamj/WizardVicunaLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巫师骆驼LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼毛</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Wizard的数据集+ChatGPT的对话扩展+Vicuna的调优方法，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">比Vicuna实现约7%的性能提升。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">桑巴诺瓦系统公司</font></font></td>
<td align="left"><a href="https://huggingface.co/sambanovasystems/BLOOMChat-176B-v1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BLOOChat</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">盛开</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BLOOMChat 是一个 1760 亿参数的多语言聊天模型。它是根据</font></font><a href="https://huggingface.co/bigscience/bloom" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BLOOM (176B)</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">助理式对话数据集上调整的指令，支持多种语言的对话、问答和生成答案。</font></font></td>
</tr>
<tr>
<td align="left"><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII</font></font></a></td>
<td align="left"><a href="https://huggingface.co/tiiuae/falcon-7b-instruct" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Falcon-7B-指令</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><a href="https://huggingface.co/tiiuae/falcon-7b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">猎鹰7B</font></font></a></td>
<td align="left"><font style="vertical-align: inherit;"></font><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于</font></font><a href="https://huggingface.co/tiiuae/falcon-7b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Falcon-7B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建的仅 7B 参数因果解码器模型</font><font style="vertical-align: inherit;">，并在聊天/指令数据集的混合上进行了微调。</font></font></td>
</tr>
<tr>
<td align="left"><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII</font></font></a></td>
<td align="left"><a href="https://huggingface.co/tiiuae/falcon-40b-instruct" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Falcon-40B-指导</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><a href="https://huggingface.co/tiiuae/falcon-40b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">猎鹰40B</font></font></a></td>
<td align="left"><font style="vertical-align: inherit;"></font><a href="https://www.tii.ae/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TII</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于</font></font><a href="https://huggingface.co/tiiuae/falcon-40b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Falcon-40B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建的 40B 参数因果解码器模型，并在</font></font><a href="https://github.com/project-baize/baize-chatbot"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Baize</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的混合上进行了微调</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国科学技术大学等</font></font></td>
<td align="left"><a href="https://github.com/OFA-Sys/ExpertLLaMA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">专家骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用上下文学习自动编写定制的专家身份，发现质量相当令人满意。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我们将相应的专家身份添加到每条指令之前，以生成增强的指令跟踪数据。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们将整个框架称为&nbsp;</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ExpertPrompting ，在我们的</font></font></strong><font style="vertical-align: inherit;"></font><a href="https://arxiv.org/abs/2305.14688" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">论文</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中可以找到更多详细信息</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浙江大学</font></font></td>
<td align="left"><a href="https://github.com/zjunlp/CaMA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">钙镁</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在不扩展词汇量的情况下对中文语料库进行进一步预训练；针对信息提取（IE）任务进行了优化。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供预训练脚本，包括大规模语料库的转换、构建和加载，以及LoRA指令微调脚本。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td align="left"><a href="https://github.com/thunlp/UltraChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超聊</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，UltraChat数据集为聊天机器人的训练提供了丰富的资源。其次，通过对LLaMA模型进行微调，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">研究人员成功创建了性能优越的对话模型UltraLLaMA。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国人民大学</font></font></td>
<td align="left"><a href="https://github.com/RUC-GSAI/YuLan-Chat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">玉兰聊天室</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于微调LLaMA开发，具有高质量的英文和中文说明。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">人工智能2</font></font></td>
<td align="left"><a href="https://github.com/allenai/open-instruct"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">图鲁</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/皮提亚/OPT</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一套 LLaMa 模型在强大的数据集组合上进行了全面微调。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">韩国科学技术院</font></font></td>
<td align="left"><a href="https://github.com/kaistAI/SelFee"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自费</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由自我反馈生成支持的迭代自我修订法学硕士。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@lyogavin</font></font></td>
<td align="left"><a href="https://github.com/lyogavin/Anima"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿尼玛</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于 QLoRA 的</font></font><a href="https://huggingface.co/timdettmers/guanaco-33b" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">33B guanaco</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行训练，微调为 10000 步。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td align="left"><a href="https://github.com/THUDM/ChatGLM2-6B"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM2-6B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ChatGLM </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> -6B是开源双语（中英）聊天模型</font></font><a href="https://github.com/THUDM/ChatGLM-6B"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ChatGLM-6B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的第二代版本。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它保留了第一代模型流畅的会话流程和低部署门槛，同时引入了以下新功能：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 更强的性能</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 更长的上下文</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 更高效的推理 - 更开放的许可</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放聊天</font></font></td>
<td align="left"><a href="https://github.com/imoneoi/openchat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放聊天</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛等</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一系列开源语言模型在小型但多样化且高质量的多轮对话数据集上进行了微调。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">具体来说，我们仅利用直接从约 90K ShareGPT 对话中过滤出来的约 6K GPT-4 对话。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管数据集规模较小，OpenLLM 仍表现出了卓越的性能。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中科院</font></font></td>
<td align="left"><a href="https://github.com/ictnlp/BayLing"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贝灵</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BayLing是一名英汉法学硕士，拥有先进的语言对齐能力，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在英汉生成、指令跟随和多轮交互方面表现出卓越的能力。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稳定性ai</font></font></td>
<td align="left"><a href="https://huggingface.co/stabilityai/FreeWilly1-Delta-SafeTensor" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自由威利</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/</font></font><a href="https://huggingface.co/stabilityai/FreeWilly2" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自由威利2</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/骆驼2</font></font></td>
<td align="left"><code>FreeWilly</code><font style="vertical-align: inherit;"></font><a href="https://arxiv.org/pdf/2306.02707.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是在Orca</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">风格数据集上微调的 Llama65B 模型</font><font style="vertical-align: inherit;">。是在</font><a href="https://arxiv.org/pdf/2306.02707.pdf" rel="nofollow"><font style="vertical-align: inherit;">Orca</font></a></font><br><code>FreeWilly2</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">风格数据集上微调的 Llama2 70B 模型</font><font style="vertical-align: inherit;">。在</font><a href="https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard" rel="nofollow"><font style="vertical-align: inherit;">Huggingface Open LLM 排行榜</font></a><font style="vertical-align: inherit;">&nbsp;上优于 Llama2 70B </font><font style="vertical-align: inherit;">。</font></font><a href="https://arxiv.org/pdf/2306.02707.pdf" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><br><code>FreeWilly2</code><font style="vertical-align: inherit;"></font><a href="https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td align="left"><a href="https://github.com/QwenLM/Qwen-7B"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Qwen-7B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里云提出的大语言模型系列Qwen（简称统一前文）的7B参数版本。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浙江大学</font></font></td>
<td align="left"><a href="https://github.com/zjunlp/KnowLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知道LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">随着深度学习技术的快速发展，ChatGPT等大型语言模型在自然语言处理领域取得了长足的进步。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然而，这些扩展模型在获取和理解知识方面仍然遇到一些挑战，包括更新知识的困难以及潜在的知识</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">差异和偏见，统称为</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知识谬误</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">KnowLM项目致力于通过推出开源的大规模知识语言模型框架并发布相应模型来解决这些问题。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">东北大学</font></font></td>
<td align="left"><a href="https://github.com/neukg/TechGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">技术GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TechGPT主要强化了以下三类任务：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 以“知识图谱构建”为核心的关系三元组提取等各类信息抽取任务</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 以“阅读理解”为核心的各类智能问答任务。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 以“文本理解”为核心的关键字生成等各种序列生成任务。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@MiuLab</font></font></td>
<td align="left"><a href="https://github.com/MiuLab/Taiwan-LLaMa"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">台湾-LLaMa</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛2</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">台湾繁体中文法学硕士。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Xwin-LM</font></font></td>
<td align="left"><a href="https://github.com/Xwin-LM/Xwin-LM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Xwin-LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉玛2</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Xwin-LM旨在开发并开源大型语言模型的对齐技术，包括监督微调（SFT）、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奖励模型（RM）、拒绝采样、人类反馈强化学习（RLHF）等。我们的第一个版本，基于 Llama2 基础模型构建</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">在</font><a href="https://tatsu-lab.github.io/alpaca_eval/" rel="nofollow"><font style="vertical-align: inherit;">AlpacaEval上排名</font></a></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TOP-1</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。值得注意的是，它是第一个</font><font style="vertical-align: inherit;">在该基准测试中</font><strong><font style="vertical-align: inherit;">超越 GPT-4 的。</font></strong></font><a href="https://tatsu-lab.github.io/alpaca_eval/" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文格研究</font></font></td>
<td align="left"><a href="https://github.com/wenge-research/YaYi"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雅仪</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/骆驼2</font></font></td>
<td align="left"><a href="https://www.wenge.com/yayi/index.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雅亿</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是在数百万人工构建的高质量领域数据上进行微调的。该训练数据涵盖</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">媒体宣传、舆情分析、公共安全、金融风控、城市治理</font><font style="vertical-align: inherit;">五个重点领域，包含百余个自然语言教学任务。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">抱脸</font></font></td>
<td align="left"><a href="https://huggingface.co/HuggingFaceH4/zephyr-7b-alpha" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和风</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">米斯特拉尔</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Zephyr 是一系列语言模型，经过训练可以充当有用的助手。 Zephyr-7B-α 是该系列中的第一个模型，是</font></font><br><a href="https://huggingface.co/mistralai/Mistral-7B-v0.1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mistralai/Mistral-7B-v0.1</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的微调版本，使用</font></font><a href="https://arxiv.org/abs/2305.18290" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">直接偏好优化 (DPO)</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在公开可用的合成数据集上进行训练</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">连贯</font></font></td>
<td align="left"><a href="https://huggingface.co/CohereForAI/c4ai-command-r-v01" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令-R</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> &nbsp;/&nbsp;</font></font><a href="https://huggingface.co/CohereForAI/c4ai-command-r-plus" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令 R+</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Command-R 具有以 10 种语言评估的多语言生成功能和高性能 RAG 功能。</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">西艾</font></font></td>
<td align="left"><a href="https://github.com/xai-org/grok-1"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">格罗克</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">314B 教育部；上下文长度：8192</font></font></td>
</tr>
<tr>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据块</font></font></td>
<td align="left"><a href="https://huggingface.co/databricks/dbrx-instruct" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">dbrx 指令</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td align="left"><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">细粒度</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">专家混合 (MoE) 架构，共有 132B 个参数，其中 36B 个参数在任何输入上都处于活动状态</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它是在 12T 文本和代码数据标记上进行预训练的。与 Mixtral-8x7B 和 Grok-1 等其他开放 MoE 模型相比，DBRX 是细粒度的，这意味着它使用了更多数量的小型专家。 DBRX 有 16 位专家，选择 4 位，而 Mixtral-8x7B 和 Grok-1 有 8 位专家，选择 2 位。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型合并</font></font></h1><a id="user-content-model-merging" class="anchor" aria-label="永久链接：模型合并" href="#model-merging"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型/方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">保险丝人工智能</font></font></td>
<td><a href="https://huggingface.co/FuseAI/FuseChat-7B-VaRM" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">保险丝聊天室</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，它对源LLM进行成对知识融合，通过轻量级微调导出多个具有相同结构和大小的目标LLM。然后，这些目标LLM在参数空间内进行合并，其中我们提出了一种新的方法VaRM，用于根据微调前后参数矩阵的变化率来确定合并权重。</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">三个具有不同架构和规模的著名聊天法学硕士的融合，即</font></font><a href="https://huggingface.co/NousResearch/Nous-Hermes-2-Mixtral-8x7B-DPO" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NH2-Mixtral-8x7B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><a href="https://huggingface.co/NousResearch/Nous-Hermes-2-SOLAR-10.7B" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NH2-Solar-10.7B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://huggingface.co/openchat/openchat_3.5" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenChat-3.5-7B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。 FuseChat-7B-VaRM</font><font style="vertical-align: inherit;">在 MT-Bench 上取得了</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">8.22</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的平均性能，超越了</font></font><a href="https://huggingface.co/berkeley-nest/Starling-LM-7B-alpha" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Starling-7B</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://huggingface.co/01-ai/Yi-34B-Chat" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Yi-34B-Chat</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等各种强大的 7B 和 34B 规模的聊天 LLM ，甚至超过了</font></font><a href="https://platform.openai.com/docs/models/gpt-3-5-turbo" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-3.5 (March)</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><a href="https://www.anthropic.com/news/claude-2-1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Claude-2.1</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、并接近</font></font><a href="https://huggingface.co/mistralai/Mixtral-8x7B-Instruct-v0.1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mixtral-8x7B-Instruct</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿尔西-艾</font></font></td>
<td><a href="https://github.com/arcee-ai/mergekit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合并工具包</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于合并预训练的大型语言模型的工具。</font></font></td>
<td></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">坂奈AI</font></font></td>
<td><a href="https://github.com/SakanaAI/evolutionary-model-merge"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进化法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型合并配方的进化优化。</font></font></td>
<td></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变压器的替代品</font></font></h1><a id="user-content-alternatives-to-transformer" class="anchor" aria-label="永久链接：变压器的替代品" href="#alternatives-to-transformer"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（也许是继任者？）</font></font></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">闪烁DL</font></font></td>
<td><a href="https://github.com/BlinkDL/RWKV-LM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RWKV-LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RWKV 是一种具有 Transformer 级 LLM 性能的 RNN。它可以像 GPT（可并行）一样直接训练。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，它结合了 RNN 和 Transformer 的优点 - 出色的性能、快速推理、节省 VRAM、快速训练、“无限”ctx_len 和免费句子嵌入。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">姆斯拉</font></font></td>
<td><a href="https://arxiv.org/abs/2307.08621" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">视网膜网络</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同时实现训练并行性、低成本推理和良好性能。我们从理论上得出了重复性和注意力之间的联系。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我们提出了序列建模的保留机制，它支持三种计算范式，即并行、循环和分块循环。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">具体来说，并行表示允许训练并行性。循环表示可实现低成本</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">O</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ( </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ) 推理，从而在不牺牲性能的情况下提高解码吞吐量、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">延迟和 GPU 内存。分块循环表示有助于具有线性复杂度的高效长序列建模，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中每个块在循环总结块的同时并行编码。语言建模的实验结果表明，RetNet 取得了良好的扩展效果、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并行训练、低成本部署和高效推理。有趣的特性使 RetNet 成为大型语言模型 Transformer 的有力继承者。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td><a href="https://backpackmodels.science" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包包</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Backpack</font><font style="vertical-align: inherit;">&nbsp;是 Transformer 的直接替代品，它提供了通过控制进行可解释性的新工具，</font></font><a href="https://arxiv.org/abs/2305.16765" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同时</font></font></a><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仍然</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">支持强大的语言模型。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">背包将单词的预测含义分解为与上下文无关的成分，并通过加权和将它们聚合起来，从而实现精确、可预测的干预。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学等</font></font></td>
<td><a href="https://github.com/HazyResearch/m2"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">君主搅拌机 (M2)</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本思想是用 Monarch 矩阵替换 Transformer 的主要元素，Monarch 矩阵是一类概括 FFT 的结构化矩阵，具有次二次性、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">硬件效率高且富有表现力。在 Monarch Mixer 中，我们使用从 Monarch 矩阵构建的层来进行跨序列的混合（替换 Attention 操作）和跨模型维度的混合（替换密集 MLP）。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">卡耐基梅隆大学等</font></font></td>
<td><a href="https://github.com/state-spaces/mamba"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">曼巴</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mamba 是一种新的状态空间模型架构，在信息密集型数据（例如语言建模）上显示出良好的性能，而之前的二次模型在 Transformers 方面存在不足。它基于</font></font><a href="https://github.com/state-spaces/s4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结构化状态空间模型</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的进展，并本着</font></font><a href="https://github.com/Dao-AILab/flash-attention"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FlashAttention</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的精神进行高效的硬件感知设计和实现</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起电脑</font></font></td>
<td><a href="https://github.com/togethercomputer/stripedhyena"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">条纹鬣狗</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">StripedHyena 是第一个</font><font style="vertical-align: inherit;">在短上下文和长上下文评估中</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与类似大小的最佳开源 Transformer 竞争的替代模型。 StripedHyena 是一种混合架构，由排列在</font></font></strong><font style="vertical-align: inherit;"><a href="https://arxiv.org/abs/2302.10866" rel="nofollow"><font style="vertical-align: inherit;">Hyena</font></a></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">块中的多头、分组查询注意力和门控卷积组成</font><font style="vertical-align: inherit;">，与传统的仅解码器 Transformer 不同。</font><font style="vertical-align: inherit;">1. 通过将卷积表示为状态空间模型（模态或规范形式）或截断滤波器，在 Hyena 块中进行恒定内存解码。</font><font style="vertical-align: inherit;">2. 比 Transformer 低延迟、更快的解码和更高的吞吐量。</font><font style="vertical-align: inherit;">3. 与 Llama-2 等优化的 Transformer 架构相比，改进了训练和推理最佳缩放法则。</font><font style="vertical-align: inherit;">4. 对高达 32k 的序列进行训练，使其能够处理更长的提示。</font></font><a href="https://arxiv.org/abs/2302.10866" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/sanderwood/bgpt"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷胱甘肽转移酶</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">bGPT 支持通过对任何类型的数据进行下一个字节预测来进行生成建模，并且可以执行计算机上可执行的任何任务，展示了模拟数字世界中所有活动的能力，其潜力仅受计算资源和我们的想象力的限制。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深度思维</font></font></td>
<td><a href="https://github.com/simudt/Griffin-Jax"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">格里芬-贾克斯</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://arxiv.org/abs/2402.19427" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Griffin: Mixing Gated Linear Recurrences with Local Attention for Efficient Language Models</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的 Jax + Flax 实现</font><font style="vertical-align: inherit;">，非官方代码（官方代码尚未发布）；</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RG-LRU 层，一种新颖的门控线性循环层，围绕它我们设计了一个新的循环块来取代 MQA。我们使用这个循环块构建了两个新模型：Hawk，一种将 MLP 与循环块交错的模型，以及 Griffin，一种混合&ZeroWidthSpace;&ZeroWidthSpace;模型，将 MLP 与循环块和局部注意力的混合交错</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Griffin-3B 优于 Mamba-3B，而 Griffin- 7B 和 Griffin-14B 的性能可与 Llama-2 相媲美，尽管训练的 token 少了近 7 倍；格里芬可以推断出比训练期间看到的长得多的序列。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">人工智能21</font></font></td>
<td><a href="https://huggingface.co/ai21labs/Jamba-v0.1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">詹巴</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Jamba 是第一个生产规模的 Mamba 实施。它是一个预训练的混合专家 (MoE) 生成文本模型，具有 12B 个活动参数和所有专家的总共 52B 个参数。它支持 256K 上下文长度，并且可以在单个 80GB GPU 上容纳多达 140K 令牌。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">教育部</font></font></h1><a id="user-content-moe" class="anchor" aria-label="永久链接：教育部" href="#moe"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型/项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">米斯特拉莱</font></font></td>
<td><a href="https://huggingface.co/mistralai/Mixtral-8x7B-v0.1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">混合-8x7B</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mixtral-8x7B 大型语言模型 (LLM) 是一种预训练的生成式稀疏专家混合模型。在我们测试的大多数基准测试中，Mistral-8x7B 的性能优于 Llama 2 70B。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海人工智能实验室等</font></font></td>
<td><a href="https://github.com/pjlab-sys4nlp/llama-moe"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼-教育部</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于</font></font><a href="https://github.com/facebookresearch/llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://www.cerebras.net/blog/slimpajama-a-627b-token-cleaned-and-deduplicated-version-of-redpajama" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SlimPajama</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的小型且经济实惠的 MoE 模型。激活的模型参数数量仅为3.0~3.5B，有利于部署和研究使用。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新加坡国立大学等</font></font></td>
<td><a href="https://github.com/XueFuzhao/OpenMoE"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放教育部</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一系列开源专家混合 (MoE) 大型语言模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雪花</font></font></td>
<td><a href="https://github.com/Snowflake-Labs/snowflake-arctic"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北极</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Arctic 采用独特的 Dense-MoE 混合变压器架构。它将 10B 密集变压器模型与剩余 128x3.66B MoE MLP 相结合，产生使用 top-2 门控选择的 480B 总数和 17B 活动参数。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多式联运</font></font></h1><a id="user-content-multi-modal" class="anchor" aria-label="永久链接：多模式" href="#multi-modal"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础模型</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">白海艾伦</font></font></td>
<td><a href="https://github.com/BaihaiAI/IDPChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">IDP聊天室</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA-13B</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稳定扩散</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放中文多模态模型，单GPU可运行，易于部署，提供UI。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿卜杜拉国王科技大学</font></font></td>
<td><a href="https://github.com/Vision-CAIR/MiniGPT-4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">迷你GPT-4</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MiniGPT-4 仅使用一个投影层，将 BLIP-2 的冻结视觉编码器与冻结的 LLM Vicuna 对齐，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并产生许多与 GPT-4 中演示的类似的新兴视觉语言功能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MSR 等</font></font></td>
<td><a href="https://github.com/haotian-liu/LLaVA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉瓦</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提出了视觉指令调整，旨在构建具有 GPT-4 级别功能的大型语言和视觉模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新加坡国立大学/星期四</font></font></td>
<td><a href="https://github.com/VPGTrans/VPGTrans"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">维普吉运输公司</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA/OPT/ </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Flan-T5/BLIP-2 </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">...</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">跨法学硕士转移 VPG 以显着降低成本构建 VL-LLM。 GPU小时数</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可减少10倍以上，训练数据量可减少至10%左右。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两种新型 VL-LLM 通过 VPGTrans 发布，包括</font></font><strong><a href="https://github.com/VPGTrans/VPGTrans#vl-llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VL-LLaMA</font></font></a></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和  </font></font><strong><a href="https://github.com/VPGTrans/VPGTrans#vl-vicuna"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VL-Vicuna</font></font></a></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><br><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VL-LLaMA</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;是多模式版本 LLaMA，通过 VPGTrans 将 BLIP-2 OPT-6.7B 传输到 LLaMA。</font></font><br><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VL-Vicuna</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个类似 GPT-4 的多模式聊天机器人，基于 Vicuna LLM。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国科学院等</font></font></td>
<td><a href="https://github.com/phellonchen/X-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-6B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">X-LLM使用X2L接口将多模态（图像、语音、视频）转换为外语，并将其输入到</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大型语言模型（ChatGLM）中以完成多模态LLM，实现令人印象深刻的多模态聊天功能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">南洋理工大学</font></font></td>
<td><a href="https://github.com/Luodian/Otter"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">獭</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放火烈鸟</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个基于 OpenFlamingo（DeepMind Flamingo 的开源版本）的多模态模型，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在 MIMIC-IT 上进行训练，并展示了改进的指令跟踪能力和上下文学习能力。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，优化 OpenFlamingo 的实施，将所需的</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">训练资源从 1 个 A100 GPU 民主化到 4 个 RTX-3090 GPU。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">厦门大学</font></font></td>
<td><a href="https://github.com/luogen1996/LaVIN"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉文</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提出了一种新颖且经济实惠的视觉语言指令调整解决方案，即模态混合适应（MMA）。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特别是，MMA 是一种端到端优化机制，它通过轻量级适配器连接图像编码器和 LLM。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同时，我们还在 MMA 中提出了一种新颖的路由算法，可以帮助模型自动转换</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单模态和多模态指令的推理路径。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国科学技术大学</font></font></td>
<td><a href="https://github.com/BradyFU/Woodpecker"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">啄木鸟</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一个纠正多模态大语言模型中的幻觉的工作。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">惠普彩泰</font></font></td>
<td><a href="https://github.com/hpcaitech/Open-Sora"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放索拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Openai Sora 的开源替代品。</font></font></td>
</tr>
</tbody>
</table>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另请参阅：</font></font><a href="https://github.com/BradyFU/Awesome-Multimodal-Large-Language-Models"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">awesome-Multimodal-Large-Language-Models</font></font></a></p>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据</font></font></h1><a id="user-content-data" class="anchor" aria-label="永久链接：数据" href="#data"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">预训练数据</font></font></h2><a id="user-content-pretrain-data" class="anchor" aria-label="永久链接：预训练数据" href="#pretrain-data"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据/项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起电脑</font></font></td>
<td><a href="https://github.com/togethercomputer/RedPajama-Data"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">红色睡衣-数据</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重现 LLaMA 训练数据集的开源配方。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@金匠</font></font></td>
<td><a href="https://github.com/goldsmith/Wikipedia"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">维基百科</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">维基百科 API 的 Pythonic 包装器。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令数据</font></font></h2><a id="user-content-instruction-data" class="anchor" aria-label="永久链接：指令数据" href="#instruction-data"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请参阅</font></font><a href="https://github.com/PhoebusSi/Alpaca-CoT/blob/main/CN_README.md#3-%E6%95%B0%E6%8D%AE%E9%9B%86%E5%90%88-data-collection"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Alpaca-CoT 数据收集</font></font></a></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">销售队伍</font></font></td>
<td><a href="https://github.com/salesforce/DialogStudio"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对话工作室</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DialogStudio：为对话式 AI 打造最丰富、最多样化的统一数据集收集和指令感知模型。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">综合数据生成</font></font></h2><a id="user-content-synthetic-data-generation" class="anchor" aria-label="永久链接：合成数据生成" href="#synthetic-data-generation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华盛顿大学等</font></font></td>
<td><a href="https://github.com/yizhongw/self-instruct"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自学</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用模型自己的一代来创建大量的教学数据。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@刘HC0428</font></font></td>
<td><a href="https://github.com/LiuHC0428/LAW-GPT#%E7%9F%A5%E8%AF%86%E9%97%AE%E7%AD%94"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可靠的自学</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 ChatGPT 根据给定文本生成一些问题和答案。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学</font></font></td>
<td><a href="https://github.com/nlpxucan/evol-instruct"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进化指导</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/nlpxucan/WizardLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">WizardLM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中提出的一种新颖方法</font><font style="vertical-align: inherit;">，通过使用LLM代替人类自动批量生产</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">各种难度级别和技能范围的开放域指令，以提高LLM的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">考斯特大学等</font></font></td>
<td><a href="https://github.com/lightaime/camel"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;提出了一种名为</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">角色扮演</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的新型交流代理框架，其中涉及使用</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">初始提示</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来引导聊天代理</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">完成任务，同时保持与人类意图的一致性。</font></font><br><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">角色扮演</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可用于生成特定任务/域中的对话数据。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@chatarena</font></font></td>
<td><a href="https://github.com/chatarena/chatarena"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天竞技场</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个提供多智能体语言游戏环境并促进有关自主 LLM 智能体及其社交互动的研究的库。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它提供了一个灵活的框架来定义多个参与者、环境以及它们之间的交互，基于马尔可夫决策过程。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">评估</font></font></h1><a id="user-content-evaluation" class="anchor" aria-label="永久链接：评估" href="#evaluation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">人工评价</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放人工智能</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-4/聊天GPT</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学/卡内基梅隆大学/MSRA ...</font></font></td>
<td><a href="https://github.com/WeOpenML/PandaLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">熊猫LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可重复且自动化的语言模型评估。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/lm-sys/FastChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天机器人竞技场</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与两个匿名模型并排聊天并投票选出更好的一个，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后使用 Elo 评级系统来计算模型的相对性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td><a href="https://github.com/tatsu-lab/alpaca_eval"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">羊驼毛评估</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/tatsu-lab/alpaca_farm/tree/main"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AlpacaFarm</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据集上的 GPT-4/Claude 评估</font><font style="vertical-align: inherit;">&nbsp;。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">克雷艾</font></font></td>
<td><a href="https://www.superclueai.com/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超级线索lyb</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/lm-sys/FastChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由cleai开发的Chatbot Arena</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中文版</font><font style="vertical-align: inherit;">&nbsp;。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海交通大学等</font></font></td>
<td><a href="https://github.com/GAIR-NLP/auto-j"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自动J</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个新的开源生成法官，可以有效地评估不同的法学硕士如何符合人类偏好。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">卡耐基梅隆大学</font></font></td>
<td><a href="https://github.com/neulab/code-bert-score"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码BERT分数</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于</font></font><a href="https://arxiv.org/abs/1904.09675" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BERTScore 的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码生成自动指标。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与 BERTScore 一样，CodeBERTScore 利用来自 CodeBERT 等模型的预先训练的上下文嵌入，并通过余弦相似度来匹配候选句子和参考句子中的单词。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与 BERTScore 不同的是，CodeBERTScore 还将自然语言输入或其他上下文与生成的代码一起进行编码，但不使用该上下文来计算余弦相似度。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基准</font></font></h2><a id="user-content-benchmark" class="anchor" aria-label="永久链接：基准" href="#benchmark"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><a href="https://mp.weixin.qq.com/s/ppRDj0tBJgcpGGx5JbzZIA" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">国内大模型实地考察</font></font></a></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基准</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">普林斯顿</font></font></td>
<td><a href="https://github.com/princeton-nlp/SWE-bench"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SWE-长凳</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从 GitHub 收集的用于评估现实世界软件问题的大型语言模型的基准。给定</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码库</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和  </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言模型的任务是生成</font><font style="vertical-align: inherit;">解决所描述问题的</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">补丁。</font></font></em><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/ruixiangcui/AGIEval"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AGIE值</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个以人为中心的基准，专门设计用于评估基础模型在与人类认知和解决问题相关的任务中的一般能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">克雷艾</font></font></td>
<td><a href="https://github.com/CLUEbenchmark/SuperCLUE-Agent"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SuperCLUE-代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于中文原生任务的智能体评估基准。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">字节跳动</font></font></td>
<td><a href="https://github.com/GPT-Fathom/GPT-Fathom"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-深寻</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-Fathom 是一个开源且可重复的 LLM 评估套件，在一致的设置下对 10 多个领先的开源和闭源 LLM 以及 OpenAI 的早期模型进行了 20 多个策划基准的基准测试。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">排行榜</font></font></h2><a id="user-content-leaderboard" class="anchor" aria-label="永久链接：排行榜" href="#leaderboard"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><a href="https://opencompass.org.cn/leaderboard-llm" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放罗盘</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">,拥抱脸</font></font></p>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">框架/工具包/平台</font></font></h1><a id="user-content-frameworktoolkitplatform" class="anchor" aria-label="永久链接：框架/工具包/平台" href="#frameworktoolkitplatform"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中科院</font></font></td>
<td><a href="https://github.com/PhoebusSi/Alpaca-CoT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">羊驼毛CoT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将 CoT 数据扩展到 Alpaca，以增强其推理能力。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旨在构建一个具有广泛指令集合（特别是CoT数据集）</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和各种大型语言模型的统一接口的指令微调（IFT）平台。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@hiyouga</font></font></td>
<td><a href="https://github.com/hiyouga/ChatGLM-Efficient-Tuning"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ChatGLM-高效调优</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 PEFT 有效微调 ChatGLM-6B。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@hiyouga</font></font></td>
<td><a href="https://github.com/hiyouga/LLaMA-Efficient-Tuning"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA-高效调优</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用 PEFT 微调 &ZeroWidthSpace;&ZeroWidthSpace;LLaMA（使用 QLoRA 的 PT+SFT+RLHF）。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@jianzhnie</font></font></td>
<td><a href="https://github.com/jianzhnie/Efficient-Tuning-LLMs"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高效调整法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">QLoRA LLM 的高效微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巨型人工智能</font></font></td>
<td><a href="https://github.com/hpcaitech/ColossalAI/blob/main/applications/Chat/README.md"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">巨聊</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://openai.com/blog/chatgpt/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于克隆ChatGPT 的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开源低成本解决方案，</font><font style="vertical-align: inherit;">具有完整的 RLHF 管道。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/DeepSpeed/tree/master/blogs/deepspeed-chat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深度快速聊天</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对各种规模的类似 ChatGPT 模型进行简单、快速且经济实惠的 RLHF 训练。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">莱昂人工智能</font></font></td>
<td><a href="https://github.com/LAION-AI/Open-Assistant"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">打开助手</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该项目旨在让每个人都能访问基于聊天的大型语言模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港科技大学</font></font></td>
<td><a href="https://github.com/OptimalScale/LMFlow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LM流</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个可扩展、方便且高效的工具箱，用于微调大型机器学习模型，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旨在用户友好、快速、可靠，并且可供整个社区使用。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/young-geng/EasyLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">易LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">EasyLM 是 JAX/Flax 中的预训练、微调、评估和服务 LLM 的一站式解决方案。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">EasyLM 可以利用 JAX 的 pjit 功能将 LLM 训练扩展到数百个 TPU/GPU 加速器。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@CogStack</font></font></td>
<td><a href="https://github.com/CogStack/opengpt"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放式GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于创建基于指令的数据集和训练会话领域专家大型语言模型 (LLM) 的框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱人工智能实验室</font></font></td>
<td><a href="https://github.com/HugAILab/HugNLP"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱自然语言处理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于 HuggingFace Transformer 的统一且全面的 NLP 库。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">D-AI计划</font></font></td>
<td><a href="https://github.com/ProjectD-AI/LLaMA-Megatron-DeepSpeed"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLaMA-威震天-DeepSpeed</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正在进行的大规模训练 Transformer 语言模型的研究，包括：BERT 和 GPT-2。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@潘启伟</font></font></td>
<td><a href="https://github.com/PanQiWei/AutoGPTQ"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自动GPTQ</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">易于使用的 LLM 量化包，具有用户友好的 API，基于 GPTQ 算法。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/modelscope/swift"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">迅速</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SWIFT（可扩展的轻量级微调基础设施）是一个可扩展的框架，旨在促进轻量级模型微调和推理。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它通过采用参数高效、内存高效和时间高效的方法，集成了各种高效微调方法的实现。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/alibaba/Megatron-LLaMA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">威震天-美洲驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了方便基于LLaMA的模型的训练，降低占用硬件资源的成本，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴决定向社区发布内部优化的Megatron-LLaMA训练框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@OpenLLMAI</font></font></td>
<td><a href="https://github.com/OpenLLMAI/OpenRLHF"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放式RLHF</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenRLHF旨在开发</font><font style="vertical-align: inherit;">基于Ray和DeepSpeed的</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高性能RLHF训练框架</font></font></strong><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。 OpenRLHF 是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最简单的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高性能 RLHF 库，支持使用单个 DGXA100（</font></font><a href="https://github.com/OpenLLMAI/OpenRLHF/blob/main/examples/scripts/train_ppo_llama_ray_34b.sh"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">脚本</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）进行 34B 模型 RLHF 训练。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenRLHF 的关键思想是使用 Ray 将 Actor 模型、奖励模型、参考模型和 Critic 模型分布到单独的 GPU 上，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同时将 Adam 优化器放置在 CPU 上。这使得能够跨多个 24GB RTX4090 GPU（或具有多个 A100 80G 的 34B 模型）对 7B 模型进行全面微调</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并且由于能够通过 Adam Offload 和 Ray 使用大生成批量大小，因此训练效率很高。</font></font><br> <strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的 13B llama2 模型的 PPO 性能是 DeepSpeedChat 的 4 倍。</font></font></strong></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@泽君王1</font></font></td>
<td><a href="https://github.com/zejunwang1/LLMTuner"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士调谐器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLMTuner是一款LLM指令调优工具，支持LoRA、QLoRA和全参数微调。在训练过程中，可以利用flashattention和xformersattention技术</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来提高训练效率，并结合LoRA、DeepSpeedZeRO、梯度检查点和4位量化等技术，有效</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">减少显存占用，在单机上达到同样的目标消费级显卡（A100/A40/A30/RTX3090/V100）微调7B/13B/34B大型号。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海人工智能实验室</font></font></td>
<td><a href="https://github.com/InternLM/xtuner"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">XTuner</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于高效微调 LLM 的工具包（InternLM、Llama、Baichuan、QWen、ChatGLM2）。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/codefuse-ai/MFTCoder"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MFT编码器</font></font></a></td>
<td><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CodeFuse-MFTCoder</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是CodeFuse针对多任务Code-LLM（代码任务的大型语言模型）的开源项目，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中包括模型、数据集、训练代码库和推理指南。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Facebook</font></font></td>
<td><a href="https://github.com/facebookresearch/llama-recipes"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼食谱</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Llama 2 模型的示例和配方。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/Azure/MS-AMP"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MS-AMP</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FP8-LM框架经过高度优化，在整个前向和后向传递过程中均采用FP8格式，大大降低了系统的计算、内存和通信开销。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结盟</font></font></h1><a id="user-content-alignment" class="anchor" aria-label="永久链接：对齐" href="#alignment"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><a href="https://arxiv.org/pdf/2109.01652.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">IFT</font></font></a></td>
<td><a href="https://openai.com/blog/chatgpt/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><a href="https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RLHF</font></font></a></td>
<td><a href="https://openai.com/blog/chatgpt/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来自人类反馈的强化学习。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">人择</font></font></td>
<td><a href="https://arxiv.org/abs/2212.08073" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">罗拉IF</font></font></a></td>
<td><a href="https://www.anthropic.com/index/introducing-claude" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">克洛德</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来自人工智能反馈的强化学习。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://arxiv.org/pdf/2304.05302v1.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">右心室颤动</font></font></a></td>
<td><a href="https://github.com/GanjinZero/RRHF"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">袋熊</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提出了一种称为 RRHF 的新颖学习范式，作为 RLHF 的替代方案，该范式对</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不同采样策略生成的响应进行评分，并学习通过排名损失使它们与人类偏好保持一致。并且性能</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与RLHF相当，过程中使用的模型更少。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港科技大学</font></font></td>
<td><a href="https://optimalscale.github.io/LMFlow/examples/raft.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">筏</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RAFT是一种新的比对算法，比传统的（基于PPO的）RLHF更高效。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">IBM/卡内基梅隆大学/麻省理工学院</font></font></td>
<td><a href="https://arxiv.org/abs/2305.03047" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自对准</font></font></a></td>
<td><a href="https://github.com/IBM/Dromedary"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单峰骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结合了原则驱动的推理和法学硕士的生成能力，可以在最少的人类监督下实现人工智能代理的自我调整。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学</font></font></td>
<td><a href="https://github.com/PKU-Alignment/safe-rlhf#constrained-value-alignment-via-safe-rlhf"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">脑血管病协会</font></font></a></td>
<td><a href="https://github.com/PKU-Alignment/safe-rlhf"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">海狸</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过安全 RLHF 进行约束值调整。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">腾讯</font></font></td>
<td><a href="https://github.com/Zyq-scut/RLTF"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RLTF</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从单元测试反馈中强化学习。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td><a href="/SunLemuria/OpenGPTAndBeyond/blob/main"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据保护组织</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">隐式优化与现有 RLHF 算法相同的目标（利用 KL 散度约束实现奖励最大化），但实现简单且易于训练。直观上，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DPO 更新增加了首选响应与不首选响应的相对对数概率，但它包含了动态的、每个示例的重要性权重，可以防止我们发现在朴素概率比目标下发生模型退化。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/thu-coai/BPO"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">业务流程外包</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BPO 背后的中心思想是创建一个自动提示优化器，将通常组织较差或含糊不清的人工提示重写为更好地传达人类意图的提示。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，这些提示可能更受 LLM 偏好，从而产生更好的人类偏好响应。实证结果表明，与 BPO 一致的 ChatGPT 的胜率比原始版本提高了 22%，而 GPT 则提高了 10%。 4.</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">人工智能2等</font></font></td>
<td><a href="https://github.com/Re-Align/urial"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">乌里亚尔</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">URIAL 是一种简单的、</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">免调整的</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对齐方法，URIAL（</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Untuned</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> LLMs with </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">R</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> estyled </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">I</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> n-context </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ALIGNMENT</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。 URIAL 纯粹通过上下文学习 (ICL) 实现有效对齐，只需三个恒定的风格示例和一个系统提示即可实现与 SFT/RLHF 相当的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放性</font></font></td>
<td><a href="https://github.com/openai/weak-to-strong"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由弱到强</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在弱模型生成的标签上天真地微调强预训练模型，它们始终比弱监督者表现得更好。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多语言</font></font></h1><a id="user-content-multi-language" class="anchor" aria-label="永久链接：多语言" href="#multi-language"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">词汇扩展</font></font></h2><a id="user-content-vocabulary-expansion" class="anchor" aria-label="永久链接：词汇扩展" href="#vocabulary-expansion"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据LLaMA repo中的官方</font></font><a href="https://github.com/facebookresearch/llama/blob/main/FAQ.md#4-other-languages"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FAQ</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，除了拉丁语言之外，其他的token并不多，所以努力之一就是扩大词汇量，一些作品如下所示：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</font></font></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型/项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础模型</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ymcui</font></font></td>
<td><a href="https://github.com/ymcui/Chinese-LLaMA-Alpaca"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国-美洲驼-羊驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深圳大学</font></font></td>
<td><a href="https://github.com/CVI-SZU/Linly"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">林利</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">全尺寸 LLaMA，在中文语料库上进一步预训练。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@Neutralzz</font></font></td>
<td><a href="https://github.com/Neutralzz/BiLLa"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">比拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉马-7B</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进一步对</font></font><a href="https://www.sciencedirect.com/science/article/pii/S2666651021000152" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Wudao</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><a href="https://arxiv.org/abs/2101.00027" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PILE</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><a href="https://www.statmt.org/wmt22/translation-task.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">WMT</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行预训练。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@pengxiao-song</font></font></td>
<td><a href="https://github.com/pengxiao-song/LaWGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拉维格PT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zh</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/ChatGLM</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用中文法律术语扩展词汇，根据自学生成的数据对教学进行微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主意</font></font></td>
<td><a href="https://huggingface.co/IDEA-CCNL/Ziya-LLaMA-13B-Pretrain-v1" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子牙</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于LLaMA的大规模预训练模型，拥有130亿个参数。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们针对中文对LLaMAtokenizer进行了优化，基于LLaMa-13B模型增量训练了1100亿个token数据，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">显着提高了对中文的理解和生成能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放伙伴</font></font></td>
<td><a href="https://github.com/OpenBuddy/OpenBuddy"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放伙伴</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/猎鹰...</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenBuddy 基于 Tii 的 Falcon 模型和 Facebook 的 LLaMA 模型构建，经过微调，包括扩展词汇表、</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">额外的常见字符和增强的令牌嵌入。通过利用这些改进和多轮对话数据集，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenBuddy 提供了一个强大的模型，能够回答问题并执行跨多种语言的翻译任务。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">佛得角</font></font></td>
<td><a href="https://github.com/Abbey4799/CuteGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可爱GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CuteGPT扩展了中文词汇量，并对Llama模型进行了预训练，提高了其对中文的理解能力。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">随后，通过对话指令对其进行微调，以增强模型理解指令的能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿尔法旗</font></font></td>
<td><a href="https://github.com/FlagAlpha/Llama2-Chinese"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿尔法旗</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英文/中文</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼/骆驼2</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于海量中文数据，从预训练开始，模型的中文能力不断迭代升级。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高效训练/微调</font></font></h1><a id="user-content-efficient-trainingfine-tuning" class="anchor" aria-label="永久链接：高效训练/微调" href="#efficient-trainingfine-tuning"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://arxiv.org/abs/2106.09685" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">低秩适应（LoRA），它冻结预训练的模型权重，并将可训练的秩分解矩阵注入</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到 Transformer 架构的每一层中，大大减少了下游任务的可训练参数的数量。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td><a href="https://aclanthology.org/2021.acl-long.353/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">前缀调优</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自然语言生成任务微调的轻量级替代方案，它保持语言模型参数冻结</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并优化一系列连续的特定于任务的向量，我们称之为前缀。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://arxiv.org/abs/2103.10385" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">P-调音</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">P-tuning 利用一些连续的自由参数作为提示，作为预训练语言模型的输入。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我们使用梯度下降来优化连续提示，作为离散提示搜索的替代方案。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四等</font></font></td>
<td><a href="https://arxiv.org/pdf/2110.07602.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">P-调整 v2</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一项新颖的实证发现表明，正确优化的提示调整可以与跨各种模型规模和 NLU 任务的普遍微调相媲美。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从技术上讲，P-tuning v2 在概念上并不新颖。它可以被视为 Deep Prompt Tuning 的优化和改编实现。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷歌</font></font></td>
<td><a href="https://arxiv.org/abs/2104.08691" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">及时调整</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种简单而有效的机制，用于学习“软提示”来调节冻结的语言模型以执行特定的下游任务。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提示调优可以看作是“前缀调优”的简化。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软等</font></font></td>
<td><a href="https://arxiv.org/abs/2303.10512" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿达洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据权重矩阵的重要性得分自适应地分配权重矩阵之间的参数预算。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特别是，AdaLoRA 以奇异值分解的形式参数化增量更新。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华盛顿大学</font></font></td>
<td><a href="https://github.com/artidoro/qlora"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">QLoRA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种高效的微调方法，可减少内存使用量，足以在单个 48GB GPU 上微调 65B 参数模型，同时保留</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">完整的 16 位微调任务性能。 QLoRA 通过冻结的 4 位量化预训练语言模型将梯度反向传播到低阶适配器 (LoRA) 中。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">佛得角</font></font></td>
<td><a href="https://github.com/OpenLMLab/LOMO"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">洛莫</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种新的优化器</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LO</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> w-Memory </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">O</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ptimization ( </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LOMO</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> )，它将梯度计算和参数更新融合在一个步骤中以减少内存使用，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从而实现在单个 RTX 3090 上对 7B 模型进行全参数微调，或单机65B型号，8×RTX 3090，每块24GB内存。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MBZUAI 等</font></font></td>
<td><a href="https://github.com/Arnav0400/ViT-Slim/tree/master/GLoRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">格洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GLoRA 增强了低秩适应 (LoRA)，采用通用提示模块来优化预训练模型权重并调整中间激活，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从而在不同的任务和数据集上提供更大的灵活性和功能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省大学洛厄尔分校</font></font></td>
<td><a href="https://github.com/Guitaricet/relora"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雷洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ReLoRA 执行高秩更新并实现与常规神经网络训练类似的性能。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;ReLoRA 的组件包括神经网络的初始全秩训练、LoRA 训练、重新启动、锯齿状学习率计划和部分优化器重置。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华为</font></font></td>
<td><a href="https://arxiv.org/pdf/2309.14717.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">QA-LoRA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为原始LoRA配备了两重能力：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（i）在微调期间，LLM的权重被量化（例如，量化为INT4）以减少时间和内存使用；</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">(ii) 经过微调后，LLM 和辅助权重自然地集成到量化模型中，而不会损失准确性。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">UMD 等</font></font></td>
<td><a href="https://github.com/neelsjain/NEFTune/tree/main"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NEFTune</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们建议在微调的前向传播过程中向训练数据的嵌入向量添加随机噪声。我们证明，这个简单的技巧</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以提高指令微调的结果，通常可以大幅度提高，而无需额外的计算或数据开销。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/TsinghuaC3I/SoRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">索拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稀疏低秩自适应（SoRA），可以在自适应过程中动态调整内在秩。我们通过</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在训练阶段结合使用近端梯度法优化的门单元来实现这一点，在门的稀疏性下控制秩的基数。在随后的推理阶段，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们消除了与清零排名对应的参数块，以将每个 SoRA 模块还原为简洁但排名最优的 LoRA。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实验结果表明，即使保留 70% 的参数和 70% 的训练时间，SoRA 也可以优于其他基线。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">福州大学等</font></font></td>
<td><a href="https://github.com/cmnfriend/O-LoRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">O-LoRA 通过将当前任务的梯度更新限制为与过去任务的梯度子空间正交来减轻过去任务知识的灾难性遗忘。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TUDB实验室</font></font></td>
<td><a href="https://github.com/TUDB-Labs/multi-lora-fine-tune"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">m-LoRA（又名 Multi-Lora Fine-Tune）是一个开源框架，用于使用高效的多种 LoRA/QLoRA 方法微调大型语言模型 (LLM)。 m-LoRA 的主要特性包括：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1. 高效的 LoRA/QLoRA：优化微调过程，通过利用共享的基于冻结的模型显着减少 GPU 内存使用。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2. 多个LoRA适配器：支持多个LoRA/QLoRA适配器的并发微调。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3.基于LoRA的Mix-of-Expert：支持</font></font><a href="https://github.com/TUDB-Labs/multi-lora-fine-tune/blob/main/MixLoRA.md"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MixLoRA</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它实现了基于多个LoRA适配器的Mix-of-Expert架构，用于冻结FFN层。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">低成本推理</font></font></h1><a id="user-content-low-cost-inference" class="anchor" aria-label="永久链接：低成本推理" href="#low-cost-inference"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">量化</font></font></h2><a id="user-content-quantization" class="anchor" aria-label="永久链接：量化" href="#quantization"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">算法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华盛顿大学等</font></font></td>
<td><a href="https://github.com/Vahe1994/SpQR"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SpQR</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种新的压缩格式和量化技术，首次实现了跨模型尺度的 LLM 近乎无损压缩，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同时达到了与之前方法类似的压缩级别。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/xijiu9/Train_Transformers_with_INT4"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Train_Transformers_with_INT4</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于前向传播，我们确定了异常值的挑战，并提出了哈达玛量化器来抑制异常值。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于反向传播，我们通过提出位分割来利用梯度的结构稀疏性，并利用分数采样技术来准确量化梯度。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英特尔</font></font></td>
<td><a href="https://github.com/intel/neural-compressor"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">神经压缩器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旨在为</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不同深度学习框架的低精度量化、稀疏性、剪枝、知识蒸馏等网络压缩技术提供统一的API，以追求最佳的推理性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英特尔</font></font></td>
<td><a href="https://github.com/intel/intel-extension-for-transformers"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">变形金刚英特尔扩展</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英特尔® Extension for Transformers 是一个创新工具包，可在英特尔平台上加速基于 Transformer 的模型，特别是在第四代英特尔至强可扩展处理器 Sapphire Rapids 上有效。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/SqueezeAILab/KVQuant/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">KV定量</font></font></a></td>
<td><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每通道、Pre-RoPE</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> Key 量化，以更好地匹配 Keys 中的异常通道；非均匀量化（</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NUQ</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）以更好地表示非均匀激活；&nbsp;</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">密集和稀疏量化，</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以减轻数值异常值对量化难度的影响；&nbsp; </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Q-Norm</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可减轻超低精度（例如 2 位）下的分布偏移； KVQuant 可以  </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在单个 A100-80GB GPU 上提供具有 1M 上下文长度的 LLaMA-7B 模型</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，甚至可以</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在 8-GPU 系统上提供具有 10M 上下文长度的 LLaMA-7B 模型</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">🔥</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></h2><a id="user-content-projects" class="anchor" aria-label="永久链接： 项目" href="#projects"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ggerganov</font></font></td>
<td><a href="https://github.com/ggerganov/llama.cpp"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼.cpp</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">llama 和其他一些模型的 c/cpp 实现，使用量化。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@NouamaneTazi</font></font></td>
<td><a href="https://github.com/NouamaneTazi/bloomz.cpp"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">布卢姆兹.cpp</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BLOOM 推理的 C++ 实现。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@mlc-ai</font></font></td>
<td><a href="https://github.com/mlc-ai/mlc-llm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个通用的解决方案，允许任何语言模型本地部署在不同的硬件后端和本地应用程序上，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">再加上一个高效的框架，让每个人都可以根据自己的用例进一步优化模型性能。&nbsp;&nbsp;</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/wangzhaode/ChatGLM-MNN"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天GLM-MNN</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将 ChatGLM-6B 模型转换为 MNN 并使用 C++ 进行推理。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">抖动</font></font></td>
<td><a href="https://github.com/Jittor/JittorLLMs"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">吉特法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大幅降低硬件成本（降低80%），目前被誉为成本最低的部署库，支持多平台。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放BMB</font></font></td>
<td><a href="https://github.com/OpenBMB/BMInf"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BMI指数</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BMnf 在最低要求下支持在单个 NVIDIA GTX 1060 GPU 上运行具有超过 100 亿个参数的模型。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;在GPU内存支持大型模型推理（例如V100或A100）的情况下，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BMInf相对于现有的PyTorch实现仍然有显着的性能提升。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">惠普彩泰</font></font></td>
<td><a href="https://github.com/hpcaitech/EnergonAI"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">EnergonAI</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">凭借张量并行运算、管道并行包装器、分布式检查点加载和定制的 CUDA 内核，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">EnergonAI 可以为大规模模型实现高效的并行推理。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">梅格引擎</font></font></td>
<td><a href="https://github.com/MegEngine/InferLLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推理法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个轻量级的LLM模型推理框架，主要参考和借鉴了</font></font><a href="https://github.com/ggerganov/llama.cpp"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">llama.cpp项目</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">llama.cpp将几乎所有核心&ZeroWidthSpace;&ZeroWidthSpace;代码和内核放在一个文件中，并使用大量宏，导致开发人员难以阅读和修改。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@saharNooby</font></font></td>
<td><a href="https://github.com/saharNooby/rwkv.cpp"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RWKV.cpp</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/BlinkDL/RWKV-LM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BlinkDL/RWKV-LM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到</font></font><a href="https://github.com/ggerganov/ggml"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ggerganov/ggml</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的端口</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调频推理</font></font></td>
<td><a href="https://github.com/FMInference/FlexGen"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">弗莱克斯根</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FlexGen 是一种高吞吐量生成引擎，用于在 GPU 内存有限的情况下运行大型语言模型。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FlexGen</font><font style="vertical-align: inherit;">通过 IO 高效卸载、压缩和  </font><strong><font style="vertical-align: inherit;">大有效批量大小实现</font></strong></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高吞吐量</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱脸</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大代码项目</font></font></td>
<td><a href="https://github.com/bigcode-project/starcoder.cpp"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">星编码器.cpp</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://github.com/ggerganov/ggml"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用ggml</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">库进行 💫 StarCoder 推理的 C++ 实现</font><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">卡耐基梅隆大学</font></font></td>
<td><a href="https://github.com/flexflow/FlexFlow/tree/inference"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">规格推断</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SpecInfer 是一个开源分布式多 GPU 系统，可通过</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推测推理</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和  </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">令牌树验证</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加速生成式 LLM 推理。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SpecInfer 背后的一个关键见解是结合各种集体提升调整的小型推测模型 (SSM) 来共同预测 LLM 的输出。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ztxz16</font></font></td>
<td><a href="https://github.com/ztxz16/fastllm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快速</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">全平台纯c++ llm加速库，支持moss、chatglm、baichuan模型，在手机上运行流畅。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/vllm-project/vllm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">弗洛姆</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个快速且易于使用的 LLM 推理和服务库。使用 PagedAttention 快速高效管理注意力键和值内存</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></strong></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td><a href="https://github.com/abacaj/mpt-30B-inference"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">mpt-30B-推理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用您的 CPU 在最新的 MPT-30B 模型上运行推理。此推理代码使用</font></font><a href="https://github.com/ggerganov/ggml"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ggml</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">量化模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海人工智能实验室</font></font></td>
<td><a href="https://github.com/InternLM/lmdeploy"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">部署</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于压缩、部署和服务 LLM 的工具包。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@turboderp</font></font></td>
<td><a href="https://github.com/turboderp/exllama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">埃拉玛</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;/&nbsp;</font></font><a href="https://github.com/turboderp/exllamav2"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">埃拉玛V2</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于在现代消费级 GPU 上本地运行 LLM 的快速推理库</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">火炬</font></font></td>
<td><a href="https://github.com/pytorch/executorch"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">执行火炬</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于为 PyTorch 模型跨移动和边缘设备启用设备上 AI 的端到端解决方案。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奥比赛</font></font></td>
<td><a href="https://github.com/xorbitsai/inference"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新推理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个强大且多功能的库，旨在服务于语言、语音识别和多模式模型。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">借助 Xorbits Inference，您只需使用一个命令即可轻松部署和服务您的或最先进的内置模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英伟达</font></font></td>
<td><a href="https://github.com/NVIDIA/TensorRT-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TensorRT-法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TensorRT-LLM 为用户提供了易于使用的 Python API 来定义大型语言模型 (LLM) 并构建</font><font style="vertical-align: inherit;">包含</font><font style="vertical-align: inherit;">最先进优化的</font></font><a href="https://developer.nvidia.com/tensorrt" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TensorRT</font></font></a><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引擎，以便在 NVIDIA GPU 上高效地执行推理。 TensorRT-LLM 还包含用于创建</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">执行这些 TensorRT 引擎的 Python 和 C++ 运行时的组件。它还包括一个</font><font style="vertical-align: inherit;">用于与</font><a href="https://developer.nvidia.com/nvidia-triton-inference-server" rel="nofollow"><font style="vertical-align: inherit;">NVIDIA Triton 推理服务器集成的</font></a></font><a href="https://github.com/triton-inference-server/tensorrtllm_backend"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">后端</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">；为法学硕士服务的生产质量体系。</font><font style="vertical-align: inherit;">使用 TensorRT-LLM 构建的模型可以在各种配置上执行，从单个 GPU 到</font><font style="vertical-align: inherit;">具有多个 GPU 的多个节点（使用</font><a href="https://docs.nvidia.com/deeplearning/nemo/user-guide/docs/en/stable/nlp/nemo_megatron/parallelisms.html#tensor-parallelism" rel="nofollow"><font style="vertical-align: inherit;">张量并行性</font></a><font style="vertical-align: inherit;">和/或</font><a href="https://docs.nvidia.com/deeplearning/nemo/user-guide/docs/en/stable/nlp/nemo_megatron/parallelisms.html#pipeline-parallelism" rel="nofollow"><font style="vertical-align: inherit;">管道并行性</font></a><font style="vertical-align: inherit;">）。</font></font><a href="https://developer.nvidia.com/nvidia-triton-inference-server" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><a href="https://docs.nvidia.com/deeplearning/nemo/user-guide/docs/en/stable/nlp/nemo_megatron/parallelisms.html#tensor-parallelism" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><a href="https://docs.nvidia.com/deeplearning/nemo/user-guide/docs/en/stable/nlp/nemo_megatron/parallelisms.html#pipeline-parallelism" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@sabetAI</font></font></td>
<td><a href="https://github.com/sabetAI/BLoRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">批量 LoRA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过同一批次中的多个 LoRA 路由推理，最大化 GPU 利用率。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱脸</font></font></td>
<td><a href="https://github.com/huggingface/text-generation-inference"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TGI</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文本生成推理 (TGI) 是一个用于部署和服务大型语言模型 (LLM) 的工具包。 TGI 为最流行的开源 LLM 提供高性能文本生成，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包括 Llama、Falcon、StarCoder、BLOOM、GPT-NeoX</font></font><a href="https://huggingface.co/docs/text-generation-inference/supported_models" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。 TGI 实现了许多功能，例如：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 简单的启动器，可服务最流行的 LLM </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 生产就绪（使用开放遥测、Prometheus 指标进行分布式跟踪）</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 张量并行，可在多个 GPU 上进行更快的推理</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- 使用服务器发送事件 (SSE) 进行令牌流</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-连续批处理传入请求以提高总吞吐量-</font><font style="vertical-align: inherit;">在最流行的架构上使用</font><a href="https://github.com/HazyResearch/flash-attention"><font style="vertical-align: inherit;">Flash Attention</font></a><font style="vertical-align: inherit;">和</font><a href="https://github.com/vllm-project/vllm"><font style="vertical-align: inherit;">Paged Attention</font></a></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">优化变压器代码进行推理</font></font><a href="https://github.com/HazyResearch/flash-attention"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font><a href="https://github.com/vllm-project/vllm"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/DeepSpeed-MII"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DeepSpeed-MII</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MII 的底层由</font></font><a href="https://arxiv.org/abs/2207.00032" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DeepSpeed-Inference</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供支持。根据模型类型、模型大小、批量大小和可用硬件资源，MII 自动应用</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DeepSpeed-Inference 中的一组适当的系统优化，以最小化延迟并最大化吞吐量。它通过使用许多预先指定的模型注入策略之一来实现这一点，该策略允许 MII 和</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DeepSpeed-Inference 识别底层 PyTorch 模型架构并用优化的实现替换它。在此过程中，MII 使其</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DeepSpeed-Inference 中的广泛优化自动可用于其支持的数千种流行模型。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">柔性流</font></font></td>
<td><a href="https://github.com/flexflow/FlexFlow/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">柔性流</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使 FlexFlow Serve 能够加速 LLM 服务的一项关键技术是推测推理，它结合了各种集体提升调整的小型推测模型 (SSM)</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来共同预测 LLM 的输出；预测被组织为令牌树，每个节点代表一个候选令牌序列。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用一种新颖的基于树的并行解码机制，根据 LLM 的输出并行验证由令牌树表示的</font><font style="vertical-align: inherit;">所有候选令牌序列的正确性。 </font><font style="vertical-align: inherit;">FlexFlow Serve 使用 LLM 作为令牌树验证器而不是</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">增量解码器，这大大减少了服务生成 LLM 的端到端推理延迟和计算要求，同时可证明保持模型质量。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BentoML</font></font></td>
<td><a href="https://github.com/bentoml/BentoML"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BentoML</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生产中机器学习的开放平台。它简化了模型打包和模型管理，优化了模型服务工作负载</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以在生产规模上运行，并加速了预测服务的创建、部署和监控。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ModelTC</font></font></td>
<td><a href="https://github.com/ModelTC/lightllm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轻型法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于Python的LLM（大型语言模型）推理和服务框架，以其轻量级设计、易于扩展和高速性能而著称。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@FasterDecoding</font></font></td>
<td><a href="https://github.com/FasterDecoding/Medusa"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">美杜莎</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用多个解码头加速 LLM 生成的简单框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">优比银行等</font></font></td>
<td><a href="https://github.com/S-LoRA/S-LoRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S-LoRA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S-LoRA 将所有适配器存储在主内存中，并将当前运行的查询使用的适配器获取到 GPU 内存。为了有效利用GPU内存并减少碎片，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S-LoRA提出了统一分页（Unified Paging）。统一分页使用统一的内存池来管理具有不同等级的动态适配器权重和具有不同序列长度的 KV 缓存张量。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，S-LoRA 采用新颖的张量并行策略和高度优化的定制 CUDA 内核，用于 LoRA 计算的异构批处理。总的来说，这些功能使 S-LoRA</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">能够以较小的开销在单个 GPU 上或跨多个 GPU 上为数千个 LoRA 适配器提供服务。与 HuggingFace PEFT 和 vLLM（对 LoRA 服务的简单支持）等最先进的库相比，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S-LoRA 可以将吞吐量提高多达 4 倍，并将服务适配器的数量增加几个数量级。因此，S-LoRA 能够为许多特定于任务的微调模型提供可扩展的服务</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并提供大规模定制微调服务的潜力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@lyogavin</font></font></td>
<td><a href="https://github.com/lyogavin/Anima/tree/main/air_llm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">航空法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当执行到某一层时，会从硬盘中加载相应层，并进行该层的计算。一旦计算完成，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该层的内存就可以完全释放。这样，GPU 内存使用量将仅为一层 Transformer 参数的大小。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华盛顿大学等</font></font></td>
<td><a href="https://github.com/punica-ai/punica"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">石榴属</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们推出了 Punica，一个在共享 GPU 集群中为多个 LoRA 模型提供服务的系统。 Punica 包含新的 CUDA 内核设计，允许对不同 LoRA 模型的 GPU 操作进行批处理。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这允许 GPU 在服务多个不同的 LoRA 模型时仅保存底层预训练模型的单个副本，从而显着提高 GPU 在内存和计算方面的效率。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的调度程序将多租户 LoRA 服务工作负载整合到共享 GPU 集群中。通过固定大小的 GPU 集群，我们的评估表明，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与最先进的 LLM 服务系统相比，Punica 在服务多个 LoRA 模型方面实现了 12 倍的吞吐量提高，同时每个令牌仅增加 2 毫秒的延迟。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/yule-BUAA/MergeLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">合并LM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这项工作中，我们发现语言模型（LM），无论是基于编码器还是基于解码器，都可以</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过同化同源模型的参数来获得新的功能，而不需要重新训练或 GPU</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。 1. 我们引入了一种称为</font><strong><font style="vertical-align: inherit;">DARE</font></strong></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的新颖操作</font><font style="vertical-align: inherit;">，可以直接将大部分（90% 甚至 99%） delta 参数设置为零，而不影响 SFT LM 的功能。</font><font style="vertical-align: inherit;">2. 我们使用 DARE 作为</font><strong><font style="vertical-align: inherit;">通用预处理技术</font></strong><font style="vertical-align: inherit;">来稀疏化多个 SFT 同源模型的 delta 参数，然后通过参数平均将它们合并为单个模型。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">苏黎世联邦理工学院</font></font></td>
<td><a href="https://github.com/pbelcak/UltraFastBERT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超快速BERT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种 BERT 变体，在推理过程中使用 0.3% 的神经元，同时性能与类似的 BERT 模型相当。 UltraFastBERT 仅选择性地使用 4095 个神经元中的 12 个进行每层推理。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;这是通过用快速前馈网络（FFF）替换前馈网络来实现的。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">优比银行等</font></font></td>
<td><a href="https://github.com/hao-ai-lab/LookaheadDecoding"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">前瞻解码</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://en.wikipedia.org/wiki/Jacobi_method" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">前瞻解码通过利用雅可比迭代方法</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">直接使用 LLM 同时提取和验证 n 元语法，从而打破了自回归解码中的顺序依赖性</font><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">前瞻解码功能</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">草稿模型或数据存储。它线性减少与每个解码步骤使用的 log(FLOPs) 直接相关的解码步骤数量。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英特尔</font></font></td>
<td><a href="https://github.com/intel-analytics/BigDL"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大DL</font></font></a></td>
<td><strong><a href="https://github.com/intel-analytics/BigDL/blob/main/python/llm"><code>bigdl-llm</code></a></strong><font style="vertical-align: inherit;"><strong><font style="vertical-align: inherit;">是一个使用INT4/FP4/INT8/FP8在 Intel </font></strong><strong><font style="vertical-align: inherit;">XPU</font></strong><font style="vertical-align: inherit;">（从</font><em><font style="vertical-align: inherit;">笔记本电脑</font></em><font style="vertical-align: inherit;">到</font><em><font style="vertical-align: inherit;">GPU</font></em><font style="vertical-align: inherit;">再到  </font><em><font style="vertical-align: inherit;">云</font></em><font style="vertical-align: inherit;">）上运行</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLM</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（大型语言模型）</font><font style="vertical-align: inherit;">的库</font><font style="vertical-align: inherit;">，延迟非常低（对于任何</font><strong><font style="vertical-align: inherit;">PyTorch</font></strong><font style="vertical-align: inherit;">模型）。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"></font></em><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"></font></em><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"></font></em><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">商汤科技等</font></font></td>
<td><a href="https://github.com/ModelTC/lightllm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轻型法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1. 三进程异步协作：分词、模型推理、去分词异步进行，GPU利用率大幅提升。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2.&nbsp; </font></font><a href="https://github.com/ModelTC/lightllm/blob/main/docs/TokenAttention.md"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Token Attention</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：实现了 token-wise 的 KV 缓存内存管理机制，实现推理过程中的零内存浪费。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3. 高性能Router：与Token Attention配合，精心管理每个Token的GPU内存，从而优化系统吞吐量。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四等</font></font></td>
<td><a href="https://github.com/imagination-research/sot/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">索特</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引导LLM生成答案的骨架，然后进行并行API调用或批量解码，并行完成每个骨架点的内容。 SoT 不仅可以显着提高 12 个法学硕士的速度，而且还可以潜在地提高多个问题类别的答案质量。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奥拉马</font></font></td>
<td><a href="https://github.com/ollama/ollama?tab=readme-ov-file"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奥拉马</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">llm 推理的 docker 风格交互。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/alibaba/rtp-llm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴面向多种应用的高性能LLM推理引擎。该项目主要基于</font></font><a href="https://github.com/NVIDIA/FasterTransformer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FasterTransformer</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，在此基础上，我们集成了来自</font></font><a href="https://github.com/NVIDIA/TensorRT-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TensorRT-LLM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的一些内核实现。 FasterTransformer和TensorRT-LLM为我们提供了可靠的性能保证。</font></font><a href="https://github.com/Dao-AILab/flash-attention"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Flash-Attention2</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/NVIDIA/cutlass"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">cutlass</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也在我们持续的性能优化过程中提供了很多帮助。我们的连续批处理和增量解码借鉴了</font></font><a href="https://github.com/vllm-project/vllm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">vllm</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的实现</font><font style="vertical-align: inherit;">；采样借鉴了</font></font><a href="https://github.com/huggingface/transformers"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Transformer</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，推测性采样集成了</font></font><a href="https://github.com/FasterDecoding/Medusa"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Medusa</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的实现，多模态部分集成了</font></font><a href="https://github.com/haotian-liu/LLaVA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">llava</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/QwenLM/Qwen-VL"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">qwen-vl 的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实现。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即时压缩</font></font></h2><a id="user-content-prompt-compression" class="anchor" aria-label="永久链接：即时压缩" href="#prompt-compression"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/LLMLingua"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士语言</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLMLingua，使用经过良好训练的对齐后的小语言模型（例如 GPT2-small 或 LLaMA-7B）来检测提示中不重要的标记，并利用黑盒 LLM 中的压缩提示进行推理，实现高达 20 倍的压缩以最小的性能损失。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提示</font></font></h1><a id="user-content-prompting" class="anchor" aria-label="永久链接：提示" href="#prompting"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><a href="https://www.promptingguide.ai/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快速工程指南</font></font></a></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷歌</font></font></td>
<td><a href="https://arxiv.org/pdf/2201.11903.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">钴酸甲酯</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种允许大型语言模型 (LLM) 在给出最终答案之前通过一系列中间步骤解决问题的技术。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">普林斯顿等</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ToT( </font></font><a href="https://arxiv.org/abs/2305.10601" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Yao 等人 (2023)</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&nbsp;和</font></font><a href="https://arxiv.org/abs/2305.08291" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Long (2023)</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> )</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ToT 维护一棵思想树，其中思想代表连贯的语言序列，作为解决问题的中间步骤。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这种方法使 LM 能够自我评估中间思想通过深思熟虑的推理过程解决问题所取得的进展。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海交通大学等</font></font></td>
<td><a href="https://arxiv.org/pdf/2305.16582.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">得到</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们提出思维图（GoT）推理，它将人类思维过程不仅建模为链，而且建模为图。通过将思维单元表示为节点</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并将它们之间的连接表示为边缘，我们的方法捕获了人类思维的非顺序性质，并允许对思维过程进行更真实的建模。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">普林斯顿等</font></font></td>
<td><a href="https://github.com/ysymyth/ReAct"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">反应</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLM 用于</font><font style="vertical-align: inherit;">以交错的方式生成</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推理轨迹</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特定于任务的操作。</font></font></em><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上海交通大学</font></font></td>
<td><a href="https://github.com/Anni-Zou/Meta-CoT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元CoT</font></font></a></td>
<td><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Meta-CoT</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一种适用于输入问题类型未知的混合任务场景中的通用CoT提示方法。它由三个阶段组成：</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（i）  </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">场景识别</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：对输入问题的场景进行分类；</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">(ii)  </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">演示选择</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：获取分类场景的 ICL 演示；</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">(iii)  </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">答案推导</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：通过向 LLM 提供包含获取的 ICL 演示和输入问题的提示来执行答案推理。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加州大学洛杉矶分校</font></font></td>
<td><a href="https://uclaml.github.io/Rephrase-and-Respond/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雷达</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们提出了一种名为“改写和回答”（RaR）的方法，它允许法学硕士改写和扩展人类提出的问题，并在单个提示中提供回答。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的实验表明，我们的方法显着提高了不同模型在各种任务中的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国科学院等</font></font></td>
<td><a href="https://arxiv.org/pdf/2307.11760.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">情绪提示</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的自动实验表明，法学硕士对情商有一定的把握，他们的表现可以通过情绪提示（我们称之为“EmotionPrompt”，将原始提示与情绪刺激相结合）来提高，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的人体研究结果表明，EmotionPrompt 可以显着提高表现的生成任务。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元</font></font></td>
<td><a href="https://arxiv.org/pdf/2311.11829.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S2A</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S2A 重新生成输入上下文以仅包含相关部分，然后再处理重新生成的上下文以得出最终响应。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷歌</font></font></td>
<td><a href="https://arxiv.org/pdf/2310.06117.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">后退提示</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们提出了后退提示，这是一种简单的提示技术，使法学硕士能够进行抽象，从包含特定细节的实例中导出高级概念和第一原理。使用概念和原则来指导推理步骤，法学硕士可以显着提高他们遵循正确的推理路径获得解决方案的能力。我们使用 PaLM-2L 模型进行了 STEP-BACK PROMPTING 实验，并观察到在 STEM、知识 QA 和多跳推理等各种具有挑战性的推理密集型任务中获得了显着的性能提升。例如，STEP-BACK PROMPTING 将 PaLM-2L 在 MMLU 物理和化学方面的表现提高了 7% 和 11%，将 TimeQA 提高了 27%，将 MuSiQue 提高了 7%。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安全</font></font></h1><a id="user-content-safety" class="anchor" aria-label="永久链接：安全" href="#safety"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">守高</font></font></td>
<td><a href="https://github.com/thu-coai/Safety-Prompts"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安全提示</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国安全提示评估和提高法学硕士的安全性。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">诚实</font></font></h1><a id="user-content-truthfulness" class="anchor" aria-label="永久链接： 诚实" href="#truthfulness"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">哈佛</font></font></td>
<td><a href="https://github.com/likenneth/honest_llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">伊蒂</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ITI 的运作方式是在推理过程中改变模型激活，遵循有限数量的注意力头的一组方向。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这种干预显着提高了 LLaMA 模型在 TruthfulQA 基准上的性能。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在名为 Alpaca 的指令微调 LLaMA 上，ITI 将其真实性从 32.5 提高到 65.1。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超出上下文窗口</font></font></h1><a id="user-content-exceeding-context-window" class="anchor" aria-label="永久链接：超出上下文窗口" href="#exceeding-context-window"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><a href="https://zhuanlan.zhihu.com/p/670280576" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://zhuanlan.zhihu.com/p/670280576</font></font></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">扩展上下文窗口</font></font></h2><a id="user-content-extending-context-window" class="anchor" aria-label="永久链接：扩展上下文窗口" href="#extending-context-window"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华盛顿大学等</font></font></td>
<td><a href="https://github.com/ofirpress/attention_with_linear_biases"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">铝锂</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ALiBi不是在 Transformer 堆栈的底部添加位置嵌入，而是为每个注意力分数添加线性偏差，允许模型在</font><font style="vertical-align: inherit;">例如 1024 个标记</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上进行训练，然后对 2048 个（或更多）标记进行推理，而无需</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">任何微调。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深巴甫洛夫等</font></font></td>
<td><a href="https://arxiv.org/abs/2304.11062" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">远程管理技术</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用循环记忆来扩展上下文长度。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">字节跳动</font></font></td>
<td><a href="https://arxiv.org/abs/2304.11062" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">单片机</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">释放大规模语言模型的无限长度输入能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元</font></font></td>
<td><a href="https://arxiv.org/pdf/2306.15595.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">位置插补</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将基于 RoPE 的预训练 LLM（例如 LLaMA 模型）的上下文窗口大小扩展到最多 32768，并进行最少的微调（1000 步以内）。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">位置插值线性缩小输入位置索引以匹配原始上下文窗口大小，而不是推断超出</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">训练的上下文长度，这可能导致灾难性的高注意力分数，从而完全破坏自注意力机制。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/DachengLi1/LongChat"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">长聊</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们没有强制 LLaMA 模型适应position_ids &gt; 2048，而是将position_ids &gt; 2048 压缩到0 到2048 之间（与</font></font><a href="https://arxiv.org/pdf/2306.15595.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Position Interpolation</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相同的机制，令人惊讶！）。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们观察到，我们的 LongChat-13B-16K 模型可靠地检索了第一个主题，其准确度与 gpt-3.5-turbo 相当。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/unilm/tree/master#revolutionizing-transformers-for-mllms-and-agi"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">龙网</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用名为扩张注意力</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的新颖组件取代了普通 Transformers 的注意力</font><font style="vertical-align: inherit;">，并成功将序列长度扩展到 10 亿个令牌。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">想法 NCBR 等</font></font></td>
<td><a href="https://github.com/CStanKonrad/long_llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">龙骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LongLLaMA 建立在</font></font><a href="https://github.com/openlm-research/open_llama"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">OpenLLaMA的基础上，并使用</font></font></a><font style="vertical-align: inherit;"></font><a href="https://arxiv.org/abs/2307.03170" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Focused Transformer (FoT)</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法进行微调</font><font style="vertical-align: inherit;">，能够处理 256k 令牌甚至更多的长上下文。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">算盘.AI</font></font></td>
<td><a href="https://huggingface.co/abacusai/Giraffe-v2-13b-32k" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">长颈鹿</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了扩展 Llama 的上下文长度能力，进行了一系列不同方案的实验。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起电脑</font></font></td>
<td><a href="https://huggingface.co/togethercomputer/Llama-2-7B-32K-Instruct" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Llama-2-7B-32K-指示</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><a href="https://huggingface.co/togethercomputer/Llama-2-7B-32K" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据Llama-2-7B-32K</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行微调的长上下文聊天模型</font><font style="vertical-align: inherit;">，基于高质量的指令和聊天数据。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">苏建林</font></font></td>
<td><a href="https://github.com/bojone/rerope"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雷罗PE</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置一个大小为$w$的窗口，窗口内位置间隔为</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，窗口外位置间隔为</font></font><math-renderer class="js-inline-math" style="display: inline" data-static-url="https://github.githubassets.com/static" data-run-id="295840d3ed8916f9b8bdba5202d23ddc" data-catalyst=""><mjx-container style="position: relative;" jax="CHTML" class="MathJax CtxtMenu_Attached_0" tabindex="0" ctxtmenu_counter="0"><mjx-math aria-hidden="true" class="MJX-TEX"><mjx-mfrac><mjx-frac><mjx-num><mjx-nstrut></mjx-nstrut><mjx-mn size="s" class="mjx-n"><mjx-c class="mjx-c31"></mjx-c></mjx-mn></mjx-num><mjx-dbox><mjx-dtable><mjx-line></mjx-line><mjx-row><mjx-den><mjx-dstrut></mjx-dstrut><mjx-mi size="s" class="mjx-i"><mjx-c class="mjx-c1D458 TEX-I"></mjx-c></mjx-mi></mjx-den></mjx-row></mjx-dtable></mjx-dbox></mjx-frac></mjx-mfrac></mjx-math><mjx-assistive-mml display="inline" unselectable="on"><math xmlns="http://www.w3.org/1998/Math/MathML"><mfrac><mn>1</mn><mi>k</mi></mfrac></math></mjx-assistive-mml></mjx-container></math-renderer><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港中文大学/麻省理工学院</font></font></td>
<td><a href="https://github.com/dvlab-research/longlora"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">朗洛拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种有效的微调方法，可以扩展预训练大型语言模型 (LLM) 的上下文大小，且计算成本有限。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不扩展上下文窗口</font></font></h2><a id="user-content-without-extending-context-window" class="anchor" aria-label="永久链接：不扩展上下文窗口" href="#without-extending-context-window"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省理工学院/元/卡耐基梅隆大学</font></font></td>
<td><a href="https://github.com/mit-han-lab/streaming-llm"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">流媒体LLM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> / </font></font><br><a href="https://github.com/hpcaitech/SwiftInfer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SwiftInfer</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为无限长度的输入</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">部署法学硕士</font><font style="vertical-align: inherit;">，而不牺牲效率和性能。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个有效的框架，使使用有限长度注意窗口训练的法学硕士能够泛化到无限序列长度，而无需任何微调。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们证明 StreamingLLM 可以使 Llama-2、MPT、Falcon 和 Pythia 能够使用多达 400 万个甚至更多的令牌执行稳定且高效的语言建模。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，我们发现在预训练期间添加占位符令牌作为专用注意力接收器可以进一步改进流部署。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在流设置中，StreamingLLM 的性能比滑动窗口重新计算基线高出 22.2 倍。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SwiftInfer：基于&nbsp;</font></font><a href="https://github.com/NVIDIA/TensorRT-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TensorRT-LLM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实现StreamingLLM 。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://browse.arxiv.org/pdf/2310.01889.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">环注意</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们提出了一种独特的方法，即环注意力（Ring Attention），它利用自注意力的块式计算来跨多个设备分发长序列，同时将</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">键值块的通信与块式注意力的计算重叠。 Ring Attention 能够对序列进行训练和推理，其长度比之前的内存高效 Transformer 的长度要长出设备计数倍，从而</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有效地消除了各个设备所施加的内存限制。对语言建模任务的大量实验证明了环注意在允许大序列输入大小</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和提高性能方面</font><font style="vertical-align: inherit;">的有效性。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">联合银行</font></font></td>
<td><a href="https://github.com/cpacker/MemGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">记忆GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个智能管理法学硕士中不同记忆层的系统，以便在法学硕士有限的上下文窗口内有效地提供扩展上下文。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，MemGPT 知道何时将关键信息推送到矢量数据库以及何时在聊天中稍后检索它，从而实现永久对话。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">福州大学等</font></font></td>
<td><a href="https://github.com/OpenLMLab/scaling-rope"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">伸缩绳</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们首先观察到，在预训练上下文长度中使用更小或更大的基数微调基于 RoPE 的 LLM 可以显着提高其外推性能。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之后，我们提出了基于 RoPE 的外推的缩放定律，这是一个从周期角度来看的统一框架，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来描述外推性能和基值之间的关系以及调整上下文长度。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/thunlp/InfLLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">InfLLM 无需训练，基于记忆，将遥远的上下文存储到额外的记忆单元中，并采用有效的机制来查找与令牌相关的单元以进行注意力计算。即使序列长度缩放到 1, 024K，InfLLM 仍然可以有效捕获长距离依赖关系。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知识编辑</font></font></h1><a id="user-content-knowledge-editing" class="anchor" aria-label="永久链接：知识编辑" href="#knowledge-editing"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型编辑必读论文：</font></font><a href="https://github.com/zjunlp/ModelEditingPapers"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ModelEditingPapers</font></font></a></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省理工学院等</font></font></td>
<td><a href="https://rome.baulab.info/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">罗马</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，我们使用因果中介分析来追踪 GPT 中隐藏状态激活的因果效应，以识别介导有关主题的事实的回忆的特定模块。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的分析表明，在处理主题名称的最后一个标记时，一系列中间层的前馈 MLP 起着决定性的作用。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其次，我们通过引入一级模型编辑方法（ROME）来改变决定前馈层在决定性标记处行为的参数，从而在模型权重中测试这一发现。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管干预很简单，但我们发现 ROME 在标准零样本关系提取基准上与其他模型编辑方法同样有效。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实施</font></font></h2><a id="user-content-implementations" class="anchor" aria-label="永久链接：实施" href="#implementations"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学</font></font></td>
<td><a href="https://github.com/hiyouga/FastEdit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快速编辑</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用一个命令将</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新鲜</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">定制的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知识有效地注入大型语言模型中。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浙江大学</font></font></td>
<td><a href="https://github.com/zjunlp/EasyEdit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简易编辑</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于编辑大型语言模型 (LLM) 的 Python 包，例如</font></font><code>GPT-J</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>Llama</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>GPT-NEO</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>GPT2</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>T5</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（支持从</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1B</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到  </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">65B 的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型），</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其目标是在特定领域内有效地改变 LLM 的行为，而不会对其他输入的性能产生负面影响。它被设计为易于使用且易于扩展。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">外部知识</font></font></h1><a id="user-content-external-knowledge" class="anchor" aria-label="永久链接：外部知识" href="#external-knowledge"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">允许模型访问外部知识，例如互联网、KG、数据库。</font></font></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@jerryjliu</font></font></td>
<td><a href="https://github.com/jerryjliu/llama_index"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼指数</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供一个中央接口将您的法学硕士与外部数据连接起来。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@imClumsyPanda</font></font></td>
<td><a href="https://github.com/imClumsyPanda/langchain-ChatGLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">langchain-ChatGLM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于本地知识的 ChatGLM 和</font></font><a href="https://github.com/hwchase17/langchain"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">langchain</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@wenda-法学硕士</font></font></td>
<td><a href="https://github.com/wenda-LLM/wenda"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文达</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个LLM调用平台</font></font><a href="https://github.com/wenda-LLM/wenda">&nbsp;</a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，旨在为小型模型插件知识库寻找和设计自动执行动作，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以达到与大型模型相同的生成能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@csunny</font></font></td>
<td><a href="https://github.com/csunny/DB-GPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据库GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为所有基于数据库的场景构建完整的私有大模型解决方案。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四、巴艾、浙江大学</font></font></td>
<td><a href="https://github.com/huchenxucs/ChatDB"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天数据库</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种将符号记忆与法学硕士相结合的新颖框架。 ChatDB 探索了用符号记忆增强法学硕士的方法，以处理任意长度的上下文。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这样的符号内存框架被实例化为具有一组 SQL 数据库的 LLM。 LLM生成SQL指令来自</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主操作SQL数据库（包括插入、选择、更新和删除），旨在完成需要多跳推理和长期符号记忆的复杂任务。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主意</font></font></td>
<td><a href="https://modelscope.cn/models/Fengshenbang/Ziya-Reader-13B-v1.0/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子牙阅读器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“Ziya-Reader-13B-v1.0”是知识问答模型。它可以根据给定的问题和知识文档准确回答问题，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且适用于多文档和单文档问答。该模型具有 8k 上下文窗口，与具有更长窗口的模型相比，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们在多个长文本任务的评估中取得了胜利。这些任务包括多文档问答、综合任务（文档检索）和长文本摘要。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，该模型还表现出出色的泛化能力，使其能够用于一般问答。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它在我们的综合能力评估集上的表现超过了Ziya-Llama-13B。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">泊坞窗</font></font></td>
<td><a href="https://github.com/docker/genai-stack"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GenAI堆栈</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过将 Docker 与 Neo4j 图数据库、LangChain 模型链接技术以及用于运行大型语言模型 (LLM) 的 Ollama 集成，显着简化了整个流程</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ARC53</font></font></td>
<td><a href="https://github.com/arc53/DocsGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT 支持的文档聊天，与您的文档聊天。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">华盛顿大学等</font></font></td>
<td><a href="https://github.com/AkariAsai/self-rag"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自我RAG</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与广泛采用的检索增强生成（RAG）方法不同，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Self-RAG</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据不同的查询按需检索（例如，可以多次检索或完全跳过检索），并通过预测</font><strong><font style="vertical-align: inherit;">反射</font></strong></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从多个细粒度方面批评自己的生成</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代币</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为生成的一个组成部分。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中国人民大学</font></font></td>
<td><a href="https://github.com/JBoRu/StructGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结构GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">受到法学硕士工具增强研究的启发，我们开发了一个迭代阅读然后推理（IRR）框架来解决基于结构化数据的问答任务，称为 StructGPT。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这个框架中，我们构建了专门的接口来从结构化数据中收集相关证据（即阅读），并让LLM专注于基于收集到的信息的推理任务（即推理）。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特别地，我们提出了一种调用线性化生成过程来支持法学硕士借助接口对结构化数据进行推理。通过使用提供的接口迭代此过程，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的方法可以逐渐接近给定查询的目标答案。对三种类型的结构化数据进行的实验表明，StructGPT</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在少样本和零样本设置下</font><font style="vertical-align: inherit;">极大地提高了 LLM 的性能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京邮电大学</font></font></td>
<td><a href="https://github.com/LHRLAB/ChatKBQA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">聊天KBQA</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">带有微调法学硕士的知识库问答的“生成然后检索”框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浙江大学</font></font></td>
<td><a href="https://github.com/zjukg/KnowPAT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知道PAT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">知识偏好调整 (KnowPAT) 是一种将法学硕士与人类知识偏好保持一致的新渠道。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">KnowPAT 结合领域知识图来构建偏好集并设计新的对齐目标以微调法学硕士。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轻子人工智能</font></font></td>
<td><a href="https://github.com/leptonai/search_with_lepton"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用轻子搜索</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基于对话的搜索演示，例如 perplexity.ai。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">网易</font></font></td>
<td><a href="https://github.com/netease-youdao/QAnything"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Q任何事情</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本地知识库问答系统，旨在支持多种文件格式和数据库，允许离线安装和使用。使用</font></font><code>QAnything</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，您可以简单地删除本地存储的任何格式的文件，并获得准确、快速和可靠的答案。目前支持的格式包括：   </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PDF(pdf)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Word(docx)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PPT(pptx)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">XLS(xlsx)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Markdown(md)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Email(eml)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TXT(txt)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Image(jpg，jpeg，png)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> , </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CSV (csv)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">网页链接(html)</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和更多格式即将推出...</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无限流</font></font></td>
<td><a href="https://github.com/infiniflow/ragflow/tree/main"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RAG流</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个基于深度文档理解的开源 RAG（检索增强生成）引擎。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">dify.ai</font></font></td>
<td><a href="https://github.com/langgenius/dify"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">迪菲</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Dify 是一个开源 LLM 应用程序开发平台。 Dify 的直观界面结合了 AI 工作流程、RAG 管道、代理功能、模型管理、可观察性功能等，让您快速从原型转向生产。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sealos.io</font></font></td>
<td><a href="https://github.com/labring/FastGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快速GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FastGPT是一个基于LLM构建的知识型问答系统，提供开箱即用的数据处理和模型调用功能，允许通过流程可视化进行工作流程编排！</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与文档聊天</font></font></h2><a id="user-content-chat-with-docs" class="anchor" aria-label="永久链接：与文档聊天" href="#chat-with-docs"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@arc53</font></font></td>
<td><a href="https://github.com/arc53/DocsGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT 支持的文档聊天，与您的文档聊天</font></font></td>
</tr>
</tbody>
</table>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多信息请参见：</font></font><a href="https://github.com/fighting41love/funNLP?tab=readme-ov-file#%E7%B1%BBchatgpt%E7%9A%84%E6%96%87%E6%A1%A3%E9%97%AE%E7%AD%94"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">funNLP</font></font></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">矢量数据库</font></font></h2><a id="user-content-vector-database" class="anchor" aria-label="永久链接：矢量数据库" href="#vector-database"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">D b</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">milvus-io</font></font></td>
<td><a href="https://github.com/milvus-io/milvus"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">米尔武斯</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">存储和计算在设计上分离的云原生矢量数据库。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元</font></font></td>
<td><a href="https://github.com/facebookresearch/faiss"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">费斯</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它包含的算法可以搜索任意大小的向量集，甚至可能无法容纳在 RAM 中的向量集。它还包含用于评估和参数调整的支持代码。 Faiss 是用 C++ 编写的，带有 Python/numpy 的完整包装器。一些最有用的算法是在 GPU 上实现的。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nms库</font></font></td>
<td><a href="https://github.com/nmslib/hnswlib"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">汉斯库</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">带有 python 绑定、插入和更新的纯头文件 C++ HNSW 实现。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的量表</font></font></td>
<td><a href="https://github.com/myscale/myscaledb"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MyScaleDB</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个基于 ClickHouse 构建的开源高性能 SQL 矢量数据库。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">外部工具</font></font></h1><a id="user-content-external-tools" class="anchor" aria-label="永久链接：外部工具" href="#external-tools"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用现有工具</font></font></h2><a id="user-content-using-existing-tools" class="anchor" aria-label="永久链接：使用现有工具" href="#using-existing-tools"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">允许模型访问外部工具，如搜索引擎、api。</font></font></p>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基础模型</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">UCB/微软</font></font></td>
<td><a href="https://github.com/ShishirPatil/gorilla/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大猩猩</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">准确调用 1,600 多个（并且还在不断增加）API 调用，同时减少幻觉。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/OpenBMB/ToolBench"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">工具骆驼</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">骆驼</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该项目旨在构建</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开源、大规模、高质量的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令调优SFT数据，以方便构建具有通用</font><strong><font style="vertical-align: inherit;">工具使用</font></strong></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">能力的强大LLM </font><font style="vertical-align: inherit;">。我们提供数据集、相应的训练和评估脚本，</font><font style="vertical-align: inherit;">以及在 ToolBench 上微调的强大模型 ToolLLaMA。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font><br><font style="vertical-align: inherit;"></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">制作新工具</font></font></h2><a id="user-content-make-new-tools" class="anchor" aria-label="永久链接：制作新工具" href="#make-new-tools"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷歌等</font></font></td>
<td><a href="https://github.com/ctlllll/LLM-ToolMaker"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">洛杉矶TM</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士创建自己的可重用工具来解决问题。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代理人</font></font></h1><a id="user-content-agent" class="anchor" aria-label="永久链接： 代理" href="#agent"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@Significant-Gravitas</font></font></td>
<td><a href="https://github.com/Significant-Gravitas/Auto-GPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自动GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将法学硕士的“想法”链接在一起，自主实现您设定的任何目标。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@yoheinakajima</font></font></td>
<td><a href="https://github.com/yoheinakajima/babyagi"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">宝贝AGI</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该系统背后的主要思想是，它根据先前任务的结果和预定义的目标创建任务。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，该脚本使用 OpenAI 的自然语言处理 (NLP) 功能根据目标创建新任务，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并使用 Chroma/Weaviate 存储和检索上下文的任务结果。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/JARVIS"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">拥抱GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语言作为法学硕士连接众多人工智能模型以解决复杂人工智能任务的接口！</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软/北卡罗来纳州立大学</font></font></td>
<td><a href="https://github.com/billxbf/ReWOO"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">雷沃</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将推理过程与外部观察分离，从而显着减少代币消耗。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学</font></font></td>
<td><a href="https://github.com/joonspk-research/generative_agents"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成代理：人类行为的交互式模拟。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四等</font></font></td>
<td><a href="https://github.com/OpenBMB/AgentVerse"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特工宇宙</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">🤖 AgentVerse 🪐 提供了一个灵活的框架，简化了为大型语言模型 (LLM) 构建自定义多代理环境的过程。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北航等</font></font></td>
<td><a href="https://github.com/lijlansg/TrafficGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">交通GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过将大型语言模型和流量专业知识无缝结合，TrafficGPT 不仅可以推进流量</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">管理，还提供了一种利用该领域人工智能功能的新颖方法。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软等</font></font></td>
<td><a href="https://github.com/microsoft/ToRA"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">托拉</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ToRA 是一系列工具集成推理 LLM 代理，旨在通过与工具交互来解决具有挑战性的数学推理问题。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港大学</font></font></td>
<td><a href="https://github.com/xlang-ai/OpenAgents"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个在日常生活中使用和托管语言代理的开放平台。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/OpenBMB/XAgent"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">X代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个开源实验性大型语言模型（LLM）驱动的自主代理，可以自动解决各种任务。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它被设计为一个通用代理，可以应用于广泛的任务。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">英伟达等</font></font></td>
<td><a href="https://github.com/eureka-research/Eureka"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尤里卡</font></font></a></td>
<td><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由法学硕士支持的人类水平的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奖励设计算法</font><font style="vertical-align: inherit;">。 Eureka 利用</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最先进的 LLM（例如 GPT-4）</font><font style="vertical-align: inherit;">卓越的零样本生成、代码编写和上下文改进功能，对奖励代码执行上下文进化优化。</font><font style="vertical-align: inherit;">由此产生的奖励可以用于</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过强化学习来获得复杂的技能。 Eureka 生成的奖励函数优于专家人工设计的奖励，无需任何特定于任务的</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提示或预定义的奖励模板。在包含 10 种不同机器人形态的 29 个开源 RL 环境的多样化套件中， Eureka 在</font><strong><font style="vertical-align: inherit;">83%</font></strong></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的任务上优于人类专家，</font><font style="vertical-align: inherit;">导致平均标准化改进为  </font><strong><font style="vertical-align: inherit;">52%</font></strong><font style="vertical-align: inherit;">。</font></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">周四</font></font></td>
<td><a href="https://github.com/THUDM/AgentTuning"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代理调优</font></font></a></td>
<td><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AgentTuning</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代表了使用跨多个代理任务的交互轨迹来调整 LLM 指令的首次尝试。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">评估结果表明，AgentTuning 使法学硕士的代理能力能够对未见过的代理任务具有强大的泛化能力，同时保持良好的通用语言能力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/autogen"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自动生成器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">AutoGen 是一个框架，支持使用多个代理来开发 LLM 应用程序，这些代理可以相互对话来解决任务。 AutoGen 代理是</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可定制的、可对话的，并且无缝地允许人类参与。他们可以采用法学硕士、人力投入和工具组合的各种模式运作。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学</font></font></td>
<td><a href="https://github.com/Yifan-Song793/RestGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">休息GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们将法学硕士与</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RESTful API</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">连接起来，解决规划、API 调用和响应解析的实际挑战。为了全面评估 RestGPT 的性能，我们提出了  </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RestBench</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个高质量的基准测试，由两个真实场景和具有黄金解决方案路径的人工注释指令组成。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RestGPT采用迭代式从粗到精的在线规划框架，并使用执行器调用RESTful API。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">微软</font></font></td>
<td><a href="https://github.com/microsoft/muzic"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">音乐经纪人</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由大语言模型 (LLM) 提供支持的音乐领域代理。其目标是帮助开发者和非专业音乐创作者自动分析用户请求并选择合适的工具来解决问题。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">汉王等</font></font></td>
<td><a href="https://github.com/wiio12/LEGO-Prover"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">乐高-证明者</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一个由法学硕士支持的自动定理证明器，以逐块方式构建证明。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">阿里巴巴</font></font></td>
<td><a href="https://github.com/modelscope/modelscope-agent"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模型范围代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将 ModelScope 中的模型与世界连接起来的代理框架。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">卡耐基梅隆大学等</font></font></td>
<td><a href="https://github.com/Genesis-Embodied-AI/RoboGen"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">机器人生成器</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个生成和自我引导的机器人代理，可以不断地提出和掌握新技能。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">北京大学等</font></font></td>
<td><a href="https://github.com/PKU-RL/LLaMA-Rider"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">美洲驼骑士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个法学硕士培训框架，使法学硕士能够根据环境反馈和自身能力自主探索开放世界，并从收集的经验中高效学习。在 Minecraft 环境中，</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它表现出了比其他方法（包括 ChatGPT 任务规划器）更好的多任务处理能力。这种对开放世界的适应能力是法学硕士的一项重大成就。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，LLaMA-Rider 能够利用过去的任务经验来解决新任务，这证明了该方法在大型模型中进行终身探索和学习的潜力。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">想法等</font></font></td>
<td><a href="https://github.com/IDEA-FinAI/ToG"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">托格</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Think-on-Graph（ToG），LLM代理在KG上迭代执行波束搜索，发现最有希望的推理路径，并返回最有可能的推理结果。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">耶鲁等</font></font></td>
<td><a href="https://github.com/Ber666/ToolkenGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">工具肯GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将每个</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">工具</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表示为</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ken</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> &nbsp;( </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">toolken</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ) 并学习它的嵌入，以与生成常规单词标记相同的方式启用工具调用。一旦工具肯被触发，法学硕士就会被提示填写要执行的工具的参数。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">腾讯</font></font></td>
<td><a href="https://appagent-official.github.io/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应用程序代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们的框架使代理能够通过简化的动作空间来操作智能手机应用程序，模仿类人交互，例如点击和滑动。这种新颖的方法绕过了对系统后端访问的需求，从而扩大了其在不同应用程序中的适用性</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">斯坦福大学等</font></font></td>
<td><a href="https://arxiv.org/abs/2401.12954" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元提示</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这种方法将单个 LM 转变为多面导体，擅长管理和集成多个独立的 LM 查询。通过使用高级指令，元提示引导 LM 将复杂的任务分解为更小、更易于管理的子任务。然后，这些子任务由同一 LM 的不同“专家”实例处理，每个实例都在特定的、定制的指令下运行。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">腾讯</font></font></td>
<td><a href="https://github.com/MoreAgentsIsAllYouNeed/More-Agents-Is-All-You-Need"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您只需要更多代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们发现，只需通过采样和投票方法，大型语言模型（LLM）的性能就会随着实例化代理的数量而变化。此外，该方法与现有的复杂方法正交，以进一步增强LLM，而增强程度与任务难度相关。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">毕达哥拉斯</font></font></td>
<td><a href="https://github.com/Pythagora-io/gpt-pilot"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-飞行员</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT Pilot 旨在研究在开发人员监督实施的同时，可以利用多少 LLM 来生成完全可用、可投入生产的应用程序。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">深智慧等</font></font></td>
<td><a href="https://github.com/geekan/MetaGPT"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">元GPT</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多代理框架：第一家人工智能软件公司，迈向自然语言编程。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放BMB</font></font></td>
<td><a href="https://github.com/OpenBMB/XAgent"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">X代理</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于解决复杂任务的自主 LLM 代理。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">船员人工智能</font></font></td>
<td><a href="https://github.com/joaomdmoura/crewAI"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">船员人工智能</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于编排角色扮演、自主人工智能代理的尖端框架。通过促进协作智能，CrewAI 使代理能够无缝协作，处理复杂的任务。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">人工智能</font></font></td>
<td><a href="https://github.com/stitionai/devika"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">德维卡</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代理人工智能软件工程师，可以理解高级人类指令，将其分解为步骤，研究相关信息并编写代码以实现给定目标。 Devika 的目标是成为</font><font style="vertical-align: inherit;">Cognition AI 的</font></font><a href="https://www.cognition-labs.com/introducing-devin" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Devin</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的有竞争力的开源替代品。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放德文</font></font></td>
<td><a href="https://github.com/OpenDevin/OpenDevin"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放德文</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个开源项目，旨在复制 Devin，一名自主人工智能软件工程师，能够执行复杂的工程任务并在软件开发项目上与用户积极协作。该项目致力于通过开源社区的力量复制、增强和创新 Devin。</font></font></td>
</tr>
</tbody>
</table>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">论文列表 : </font></font><a href="https://github.com/WooooDyy/LLM-Agent-Paper-List"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLM-Agent-Paper-List</font></font></a></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">论文/存储库/博客/...：</font></font><a href="https://github.com/hyp1231/awesome-llm-powered-agent" title="论文/存储库/博客..."><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很棒的 LLM 支持的代理</font></font></a></p>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士 XXX</font></font></h1><a id="user-content-llms-as-xxx" class="anchor" aria-label="永久链接： 法学硕士 XXX" href="#llms-as-xxx"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">贡献者</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士作为</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回购协议</font></font></th>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要特征</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷歌深度思维</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">优化器</font></font></td>
<td><a href="https://arxiv.org/pdf/2309.03409.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">奥普罗</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Optimization by PROmpting (OPRO)，一种将法学硕士作为优化器的简单而有效的方法</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，其中优化任务以自然语言描述。在每个优化步骤中，LLM 根据包含</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">先前生成的解决方案及其值的提示生成新的解决方案，然后对新解决方案进行评估并将其添加到下一个优化步骤的提示中。</font></font></td>
</tr>
<tr>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">香港大学等</font></font></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">图形任务的一部分</font></font></td>
<td><a href="https://github.com/yhLeeee/Awesome-LLMs-in-Graph-tasks"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">令人敬畏的图任务中的法学硕士</font></font></a></td>
<td><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">精选的研究论文集，探索法学硕士在图形相关任务中的利用。</font></font></td>
</tr>
</tbody>
</table>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类似系列</font></font></h1><a id="user-content-similar-collections" class="anchor" aria-label="永久链接：类似集合" href="#similar-collections"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<table>
<thead>
<tr>
<th><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放式指令跟随 LLMS 集合</font></font></th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://zhuanlan.zhihu.com/p/628716889" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开源大型语言模型（LLM）合集</font></font></a></td>
</tr>
<tr>
<td><a href="https://sota.jiqizhixin.com/models/list" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">机器之心SOTA!模型</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/nichtdax/awesome-totally-open-chatgpt"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">太棒了 完全开放 Chatgpt</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/DAMO-NLP-SG/LLM-Zoo"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">动物园法学硕士</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/Hannibal046/Awesome-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">太棒了-LLM</font></font></a></td>
</tr>
<tr>
<td><a href="https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">🤗 打开 LLM 排行榜</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/eugeneyan/open-llms"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开放法学硕士</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/HqWu-HITCS/Awesome-Chinese-LLM"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">太棒了-中文-法学硕士</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/lonePatient/awesome-pretrained-chinese-nlp-models"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很棒的预训练中文 NLP 模型</font></font></a></td>
</tr>
<tr>
<td><a href="https://github.com/RUCAIBox/LLMSurvey"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">法学硕士调查</font></font></a></td>
</tr>
</tbody>
</table>
</article></div>
