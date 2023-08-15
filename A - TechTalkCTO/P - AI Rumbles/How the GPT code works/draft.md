((Some intro, why I wrote this, because existing step by step, was very math focused, with the assumption you have some background in machine learning))

We would be using GPT2, in 140 lines, to explain how everything works.

While GPT3, GPTJ, and other major opensource LLM models work in nearly identical ways, they would also be
- scaled up with many more layers
- may have different ordering and sizes for the various linear encoding
- has many order of magnitude more code for optimization in every part of the process

((In this process, you will also gain a better understanding, on the various "tuning" parameters you find on openAI (or other cloud provider) hosted API))

With that said, the core architecture stayed the same. So lets get started

> Throughout the entire process, the various example used to illustrate how the inner working function, are purely examples
> and are purely used as a means of illustration.

## Running the code step by step

**Opening the main function**

```python
import numpy as np
...
def main(prompt: str, n_tokens_to_generate: int = 40, model_size: str = "124M", models_dir: str = "models"):
	from utils import load_encoder_hparams_and_params
	encoder, hparams, params = load_encoder_hparams_and_params(model_size, models_dir)
```

After importing the dependecies. The main function is given the input "prompt" string, and the number of tokens to "generate next for completion".

The first thing it does, is given the model "name" / "path", it loads the following

- the encoder
- the model parameters (aka the weights)
- the hyper parameters (aka the model metadata)

> We would cover more on the various parameters, as it gets used in the code later

**The basics of token encoding**

```python
	input_ids = encoder.encode(prompt)
```

The first thing we do, is given the encoder model, we convert the prompt string into an array of tokens IDs, which are integers. 

So for example the following input string, 

```
hello world, welcome to our following
```

Will get mapped to the following string tokens

```
[
	"hello",
	" world",
	",",
	" wel",
	"come"
	" to"
	" our"
]
```

Which will transalte to the following _example_ int values

```
[
	123,
	456,
	7,
	890,
	101,
	121,
	231
]
```

We do this mainly for the following reason
- our LLM models function purely on an abstract "math" level. As you will see by the end of the guide
- most languages words, are made of common phrases (eg: "ing" is reused across multiple words), this allow the AI to better understand the relationship of words with unique phrases
- "As of Q1 2023", the AI transformer architecture 
	- has N^2 computing complexity based on the number of input tokens
	- as such, it requres less parameters (and ram, and compute), for the AI model to process larger context size. For example, a 500 words can typically be represented by a ~750 token array. Instead of a ~2,500+ character array.

> You will see statements with (AFAIK), or (As of Q1 2023) which is used to either represent knowledge I have limited understand of, or statements which may change in the future, with future transformer architecture, of which there are already several in propsal (and experimentation)

