---
layout: default
title: Python for CSV Processing Hands-On Demo Slides and Examples
summary: Conference-Length Hands-On Demo
image: /pypancsv/images/craftingpython.png
---

## Python for Spreadsheet Manipulation - Hands-On Demo

### Table of Contents

* [Slides](#slides-pdf)
* [Exercises we did](#exercises-we-did)
* [Further Resources](#further-resources)

### Slides PDF

[Click here to download a PDF of the slides](Demo201901.pdf){:target="_blank"}

### Exercises We Did

We started with this code, which you can edit [edit here](https://repl.it/@rplrpl/40-Minute-Semi-Hands-On-Starter-Code){:target="_blank"}:

```python
import pandas
pandas.set_option('expand_frame_repr', False)

filepath1 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample1.csv'
filepath2 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample2.csv'
filepath3 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample3.csv'
filepath4 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample4.csv'

# ################################################################################
# Everything above this point is code from the teacher that you should not delete.
# ################################################################################
```

By the time we were finished, we ended up with this code _(which includes a lot of code we "commented out" as we proceeded so that it would no longer run)_:
```python
import pandas
pandas.set_option('expand_frame_repr', False)

filepath1 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample1.csv'
filepath2 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample2.csv'
filepath3 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample3.csv'
filepath4 = 'https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample4.csv'

# ################################################################################
# Everything above this point is code from the teacher that you should not delete.
# ################################################################################

def p(input):
	print(input)
	print('---DIVIDER---')

#p('Hello World')

df1 = pandas.read_csv(filepath1)
#p(df1)

'''
p(len(df1))
p(df1.columns)
p(len(df1.columns))
p(list(df1.columns))
p(sorted(df1.columns, key=str.lower))
'''

lcol = df1['Last']
'''
p(lcol)
p(list(lcol))
lcolunq = lcol.unique()
p(lcolunq)
p(len(lcolunq))
'''

'''
flcolnames = ['First','Last']
flcols = df1[flcolnames]
p(flcols)
fcol = df1['First']
allnames = pandas.concat([lcol,
fcol])
p(sorted(allnames))
'''

df2 = pandas.read_csv(filepath2)
df2match = df2.rename(columns={'FirstName':'First','LastName':'Last'})
mergedf = df1.merge(df2match, on=flcolnames, how='outer', indicator=True)
#p(mergedf)
#p(mergedf.query('_merge != "both"'))

mergedf.to_csv('mergeoutput.csv', index=0)
```

#### Exercise 1

This code addition:

```python
def p(input):
	print(input)
	print('---DIVIDER---')
p('Hello World')
```

Produced this output:

```
Hello World
---DIVIDER---
```

#### Exercise 2

This code addition:

```python
df1 = pandas.read_csv(filepath1)
p(df1)
```

Produced this output:

```
      Id    First      Last           Email                      Company
0   5829    Jimmy    Buffet  jb@example.com                          RCA
1   2894  Shirley  Chisholm  sc@example.com       United States Congress
2    294  Marilyn    Monroe  mm@example.com                          Fox
3  30829    Cesar    Chavez  cc@example.com          United Farm Workers
4    827  Vandana     Shiva  vs@example.com                     Navdanya
5   9284   Andrea     Smith  as@example.com     University of California
6    724   Albert    Howard  ah@example.com  Imperial College of Science
---DIVIDER---
```

#### Exercise 3

This code addition:

```python
p(len(df1))
p(df1.columns)
p(len(df1.columns))
p(list(df1.columns))
p(sorted(df1.columns, key=str.lower))
```

Produced this output:

```
7
---DIVIDER---
Index(['Id', 'First', 'Last', 'Email', 'Company'], dtype='object')
---DIVIDER---
5
---DIVIDER---
['Id', 'First', 'Last', 'Email', 'Company']
---DIVIDER---
['Company', 'Email', 'First', 'Id', 'Last']
---DIVIDER---
```

#### Exercise 4

This code addition:

```python
lcol = df1['Last']
p(lcol)
p(list(lcol))
lcolunq = lcol.unique()
p(lcolunq)
p(len(lcolunq))
```


Produced this output:

```
0      Buffet
1    Chisholm
2      Monroe
3      Chavez
4       Shiva
5       Smith
6      Howard
Name: Last, dtype: object
---DIVIDER---
['Buffet', 'Chisholm', 'Monroe', 'Chavez', 'Shiva', 'Smith', 'Howard']
---DIVIDER---
['Buffet' 'Chisholm' 'Monroe' 'Chavez' 'Shiva' 'Smith' 'Howard']
---DIVIDER---
7
---DIVIDER---
```

### Further Resources

* [Official documentation of Pandas commands](https://pandas.pydata.org/pandas-docs/stable/api.html){:target="_blank"}
  * [Official documentation of Pandas commands available for every "Series"-typed expression](https://pandas.pydata.org/pandas-docs/stable/api.html#series){:target="_blank"}
  * [Official documentation of Pandas commands available for "Series"-typed expressions that contain plaintext cells](https://pandas.pydata.org/pandas-docs/stable/api.html#string-handling){:target="_blank"}
* [Quick Examples](/pypancsv/quickexamples){:target="_blank"} for some exercises you can play with yourself
* [Re-implementation of some "Joy of Data" session computations](https://repl.it/@rplrpl/Happy-Spreadsheets-GusDay2019-Play){:target="_blank"} -- if you also attended the "Joy of Data" Google Sheets session, you may enjoy seeing my attempt to re-implement the calculations in Python.  Skipped re-implementing the entire interactive "Team Report" tab -- it's so visual, it's just not suited to a behind-the-scenes spreadsheet-editing approach like command-line programming.  Just because you CAN use a chainsaw to carve watermelon art doesn't mean you SHOULD.  As I mentioned ... I don't ALWAYS edit my spreadsheets with Python.  I still use Excel a lot.  That "Team Report" tab is a great example of why.
