> For a healthier future in AI

The following is an abstract of some thoughts i had from the RWKV podcast found here: https://www.latent.space/p/rwkv#details
# Why Alternatives Matters ?

Transformers architecture is at its peak now with the AI revolution of 2023. However in all the rush placed onto it due to recent success. It's easy to ignore alternatives, that we can be learning from.

And it matters, because as Engineers, we should not be using a one size fit all solution of a hammer for every problem nail. We should be finding trade-offs, in every solution.

Failure to do so, would lead us trapped within the limitation of one particular platform. While being blissfully unaware of all others alternatives. Potentially holding back on future development for years.

And this problem is not unique to "AI". It's a pattern in history that does tend to repeat itself, from ancient times. To modern times.

**A page from the SQL war history...**

A notable recent example, in software development. Was the trend towards NoSQL, when SQL servers started hitting their physical limitations. Startups all over, made the giant move towards NoSQL for "scale" reasons, despite being no where close to those scales. 

However overtime, as eventual-consistency, and NoSQL management overhead issues start to pile up, and as hardware capabilities made giant leap frogs in speed and capacity in SSD. We see a recent trend back towards SQL based servers for their simplicity, and its scalability being sufficient for 90+% of almost all startups.

Does that mean SQL is better then NoSQL. Or vice-visa? Neither, its simply just means each technology has its preferred use case, with their pros-and-cons. And their learning points, which can be cross-pollinated among similar technologies.

> As such I hope you view this article as not an attack on transformers, but a healthy appreciation on alternatives. With that, lets get on to the main topic

---

# What is the biggest pain point for existing transformer architecture?

In general this covers compute, context length, datasets and alignment. For this conversation, we will be focusing on compute, and context length

- Quadratic computation costs, due to an `O(N^2)` computational cost increase for every input and output token used or generated. Making context sizes of >100k incredibly expensive to compute. This directly impact both inference and training cost
- The current GPU shortage for AI infrastructure significantly makes this a bigger issue
- Limitation in context size window, and the ability to pay attention to them - heavily limiting "smart agents" use cases (like [smol-dev](https://github.com/PicoCreator/smol-dev-js) ), forcing such systems to use work arounds. The larger the context size we can push, the less work arounds we will need (we are putting aside the lack of dataset issue for now, as that happens regardless of architecture)

So how do we solve this?

# Introducing RWKV - a linear transformer / modern large scale RNN

> The following is based on the RWKV paper found here at a high level : [https://arxiv.org/abs/2305.13048](https://arxiv.org/abs/2305.13048) 
> If you would like to have a much deeper technical dive on RWKV architecture, you can find resources on its [wiki page here](https://wiki.rwkv.com/advance/architecture.html#how-does-wkv-works-i-want-the-nitty-gritty-where-do-i-find-it)

[RWKV](https://arxiv.org/abs/2305.13048), along with [Microsoft RetNet](https://arxiv.org/abs/2307.08621) are among the first in potentially a new class of AI models collectively called ["Linear Transformers"](https://linear-transformers.com/)

It tackles the above 3 limitations directly by supporting the following
- Linear computational cost for each tokens regardless of context size. 
- Due to its relatively lower system requirements in RNN mode, it can give reasonable token/sec output on CPU systems (especially ARM chips)
- No hard limitation of the context size window, as its an RNN. (any limits RWKV documents is guideline limits the model is trained the model for, you are free to finetune, and use beyond said limits)

As we continue to scale up AI models, to large context sizes. From 100k and beyond. The quadratic computational costs starts to exponentially increase. Slowly negating the scalability benefits in which transformer replaced its predecessor: Recurrent Neural Networks. Which were known for its scaling bottlenecks, which prevented it from growing past the billion parameter scale.

Linear Transformers, however instead of abandoning the Recurrent Neural Network architecture. Took lessons learnt from making transformers scalable, and re-engineered RNN's to work similar to transformers, and remove all those bottleneck. 

Bringing them back into the race with transformers, in terms of training speeds. Allowing them to both operate efficiently at `O(N)` cost, while scaling past a billion parameters in training. All while maintaining similar performance levels.

![[linear-transformer-computational-cost.png]]
> Graph showing linear transformer computational cost scaling linearly per token -vs- expotential cost increases for transformer models
 
At this point of writing, RWKV is the largest OSS avaliable linear transformer. At 14B parameter counts, running on par with GPT-NeoX or other transformers with similar dataset training data (ie. the pile)

![[zero-shot-pile-perf.png]]

But what does this mean, in simpler terms?

**Pros**
- Its over 10x cheaper to infer and train then transformer, especially on large context sizes
- Its can run slowly on very limited hardware in RNN mode
- With the same dataset, it runs on par with existing transformer architecture
- It does not have a technical limit to its context size (its an RNN)

**Cons**
- It suffers from a varient of the sliding window problem, as it can only compress and store "so much" information into its memory state (note that similar challenges to attention is faced for transformer with >8k context sizes)
- It is not yet proven to scale beyond 14B parameters
- It is not as optimised / well adopted in both training and dataset, as compared to transformers

So while RWKV is not yet at the same training scale as existing 60B+ LLaMA models and their alternatives (both in dataset used, and param count). Greatly limiting its use cases when compared to such models.

The point here, is that with the right support and resources. It has the potential to go beyond existing models, with much lower running cost, and larger context size. Especially with the increasing trend towards smaller, efficient expert models.

So keep this on your radar for future developments. 
And if its efficiency is desired for your use case, why not give it a consideration?

> Also one last thing i forget to mentioned:
> Linear Transformers typically do not use classic Transformer attention, but an approximate equivalent, meaning ...
> 
> [**Attention is Not All You Need**](https://arxiv.org/abs/2103.03404)

---

## Other alternatives and its benefits we should probably learn from

- **Diffusion Models** : while they are incredibly slow (expensive) to train for text models. They are extreamly resillient to multi-epoch training, in the hundreds - and has proven itself in the image space. Figuring out why it is resillient to multi-epoch training, [maybe essential in mitigating the token crisis](https://arxiv.org/abs/2305.13230)
  
- **Generative Adversarial Networks / Agents** : techniques could be used to train desired skillsets, to a specific goal without datasets. Even for text based models

---

> Disclosure: I am a code contributor to the RWKV project, and an active member in the community. 
> 
> However it does not mean I view RWKV as the final answer, even if in the future where "Linear Transformers" beat out traditional "Transformer" networks in the future, research into alternatives is still important for healthy ecosystem development. 
> 
> I strongly believe there is no such thing as "one architecture to rule them all"
> 
> Additionally, i am aware there has since been developments like TransformerXL to more efficiently scale transformers, somewhere between quadratic cost, and linear cost. However with very limited known implementation of this method in public, it is hard for me to evaluate its pros and cons.
