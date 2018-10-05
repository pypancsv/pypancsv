<h1>Meeting link:</h1>

<h1><a href="https://link.stthomas.edu/sfpypres1rd1meeting" target="_blank">https://link.stthomas.edu/sfpypres1rd1meeting</a></h1>

<h1>Ignore all these instructions until I get to them.</h1>

These are you to copy/paste from if the screen is grainy from my PowerPoint or I've navigated away from it.  You can also hand-type the code from the PowerPoint if you can type fast enough, for better retention, although watch your typos. :-)

[https://link.stthomas.edu/sfpyhello](https://link.stthomas.edu/sfpyhello)

- Exercise 1:  Get it running

- Exercise 2:  Change Hello World to Yay Us

- Exercise 3:  Backspace or Comment out the Hello World line and, one at a time, type and run each of the following lines of code, guessing the output before you hit run:

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

https://link.stthomas.edu/sfpyreadcsv

- Exercise 1:  Get it running; take a look at what types of commands displayed what

- Exercise 2:  Replace "df1" with "df2" everywhere but the first line.  Contrast output.

- Exercise 3:  Replace "df2" with "df3" everywhere but the first line.  Contrast output.

- Exercise 4:  Comment out all the old "print(...)" statements and add the following line of code and run:

```python
print(df3['Address'].unique())
```
- Exercise 5:  Add the following line of code and run:

```python
print(len(df3['Address'].unique()))
```

- Exercise 6:  Add the following lines of code and run:

```python
print(df3.drop_duplicates(['Address'], keep=False)) 
print(len(df3.drop_duplicates(['Address'], keep=False))) 
print(len(df3.drop_duplicates(['Address','D.O.B.'], keep=False)))
```
