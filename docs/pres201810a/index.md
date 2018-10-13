# Zoom VIDEOCONFERENCE link:
# [https://bit.ly/2naF1N8](https://bit.ly/2naF1N8){:target="_blank"}

---

# Instructions & Code Snippets You Will Need

## Notes:

* All links you will need start with "https://link.stthomas.edu/**sfpy**..."
* If the "Codebunk" development environment gives you trouble, all "starter code" links can have "-b" _(a hyphen and a lowercase letter b)_ added to the end of them to get the same "starter code" in a slower-but-less-finicky environment called "Repl.it"

---

## Table of Contents

1. [Starter Code:  "hello"](#1-starter-code--hello)
  * [Exercise 1A](#ex1a)
  * [Exercise 1B](#ex1b)
  * [Exercise 1C](#ex1c)
2. [Starter Code:  "readcsv"](#2-starter-code--readcsv)
  * [Exercise 2A](#ex2a)
  * [Exercise 2B](#ex2b)
  * [Exercise 2C](#ex2c)
  * _(--Break-- -- leave your code up)_
  * [Exercise 2D](#ex2d)
  * [Exercise 2E](#ex2e)
  * [Exercise 2F](#ex2f)
3. [Starter Code:  "123"](#3-starter-code--123)
  * [Exercise 3A](#ex3a)
  * [Exercise 3B](#ex3b)
  * [Exercise 3C](#ex3c)
  * [Exercise 3D](#ex3d)
  * [Exercise 3E](#ex3e)
  * [Exercise 3F](#ex3f)
  * [Exercise 3G](#ex3g)
  * [Exercise 3H](#ex3h)
  * [Exercise 3I](#ex3i)
  * _(--Break--)_
4. [Starter Code:  "filter1"](#4-starter-code--filter1)
  * [Exercise 4A](#ex4a)
  * [Exercise 4B](#ex4b)

---

## 1. [Starter Code:  "hello"](https://link.stthomas.edu/sfpyhello){:target="_blank"}
[https://link.stthomas.edu/sfpyhello](https://link.stthomas.edu/sfpyhello){:target="_blank"}

<div id='ex1a'/>
## Exercise 1A:  Running the "hello" starter code

* For this exercise, we're just making sure we can run the starter code.  Remember that in Codebunk, you can't just run the "starter code."  to make your code runnable _(which also makes it editable)_, you have to:
  1. Type something into the "what name do you want to run this as?"
  2. Click "Fork" at the far right-hand side of the screen
  3. Type something into the "what name do you want to run this as?"
  
### **IMPORTANT**:

Did you notice that when you "forked" your code, you got a new URL in your browser's URL bar?

No worries if you didn't notice.

But that new URL is **yours**.  If you need help and want to show someone else your code, you can send them that URL.

_(If you open someone else's URL, be careful not to get it confused with your own code!  Also note that I believe you won't be able to run it without in turn "forking" **it** into a new URL, which is great -- you shouldn't be able to mess up anybody else's code, and if you make fixes and want to send them back a "fixed" copy, you can just send back your "fork" of their "fork" -- note that we're now 3 "forks" in from the original "starter code!")_
  
<div id='ex1b'/>
## Exercise 1B:  Modifying the "hello" starter code and running your modifications

* For this exercise, change the phrase `Hello World` to instead say `Yay Us`.
* There's no need to re-load the "hello" starter code, but if you did, you'll have to re-do Exercise 1A (all the "fork" stuff).

<div id='ex1c'/>
## Exercise 1C:  Modifying the "hello" starter code to see what  `print()` and `print(type())` statements do with various inputs

* Backspace out or "comment out" your old `print('Yay Us!')` code.
* Enter the following lines of code, one at a time, running each line after you enter it _(guessing what you'll see before you hit "run")_:

```python
print('Hello World')
print(type('Hello World'))
print(5)
print(type(5))
print(None)
print(type(None))
print(False)
print(type(False))
print(3 * 2.5 * 4)
print(type(3 * 2.5 * 4))
print(3 * 2.5 * 4 < 1)
print(type(3 * 2.5 * 4 < 1))
myFirstVariable = 3 * 2.5 * 4
print(myFirstVariable)
print(type(myFirstVariable))
print(myFirstVariable < 1)
print(type(myFirstVariable < 1))
print('Bye!')
```

---

## 2. [Starter Code:  "readcsv"](https://link.stthomas.edu/sfpyreadcsv){:target="_blank"}
[https://link.stthomas.edu/sfpyreadcsv](https://link.stthomas.edu/sfpyreadcsv){:target="_blank"}

<div id='ex2a'/>
## Exercise 2A:  Running the "readcsv" starter code

* For this exercise, we're just:
  * making sure we can run the starter code and
  * looking at the output
* _(Remember all the "fork" stuff when you first load the starter code!)_

<div id='ex2b'/>
## Exercise 2B:  Changing `df1` to `df2` and seeing the new output

* Be sure not to change `df1` to `df2` in the line at the top where we read the first CSV file into `df1`.  Leave that alone.
* Change `df1` to `df2` in all of the `print()` statements and re-run the code and look at the differences in the output.

<div id='ex2c'/>
## Exercise 2C:  Changing `df2` to `df3` in all of the `print()` statements and re-running the code

* Be sure not to change `df2` to `df3` in the line at the top where we read the second CSV file into `df2`.  Leave that alone.

## --Break--

* Leave your code up -- we'll pick up where we left off.

<div id='ex2d'/>
## Exercise 2D:  Inspecting "unique addresses" in `df3`

* "Comment out" _(render unrunnable)_ all of our previous `print()` statements by putting `'''` before the first line of `print()` statements and `'''` after the last line of `print()` statements
* At the end of the code, add the following new line and run your program:
```python
print(df3['Address'].unique())
```
* You should see the following output:
```
['305 Grover Lane, Sunny, AK' '800 Golden Leaf Street, Snowy, NM' '87834 Lyons Terrace, Rainy, OR' '98 Paget Trail, Cloudy, WY']
```

<div id='ex2e'/>
## Exercise 2E:  Counting "unique addresses" in `df3`

* At the end of the code, add the following new line and run your program:
```python
print(len(df3['Address'].unique()))
```
* You should see the following output _(note the number "4" on the 2nd line)_:
```
['305 Grover Lane, Sunny, AK' '800 Golden Leaf Street, Snowy, NM' '87834 Lyons Terrace, Rainy, OR' '98 Paget Trail, Cloudy, WY']
4
```

<div id='ex2f'/>
## Exercise 2F:  Playing with `.drop_duplicates()` against `df3`

* "Comment out" _(render unrunnable)_ your two lines of code from exercises "2D" and "2E" by prefixing them with a `#`
* At the end of the code, add the following new lines of code and run your program:
```python
print(df3.drop_duplicates(['Address'], keep=False)) 
print(len(df3.drop_duplicates(['Address'], keep=False))) 
print(len(df3.drop_duplicates(['Address','D.O.B.'], keep=False)))
```
* You should see the following output:
```
      Id First    Last     D.O.B.                     Address                   
8  67526  Kata  Windus  10/4/1991  98 Paget Trail, Cloudy, WY                   
1                                                                               
7                                                           
```
  * The first two lines of output are a list of people who "live alone" (people who have a unique address) -- our `keep=False` setting in the `.drop_duplicates()` command meant that we didn't want anyone in our output who shared an address with someone else in the data set.
    * The number "8" at the beginning of the 2nd line of output is **just a "row ID"** indicating that Kata Windus was "row #8" of the data set _(starting counting with "0," so conceptually, really more "row #9" -- and in Excel, where headers take up the first row and you start counting with "2," she'd be "row #10")_
  * The third line of output, the number "1," is a count of the number of rows in our previous output -- as we could see, there was just 1.
  * The fourth line of output, the number "7," is a different count:  it's the count of "people who don't live with a twin."
    * As you can see, we added a 2nd parameter to the list of columns indicating our "duplication criteria."  Now we only "drop duplicate rows" from our output if they have the same address AND date of birth as someone else in the data set.
    * It's a 9-row data set, and we only had 2 "twins living together" _(Othelia and Pansy)_, so they were dropped, and that leaves 7 people left.

---

## 3. [Starter Code:  "123"](https://link.stthomas.edu/sfpy123){:target="_blank"}
[https://link.stthomas.edu/sfpy123](https://link.stthomas.edu/sfpy123){:target="_blank"}

<div id='ex3a'/>
## Exercise 3A:  Building a "Pandas Series" of Initials from `df1` first & last name columns

* _(Remember all the "fork" stuff when you first load the starter code!)_
* At the end of the program, add the following code and run the program:
```python
ser1first = df1['First'].str[0]
ser1last = df1['Last'].str[0]
ser1initials = ser1first + '. ' + ser1last + '.'
print(ser1initials)
```
* You should see the following output:
```
0    J. B.
1    S. C.
2    M. M.
3    C. C.
4    V. S.
5    A. S.
6    A. H.
dtype: object
```

<div id='ex3b'/>
## Exercise 3B:  Building a SORTED "Pandas Series" of Initials from `df1` first & last name columns and adding it to `df1` as a new column

* Completely backspace out your line of code from exercise 3A that says `print(ser1initials)`
* At the end of the program, add the following code and run the program:
```python
ser1initsrt = ser1initials.sort_values()
print(ser1initsrt)
df1['Initials'] = ser1initsrt
```
* You should see the following output:
```
6    A. H.
5    A. S.
3    C. C.
0    J. B.
2    M. M.
1    S. C.
4    V. S.
dtype: object
```
* Note how the initials are now in alphabetical order, and that the "row IDs" as initially assigned have "stuck with" their data.
* At the end of the program, add the following code and run the program:
```python
print(df1)
```
* You should see the following output _(note that the initials are with the correct names, despite us "pre-sorting" the "Pandas Series")_:
```
      Id    First      Last           Email                      Company Initials
0   5829    Jimmy    Buffet  jb@example.com                          RCA    J. B.
1   2894  Shirley  Chisholm  sc@example.com       United States Congress    S. C.
2    294  Marilyn    Monroe  mm@example.com                          Fox    M. M.
3  30829    Cesar    Chavez  cc@example.com          United Farm Workers    C. C.
4    827  Vandana     Shiva  vs@example.com                     Navdanya    V. S.
5   9284   Andrea     Smith  as@example.com     University of California    A. S.
6    724   Albert    Howard  ah@example.com  Imperial College of Science    A. H.
```

<div id='ex3c'/>
## Exercise 3C:  Building a SORTED "Python List" of Initials from `df1` first & last name columns and adding it to `df1` as a new column

* Completely backspace out your lines of code from exercise 3B that say `print(ser1initsrt)` and `print(df1)`
* At the end of the program, add the following code and run the program:
```python
list1initsrt = list(ser1initsrt)
df1['Initials'] = list1initsrt
print(list1initsrt)
```
* You should see the following output:
```
['A. H.', 'A. S.', 'C. C.', 'J. B.', 'M. M.', 'S. C.', 'V. S.']
```
* Note how this looks different from the pre-sorted "Pandas Series."
  * "Item IDs" in the list are implied, with "A. H." being "0," "A. S." being "1," etc.
* At the end of the program, add the following code and run the program:
```python
print(df1)
```
* You should see the following output _(note that the intials are all messed up compared to the names!)_:
```
      Id    First      Last           Email                      Company Initials
0   5829    Jimmy    Buffet  jb@example.com                          RCA    A. H.
1   2894  Shirley  Chisholm  sc@example.com       United States Congress    A. S.
2    294  Marilyn    Monroe  mm@example.com                          Fox    C. C.
3  30829    Cesar    Chavez  cc@example.com          United Farm Workers    J. B.
4    827  Vandana     Shiva  vs@example.com                     Navdanya    M. M.
5   9284   Andrea     Smith  as@example.com     University of California    S. C.
6    724   Albert    Howard  ah@example.com  Imperial College of Science    V. S.
```
* Moral of the story:  "Pandas Series" and "Python Lists" are kind of similar, but can behave differently when you're trying to use them for specialized purposes, such as editing the data in a "Pandas DataFrame."

<div id='ex3d'/>
## Exercise 3D:  Trying to sort `df3` from oldest to youngest

* Completely **backspace out** all the code we just wrote in exercises 3A-3C.  We won't need it anymore.
  * Leave in the code that was already in the "starter code."
* At the end of the program, add the following code and run the program:
```python
df3sorted = df3.sort_values(by=['D.O.B.'], ascending=[True])
print(df3sorted[['First','Last','D.O.B.']])
```
* Note the "double brackets" in the 2nd line of code.  By putting a "list of column names" inside the outer brackets following the name of our `df3sorted` "Pandas Dataframe," we are specifying that we only want to see the data from those columns in our output.
  * This is handy when we are working with data that has as lot of columns, but we only need to see a few to spot-check.
* You should see the following output _(did we actually sort people from oldest to youngest?)_:
```
      First        Last      D.O.B.
1  Quintina        Lean  10/14/1963
8      Kata      Windus   10/4/1991
3      Yuri      Dalton  11/12/1980
2     Corny      Noller  12/13/1990
0     Salli      Broxup   12/3/1991
5      Mata  Pierrepont   8/19/1970
6   Othelia    Eastbury    8/4/1955
7     Pansy      Mallya    8/4/1955
4   Doretta      Herche   9/21/2010
```

<div id='ex3e'/>
## Exercise 3E:  Actually sorting `df3` from oldest to youngest
* Don't erase any code from exercise 3D.
* Find the line near the top of the code that already existed in the starter code" that reads like `df3 = pandas.read_csv(…)` and, right after the word `object`, add `, parse_dates=['D.O.B.']` _(with the leading comma)_ so that the line ends up looking like this, and run the code:
```python
df3 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample3.csv', dtype=object, parse_dates=['D.O.B.'])
```
* You should see the following output _(did we actually sort people from oldest to youngest?)_:
```
      First        Last     D.O.B.
6   Othelia    Eastbury 1955-08-04
7     Pansy      Mallya 1955-08-04
1  Quintina        Lean 1963-10-14
5      Mata  Pierrepont 1970-08-19
3      Yuri      Dalton 1980-11-12
2     Corny      Noller 1990-12-13
8      Kata      Windus 1991-10-04
0     Salli      Broxup 1991-12-03
4   Doretta      Herche 2010-09-21
```

<div id='ex3f'/>
## Exercise 3F:  Identifying duplicate rows in `df3` using "all columns" as the "duplicate key"

* Close the tab where you performed exercise 3E and open [https://link.stthomas.edu/sfpy123](https://link.stthomas.edu/sfpy123){:target="_blank"} fresh in a new tab to start the "starter code" over.
  * _(Remember all the "fork" stuff when you first load the starter code!)_
* At the end of the program, add the following code and run the program:
```python
print(df3.duplicated(keep=False))
```
* You should see the following output:
```
0    False
1    False
2    False
3    False
4    False
5    False
6    False
7    False
8    False
dtype: bool
```
* Note that there are no duplicates, because when we take "all columns" into consideration, no two rows in `df3` are exactly alike!

<div id='ex3g'/>
## Exercise 3G:  Identifying duplicate rows in `df3` using "address & birthdate" as the "duplicate key"

* Change the line of code you wrote in exercise 3F to be this line of code instead and run the program:
```python
print(df3.duplicated(['Address','D.O.B.'], keep=False))
```
* You should see the following output:
```
0    False
1    False
2    False
3    False
4    False
5    False
6     True
7     True
8    False
dtype: bool
```
* Note that the `keep=False` setting meant that we wanted ALL "twins living together" flagged "True."
  * There are also `keep='first'` and `keep='last'` options that will only flag the "first row of a duplicate-set" or "last row of a duplicate-set" as "True."

<div id='ex3h'/>
## Exercise 3H:  Counting duplicate rows in `df3` using "address & birthdate" as the "duplicate key"

* Change the line of code you wrote in exercise 3G to be this line of code instead and run the program:
```python
print(df3.duplicated(['Address','D.O.B.'], keep=False).sum())
```
* You should see the following output:
```
2
```
* Because `True` is interpreted as `1` and `False` is interpreted as `0` by the `.sum()` operation available for "Pandas Series"-typed data, we can quickly count the "number of people who live with a twin."
  * This is handy when the data set is too big to eyeball that information from!

<div id='ex3i'/>
## Exercise 3I:  Displaying duplicate rows in `df3` using "address & birthdate" as the "duplicate key"

* Backspace out your code from exercise 3H.
* Add the following code to the end of the program and run the program:
```python
ser3isdup = df3.duplicated(['Address','D.O.B.'], keep=False)
print(df3[ser3isdup])
```
* You should see the following output:
```
      Id    First      Last    D.O.B.                         Address
6  32443  Othelia  Eastbury  8/4/1955  87834 Lyons Terrace, Rainy, OR
7  22082    Pansy    Mallya  8/4/1955  87834 Lyons Terrace, Rainy, OR
```

## --Break--

---

## 4. [Starter Code:  "filter1"](https://link.stthomas.edu/sfpyfilter1){:target="_blank"}
[https://link.stthomas.edu/sfpyfilter1](https://link.stthomas.edu/sfpyfilter1){:target="_blank"}

<div id='ex4a'/>
## Exercise 4A:  Running the "filter1" starter code

* For this exercise, we're just:
  * making sure we can run the starter code and
  * looking at the output
* _(Remember all the "fork" stuff when you first load the starter code!)_

<div id='ex4b'/>
## Exercise 4B:  Changing the "filters" to different business logic

* Business rule change #1
  * Instead of doing:  "Display all columns, but only rows where 'Last' starts with capital 'C' or 'S'" 
  * Do:  "Display all columns, but only rows where 'Company' case-insensitively ends with 'a' or where 'Id' is less than 800"
* Hint:  every "Pandas Series" has the following operations:
  * `.str.lower()` _(the resulting output is also a Series, full of text-typed data)_
  * `.str.upper()` _(the resulting output is also a Series, full of text-typed data)_
  * `.str.endswith(…)` _(the resulting output is also a Series, full of True-False data)_
  * `.astype('int')` _(the resulting output is also a Series, full of integer-typed data)_
* Try it yourself and follow along as volunteers from the face-to-face group come up to my desk to edit the code collaboratively
* It might help to "comment out" all of the code starting with the first `print(…)` statement from the "starter code" so that you can see it for hints but so that it doesn't run.
