---
layout: page
title: Andrew Ng's Machine Learning
---

[Brilliant course](https://www.youtube.com/watch?v=UzxYlbK2c7E&list=PLA89DCFA6ADACE599). Here you can find a quick recap of the lectures in the form of notes, questions that got me good sometimes and the problem set solutions :) 

<div>
{% for item in site.data.ml_list.toc %}
    <h3> {{ item.title}} </h3>
    <ul>
        {% for entry in item.subfolderitems %}
            <li><a href="{{ entry.url}}">{{entry.page}}</a></li>
            
        {% endfor %}
    </ul>
{% endfor %}
</div>
