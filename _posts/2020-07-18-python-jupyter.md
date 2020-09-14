---
published: true
title: Jupyter
tags: repl python notebook jupyter
---
> open-source web application that allows you to create and share documents that contain live code, equations, visualizations and narrative text - [Jupyter](https://jupyter.org/index.html)

## [Install][https://jupyter.org/install.html)

- Jupyter Notebook
{% highlight bash %}
sudo pip3 install notebook
jupyter notebook
{% endhighlight %}

### Using Matplot

{% highlight python %}
import matplotlib
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

x = np.linspace(0, 3*np.pi, 500)
plt.plot(x, np.sin(x**2))
plt.title('A simple chirp')
plt.show()
{% endhighlight %}

### Using Graphviz

{% highlight python %}
sudo pip3 install notebook
jupyter notebook
{% endhighlight %}
