---
layout: home
title: O livro de Cesário Verde
image: capa
---

{% for post in site.posts limit: 5 %}
{% assign length = site.posts.size %}
{% assign lengthID = site.posts.size | plus: 1%}
<div class="posts">
  <div id="js-{{ forloop.index }}" class="post -fixed{% if forloop.index == 1 %} -first{% endif %}{% if forloop.index == length %} -last{% endif %}">
    <span id="{{ post.url | remove: '/' }}">
    {% if forloop.index != 1 %}
      <div class="post-header ctnr-golden">
        <h1 class="post-title">
          <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
        </h1>
      </div>
    {% endif %}
    </span>
 	{% picture {{ post.image | append: ".jpg" }} --alt {{ post.image }} --img class="post-image" --img loading="lazy" style="z-index: {{ lengthID | minus: forloop.index }}" %}
	<div class="ctnr-wide">
    {{ post.content }}
    </div>
  </div>
{% endfor %}
</div>
<div class="infinite-spinner"></div>
