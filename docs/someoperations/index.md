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

{% unless row.URL == '' or row.URL == blank or row.URL == nil or row.URL == undefined or row.URL == empty %}<a href="{{ row.URL }}" target="_blank"><i>(official documentation link)</i></a>{% endunless %}

{% unless row.InNum == '' or row.InNum == blank or row.InNum == nil or row.InNum == undefined or row.InNum == empty %}**Number of input values:**
{{ row.InNum }}{% endunless %}

{% unless row.DataTypes == '' or row.DataTypes == blank or row.DataTypes == nil or row.DataTypes == undefined or row.DataTypes == empty %}**Allowable input value "data types:"**
{{ row.DataTypes }}{% endunless %}

{% unless row.OutType == '' or row.OutType == blank or row.OutType == nil or row.OutType == undefined or row.OutType == empty %}**Data type of output value**
{{ row.OutType }}{% endunless %}

{% unless row.OutputNote == '' or row.OutputNote == blank or row.OutputNote == nil or row.OutputNote == undefined or row.OutputNote == empty %}**Note about the output value**
{{ row.OutputNote }}{% endunless %}

---

{% endfor %}

---

## Footer example
