---
layout: post
title:  "Coding the Fibonacci Formula"
date:   2014-11-22 08:16:00
categories: writing meta programming
---

Programming the fibonnaci sequence has always been a popular coding question. Sometimes it's asked to determine if person has a modicum of programming skill other times it's used in teaching to explain the differences between recursive and iterative programming.

It's a fun question and a fun formula. I thought it was cool the first time I saw it. But of all the fibonacci programs you can write, in any language, mathematicians, I think, have come up with the ultimate 'algorithm'. But first I just want to spell out several implementations of the fibonacci algorithm.


{% highlight python %}
def fib_recursive(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)
{% endhighlight %}


{% highlight python %}
def fib_iterative(n):
    a, b = 0, 1
    for i in range(0, n):
        a, b = b, a + b
    return b
{% endhighlight %}

{% highlight python %}
KNOWN_FIBS = {}

def fib_with_memoization(n):
    if KNOWN_FIBS.get(n, None):
        return KNOWN_FIBS.get(n)

    if n < 2:
        return n
    else:
        KNOWN_FIBS[n] = fib(n-1) + fib(n-2)

    return KNOWN_FIBS.get(n)
{% endhighlight %}

<br>
<br>

But instead of any of the above functions this is the one a programmer would use in real life,

$$
fib(n) = \frac{ \varphi^n }{ \sqrt5 }
\\
\mbox{where } \varphi = \mbox{golden ratio} \approx 1.618039...
$$

Yup... that's what a programmer would do in real life if they needed the fibonacci sequence to solve an actual problem.
