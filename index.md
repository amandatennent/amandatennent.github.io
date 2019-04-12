---
layout: default
---

<div>

{%- if page.title -%}

  <header>
    <h1>{{ page.title }}</h1>
  </header>
  {%- endif -%}

{%- if site.posts.size > 0 -%}

  <div class="article mb-4">
    <h2>{{ page.list_title | default: "Posts" }}</h2>
  </div>
  <ul class="list-unstyled" style="padding-left: 0; list-style-type: none;">
    {%- for post in site.posts -%}
    <li class="article mb-4">
      <p class="h5 mb-2">
        <a href="{{ post.url | relative_url }}">
          <h3>{{ post.title | escape }}</h3>
        </a>
      </p>
      {% if post.image %}
      <div class="post-image mb-2 mt-3">
        <a href="{{ post.url | relative_url }}">
          <img src="{{ post.image | relative_url }}">
        </a>
      </div>
      {% endif %}
      <p class="text-muted">
        {%- assign date_format = "%b %-d, %Y" -%}
        {{ post.date | date: date_format }}
      </p>
        {{ post.content | strip_html | truncatewords: 50 }}
    </li>
    {%- endfor -%}
  </ul>

  <div class="article">
    <p>
      <a href="{{ "/feed.xml" | relative_url }}">Subscribe via RSS</a>
    </p>
  </div>
  {%- endif -%}

</div>
