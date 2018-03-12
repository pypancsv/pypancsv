---
layout: default
title: CSV Processing with Python and Pandas - Some "Operations"
---

# CSV Processing with Python and Pandas - Some "Operations"

A quick-reference of Python & Pandas "operations" that come in handy for CSV processing

Key:
* "\~\~\~" means, "put an input expression here"
* "\~\~\~1\~\~\~" means, "put input expression #1 here" _(if the operation needs more than 1 input expression)_
* "\~\~\~2\~\~\~" means, "put input expression #1 here" _(if the operation needs more than 1 input expression)_
* "\~\~\~3\~\~\~" means, "put input expression #1 here" _(if the operation needs more than 1 input expression)_
* and so on


---

{% for row in site.data.expressionoperations %}
### {{ row.Expression }}{% unless row.URL != '' %}[(documentation link)]({{ %%row.URL%% }}){:target="_blank"}{% endif %}
{% endfor %}
