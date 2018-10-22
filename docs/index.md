---
layout: default
title: CSV Processing with Python and Pandas
---

# CSV Processing with Python and Pandas

Welcome!

This site is meant to support my evangelization of Python as a "power tool" for CSV-file processing that isn't much harder to learn than writing fancy Excel formulas is -- and certainly simpler to learn than writing Excel VisualBasic macros by hand.

## Presentation Slide Examples

If you're here after watching a presentation, visit [Quick Examples](quickexamples){:target="_blank"} to:

* Review sample code from the presentation
* Run it yourself
* Test your ability to edit the examples to do something else

### Slides

[October 2018 slides, video, and afterthoughts here](HandsOn201810)

[April 2018 slides PDF here](Presentation201804.pdf){:target="_blank"}

## Common "Operations"

If you've worked your way through the examples and want a further challenge, visit my list of [operations commonly used for CSV processing](commonoperations){:target="_blank"} _(under construction)_ to learn more functions that you can put into your Python scripts.

For example, once you can filter for rows whose "Last Name starts with capital S" you may want to...

* Know what operation would "uppercase" the contents of cells in the "Last Name" column _(handy to do **before** the "capital S" filter for case-insensitivity)_

* Know what operation would check whether numeric cell values in an "Age" column are "< 60"

## Why Learn Python

Python can be really handy for:

* Processing files so big that Excel freezes when you try to filter and delete rows

* Processing files with zip codes that contain "leading zeroes"

* Combining data from 2 CSV files when the "key" for records being "equivalent" is spread out across multiple columns

* Leveraging the fact that Python is good at "programming-ey" things, too -- for example, you could repeat the same steps on every CSV file in a directory

* Scripting repetitive work that would be very difficult to record as an Excel macro.  e.g.:

  * You need to filter, then pivot, then treat that as a new table, then filter again, or
  * Column positions are constantly moving around from day to day, or
  * Column names are constantly changing in a way that has a pattern, but is just enough to confuse an Excel macro
