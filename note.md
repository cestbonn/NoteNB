# 1. challenge
prompt虽好，但是依然打不过finetune，GPT3 few shot<T5-XXL, 前者是后者的16倍参数。


# 2. related work
1. [AutoPrompt](https://aclanthology.org/2020.emnlp-main.346.pdf) propose a search algorithm over the discrete space of words, guided by the downstream application training data.
2. [Prefix-Tuning](https://arxiv.org/abs/2101.00190) propose “prefix tuning” and show strong results on generative tasks. This method freezes the model parameters and back-propagates the error during tuning to prefix ac-tivations prepended to each layer in the encoder stack, including the input layer. [WARP](https://aclanthology.org/2021.acl-long.381.pdf) simplify this recipe by restricting the trainable parameters to the input and output sub-networks of a masked language model, and show reasonable results on classifications tasks.

# 3. softprompt的优点
1. 可以与model tuning相媲美，尤其考虑到softprompt只需要小规模的tuning
2. 对每一个downstream task，只需要tuning一个prompt就好了。注意，是prompt per task！
3. 对同一个task，可以训练多个prompt，再ensemble，比model ensemble要好
4. Explicitly separating task-specific parameters from the “generalist” parameters needed for general language-understanding has a range of ad-ditional benefits. 证明了把task-specific knowledge和general ability 分开是有好处的
	1. domain shift

# 4. 结论
1. prompt tuning 可以完全替代 finetune
2. prompt tuning becomes more competitive with scale.
