---
title: "Python for Spreadsheet Manipulation 102 - Hands-On Training for Salesforce Admins"
---

# Zoom VIDEOCONFERENCE link:
# [https://bit.ly/2D0rwbw](https://bit.ly/2D0rwbw){:target="_blank"}

---

## Python for Spreadsheet Manipulation 102 - Hands-On Training for Salesforce Admins ("Salesforce Saturday")

# Saturday, January 26th
# [11:25AM-2PM CST](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20190126T1125&p1=219){:target="_blank"}

This is an online live webcast of a face-to-face training, but I will so my best to monitor the chat for Q&A from online attendees, particularly during designated Q&A times.

---

# "101" recording link

We'll do a quick recap from "101" (see https://pypancsv.github.io/pypancsv/HandsOn201810/).

# "102" material

> 1. Combining spreadsheets on data they share in common (think "VLOOKUP")
> 2. Looping over every file in a directory, running the same program against each file
> 3. Selectively editing data in specific cells or deleting specific rows _(if time)_
> 4. A very basic "pivot" _(if time)_

---

# Instructions & Code Snippets You Will Need

## Notes:

* All links you will need start with "https://link.stthomas.edu/**sfpy**..."
* If the "Repl.it" development environment gives you trouble, try adding "-b" _(a hyphen and a lowercase letter b)_ to the end of the link to see the same thing in a different environment called "Codebunk" _(no guarantee I had time to get them all online in Codebunk, but check ... or just let me know)_

---

## Table of Contents

