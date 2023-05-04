---
language:
  - en
thumbnail: null
tags:
  - text generation
  - conversational
pipeline_tag: text-generation
inference: false
---
<h1 style="text-align: center">Pygmalion 7B</h1>
<h2 style="text-align: center">A conversational LLaMA fine-tune.</h2>

## Model Details:

Pygmalion 7B is a dialogue model based on Meta's LLaMA-7B.

This is version 1. It has been fine-tuned using a subset of the data from Pygmalion-6B-v8-pt4, for those of you familiar with the project.

## Applying the XORs

This models has the XOR files pre-applied out of the box.
Converted from the XORs weights from PygmalionAI's release https://huggingface.co/PygmalionAI/pygmalion-7b

## Prompting

The model was trained on the usual Pygmalion persona + chat format, so any of the usual UIs should already handle everything correctly. If you're using the model directly, this is the expected formatting:

```
[CHARACTER]'s Persona: [A few sentences about the character you want the model to play]
<START>
[DIALOGUE HISTORY]
You: [User's input message here]
[CHARACTER]:
```

Where `[CHARACTER]` is, as you can probably guess, the name of the character you want the model to portray, `<START>` should be used verbatim as a delimiter token to separate persona and scenario data from the dialogue, and `[DIALOGUE HISTORY]` is a sliding window of chat history so the model can have conversational context to draw from. Here's a concrete example:

```
Assistant's Persona: Assistant is a highly intelligent language model trained to comply with user requests.
<START>
Assistant: Hello! How may I help you today?
You: What is Zork?
Assistant:
```

Which will generate something like:

```
 Zork is an interactive fiction computer game created in the 1970s by Infocom, Inc., which was later acquired by Activision Blizzard. It is widely considered one of the most influential games ever made and has been credited with popularizing text-based adventure games. The original version of Zork was written in the programming language MACRO-10, but it was ported to many other platforms over the years."
```

The model will automatically emit an end-of-text token (`</s>`) when it judges that the response is complete.

## Limitations and biases

The intended use-case for this model is fictional conversation for entertainment purposes. Any other sort of usage is out of scope.

As such, it was **not** fine-tuned to be safe and harmless: the base model _and_ this fine-tune have been trained on data known to contain profanity and texts that are lewd or otherwise offensive. It may produce socially unacceptable or undesirable text, even if the prompt itself does not include anything explicitly offensive. Outputs might often be factually wrong or misleading.
