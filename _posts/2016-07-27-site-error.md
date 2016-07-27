---
layout: post
title:  Learning Notes - This Site Error
---

## post.html模版中对日期进行格式化时产生的build错误
需要将`page.date | date_to_string` 改为 `page.date`，问题可能是格式化函数的支持问题导致的？去掉后编译可通过。

错误提示为
```
Invalid Date: '' is not a valid datetime.
Liquid Exception: exit in _layouts/post.html
```

```
---
layout: default
---

<div class="post">
  <h1 class="post-title">{{ page.title }}</h1>
  <span class="post-date">{{ page.date | date_to_string }}</span>
  {{ content }}
</div>

<div class="related">
  <h2>Related Posts</h2>
  <ul class="related-posts">
    {% for post in site.related_posts limit:3 %}
      <li>
        <h3>
          <a href="{{ site.baseurl }}{{ post.url }}">
            {{ post.title }}
            <small>{{ post.date | date_to_string }}</small>
          </a>
        </h3>
      </li>
    {% endfor %}
  </ul>
</div>
```



