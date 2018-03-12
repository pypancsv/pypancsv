---
layout: default
title: CSV Processing with Python and Pandas - Some "Operations"
---

# CSV Processing with Python and Pandas - Some "Operations"

A quick dump of Python & Pandas "operations" that come in handy for CSV processing

---

* **Q:**  What are "operations," for the purposes of this documentation?<br/>
* **A:**  They're the other part of code, besides "expressions," that goes into writing "expressions" and "statements."

* **Q:**  Okay, great, so what are those?<br/>
* **A:**  Well, for our purposes here...
  1. An "<b><u>expression</u></b>" is any code you type that produces <b>1 output value</b>.<br/>
     It <i>is</i> some value, if you will.<br/>
     An "expression" is made up of expressions/values & "operations" (expressions can be inside of other expressions.  A single value is just a really simple expression).<br/>
     Examples are:  <b>"1"</b> or <b>"1 + 1"</b> or <b>concatenate("h","e","l","l","o")</b>.<br/>
     If you're reading this, you're probably an Excel whiz -- basically, expressions are the kinds of things that can go inside of cells in Excel.<br/>
     Note, though, that expressions don't "<i>do</i> things."  They "<i>are</i> things."<br/>
     Therefore, they <i>aren't programs</i>, any more than a cell in Excel would be a "program."<br/>
     When coding Python, it doesn't really make sense to put an "expression" by itself  in its own line of code, because that's like shouting at somebody, "Do <b>3</b>!"
  2. A "<b><u>statement</u></b>" is any code you type that <b>actually does something.</b><br/>
     They don't have values.  They <i>aren't</i> something -- they <i>do</i> something.<br/>
     A "statement" is <b>the smallest runnable chunk of code possible in a program</b>.<br/>
     It's the equivalent of a "sentence" in human languages.<br/>
     <i>(And just as a 1-sentence "essay" is still, technically, an "essay," a 1-statement "program" is still, technically, a "program."  Statements are generally separated from each other by putting them on new lines of your code.)</i><br/>
     Examples are:  <b>"Show me the value of '1+1' on my screen"</b> or <b>"store the value of '1+1' under the nickname 'myMath'"</b> or <b>"Make the 'Pandas' package of operations available for me to write code with."</b>

---

---

# "Statement" Operations

These are used in stringing 0 or more "expressions" together a "statement" (code that _does_ something).

Key:
* "°°°" means, "put something here"
* "°°°1°°°" means, "put thing #1 here" _(if the operation needs >1)_
* "°°°2°°°" means, "put thing #2 here" _(if the operation needs >1)_
* and so on

---

### print(°°°)

<a href="https://docs.python.org/3/library/functions.html#print" target="_blank"><i>(official documentation link)</i></a>

This shows the value of the input you typed on your screen, presuming you have your Python program running in a context that gives you a text-based "output console."

**Data type of input "thing:"**<br/>
Some sort of **expression** whose output value it is meaningful to "print to screen"<br/>
_(Don't be afraid to try with all kinds of expressions, even if they don't seem inherently "displayable" -- some "data types" get pretty creative figuring out how to render themselves from inside a "print()" statement!)_

---

### °°°1°°° = °°°2°°°

This stores the value of the "expression" you typed as "input thing #2" as a "variable" going by the nickname you typed as "input thing #1."<br/>
From then on in your code, instead of re-typing all the code that computed the value of °°°2°°°, you can just type the text you put as °°°1°°°.<br/>
This "nickname" becomes an expression in and of itself, a more concise way of re-typing °°°2°°°.<br/>
_(That is, unless you do this again into the same nickname with a different expression.  Then, of course, after that second use of "=" to the same nickname in your code, the other expression's value will be used when you refer to the nickname!)_<br/>

This "=" is known as an "assignment operator" in programming jargon and is really special.  Because we already used "=" here, note that when we want to check whether it's true or false that two values "equal" each other, we'll have to use other snippets of code, because "=" has already been claimed by the grammar of writing Python code for this special use!

**Data type of "input thing #1":"**<br/>
A word you want to reuse, later in your code, to reference the output value of the expression to the right of the "="

**Data type of input "thing #2:"**<br/>
Some sort of **expression**

---

### import(°°°)

<a href="https://docs.python.org/3/reference/simple_stmts.html#import" target="_blank"><i>(official documentation link)</i></a>

This says that you want to use a Python "package," like Pandas, when writing your code, and that you want to have access to "data types" and "operations" that normal-Python doesn't know about.

**Data type of input "thing:"**<br/>
The name of a Python "package"

---

---

# "Expression" Operations

These are used in stringing 0 or more "expressions" together into a new expression with a single output value.

Just as most of the richness of Excel is in its Formula Editor, most of the "operations" you'll use to process CSV files by writing Python & Pandas code are operations used to form "expressions."

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

{% unless row.InNum == '' or row.InNum == blank or row.InNum == nil or row.InNum == undefined or row.InNum == empty %}**Number of input values:**<br/>
{{ row.InNum }}{% endunless %}

{% unless row.DataTypes == '' or row.DataTypes == blank or row.DataTypes == nil or row.DataTypes == undefined or row.DataTypes == empty %}**Allowable input value "data types:"**<br/>
{{ row.DataTypes }}{% endunless %}

{% unless row.OutType == '' or row.OutType == blank or row.OutType == nil or row.OutType == undefined or row.OutType == empty %}**Data type of output value:**<br/>
{{ row.OutType }}{% endunless %}

{% unless row.OutputNote == '' or row.OutputNote == blank or row.OutputNote == nil or row.OutputNote == undefined or row.OutputNote == empty %}**Note about the output value:**<br/>
{{ row.OutputNote }}{% endunless %}

---

{% endfor %}

---

## Footer example
