---
layout: default
title: CSV Processing with Python and Pandas - Quick Examples
---

# CSV Processing with Python and Pandas - Quick Examples

Below are examples you may have seen in a presentation and want to review at your own leisure.

---

## Contents

1. [CSV files used](#first-the-csv-files-within-the-examples)
2. [Example: Import CSV -> Pandas. Print. Export to new CSV.](#example-code--import-csv---pandas--print--export-to-new-csv)
3. [Example: Filter out rows by last name](#example-code--filter-out-rows-whose-last-names-dont-start-with-a-capital-c-or-capital-s)
4. [Example: Fancy cell edits.  Add, remove, & rename columns.](#example-code--complex-cell-updates-and-adding-removing-and-renaming-columns)
5. [Example: Merge 2 CSV files on a multi-column match](#example-code--merging-2-csv-files-w-a-multi-column-match)
6. [Example: Filter rows based on aggregations ("keep oldest person per address")](#example-code--filter-rows-based-on-aggregations)
7. [Example: Add data based on aggregation ("flag oldest person per address")](#example-code--add-new-data-based-on-aggregation)
8. [Example: Pivot a transaction log into a "people and what they did" summary](#example-code--pivot-a-course-registration-log-to-a-people-and-what-they-registered-for-summary)
9. [Example: Concatenate unique first+last names from every CSV in a folder](#example-code--concatenate-unique-firstlast-names-from-every-csv-in-a-folder-if-the-file-has-them)
10. [Tips](#tips-for-learning-more)

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

### Sample CSV #2

* Has 7 rows, 5 columns _(different ones than sample CSV #1)_
* Meant to represent records from a "people"-typed table in "Data Source #2"

{% assign sampletwo=site.data.sample2 %}

<table>
    <thead>
    {% for column in sampletwo[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in sampletwo %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

### Sample CSV #3

* Has 9 rows, 5 columns
* Meant to represent records from a "people"-typed table in "Data Source #3"

{% assign samplethree=site.data.sample3 %}

<table>
    <thead>
    {% for column in samplethree[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in samplethree %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

### Sample CSV #4

* Has 6 rows, 4 columns
* Meant to represent records from a "transactions"-typed table in "Data Source #4"

{% assign tallyin=site.data.tallypivotinput %}

<table>
    <thead>
    {% for column in tallyin[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in tallyin %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

---

## Second, a note on "°°°"

* °°°, when I'm talking about "operations" you can use in code, means "something goes here"

* When there are lots of "somethings," I'll use °°°1°°°, °°°2°°°, etc.

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

{% assign out_fiveline=site.data.out_fiveline %}

<table>
    <thead>
    {% for column in out_fiveline[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_fiveline %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

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

{% assign out_lastcs=site.data.out_lastcs %}

<table>
    <thead>
    {% for column in out_lastcs[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_lastcs %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

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
print('---Let\'s see what kind of output "df.loc[]" generates---')
print(df.loc[theseRowsLastNamesStartWithCapitalS,'Last'])
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

    ---Let's see what kind of output "df.loc[]" generates---
    4    Shiva
    5    Smith
    Name: Last, dtype: object
    ---We have modified the Python variable "df" to have 3 new rows, plus changes in the "Last" and "Email" columns on specific rows only, and we dropped the "Id" and "Company" rows, and finally, we renamed the "First," "Last," and "Email" columns.---
      First Name Last Name   Email Address New1 New2 New3
    0      Jimmy    Buffet  jb@example.com  NaN  NaN  eee
    1    Shirley  Chisholm             bbb  NaN  ddd  eee
    2    Marilyn    Monroe             bbb  NaN  ddd  eee
    3      Cesar    Chavez  cc@example.com  NaN  NaN  eee
    4    Vandana       aaa  vs@example.com  ccc  NaN  eee
    5     Andrea       aaa             bbb  ccc  ddd  eee
    6     Albert    Howard             bbb  NaN  ddd  eee

{% assign out_complexupdates=site.data.out_complexupdates %}

<table>
    <thead>
    {% for column in out_complexupdates[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_complexupdates %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

### Test yourself!

[Click here](https://repl.it/@rplrpl/Filter-out-rows-last-name-not-C-or-S){:target="_blank"} and make something cool.

_(Note:  first run takes a minute or so.)_

Feel free to backspace over anything you want, except the first 3 lines, which import the CSV file:

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('sample1.csv')
```

There's a lot of code in this example that you didn't see in the other examples, so poke at them and see what you can get to run!  Have fun and get creative.

Bored?  Try throwing in some other [common Python/Pandas operations](../commonoperations){:target="_blank"} once you're feeling confident.

* Hint #1:  Remember that you can "checkpoint" your work by storing the output of "expressions" into "variables" _(nicknames you can use later in your code)_.  4 examples from the code above are:

  * `theseRowsLastNamesStartWithCapitalS = df['Last'].str.startswith('S')`, which saves a Pandas "Series" into a "variable" called "theseRowsLastNamesStartWithCapitalS"

  * `df = df.drop(['Id','Company'], axis=1)`:  what's going on here is that the right side of the "`=`" outputs a new "Pandas DataFrame" _(table)_ that is just like the one currently stored in the variable called "df" _(at the time that this line of code begins)_ ... and then it completely wipes out everything that was stored in "df" and overwrites its contents so that instead, the **new** output from the right side of the "`=`" becomes the value of the variable called "df" for all lines of code afterwards.

* Hint #2:  Certain code fragments aren't "variables" but are nevertheless comfortable sitting on the left side of an "`=`", and they behave in special ways when put there.  Easiest to explain by example:

  * `df['New3'] = 'eee'` modifies the contents of the "Pandas DataFrame" _(table)_ saved in the variable called "df" so that every row of its column labeled "New3" will now contain the text "eee".

    * And if the "Pandas DataFrame" stored in "df" doesn't yet have a "New3" column?  Add it, filling in all the values with "eee."<br/>&nbsp;

  * `df.loc[theseRowsLastNamesStartWithCapitalS,'Last'] = 'aaa'`, modifies the contents of the "Pandas DataFrame" _(table)_ saved in the variable called "df" so that any rows of its column labeled "Last" that have the same row-number as the rows of the "Pandas Series" called "theseRowsLastNamesStartWithCapitalS" will now contain the text "aaa".

    * And if the "Pandas DataFrame" stored in "df" doesn't yet have a "Last" column?  Add it, filling in only "aaa" in the appropriate rows, leaving the rest blank.<br/>&nbsp;

* Hint #3:  If you want to get *really* geeky, knowing what *kind* of data is coming out of the "expressions" you're building (or what kind of "output" values you're storing into "variables") can be *really* handy if you want to consult online coding manuals.  Try putting a variable name you've already stored a value in, or any piece of code that outputs a value, inside the "°°°" of a line that says "[print(type(°°°))](https://docs.python.org/3/library/functions.html#type){:target="_blank"}" to see what "data type" that value is considered by Python, which influences how code around it behaves.

---

## Example Code:  Merging 2 CSV files w/ a multi-column match

[Click here](https://repl.it/@rplrpl/Merging-2-CSV-files-with-multi-column-matching){:target="_blank"} to run code like this.

_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df1 = pandas.read_csv('C:\\yay\\sample1.csv', dtype=object)
df2 = pandas.read_csv('C:\\yay\\sample2.csv', dtype=object)
mergedf = df1.merge(df2.rename(columns = {'LastName':'Last', 'FirstName':'First', 'Em':'Email'}), how='outer', on=['Last', 'First'], suffixes=('_csv1', '_csv2'))
print('---Contents of DataFrame "mergedf":---')
print(mergedf)
mergedf.to_csv('C:\\yay\\out_outermerge.csv', index=False, quoting=1)
```

{% assign out_outermerge=site.data.out_outermerge %}

<table>
    <thead>
    {% for column in out_outermerge[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_outermerge %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

### Test yourself!

[Click here](https://repl.it/@rplrpl/Merging-2-CSV-files-with-multi-column-matching){:target="_blank"} and edit the code so that instead of so that instead of displaying everybody in both files, we only display the people from "CSV #2," but we add in their _details_ from "CSV #1" if they happen to appear in that CSV file, but only consider them a match if Last Name, First Name, AND EMAIL all match _(meaning that we won't pull in any "CSV #1" data about Albert Howard, since he has a different email address in that file)_.

_(Note:  first run takes a minute or so.)_

* Hint #1:  you're going to want to change what's in the "`on=°°°`" parameter of the "[°°°1°°°.merge(°°°2°°°, how='°°°3°°°', on=°°°3°°°, suffixes=°°°4°°°)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.merge.html){:target="_blank"}" operation as well as the "`how='°°°'`" parameter of that same operation.<br/>Your options for "how" are "outer," "inner," "left," and "right."<br/>

* Hint #2:  When you "[print(°°°)](https://docs.python.org/3/library/functions.html#print){:target="_blank"}" a "Pandas DataFrame," blank cells show up as NaN so you can tell them apart from blank-_looking_ values like a single space.  Don't worry -- if you run "[°°°1°°°.to_csv(°°°2°°°, index=False, quoting=1)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.to_csv.html){:target="_blank"}" against it, the cells go back to being blank again!

Keep trying until your output looks like this -- be sure you have Donald Duck and not Jimmy Buffet in your output!

    ---Contents of DataFrame "mergedf":---
         Id    First    Last                  Email                   Company PersonId FavoriteFood
    0   294  Marilyn  Monroe         mm@example.com                       Fox     x934      Carrots
    1   827  Vandana   Shiva         vs@example.com                  Navdanya      02e     Amaranth
    2  9284   Andrea   Smith         as@example.com  University of California    9e84f         Kale
    3   NaN  Shirley  Temple         st@example.com                       NaN    983mv    Lollipops
    4   NaN   Donald    Duck         dd@example.com                       NaN    k28fo     Pancakes
    5   NaN   Albert  Howard  ahotherem@example.com                       NaN      8xi     Potatoes

---

## Example Code:  Filter rows based on aggregations

[Click here](https://repl.it/@rplrpl/Filter-rows-based-on-aggregations){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('C:\\yay\\sample3.csv', dtype=object, parse_dates=['Actv Date'])
groupingByAddress = df.groupby('Address')
groupedDataFrame = groupingByAddress.apply(lambda x: x[x['D.O.B.'] == x['D.O.B.'].max()])
outputdf = groupedDataFrame.reset_index(drop=True)
print(outputdf)
outputdf.to_csv('C:\\yay\\out_oldest_person_per_address.csv', index=False, quoting=1)
```

{% assign out_oldest_person_per_address=site.data.out_oldest_person_per_address %}

<table>
    <thead>
    {% for column in out_oldest_person_per_address[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_oldest_person_per_address %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

_There seem to be twins at one of the addresses!_

### Enhance your skills!

This example ... has a lot to unpack.  So much that if you just start playing around and hitting "run," you might not learn much.

I recommend reading [this blog post](http://oracle2salesforce.blogspot.com/2016/12/filtering-rows-by-maximum-date-per-group.html){:target="_blank"} for a full explanation of what's going on in those 8 lines of code.

* Note that the blog post uses an equivalent problem on different data:  it's going for "most recent correspondence per company" instead of "oldest person per address."

THEN [click here](https://repl.it/@rplrpl/Filter-rows-based-on-aggregations){:target="_blank"} to have some fun trying all sorts of fun with aggregations.

_(Note:  first run takes a minute or so.)_

Feel free to backspace over anything you want, except the first 3 lines, which import the CSV file:

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('sample3.csv')
```

After reading [the blog post](http://oracle2salesforce.blogspot.com/2016/12/filtering-rows-by-maximum-date-per-group.html){:target="_blank"}, you might have noticed that some of the intermediate steps were practically an Excel PivotTable.

Yes!  Good catch!

You can do things like PivotTables with Python and Pandas.  This is one reason scientists and "data scientists" **love** Python and Pandas.  They're always summarizing data in one way or another.

Getting the output to export to CSV the way you envision it can be a bit tricky, to be honest, as a lot of the commands pertaining to PivotTable-style aggregation aren't as intuitive as the other commands you've seen.

But isn't it **neat** that there's a relatively simple programming language powerful enough to let you hop back and forth between row-modification, filtering, pivot-table-style-aggregations, and then treating that PivotTable as if it were a "normal table?"

Such a process would be **so much** copying and pasting into new tabs in Excel.

---

## Example Code:  Add new data based on aggregation

Instead of eliminating rows that aren't the oldest person at an address, you can merely add a new column noting who is.  The code still starts out by saving data to a variable called "groupingByAddress," but from there on out, it's different.

[Click here](https://repl.it/@rplrpl/Add-new-data-based-on-aggregation){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('C:\\yay\\sample3.csv', dtype=object, parse_dates=['D.O.B.'])
groupingByAddress = df.groupby('Address')
rowIsOldestPersonAtAddress = df['D.O.B.'] == groupingByAddress['D.O.B.'].transform('max')
df['IsOldestAtAddr'] = False
df.loc[rowIsOldestPersonAtAddress, 'IsOldestAtAddr'] = True
print(df)
df.to_csv('C:\\yay\\out_noted_if_is_oldest_per_address.csv', index=False, quoting=1)
```

{% assign out_noted_if_is_oldest_per_address=site.data.out_noted_if_is_oldest_per_address %}

<table>
    <thead>
    {% for column in out_noted_if_is_oldest_per_address[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_noted_if_is_oldest_per_address %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

Note that we add a column "IsOldestAtAddr" and set the whole thing to "False" before adding a conditional "True" to some of its cells with our command on the next line.

If we hadn't included the first "False" line, our new "IsOldestAtAddr" would have still been created, but there would have been blank spaces instead of "False."

In some cases, that may be exactly what you'd like to do.

---

## Example Code:  Pivot a course-registration log to a "people and what they registered for" summary

[Click here](https://repl.it/@rplrpl/Pivoting-transaction-rows-to-one-row-per-person){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
import numpy
pandas.set_option('expand_frame_repr', False)
df = pandas.read_csv('C:\\yay\\sample4.csv')
df['Program Registered For'] = 'Program' + df['Program Registered For']
non_program_columns = list(filter(lambda x: x!= 'Program Registered For', df.keys()))
pivotdf = pandas.pivot_table(df, index=non_program_columns, columns='Program Registered For', aggfunc=numpy.size)
pivotdf[pandas.notnull(pivotdf)] = 'Registered'
pivotdf.reset_index(inplace=True)
print(pivotdf)
pivotdf.to_csv('C:\\yay\\out_pivoted_program_registrations.csv', index=False, quoting=1)
```

{% assign tallyout=site.data.tallypivotoutput %}

<table>
    <thead>
    {% for column in tallyout[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in tallyout %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

_(This could be useful for updating a simple "people" table, like a mailing list, with a summary of who already took which courses, so you don't spam them asking them to take the course again.)_

---

## Example Code:  Concatenate unique first+last names from every CSV in a folder, if the file has them

[Click here](https://repl.it/@rplrpl/Concatenate-unique-firstlast-names-from-every-folder-CSV){:target="_blank"} to run code like this.<br/>_(Note:  first run takes a minute or so.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
inputfolder = 'C:\\yay\\folder\\'
listOfDFsToConcatenate = []
for file in [f for f in os.listdir(inputfolder) if f.endswith('.csv')]:
    df = pandas.read_csv(os.path.join(root, file))
    df = df.rename(columns = {'First Name':'First', 'FirstName':'First', 'Last Name':'Last', 'LastName':'Last'})
    if 'First' in df.columns and 'Last' in df.columns:
        df = df[['First','Last']]
        df['SourceFile'] = file
        listOfDFsToConcatenate.append(df)
concatdf = pandas.concat(listOfDFsToConcatenate, ignore_index=True)
concatdf = concatdf.drop_duplicates(subset=['First','Last'])
print(concatdf)
concatdf.to_csv('C:\\yay\\out_concatenated_unique_names.csv', index=False, quoting=1)
```

{% assign out_concatenated_unique_names=site.data.out_concatenated_unique_names %}

<table>
    <thead>
    {% for column in out_concatenated_unique_names[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in out_concatenated_unique_names %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

In this example, presume our 4 sample CSV files are all stored at `C:\yay\folder\`.

We loop through every file ending in ".csv" in it.

If the file has a "First" and a "Last" column, it's a candidate for concatenation.

We pre-process a bit to also accept "FirstName," "First Name," "LastName," and "Last Name."  _(Note that the pre-processing shown isn't terribly robust in case of a file that has both "First Name" and "First.")_

If the CSV file is a candidate for concatenation, we strip it down to just its "First" and "Last" columns, then add a third "SourceFile" column.

Then, after we've set aside all such CSV files into a Python "list" of "Pandas DataFrames," we concatenate them all ("`ignore_index=True`" indicating that we want to continue our line-numbering system, not start over at 0, when the concatenated file starts from the next CSV file).

Finally, in this case, we decide that we only want to keep the first time we encountered a given First+Last name combination, so we "drop the duplicates."

---

## Tips for learning more

**IMPORTANT**:  Never, ever, ever use your company's actual data in an online code editor.  You have no idea who's collecting what on the other side.  Always [install a proper "IDE" on your hard drive](http://oracle2salesforce.blogspot.com/2016/12/installing-python-3-on-windows.html){:target="_blank"} before playing with sensitive data in Python.

Once you practice Python & Pandas enough to understand how the ["output values" of "expressions"](../commonoperations){:target="_blank"} impact the way you can write code, and to have a sense for how easy it is to daisy-chain little CSV-file transformations into bigger ones, and once you save enough sample files of your "practice" work to have a personal quick-reference _(or bookmark this site)_, you will be well on your way to knowing how to write Python+Pandas programs that actually save you more time than opening up Excel and doing the job by hand.

In my opinion, you'll get a lot of "bang for your buck" out of Python:

* To process files so big that Excel freezes when you try to filter and delete rows

* To process files with zip codes that contain "leading zeroes."<br/>

  * Just be sure to write something along the lines of  "[pandas.read_csv('mydata.csv', dtype={'HomeZip' : object, 'BizZip' : object})](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html){:target="_blank"}" when importing your CSV file to indicate that the data in those columns should be interpreted as text, not numbers.<br/>&nbsp;<br/>

* For features that are annoying in Excel _(e.g. multi-column VLOOKUP)_

* To combine with other things Python is good at (such as inspecting every CSV file in a directory on your hard drive and repeating the same steps for all of them).

* As a "Run button" for repetitive work _(that is, as an alternative to macros that would otherwise be difficult to record/write)_

Don't let your lack of ability to do an _entire_ CSV-handling transformation in Python stop you.  I often heed [Randall Munroe's advice from XKCD cartoon #1319](https://xkcd.com/1319/){:target="_blank"} and do things in Excel until they become annoying, do the annoying part in Python, then switch back to Excel.

Believe in yourself, and how much saved-time-in-Excel you're worth!
