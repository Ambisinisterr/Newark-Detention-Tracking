# Newark-Detention-Tracking

##Goal
----
Create a Dashboard which can quickly collect and aggregate information from various existing google spreadsheets. Allow for settings to be assigned by users as certain variables will change over time based on market situations.

Collect the Following Data:
1) Brewery Schedules from January to December (Each is a unique Spreadsheet)
2) Collect each day from the monthly schedules (Each is it's own page)
3) Filter to only collect Line 65 and Line 85 Loads

Display the following:
1) Total detention for each day
2) Total detention for each week
3) Total detention for each month
3) Total Detention for the year
4) Breakdown of detention for Line 65 and Line 85 Loads
5) Display costs for all of the above metrics

Finishing Touches
1) Allow detention forfeited to be user defined
2) Allow cost per hour to be user defined
3) Highlight cells for easier reading

----
## Background

The terminal I work for at NFI mainly serviced the Anhueser Busch Newark Brewery and NFI runs the inbound loads as a feeder operation. In short this means NFI can only operate as long as the Newark Operation is up and running. If Newark's production is down and there is no empty equipment to take out of Newark then the NFI Drivers will be detained at Newark until Newark is able to resume operations or until they run out of DOT Service Hours.

Keeping track of how much detention is being accrued allows us to guage how quickly we are reacting to changes in Newark's production and will help the terminal gauging the costs incurred for slow responses.

----

##Final Product
----

[INSERT IMAGE HERE]

##Logic
----

### Importing Every Month
In order to import every month I used a combination of excel formulas and SQL.

Code for January:
```
=IFERROR(QUERY(
{IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B6,"M/D")&"!A1:M"),"SELECT '"&TEXT(B6,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B7,"M/D")&"!A1:M"),"SELECT '"&TEXT(B7,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B8,"M/D")&"!A1:M"),"SELECT '"&TEXT(B8,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B9,"M/D")&"!A1:M"),"SELECT '"&TEXT(B9,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B10,"M/D")&"!A1:M"),"SELECT '"&TEXT(B10,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B11,"M/D")&"!A1:M"),"SELECT '"&TEXT(B11,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B12,"M/D")&"!A1:M"),"SELECT '"&TEXT(B12,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B13,"M/D")&"!A1:M"),"SELECT '"&TEXT(B13,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B14,"M/D")&"!A1:M"),"SELECT '"&TEXT(B14,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B15,"M/D")&"!A1:M"),"SELECT '"&TEXT(B15,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B16,"M/D")&"!A1:M"),"SELECT '"&TEXT(B16,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B17,"M/D")&"!A1:M"),"SELECT '"&TEXT(B17,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B18,"M/D")&"!A1:M"),"SELECT '"&TEXT(B18,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B19,"M/D")&"!A1:M"),"SELECT '"&TEXT(B19,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B20,"M/D")&"!A1:M"),"SELECT '"&TEXT(B20,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B21,"M/D")&"!A1:M"),"SELECT '"&TEXT(B21,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B22,"M/D")&"!A1:M"),"SELECT '"&TEXT(B22,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B23,"M/D")&"!A1:M"),"SELECT '"&TEXT(B23,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B24,"M/D")&"!A1:M"),"SELECT '"&TEXT(B24,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B25,"M/D")&"!A1:M"),"SELECT '"&TEXT(B25,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B26,"M/D")&"!A1:M"),"SELECT '"&TEXT(B26,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B27,"M/D")&"!A1:M"),"SELECT '"&TEXT(B27,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B28,"M/D")&"!A1:M"),"SELECT '"&TEXT(B28,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B29,"M/D")&"!A1:M"),"SELECT '"&TEXT(B29,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B30,"M/D")&"!A1:M"),"SELECT '"&TEXT(B30,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B31,"M/D")&"!A1:M"),"SELECT '"&TEXT(B31,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B32,"M/D")&"!A1:M"),"SELECT '"&TEXT(B32,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B33,"M/D")&"!A1:M"),"SELECT '"&TEXT(B33,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B34,"M/D")&"!A1:M"),"SELECT '"&TEXT(B34,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B35,"M/D")&"!A1:M"),"SELECT '"&TEXT(B35,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""});
IFERROR(QUERY(IMPORTRANGE(C3,TEXT(B36,"M/D")&"!A1:M"),"SELECT '"&TEXT(B36,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0),{"","","","","",""})
},"SELECT * WHERE Col1 IS NOT NULL",0),"No Results")
```

Breakdown

The above is not pretty so let's walk though the logic.

Wrapper Query
```
IFERROR(QUERY(...,"SELECT * WHERE Col2 IS NOT NULL",0),"No Results")
```
This is a query which will combine every day of the month. If there is no results for that month return "No Results." Otherwise it will return all results where there is a Driver ID in the sheet.

Array of Dates
```
{IFERROR(QUERY( ... ),{"","","","","",""})}
```
Everything between the two brackets is an array of 31 queries which is one for each date. If the date does not exist or there is no information in the date it will return 6 empty cells to ensure compatibility with the remaining queries.

SQL Query and Import Range
```
QUERY(IMPORTRANGE(C3,TEXT(B6,"M/D")&"!A1:M"),"SELECT '"&TEXT(B6,"MM/DD")&"',Col1,Col7,Col9,Col11,Col12 WHERE Col11 IS NOT NULL AND (Col9 LIKE '%85' OR Col9 LIKE '%65')",0)
```
1) Import a range from a URL in C3.
2) Sheet is the text from B6 (a date) formated to be M/D. Cells A1:M
3) Query: 
a) Create Date Column which is B6
b) Get Driver ID, Order Numer, Product/Line Number, Arrival Time, Departure Time from specified sheet

Final Results look like this:
|------|-----------|-------------|---------------------|--------------|----------------|
| Date | Driver ID | Order Numer | Product/Line Number | Arrival Time | Departure Time |
|08/01 | PORAN 2   | 836527      | BHL 85              | 22:53        | 23:03          |

Difference in time
```
=ARRAYFORMULA(IF(D6:D="","",IF((I6:I-H6:H)-TIME(0,Detention!N19,0)<0,0,(I6:I-H6:H)-TIME(0,Detention!N19,0))))
```
A difference row was added to subtract the Arrival Time from the Departure Time along with a forfeited time set by the user in the Detention sheet.
In short this says for every cell in the column, if there is no date in the row, leave blank. If the Departure minus Arrival minus Forfeited Time is less than 0, return 0. Otherwise return the difference.

Final Output of the Month

[INSERT IMAGE HERE]


