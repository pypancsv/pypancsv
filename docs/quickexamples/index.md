---
layout: default
title: CSV Processing with Python and Pandas - Quick Examples
---

# CSV Processing with Python and Pandas - Quick Examples

Below are examples you may have seen in a presentation and want to review at your own leisure.

---

## First, the CSV files within the examples:

### Sample CSV #1

* Has 7 rows, 5 columns
* Meant to represent records from a "people"-typed table in "Data Source #1"

{% assign sampleone=site.data.sample1 %}

<table>
    <thead>
    {% for column in sampleone[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in sampleone %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

---

## Example Code:  Import CSV -> Pandas.  Print.  Export to new CSV.

[Click here](https://repl.it/@rplrpl/Import-a-CSV-into-Pandas-Print-the-resulting-DataFrame){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('c:\\yay\\sample1.csv')
print('---Here are all 7 lines---')
print(df)
print('---Here are the first 5 lines---')
print(df.head())
fivelinedf = df.head()
fivelinedf.to_csv('C:\\yay\\out_fiveline.csv', index=False, quoting=1)
```

### Test yourself!


[Click here](https://repl.it/@rplrpl/Import-a-CSV-into-Pandas-Print-the-resulting-DataFrame){:target="_blank"} and edit the code so that instead of saying "Here are the first 5 lines", it says, "Here are the last 2 lines", and edit the next line of code to do just that _(display the last 2 lines)_.

_(Note:  first run takes a minute or so.)_

* Hint:  it's the "[°°°1°°°.tail(°°°2°°°)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.tail.html){:target="_blank"}" operation.<br/>

Keep trying until your output looks like this:

    ---Here are all 7 lines---
          Id    First      Last           Email                      Company
    0   5829    Jimmy    Buffet  jb@example.com                          RCA
    1   2894  Shirley  Chisholm  sc@example.com       United States Congress
    2    294  Marilyn    Monroe  mm@example.com                          Fox
    3  30829    Cesar    Chavez  cc@example.com          United Farm Workers
    4    827  Vandana     Shiva  vs@example.com                     Navdanya
    5   9284   Andrea     Smith  as@example.com     University of California
    6    724   Albert    Howard  ah@example.com  Imperial College of Science
    ---Here are the last 2 lines---
         Id   First    Last           Email                      Company
    5  9284  Andrea   Smith  as@example.com     University of California
    6   724  Albert  Howard  ah@example.com  Imperial College of Science

---

## Example Code:  Filter out rows whose last names don't start with a capital C or capital S

This example actually shows off 3 different Pandas operations:

1. Displaying the contents of the CSV file's column "Last"
2. Displaying a single column indicating "True or False:  Do the contents of 'Last' in this row start with a capital C or capital S?"
3. Displaying a new table that only includes rows where the contents of "Last" actually started with a capital C or capital S.

[Click here](https://repl.it/@rplrpl/Filter-out-rows-last-name-not-C-or-S){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('c:\\yay\\sample1.csv')
print('---What is in "Last" for each row?---')
print(df['Last'])
print('---For each row, does "Last" start with capital "C" or "S"?---')
print(df['Last'].str.startswith('C') | df['Last'].str.startswith('S'))
print('---Show all columns, but only rows where "Last" starts with capital "C" or "S"---')
lastCSdf = df[df['Last'].str.startswith('C') | df['Last'].str.startswith('S')]
print(lastCSdf)
lastCSdf.to_csv('C:\\yay\\out_lastcs.csv', index=False, quoting=1)
```

### Test yourself!

[Click here](https://repl.it/@rplrpl/Filter-out-rows-last-name-not-C-or-S){:target="_blank"} and edit the code so that instead of saying 'Show all columns, but only rows where "Last" starts with capital "C" or "S"', it says, 'Show all columns, but only rows where "Company" case-insensitively ends with "a" or "Id" is less than 800', and edit the next line of code to do just that _(display only rows where "Company" ends with "A" or "a" or the "Id" is a number less than 800)_.

_(Note:  first run takes a minute or so.)_

* Hint #1:  For the case-insensitive comparison, try experimenting with the "[°°°.str.lower()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.lower.html){:target="_blank"}" or "[°°°.str.upper()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.upper.html){:target="_blank"}" operations.  You can slip it in right before the "[°°°.str.endswith()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.endswith.html){:target="_blank"}"  operation to force "[°°°.str.endswith()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.endswith.html){:target="_blank"}" to operate against the all-uppercased/lowercased text instead of the original text.

* Hint #2:  You can compare a "Pandas Series" (e.g. "`df[Last]`") directly with a single value.  For example, "`df[Last] < 'Ferret'`" outputs a single column indicating "True or False:  Do the contents of 'Last' in this row come earlier in the alphabet than the word 'Ferret'?"

* Hint #3:  If, for some reason, your code is displaying _every_ row, try surrounding the code on either side of the "or" ("`|`") with parentheses.<br/>In other words, if "`df[°°°1°°° | °°°2°°°]`" doesn't work for filtering the rows, try "`df[(°°°1°°°) | (°°°2°°°)]`".<br/>Sometimes the code gets finicky and extra parentheses help un-confuse it.

Keep trying until your output looks like this:

    ---What is in "Last" for each row?---
    0      Buffet
    1    Chisholm
    2      Monroe
    3      Chavez
    4       Shiva
    5       Smith
    6      Howard
    Name: Last, dtype: object
    ---For each row, does "Last" start with capital "C" or "S"?---
    0     True
    1    False
    2     True
    3    False
    4     True
    5     True
    6     True
    dtype: bool
    ---Show all columns, but only rows where "Company" case-insensitively ends with "a" or "Id" is less than 800---
    	 Id    First    Last           Email                      Company
    0  5829    Jimmy  Buffet  jb@example.com                          RCA
    2   294  Marilyn  Monroe  mm@example.com                          Fox
    4   827  Vandana   Shiva  vs@example.com                     Navdanya
    5  9284   Andrea   Smith  as@example.com     University of California
    6   724   Albert  Howard  ah@example.com  Imperial College of Science

---

## Example Code:  Complex Cell Updates and Adding, Removing, and Renaming Columns

[Click here](https://repl.it/@rplrpl/Complex-Cell-Updates-and-Adding-Removing-and-Renaming-Colu){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('c:\\yay\\sample1.csv')
theseRowsLastNamesStartWithCapitalS = df['Last'].str.startswith('S')
theseRowsHaveA4InTheirId = df['Id'].astype(str).str.contains('4')
df.loc[theseRowsLastNamesStartWithCapitalS,'Last'] = 'aaa'
df.loc[theseRowsHaveA4InTheirId,'Email'] = 'bbb'
df.loc[theseRowsLastNamesStartWithCapitalS,'New1'] = 'ccc'
df.loc[theseRowsHaveA4InTheirId,'New2'] = 'ddd'
df['New3'] = 'eee'
df = df.drop(['Id','Company'], axis=1)
df = df.rename(columns = {'First':'First Name', 'Last':'Last Name', 'Email':'Email Address'})
print('---We have modified the Python variable "df" to have 3 new rows, plus changes in the "Last" and "Email" columns on specific rows only, and we dropped the "Id" and "Company" rows, and finally, we renamed the "First," "Last," and "Email" columns.---')
print(df)
df.to_csv('C:\\yay\\out_complexupdates.csv', index=False, quoting=1)
```

The output looks like this:

    ---We have modified the Python variable "df" to have 3 new rows, plus changes in the "Last" and "Email" columns on specific rows only, and we dropped the "Id" and "Company" rows, and finally, we renamed the "First," "Last," and "Email" columns.---
    First Name Last Name   Email Address New1 New2 New3
    0      Jimmy    Buffet  jb@example.com  NaN  NaN  eee
    1    Shirley  Chisholm             bbb  NaN  ddd  eee
    2    Marilyn    Monroe             bbb  NaN  ddd  eee
    3      Cesar    Chavez  cc@example.com  NaN  NaN  eee
    4    Vandana       aaa  vs@example.com  ccc  NaN  eee
    5     Andrea       aaa             bbb  ccc  ddd  eee
    6     Albert    Howard             bbb  NaN  ddd  eee

### Test yourself!

[Click here](https://repl.it/@rplrpl/Filter-out-rows-last-name-not-C-or-S){:target="_blank"} and make something cool.

There's a lot of code in this example that you didn't see in the other examples.  Poke around and guess what might be going on and see if it runs.  Have fun and get creative.

Hint:  Remember that you can "checkpoint" your work by storing the output of "expressions" into "variables" _(nicknames you can use later in your code)_.  4 examples from the code above are:

* `theseRowsLastNamesStartWithCapitalS = df['Last'].str.startswith('S')`, which saves a Pandas "Series" into a "variable" called "theseRowsLastNamesStartWithCapitalS"
* `df = df.drop(['Id','Company'], axis=1)`:  what's going on here is that the right side of the "`=`" outputs a new "Pandas DataFrame" _(table)_ that is just like the one currently stored in the variable called "df" _(at the time that this line of code begins)_ ... and then it completely wipes out everything that was stored in "df" and overwrites its contents so that instead, the **new** output from the right side of the "`=`" becomes the value of the variable called "df" for all lines of code afterwards.
* `df['New3'] = 'eee'`, which modifies the contents of the "Pandas DataFrame" _(table)_ saved in the variable called "df" so that every row of its column labeled "New3" will now contain the text "eee".
* `df.loc[theseRowsHaveA4InTheirId,'Email'] = 'bbb'`, which modifies the contents of the "Pandas DataFrame" _(table)_ saved in the variable called "df" so that any rows of its column labeled "Email" that have the same row-number as the rows of the "Pandas Series" called "theseRowsHaveA4InTheirId" will now contain the text "bbb".
