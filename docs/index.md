---
layout: default
title: CSV Processing with Python and Pandas - Some Basic Instructions
---

# CSV Processing with Python and Pandas - Some Basic Instructions

I am learning how to host content with GitHub.

## Sample CSV #1

{% assign mydata=site.data.sample1 %}
<table>
    <thead>
    {% for column in mydata[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </thead>
    <tbody>
    {% for row in mydata %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>

## Example Code:  Import CSV -> Pandas.  Print.  Export to new CSV.

[Click here](https://repl.it/@rplrpl/Python-for-Salesforce-Administrators-0002-Reading-In-A-C){:target="_blank"} to run code like this, minus the "export to new CSV" functionality.<br/>_(Note:  first run takes a minute or so.)_

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

## Links

[This is page two](pagetwo){:target="_blank"}
