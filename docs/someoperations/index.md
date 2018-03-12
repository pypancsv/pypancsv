---
layout: default
title: CSV Processing with Python and Pandas - Some "Operations"
---

# CSV Processing with Python and Pandas - Some "Operations"

A quick-reference of Python & Pandas "operations" that come in handy for CSV processing

---

{% for row in site.data.expressionoperations %}
### {{ row.Expression }}{% unless row.URL != '' %}[(documentation link)]({{ %%row.URL%% }}){:target="_blank"}{% endif %}
{% endfor %}
