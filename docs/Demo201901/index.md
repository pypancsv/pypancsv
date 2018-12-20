---
layout: default
title: Python for CSV Processing Hands-On Demo Slides and Examples
summary: Conference-Length Hands-On Demo
image: /pypancsv/images/craftingpython.png
---

## Python for Spreadsheet Manipulation - Hands-On Demo

### Table of Contents

* [Exercises we did](#exercises-we-did)
* [Slides](#slides-pdf)
* [Further Resources](#further-resources)

### Exercises We Did

We started with this code, which you can edit [edit here](here){:target="_blank"}:

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


### Slides PDF

[Click here to download a PDF of the slides](Demo201901.pdf){:target="_blank"}

### Further Resources

* [Official documentation of Pandas commands](https://pandas.pydata.org/pandas-docs/stable/api.html){:target="_blank"}
  * [Official documentation of Pandas commands available for every "Series"-typed expression](https://pandas.pydata.org/pandas-docs/stable/api.html#series){:target="_blank"}
  * [Official documentation of Pandas commands available for "Series"-typed expressions that contain plaintext cells](https://pandas.pydata.org/pandas-docs/stable/api.html#string-handling){:target="_blank"}
* [Quick Examples](/pypancsv/quickexamples){:target="_blank"} for some exercises you can play with yourself
