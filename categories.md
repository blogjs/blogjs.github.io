---
layout: page
title: Categories
permalink: /categories/
published: true
order: 2
keywords: "categories, javascript, blog, articles, tags"
description: "All posts of 'blogJS - Javascript blog', sorted by categories"
---

{% assign rawcats = "" %}
{% for post in site.posts %}
    {% assign cats = post.categories | join:'|' | append:'|' %}
    {% assign rawcats = rawcats | append:cats %}
{% endfor %}
{% assign rawcats = rawcats | split:'|' | sort %}
{% assign cats = "" %}
{% for cat in rawcats %}
    {% if cat != "" %}
        {% if cats == "" %}
            {% assign cats = cat | split:'|' %}
        {% endif %}
        {% unless cats contains cat %}
            {% assign cats = cats | join:'|' | append:'|' | append:cat | split:'|' %}
        {% endunless %}
    {% endif %}
{% endfor %}

{% for cat in cats %}<a href="#{{ cat | slugify }}"> {{ cat }}</a>, {% endfor %}


{% for cat in cats %}
<h3 id="{{ cat | slugify }}">{{ cat }}</h3>
<ul>
{% for post in site.posts %}
{% if post.categories contains cat %}
<li>

<a href="{{ post.url }}">
{{ post.title }}
</a>
<small>{{ post.date | date_to_string }}</small>

</li>
{% endif %}
{% endfor %}
</ul>
{% endfor %}