# awesome-self-consuming-ai-papers
Papers about self-consuming generative models, which have a tendency to go MAD or collapse.

Sorted by upload date (oldest first). Updated as of 5/14/2024.

### "Solving" MADness:
1. Self-Correcting Self-Consuming Loops for Generative Model Training
2. Is Model Collapse Inevitable? Breaking the Curse of Recursion by Accumulating Real and Synthetic Data (Donoho's paper)

### Analyzing or explaining self-consumption/MADness:
1. On the Stability of Iterative Retraining of Generative Models on their own Data
2. Model Collapse Demystified: The Case of Regression
3. A Tale of Tails: Model Collapse as a Change of Scaling Laws (same authors as Model Collapse Demystified)
4. Towards Theoretical Understandings of Self-Consuming Generative Models
5. Heat Death of Generative Models in Closed-Loop Learning

### Additional observations of MADness in self-consumption:
1. The Curious Decline of Linguistic Diversity: Training Language Models on Synthetic Text
2. Large Language Models Suffer From Their Own Output: An Analysis of the Self-Consuming Training Loop
3. Nepotistically Trained Generative-AI Models Collapse
4. AI and the Problem of Knowledge Collapse

### Ethical and societal implications of MADness:
1. [arXiv 23] [Are Large Language Models a Threat to Digital Public Goods? Evidence From Activity on Stack Overflow](https://arxiv.org/abs/2307.07367)
   * ChatGPT poses a threat to digital public goods like Stack Overflow since it can answer some questions itself; its answers are privately generated for users, and are thus not uploaded online, hence reducing the amount of activity on Stack Overflow for programming languages which Stack Overflow has sufficient knowledge of.
   * Authors: Maria del Rio-Chanona, Nadzeya Laurentsyeva, Johannes Wachs
2. [arXiv 23] [Generative Artificial Intelligence Enhances Creativity but Reduces the Diversity of Novel Content](https://arxiv.org/abs/2311.09807)
   * LLMs are finetuned recursively; the authors measure their creativity via novel metrics targeting lexical, syntactic, and semantic diversity. They show a consistent decrease in the diversity of the model outputs through successive iterations, which can be especially concerning for tasks demanding high levels of creativity. 
   * Authors: Yanzhu Guo, Guokan Shang, Michalis Vazirgiannis, Chloé Clavel
3. LLMs may dominate information access: Neural retrievers are biased towards LLM-generated texts

### Self-consumption for good (i.e., training generative models on AI-generated or AI-curated data):
1. [ICLR 24 rejected] [Upgrading VAE Training With Unlimited Data Plans Provided by Diffusion Models](https://openreview.net/forum?id=pyW37euNXb)
   * The paper introduces a novel approach for training VAEs using samples from a pre-trained diffusion model to address the overfitting problem in VAE encoders, which improves generalization performance, amortization gap, and robustness over traditional training methods. Note that this method relies on the accuracy of the diffusion model and adds significant computaitonal overhead.
   * Authors: Tim Z. Xiao, Johannes Zenn, Robert Bamler
2. Bootstrapping LLM-based Task-Oriented Dialogue Agents via Self-Talk
3. Iterated Denoising Energy Matching for Sampling from Boltzmann Densities
4. How to Train Data-Efficient LLMs
