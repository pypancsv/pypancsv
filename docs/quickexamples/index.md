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

[Click here](https://repl.it/@rplrpl/Import-a-CSV-into-Pandas-Print-the-resulting-DataFrame){:target="_blank"} to run code like this, minus the "export to new CSV" functionality.<br/>_(Note:  first run takes a minute or so.)_

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


[Click here](https://repl.it/@rplrpl/Import-a-CSV-into-Pandas-Print-the-resulting-DataFrame){:target="_blank"} and edit the code so that instead of saying "Here are the first 5 lines," it says, "Here are the last 2 lines," and edit the next line of code to do just that _(display the last 2 lines)_.

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
