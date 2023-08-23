---
layout: categories
title: Student Blog
---

## James's Page

Go to my [Github account](https://github.com/Jw95z) !!

## Overview of Hacks, Study and Tangibles
Blogging in GitHub pages is a way to learn and code at the same time. 

- Plans, Lists, [Scrum Boards](https://clickup.com/blog/scrum-board/) help you to track key events, show progress and record time.  Effort is a big part of your class grade.  Show plans and time spent!
- [Hacks(Todo)](https://levelup.gitconnected.com/six-ultimate-daily-hacks-for-every-programmer-60f5f10feae) enable you to stay in focus with key requirements of the class.  Each Hack will produce Tangibles.
- Tangibles or [Tangible Artifacts](https://en.wikipedia.org/wiki/Artifact_(software_development)) are things you accumulate as a learner and coder. 


<html>
    {% if site.categories.size > 0 %}
    <h2>Contents</h2>

    {% assign categories = "" | split:"" %}
    {% for c in site.categories %}
        {% assign categories = categories | push: c[0] %}
    {% endfor %}
    {% assign categories = categories | sort_natural %}

    <ul>
    {% for category in categories %}
        <li><a href="#{{ category }}">{{ category }}</a></li>
    {% endfor %}
    </ul>

    {% for category in categories %}
        <h3 id ="{{ category }}"><i class="fas fa-tags category-tags-icon"></i> {{ category }}</h3>
        <a name="{{ category | slugize }}"></a>
        {% for post in site.categories[category] %}
            {% if post.hide != true %}
            {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
            <article class="archive-item">
            <p class="post-meta post-meta-title"><a class="page-meta" href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a>  • {{ post.date | date: date_format }}</p>
            </article>
            {% endif %}
        {% endfor %}
    {% endfor %}

    {% endif %}

</html>