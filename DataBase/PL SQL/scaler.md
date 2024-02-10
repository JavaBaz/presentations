### SUBSTR
 returns a string value. If length is a negative number

```sql
SELECT COLUMN_NAME, SUBSTR(COLUMN_NAME, start_position [, length ] )
FROM TABLE_NAME
```
> NOTE: it might return null values.

> NOTE: If length is a negative number, then the SUBSTR function will return a NULL value.

<br>

------

### LENGTH
returns the length of the specified string.

If string1 is NULL, then the LENGTH function will return NULL.

```sql
SELECT COLUMN_NAME, LENGTH(COLUMN_NAME)
FROM TABLE_NAME
```

<br>

------


### CONCAT 
allows you to concatenate two strings together.


```sql
SELECT CONCAT( string1, string2 )
FROM TABLE_NAME
```

<br>

------


### LOWER  
converts all letters in the specified string to lowercase. 

```sql
SELECT LOWER(COLUMN_NAME)
FROM TABLE_NAME
```
> NOTE: If there are characters in the string that are not letters, they are unaffected by this function.
<br>

------


### UPPER   
converts all letters in the specified string to uppercase. 
```sql
SELECT UPPER (COLUMN_NAME)
FROM TABLE_NAME
```
> NOTE: If there are characters in the string that are not letters, they are unaffected by this function.
<br>

------

### INSTR    
returns the location of a substring in a string.

```sql
SELECT INSTR( string, substring [, start_position [, th_appearance ] ] )
FROM TABLE_NAME
```
<br>

------

### LPAD    
pads the left-side of a string with a specific set of characters (when string1 is not null).

```sql
SELECT LPAD( string1, padded_length [, pad_string] )
FROM TABLE_NAME
```
> NOTE: If "pad_string" parameter is omitted, the LPAD function will pad spaces to the left-side of string1.
<br>

------

### RPAD    
pads the right-side of a string with a specific set of characters (when string1 is not null).

```sql
SELECT RPAD( string1, padded_length [, pad_string] )
FROM TABLE_NAME
```
> NOTE: If "pad_string" parameter is omitted, the RPAD function will pad spaces to the right-side of string1.
<br>

------

### TO_CHAR    
converts a number or date to a string.

```sql
SELECT TO_CHAR( value [, format_mask] [, nls_language] )
FROM TABLE_NAME
```
#### Example 
```
TO_CHAR(1210.73, '9999.9')
Result: ' 1210.7'

TO_CHAR(-1210.73, '9999.9')
Result: '-1210.7'

TO_CHAR(1210.73, '9,999.99')
Result: ' 1,210.73'

TO_CHAR(1210.73, '$9,999.00')
Result: ' $1,210.73'

TO_CHAR(21, '000099')
Result: ' 000021'
```

<br>

#### Example 

```
TO_CHAR(sysdate, 'yyyy/mm/dd')
Result: '2003/07/09'

TO_CHAR(sysdate, 'Month DD, YYYY')
Result: 'July 09, 2003'

TO_CHAR(sysdate, 'FMMonth DD, YYYY')
Result: 'July 9, 2003'

TO_CHAR(sysdate, 'MON DDth, YYYY')
Result: 'JUL 09TH, 2003'

TO_CHAR(sysdate, 'FMMON DDth, YYYY')
Result: 'JUL 9TH, 2003'

TO_CHAR(sysdate, 'FMMon ddth, YYYY')
Result: 'Jul 9th, 2003'
```

>NOTE: You will notice that in some TO_CHAR function examples, the format_mask parameter begins with "FM". This means that zeros and blanks are suppressed. This can be seen in the examples below.

#### Example 
```
TO_CHAR(sysdate, 'FMMonth DD, YYYY')
Result: 'July 9, 2003'

TO_CHAR(sysdate, 'FMMON DDth, YYYY')
Result: 'JUL 9TH, 2003'

TO_CHAR(sysdate, 'FMMon ddth, YYYY')
Result: 'Jul 9th, 2003'
```

------

### ROUND    
 returns a number rounded to a certain number of decimal places.

```sql
SELECT ROUND( number [, decimal_places] )
FROM TABLE_NAME
```
> NOTE: "decimal_places" parameter is Optional. It's the number of decimal places rounded to. This value must be an integer. If this parameter is omitted, the ROUND function will round the number to 0 decimal places.

<br>

#### Example 
```
ROUND(125.315)
Result: 125

ROUND(125.315, 0)
Result: 125

ROUND(125.315, 1)
Result: 125.3

ROUND(125.315, 2)
Result: 125.32

ROUND(125.315, 3)
Result: 125.315

ROUND(-125.315, 2)
Result: -125.32
```
------

### TRUNC     
returns a date truncated to a specific unit of measure.

```sql
SELECT TRUNC ( date [, format ] )
FROM TABLE_NAME
```
format :

| Unit                         | Valid format parameters |
| ----                         | ----------------------- | 
| Content Cell                 | Content Cell  |
| Year 	                       | SYYYY, YYYY, YEAR, SYEAR, YYY, YY, Y |
| ISO Year                     | IYYY, IY, I |
| Quarter                      | Q |
| Month      	               | MONTH, MON, MM, RM |
| Week 	                       | WW |
| IW       	                   | IW |
| W         	               | W |
| Day     	                   | DDD, DD, J |
| Start day of the week 	   | DAY, DY, D |
| Hour 	                       | HH, HH12, HH24 |
| Minute 	                   | MI |



<br>

#### Example 
```
TRUNC(TO_DATE('22-AUG-03'), 'YEAR')
Result: '01-JAN-03'

TRUNC(TO_DATE('22-AUG-03'), 'Q')
Result: '01-JUL-03'

TRUNC(TO_DATE('22-AUG-03'), 'MONTH')
Result: '01-AUG-03'

TRUNC(TO_DATE('22-AUG-03'), 'DDD')
Result: '22-AUG-03'

TRUNC(TO_DATE('22-AUG-03'), 'DAY')
Result: '17-AUG-03'
```

------


### SYSDATE     
returns the current system date and time on your local database.

```sql
SELECT SYSDATE
FROM DUAL
```
#### Example 
```sql 
SELECT TO_CHAR(SYSDATE, 'yyyy/mm/dd')
FROM DUAL
```

------