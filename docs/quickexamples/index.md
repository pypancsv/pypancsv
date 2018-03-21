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


[Click here](https://repl.it/@rplrpl/Import-a-CSV-into-Pandas-Print-the-resulting-DataFrame){:target="_blank"} and edit the code so that instead of saying "---Here are the first 5 lines---", it says, "---Here are the last 2 lines---", and edit the next line of code to do just that _(display the last 2 lines)_.

Hint:  it's the "[°°°1°°°.tail(°°°2°°°)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.tail.html){:target="_blank"}" operation).<br/>

_(Note:  first run after editing the code takes a minute or so.)_

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


[Click here](https://repl.it/@rplrpl/Filter-out-rows-last-name-not-C-or-S){:target="_blank"} and edit the code so that instead of saying '---Show all columns, but only rows where "Last" starts with capital "C" or "S"---', it says, '---Show all columns, but only rows where "Company" case-insensitively ends with "a" or "Id" is less than 800---', and edit the next line of code to do just that _(only rows where "Company" ends with "A" or "a" or the "Id" is a number less than 800)_.

Hint #1:  I recommend experimenting with using the "[°°°.str.lower()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.lower.html){:target="_blank"}" or "[°°°.str.upper()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.upper.html){:target="_blank"}" operation against "Company," which you can slip in right before the "[°°°.str.endswith()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.endswith.html){:target="_blank"}"  operation _(which in turn will then operate against the all-uppercased/lowercased copy of the contents of "Company" instead of against the original contents of "Company")_, for the case-insensitive "a" test.'

Hint #2:  You can compare a "Pandas Series" _(e.g. "`df[Last]`")_ directly with a single value.  For example, "*df\[Last\] < 'Ferret'*" outputs a single column indicating "True or False:  Do the contents of 'Last' in this row come earlier in the alphabet than the word 'Ferret'?"

Hint #3:  If, for some reason, your code is displaying _every_ row, try surrounding the pieces inside your outermost "df\[°°°\]" on either side of the "or" (the "`|`") with parentheses.<br/>If "`df[°°°1°°° | °°°2°°°]`" doesn't work for filtering the rows, try "`df[(°°°1°°°) | (°°°2°°°)]`".

_(Note:  first run after editing the code takes a minute or so.)_

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
