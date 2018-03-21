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
