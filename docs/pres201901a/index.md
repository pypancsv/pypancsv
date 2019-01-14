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

<div id="colcommands"/>

## Columns:  Adding, Deleting, Reordering, & Renaming

<div id="colcommands-add-1"/>

### Adding columns, approach 1 of 2

`dfVarName['ColumnName'] = 'abc'` overwrites every cell in the column called `ColumnName`, within the table (a.k.a. a "[Pandas DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html){:target="_blank"}") that you've stored in the variable `dfVarName`, with the value `abc` if such a column already existed.

* If it didn't already exist, the command adds a new column by that name and fills it down with the value `abc`.

Of course, you could also put `None` on the right-hand side of the `=` to create a new blank column.

Or you could put some sort of "[Pandas Series](https://pandas.pydata.org/pandas-docs/stable/dsintro.html){:target="_blank"}" with the same set of "item IDs" that `dfVarName` has as "row IDs" to on the right-hand side of the `=`.

* So, for example, if you had a column in `dfVarName` called `FirstName`, you could create a new `UpperCaseFirstName` column with upper-cased copies of that data by saying:

```python
dfVarName['UpperCaseFirstName'] = dfVarName['FirstName'].str.upper()
```

<div id="colcommands-add-2"/>

### Adding columns, approach 2 of 2

`dfVarName = dfVarName.assign(ColumnName1 = 'abc', ColumnName2 = 'def')` overwrites every cell in the columns called `ColumnName1` and `ColumnName2`, within the table (a.k.a. a "[Pandas DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html){:target="_blank"}") that you've stored in the variable `dfVarName`, with the value `abc` if such a column already existed.

* If either or both of those columns didn't already exist, the command would add the appropriate columns and fill them down as specified.

Of course, you could also put `None` where I've put `'abc'` or `'def'` to create new blank columns.

Or you could put some sort of "[Pandas Series](https://pandas.pydata.org/pandas-docs/stable/dsintro.html){:target="_blank"}" with the same set of "item IDs" that `dfVarName` has as "row IDs" on the right-hand side of either (or both) `=` symbols within the `assign()` parentheses.

* For example:
```python
dfVarName = dfVarName.assign(UpperCaseFirstName = dfVarName['FirstName'].str.upper(), LowerCaseFirstNamedfVarName['FirstName'].str.lower())
```

Although the `.assign()` approach involves more typing and doesn't offer an obvious way to include spaces in your column names, a nifty thing about it is that the `dfVarName.assign(...)` produces a full-fledged "enhanced" copy of `dfVarName` without, in and of itself, overwriting the original contents of `dfVarName` _(that's why we have it to the right of a `dfVarName = ...` -- we're overwriting the contents of `dfVarName`)_.

* That can be handy when, for example, you want to temporarily append a "throwaway" additional column to a table just before passing it to "spreadsheet concatenation" code as input, so that you'll be able to tell which rows of your "concatenation" output came from which input spreadsheet.
