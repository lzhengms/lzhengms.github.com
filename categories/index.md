---
layout: post
title: categories
---
{% include JB/setup %}

<div id="tag_cloud">
     {% for cat in site.categories %}
     <a rel="3" title="essay" href="#essay" style="font-size: 1em; color: rgb(249, 201, 206);">{{ cat[0] }} ({{ cat[1].size }}) </a>
     {% endfor %}
     </div>
<ul class="listing">
     {% for cat in site.categories %}
       <li id="{{ cat[0] }}" class="listing-seperator">{{ cat[0] }}</li>
       {% for post in cat[1] %}
       <li class="listing-item">
         <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
         <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
       </li>
     {% endfor %}
        {% endfor %}
     </ul>
<script charset="utf-8" type="text/javascript" src="/js/jquery.tagcloud.js"></script>
<script language="javascript">
$.fn.tagcloud.defaults = {
    size: {start: 1, end: 1, unit: 'em'},
      color: {start: '#f8e0e6', end: '#ff3333'}
};
$(function () {
    $('#tag_cloud a').tagcloud();
});
</script>