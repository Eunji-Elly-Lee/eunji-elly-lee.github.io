---
layout: default
title: About Java
---

<div class="home" id="home">
  <h1 class="pageTitle">Java Posts</h1>
  {%- for post in site.categories[java] -%}
    <div class="posts noList">
        {%- for post in paginator.posts -%}
        <article>
            <span class="date">{{ post.date | date: '%B %d, %Y' }}</span>
            <h3><a class="post-link" href="{{ post.url }}">{{ post.title }}</a></h3>
            <p>{%- if post.description -%}{{ post.description }}{%- else -%}{{ post.excerpt | strip_html }}{%- endif -%}</p>
        </article>
        {%- endfor -%}
    </div>
    <!-- Pagination links -->
    <div class="pagination">
        {%- if paginator.previous_page -%}
        <a href="{{ paginator.previous_page_path }}" class="previous button__outline">Newer Posts</a> 
        {%- endif -%}
        {%- if paginator.next_page -%}
        <a href="{{ paginator.next_page_path }}" class="next button__outline">Older Posts</a>
        {%- endif -%}
    </div>
  {%- endfor -%}
</div>