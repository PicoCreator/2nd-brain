> For a healthier future in AI

The following is an abstract of some thoughts i had from the RWKV podcast found here: https://www.latent.space/p/rwkv#details
# Why Alternatives Matters ?

Transformer architectures are currently at their peak with the AI revolution of 2023. However, in the rush to adopt them due to their recent success, it's easy to ignore alternatives that we can learn from.

As engineers, we should not take a one-size-fits-all approach, using the same hammer for every nail. We should find trade-offs in every solution. Failure to do so would trap us within the limitations of one particular platform, while remaining blissfully unaware of all other alternatives. This could potentially hold back development for years.

This problem is not unique to AI. It's a historical pattern that has repeated itself since ancient times up to the modern day.

**A page from the SQL war history...**

A notable recent example in software development was the trend towards NoSQL when SQL servers started hitting physical limitations. Startups everywhere made the move to NoSQL for "scale" reasons, despite being nowhere near those scales.

However, over time as eventual consistency and NoSQL management overhead emerged, and hardware capabilities made giant leaps in SSD speed and capacity, we've seen a recent trend back to SQL servers for their simplicity and now sufficient scalability for 90%+ of startups.

Does this mean SQL is better than NoSQL or vice versa? No, it simply means each technology has preferred use cases with pros/cons and learning points that can cross-pollinate among similar technologies.

> I hope you view this article as not an attack on transformers, but a healthy appreciation on alternatives. With that, lets get on to the main topic

---

# What is the biggest pain point for existing transformer architecture?

Generally this covers compute, context length, datasets and alignment. For this discussion, we'll focus on compute and context length:

- Quadratic computational costs due to `O(N^2)` increase per token used/generated. This makes context sizes >100k incredibly expensive. Which impacts inference and training.
- Current GPU shortage exacerbates this issue.
- Context size limits attention, heavily restricting "smart agent" use cases (like [smol-dev](https://github.com/PicoCreator/smol-dev-js)), forcing workarounds. Larger contexts need fewer workarounds.

So how do we solve this?

# Introducing RWKV - a linear transformer / modern large scale RNN

> The following summarises the RWKV paper at a high level: [https://arxiv.org/abs/2305.13048](https://arxiv.org/abs/2305.13048)
> For a deeper technical dive on RWKV architecture, see the [wiki](https://wiki.rwkv.com/advance/architecture.html#how-does-wkv-works-i-want-the-nitty-gritty-where-do-i-find-it).

[RWKV](https://arxiv.org/abs/2305.13048), along with [Microsoft RetNet](https://arxiv.org/abs/2307.08621), are among the first of a new class called ["Linear Transformers"](https://linear-transformers.com/).
It tackles the above 3 limitations directly by supporting the following

- Linear computational cost regardless of context size.
- Lower requirements allow reasonable token/sec output on CPU (especially ARM) in RNN mode.
- No hard context size limit as an RNN. Any limits in docs are guidelines - you can finetune beyond them.

As we continue to scale up AI models, to large context sizes. From 100k and beyond. The quadratic computational costs starts to exponentially increase. 

Linear Transformers, however instead of abandoning the Recurrent Neural Network architecture and their bottlenecks which forced them to be replaced by transformers. 

Took lessons learnt from making transformers scalable, and re-engineered RNN's to work similar to transformers, and remove all those bottleneck. 

Bringing them back into the race with transformers, in terms of training speeds. Allowing them to both operate efficiently at `O(N)` cost, while scaling past a billion parameters in training. All while maintaining similar performance levels.

![[linear-transformer-computational-cost.png]]
>Graph showing linear transformer computational cost scaling linearly per token vs. exponential increases for transformers
 
At 14B parameters, RWKV is the largest open-source linear transformer, on par with GPT-NeoX and others on similar datasets (e.g. The Pile).

![[zero-shot-pile-perf.png]]

But what does this mean, in simpler terms?

**Pros**
- 10x+ cheaper inference/training than transformers at large context sizes
- Can run slowly on very limited hardware in RNN mode
- Similar performance to transformers on same datasets
- No technical context size limit as RNN

**Cons**
- Sliding window problem, with lossy memory past a certain point
- Not proven to scale beyond 14B parameters yet
- Less optimised and adopted than transformers
  
So while RWKV isn't yet at 60B+ parameter scales like LLaMA2, with the right support/resources it has potential to get there at lower cost and larger contexts. Especially as expert models trend towards smaller and efficient.

Consider it if efficiency matters for your use case. But it's not the final solution - healthy alternatives are still key.

> Also one last thing i forget to mentioned:
> Linear Transformers typically do not use classic Transformer attention, but an approximate equivalent, meaning ...
> 
> [**Attention is Not All You Need**](https://arxiv.org/abs/2103.03404)

---

## Other alternatives and its benefits we should probably learn from

- **Diffusion Models**: Slow to train for text, but extremely resilient to multi-epoch training. Figuring out why could help mitigate the [token crisis](https://arxiv.org/abs/2305.13230)
  
- **Generative Adversarial Networks / Agents** : techniques could be used to train desired skillsets, to a specific goal without datasets. Even for text based models

---

> Disclosure: I am a code contributor to the RWKV project, and an active member in the community. 
> 
> However it does not mean I view RWKV as the final answer, even if in the future where "Linear Transformers" beat out traditional "Transformer" networks in the future, research into alternatives is still important for healthy ecosystem development. 
> 
> I strongly believe there is no such thing as "one architecture to rule them all"
> 
> Additionally, i am aware there has since been developments like TransformerXL to more efficiently scale transformers, somewhere between quadratic cost, and linear cost. However with very limited known implementation of this method in public, it is hard for me to evaluate its pros and cons.
