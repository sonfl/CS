---
layout: page
title: Andrew Ng's Machine Learning
---

[Brilliant course](https://www.youtube.com/watch?v=UzxYlbK2c7E&list=PLA89DCFA6ADACE599). Here you can find a quick recap of the lectures in the form of notes, questions that got me good sometimes and the problem set solutions :) 

<div>
{% for item in site.data.ml_list.toc %}
    <h3>{{ item.title}} </h3>
    <ul>
            <li><a href="{{site.baseurl}}{{ site.data.ml_list.base_path}}{{site.data.ml_list.notes_path}}{{item.number}}">Notes</a></li>
            <li><a href="{{site.baseurl}}{{ site.data.ml_list.base_path}}{{site.data.ml_list.questions_path}}{{item.number}}">Questions</a></li>
            <li><a href="{{site.baseurl}}{{ site.data.ml_list.base_path}}{{site.data.ml_list.ps_path}}{{item.number}}">Problem set</a></li>
    </ul>
{% endfor %}
</div>
