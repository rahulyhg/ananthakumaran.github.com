---
layout: post
title: Ruby Block
header: Ruby Block
meta_keywords: blocks in ruby, functional programming, lisp
meta_descripton: comparing ruby's block with lisp functions
tags: ruby
---

{% highlight ruby %}
def foo
  print "foo"
  yield
end

foo { print "bar" }
{% endhighlight %}

When I encountered Ruby's block for the first time, I thought it was a
new type of construct. We are calling a function foo and passing it a
block. The foo function will print `foo` and then magically transfer
the control to the block, which will then print the `bar` and then
magically return the control to the foo function. Whenever I use the
word 'magically', I mean that I am not fully aware of what is
happening. I guess this is how most imperative programmer will
think. Well I used to think this way. I guess this is the problem with
the imperative programmer. We kind of think sequentially. Oops I
forgot to mention who is an imperative programmer. If you have written
programs only in languages like c, c++, Java etc, then you are an
imperative programmer. Well I was an imperative programmer until the
beginning of the fourth year in the college.

I had a very small dosage of lisp. Suddenly my way of thinking changed
considerably. I mean suddenly I realized that we can consider a
function as a value in javascript. Well I have written code without
understanding the basic concept.

Ok, lets rewrite the above method in scheme to explain it in terms of
functional programming

{% highlight scheme %}
(define (foo block)
  (display "foo")
  (block))

(foo (lambda ()
       (display "bar")))
{% endhighlight %}


I guess the above code is very easy to explain. We are calling the foo
function and passing it a function and the foo function prints `foo`
and calling the function we passed, which in turn prints `bar`. Here
is the trick, we can pass function as a value to other function. So
what is really happening in Ruby. Well I don't know the internals of
the Ruby, I guess there is no need to know the internals in order to
it to understand the concept. There is no such thing called
`Block`. It is a simple function with no name, aka `lambda`. Then you
might ask what is `Yield`. Well yield is a kind of syntax sugar. In
Ruby you can pass a block to a function and the called function can
call it with the yield key word. In fact you can handle the block
explicitly

{% highlight ruby %}
def foo(&b)
  print "foo"
  b.call()
end

foo { print "bar" }
{% endhighlight %}


So the bottom line is, learn lisp, it will help you to think in a
different way. I should take a heavy dosage of lisp, which I guess
will make me look at the world in yet a different way.
