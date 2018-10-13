# Zoom VIDEOCONFERENCE link:
# [https://bit.ly/2naF1N8](https://bit.ly/2naF1N8){:target="_blank"}

---

# Instructions & Code Snippets You Will Need

## Notes:

* All links you will need start with "https://link.stthomas.edu/**sfpy**..."
* If the "Codebunk" development environment gives you trouble, all "starter code" links can have "-b" _(a hyphen and a lowercase letter b)_ added to the end of them to get the same "starter code" in a slower-but-less-finicky environment called "Repl.it"

---

## Quick Links To Sections Of These Instructions

1. [Starter Code:  "hello"](#1-starter-code--hello)
2. [Starter Code:  "readcsv"](#2-starter-code--readcsv)

---

## 1. [Starter Code:  "hello"](https://link.stthomas.edu/sfpyhello){:target="_blank"}
[https://link.stthomas.edu/sfpyhello](https://link.stthomas.edu/sfpyhello){:target="_blank"}

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
  
## Exercise 1B:  Modifying the "hello" starter code and running your modifications

* For this exercise, change the phrase `Hello World` to instead say `Yay Us`.
* There's no need to re-load the "hello" starter code, but if you did, you'll have to re-do Exercise 1A (all the "fork" stuff).

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

## Exercise 2A:  Running the "readcsv" starter code

* For this exercise, we're just:
  * making sure we can run the starter code and
  * looking at the output
* _(Remember all the "fork" stuff when you first load the starter code!)_

## Exercise 2B:  Changing `df1` to `df2` and seeing the new output

* Be sure not to change `df1` to `df2` in the line at the top where we read the first CSV file into `df1`.  Leave that alone.
* Change `df1` to `df2` in all of the `print()` statements and re-run the code and look at the differences in the output.

## Exercise 2C:  Changing `df2` to `df3` in all of the `print()` statements and re-running the code

* Be sure not to change `df2` to `df3` in the line at the top where we read the second CSV file into `df2`.  Leave that alone.

## --Break--

* Leave your code up -- we'll pick up where we left off.

## Exercise 2D:  Inspecting "unique addresses" in `df3`

* Note that in the slideshow page header, I labeled this exercise "df3-A."
* "Comment out" _(render unrunnable)_ all of our previous `print()` statements by putting `'''` before the first line of `print()` statements and `'''` after the last line of `print()` statements
* At the end of the code, add the following new line and run your program:
```python
print(df3['Address'].unique())
```
* You should see the following output:
```
['305 Grover Lane, Sunny, AK' '800 Golden Leaf Street, Snowy, NM' '87834 Lyons Terrace, Rainy, OR' '98 Paget Trail, Cloudy, WY']
```

## Exercise 2E:  Counting "unique addresses" in `df3`

* Note that in the slideshow page header, I labeled this exercise "df3-B."
* At the end of the code, add the following new line and run your program:
```python
print(len(df3['Address'].unique()))
```
* You should see the following output _(note the number "4" on the 2nd line)_:
```
['305 Grover Lane, Sunny, AK' '800 Golden Leaf Street, Snowy, NM' '87834 Lyons Terrace, Rainy, OR' '98 Paget Trail, Cloudy, WY']
4
```

## Exercise 2F:  Playing with `.drop_duplicates()` against `df3`

* Note that in the slideshow page header, I labeled this exercise "df3-C."
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

