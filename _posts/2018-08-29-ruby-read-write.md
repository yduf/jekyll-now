---
published: true
title: Read/Write File in Ruby
tags: file ruby
---
Simplest form of [Read](https://stackoverflow.com/a/5545293/51386) / [Write](https://stackoverflow.com/a/19337403/51386) for a file in Ruby:

{% highlight ruby %}
puts File.read(file_name)
{% endhighlight %}

{% highlight ruby %}
File.write('/path/to/file', 'Some glorious content')
{% endhighlight %}

## [Why is “slurping” a file not a good practice?](https://stackoverflow.com/questions/25189262/why-is-slurping-a-file-not-a-good-practice)

{% highlight ruby %}
IO.foreach("testfile") {|x| print "GOT ", x }
{% endhighlight %}

{% highlight ruby %}
File.foreach('testfile') {|x| print "GOT", x }
{% endhighlight %}

## Block API

{% highlight ruby %}
File::open('yozloy.txt','w') do |f|
  f << 'Some contains'
end
{% endhighlight %}