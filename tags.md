---
layout:   default
title:    Tags
---
{% comment%}
Here we generate all the tags.
{% endcomment%}

{% assign rawtags = "" %}
{% for post in site.posts %}
{% assign ttags = post.tags | join:'|' | append:'|' %}
{% assign rawtags = rawtags | append:ttags %}
{% endfor %}

{% assign rawtags = rawtags | split:'|' | sort %}

{% assign tags = "" %}

{% for tag in rawtags %}
{% if tag != "" %}

{% if tags == "" %}
{% assign tags = tag | split:'|' %}
{% endif %}

{% unless tags contains tag %}
{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
{% endunless %}
{% endif %}
{% endfor %}

# Tags

<p></p> 

<div class="tags-expo">
<!-- List all tags -->
<div class="tags-expo-list">
  {% for tag in tags %}
  <a href="#{{ tag | slugify }}" class="post__tag"> {{ tag }} </a>
  {% endfor %}
</div>


<!-- List posts under each tag-->
{% for tag in tags %}
<h2 id="{{ tag | slugify }}">{{ tag }}</h2>
<ul>
  {% for post in site.posts %}
  {% if post.tags contains tag %}
  <li>
    <h3>
      <a href="{% if post.href %}{{ post.href }}
               {% elsif post.url %}{{ site.baseurl}}{{post.url}}{% endif %}">
            {{ post.title }}:
            <small class="postdate">
              {{ post.authors }} | {{ post.date | date_to_long_string }}
            </small>
      </a>
    </h3>
  </li>
  {% endif %}
  {% endfor %}
</ul>
{% endfor %}
</div>