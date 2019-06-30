---
published: true
title: Memoization
tags: ruby recursive optimize Fibonacci
---
> an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again. - [wikipedia](https://fr.wikipedia.org/wiki/M%C3%A9mo%C3%AFsation)

## [Fibonacci](https://fr.wikipedia.org/wiki/Suite_de_Fibonacci#Algorithme_r%C3%A9cursif_na%C3%AFf)

{% highlight ruby %}
def fibo( n)
   if (@f ||= []) && @f[n]      # memoize value on the fly
   elsif( n <= 1)
        @f[n] = n
   else 
        @f[n] = fibo( n-2) + fibo( n -1)
   end

   @f[n]
end

n = 1000 # gets.to_i
puts [*0..n].map {|n| fibo(n)}.join(" ")
{% endhighlight %}
