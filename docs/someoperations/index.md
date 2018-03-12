---
layout: default
title: CSV Processing with Python and Pandas - Some "Operations"
---

# CSV Processing with Python and Pandas - Some "Operations"

A quick-reference of Python & Pandas "operations" that come in handy for CSV processing

---

{% assign expops=site.data.expressionoperations %}

<ul>
{% for x in site.data.expressionoperations %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ x.Expression }}
    </a>
  </li>
{% endfor %}
</ul>
