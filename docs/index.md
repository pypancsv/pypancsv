---
layout: default
title: CSV Processing with Python and Pandas - Some Basic Instructions
---

# CSV Processing with Python and Pandas - Some Basic Instructions

I am learning how to host content with GitHub.

## Example Code:  Import CSV -> Pandas.  Print.  Export to new CSV.

[Click here](https://repl.it/@rplrpl/Python-for-Salesforce-Administrators-0002-Reading-In-A-C){:target="_blank"} to code like this.

_(Note:  first run, or first run after first editing the code, takes a minute or so.)_

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
