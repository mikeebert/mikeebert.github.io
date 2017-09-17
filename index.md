---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
---

<div class="posts">
{% for post in site.posts limit:10 %}
  <article class="post">

  <h1><a href="{{ site.baseurl }}{{ post.url }}">{{post.title }}</a></h1>

  <div class="entry">
  {{ post.excerpt }}
  </div>

  <a href="{{ site.baseurl }}{{post.url }}" class="read-more">Read More</a>
  </article>
{% endfor %}
<p></p>
</div>

<div>
  <a href="/posts/" class="read-more">See all posts</a>
</div>
