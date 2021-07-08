# HuggingFace / GPT2 
* originally OpenAI GPT-2 model was proposed in [anguage Models are Unsupervised Multitask Learners](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)

## GPT-2
* a causal (unidirectional) transformer pretrained using language modeling on a very large corpus of ~40 GB of text data.

## How to reuse the past in generative model? 
* [reference link](https://huggingface.co/transformers/v2.9.1/quickstart.html#using-the-past)
* GPT-2  make use of a `past` or `mems` attribute 
  * this attribute can be used to prevent re-computing the key/value pairs when using sequential decoding. 
  * It is useful when generating sequences 
  * Because a big part of the attention mechanism benefits from previous computations.
  * cf) some other models (GPT, XLNet, Transfo-XL, CTRL) also use this techqnique

* <b>A fully-working example using the `past` with `GPT2LMHeadModel` and `argmax decoding`.</b>

  * ⚠️ :warning: (`argmax decoding` should only be used as an example, as it introduces a lot of repetition)
   ```python
      from transformers import GPT2LMHeadModel, GPT2Tokenizer
      import torch

      tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
      model = GPT2LMHeadModel.from_pretrained('gpt2')

      generated = tokenizer.encode("The Manhattan bridge")
      context = torch.tensor([generated])
      past = None

      for i in range(100):
          print(i)
          output, past = model(context, past=past)
          token = torch.argmax(output[..., -1, :])

          generated += [token.tolist()]
          context = token.unsqueeze(0)

      sequence = tokenizer.decode(generated)

      print(sequence)
   ```
   * :grey_question: :grey_exclamation: code without using only `past` with `GPT2LMHeadModel'?
