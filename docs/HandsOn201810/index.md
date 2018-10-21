---
layout: default
title: Python for CSV Processing 101 Slides and Video
summary: Salesforce Saturday Hands-On Training
image: /pypancsv/images/handsonslidesnip.jpg
---

## Python for Spreadsheet Manipulation 101 - Hands-On Training for Salesforce Admins

Thanks for coding for THREE HOURS with me on a sunny Saturday!

### Table of Contents

* [Homework](#homework)
* [Exercises we did](#exercises-we-did)
* [Slides](#slides-pdf)
* [Video](#session-recording)
* [Further Resources](#further-resources)
* [Door Prize Scripts](#door-prize-scripts)

### Homework

If I could give you one homework assignment, it'd be to **get Python up and running on your computer**.

If you can't apply this to your real-world business problems, I'm going to cry.

And the number one thing that's going to stop you isn't lack of Python knowledge ... it's not having your tools "ready to go" when you think of a business problem you could solve using it.

Don't make me cry.

* **So your homework is to get an "IDE" set up and to copy/paste [the "Hello World" program](https://codebunk.com/b/612238124/){:target="_blank"} and [the "read a CSV file off the internet and print stuff out about it" program](https://codebunk.com/b/437206634/){:target="_blank"} onto _YOUR_ computer, running them from there.**

As soon as you have both of those code snippets up and running, **the world is at your fingertips**!

[Tweet me when you get it](https://www.twitter.com/KatieKodes){:target="_blank"} -- #AwesomeAdmin & #YayUs !

* For Windows computers on which I have "admin" rights to properly install software, I've really enjoyed working with "[**Anaconda**](https://www.anaconda.com/download/){:target="_blank"}," which both installs Python plus its "Pandas" plugin on your computer _(so that an IDE's "run button" actually does something -- your computer doesn't come "out of the box" understanding Python code)_ and installs the "Spyder" IDE (the actual text-editor-with-run-button).
* For Windows computers on which I don't have permission to install software, I've made good use of [these directions for installing **WinPython**](https://tinyurl.com/PyPanCsvWinIde){:target="_blank"}.  Note that without administrator rights, you might not be able to update certain components of Windows to support the latest version of WinPython, which I address in the directions, but older versions of WinPython make your computer only understand commands from older versions of Python and its Pandas plugin, which might leave you Googling for how things "used to be done" in cases where the way Python code is written has gotten simpler and easier to use as time goes on.
* Some people also like [**PyCharm**](https://www.jetbrains.com/pycharm/){:target="_blank"}.  (Definitely seems available for Windows & Mac...)
* Linux / Mac:  I ... don't have either of those.  Try [**Anaconda**](https://www.anaconda.com/download/){:target="_blank"} -- it seems to be available for both.

DM me [on Twitter](https://www.twitter.com/KatieKodes){:target="_blank"} if you get stuck.

### Exercises We Did

[Click here for the "Exercises" instructions](exercises){:target="_blank"}

### Slides PDF

[Click here to download a PDF of the slides](HandsOn201810.pdf){:target="_blank"}

### Session Recording

> **IMPORTANT NOTE:**
> 
> The links have changed!  The links in the session recording are no longer guaranteed to be accurate!  If they no longer work, or seem to be doing something different, it's because I reused them for another presentation!
> 
> Replacement links are available with a "201810-" after the "sfpy" but before the rest of the URL.
> 
> So .../sfpyhello becomes .../sfpy201810-hello and .../sfpyhello-b becomes .../sfpy201820-hello-b

[![Click here for session video](/pypancsv/images/handsonslidesnip.jpg)](https://www.youtube.com/watch?v=rytPU9_NcGI "Python for Spreadsheet Manipulation 101 - video"){:target="_blank"}

[(Click here for session video)](https://www.youtube.com/watch?v=rytPU9_NcGI "Python for Spreadsheet Manipulation 101 - video"){:target="_blank"}

### Further Resources

* [Official documentation of Pandas commands](https://pandas.pydata.org/pandas-docs/stable/api.html){:target="_blank"}
  * [Official documentation of Pandas commands available for every "Series"-typed expression](https://pandas.pydata.org/pandas-docs/stable/api.html#series){:target="_blank"}
  * [Official documentation of Pandas commands available for "Series"-typed expressions that contain plaintext cells](https://pandas.pydata.org/pandas-docs/stable/api.html#string-handling){:target="_blank"}
* [Quick Examples](/pypancsv/quickexamples){:target="_blank"} of the sort that we went over in class, with a "homework" exercise for each problem

### Door Prize Scripts

Hopefully you can use these at work **yesterday**.

[Tweet me if you use these in real life](https://www.twitter.com/KatieKodes){:target="_blank"} -- #AwesomeAdmin & #YayUs !

#### Duplicate Summarizer

This script, once you give it the location of your CSV file on line 3 and the the set of column names that make up your "duplicate matching key" on line 4, will tell you 5 useful things:

 1. How many rows are a "duplicate" of some other row
 2. How many "groups" of duplicates there are in your CSV file
 3. How many total rows there are in your CSV file
 4. What the "duplicated" rows say in them
 5. What the "nature of the groups" are _(e.g. if you're grouping on "FirstName" & "LastName," a table showing you things like "John Smith," "Jane Doe," etc.)_

```python
import pandas
pandas.set_option('expand_frame_repr', False)
filename = 'c:\\example\\sample.csv' # Edit this before running
dupeColumns = ['col1','col2','col3'] # Edit this before running
df = pandas.read_csv(filename, dtype=object)
isDupeSeries = df.duplicated(dupeColumns, keep=False)
isFirstDupeSeries = df.duplicated(dupeColumns, keep='first')
print(str(isDupeSeries.sum()) + ' dupes in ' + 
      str(isFirstDupeSeries.sum()) + ' groups in ' + 
      str(len(df)) + ' rows')
print('\r\n---The duped rows are:---')
print(df[isDupeSeries])
print('\r\n---The "dupe keys" are:---')
print(df[isFirstDupeSeries][dupeColumns])
```
