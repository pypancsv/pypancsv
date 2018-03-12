---
layout: default
title: CSV Processing with Python and Pandas - Some "Operations"
---

# CSV Processing with Python and Pandas - Some "Operations"

A quick-reference of Python & Pandas "operations" that come in handy for CSV processing

Key:
* "°°°" means, "put an input expression here"
* "°°°1°°°" means, "put input expression #1 here" _(if the operation needs >1)_
* "°°°2°°°" means, "put input expression #2 here" _(if the operation needs >1)_
* and so on


---

{% assign expops=site.data.expressionoperations %}

{% for row in expops %}

### {{ row.Expression }}

{% unless {{row.URL}} == '' or not set or blank or nil %}<a href="{{ row.URL }}" target="_blank"><i>(official documentation link)</i></a>{% endunless %}

---

{% endfor %}

---

## Footer example