1. [Exercise 1:  Make sure you can run Python code](#ex1)
2. [Exercise 2:  Reading, displaying, & analyzing a CSV file](#ex2)
  * [Code To Look At:  Python 101 Recap](#recap101)
3. [Exercise 3:  Add/Delete/Rename/Reorder Columns Yourself](#ex3)
  * [Cheat Sheet:  Add/Delete/Reorder/Rename Columns](#colcommands)
  * [Door Prize Script:  Dynamic Rename & Reorder](#doorprize-col)
4. [Exercise 4:  Combine 5 spreadsheets into 1 CampaignMemberRecordsToInsert spreadsheet](#ex4)
 * [Cheat Sheet:  Concatenation Examples ↕](#concat)
 * [Cheat Sheet:  Merge Examples ↔](#merge)
 * [Door Prize Script:  Event-Attendance-Concatenating Loop ↕](#doorprize-concat)

---

<div id='ex1'/>

## Exercise 1:  Make sure you can run Python code

Open [https://link.stthomas.edu/sfpyhello](https://link.stthomas.edu/sfpyhello){:target="_blank"} "starter code."

All it says is this:

```python
print('Hello, world!')
```

Hit the big green "run" button, top center.

Do you see "`Hello, world!`" at right?  Hooray!  (Let me know if not.)

Now **change** `Hello, world!` to `Yay, us!` so that your code looks like this and hit the "run" button again.

Do you see "`Yay, us!`" at right?  Yay, you!  (Let me know if not.  We want to make this a "Yay, us!" moment.)

---

<div id='ex2'/>

## Exercise 2:  Reading, displaying, & analyzing a CSV file

Open the [https://link.stthomas.edu/sfpyfiles](https://link.stthomas.edu/sfpyfiles){:target="_blank"} "starter code."

Add a new line to the end of the file and type these 4 lines exactly as seen here (hitting “enter” to start a new line as indicated):

```python
df1 = pandas.read_csv(filepath1)
print(df1)
print('--------')
print('There are ' + str(len(df1)) + ' rows')
```

Hit the "run" button.

Do you see a table full of contacts at right, then a divider line, then an announcement that there are "7 rows"?

---

<div id="recap101"/>

## Code To Look At:  Python 101 Recap

We'll look together at the code at [https://link.stthomas.edu/sfpy101recap](https://link.stthomas.edu/sfpy101recap){:target="_blank"}

---

<div id='ex3'/>

## Exercise 3:  Add/Delete/Rename/Reorder Columns Yourself

Open the [https://link.stthomas.edu/sfpy123](https://link.stthomas.edu/sfpy123){:target="_blank"} "starter code."

If this "starter code" had a `print(df1)` command in it, `df1` would look like this to start:

```
      Id    First      Last           Email                      Company
0   5829    Jimmy    Buffet  jb@example.com                          RCA
1   2894  Shirley  Chisholm  sc@example.com       United States Congress
2    294  Marilyn    Monroe  mm@example.com                          Fox
3  30829    Cesar    Chavez  cc@example.com          United Farm Workers
4    827  Vandana     Shiva  vs@example.com                     Navdanya
5   9284   Andrea     Smith  as@example.com     University of California
6    724   Albert    Howard  ah@example.com  Imperial College of Science
```

* At the end of the program, add code that modifies the contents of `df1` as follows, and make your last line of code `print(df1)`:
 1. Add a column called `Hello` with the phrase `Yay Us` filled in all the way down
 2. Rename `Last` to `Last Name` and `First` to `First Name`
 3. Delete the `Email` column
 4. Reorder the columns to be `Hello`, `Last Name`, `Company`, `First Name`, & then `Id`.
* You should see the following output:
```
    Hello Last Name                      Company First Name     Id
0  Yay Us    Buffet                          RCA      Jimmy   5829
1  Yay Us  Chisholm       United States Congress    Shirley   2894
2  Yay Us    Monroe                          Fox    Marilyn    294
3  Yay Us    Chavez          United Farm Workers      Cesar  30829
4  Yay Us     Shiva                     Navdanya    Vandana    827
5  Yay Us     Smith     University of California     Andrea   9284
6  Yay Us    Howard  Imperial College of Science     Albert    724
```

Don't forget that:

* You might need to surround column names with single quotes to indicate that they're text, not code
* When typing out a list in your code, you need a pair of square brackets around them to indicate it's a list _(in addition to whatever other square brackets might be present in your code due to Pandas loving square brackets)_

---

<div id="colcommands"/>

## Cheat Sheet:  Add/Delete/Reorder/Rename Columns

<div id="colcommands-add-1"/>

### Adding columns, approach 1 of 2

```python
dfVarName['ColumnName'] = 'abc'
```

or

```python
dfVarName['UpperCaseFirstName'] = dfVarName['FirstName'].str.upper()
```

etc.

<div id="colcommands-add-2"/>

### Adding columns, approach 2 of 2

```python
dfVarName = dfVarName.assign(ColumnName1 = 'abc', ColumnName2 = 'def')
```

or

```python
dfVarName = dfVarName.assign(UpperCaseFirstName = dfVarName['FirstName'].str.upper(), LowerCaseFirstName = dfVarName['FirstName'].str.lower())
```

etc.

<div id="colcommands-del-1"/>

### Deleting columns, approach 1 of 2 _(keep only columns named)_

```python
dfVarName = dfVarName[['ColumnName1','ColumnName2','ColumnName3']]
```

or

```python
dfVarName = dfVarName[varNameHoldingAListOfColumnNames]
```

etc.

<div id="colcommands-del-2"/>

### Deleting columns, approach 2 of 2 _(discard columns named)_

```python
dfVarName = dfVarName.drop(columns=['ColumnName1','ColumnName2','ColumnName3'])
```

or

```python
dfVarName = dfVarName.drop(columns=varNameHoldingAListOfColumnNames)
```

etc.

<div id="colcommands-reo-1"/>

### Reordering columns

```python
dfVarName = dfVarName[['ColumnName1','ColumnName2','ColumnName3']]
```

or

```python
dfVarName = dfVarName[varNameHoldingAListOfColumnNames]
```

etc.

_(They'll come out in the order you specified.)_


<div id="colcommands-ren-2"/>

### Renaming columns

```python
dfVarName = dfVarName.rename(columns={'ColumnName1':'NewColumnName1','ColumnName2':'NewColumnName2'})
```

or

```python
dfVarName = dfVarName.rename(columns=varNameHoldingAMapOfColumnRenameLogic)
```

etc.

---

<div id="doorprize-col"/>

## Door Prize Script:  Dynamic Rename & Reorder

[Tweet me if you use this in real life](https://www.twitter.com/KatieKodes){:target="_blank"} – remember to hashtag #AwesomeAdmin & #YayUs !

This code makes use of intermediate-level Python functionality called "list [comprehensions](https://dbader.org/blog/list-dict-set-comprehensions-in-python){:target="_blank"}" and "dict comprehensions" to build the contents of `columnsWithProgramInTheName` _(a list)_, `theRestOfTheColumns` _(a list)_, and `renamingMap` _(a "dict", which is a data structure to indicate that certain things should "become" other things as specified)_.

They're just concise-to-type "for loops," to be honest.

To build `newColumnOrder` _(a "list")_, this code takes advantage of Python's ridiculously simple grammar for combining two lists:  you just put a "`+`" between them.

What's really neat, though, is that it:

 1. dynamically extracts a list of all columns that have the word `Program` in their name
 2. strips that word from those column names _(a rename)_, and then
 3. shoves them all to the beginning of the spreadsheet ahead of "the rest" of the columns _("the rest" being something it also computed dynamically)_

Code:

```python
import pandas
pandas.set_option('expand_frame_repr', False)

df = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/tallypivotoutput.csv', dtype=object)

print('---At first, "df" looks like this:---')
print(df)

columnsWithProgramInTheName = [x for x in df.columns if 'Program' in x]
theRestOfTheColumns = [x for x in df.columns if x not in columnsWithProgramInTheName]

newColumnOrder = columnsWithProgramInTheName + theRestOfTheColumns
df = df[newColumnOrder]

renamingMap = {x:x.replace('Program','') for x in columnsWithProgramInTheName}
df = df.rename(columns=renamingMap)

print()
print('---After reordering and renaming dynamically, "df" looks like this:---')
print(df)
```

Output:

```
---At first, "df" looks like this:---
    Id First Name Last Name ProgramAcrobatics ProgramBasketWeaving ProgramComputerProgramming ProgramScubaDiving
0   29       John       Doe               NaN           Registered                        NaN         Registered
1  872       Jane      Dill        Registered                  NaN                        NaN         Registered
2   75       Mick       Jag               NaN                  NaN                 Registered         Registered

---After reordering and renaming dynamically, "df" looks like this:---
   Acrobatics BasketWeaving Computerming ScubaDiving   Id First Name Last Name
0         NaN    Registered          NaN  Registered   29       John       Doe
1  Registered           NaN          NaN  Registered  872       Jane      Dill
2         NaN           NaN   Registered  Registered   75       Mick       Jag
```

---

<div id='ex4'/>

## Exercise 4:  Combine 5 spreadsheets into 1 CampaignMemberRecordsToInsert spreadsheet

Open the [https://link.stthomas.edu/sfpyeventmerge](https://link.stthomas.edu/sfpyeventmerge){:target="_blank"} "starter code" if you want to work alone without anybody typing over you, or [https://link.stthomas.edu/sfpy102collab](https://link.stthomas.edu/sfpy102collab){:target="_blank"} if you'd rather collaborative-code with others (or open both in separate tabs, but keep track of which is which).

Your data looks like this.

Event attendance spreadsheet #1 (`evdf1`):

```
     First        Last           Email                 Event Name  Event Date Attendance Status
0   Revkah     Lilburn  rl@example.com  Python for Salesforce 101  2018-10-20          Attended
1   Haskel   Southerns  hs@example.com  Python for Salesforce 101  2018-10-20           No-Show
2  Ermanno  Withinshaw  ew@example.com  Python for Salesforce 101  2018-10-20          Attended
```

Event attendance spreadsheet #2 (`evdf2`):

```
    First       Last           Email                              Event Name  Event Date Attendance Status
0  Haskel  Southerns  hs@example.com  Python for Salesforce 101-Office Hours  2018-11-10           No-Show
```

Event attendance spreadsheet #3 (`evdf3`):

```
      First       Last           Email                 Event Name  Event Date Attendance Status
0  Julianna     Judron  jj@example.com  Python for Salesforce 102  2019-01-26           No-Show
1    Haskel  Southerns  hs@example.com  Python for Salesforce 102  2019-01-26          Attended
2      Adah    Dimmock  ad@example.com  Python for Salesforce 102  2019-01-26         Cancelled
```

Salesforce Contact object existing record dump:

```
       ID FIRSTNAME  LASTNAME             EMAIL         PHONE
0  003X01      Anna  Appleton    aa@example.com  555-555-0101
1  003X02      Adah   Dimmock  dima@example.com  555-555-0202
2  003X03       Ben  Bensalem    bs@example.com  555-555-0303
3  003X04  Julianna    Judron    jj@example.com  555-555-0404
4  003X05  Julianna    Judron    jj@example.com  555-555-0505
5  003X06    Zainab     Zahar    zz@example.com  555-555-0606
```

Salesforce Campaign object existing record dump:

```
       ID                                    NAME HAPPENED_ON__C
0  701X01                     Parasailing Fun Day     2017-07-20
1  701X02               Python for Salesforce 101     2018-10-20
2  701X03  Python for Salesforce 101-Office Hours     2018-11-10
3  701X04                           Hockey Outing     2019-01-01
4  701X05               Python for Salesforce 102     2019-01-26
```


We're going to create a file called **CampaignMemberRecordsToInsert.csv** of people we can find in Salesforce already that looks like this:

| ContactId | CampaignId | CampaignMemberStatus | Last | First | Email | Event Name | Event Date |
| --- | --- | --- | --- | --- | --- | --- | --- |
|003X04|701X05|No-Show|Judron|Julianna|jj@example.com|Python for Salesforce 102|2019-01-26|

Wow!  Just Julianna?

* What about Adah?  _(Oh, his email address is different in Salesforce.)_
* And wait, why only the one record for Julianna?  Isn't she duplicated in Salesforce?  _(We'll handle that ... see below.  We're deciding to only mark 1 of her 2 duplicate Contact records as having been at the event, as a business practice.)_

Here are the steps we'll follow to get there:

1. Concatenate the 3 EventBrite sheets vertically ↕ and save it as “eventsdf”
2. Do an “inner” merge from “eventsdf” to “contactsdf” (“inner” implication:  drops any attendees not yet in Salesforce – we’ll get to them later) matching on the FIRSTNAME, LASTNAME, & EMAIL; save the result as “merge1df”.
3. Drop any “First+Last+Email” duplicates in “merge1df,” keeping only the 1st one found for a given combo.
4. Delete columns from “merge1df” so that only the columns of “eventsdf” and “Id” remain; ensure the change persists to “merge1df”.
5. Rename the “ID” column of “merge1df” to “ContactId”; ensure “merge1df” changes.
6. Merge “merge1df” against “campaignsdf” on event name & start date; “inner” merge; save the result as “merge2df”.
7. Rename the “ID” column of “merge2df” to “CampaignId”; ensure “merge2df” changes.
8. Rename the “Attendance Status” column of “merge2df” to “CampaignMemberStatus”; ensure “merge2df” changes.
9. Re-order the fields of “merge2df” to be:  ContactId, CampaignId, CampaignMemberStatus, Last, First, Email, Event Name, Event Date.  Don’t bother including “NAME” or “HAPPENED_ON__C” in your final output if they exist.
10. Export your data to “CampaignMemberRecordsToInsert.csv” and have a look.  Does it look like in the “cheat sheet?”

Whew!  That's a lot!

Whether you're coding in your own "solo" console or helping type into the "group" console, we'll solve this one out loud together.

---

<div id="concat"/>

## Cheat Sheet:  Concatenation Examples ↕

### Example 1:  List all unique e-mail addresses in a spreadsheet, whether they be under the "`Email`," "`WorkEmail__c`," or "`SchoolEmail__c`" columns.

```python
concat_series = pandas.concat([df['Email'], df['WorkEmail__c'], df['SchoolEmail__c']])
nonnullemails_series = concat_series.dropna()
uniquenonnullemails_ndarray = nonnullemails_series.unique()
pandas.Series(uniquenonnullemails_ndarray, name='Emails').to_csv('c:\\example\\uniqueemails.csv', index=False, header=True)
```

If we ran the above code after reading a spreadsheet into the "`df`" variable that looked like this:

|Name|Email|WorkEmail__c|SchoolEmail__c|
|---|---|---|---|
|Annie Appleton|aa@example.com|aa@work.com|aa@school.com|
|Andrew Appleton|aa@example.com|andrew@work.com|andrew@school.com|
|Berenice Benita|bb@example.com|bb@work.com|bb@school.com|

Then the file we saved to, uniqueemails.csv, looks like this when opened _(note that `aa@example.com` only appears once)_:

|Emails|
|---|
|aa@example.com|
|bb@example.com|
|aa@work.com|
|andrew@work.com|
|bb@work.com|
|aa@school.com|
|andrew@school.com|
|bb@school.com|

> Note that the "`.unique()`" operation, which you can append to any "Series"-typed data, produces output that is _not_ a Pandas Series _(whereas "`.dropna()`," for example, produces another Series as output)_.
> 
> It's yet _another_ list-like data structure called a `numpy.ndarray`.
> 
> To write back to disk as a 1-column CSV or Excel file, we'll want to turn it back into a Series, which is what we do on the last line _(giving the first column the name "Emails" because that feels like a good name)_, so we can take advantage of "`.to_csv(...)`."
> 
> If instead we had put `uniquenonnullemails_ndarray` inside `print(...)`, we would have seen the data surrounded by square brackets, separated by a space but no commas.  If we had wanted commas as a separator, we would have put it inside of `print(list(...))` to form `print(list(uniquenonnullemails_ndarray))`.


### Example 2:  List all unique e-mail addresses between 2 spreadsheets, whether they be under #1's "`Email`," "`WorkEmail__c`," or "`SchoolEmail__c`" columns, or under #2's "`EMAILADDR`," "`EMAIL2__C`," "`EMAIL3__C`," or "`EMAIL4__C`" columns.

```python
concat_series = pandas.concat([df1['Email'], df1['WorkEmail__c'], df1['SchoolEmail__c'], df2['EMAILADDR'], df2['EMAIL2__C'], df2['EMAIL3__C'], df2['EMAIL4__C']])
nonnullemails_series = concat_series.dropna()
uniquenonnullemails_ndarray = nonnullemails_series.unique()
pandas.Series(uniquenonnullemails_ndarray, name='Emails').to_csv('c:\\example\\uniqueemails2.csv', index=False, header=True)
```

> <b>** HEY LOOK! **</b>
> 
> It's the exact same code as example 1.  We just added more things to the list inside "`pandas.concat(...)`" in the first line!

If we ran the above code after reading a spreadsheet into the "`df1`" variable that looked like this...

|Name|Email|WorkEmail__c|SchoolEmail__c|
|---|---|---|---|
|Annie Appleton|aa@example.com|aa@work.com|aa@school.com|
|Andrew Appleton|aa@example.com|andrew@work.com|andrew@school.com|
|Berenice Benita|bb@example.com|bb@work.com|bb@school.com|

...and after reading a spreadsheet into the "`df2`" variable that looked like this:

|Name|EMAILADDR|EMAIL2__C|EMAIL3__C|EMAIL4__C|
|---|---|---|---|---|
|Berenice Benita|bb@example.com|bb@school.com|bb@play.com|bb@example.com|

Then the file we saved to, uniqueemails2.csv, looks like this when opened _(there was just 1 email address in the 2nd spreadsheet that we didn't yet know about)_:

|Emails|
|---|
|aa@example.com|
|bb@example.com|
|aa@work.com|
|andrew@work.com|
|bb@work.com|
|aa@school.com|
|andrew@school.com|
|bb@school.com|
|bb@play.com|

### Example 3:  Spreadsheet 1 has columns "`First`," "`Last`," & "`Email`."<br/>Spreadsheet 2 has columns "`LastName`," "`Em`," & "`FirstName`."<br/>Concatenate appropriately _(e.g. `Em` = `Email`)_ & dedupe _(by all 3 fields together)_.

```python
col2EquivInCol1 = {'FirstName':'First', 'LastName':'Last', 'Em':'Email'}
rawconcat_df = pandas.concat([df1, df2.rename(columns=col2EquivInCol1)], sort=False)
dedupedconcat_df = rawconcat_df.drop_duplicates(subset=df1.columns)
dedupedconcat_df.to_csv('c:\\example\\concatdedupedtables.csv', index=False)
```

> Note:  The "`sort=False`" option in "`pandas.concat(...)`" keeps that command from rearranging the columns in alphabetical order.

If we ran the above code after reading a spreadsheet into the "`df1`" variable that looked like this...

| First | Last | Email |
| --- | --- | --- |
| Jimmy | Buffet | jb@example.com |
| Shirley | Chisholm | sc@example.com |
| Marilyn | Monroe | mm@example.com |
| Cesar | Chavez | cc@example.com |
| Vandana | Shiva | vs@example.com |
| Andrea | Smith | as@example.com |
| Albert | Howard | ah@example.com |

...and after reading a spreadsheet into the "`df2`" variable that looked like this:

| LastName | Em | FirstName |
| --- | --- | --- |
| Temple | st@example.com | Shirley |
| Smith | as@example.com | Andrea |
| Duck | dd@example.com | Donald |
| Monroe | mm@example.com | Marilyn |
| Howard | ahotherem@example.com | Albert |
| Shiva | vs@example.com | Vandana |

Then the file we saved to, concatdedupedtables.csv, looks like this when opened:

| First | Last | Email |
| --- | --- | --- |
| Jimmy | Buffet | jb@example.com |
| Shirley | Chisholm | sc@example.com |
| Marilyn | Monroe | mm@example.com |
| Cesar | Chavez | cc@example.com |
| Vandana | Shiva | vs@example.com |
| Andrea | Smith | as@example.com |
| Albert | Howard | ah@example.com |
| Shirley | Temple | st@example.com |
| Donald | Duck | dd@example.com |
| Albert | Howard | ahotherem@example.com |

### Example 4:  Spreadsheet 1, Spreadsheet 2, & Spreadsheet 3 all have columns "`Name`," "`DOB`," & "`AttendedOrNot`" _(they're EventBrite exports)_.<br/>Add a "`WhichSheet`" column to each of them saying "Event1," "Event2," or "Event3," concatenate, and sort by "`Name`," "`DOB`," & "`WhichSheet`."

```python
rawconcat_df = pandas.concat([df1.assign(WhichSheet='Event1'), df2.assign(WhichSheet='Event2'), df3.assign(WhichSheet='Event3')], sort=False)
sortedconcat_df = rawconcat_df.sort_values(by=['Name','DOB','WhichSheet'])
sortedconcat_df.to_csv('c:\\example\\concatsortedtables.csv', index=False)
```

> Note:  The "`sort=False`" option in "`pandas.concat(...)`" keeps that command from rearranging the columns in alphabetical order.

If we ran the above code after reading a spreadsheet into the "`df1`" variable that looked like this...

Name|DOB|AttendedOrNot
---|---|---
Annie Appleton|1950-02-02|Yes
Berenice Benita|2000-01-01|No

...and after reading a spreadsheet into the "`df2`" variable that looked like this...

Name|DOB|AttendedOrNot
---|---|---
Annie Appleton|1950-02-02|No
Christina Cruz|1975-03-03|Yes

...and after reading a spreadsheet into the "`df3`" variable that looked like this:

Name|DOB|AttendedOrNot
---|---|---
Christina Cruz|1975-03-03|No

Then the file we saved to, concatsortedtables.csv, looks like this when opened:

Name|DOB|AttendedOrNot|WhichSheet
---|---|---|---
Annie Appleton|1950-02-02|Yes|Event1
Annie Appleton|1950-02-02|No|Event2
Berenice Benita|2000-01-01|No|Event1
Christina Cruz|1975-03-03|Yes|Event2
Christina Cruz|1975-03-03|No|Event3

---

<div id="merge"/>

## Cheat Sheet:  Merge Examples ↔

### Example 1:  Spreadsheet #1 is full of people.<br/>Spreadsheet #2 is full of data about countries of the world.<br/>Add "`Country Code`" & "`Country Capital`" columns to #1, using people's "`MailingCountry`" data as a matching key to #2's "`Name`" column.

```python
columnstokeep = list(df1.columns) + ['Code','Capital']
mergedf = df1.merge(df2, how='left', left_on=['MailingCountry'], right_on=['Name'])
mergedf = mergedf[columnstokeep]
mergedf = mergedf.rename(columns={'Code':'Country Code', 'Capital':'Country Capital'})
mergedf.to_csv('c:\\example\\countryenhanced.csv', index=False)
```

If we ran the above code after reading a spreadsheet into the "`df1`" variable that looked like this...

| Id | First | Last | MailingCountry |
| --- | --- | --- | --- |
| 30829 | Cesar | Chavez | United States |
| 827 | Vandana | Shiva | India |
| 9284 | Andrea | Smith | United States |
| 724 | Albert | Howard | United Kingdom |

...and after reading a spreadsheet into the "`df2`" variable that looked like this:

| Name | Code | Capital | SqKm |
| --- | --- | --- | --- |
| Argentina | AR | Buenos Aires | 2,780,400 |
| Barbados | BB | Bridgetown | 430 |
| Iceland | IC | Reykjavik | 103,000 |
| India | IN | New Delhi | 3,287,263 |
| Tunisia | TS | Tunis | 163,610 |
| United Kingdom | UK | London | 242,495 |
| United States | US | Washington, D.C. | 9,525,067 |
| Vanuatu | NH | Port Vila | 12,189 |

Then the file we saved to, countryenhanced.csv, looks like this when opened:

| Id | First | Last | MailingCountry | Country Code | Country Capital |
| --- | --- | --- | --- | --- | --- |
| 30829 | Cesar | Chavez | United States | US | Washington, D.C. |
| 827 | Vandana | Shiva | India | IN | New Delhi |
| 9284 | Andrea | Smith | United States | US | Washington, D.C. |
| 724 | Albert | Howard | United Kingdom | UK | London |

### Example 2:  Combine 2 spreadsheets full of people and things you know about them on "`First`," "`Last`," & "`Email`" as a matching key.

```python
col2EquivInCol1 = {'FirstName':'First', 'LastName':'Last', 'Em':'Email'}
mergedf = df1.merge(df2.rename(columns=col2EquivInCol1), how='outer', on=['First','Last','Email'], indicator=True)
mergedf.to_csv('c:\\example\\personmerge.csv', index=False)
```

If we ran the above code after reading a spreadsheet into the "`df1`" variable that looked like this...

Id|First|Last|Email|Company
---|---|---|---|---
5829|Jimmy|Buffet|jb@example.com|RCA
2894|Shirley|Chisholm|sc@example.com|United States Congress
294|Marilyn|Monroe|mm@example.com|Fox
30829|Cesar|Chavez|cc@example.com|United Farm Workers
827|Vandana|Shiva|vs@example.com|Navdanya
9284|Andrea|Smith|as@example.com|University of California
724|Albert|Howard|ah@example.com|Imperial College of Science

...and after reading a spreadsheet into the "`df2`" variable that looked like this:

PersonId|FirstName|LastName|Em|FavoriteFood
---|---|---|---|---
983mv|Shirley|Temple|st@example.com|Lollipops
9e84f|Andrea|Smith|as@example.com|Kale
k28fo|Donald|Duck|dd@example.com|Pancakes
x934|Marilyn|Monroe|mm@example.com|Carrots
8xi|Albert|Howard|ahotherem@example.com|Potatoes
02e|Vandana|Shiva|vs@example.com|Amaranth

Then the file we saved to, personmerge.csv, looks like this when opened:

Id|First|Last|Email|Company|PersonId|FavoriteFood|\_merge
---|---|---|---|---|---|---|---
5829|Jimmy|Buffet|jb@example.com|RCA|||left\_only
2894|Shirley|Chisholm|sc@example.com|United States Congress|||left\_only
294|Marilyn|Monroe|mm@example.com|Fox|x934|Carrots|both
30829|Cesar|Chavez|cc@example.com|United Farm Workers|||left\_only
827|Vandana|Shiva|vs@example.com|Navdanya|02e|Amaranth|both
9284|Andrea|Smith|as@example.com|University of California|9e84f|Kale|both
724|Albert|Howard|ah@example.com|Imperial College of Science|||left\_only
||Shirley|Temple|st@example.com||983mv|Lollipops|right\_only
||Donald|Duck|dd@example.com||k28fo|Pancakes|right\_only
||Albert|Howard|ahotherem@example.com||8xi|Potatoes|right\_only

Just to help drive home how this "horizontal" "merge" operation is different from a "vertical" "concat" operation, check out this code:

```python
col2EquivInCol1 = {'FirstName':'First', 'LastName':'Last', 'Em':'Email'}
concatdf = pandas.concat([df1,df2.rename(columns=col2EquivInCol1)], sort=False)
concatdf.to_csv('c:\\example\\personconcat.csv', index=False)
```

The output file we'd have saved to, personconcat.csv, would like this when opened:

Id|First|Last|Email|Company|PersonId|FavoriteFood
---|---|---|---|---|---|---
5829|Jimmy|Buffet|jb@example.com|RCA||
2894|Shirley|Chisholm|sc@example.com|United States Congress||
294|Marilyn|Monroe|mm@example.com|Fox||
30829|Cesar|Chavez|cc@example.com|United Farm Workers||
827|Vandana|Shiva|vs@example.com|Navdanya||
9284|Andrea|Smith|as@example.com|University of California||
724|Albert|Howard|ah@example.com|Imperial College of Science||
||Shirley|Temple|st@example.com||983mv|Lollipops
||Andrea|Smith|as@example.com||9e84f|Kale
||Donald|Duck|dd@example.com||k28fo|Pancakes
||Marilyn|Monroe|mm@example.com||x934|Carrots
||Albert|Howard|ahotherem@example.com||8xi|Potatoes
||Vandana|Shiva|vs@example.com||02e|Amaranth

As you can see, we did manage to "stack" the First, Last, & Email columns by renaming column names in `df2` before adding it to the list of sheets to vertically concatenate _(because `pandas.concat(...)` looks for column names that are exact matches of each other and just "adds on" columns not found in every spreadsheet passed do it)_.

However, we've lost any sense of connection between the fact that Marilyn Monroe works for Fox and the fact that Marilyn Monroe likes to eat carrots.

* We could alphabetize it for easier visual scanning _(`cdf = cdf.sort_values(by=['First','Last','Email'])`)_ ...
* We could facilitate visual scanning for duplicates on First+Last+Email by adding a helper column _(`cdf['isDupe'] = cdf.duplicated(subset=['First','Last','Email'], keep=False)`)_ ...
* We could even get "non-duplicates" out of our way by filtering on that column _(`cdf = cdf[cdf['isDupe']]`)_ ...

...but why?  A horizontal merge probably serves our "find out that Marilyn works for Fox and likes carrots" use case better.

There might be business processes where we actually want our output to be a "vertical concat," however.

* For example, perhaps we actually are just trying to look for duplicates by first/last/email, and data like `Company` and `FavoriteFood` are "extra" data we couldn't care less about.
  * We don't care if they show up, but we don't care if they don't.
  * We want to take advantage of vertical-concatenation's ability to process dozens of spreadsheets in one command. 

Point is, think about whether you would be copy-pasting vertically in Excel or whether you would be VLOOKUP-ing in Excel before you decide which is appropriate for you!

### Example 3:  Cross-check 2 financial transaction logs that should be identical, ensuring no Transaction ID exists in only one spreadsheet, nor has a different timestamp between the two spreadsheets.

```python
mergedf = df1.merge(df2, how='outer', left_on=['TransactionId'], right_on=['Id'], indicator=True)
mergedf['HasProblem'] = (mergedf['_merge'] != 'both') | (mergedf['Timestamp_x'] != mergedf['Timestamp_y'])
mergedf = mergedf[['HasProblem','TransactionId','_merge','Timestamp_x','Amount_x','Timestamp_y','Amount_y']]
mergedf.to_csv('c:\\example\\transactionverify.csv', index=False)
```

If we ran the above code after reading a spreadsheet into the "`df1`" variable that looked like this...

TransactionId|Amount|Timestamp|CCLast4
---|---|---|---
28499202|$87.71|2018-06-14T04:02:00-05:00|3885
17689183|$1,508.82|2014-11-13T18:27:00-05:00|9274
92840068|$1.08|2016-02-08T15:53:00-05:00|9274
92848928|$981.46|2019-01-03T07:01:00-05:00|1784

...and after reading a spreadsheet into the "`df2`" variable that looked like this:

Timestamp|BudgetCode|Amount|Id
---|---|---|---
2016-02-08T15:53:00-05:00|8294|$1.08|92840068
2014-12-01T08:23:00-05:00|7140|$1,508.82|17689183
2018-06-14T04:02:00-04:00|8294|$87.71|28499202
2013-02-09T08:01:00-05:00|8294|$517.84|82947820

Then the file we saved to, transactionverify.csv, looks like this when opened:

HasProblem|TransactionId|\_merge|Timestamp\_x|Amount\_x|Timestamp\_y|Amount\_y
---|---|---|---|---|---|---
True|28499202|both|2018-06-14T04:02:00-05:00|$87.71|2018-06-14T04:02:00-04:00|$87.71
True|17689183|both|2014-11-13T18:27:00-05:00|$1,508.82|2014-12-01T08:23:00-05:00|$1,508.82
False|92840068|both|2016-02-08T15:53:00-05:00|$1.08|2016-02-08T15:53:00-05:00|$1.08
True|92848928|left\_only|2019-01-03T07:01:00-05:00|$981.46||
True||right\_only|||2013-02-09T08:01:00-05:00|$517.84

> If we were working with millions of records, most of which would be false, we might want to filter out the rows where "`HasProblem`" is `False`.
> 
> We haven't gotten to this yet, but you could use an approach for filtering series by adding the following line of code right before `mergedf = mergedf[['HasProblem','TransactionId',...,'Amount_y']]`:
> 
> `mergedf = mergedf[mergedf['HasProblem']]`

If you look at our output data carefully, you might notice that transaction ID 28499202 is only problematic because of a time zone difference (UTC-5 vs. UTC-5).

June 14th, 2018 is in the summer, so this might be a simple problem of one of our systems logging Daylight Savings Time incorrectly.

* We could update our Python script to ignore this particular kind of issue by converting "`Timestamp`" in `df1` and `df2` to be interpreted as real dates, rather than as plaintext, before we check for equivalency between `Timestamp_x` and `Timestamp_y`.  That might be the right approach if:
  * One system logged "noon in New York" as "T12:00:00-05:00" _(winter)_ / "T12:00:00-04:00" _(summer)_
  * The other system logged "noon in New York" as "T17:00:00Z" _(winter)_ / "T16:00:00Z" _(summer)_, which means it's logging transactions when they happened in Greenwich Mean Time / UTC.

However, for this particular issue, that's not quite what we're seeing.  It's probably one of the systems producing the logs that is forgetting to account for Daylight Savings Time, so there's probably a bug we should ask to have fixed "upstream" of our logs.

---

<div id="doorprize-concat"/>

## Door Prize Script:  Event-Attendance-Concatenating Loop ↕

[Tweet me if you use this in real life](https://www.twitter.com/KatieKodes){:target="_blank"} – remember to hashtag #AwesomeAdmin & #YayUs !

To watch this run, visit [https://repl.it/@rplrpl/Door-Prize-Multi-Event-Concatenator](https://repl.it/@rplrpl/Door-Prize-Multi-Event-Concatenator){:target="_blank"}

I've saved 4 files inside of my codebase at Repl.it _(the 3 we saw earlier, plus a new one full of RSVPs for "Python 103")_.

**PLEASE BE CAREFUL** about the code you're writing when you run code against "every file in a folder."  You can overwrite so many files in a milisecond.

**Just like I say, "Don't write your output to the same file that you're reading your input from"**:

* **Don't write a loop that writes output files to the same filenames OR the same directory as you're reading your input from"**

Code:

```python
import os
import pandas

lookForCSVsInThisFolder = 'C:\\FolderWhereIPutAllTheFiles\\'

listOfDataFrames = []
for x in os.listdir(lookForCSVsInThisFolder):
  if x.endswith('.csv'):
    xdf = pandas.read_csv(x)
    xdf = xdf.assign(WhichCSV = x)
    listOfDataFrames.append(xdf)

concatdf = pandas.concat(listOfDataFrames)

concatdf = concatdf.sort_values(by=['First','Last','Email','WhichCSV'])

concatdf.to_csv('c:\\example\\loopconcat.csv', index=False)
```

> _(Note:  in the Repl.it, instead of setting "`lookForCSVsInThisFolder`" to `'C:\\FolderWhereIPutAllTheFiles\\'`, in the Repl.it, I set it to "`'.'`" because that means "the same folder I'm running my Python from" -- this is specific to Repl.it and isn't normally the way I want you to code.)_.

Note that if you don't need the "WhichCSV" column added, your code can be **much** shorter, bringing the creation of "`concatdf`" down to a single line thanks to "list comprehensions":

```python
import os
import pandas

lookForCSVsInThisFolder = 'C:\\FolderWhereIPutAllTheFiles\\'

concatdf = pandas.concat([pandas.read_csv(x) for x in os.listdir(lookForCSVsInThisFolder) if x.endswith('.csv')])

concatdf = concatdf.sort_values(by=['First','Last','Email','WhichCSV'])

concatdf.to_csv('c:\\example\\loopconcat-alternate.csv', index=False)
```

Then the file we saved to, loopconcat.csv, looks like this when opened:

First|Last|Email|Event Name|Event Date|Attendance Status|WhichCSV
---|---|---|---|---|---|---
Adah|Dimmock|ad@example.com|Python for Salesforce 102|2019-01-26|Cancelled|mergehandson_event3.csv
Adah|Dimmock|ad@example.com|Python for Salesforce 103|2019-12-29|RSVPed|mergehandson_event4.csv
Ermanno|Withinshaw|ew@example.com|Python for Salesforce 101|2018-10-20|Attended|mergehandson_event1.csv
Harwilll|Menhenitt|hm@example.com|Python for Salesforce 103|2019-12-29|RSVPed|mergehandson_event4.csv
Haskel|Southerns|hs@example.com|Python for Salesforce 101|2018-10-20|No-Show|mergehandson_event1.csv
Haskel|Southerns|hs@example.com|Python for Salesforce 101|2019-11-26|Attended|mergehandson_event3.csv
Haskel|Southerns|hs@example.com|Python for Salesforce 103|2019-12-29|RSVPed|mergehandson_event4.csv
Haskel|Southerns|hs@example.com|Python for Salesforce 101-Office Hours|2018-11-10|No-Show|mergehandson_event2.csv
Julianna|Judron|jj@example.com|Python for Salesforce 102|2019-01-26|No-Show|mergehandson_event3.csv
Revkah|Lilburn|rl@example.com|Python for Salesforce 101|2018-10-20|Attended|mergehandson_event1.csv
Revkah|Lilburn|rl@example.com|Python for Salesforce 103|2019-12-29|Cancelled|mergehandson_event4.csv
