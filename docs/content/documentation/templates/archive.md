+++
title = "Archive"
weight = 90
+++

Gutenberg doesn't have a built-in way to display an archive page, a page showing
all post titles ordered by year. However, this can be accomplished directly in the templates:

```jinja2
{% for year, posts in section.pages | group_by(attribute="year") %}
    <h2>{{ year }}</h2>

    <ul>
    {% for post in posts %}
        <li><a href="{{ post.permalink }}">{{ post.title }}</a></li>
    {% endfor %}
    </ul>
{% endfor %}
```

This snippet assumes that posts are sorted by date and that you want to display the archive
in a descending order. If you want to show articles in a ascending order, simply add a `reverse` filter
after the `group_by`.
