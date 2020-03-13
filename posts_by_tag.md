---
layout: default
title: Posts by Tags
permalink: /tags/
---
<style>
	ul.tag-box li {
  display: inline-block;
  list-style: none;
  list-style-image: none;
  margin-bottom: 7px;
}
ul.tag-box li a {
  background: #e6e6e6;
  padding: 4px 8px;
  border-radius: 3px;
  color: #f76b48;
}
ul.tag-box li span.size {
  font-weight: 300;
}
</style>

<h3>All tags with counts</h3>
{% assign sorted_tags = (site.tags | sort:0) %}
<ul class="tag-box">
	{% for tag in sorted_tags %}
		{% assign t = tag | first %}
		{% assign posts = tag | last %}
		<li><a href="#{{ t | downcase }}">{{ t }} <span class="size">({{ posts.size }})</span></a></li>
	{% endfor %}
</ul>

{% for tag in sorted_tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<h4 id="{{ t | downcase }}">{{ t }}</h4>
<ul>
{% for post in posts %}
  {% if post.tags contains t %}
    <li>
       <span class="date">{{ post.date | date: '%d %b %y' }}</span>:  <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endif %}
{% endfor %}
</ul>
{% endfor %}

<!-- Listing posts by tag template from http://github.com/cagrimmett/jekyll-tools -->
