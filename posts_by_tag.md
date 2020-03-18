---
layout: blogPageDefault
title: Posts sorted according to tags
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
<h1>{{ page.title }}</h1>
<!-- <h3>All tags with counts</h3> -->
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
<!-- AddToAny BEGIN -->
<h2>Share :</h2>
<div class="a2a_kit a2a_kit_size_32 a2a_default_style">
<a class="a2a_dd" href="https://www.addtoany.com/share"></a>
<a class="a2a_button_facebook"></a>
<a class="a2a_button_email"></a>
<a class="a2a_button_twitter"></a>
<a class="a2a_button_google_gmail"></a>
<a class="a2a_button_telegram"></a>
<a class="a2a_button_blogger"></a>
<a class="a2a_button_google_bookmarks"></a>
<a class="a2a_button_evernote"></a>
<a class="a2a_button_linkedin"></a>
<br><br>
</div>
<script async src="https://static.addtoany.com/menu/page.js"></script>
<!-- AddToAny END -->
