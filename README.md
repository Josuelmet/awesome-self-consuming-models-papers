# awesome-self-consuming-ai-papers
Papers about self-consuming generative models, which have a tendency to go MAD or collapse.

Sorted by upload date (oldest first). Updated as of 5/14/2024.

### Foundational work:
1. [arXiv 23] [The Curse of Recursion: Training on Generated Data Makes Models Forget](https://arxiv.org/abs/2305.17493)
2. [ICLR 24] [Self-Consuming Generative Models Go MAD](https://openreview.net/forum?id=ShjMHfmPs0)

### "Solving" MADness:
1. [arXiv 24] [Self-Correcting Self-Consuming Loops for Generative Model Training](https://arxiv.org/abs/2402.07087)
   * The authors try to stabilize self-consuming generative model training. Introducing an idealized correction function, which maps a data point to be more likely under the true data distribution, theoretically stabilizes self-consumption exponentially. The authors propose self-correction functions, which rely on expert knowledge (e.g. the laws of physics programmed in a simulator), and empirically validate their effectiveness at avoiding model collapse on a human motion synthesis task (even when the ratio of synthetic data to real data is as high as 100%).
   * Nate Gillman, Michael Freeman, Daksh Aggarwal, Chia-Hong Hsu, Calvin Luo, Yonglong Tian, Chen Sun
2. [arXiv 24] [Is Model Collapse Inevitable? Breaking the Curse of Recursion by Accumulating Real and Synthetic Data](https://arxiv.org/abs/2404.01413) 
   * The authors show that accumulating the successive generations of synthetic data alongside the original real data avoids model collapse. To understand why, they use an analytically tractable framework introduced by prior work in which a sequence of linear models are fit to the previous models' outputs. Under this framework, data accumulation provably limits the test error by a finite upper bound independent of the number of iterations (meaning model collapse no longer occurs).
   * Matthias Gerstgrasser, Rylan Schaeffer, Apratim Dey, Rafael Rafailov, Henry Sleight, John Hughes, Tomasz Korbak, Rajashree Agrawal, Dhruv Pai, Andrey Gromov, Daniel A. Roberts, Diyi Yang, David L. Donoho, Sanmi Koyejo
3. [arXiv 24] [Removing Bias from Maximum Likelihood Estimation with Model Autophagy](https://arxiv.org/pdf/2405.13977)
   * The authors propose autophagy-Penalized Likelihood Estimation (PLE), which uses hypernetworks to outperform Maximum-Likelihood Estimation (MLE) with respect to minority-class fairness and stability in self-consumption.
   * Paul Mayer, Lorenzo Luzi, Ali Siahkoohi, Don H. Johnson, Richard G. Baraniuk

### Analyzing or explaining self-consumption/MADness (via theory):
1. [arXiv 24] [A Tale of Tails: Model Collapse as a Change of Scaling Laws](https://arxiv.org/abs/2402.07043) (same authors as Model Collapse Demystified)
   * Neural scaling laws predict the improvements of large models when increasing capacity and the size of training data. How will the scaling laws change when training data is partially synthetic? The authors develop a theoretical framework of model collapse through the lens of scaling laws. They discover a wide range of decay phenomena, analyzing loss of scaling, shifted scaling with number of generations, the "un-learning" of skills, and grokking when mixing human and synthesized data. Their theory is validated by large-scale experiments with a transformer on an arithmetic task and text generation using the large language model Llama2.
   * Elvis Dohmatob, Yunzhen Feng, Pu Yang, Francois Charton, Julia Kempe
2. [ICLR 24] [On the Stability of Iterative Retraining of Generative Models on their own Data](https://openreview.net/forum?id=JORAfH2xFd)
   * The authors provide a theoretical understanding of when generative models iteratively re-trained on their own data diverge from the original target distribution. They provide theoretical proofs (with Gaussians) that suggest that if the share of generated data w.r.t. the original data is small enough, this training can still be stable, whereas otherwise it collapses.
   * Quentin Bertrand, Joey Bose, Alexandre Duplessis, Marco Jiralerspong, Gauthier Gidel
3. [arXiv 24] [Model Collapse Demystified: The Case of Regression](https://arxiv.org/abs/2402.07712)
   * The authors study self-consumption in high-dimensional regression and obtain analytic formulae which quantitatively outline the phenomenon of MADness / model collapse in a broad range of regimes. In the special case of polynomial decaying spectral and source conditions, they obtain modified scaling laws which exhibit new crossover phenomena from fast to slow rates. They also propose a simple strategy based on adaptive regularization to mitigate model collapse.
   * Elvis Dohmatob, Yunzhen Feng, Julia Kempe
4. [arXiv 24] [Towards Theoretical Understandings of Self-Consuming Generative Models](https://arxiv.org/abs/2402.11778)
   * The authors construct a kernel-based theoretical framework to rigorously evaluate how this self-consumption in training impacts the data distributions learned by future models. They derive bounds on the total variation (TV) distance between future synthetic data and the original real data distribution under various scenarios; this distance can be effectively controlled under the condition that mixed training dataset sizes or proportions of real data are large enough. Interestingly, while the TV distance exhibits an initial ascent, it declines beyond a threshold point. The authors also specialize their general results to diffusion models, delivering nuanced insights such as the efficacy of optimal early stopping within self-consumption.
   * Shi Fu, Sen Zhang, Yingjie Wang, Xinmei Tian, Dacheng Tao
5. [arXiv 24] [Heat Death of Generative Models in Closed-Loop Learning](https://arxiv.org/abs/2404.02325)
   * The authors study the learning dynamics of self-consuming generative models using both synthetic and real data. Using dynamical systems tools, they show that, unless a sufficient amount of external data is introduced at each iteration, any non-trivial temperature during sampling leads the models to asymptotically degenerate: either the generative distribution collapses to a small set of outputs, or becomes uniform over a large set of outputs.
   * Matteo Marchi, Stefano Soatto, Pratik Chaudhari, Paulo Tabuada

### Additional observations of MADness in self-consumption:
1. [arXiv 23] [Nepotistically Trained Generative-AI Models Collapse](https://arxiv.org/abs/2311.12202)
   * When retrained on even small amounts of their own creation, Stable Diffusion produces highly distorted images; this distortion extends beyond the text prompts used in retraining. Furthermore, once poisoned, the Stable Diffusion struggles to fully heal even after retraining on only real images.
   * Matyas Bohacek, Hany Farid
2. [arXiv 23] [The Curious Decline of Linguistic Diversity: Training Language Models on Synthetic Text](https://arxiv.org/abs/2311.09807)
   * LLMs are finetuned recursively; the authors measure their creativity via novel metrics targeting lexical, syntactic, and semantic diversity. They show a consistent decrease in the diversity of the model outputs through successive iterations, which can be especially concerning for tasks demanding high levels of creativity. 
   * Yanzhu Guo, Guokan Shang, Michalis Vazirgiannis, Chloé Clavel
3. [arXiv 23] [Large Language Models Suffer From Their Own Output: An Analysis of the Self-Consuming Training Loop](https://arxiv.org/abs/2311.16822)
   * Self-consumption in LLMs can initially improve both quality and diversity. However, after a few generations the output inevitably degenerates in diversity - the rate of degeneration depends on the proportion of real and generated data.
   * Martin Briesch, Dominik Sobania, Franz Rothlauf

### Ethical and societal implications of MADness:
1. [arXiv 23] [Are Large Language Models a Threat to Digital Public Goods? Evidence From Activity on Stack Overflow](https://arxiv.org/abs/2307.07367)
   * ChatGPT poses a threat to digital public goods like Stack Overflow since it can answer some questions itself; its answers are privately generated for users, and are thus not uploaded online, hence reducing the amount of activity on Stack Overflow for programming languages which Stack Overflow has sufficient knowledge of.
   * Maria del Rio-Chanona, Nadzeya Laurentsyeva, Johannes Wachs
2. [arXiv 23] [Generative Artificial Intelligence Enhances Creativity but Reduces the Diversity of Novel Content](https://arxiv.org/abs/2312.00506)
   * This is an online experimental study where some writers could obtain ideas for a story from a generative AI platform. Access to AI increases the writers' creativity, with stories being evaluated as better written and more enjoyable, especially among less creative writers. However, AI-enabled stories are more similar to each other than stories by humans alone.
   * Anil R. Doshi, Oliver P. Hauser
3. [arXiv 24] [Feedback Loops With Language Models Drive In-Context Reward Hacking](https://arxiv.org/abs/2402.06627)
   * LLM feedback loops can cause in-context reward hacking (ICRH): for example, an LLM agent deployed to increase Twitter engagement may retrieve its own previous tweets and make them more controversial, increasing engagement but also toxicity. The authors identify and study two processes that lead to ICRH: output-refinement and policy-refinement, and provide three recommendations for evaluation to capture more instances of ICRH. 
   * Alexander Pan, Erik Jones, Meena Jagadeesan, Jacob Steinhardt
4. [ICLR 2024 AGI Workshop] [Neural Retrievers are Biased Towards LLM-Generated Content](https://openreview.net/forum?id=taFdHx5RTd)
   * Neural retrieval models (i.e., for search engines) tend to rank LLM-generated documents higher. The authors find this is because LLM-generated texts exhibit more focused semantics with less noise, making them easier for neural retrievers to semantic match. They thus also propose a plug-and-play debiased constraint for neural retrieval.
   * Sunhao Dai, Yuqi Zhou, Liang Pang, Weihao Liu, Xiaolin Hu, Yong Liu, Xiao Zhang, Gang Wang, Jun Xu
5. [arXiv 24] [AI and the Problem of Knowledge Collapse](https://arxiv.org/abs/2404.03502)
   * Unlike humans, AI models cannot choose their training data or seek out diverse forms of knowledge. To identify conditions under which knowledge collapse occurs, the author provides a simple model in which a community of learners or innovators choose traditional or AI-assisted methods. A 20% discount on AI-generated content generates public beliefs 2.3 times further from the truth than when there is no discount. An empirical approach to measuring the distribution of LLM outputs is provided in theoretical terms and illustrated through a specific example.
   * Andrew J. Peterson

### Self-consumption for good (i.e., training generative models on AI-generated or AI-curated data):
1. [arXiv 23] [Fair GANs through model rebalancing for extremely imbalanced class distributions](https://arxiv.org/abs/2308.08638)
   * GANs that have learned imbalanced distributions are made balanced by self-generated data that has been sampled with an evolutionary algorithm so as to be balanced. The authors validate this method with StyleGAN2 and FFHQ/CIFAR10.
   * Anubhav Jain, Nasir Memon, Julian Togelius
2. [ICLR 24 rejected] [Upgrading VAE Training With Unlimited Data Plans Provided by Diffusion Models](https://openreview.net/forum?id=pyW37euNXb)
   * The paper introduces a novel approach for training VAEs using samples from a pre-trained diffusion model to address the overfitting problem in VAE encoders, which improves generalization performance, amortization gap, and robustness over traditional training methods. Note that this method relies on the accuracy of the diffusion model and adds significant computaitonal overhead.
   * Tim Z. Xiao, Johannes Zenn, Robert Bamler
3. [arXiv 24] [Bootstrapping LLM-based Task-Oriented Dialogue Agents via Self-Talk](https://arxiv.org/abs/2401.05033)
   * LLM training data is generated via "self-talk". The authors introduce an automated way to measure the (partial) success of a dialogue. This metric is used to filter the generated conversational data that is fed back in LLM for training. The authors show that such self-talk data improves performance and have certain characteristics could be connected to their potential utility as training data.
   * Dennis Ulmer, Elman Mansimov, Kaixiang Lin, Justin Sun, Xibin Gao, Yi Zhang
4. [arXiv 24] [Iterated Denoising Energy Matching for Sampling from Boltzmann Densities](https://arxiv.org/abs/2402.06121)
   * iDEM is a scalable and efficient method to sample from unnormalized probability distributions. It makes use of the DEM objective, inspired by the stochastic regression and simulation-free principles of score and flow matching objectives while allowing one to learn off-policy, in a loop while itself generating new states which are subsequently learned on.
   * Tara Akhound-Sadegh, Jarrid Rector-Brooks, Avishek Joey Bose, Sarthak Mittal, Pablo Lemos, Cheng-Hao Liu, Marcin Sendera, Siamak Ravanbakhsh, Gauthier Gidel, Yoshua Bengio, Nikolay Malkin, Alexander Tong
5. [arXiv 24] [How to Train Data-Efficient LLMs](https://arxiv.org/abs/2402.09668)
   * The authors investigate whether LLMs can curate data samples that sufficiently describe a real training set while being much more concise. They propose querying LLMs to assess the quality of training samples; the resulting curated data can train models up to 70% faster than real data, even when rejecting up to 90% of the original real dataset. 
   * Noveen Sachdeva, Benjamin Coleman, Wang-Cheng Kang, Jianmo Ni, Lichan Hong, Ed H. Chi, James Caverlee, Julian McAuley, Derek Zhiyuan Cheng
6. [CVPR SyntaGen 24] [Is Synthetic Data all We Need? Benchmarking the Robustness of Models Trained with Synthetic Images](https://openreview.net/forum?id=wPW3k20lkW)
   * The authors compare real and synthetic images for training robust supervised, self-supervised, or multi-modal models. Self-supervised and multi-modal models can achieve equal robustness with either source of data, but supervised models are generally more robust when trained on real data. Additionally, synthetically trained models are more vulnerable to adversarial attacks and common corruptions, most likely due to the lack of realistic noise present in synthetic datasets. Synthetic clones also display a stronger shape bias compared to models trained on real images. Lastly, synthetically trained models benefit from more training samples, a mixture of real and synthetic images, and more diversity in the synthetic training data.
   * Krishnakant Singh, Thanush Navaratnam, Jannik Holmer, Simone Schaub-Meyer, Stefan Roth

