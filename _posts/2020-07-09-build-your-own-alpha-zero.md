---
published: true
title: How to build your own AlphaZero
tags: AI jupyter tensorflow
---
> With this, AlphaZero was born — the general algorithm for getting good at something, quickly, without any prior knowledge of human expert strategy. - [Applied Data Science](https://medium.com/applied-data-science/how-to-build-your-own-alphazero-ai-using-python-and-keras-7f664945c188)

![caption](https://miro.medium.com/max/902/1*ROq9V2D5eR_dDFFFfjA5zw.png)

see also
- [From-scratch implementation of AlphaZero for Connect4](https://towardsdatascience.com/from-scratch-implementation-of-alphazero-for-connect4-f73d4554002a)

## Ref
- [AlphaGo Zero - How and Why it Works](http://tim.hibal.org/blog/alpha-zero-how-and-why-it-works/)
- [Mastering the game of Go without human knowledge](https://www.gwern.net/docs/rl/2017-silver.pdf)
- [AlphaGO zero cheat sheet](https://adspassets.blob.core.windows.net/website/content/alpha_go_zero_cheat_sheet.png)

## Learning Algorithm summary

- Mentally play through possible future scenarios, giving priority to promising paths, whilst also considering how others are most likely to react to your actions and continuing to explore the unknown.

- After reaching a state that is unfamiliar, evaluate how favourable you believe the position to be and cascade the score back through previous positions in the mental pathway that led to this point.

- After you’ve finished thinking about future possibilities, take the action that you’ve explored the most.

- At the end of the game, go back and evaluate where you misjudged the value of the future positions and update your understanding accordingly.

## Code
see also [AlphaGo Zero cheat sheet](https://medium.com/applied-data-science/how-to-build-your-own-alphazero-ai-using-python-and-keras-7f664945c188)

- [Jupyter]({% post_url 2020-07-18-python-jupyter %}) notebook for [DeepReinforcementLearning (github)](https://github.com/yduf/DeepReinforcementLearning)


## Dependencies to add to docker images

{% highlight bash %}
pip3 install matplotlib
pip3 install pydot pydot-ng
pip3 install graphviz

apt-get update && apt-get install graphviz
{% endhighlight %}
