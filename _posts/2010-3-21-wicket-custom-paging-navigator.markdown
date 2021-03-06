---
layout: post
title: Wicket Custom Paging Navigator
header : Wicket Custom Paging Navigator
meta_keywords: wicket , wicket custom markup , custom paging navigator
meta_description: wicket custom paging navigator
tags: wicket
---

Wicket Built-in Components
--------------------------
Wicket provides lot of useful components out of the box. Sometimes we
would like to change the appearance(aka markup) of the built-in
components. It is very easy to do.

Original Markup
---------------
Each component has a markup file associated with it. We will take the
PagingNavigator as an example. It is associated with the markup file
PagingNavigator.html. I got the markup from
[1](http://github.com/apache/wicket/blob/trunk/wicket/src/main/java/org/apache/wicket/markup/html/navigation/paging/PagingNavigator.html).

{% highlight html %}
<html xmlns:wicket>
<body>
  <wicket:panel>
	<a wicket:id="first">&lt;&lt;</a>&nbsp;<a wicket:id="prev">&lt;</a>
    <span wicket:id="navigation">
		  <a wicket:id="pageLink" href="#"><span wicket:id="pageNumber">5</span></a>
    </span>
    <a wicket:id="next">&gt;</a>&nbsp;<a wicket:id="last">&gt;&gt;</a>
  </wicket:panel>
</body>
</html>
{% endhighlight %}

Extend the Component
--------------------
First we need to extend the Component, in our case it is PagingNavigator.

{% highlight java %}
public class CustomPagingNavigator extends PagingNavigator
{
   public CustomPagingNavigator(final String id, final IPageable pageable)
	{
		this(id, pageable, null);
	}

	public CustomPagingNavigator(final String id, final IPageable pageable,
		final IPagingLabelProvider labelProvider)
	{
		super(id,pageable,labelProvider);
	}

}
{% endhighlight %}

Customize the Markup
--------------------
Create a markup file for the component(CustomPagingNavigator.html) and
copy the original markup. The only restriction is, we should not
change the `wicket:id` and the hierarchy of the `wicket:id`.  I don't
like the &lt; and &gt; symbols. So i am going to change it and i like
to add `|` between the links.
{% highlight html %}
<html xmlns:wicket>
<body>
  <wicket:panel>
	<a wicket:id="first">first |</a>&nbsp;<a wicket:id="prev">previous |</a>
    <span wicket:id="navigation">
		  <a wicket:id="pageLink" href="#"><span wicket:id="pageNumber">5</span> |</a>
    </span>
    <a wicket:id="next">next |</a>&nbsp;<a wicket:id="last">last</a>
  </wicket:panel>
</body>
</html>
{% endhighlight %}


I have made small changes only. But you can go on and make further
changes like showing images instead of first, last etc.
