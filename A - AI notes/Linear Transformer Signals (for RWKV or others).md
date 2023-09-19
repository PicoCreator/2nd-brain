JosephJack @ GP of OSSCapital: 
https://twitter.com/JosephJacks_/status/1699295752638578796
> You heard it here first: Neural Net architectures that are fundamentally more compute efficient at training and inference time (by orders of magnitude) are a direct threat to NVIDIAs current growth dynamic.

Emad Mostaque @ Founder of Stability.AI
https://news.ycombinator.com/item?id=37368264
> (On RWKV) They have the potential for far better edge inference and also benefits longer context windows.
> 
> There are other architectures out there too we are supporting, I would be surprised if the current transformer LLM paradigm is what we use in a few years

Swyx @ latent.space
https://www.latent.space/p/rwkv#details
> most significant challenger to (transformer) emerge this year has been [RWKV - Receptance Weighted Key Value models](https://huggingface.co/blog/rwkv), which revive the RNN for GPT-class LLMs, inspired by a 2021 paper on [Attention Free Transformers](https://arxiv.org/abs/2105.14103) from Apple (surprise!).

Quentin Anthony @ Head of HPC at EleutherAI
https://www.latent.space/p/transformers-math#details
> there's a paper that I was involved with called RWKV that I would recommend people read

Tri Dao @ Stanford, Creator of FlashAttention, Founder of Together AI
https://www.latent.space/p/flashattention
> RWKV scale up to, they have a model at 14 billion that seems pretty competitive with Transformer. So that's really exciting. That's kind of an intellectual thing. We want to figure out if attention is necessary.

Tianqi Chen @ Founder of OctoML
https://www.latent.space/p/llms-everywhere
> (you looking out for anything post-transformers as far as architecture is concerned?)
> there is an open source version called RWKV. It's like a recurrent models that allows you to summarize things. Actually, we are bringing RWKV to MOC as well !

Siraj Raval @ Founder of GPT School, Ex-Twilio
https://twitter.com/sirajraval/status/1699497361863762025
> Attention is NOT all you need? There's a new Recurrent Neural Net with Transformer-level performance for training & MUCH faster inference. 🔥 It's called RWKV (Receptance Weighted Key Value). Recurrence returns!

Matt Shumer @ CEO [@HyperWriteAI](https://twitter.com/HyperWriteAI), [@OthersideAI](https://twitter.com/OthersideAI)
https://twitter.com/mattshumer_/status/1699054234992320924?s=20
> Yes!! I’ve been following the RWKV project (even evaluated it for some internal models) for a while now. Great to see it getting some attention (hah).

Yannic Kilcher @ CTO of DeepJudge
https://www.youtube.com/watch?v=x8pW19wKfXQ&ab_channel=YannicKilcher
> very interesting project and a very  interesting model architecture because it has some properties of Transformers notably it's a model architecture that's very scalable in terms of training so you can stack it really deep and you can still train it and also you can parallelize training at the same time it avoids the quadratic memory bottleneck that Transformers have by essentially being an RNN

Hugging Face
https://huggingface.co/blog/rwkv
> Due to only needing matrix-vector operations, RWKV is an ideal candidate for non-standard and experimental computing hardware, such as photonic processors/accelerators.

Top OSI licensed model in Japanese benchmarks
https://yuzuai.jp/benchmark

Most energy efficient model (Tokens per Joules)
https://ml.energy/leaderboard/?__theme=light
