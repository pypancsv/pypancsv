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

_("101" recording [here](https://pypancsv.github.io/pypancsv/HandsOn201810/){:target="_blank"})_

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
5. [Exercise 5:  Make "ContactsToInsert" and "CampaignMembersToInsert" for those not in Salesforce](#ex5)
6. [Exercise 6:  Add a new "Note" column to our concatenated events roster](#ex6)
7. [Door Prize Script:  A little pivot](#pivot)
8. [DON'T PEEK!  Possible answers to exercises 3-6](#answers)

---

# Instructions & Code Snippets You Will Need

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
|003X05|701X05|No-Show|Judron|Julianna|jj@example.com|Python for Salesforce 102|2019-01-26|

Wow!  Just Julianna?

* What about Adah?  _(Oh, his email address is different in Salesforce.)_
* Note that we're going to create CampaignMember records on _both_ Julianas in Salesforce.  Maybe we have a tiny data set and we catch this.  Maybe we have a huge data set and we don't, and we catch it later when deduplicating Contacts.  For now, we'll go with the latter.  Deciding how to deal with this issue is more of a business logic problem than a programming problem.

Here are the steps we'll follow to get there:

1. Concatenate the 3 EventBrite sheets vertically ↕ and save it as “eventsdf”
2. Do an “inner” merge from “eventsdf” to “contactsdf” (“inner” implication:  drops any attendees not yet in Salesforce – we’ll get to them later) matching on the FIRSTNAME, LASTNAME, & EMAIL; save the result as “merge1df”.
3. Delete columns from “merge1df” so that only the columns of “eventsdf” and the “ID” column remain; ensure the change persists to “merge1df”.
4. Rename the “ID” column of “merge1df” to “ContactId”; ensure “merge1df” changes.
5. Merge “merge1df” against “campaignsdf” on event name & start date; “inner” merge; save the result as “merge2df”.
6. Rename the “ID” column of “merge2df” to “CampaignId”; ensure “merge2df” changes.
7. Rename the “Attendance Status” column of “merge2df” to “CampaignMemberStatus”; ensure “merge2df” changes.
8. Re-order the fields of “merge2df” to be:  ContactId, CampaignId, CampaignMemberStatus, Last, First, Email, Event Name, Event Date.  Don’t bother including “NAME” or “HAPPENED_ON__C” in your final output if they exist.
9. Export your data to “CampaignMemberRecordsToInsert.csv” and have a look.  Does it look like it should?

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

---

<div id='ex5'/>

## Exercise 5:  Make "ContactsToInsert" and "CampaignMembersToInsert" for those not in Salesforce

If you accidentally closed your work, open the [https://link.stthomas.edu/sfpyeventmerge2](https://link.stthomas.edu/sfpyeventmerge2){:target="_blank"} "starter code" if you want to work alone without anybody typing over you, or [https://link.stthomas.edu/sfpy102collab](https://link.stthomas.edu/sfpy102collab){:target="_blank"} if you'd rather collaborative-code with others (or open both in separate tabs, but keep track of which is which).

You're going to pick up with `eventsdf` already existing _(that was the first concatenation you did in the previous exercise)_, and you'll be shooting to create a file called **CampaignMemberRecordsToInsert2.csv** that looks like this:

ContactId|CampaignId|CampaignMemberStatus|Last|First|Email|Event Name|Event Date
---|---|---|---|---|---|---|---
003X61|701X02|Attended|Lilburn|Revkah|rl@example.com|Python for Salesforce 101|2018-10-20
003X62|701X02|No-Show|Southerns|Haskel|hs@example.com|Python for Salesforce 101|2018-10-20
003X63|701X02|Attended|Withinshaw|Ermanno|ew@example.com|Python for Salesforce 101|2018-10-20
003X64|701X03|No-Show|Southerns|Haskel|hs@example.com|Python for Salesforce 101-Office Hours|2018-11-10
003X65|701X05|Attended|Southerns|Haskel|hs@example.com|Python for Salesforce 102|2019-01-26
003X66|701X05|Cancelled|Dimmock|Adah|ad@example.com|Python for Salesforce 102|2019-01-26

The ContactIds come from a command we're going to do that I wrote to imitate exporting a DataFrame called "`merge3df`" to a file called "`ContactsToInsert.csv`," pushing that file into Salesforce Data Loader as a Contact insertion operation, getting the "success" file back, and re-loading that "success" file back into Python as the new value of "`merge3df`" _(with `merge3df = pandas.read_csv('successBlahBlah.csv')`)_.

Here are the steps we'll follow to get this file:

1. Do a “left” merge from “eventsdf” to “contactsdf” matching on the FIRSTNAME, LASTNAME, & EMAIL; turn on the “indicator=True” flag; save the result as “merge3df”.
2. Remove from “merge3df” any rows where the value in the “_merge” column is not “left_only”; ensure change persists.  (We do this by building an expression that becomes a “Series” of True/False values with the same “Item Ids” that “merge3df” has as “row IDs,” then putting that expression inside “merge3df = merge3df[…]”)
3. Run the following command:  `merge3df = doFakeDataLoad(merge3df)`
4. Delete columns from “merge3df” so that only the columns of “eventsdf” and “ID” remain; ensure the change persists to “merge3df”.  _(Note:  from here on out, we’ve done this before, just merge1->merge3 & merge2->merge4.)_
5. Rename the “ID” column of “merge3df” to “ContactId”; ensure “merge3df” changes.
6. Merge “merge3df” against “campaignsdf” on event name & start date; “inner” merge; save the result as “merge4df”.
7. Rename the “ID” column of “merge4df” to “CampaignId”; ensure “merge4df” changes.
8. Rename the “Attendance Status” column of “merge4df” to “CampaignMemberStatus”; ensure “merge4df” changes.
9. Re-order the fields of “merge4df” to be:  ContactId, CampaignId, CampaignMemberStatus, Last, First, Email, Event Name, Event Date.  Don’t bother including “NAME” or “HAPPENED_ON__C” in your final output if they exist.
10. Export your data to “CampaignMemberRecordsToInsert2.csv” & have a look.  Does it look like it should?

Again, whether you're coding in your own "solo" console or helping type into the "group" console, we'll solve this one out loud together.  The only hard part is really steps 1-3; we can just copy/paste the rest of the code and change "merge1df" to "merge3df" and "merge2df" to "merge4df" and "....csv" to "...2.csv"

---

<div id='ex6'/>

## Exercise 6:  Add a new "Note" column to our concatenated events roster

If you accidentally closed your work, open the [https://link.stthomas.edu/sfpyeventnotes](https://link.stthomas.edu/sfpyeventnotes){:target="_blank"} "starter code" if you want to work alone without anybody typing over you, or [https://link.stthomas.edu/sfpy102collab](https://link.stthomas.edu/sfpy102collab){:target="_blank"} if you'd rather collaborative-code with others (or open both in separate tabs, but keep track of which is which).

You'll COPY the contents of "`eventsdf`" into a new DataFrame called "`notesdf`."  You'll edit "Event Name" in `notesdf` to make it a little easier to skim, and then you'll add a new "`Note`" column to `notesdf` and selectively fill it in so that your output data looks like this:

First|Last|Event Name|Event Date|Note
---|---|---|---|---
Revkah|Lilburn|PySF101|2018-10-20|
Haskel|Southerns|PySF101|2018-10-20|Flag A:  2018-10-20
Ermanno|Withinshaw|PySF101|2018-10-20|
Haskel|Southerns|PySF101-Office Hours|2018-11-10|Flag B:  HASKEL
Julianna|Judron|PySF102|2019-01-26|Flag B:  JULIANNA
Haskel|Southerns|PySF102|2019-01-26|Flag B:  HASKEL
Adah|Dimmock|PySF102|2019-01-26|Flag B:  ADAH

Here are the steps we'll follow to get this file:

1. Make a clean copy of `eventsdf` into a new DataFrame called `notesdf` _(note:  you can't just say `notesdf = eventsdf` ... you have to say `notesdf = eventsdf.copy()`, lest you simultaneously edit the contents of the original `eventsdf`)_.
2. Overwrite the contents of the “Event Name” column of `notesdf` to replace “`'Python for Salesforce '`” with “`'PySF'`” for better skimmability.  _(Note:  all text-filled “Series” have a `.str.replace(thingToReplace, replaceItWith)` operation.)_
3. Get rid of the “Email” & “Attendance Status” columns.  They’re just wasting screen space right now.
4. Add a new blank column called “Note” to notesdf (add a new column & fill it all the way down as the value None).
5. Selectively edit the value of Note to say “Flag A:  ” along with the Event Date from that row **if** the person’s last name starts with a capital S.
6. Selectively edit the value of Note to say “Flag B:  ” along with an upper-cased version of the person’s first name **if** they’re on the roster for an event in November 2018 or later.
7. print(...) or .to_csv(...) your data & have a look.  Does it look like it should?

Note that two of Haskel Southerns' 3 notes are "flag B," even though he's eligible for "flag A," having a last name that begins with "S."  **Why do you think that is?**

Again, whether you're coding in your own "solo" console or helping type into the "group" console, we'll solve this one out loud together.  We'll piece things together a little bit at a time, and using "placeholders" for data you intend to build later _(like "`'Hi There'`" as a stand-in for the "Flag A + date" data)_ when you're not sure what a command would be is a great idea, while you test that you got a different part of the code right, just like you would do when building a complicated Excel formula!


First|Last|Email|Event Name|Event Date|Attendance Status
---|---|---|---|---|---
Revkah|Lilburn|rl@example.com|Python for Salesforce 101|2018-10-20|Attended
Haskel|Southerns|hs@example.com|Python for Salesforce 101|2018-10-20|No-Show
Ermanno|Withinshaw|ew@example.com|Python for Salesforce 101|2018-10-20|Attended
Haskel|Southerns|hs@example.com|Python for Salesforce 101-Office Hours|2018-11-10|No-Show
Julianna|Judron|jj@example.com|Python for Salesforce 102|2019-01-26|No-Show
Haskel|Southerns|hs@example.com|Python for Salesforce 102|2019-01-26|Attended
Adah|Dimmock|ad@example.com|Python for Salesforce 102|2019-01-26|Cancelled

---

<div id='pivot'/>

## Door Prize Script:  A little pivot

Here's one more script for you to take home.

I've always been a bit "meh" about statistics and pivottables.

I suppose I lean towards programming, rather than data analysis, because my heart lies with beating a computer into giving "question-askers" the answers they seek ... not coming up with all the great questions.

But many of you are probably the question-askers in your organizations!  So it IS important to be able to summarize data!

And honestly, one thing I love, as a Salesforce admin, about doing pivot tables and aggregations with Python, is incorporating them into scripts I'm writing to automate repetitive, boring work.  Sometimes in Excel I DO make a PivotTable just to copy it back into a new tab without any formatting, tweak it a bit, and keep on editing as if it had always been an ordinary data table.  I definitely do that, too, in Python.

However, the commands and approaches quickly get varied even faster than all that nonsense about a million different meanings to `df[...]`.

If you want to become a pivot table expert for business analytics, you have to check out the blog [Practical Business Python](http://pbpython.com){:target="_blank"}.  I recommend going through the archives and poking around 2014 and early 2015 _(like all blogs, it can get more complicated over time as the author has "covered the easy stuff")_.

But let's do one simple example!

Starting with our trusty concatenated event roster, `eventsdf` ...

First|Last|Email|Event Name|Event Date|Attendance Status
---|---|---|---|---|---
Revkah|Lilburn|rl@example.com|Python for Salesforce 101|2018-10-20|Attended
Haskel|Southerns|hs@example.com|Python for Salesforce 101|2018-10-20|No-Show
Ermanno|Withinshaw|ew@example.com|Python for Salesforce 101|2018-10-20|Attended
Haskel|Southerns|hs@example.com|Python for Salesforce 101-Office Hours|2018-11-10|No-Show
Julianna|Judron|jj@example.com|Python for Salesforce 102|2019-01-26|No-Show
Haskel|Southerns|hs@example.com|Python for Salesforce 102|2019-01-26|Attended
Adah|Dimmock|ad@example.com|Python for Salesforce 102|2019-01-26|Cancelled

...we'll pivot people into a single line _(treating a name+email as a "person")_ apiece and display a bit of attendance information to the right of their name.

With this code:

```python
import numpy
import pandas
evdf1 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_event1.csv')
evdf2 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_event2.csv')
evdf3 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_event3.csv')
eventsdf = pandas.concat([evdf1, evdf2, evdf3])

pivotdf = pandas.pivot_table(eventsdf, index=['First','Last','Email'], columns='Event Date', values='Attendance Status', aggfunc=numpy.min)
pivotdf = pivotdf.reset_index()
pivotdf.columns.name = None
eventDatesOffered = list(eventsdf['Event Date'].unique())
pivotdf['RSVPed'] = pivotdf[eventDatesOffered].count(axis='columns')
pivotdf['Came'] = pivotdf[eventDatesOffered].isin(['Attended']).sum(axis='columns')
pivotdf['Didnt'] = pivotdf[eventDatesOffered].isin(['No-Show','Cancelled']).sum(axis='columns')
pivotdf.to_csv('outputpivot.csv', index=False)
```

We'll end up with a CSV file as output that looks like this:

First|Last|Email|2018-10-20|2018-11-10|2019-01-26|RSVPed|Came|Didnt
---|---|---|---|---|---|---|---|---
Adah|Dimmock|ad@example.com|||Cancelled|1|0|1
Ermanno|Withinshaw|ew@example.com|Attended|||1|1|0
Haskel|Southerns|hs@example.com|No-Show|No-Show|Attended|3|1|2
Julianna|Judron|jj@example.com|||No-Show|1|0|1
Revkah|Lilburn|rl@example.com|Attended|||1|1|0

We often need to import a 2nd "module" _(extension to Python commands)_ called "numpy" when doing pivots, so that we can refer to certain ... well ... pieces of that "module" that pivots work better with.

When we call the `pandas.pivot_table(...)` command, we specify that we want to process `eventsdf`, that we want the "which data to use as a "single row" to be first+last+email, that we want to set up as many new columns to the right of that as there are unique values in `eventsdf`'s "`Event Date`" column, and that at the intersection of a given person and a given date, we want to put the "minimum" _(earliest-in-the-alphabet)_ value found among all rows of `eventsdf` that had that person and that event date.

_(In our `eventsdf` data, we never have more than 1 RSVP per person.  Picking a "minimum" function or a "maximum" function on such data is always a neat trick when you're forced to "aggregate" your data down to a single value, and yet you know it already is a single value.)_

If we were to `print(...)` the output of that command, it'd look pretty hideous, so to get things back to looking like a normal table (this is the part that's like copy-pasting from a PivotTable into a new blank tab and stripping formatting and doing a little tweaking), we run these two commands back-to-back:  `pivotdf = pivotdf.reset_index()` to get the row and column headers back where they belong, and `pivotdf.columns.name = None` to get a weird "`Event Date`" out of the upper-left-hand corner of the table.

Next we're going to take advantage of the fact that we had _just_ taken all unique values found in `eventsdf`'s "`Event Date`" column and turned them into columns of `pivotdf`.

First, we'll manually scan `eventsdf['EventDate']` for its unique values, and we store them into a variable as a list.  We could type them, because there are only 3, but what if this were a much bigger table?  Best to let the computer do it.

Now ... what do you get if you say `someDataFrame[someListOfColumnNames]`?

You get a "sub-table" copy of that DataFrame for those columns that is, in and of itself, also a DataFrame!

That's what the next few lines do in the parts to the right of the `=` that say `pivotdf[eventDatesOffered]`.

* Tacked onto the end of "DataFrame"-typed data, `.count(axis='columns')` produces a "Series", whose item IDs correspond to the DataFrame's row IDs, indicating how many non-null values appear in that row of the DataFrame.
* Tacked onto the end of "DataFrame"-typed data, .isin(['No-Show','Cancelled']) produces a copy of that DataFrame, only with all the cell values replaced by whether that value is among "No Show"/"Cancelled."<br/>In turn, tacked onto the end of "DataFrame"-typed data that's full of numeric values, `.sum(axis='columns')` produces a "Series", whose item IDs correspond to the DataFrame's row IDs, indicating the sum of the values in that row of the DataFrame (and remember, True = 1; False = 0 ... power of 1!).
* And of course, putting such "Series"-typed expressions to the right of `pivotdf['NewColumnName'] = ` adds a new column and fills the values down as indicated.
* Notice that this whole operation didn't actually really have anything to do with "pivoting."  This was normal "table-editing" stuff.  We turned our "pivot" back into a "normal table" a long time ago with `pivotdf = pivotdf.reset_index()`.  This is the kind of "normal" stuff that you might do in Excel _after_ you've copied & pasted your PivotTable back into a "normal worksheet."

Finally, we write our table out to CSV.

## And that's a wrap for class -- thanks for coming!

---

<div id='answers'/>

## Don't peek!  Possible answers for exercises 3, 4, 5, & 6

### 3

```python
import pandas
pandas.set_option('expand_frame_repr', False)

df1 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/sample1.csv', dtype=object)

df1['Hello'] = 'Yay Us'
df1 = df1.rename(columns={'Last':'Last Name','First':'First Name'})
df1 = df1.drop(columns=['Email'])
df1 = df1[['Hello', 'Last Name', 'Company', 'First Name', 'Id']]
print(df1)
```

### 4 - 6

```python
import pandas
pandas.set_option('expand_frame_repr', False)

evdf1 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_event1.csv')
evdf2 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_event2.csv')
evdf3 = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_event3.csv')
contactsdf = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_sf_contacts.csv')
campaignsdf = pandas.read_csv('https://raw.githubusercontent.com/pypancsv/pypancsv/master/docs/_data/mergehandson_sf_campaigns.csv')

def doFakeDataLoad(dfToFakeInserting):
    idNos = range(61, 61+len(dfToFakeInserting))
    dfToFakeInserting['ID'] = ['003X'+str(x) for x in idNos]
    dfToFakeInserting['STATUS'] = 'Item Created'
    dfToFakeInserting = dfToFakeInserting[['ID'] + [x for x in dfToFakeInserting if x not in ['ID','STATUS']] + ['STATUS']]
    return dfToFakeInserting

# ######## EXERCISE 4 #########
eventsdf = pandas.concat([evdf1, evdf2, evdf3])
merge1df = eventsdf.merge(contactsdf, how='inner', left_on=['First','Last','Email'], right_on=['FIRSTNAME','LASTNAME','EMAIL'])
merge1df = merge1df[list(eventsdf.columns) + ['ID']]
merge1df = merge1df.rename(columns={'ID':'ContactId'})
merge2df = merge1df.merge(campaignsdf, how='inner', left_on=['Event Name','Event Date'], right_on=['NAME','HAPPENED_ON__C'])
merge2df = merge2df.rename(columns={'ID':'CampaignId','Attendance Status':'CampaignMemberStatus'})
merge2df = merge2df[['ContactId', 'CampaignId', 'CampaignMemberStatus', 'Last', 'First', 'Email', 'Event Name', 'Event Date']]
print(merge2df)

# ######## EXERCISE 5 #########
merge3df = eventsdf.merge(contactsdf, how='left', left_on=['First','Last','Email'], right_on=['FIRSTNAME','LASTNAME','EMAIL'], indicator=True)
notInSFSeries = merge3df['_merge']=='left_only'
merge3df = merge3df[notInSFSeries]
merge3df = doFakeDataLoad(merge3df)
merge3df = merge3df[list(eventsdf.columns) + ['ID']]
merge3df = merge3df.rename(columns={'ID':'ContactId'})
merge4df = merge3df.merge(campaignsdf, how='inner', left_on=['Event Name','Event Date'], right_on=['NAME','HAPPENED_ON__C'])
merge4df = merge4df.rename(columns={'ID':'CampaignId','Attendance Status':'CampaignMemberStatus'})
merge4df = merge4df[['ContactId', 'CampaignId', 'CampaignMemberStatus', 'Last', 'First', 'Email', 'Event Name', 'Event Date']]
print(merge4df)

# ######## EXERCISE 6 #########
notesdf = eventsdf.copy()
notesdf['Event Name'] = notesdf['Event Name'].str.replace('Python for Salesforce ','PySF')
notesdf = notesdf.drop(columns=['Email','Attendance Status'])
notesdf['Note'] = None
conditionAseries = notesdf['Last'].str.startswith('S')
notesdf['Note'][conditionAseries] = 'Flag A:  ' + notesdf['Event Date']
conditionBseries = notesdf['Event Date'] > '2018-10-31'
notesdf['Note'][conditionBseries] = 'Flag B:  ' + notesdf['First'].str.upper()
print(notesdf)
```
