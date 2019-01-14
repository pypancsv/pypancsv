# Zoom VIDEOCONFERENCE link:
# [https://bit.ly/2D0rwbw](https://bit.ly/2D0rwbw){:target="_blank"}

---

## Python for Spreadsheet Manipulation 102 - Hands-On Training for Salesforce Admins ("Salesforce Saturday")

# Saturday, January 26th
# [11:25AM-2PM CST](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20190126T1125&p1=219){:target="_blank"}

This is an online live webcast of a face-to-face training, but I will so my best to monitor the chat for Q&A from online attendees, particularly during designated Q&A times.

---

# Teaser

PART TWO: this time we'll get to VLOOKUP! Woot!

We'll do a quick recap from "101" (see https://pypancsv.github.io/pypancsv/HandsOn201810/).

We won't go back in depth over programming fundamentals like "what is a variable?" and "what're the implications of running code against a single cell vs. a column vs. a whole subsection of a table?"

But if you're adventurous and missed out last time, join us anyway! Worst you can do is get a little lost.  :-)

> Have you ever dreaded the first of the month because you know there's a CSV or XLSX spreadsheet waiting in your inbox that is going to consume half your day to clean up in Excel, just like it did last month, and the month before that, and the month before that...?
> 
> Python is a programming language that, together with its extension Pandas, has exploded in popularity among "non-programmers" with data to crunch because of its simplicity to write.
> 
> If you are a bit of an "Excel formula geek" or "Salesforce formula field go-to" or "Salesforce Process Builder whiz," YOU CAN DO THIS!
> 
> (Disclaimer: if you toss spreadsheets in terror to your "Excel power-user" coworker, you might find this Salesforce Saturday a bit of a challenge.)
> 
> With a practical focus on real-world Salesforce Admin problems, we'll cover writing and combining spreadsheet edits such as:
> 
> 1. Modifying only cells that meet certain criteria
> 
> 2. Pivoting data into a different shape
> 
> 3. Combining spreadsheets on data they share in common (think "VLOOKUP")
> 
> 4. Looping over every file in a directory, running the same program against each file

---

# Instructions & Code Snippets You Will Need

...(coming soon)...

---

## Table of Contents

* [Cheat Sheet:  Add/Delete/Reorder/Rename Columns](#colcommands)
1. [Exercise 1:  "readcsv"](#2-starter-code--readcsv)

---

<div id="colcommands"/>

## Cheat Sheet:  Add/Delete/Reorder/Rename Columns

<div id="colcommands-add-1"/>

### Adding columns, approach 1 of 2

```python
dfVarName['ColumnName'] = 'abc'
```

or

```python
dfVarName['UpperCaseFirstName'] = dfVarName['FirstName'].str.upper()
```

etc.

<div id="colcommands-add-2"/>

### Adding columns, approach 2 of 2

```python
dfVarName = dfVarName.assign(ColumnName1 = 'abc', ColumnName2 = 'def')
```

or

```python
dfVarName = dfVarName.assign(UpperCaseFirstName = dfVarName['FirstName'].str.upper(), LowerCaseFirstName = dfVarName['FirstName'].str.lower())
```

etc.

<div id="colcommands-del-1"/>

### Deleting columns, approach 1 of 2 _(keep only columns named)_

```python
dfVarName = dfVarName[['ColumnName1','ColumnName2','ColumnName3']]
```

or

```python
dfVarName = dfVarName[varNameHoldingAListOfColumnNames]
```

etc.

<div id="colcommands-del-2"/>

### Deleting columns, approach 2 of 2 _(discard columns named)_

```python
dfVarName = dfVarName.drop(columns=['ColumnName1','ColumnName2','ColumnName3'])
```

or

```python
dfVarName = dfVarName.drop(columns=varNameHoldingAListOfColumnNames)
```

etc.

<div id="colcommands-reo-1"/>

### Reordering columns

```python
dfVarName = dfVarName[['ColumnName1','ColumnName2','ColumnName3']]
```

or

```python
dfVarName = dfVarName[varNameHoldingAListOfColumnNames]
```

etc.

_(They'll come out in the order you specified.)_


<div id="colcommands-ren-2"/>

### Renaming columns

```python
dfVarName = dfVarName.rename(columns={'ColumnName1':'NewColumnName1','ColumnName2':'NewColumnName2'})
```

or

```python
dfVarName = dfVarName.rename(columns=varNameHoldingAMapOfColumnRenameLogic)
```

etc.
