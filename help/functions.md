# Function Reference {: data-toc-label='' }

Grist formulas support most Excel functions, as well as the Python programming language.

The table below lists Grist-specific functions, and the suite of the included Excel-like functions.
In addition, the entire [Python standard library](https://docs.python.org/3.9/library/) is
available. For more about using formulas in Grist, see [Intro to Formulas](formulas.md).

[Grist uses Python (version 3.9)](python.md) for formulas. You can use nearly all features of
Python (see [Python documentation](https://docs.python.org/3.9/)). Here are some helpful notes:

- Python is case-sensitive, including for Grist table and column names. Excel-like functions are
  always in uppercase. E.g. [**if**](https://docs.python.org/3/tutorial/controlflow.html#if-statements)
  is a Python keyword, while [**IF**](#if) is an Excel-like function.
- Compare for equality using `==`, in place of Excel's single `=` (which in Python means assignment).
  "Not equal" uses `!=` in place of Excel's `<>`.
- You may write multi-line Python in formulas (use <code class="keys">*Shift* + *Enter*</code> to
  add lines), including statements, variables, imports, etc.
- Grist code runs in a secure sandbox, with no access to anything outside your document.

<!-- BEGIN mkpydocs table -->
| Category | Functions |
| --- | --- |
| Grist | <a  href="#record">Record</a> or <a  href="#record"> rec</a>, <a  href="#_field">$Field</a> or <a  href="#_field"> rec.Field</a>, <a  href="#_group">$group</a> or <a  href="#_group"> rec.group</a>, <a  href="#recordset">RecordSet</a>, <a  href="#usertable">UserTable</a>, <a  href="#all">all</a>, <a  href="#lookupone">lookupOne</a>, <a  href="#lookuprecords">lookupRecords</a> |
| Date | <a  href="#date">DATE</a>, <a  href="#dateadd">DATEADD</a>, <a  href="#datedif">DATEDIF</a>, <a  href="#datevalue">DATEVALUE</a>, <a  href="#date_to_xl">DATE_TO_XL</a>, <a  href="#day">DAY</a>, <a  href="#days">DAYS</a>, <a  href="#dtime">DTIME</a>, <a  href="#edate">EDATE</a>, <a  href="#eomonth">EOMONTH</a>, <a  href="#hour">HOUR</a>, <a  href="#isoweeknum">ISOWEEKNUM</a>, <a  href="#minute">MINUTE</a>, <a  href="#month">MONTH</a>, <a  href="#now">NOW</a>, <a  href="#second">SECOND</a>, <a  href="#today">TODAY</a>, <a  href="#weekday">WEEKDAY</a>, <a  href="#weeknum">WEEKNUM</a>, <a  href="#xl_to_date">XL_TO_DATE</a>, <a  href="#year">YEAR</a>, <a  href="#yearfrac">YEARFRAC</a> |
| Info | <a class="unimplemented" href="#cell">CELL</a>, <a  href="#current_conversion">CURRENT_CONVERSION</a>, <a class="unimplemented" href="#isblank">ISBLANK</a>, <a  href="#isemail">ISEMAIL</a>, <a  href="#iserr">ISERR</a>, <a  href="#iserror">ISERROR</a>, <a  href="#islogical">ISLOGICAL</a>, <a  href="#isna">ISNA</a>, <a  href="#isnontext">ISNONTEXT</a>, <a  href="#isnumber">ISNUMBER</a>, <a  href="#isref">ISREF</a>, <a  href="#isreflist">ISREFLIST</a>, <a  href="#istext">ISTEXT</a>, <a  href="#isurl">ISURL</a>, <a  href="#n">N</a>, <a  href="#na">NA</a>, <a  href="#peek">PEEK</a>, <a  href="#record_2">RECORD</a>, <a class="unimplemented" href="#request">REQUEST</a>, <a class="unimplemented" href="#type">TYPE</a> |
| Logical | <a  href="#and">AND</a>, <a  href="#false">FALSE</a>, <a  href="#if">IF</a>, <a  href="#iferror">IFERROR</a>, <a  href="#not">NOT</a>, <a  href="#or">OR</a>, <a  href="#true">TRUE</a> |
| Lookup | <a  href="#lookupone_2">lookupOne</a>, <a  href="#lookuprecords_2">lookupRecords</a>, <a class="unimplemented" href="#address">ADDRESS</a>, <a class="unimplemented" href="#choose">CHOOSE</a>, <a class="unimplemented" href="#column">COLUMN</a>, <a class="unimplemented" href="#columns">COLUMNS</a>, <a  href="#contains">CONTAINS</a>, <a class="unimplemented" href="#getpivotdata">GETPIVOTDATA</a>, <a class="unimplemented" href="#hlookup">HLOOKUP</a>, <a class="unimplemented" href="#hyperlink">HYPERLINK</a>, <a class="unimplemented" href="#index">INDEX</a>, <a class="unimplemented" href="#indirect">INDIRECT</a>, <a class="unimplemented" href="#lookup">LOOKUP</a>, <a class="unimplemented" href="#match">MATCH</a>, <a class="unimplemented" href="#offset">OFFSET</a>, <a class="unimplemented" href="#row">ROW</a>, <a class="unimplemented" href="#rows">ROWS</a>, <a  href="#self_hyperlink">SELF_HYPERLINK</a>, <a  href="#vlookup">VLOOKUP</a> |
| Math | <a  href="#abs">ABS</a>, <a  href="#acos">ACOS</a>, <a  href="#acosh">ACOSH</a>, <a  href="#arabic">ARABIC</a>, <a  href="#asin">ASIN</a>, <a  href="#asinh">ASINH</a>, <a  href="#atan">ATAN</a>, <a  href="#atan2">ATAN2</a>, <a  href="#atanh">ATANH</a>, <a  href="#ceiling">CEILING</a>, <a  href="#combin">COMBIN</a>, <a  href="#cos">COS</a>, <a  href="#cosh">COSH</a>, <a  href="#degrees">DEGREES</a>, <a  href="#even">EVEN</a>, <a  href="#exp">EXP</a>, <a  href="#fact">FACT</a>, <a  href="#factdouble">FACTDOUBLE</a>, <a  href="#floor">FLOOR</a>, <a  href="#gcd">GCD</a>, <a  href="#int">INT</a>, <a  href="#lcm">LCM</a>, <a  href="#ln">LN</a>, <a  href="#log">LOG</a>, <a  href="#log10">LOG10</a>, <a  href="#mod">MOD</a>, <a  href="#mround">MROUND</a>, <a  href="#multinomial">MULTINOMIAL</a>, <a  href="#odd">ODD</a>, <a  href="#pi">PI</a>, <a  href="#power">POWER</a>, <a  href="#product">PRODUCT</a>, <a  href="#quotient">QUOTIENT</a>, <a  href="#radians">RADIANS</a>, <a  href="#rand">RAND</a>, <a  href="#randbetween">RANDBETWEEN</a>, <a  href="#roman">ROMAN</a>, <a  href="#round">ROUND</a>, <a  href="#rounddown">ROUNDDOWN</a>, <a  href="#roundup">ROUNDUP</a>, <a  href="#seriessum">SERIESSUM</a>, <a  href="#sign">SIGN</a>, <a  href="#sin">SIN</a>, <a  href="#sinh">SINH</a>, <a  href="#sqrt">SQRT</a>, <a  href="#sqrtpi">SQRTPI</a>, <a class="unimplemented" href="#subtotal">SUBTOTAL</a>, <a  href="#sum">SUM</a>, <a class="unimplemented" href="#sumif">SUMIF</a>, <a class="unimplemented" href="#sumifs">SUMIFS</a>, <a  href="#sumproduct">SUMPRODUCT</a>, <a class="unimplemented" href="#sumsq">SUMSQ</a>, <a  href="#tan">TAN</a>, <a  href="#tanh">TANH</a>, <a  href="#trunc">TRUNC</a>, <a  href="#uuid">UUID</a> |
| Schedule | <a  href="#schedule">SCHEDULE</a> |
| Stats | <a class="unimplemented" href="#avedev">AVEDEV</a>, <a  href="#average">AVERAGE</a>, <a  href="#averagea">AVERAGEA</a>, <a class="unimplemented" href="#averageif">AVERAGEIF</a>, <a class="unimplemented" href="#averageifs">AVERAGEIFS</a>, <a  href="#average_weighted">AVERAGE_WEIGHTED</a>, <a class="unimplemented" href="#binomdist">BINOMDIST</a>, <a class="unimplemented" href="#confidence">CONFIDENCE</a>, <a class="unimplemented" href="#correl">CORREL</a>, <a  href="#count">COUNT</a>, <a  href="#counta">COUNTA</a>, <a class="unimplemented" href="#covar">COVAR</a>, <a class="unimplemented" href="#critbinom">CRITBINOM</a>, <a class="unimplemented" href="#devsq">DEVSQ</a>, <a class="unimplemented" href="#expondist">EXPONDIST</a>, <a class="unimplemented" href="#fdist">FDIST</a>, <a class="unimplemented" href="#fisher">FISHER</a>, <a class="unimplemented" href="#fisherinv">FISHERINV</a>, <a class="unimplemented" href="#forecast">FORECAST</a>, <a class="unimplemented" href="#f_dist">F_DIST</a>, <a class="unimplemented" href="#f_dist_rt">F_DIST_RT</a>, <a class="unimplemented" href="#geomean">GEOMEAN</a>, <a class="unimplemented" href="#harmean">HARMEAN</a>, <a class="unimplemented" href="#hypgeomdist">HYPGEOMDIST</a>, <a class="unimplemented" href="#intercept">INTERCEPT</a>, <a class="unimplemented" href="#kurt">KURT</a>, <a class="unimplemented" href="#large">LARGE</a>, <a class="unimplemented" href="#loginv">LOGINV</a>, <a class="unimplemented" href="#lognormdist">LOGNORMDIST</a>, <a  href="#max">MAX</a>, <a  href="#maxa">MAXA</a>, <a  href="#median">MEDIAN</a>, <a  href="#min">MIN</a>, <a  href="#mina">MINA</a>, <a class="unimplemented" href="#mode">MODE</a>, <a class="unimplemented" href="#negbinomdist">NEGBINOMDIST</a>, <a class="unimplemented" href="#normdist">NORMDIST</a>, <a class="unimplemented" href="#norminv">NORMINV</a>, <a class="unimplemented" href="#normsdist">NORMSDIST</a>, <a class="unimplemented" href="#normsinv">NORMSINV</a>, <a class="unimplemented" href="#pearson">PEARSON</a>, <a class="unimplemented" href="#percentile">PERCENTILE</a>, <a class="unimplemented" href="#percentrank">PERCENTRANK</a>, <a class="unimplemented" href="#percentrank_exc">PERCENTRANK_EXC</a>, <a class="unimplemented" href="#percentrank_inc">PERCENTRANK_INC</a>, <a class="unimplemented" href="#permut">PERMUT</a>, <a class="unimplemented" href="#poisson">POISSON</a>, <a class="unimplemented" href="#prob">PROB</a>, <a class="unimplemented" href="#quartile">QUARTILE</a>, <a class="unimplemented" href="#rank">RANK</a>, <a class="unimplemented" href="#rank_avg">RANK_AVG</a>, <a class="unimplemented" href="#rank_eq">RANK_EQ</a>, <a class="unimplemented" href="#rsq">RSQ</a>, <a class="unimplemented" href="#skew">SKEW</a>, <a class="unimplemented" href="#slope">SLOPE</a>, <a class="unimplemented" href="#small">SMALL</a>, <a class="unimplemented" href="#standardize">STANDARDIZE</a>, <a  href="#stdev">STDEV</a>, <a  href="#stdeva">STDEVA</a>, <a  href="#stdevp">STDEVP</a>, <a  href="#stdevpa">STDEVPA</a>, <a class="unimplemented" href="#steyx">STEYX</a>, <a class="unimplemented" href="#tdist">TDIST</a>, <a class="unimplemented" href="#tinv">TINV</a>, <a class="unimplemented" href="#trimmean">TRIMMEAN</a>, <a class="unimplemented" href="#ttest">TTEST</a>, <a class="unimplemented" href="#t_inv">T_INV</a>, <a class="unimplemented" href="#t_inv_2t">T_INV_2T</a>, <a class="unimplemented" href="#var">VAR</a>, <a class="unimplemented" href="#vara">VARA</a>, <a class="unimplemented" href="#varp">VARP</a>, <a class="unimplemented" href="#varpa">VARPA</a>, <a class="unimplemented" href="#weibull">WEIBULL</a>, <a class="unimplemented" href="#ztest">ZTEST</a> |
| Text | <a  href="#char">CHAR</a>, <a  href="#clean">CLEAN</a>, <a  href="#code">CODE</a>, <a  href="#concat">CONCAT</a>, <a  href="#concatenate">CONCATENATE</a>, <a  href="#dollar">DOLLAR</a>, <a  href="#exact">EXACT</a>, <a  href="#find">FIND</a>, <a  href="#fixed">FIXED</a>, <a  href="#left">LEFT</a>, <a  href="#len">LEN</a>, <a  href="#lower">LOWER</a>, <a  href="#mid">MID</a>, <a  href="#phone_format">PHONE_FORMAT</a>, <a  href="#proper">PROPER</a>, <a  href="#regexextract">REGEXEXTRACT</a>, <a  href="#regexmatch">REGEXMATCH</a>, <a  href="#regexreplace">REGEXREPLACE</a>, <a  href="#replace">REPLACE</a>, <a  href="#rept">REPT</a>, <a  href="#right">RIGHT</a>, <a  href="#search">SEARCH</a>, <a  href="#substitute">SUBSTITUTE</a>, <a  href="#t">T</a>, <a class="unimplemented" href="#text">TEXT</a>, <a  href="#trim">TRIM</a>, <a  href="#upper">UPPER</a>, <a  href="#value">VALUE</a> |
<!-- END mkpydocs table -->

<!-- BEGIN mkpydocs docs -->
### Grist
<details id="record"><summary >
#### Record
<code>class __Record__</code>
<a class="headerlink" href="#record" title="Permanent link">#</a>
</summary>
A Record represents a record of data. It is the primary means of accessing values in formulas. A
Record for a particular table has a property for each data and formula column in the table.

In a formula, `$field` is translated to `rec.field`, where `rec` is the Record for which the
formula is being evaluated.

For example:
```
def Full_Name(rec, table):
  return rec.First_Name + ' ' + rec.LastName

def Name_Length(rec, table):
  return len(rec.Full_Name)
```
</details>
<details id="_field"><summary >
#### $Field
<code>__$__*Field* or __rec__*.Field*</code>
<a class="headerlink" href="#_field" title="Permanent link">#</a>
</summary>
Access the field named "Field" of the current record. E.g. `$First_Name` or `rec.First_Name`.
</details>
<details id="_group"><summary >
#### $group
<code>__$group__</code>
<a class="headerlink" href="#_group" title="Permanent link">#</a>
</summary>
In a [summary table](summary-tables.md), `$group` is a special field
containing the list of Records that are summarized by the current summary line.  E.g. the formula
`len($group)` counts the number of those records being summarized in each row.

See [RecordSet](#recordset) for useful properties offered by the returned object.

Examples:
```
sum($group.Amount)                        # Sum of the Amount field in the matching records
sum(r.Amount for r in $group)             # Same as sum($group.Amount)
sum(r.Amount for r in $group if r > 0)    # Sum of only the positive amounts
sum(r.Shares * r.Price for r in $group)   # Sum of shares * price products
```
</details>
<details id="recordset"><summary >
#### RecordSet
<code>class __RecordSet__</code>
<a class="headerlink" href="#recordset" title="Permanent link">#</a>
</summary>
A RecordSet represents a collection of records, as returned by `Table.lookupRecords()` or
`$group` property in summary views.

A RecordSet allows iterating through the records:
```
sum(r.Amount for r in Students.lookupRecords(First_Name="John", Last_Name="Doe"))
min(r.DueDate for r in Tasks.lookupRecords(Owner="Bob"))
```

RecordSets also provide a convenient way to access the list of values for a particular field for
all the records, as `record_set.Field`. For example, the examples above are equivalent to:
```
sum(Students.lookupRecords(First_Name="John", Last_Name="Doe").Amount)
min(Tasks.lookupRecords(Owner="Bob").DueDate)
```

You can get the number of records in a RecordSet using `len`, e.g. `len($group)`.
</details>
<details id="usertable"><summary >
#### UserTable
<code>class __UserTable__</code>
<a class="headerlink" href="#usertable" title="Permanent link">#</a>
</summary>
Each data table in the document is represented in the code by an instance of `UserTable` class.
These names are always capitalized. A UserTable provides access to all the records in the table,
as well as methods to look up particular records.

Every table in the document is available to all formulas.
</details>
<details id="all"><summary >
#### all
<code>UserTable.__all__</code>
<a class="headerlink" href="#all" title="Permanent link">#</a>
</summary>
The list of all the records in this table.

For example, this evaluates to the number of records in the table `Students`.
```
len(Students.all)
```

This evaluates to the sum of the `Population` field for every record in the table `Countries`.
```
sum(r.Population for r in Countries.all)
```
</details>
<details id="lookupone"><summary >
#### lookupOne
<code>UserTable.__lookupOne__(Field_In_Lookup_Table=value, ...)</code>
<a class="headerlink" href="#lookupone" title="Permanent link">#</a>
</summary>
Returns a [Record](#record) matching the given field=value arguments. The value may be any expression,
most commonly a field in the current row (e.g. `$SomeField`) or a constant (e.g. a quoted string
like `"Some Value"`). If multiple records match, returns one of them. If none match, returns the
special empty record.

For example:
```
People.lookupOne(First_Name="Lewis", Last_Name="Carroll")
People.lookupOne(Email=$Work_Email)
```
</details>
<details id="lookuprecords"><summary >
#### lookupRecords
<code>UserTable.__lookupRecords__(Field_In_Lookup_Table=value, ...)</code>
<a class="headerlink" href="#lookuprecords" title="Permanent link">#</a>
</summary>
Returns a [RecordSet](#recordset) matching the given field=value arguments. The value may be any expression,
most commonly a field in the current row (e.g. `$SomeField`) or a constant (e.g. a quoted string
like `"Some Value"`) (examples below).
If `sort_by=field` is given, sort the results by that field.

For example:
```
People.lookupRecords(Email=$Work_Email)
People.lookupRecords(First_Name="George", Last_Name="Washington")
People.lookupRecords(Last_Name="Johnson", sort_by="First_Name")
```

See [RecordSet](#recordset) for useful properties offered by the returned object.

See [CONTAINS](#contains) for an example utilizing `UserTable.lookupRecords` to find records
where a field of a list type (such as `Choice List` or `Reference List`) contains the given
value.
</details>
### Date
<details id="date"><summary >
#### DATE
<code>__DATE__(year, month, day)</code>
<a class="headerlink" href="#date" title="Permanent link">#</a>
</summary>
Returns the `datetime.datetime` object that represents a particular date.
The DATE function is most useful in formulas where year, month, and day are formulas, not
constants.

If year is between 0 and 1899 (inclusive), adds 1900 to calculate the year.

```python
>>> DATE(108, 1, 2)
datetime.date(2008, 1, 2)
```

```python
>>> DATE(2008, 1, 2)
datetime.date(2008, 1, 2)
```

If month is greater than 12, rolls into the following year.

```python
>>> DATE(2008, 14, 2)
datetime.date(2009, 2, 2)
```

If month is less than 1, subtracts that many months plus 1, from the first month in the year.

```python
>>> DATE(2008, -3, 2)
datetime.date(2007, 9, 2)
```

If day is greater than the number of days in the given month, rolls into the following months.

```python
>>> DATE(2008, 1, 35)
datetime.date(2008, 2, 4)
```

If day is less than 1, subtracts that many days plus 1, from the first day of the given month.

```python
>>> DATE(2008, 1, -15)
datetime.date(2007, 12, 16)
```
</details>
<details id="dateadd"><summary >
#### DATEADD
<code>__DATEADD__(start_date, days=0, months=0, years=0, weeks=0)</code>
<a class="headerlink" href="#dateadd" title="Permanent link">#</a>
</summary>
Returns the date a given number of days, months, years, or weeks away from `start_date`. You may
specify arguments in any order if you specify argument names. Use negative values to subtract.

For example, `DATEADD(date, 1)` is the same as `DATEADD(date, days=1)`, ands adds one day to
`date`. `DATEADD(date, years=1, days=-1)` adds one year minus one day.


```python
>>> DATEADD(DATE(2011, 1, 15), 1)
datetime.date(2011, 1, 16)
```

```python
>>> DATEADD(DATE(2011, 1, 15), months=1, days=-1)
datetime.date(2011, 2, 14)
```

```python
>>> DATEADD(DATE(2011, 1, 15), years=-2, months=1, days=3, weeks=2)
datetime.date(2009, 3, 4)
```

```python
>>> DATEADD(DATE(1975, 4, 30), years=50, weeks=-5)
datetime.date(2025, 3, 26)
```

</details>
<details id="datedif"><summary >
#### DATEDIF
<code>__DATEDIF__(start_date, end_date, unit)</code>
<a class="headerlink" href="#datedif" title="Permanent link">#</a>
</summary>
Calculates the number of days, months, or years between two dates.
Unit indicates the type of information that you want returned:

  - "Y": The number of complete years in the period.
  - "M": The number of complete months in the period.
  - "D": The number of days in the period.
  - "MD": The difference between the days in start_date and end_date. The months and years of the
    dates are ignored.
  - "YM": The difference between the months in start_date and end_date. The days and years of the
    dates are ignored.
  - "YD": The difference between the days of start_date and end_date. The years of the dates are
    ignored.

Two complete years in the period (2)

```python
>>> DATEDIF(DATE(2001, 1, 1), DATE(2003, 1, 1), "Y")
2
```

440 days between June 1, 2001, and August 15, 2002 (440)

```python
>>> DATEDIF(DATE(2001, 6, 1), DATE(2002, 8, 15), "D")
440
```

75 days between June 1 and August 15, ignoring the years of the dates (75)

```python
>>> DATEDIF(DATE(2001, 6, 1), DATE(2012, 8, 15), "YD")
75
```

The difference between 1 and 15, ignoring the months and the years of the dates (14)

```python
>>> DATEDIF(DATE(2001, 6, 1), DATE(2002, 8, 15), "MD")
14
```
</details>
<details id="datevalue"><summary >
#### DATEVALUE
<code>__DATEVALUE__(date_string, tz=None)</code>
<a class="headerlink" href="#datevalue" title="Permanent link">#</a>
</summary>
Converts a date that is stored as text to a `datetime` object.


```python
>>> DATEVALUE("1/1/2008")
datetime.datetime(2008, 1, 1, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> DATEVALUE("30-Jan-2008")
datetime.datetime(2008, 1, 30, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> DATEVALUE("2008-12-11")
datetime.datetime(2008, 12, 11, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> DATEVALUE("5-JUL").replace(year=2000)
datetime.datetime(2000, 7, 5, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

In case of ambiguity, prefer M/D/Y format.

```python
>>> DATEVALUE("1/2/3")
datetime.datetime(2003, 1, 2, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```
</details>
<details id="date_to_xl"><summary >
#### DATE_TO_XL
<code>__DATE_TO_XL__(date_value)</code>
<a class="headerlink" href="#date_to_xl" title="Permanent link">#</a>
</summary>
Converts a Python `date` or `datetime` object to the serial number as used by
Excel, with December 30, 1899 as serial number 1.

See XL_TO_DATE for more explanation.


```python
>>> DATE_TO_XL(datetime.date(2008, 1, 1))
39448.0
```

```python
>>> DATE_TO_XL(datetime.date(2012, 3, 14))
40982.0
```

```python
>>> DATE_TO_XL(datetime.datetime(2012, 3, 14, 1, 30))
40982.0625
```
</details>
<details id="day"><summary >
#### DAY
<code>__DAY__(date)</code>
<a class="headerlink" href="#day" title="Permanent link">#</a>
</summary>
Returns the day of a date, as an integer ranging from 1 to 31. Same as `date.day`.


```python
>>> DAY(DATE(2011, 4, 15))
15
```

```python
>>> DAY("5/31/2012")
31
```

```python
>>> DAY(datetime.datetime(1900, 1, 1))
1
```

</details>
<details id="days"><summary >
#### DAYS
<code>__DAYS__(end_date, start_date)</code>
<a class="headerlink" href="#days" title="Permanent link">#</a>
</summary>
Returns the number of days between two dates. Same as `(end_date - start_date).days`.


```python
>>> DAYS("3/15/11","2/1/11")
42
```

```python
>>> DAYS(DATE(2011, 12, 31), DATE(2011, 1, 1))
364
```

```python
>>> DAYS("2/1/11", "3/15/11")
-42
```

</details>
<details id="dtime"><summary >
#### DTIME
<code>__DTIME__(value, tz=None)</code>
<a class="headerlink" href="#dtime" title="Permanent link">#</a>
</summary>
Returns the value converted to a python `datetime` object. The value may be a
`string`, `date` (interpreted as midnight on that day), `time` (interpreted as a
time-of-day today), or an existing `datetime`.

The returned `datetime` will have its timezone set to the `tz` argument, or the
document's default timezone when `tz` is omitted or None. If the input is itself a
`datetime` with the timezone set, it is returned unchanged (no changes to its timezone).


```python
>>> DTIME(datetime.date(2017, 1, 1))
datetime.datetime(2017, 1, 1, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> DTIME(datetime.date(2017, 1, 1), 'Europe/Paris')
datetime.datetime(2017, 1, 1, 0, 0, tzinfo=moment.tzinfo('Europe/Paris'))
```

```python
>>> DTIME(datetime.datetime(2017, 1, 1))
datetime.datetime(2017, 1, 1, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> DTIME(datetime.datetime(2017, 1, 1, tzinfo=moment.tzinfo('UTC')))
datetime.datetime(2017, 1, 1, 0, 0, tzinfo=moment.tzinfo('UTC'))
```

```python
>>> DTIME(datetime.datetime(2017, 1, 1, tzinfo=moment.tzinfo('UTC')), 'Europe/Paris')
datetime.datetime(2017, 1, 1, 0, 0, tzinfo=moment.tzinfo('UTC'))
```

```python
>>> DTIME("1/1/2008")
datetime.datetime(2008, 1, 1, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

</details>
<details id="edate"><summary >
#### EDATE
<code>__EDATE__(start_date, months)</code>
<a class="headerlink" href="#edate" title="Permanent link">#</a>
</summary>
Returns the date that is the given number of months before or after `start_date`. Use
EDATE to calculate maturity dates or due dates that fall on the same day of the month as the
date of issue.


```python
>>> EDATE(DATE(2011, 1, 15), 1)
datetime.date(2011, 2, 15)
```

```python
>>> EDATE(DATE(2011, 1, 15), -1)
datetime.date(2010, 12, 15)
```

```python
>>> EDATE(DATE(2011, 1, 15), 2)
datetime.date(2011, 3, 15)
```

```python
>>> EDATE(DATE(2012, 3, 1), 10)
datetime.date(2013, 1, 1)
```

```python
>>> EDATE(DATE(2012, 5, 1), -2)
datetime.date(2012, 3, 1)
```

</details>
<details id="eomonth"><summary >
#### EOMONTH
<code>__EOMONTH__(start_date, months)</code>
<a class="headerlink" href="#eomonth" title="Permanent link">#</a>
</summary>
Returns the date for the last day of the month that is the indicated number of months before or
after start_date. Use EOMONTH to calculate maturity dates or due dates that fall on the last day
of the month.


```python
>>> EOMONTH(DATE(2011, 1, 1), 1)
datetime.date(2011, 2, 28)
```

```python
>>> EOMONTH(DATE(2011, 1, 15), -3)
datetime.date(2010, 10, 31)
```

```python
>>> EOMONTH(DATE(2012, 3, 1), 10)
datetime.date(2013, 1, 31)
```

```python
>>> EOMONTH(DATE(2012, 5, 1), -2)
datetime.date(2012, 3, 31)
```

</details>
<details id="hour"><summary >
#### HOUR
<code>__HOUR__(time)</code>
<a class="headerlink" href="#hour" title="Permanent link">#</a>
</summary>
Same as `time.hour`.


```python
>>> HOUR(XL_TO_DATE(0.75))
18
```

```python
>>> HOUR("7/18/2011 7:45")
7
```

```python
>>> HOUR("4/21/2012")
0
```

</details>
<details id="isoweeknum"><summary >
#### ISOWEEKNUM
<code>__ISOWEEKNUM__(date)</code>
<a class="headerlink" href="#isoweeknum" title="Permanent link">#</a>
</summary>
Returns the ISO week number of the year for a given date.


```python
>>> ISOWEEKNUM("3/9/2012")
10
```

```python
>>> [ISOWEEKNUM(DATE(2000 + y, 1, 1)) for y in [0,1,2,3,4,5,6,7,8]]
[52, 1, 1, 1, 1, 53, 52, 1, 1]
```

</details>
<details id="minute"><summary >
#### MINUTE
<code>__MINUTE__(time)</code>
<a class="headerlink" href="#minute" title="Permanent link">#</a>
</summary>
Returns the minutes of `datetime`, as an integer from 0 to 59.
Same as `time.minute`.


```python
>>> MINUTE(XL_TO_DATE(0.75))
0
```

```python
>>> MINUTE("7/18/2011 7:45")
45
```

```python
>>> MINUTE("12:59:00 PM")
59
```

```python
>>> MINUTE(datetime.time(12, 58, 59))
58
```

</details>
<details id="month"><summary >
#### MONTH
<code>__MONTH__(date)</code>
<a class="headerlink" href="#month" title="Permanent link">#</a>
</summary>
Returns the month of a date represented, as an integer from from 1 (January) to 12 (December).
Same as `date.month`.


```python
>>> MONTH(DATE(2011, 4, 15))
4
```

```python
>>> MONTH("5/31/2012")
5
```

```python
>>> MONTH(datetime.datetime(1900, 1, 1))
1
```

</details>
<details id="now"><summary >
#### NOW
<code>__NOW__(tz=None)</code>
<a class="headerlink" href="#now" title="Permanent link">#</a>
</summary>
Returns the `datetime` object for the current time.
</details>
<details id="second"><summary >
#### SECOND
<code>__SECOND__(time)</code>
<a class="headerlink" href="#second" title="Permanent link">#</a>
</summary>
Returns the seconds of `datetime`, as an integer from 0 to 59.
Same as `time.second`.


```python
>>> SECOND(XL_TO_DATE(0.75))
0
```

```python
>>> SECOND("7/18/2011 7:45:13")
13
```

```python
>>> SECOND(datetime.time(12, 58, 59))
59
```

</details>
<details id="today"><summary >
#### TODAY
<code>__TODAY__(tz=None)</code>
<a class="headerlink" href="#today" title="Permanent link">#</a>
</summary>
Returns the `date` object for the current date.
</details>
<details id="weekday"><summary >
#### WEEKDAY
<code>__WEEKDAY__(date, return_type=1)</code>
<a class="headerlink" href="#weekday" title="Permanent link">#</a>
</summary>
Returns the day of the week corresponding to a date. The day is given as an integer, ranging
from 1 (Sunday) to 7 (Saturday), by default.

Return_type determines the type of the returned value.

  - 1 (default) - Returns 1 (Sunday) through 7 (Saturday).
  - 2   - Returns 1 (Monday) through 7 (Sunday).
  - 3   - Returns 0 (Monday) through 6 (Sunday).
  - 11  - Returns 1 (Monday) through 7 (Sunday).
  - 12  - Returns 1 (Tuesday) through 7 (Monday).
  - 13  - Returns 1 (Wednesday) through 7 (Tuesday).
  - 14  - Returns 1 (Thursday) through 7 (Wednesday).
  - 15  - Returns 1 (Friday) through 7 (Thursday).
  - 16  - Returns 1 (Saturday) through 7 (Friday).
  - 17  - Returns 1 (Sunday) through 7 (Saturday).


```python
>>> WEEKDAY(DATE(2008, 2, 14))
5
```

```python
>>> WEEKDAY(DATE(2012, 3, 1))
5
```

```python
>>> WEEKDAY(DATE(2012, 3, 1), 1)
5
```

```python
>>> WEEKDAY(DATE(2012, 3, 1), 2)
4
```

```python
>>> WEEKDAY("3/1/2012", 3)
3
```
</details>
<details id="weeknum"><summary >
#### WEEKNUM
<code>__WEEKNUM__(date, return_type=1)</code>
<a class="headerlink" href="#weeknum" title="Permanent link">#</a>
</summary>
Returns the week number of a specific date. For example, the week containing January 1 is the
first week of the year, and is numbered week 1.

Return_type determines which week is considered the first week of the year.

  - 1 (default) - Week 1 is the first week starting Sunday that contains January 1.
  - 2   - Week 1 is the first week starting Monday that contains January 1.
  - 11  - Week 1 is the first week starting Monday that contains January 1.
  - 12  - Week 1 is the first week starting Tuesday that contains January 1.
  - 13  - Week 1 is the first week starting Wednesday that contains January 1.
  - 14  - Week 1 is the first week starting Thursday that contains January 1.
  - 15  - Week 1 is the first week starting Friday that contains January 1.
  - 16  - Week 1 is the first week starting Saturday that contains January 1.
  - 17  - Week 1 is the first week starting Sunday that contains January 1.
  - 21  - ISO 8601 Approach: Week 1 is the first week starting Monday that contains January 4.
        Equivalently, it is the week that contains the first Thursday of the year.


```python
>>> WEEKNUM(DATE(2012, 3, 9))
10
```

```python
>>> WEEKNUM(DATE(2012, 3, 9), 2)
11
```

```python
>>> WEEKNUM('1/1/1900')
1
```

```python
>>> WEEKNUM('2/1/1900')
5
```
</details>
<details id="xl_to_date"><summary >
#### XL_TO_DATE
<code>__XL_TO_DATE__(value, tz=None)</code>
<a class="headerlink" href="#xl_to_date" title="Permanent link">#</a>
</summary>
Converts a provided Excel serial number representing a date into a `datetime` object.
Value is interpreted as the number of days since December 30, 1899.

(This corresponds to Google Sheets interpretation. Excel starts with Dec. 31, 1899 but wrongly
considers 1900 to be a leap year. Excel for Mac should be configured to use 1900 date system,
i.e. uncheck "Use the 1904 date system" option.)

The returned `datetime` will have its timezone set to the `tz` argument, or the
document's default timezone when `tz` is omitted or None.


```python
>>> XL_TO_DATE(41100.1875)
datetime.datetime(2012, 7, 10, 4, 30, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> XL_TO_DATE(39448)
datetime.datetime(2008, 1, 1, 0, 0, tzinfo=moment.tzinfo('America/New_York'))
```

```python
>>> XL_TO_DATE(40982.0625)
datetime.datetime(2012, 3, 14, 1, 30, tzinfo=moment.tzinfo('America/New_York'))
```
</details>
<details id="year"><summary >
#### YEAR
<code>__YEAR__(date)</code>
<a class="headerlink" href="#year" title="Permanent link">#</a>
</summary>
Returns the year corresponding to a date as an integer.
Same as `date.year`.


```python
>>> YEAR(DATE(2011, 4, 15))
2011
```

```python
>>> YEAR("5/31/2030")
2030
```

```python
>>> YEAR(datetime.datetime(1900, 1, 1))
1900
```

</details>
<details id="yearfrac"><summary >
#### YEARFRAC
<code>__YEARFRAC__(start_date, end_date, basis=0)</code>
<a class="headerlink" href="#yearfrac" title="Permanent link">#</a>
</summary>
Calculates the fraction of the year represented by the number of whole days between two dates.

Basis is the type of day count basis to use.

  * `0` (default) - US (NASD) 30/360
  * `1`   - Actual/actual
  * `2`   - Actual/360
  * `3`   - Actual/365
  * `4`   - European 30/360
  * `-1`  - Actual/actual (Google Sheets variation)

This function is useful for financial calculations. For compatibility with Excel, it defaults to
using the NASD standard calendar. For use in non-financial settings, option `-1` is
likely the best choice.

See <https://en.wikipedia.org/wiki/360-day_calendar> for explanation of
the US 30/360 and European 30/360 methods. See <http://www.dwheeler.com/yearfrac/> for analysis of
Excel's particular implementation.

Basis `-1` is similar to `1`, but differs from Excel when dates span both leap and non-leap years.
It matches the calculation in Google Sheets, counting the days in each year as a fraction of
that year's length.

Fraction of the year between 1/1/2012 and 7/30/12, omitting the Basis argument.

```python
>>> "%.8f" % YEARFRAC(DATE(2012, 1, 1), DATE(2012, 7, 30))
'0.58055556'
```

Fraction between same dates, using the Actual/Actual basis argument. Because 2012 is a Leap
year, it has a 366 day basis.

```python
>>> "%.8f" % YEARFRAC(DATE(2012, 1, 1), DATE(2012, 7, 30), 1)
'0.57650273'
```

Fraction between same dates, using the Actual/365 basis argument. Uses a 365 day basis.

```python
>>> "%.8f" % YEARFRAC(DATE(2012, 1, 1), DATE(2012, 7, 30), 3)
'0.57808219'
```
</details>
### Info
<details id="cell"><summary class="unimplemented">
#### CELL
<code>__CELL__(info_type, reference)</code>
<a class="headerlink" href="#cell" title="Permanent link">#</a>
</summary>
Returns the requested information about the specified cell. This is not implemented in Grist

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="current_conversion"><summary >
#### CURRENT_CONVERSION
<code>__CURRENT_CONVERSION__(rec)</code>
<a class="headerlink" href="#current_conversion" title="Permanent link">#</a>
</summary>
Internal function used by Grist during column type conversions. Not available for use in
formulas.
</details>
<details id="isblank"><summary class="unimplemented">
#### ISBLANK
<code>__ISBLANK__(value)</code>
<a class="headerlink" href="#isblank" title="Permanent link">#</a>
</summary>
Returns whether a value refers to an empty cell. It isn't implemented in Grist. To check for an
empty string, use `value == ""`.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="isemail"><summary >
#### ISEMAIL
<code>__ISEMAIL__(value)</code>
<a class="headerlink" href="#isemail" title="Permanent link">#</a>
</summary>
Returns whether a value is a valid email address.

Note that checking email validity is not an exact science. The technical standard considers many
email addresses valid that are not used in practice, and would not be considered valid by most
users. Instead, we follow Google Sheets implementation, with some differences, noted below.


```python
>>> ISEMAIL("Abc.123@example.com")
True
```

```python
>>> ISEMAIL("Bob_O-Reilly+tag@example.com")
True
```

```python
>>> ISEMAIL("John Doe")
False
```

```python
>>> ISEMAIL("john@aol...com")
False
```
</details>
<details id="iserr"><summary >
#### ISERR
<code>__ISERR__(value)</code>
<a class="headerlink" href="#iserr" title="Permanent link">#</a>
</summary>
Checks whether a value is an error. In other words, it returns true
if using `value` directly would raise an exception.

NOTE: Grist implements this by automatically wrapping the argument to use lazy evaluation.

A more Pythonic approach to checking for errors is:
```
try:
  ... value ...
except Exception, err:
  ... do something about the error ...
```

For example:


```python
>>> ISERR("Hello")
False
```
</details>
<details id="iserror"><summary >
#### ISERROR
<code>__ISERROR__(value)</code>
<a class="headerlink" href="#iserror" title="Permanent link">#</a>
</summary>
Checks whether a value is an error or an invalid value. It is similar to `ISERR`, but also
returns true for an invalid value such as NaN or a text value in a Numeric column.

NOTE: Grist implements this by automatically wrapping the argument to use lazy evaluation.


```python
>>> ISERROR("Hello")
False
```

```python
>>> ISERROR(AltText("fail"))
True
```

```python
>>> ISERROR(float('nan'))
True
```
</details>
<details id="islogical"><summary >
#### ISLOGICAL
<code>__ISLOGICAL__(value)</code>
<a class="headerlink" href="#islogical" title="Permanent link">#</a>
</summary>
Checks whether a value is `True` or `False`.


```python
>>> ISLOGICAL(True)
True
```

```python
>>> ISLOGICAL(False)
True
```

```python
>>> ISLOGICAL(0)
False
```

```python
>>> ISLOGICAL(None)
False
```

```python
>>> ISLOGICAL("Test")
False
```

</details>
<details id="isna"><summary >
#### ISNA
<code>__ISNA__(value)</code>
<a class="headerlink" href="#isna" title="Permanent link">#</a>
</summary>
Checks whether a value is the error `#N/A`.


```python
>>> ISNA(float('nan'))
True
```

```python
>>> ISNA(0.0)
False
```

```python
>>> ISNA('text')
False
```

```python
>>> ISNA(float('-inf'))
False
```

</details>
<details id="isnontext"><summary >
#### ISNONTEXT
<code>__ISNONTEXT__(value)</code>
<a class="headerlink" href="#isnontext" title="Permanent link">#</a>
</summary>
Checks whether a value is non-textual.


```python
>>> ISNONTEXT("asdf")
False
```

```python
>>> ISNONTEXT("")
False
```

```python
>>> ISNONTEXT(AltText("text"))
False
```

```python
>>> ISNONTEXT(17.0)
True
```

```python
>>> ISNONTEXT(None)
True
```

```python
>>> ISNONTEXT(datetime.date(2011, 1, 1))
True
```

</details>
<details id="isnumber"><summary >
#### ISNUMBER
<code>__ISNUMBER__(value)</code>
<a class="headerlink" href="#isnumber" title="Permanent link">#</a>
</summary>
Checks whether a value is a number.


```python
>>> ISNUMBER(17)
True
```

```python
>>> ISNUMBER(-123.123423)
True
```

```python
>>> ISNUMBER(False)
True
```

```python
>>> ISNUMBER(float('nan'))
True
```

```python
>>> ISNUMBER(float('inf'))
True
```

```python
>>> ISNUMBER('17')
False
```

```python
>>> ISNUMBER(None)
False
```

```python
>>> ISNUMBER(datetime.date(2011, 1, 1))
False
```
</details>
<details id="isref"><summary >
#### ISREF
<code>__ISREF__(value)</code>
<a class="headerlink" href="#isref" title="Permanent link">#</a>
</summary>
Checks whether a value is a table record.

For example, if a column `person` is of type Reference to the `People` table,
then `ISREF($person)` is `True`.
Similarly, `ISREF(People.lookupOne(name=$name))` is `True`. For any other type of value,
`ISREF()` would evaluate to `False`.


```python
>>> ISREF(17)
False
```

```python
>>> ISREF("Roger")
False
```

</details>
<details id="isreflist"><summary >
#### ISREFLIST
<code>__ISREFLIST__(value)</code>
<a class="headerlink" href="#isreflist" title="Permanent link">#</a>
</summary>
Checks whether a value is a [`RecordSet`](#recordset),
the type of values in Reference List columns.

For example, if a column `people` is of type Reference List to the `People` table,
then `ISREFLIST($people)` is `True`.
Similarly, `ISREFLIST(People.lookupRecords(name=$name))` is `True`. For any other type of value,
`ISREFLIST()` would evaluate to `False`.


```python
>>> ISREFLIST(17)
False
```

```python
>>> ISREFLIST("Roger")
False
```

</details>
<details id="istext"><summary >
#### ISTEXT
<code>__ISTEXT__(value)</code>
<a class="headerlink" href="#istext" title="Permanent link">#</a>
</summary>
Checks whether a value is text.


```python
>>> ISTEXT("asdf")
True
```

```python
>>> ISTEXT("")
True
```

```python
>>> ISTEXT(AltText("text"))
True
```

```python
>>> ISTEXT(17.0)
False
```

```python
>>> ISTEXT(None)
False
```

```python
>>> ISTEXT(datetime.date(2011, 1, 1))
False
```

</details>
<details id="isurl"><summary >
#### ISURL
<code>__ISURL__(value)</code>
<a class="headerlink" href="#isurl" title="Permanent link">#</a>
</summary>
Checks whether a value is a valid URL. It does not need to be fully qualified, or to include
"http://" and "www". It does not follow a standard, but attempts to work similarly to ISURL in
Google Sheets, and to return True for text that is likely a URL.

Valid protocols include ftp, http, https, gopher, mailto, news, telnet, and aim.


```python
>>> ISURL("http://www.getgrist.com")
True
```

```python
>>> ISURL("https://foo.com/test_(wikipedia)#cite-1")
True
```

```python
>>> ISURL("mailto://user@example.com")
True
```

```python
>>> ISURL("http:///a")
False
```
</details>
<details id="n"><summary >
#### N
<code>__N__(value)</code>
<a class="headerlink" href="#n" title="Permanent link">#</a>
</summary>
Returns the value converted to a number. True/False are converted to 1/0. A date is converted to
Excel-style serial number of the date. Anything else is converted to 0.


```python
>>> N(7)
7
```

```python
>>> N(7.1)
7.1
```

```python
>>> N("Even")
0
```

```python
>>> N("7")
0
```

```python
>>> N(True)
1
```

```python
>>> N(datetime.datetime(2011, 4, 17))
40650.0
```

</details>
<details id="na"><summary >
#### NA
<code>__NA__()</code>
<a class="headerlink" href="#na" title="Permanent link">#</a>
</summary>
Returns the "value not available" error, `#N/A`.


```python
>>> math.isnan(NA())
True
```

</details>
<details id="peek"><summary >
#### PEEK
<code>__PEEK__(func)</code>
<a class="headerlink" href="#peek" title="Permanent link">#</a>
</summary>
Evaluates the given expression without creating dependencies
or requiring that referenced values are up to date, using whatever value it finds in a cell.
This is useful for preventing circular reference errors, particularly in trigger formulas.

For example, if the formula for `A` depends on `$B` and the formula for `B` depends on `$A`,
then normally this would raise a circular reference error because each value needs to be
calculated before the other. But if `A` uses `PEEK($B)` then it will simply get the value
already stored in `$B` without requiring that `$B` is first calculated to the latest value.
Therefore `A` will be calculated first, and `B` can use `$A` without problems.
</details>
<details id="record_2"><summary >
#### RECORD
<code>__RECORD__(record_or_list, dates_as_iso=False, expand_refs=0)</code>
<a class="headerlink" href="#record_2" title="Permanent link">#</a>
</summary>
Returns a Python dictionary with all fields in the given record. If a list of records is given,
returns a list of corresponding Python dictionaries.

If dates_as_iso is set, Date and DateTime values are converted to string using ISO 8601 format.

If expand_refs is set to 1 or higher, Reference values are replaced with a RECORD representation
of the referenced record, expanding the given number of levels.

Error values present in cells of the record are replaced with None value, and a special key of
"_error_" gets added containing the error messages for those cells. For example:
`{"Ratio": None, "_error_": {"Ratio": "ZeroDivisionError: integer division or modulo by zero"}}`

Note that care is needed to avoid circular references when using RECORD(), since it creates a
dependency on every cell in the record. In case of RECORD(rec), the cell containing this call
will be omitted from the resulting dictionary.

For example:
```
RECORD($Person)
RECORD(rec)
RECORD(People.lookupOne(First_Name="Alice"))
RECORD(People.lookupRecords(Department="HR"))
```
</details>
<details id="request"><summary class="unimplemented">
#### REQUEST
<code>__REQUEST__(url, params=None, headers=None)</code>
<a class="headerlink" href="#request" title="Permanent link">#</a>
</summary>

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="type"><summary class="unimplemented">
#### TYPE
<code>__TYPE__(value)</code>
<a class="headerlink" href="#type" title="Permanent link">#</a>
</summary>
Returns a number associated with the type of data passed into the function. This is not
implemented in Grist. Use `isinstance(value, type)` or `type(value)`.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
### Logical
<details id="and"><summary >
#### AND
<code>__AND__(logical_expression, *logical_expressions)</code>
<a class="headerlink" href="#and" title="Permanent link">#</a>
</summary>
Returns True if all of the arguments are logically true, and False if any are false.
Same as `all([value1, value2, ...])`.


```python
>>> AND(1)
True
```

```python
>>> AND(0)
False
```

```python
>>> AND(1, 1)
True
```

```python
>>> AND(1,2,3,4)
True
```

```python
>>> AND(1,2,3,4,0)
False
```

</details>
<details id="false"><summary >
#### FALSE
<code>__FALSE__()</code>
<a class="headerlink" href="#false" title="Permanent link">#</a>
</summary>
Returns the logical value `False`. You may also use the value `False` directly. This
function is provided primarily for compatibility with other spreadsheet programs.


```python
>>> FALSE()
False
```

</details>
<details id="if"><summary >
#### IF
<code>__IF__(logical_expression, value_if_true, value_if_false)</code>
<a class="headerlink" href="#if" title="Permanent link">#</a>
</summary>
Returns one value if a logical expression is `True` and another if it is `False`.

The equivalent Python expression is:
```
value_if_true if logical_expression else value_if_false
```

Since Grist supports multi-line formulas, you may also use Python blocks such as:
```
if logical_expression:
  return value_if_true
else:
  return value_if_false
```

NOTE: Grist follows Excel model by only evaluating one of the value expressions, by
automatically wrapping the expressions to use lazy evaluation. This allows `IF(False, 1/0, 1)`
to evaluate to `1` rather than raise an exception.


```python
>>> IF(12, "Yes", "No")
'Yes'
```

```python
>>> IF(None, "Yes", "No")
'No'
```

```python
>>> IF(True, 0.85, 0.0)
0.85
```

```python
>>> IF(False, 0.85, 0.0)
0.0
```
</details>
<details id="iferror"><summary >
#### IFERROR
<code>__IFERROR__(value, value_if_error='')</code>
<a class="headerlink" href="#iferror" title="Permanent link">#</a>
</summary>
Returns the first argument if it is not an error value, otherwise returns the second argument if
present, or a blank if the second argument is absent.

NOTE: Grist handles values that raise an exception by wrapping them to use lazy evaluation.


```python
>>> IFERROR(float('nan'), "**NAN**")
'**NAN**'
```

```python
>>> IFERROR(17.17, "**NAN**")
17.17
```

```python
>>> IFERROR("Text")
'Text'
```

```python
>>> IFERROR(AltText("hello"))
''
```
</details>
<details id="not"><summary >
#### NOT
<code>__NOT__(logical_expression)</code>
<a class="headerlink" href="#not" title="Permanent link">#</a>
</summary>
`True`. Same as `not logical_expression`.


```python
>>> NOT(123)
False
```

```python
>>> NOT(0)
True
```

</details>
<details id="or"><summary >
#### OR
<code>__OR__(logical_expression, *logical_expressions)</code>
<a class="headerlink" href="#or" title="Permanent link">#</a>
</summary>
Returns True if any of the arguments is logically true, and false if all of the
arguments are false.
Same as `any([value1, value2, ...])`.


```python
>>> OR(1)
True
```

```python
>>> OR(0)
False
```

```python
>>> OR(1, 1)
True
```

```python
>>> OR(0, 1)
True
```

```python
>>> OR(0, 0)
False
```

```python
>>> OR(0,False,0.0,"",None)
False
```

```python
>>> OR(0,None,3,0)
True
```

</details>
<details id="true"><summary >
#### TRUE
<code>__TRUE__()</code>
<a class="headerlink" href="#true" title="Permanent link">#</a>
</summary>
Returns the logical value `True`. You may also use the value `True` directly. This
function is provided primarily for compatibility with other spreadsheet programs.


```python
>>> TRUE()
True
```

</details>
### Lookup
<details id="lookupone_2"><summary >
#### lookupOne
<code>UserTable.__lookupOne__(Field_In_Lookup_Table=value, ...)</code>
<a class="headerlink" href="#lookupone_2" title="Permanent link">#</a>
</summary>
Returns a [Record](#record) matching the given field=value arguments. The value may be any expression,
most commonly a field in the current row (e.g. `$SomeField`) or a constant (e.g. a quoted string
like `"Some Value"`). If multiple records match, returns one of them. If none match, returns the
special empty record.

For example:
```
People.lookupOne(First_Name="Lewis", Last_Name="Carroll")
People.lookupOne(Email=$Work_Email)
```
</details>
<details id="lookuprecords_2"><summary >
#### lookupRecords
<code>UserTable.__lookupRecords__(Field_In_Lookup_Table=value, ...)</code>
<a class="headerlink" href="#lookuprecords_2" title="Permanent link">#</a>
</summary>
Returns a [RecordSet](#recordset) matching the given field=value arguments. The value may be any expression,
most commonly a field in the current row (e.g. `$SomeField`) or a constant (e.g. a quoted string
like `"Some Value"`) (examples below).
If `sort_by=field` is given, sort the results by that field.

For example:
```
People.lookupRecords(Email=$Work_Email)
People.lookupRecords(First_Name="George", Last_Name="Washington")
People.lookupRecords(Last_Name="Johnson", sort_by="First_Name")
```

See [RecordSet](#recordset) for useful properties offered by the returned object.

See [CONTAINS](#contains) for an example utilizing `UserTable.lookupRecords` to find records
where a field of a list type (such as `Choice List` or `Reference List`) contains the given
value.
</details>
<details id="address"><summary class="unimplemented">
#### ADDRESS
<code>__ADDRESS__(row, column, absolute_relative_mode, use_a1_notation, sheet)</code>
<a class="headerlink" href="#address" title="Permanent link">#</a>
</summary>
Returns a cell reference as a string.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="choose"><summary class="unimplemented">
#### CHOOSE
<code>__CHOOSE__(index, choice1, choice2)</code>
<a class="headerlink" href="#choose" title="Permanent link">#</a>
</summary>
Returns an element from a list of choices based on index.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="column"><summary class="unimplemented">
#### COLUMN
<code>__COLUMN__(cell_reference=None)</code>
<a class="headerlink" href="#column" title="Permanent link">#</a>
</summary>
Returns the column number of a specified cell, with `A=1`.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="columns"><summary class="unimplemented">
#### COLUMNS
<code>__COLUMNS__(range)</code>
<a class="headerlink" href="#columns" title="Permanent link">#</a>
</summary>
Returns the number of columns in a specified array or range.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="contains"><summary >
#### CONTAINS
<code>__CONTAINS__(value, match_empty=no_match_empty)</code>
<a class="headerlink" href="#contains" title="Permanent link">#</a>
</summary>
Use this marker with [UserTable.lookupRecords](#lookuprecords) to find records
where a field of a list type (such as `Choice List` or `Reference List`) contains the given value.

For example:

    MoviesTable.lookupRecords(genre=CONTAINS("Drama"))

will return records in `MoviesTable` where the column `genre`
is a list or other container such as `["Comedy", "Drama"]`,
i.e. `"Drama" in $genre`.

Note that the column being looked up (e.g. `genre`)
must have values of a container type such as list, tuple, or set.
In particular the values mustn't be strings, e.g. `"Comedy-Drama"` won't match
even though `"Drama" in "Comedy-Drama"` is `True` in Python.
It also won't match substrings within container elements, e.g. `["Comedy-Drama"]`.

You can optionally pass a second argument `match_empty` to indicate a value that
should be matched against empty lists in the looked up column.

For example, given this formula:

    MoviesTable.lookupRecords(genre=CONTAINS(g, match_empty=''))

If `g` is `''` (i.e. equal to `match_empty`) then the column `genre` in the returned records
will either be an empty list (or other container) or a list containing `g` as usual.
</details>
<details id="getpivotdata"><summary class="unimplemented">
#### GETPIVOTDATA
<code>__GETPIVOTDATA__(value_name, any_pivot_table_cell, original_column_1, pivot_item_1=None, *args)</code>
<a class="headerlink" href="#getpivotdata" title="Permanent link">#</a>
</summary>
Extracts an aggregated value from a pivot table that corresponds to the specified row and column headings.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="hlookup"><summary class="unimplemented">
#### HLOOKUP
<code>__HLOOKUP__(search_key, range, index, is_sorted)</code>
<a class="headerlink" href="#hlookup" title="Permanent link">#</a>
</summary>
Horizontal lookup. Searches across the first row of a range for a key and returns the value of a specified cell in the column found.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="hyperlink"><summary class="unimplemented">
#### HYPERLINK
<code>__HYPERLINK__(url, link_label)</code>
<a class="headerlink" href="#hyperlink" title="Permanent link">#</a>
</summary>
Creates a hyperlink inside a cell.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="index"><summary class="unimplemented">
#### INDEX
<code>__INDEX__(reference, row, column)</code>
<a class="headerlink" href="#index" title="Permanent link">#</a>
</summary>
Returns the content of a cell, specified by row and column offset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="indirect"><summary class="unimplemented">
#### INDIRECT
<code>__INDIRECT__(cell_reference_as_string)</code>
<a class="headerlink" href="#indirect" title="Permanent link">#</a>
</summary>
Returns a cell reference specified by a string.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="lookup"><summary class="unimplemented">
#### LOOKUP
<code>__LOOKUP__(search_key, search_range_or_search_result_array, result_range=None)</code>
<a class="headerlink" href="#lookup" title="Permanent link">#</a>
</summary>
Looks through a row or column for a key and returns the value of the cell in a result range located in the same position as the search row or column.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="match"><summary class="unimplemented">
#### MATCH
<code>__MATCH__(search_key, range, search_type)</code>
<a class="headerlink" href="#match" title="Permanent link">#</a>
</summary>
Returns the relative position of an item in a range that matches a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="offset"><summary class="unimplemented">
#### OFFSET
<code>__OFFSET__(cell_reference, offset_rows, offset_columns, height, width)</code>
<a class="headerlink" href="#offset" title="Permanent link">#</a>
</summary>
Returns a range reference shifted a specified number of rows and columns from a starting cell reference.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="row"><summary class="unimplemented">
#### ROW
<code>__ROW__(cell_reference)</code>
<a class="headerlink" href="#row" title="Permanent link">#</a>
</summary>
Returns the row number of a specified cell.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="rows"><summary class="unimplemented">
#### ROWS
<code>__ROWS__(range)</code>
<a class="headerlink" href="#rows" title="Permanent link">#</a>
</summary>
Returns the number of rows in a specified array or range.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="self_hyperlink"><summary >
#### SELF_HYPERLINK
<code>__SELF_HYPERLINK__(label=None, page=None, **kwargs)</code>
<a class="headerlink" href="#self_hyperlink" title="Permanent link">#</a>
</summary>
Creates a link to the current document.  All parameters are optional.

The returned string is in URL format, optionally preceded by a label and a space
(the format expected for Grist Text columns with the HyperLink option enabled).

A numeric page number can be supplied, which will create a link to the
specified page.  To find the numeric page number you need, visit a page
and examine its URL for a `/p/NN` part.

Any number of arguments of the form `LinkKey_NAME` may be provided, to set
`user.LinkKey.NAME` values that will be available in access rules.  For example,
if a rule allows users to view rows when `user.LinkKey.Code == rec.Code`,
we might want to create links with `SELF_HYPERLINK(LinkKey_Code=$Code)`.


```python
>>> SELF_HYPERLINK()
u'https://docs.getgrist.com/sbaltsirg/Example'
```

```python
>>> SELF_HYPERLINK(label='doc')
u'doc https://docs.getgrist.com/sbaltsirg/Example'
```

```python
>>> SELF_HYPERLINK(page=2)
u'https://docs.getgrist.com/sbaltsirg/Example/p/2'
```

```python
>>> SELF_HYPERLINK(LinkKey_Code='X1234')
u'https://docs.getgrist.com/sbaltsirg/Example?Code_=X1234'
```

```python
>>> SELF_HYPERLINK(label='order', page=3, LinkKey_Code='X1234', LinkKey_Name='Bi Ngo')
u'order https://docs.getgrist.com/sbaltsirg/Example/p/3?Code_=X1234&Name_=Bi+Ngo'
```

```python
>>> SELF_HYPERLINK(Linky_Link='Link')
Traceback (most recent call last):
...
TypeError: unexpected keyword argument 'Linky_Link' (not of form LinkKey_NAME)
```

</details>
<details id="vlookup"><summary >
#### VLOOKUP
<code>__VLOOKUP__(table, **field_value_pairs)</code>
<a class="headerlink" href="#vlookup" title="Permanent link">#</a>
</summary>
Vertical lookup. Searches the given table for a record matching the given `field=value`
arguments. If multiple records match, returns one of them. If none match, returns the special
empty record.

The returned object is a record whose fields are available using `.field` syntax. For example,
`VLOOKUP(Employees, EmployeeID=$EmpID).Salary`.

Note that `VLOOKUP` isn't commonly needed in Grist, since [Reference columns](col-refs.md) are the
best way to link data between tables, and allow simple efficient usage such as `$Person.Age`.

`VLOOKUP` is exactly quivalent to `table.lookupOne(**field_value_pairs)`. See
[lookupOne](#lookupone).

For example:
```
VLOOKUP(People, First_Name="Lewis", Last_Name="Carroll")
VLOOKUP(People, First_Name="Lewis", Last_Name="Carroll").Age
```
</details>
### Math
<details id="abs"><summary >
#### ABS
<code>__ABS__(value)</code>
<a class="headerlink" href="#abs" title="Permanent link">#</a>
</summary>
Returns the absolute value of a number.


```python
>>> ABS(2)
2
```

```python
>>> ABS(-2)
2
```

```python
>>> ABS(-4)
4
```

</details>
<details id="acos"><summary >
#### ACOS
<code>__ACOS__(value)</code>
<a class="headerlink" href="#acos" title="Permanent link">#</a>
</summary>
Returns the inverse cosine of a value, in radians.


```python
>>> round(ACOS(-0.5), 9)
2.094395102
```

```python
>>> round(ACOS(-0.5)*180/PI(), 10)
120.0
```

</details>
<details id="acosh"><summary >
#### ACOSH
<code>__ACOSH__(value)</code>
<a class="headerlink" href="#acosh" title="Permanent link">#</a>
</summary>
Returns the inverse hyperbolic cosine of a number.


```python
>>> ACOSH(1)
0.0
```

```python
>>> round(ACOSH(10), 7)
2.9932228
```

</details>
<details id="arabic"><summary >
#### ARABIC
<code>__ARABIC__(roman_numeral)</code>
<a class="headerlink" href="#arabic" title="Permanent link">#</a>
</summary>
Computes the value of a Roman numeral.


```python
>>> ARABIC("LVII")
57
```

```python
>>> ARABIC('mcmxii')
1912
```

</details>
<details id="asin"><summary >
#### ASIN
<code>__ASIN__(value)</code>
<a class="headerlink" href="#asin" title="Permanent link">#</a>
</summary>
Returns the inverse sine of a value, in radians.


```python
>>> round(ASIN(-0.5), 9)
-0.523598776
```

```python
>>> round(ASIN(-0.5)*180/PI(), 10)
-30.0
```

```python
>>> round(DEGREES(ASIN(-0.5)), 10)
-30.0
```

</details>
<details id="asinh"><summary >
#### ASINH
<code>__ASINH__(value)</code>
<a class="headerlink" href="#asinh" title="Permanent link">#</a>
</summary>
Returns the inverse hyperbolic sine of a number.


```python
>>> round(ASINH(-2.5), 9)
-1.647231146
```

```python
>>> round(ASINH(10), 9)
2.99822295
```

</details>
<details id="atan"><summary >
#### ATAN
<code>__ATAN__(value)</code>
<a class="headerlink" href="#atan" title="Permanent link">#</a>
</summary>
Returns the inverse tangent of a value, in radians.


```python
>>> round(ATAN(1), 9)
0.785398163
```

```python
>>> ATAN(1)*180/PI()
45.0
```

```python
>>> DEGREES(ATAN(1))
45.0
```

</details>
<details id="atan2"><summary >
#### ATAN2
<code>__ATAN2__(x, y)</code>
<a class="headerlink" href="#atan2" title="Permanent link">#</a>
</summary>
Returns the angle between the x-axis and a line segment from the origin (0,0) to specified
coordinate pair (`x`,`y`), in radians.


```python
>>> round(ATAN2(1, 1), 9)
0.785398163
```

```python
>>> round(ATAN2(-1, -1), 9)
-2.35619449
```

```python
>>> ATAN2(-1, -1)*180/PI()
-135.0
```

```python
>>> DEGREES(ATAN2(-1, -1))
-135.0
```

```python
>>> round(ATAN2(1,2), 9)
1.107148718
```

</details>
<details id="atanh"><summary >
#### ATANH
<code>__ATANH__(value)</code>
<a class="headerlink" href="#atanh" title="Permanent link">#</a>
</summary>
Returns the inverse hyperbolic tangent of a number.


```python
>>> round(ATANH(0.76159416), 9)
1.00000001
```

```python
>>> round(ATANH(-0.1), 9)
-0.100335348
```

</details>
<details id="ceiling"><summary >
#### CEILING
<code>__CEILING__(value, factor=1)</code>
<a class="headerlink" href="#ceiling" title="Permanent link">#</a>
</summary>
Rounds a number up to the nearest multiple of factor, or the nearest integer if the factor is
omitted or 1.


```python
>>> CEILING(2.5, 1)
3
```

```python
>>> CEILING(-2.5, -2)
-4
```

```python
>>> CEILING(-2.5, 2)
-2
```

```python
>>> CEILING(1.5, 0.1)
1.5
```

```python
>>> CEILING(0.234, 0.01)
0.24
```

</details>
<details id="combin"><summary >
#### COMBIN
<code>__COMBIN__(n, k)</code>
<a class="headerlink" href="#combin" title="Permanent link">#</a>
</summary>
Returns the number of ways to choose some number of objects from a pool of a given size of
objects.


```python
>>> COMBIN(8,2)
28
```

```python
>>> COMBIN(4,2)
6
```

```python
>>> COMBIN(10,7)
120
```

</details>
<details id="cos"><summary >
#### COS
<code>__COS__(angle)</code>
<a class="headerlink" href="#cos" title="Permanent link">#</a>
</summary>
Returns the cosine of an angle provided in radians.


```python
>>> round(COS(1.047), 7)
0.5001711
```

```python
>>> round(COS(60*PI()/180), 10)
0.5
```

```python
>>> round(COS(RADIANS(60)), 10)
0.5
```

</details>
<details id="cosh"><summary >
#### COSH
<code>__COSH__(value)</code>
<a class="headerlink" href="#cosh" title="Permanent link">#</a>
</summary>
Returns the hyperbolic cosine of any real number.


```python
>>> round(COSH(4), 6)
27.308233
```

```python
>>> round(COSH(EXP(1)), 7)
7.6101251
```

</details>
<details id="degrees"><summary >
#### DEGREES
<code>__DEGREES__(angle)</code>
<a class="headerlink" href="#degrees" title="Permanent link">#</a>
</summary>
Converts an angle value in radians to degrees.


```python
>>> round(DEGREES(ACOS(-0.5)), 10)
120.0
```

```python
>>> DEGREES(PI())
180.0
```

</details>
<details id="even"><summary >
#### EVEN
<code>__EVEN__(value)</code>
<a class="headerlink" href="#even" title="Permanent link">#</a>
</summary>
Rounds a number up to the nearest even integer, rounding away from zero.


```python
>>> EVEN(1.5)
2
```

```python
>>> EVEN(3)
4
```

```python
>>> EVEN(2)
2
```

```python
>>> EVEN(-1)
-2
```

</details>
<details id="exp"><summary >
#### EXP
<code>__EXP__(exponent)</code>
<a class="headerlink" href="#exp" title="Permanent link">#</a>
</summary>
Returns Euler's number, e (~2.718) raised to a power.


```python
>>> round(EXP(1), 8)
2.71828183
```

```python
>>> round(EXP(2), 7)
7.3890561
```

</details>
<details id="fact"><summary >
#### FACT
<code>__FACT__(value)</code>
<a class="headerlink" href="#fact" title="Permanent link">#</a>
</summary>
Returns the factorial of a number.


```python
>>> FACT(5)
120
```

```python
>>> FACT(1.9)
1
```

```python
>>> FACT(0)
1
```

```python
>>> FACT(1)
1
```

```python
>>> FACT(-1)
Traceback (most recent call last):
  ...
ValueError: factorial() not defined for negative values
```

</details>
<details id="factdouble"><summary >
#### FACTDOUBLE
<code>__FACTDOUBLE__(value)</code>
<a class="headerlink" href="#factdouble" title="Permanent link">#</a>
</summary>
Returns the "double factorial" of a number.


```python
>>> FACTDOUBLE(6)
48
```

```python
>>> FACTDOUBLE(7)
105
```

```python
>>> FACTDOUBLE(3)
3
```

```python
>>> FACTDOUBLE(4)
8
```

</details>
<details id="floor"><summary >
#### FLOOR
<code>__FLOOR__(value, factor=1)</code>
<a class="headerlink" href="#floor" title="Permanent link">#</a>
</summary>
Rounds a number down to the nearest integer multiple of specified significance.


```python
>>> FLOOR(3.7,2)
2
```

```python
>>> FLOOR(-2.5,-2)
-2
```

```python
>>> FLOOR(2.5,-2)
Traceback (most recent call last):
  ...
ValueError: factor argument invalid
```

```python
>>> FLOOR(1.58,0.1)
1.5
```

```python
>>> FLOOR(0.234,0.01)
0.23
```

</details>
<details id="gcd"><summary >
#### GCD
<code>__GCD__(value1, *more_values)</code>
<a class="headerlink" href="#gcd" title="Permanent link">#</a>
</summary>
Returns the greatest common divisor of one or more integers.


```python
>>> GCD(5, 2)
1
```

```python
>>> GCD(24, 36)
12
```

```python
>>> GCD(7, 1)
1
```

```python
>>> GCD(5, 0)
5
```

```python
>>> GCD(0, 5)
5
```

```python
>>> GCD(5)
5
```

```python
>>> GCD(14, 42, 21)
7
```

</details>
<details id="int"><summary >
#### INT
<code>__INT__(value)</code>
<a class="headerlink" href="#int" title="Permanent link">#</a>
</summary>
Rounds a number down to the nearest integer that is less than or equal to it.


```python
>>> INT(8.9)
8
```

```python
>>> INT(-8.9)
-9
```

```python
>>> 19.5-INT(19.5)
0.5
```

</details>
<details id="lcm"><summary >
#### LCM
<code>__LCM__(value1, *more_values)</code>
<a class="headerlink" href="#lcm" title="Permanent link">#</a>
</summary>
Returns the least common multiple of one or more integers.


```python
>>> LCM(5, 2)
10
```

```python
>>> LCM(24, 36)
72
```

```python
>>> LCM(0, 5)
0
```

```python
>>> LCM(5)
5
```

```python
>>> LCM(10, 100)
100
```

```python
>>> LCM(12, 18)
36
```

```python
>>> LCM(12, 18, 24)
72
```

</details>
<details id="ln"><summary >
#### LN
<code>__LN__(value)</code>
<a class="headerlink" href="#ln" title="Permanent link">#</a>
</summary>
Returns the the logarithm of a number, base e (Euler's number).


```python
>>> round(LN(86), 7)
4.4543473
```

```python
>>> round(LN(2.7182818), 7)
1.0
```

```python
>>> round(LN(EXP(3)), 10)
3.0
```

</details>
<details id="log"><summary >
#### LOG
<code>__LOG__(value, base=10)</code>
<a class="headerlink" href="#log" title="Permanent link">#</a>
</summary>
Returns the the logarithm of a number given a base.


```python
>>> LOG(10)
1.0
```

```python
>>> LOG(8, 2)
3.0
```

```python
>>> round(LOG(86, 2.7182818), 7)
4.4543473
```

</details>
<details id="log10"><summary >
#### LOG10
<code>__LOG10__(value)</code>
<a class="headerlink" href="#log10" title="Permanent link">#</a>
</summary>
Returns the the logarithm of a number, base 10.


```python
>>> round(LOG10(86), 9)
1.934498451
```

```python
>>> LOG10(10)
1.0
```

```python
>>> LOG10(100000)
5.0
```

```python
>>> LOG10(10**5)
5.0
```

</details>
<details id="mod"><summary >
#### MOD
<code>__MOD__(dividend, divisor)</code>
<a class="headerlink" href="#mod" title="Permanent link">#</a>
</summary>
Returns the result of the modulo operator, the remainder after a division operation.


```python
>>> MOD(3, 2)
1
```

```python
>>> MOD(-3, 2)
1
```

```python
>>> MOD(3, -2)
-1
```

```python
>>> MOD(-3, -2)
-1
```

</details>
<details id="mround"><summary >
#### MROUND
<code>__MROUND__(value, factor)</code>
<a class="headerlink" href="#mround" title="Permanent link">#</a>
</summary>
Rounds one number to the nearest integer multiple of another.


```python
>>> MROUND(10, 3)
9
```

```python
>>> MROUND(-10, -3)
-9
```

```python
>>> round(MROUND(1.3, 0.2), 10)
1.4
```

```python
>>> MROUND(5, -2)
Traceback (most recent call last):
  ...
ValueError: factor argument invalid
```

</details>
<details id="multinomial"><summary >
#### MULTINOMIAL
<code>__MULTINOMIAL__(value1, *more_values)</code>
<a class="headerlink" href="#multinomial" title="Permanent link">#</a>
</summary>
Returns the factorial of the sum of values divided by the product of the values' factorials.


```python
>>> MULTINOMIAL(2, 3, 4)
1260
```

```python
>>> MULTINOMIAL(3)
1
```

```python
>>> MULTINOMIAL(1,2,3)
60
```

```python
>>> MULTINOMIAL(0,2,4,6)
13860
```

</details>
<details id="odd"><summary >
#### ODD
<code>__ODD__(value)</code>
<a class="headerlink" href="#odd" title="Permanent link">#</a>
</summary>
Rounds a number up to the nearest odd integer.


```python
>>> ODD(1.5)
3
```

```python
>>> ODD(3)
3
```

```python
>>> ODD(2)
3
```

```python
>>> ODD(-1)
-1
```

```python
>>> ODD(-2)
-3
```

</details>
<details id="pi"><summary >
#### PI
<code>__PI__()</code>
<a class="headerlink" href="#pi" title="Permanent link">#</a>
</summary>
Returns the value of Pi to 14 decimal places.


```python
>>> round(PI(), 9)
3.141592654
```

```python
>>> round(PI()/2, 9)
1.570796327
```

```python
>>> round(PI()*9, 8)
28.27433388
```

</details>
<details id="power"><summary >
#### POWER
<code>__POWER__(base, exponent)</code>
<a class="headerlink" href="#power" title="Permanent link">#</a>
</summary>
Returns a number raised to a power.


```python
>>> POWER(5,2)
25.0
```

```python
>>> round(POWER(98.6,3.2), 3)
2401077.222
```

```python
>>> round(POWER(4,5.0/4), 9)
5.656854249
```

</details>
<details id="product"><summary >
#### PRODUCT
<code>__PRODUCT__(factor1, *more_factors)</code>
<a class="headerlink" href="#product" title="Permanent link">#</a>
</summary>
Returns the result of multiplying a series of numbers together. Each argument may be a number or
an array.


```python
>>> PRODUCT([5,15,30])
2250
```

```python
>>> PRODUCT([5,15,30], 2)
4500
```

```python
>>> PRODUCT(5,15,[30],[2])
4500
```
</details>
<details id="quotient"><summary >
#### QUOTIENT
<code>__QUOTIENT__(dividend, divisor)</code>
<a class="headerlink" href="#quotient" title="Permanent link">#</a>
</summary>
Returns one number divided by another, without the remainder.


```python
>>> QUOTIENT(5, 2)
2
```

```python
>>> QUOTIENT(4.5, 3.1)
1
```

```python
>>> QUOTIENT(-10, 3)
-3
```

</details>
<details id="radians"><summary >
#### RADIANS
<code>__RADIANS__(angle)</code>
<a class="headerlink" href="#radians" title="Permanent link">#</a>
</summary>
Converts an angle value in degrees to radians.


```python
>>> round(RADIANS(270), 6)
4.712389
```

</details>
<details id="rand"><summary >
#### RAND
<code>__RAND__()</code>
<a class="headerlink" href="#rand" title="Permanent link">#</a>
</summary>
Returns a random number between 0 inclusive and 1 exclusive.
</details>
<details id="randbetween"><summary >
#### RANDBETWEEN
<code>__RANDBETWEEN__(low, high)</code>
<a class="headerlink" href="#randbetween" title="Permanent link">#</a>
</summary>
Returns a uniformly random integer between two values, inclusive.
</details>
<details id="roman"><summary >
#### ROMAN
<code>__ROMAN__(number, form_unused=None)</code>
<a class="headerlink" href="#roman" title="Permanent link">#</a>
</summary>
Formats a number in Roman numerals. The second argument is ignored in this implementation.


```python
>>> ROMAN(499,0)
'CDXCIX'
```

```python
>>> ROMAN(499.2,0)
'CDXCIX'
```

```python
>>> ROMAN(57)
'LVII'
```

```python
>>> ROMAN(1912)
'MCMXII'
```

</details>
<details id="round"><summary >
#### ROUND
<code>__ROUND__(value, places=0)</code>
<a class="headerlink" href="#round" title="Permanent link">#</a>
</summary>
Rounds a number to a certain number of decimal places,
by default to the nearest whole number if the number of places is not given.

Rounds away from zero ('up' for positive numbers)
in the case of a tie, i.e. when the last digit is 5.


```python
>>> ROUND(1.4)
1.0
```

```python
>>> ROUND(1.5)
2.0
```

```python
>>> ROUND(2.5)
3.0
```

```python
>>> ROUND(-2.5)
-3.0
```

```python
>>> ROUND(2.15, 1)
2.2
```

```python
>>> ROUND(-1.475, 2)
-1.48
```

```python
>>> ROUND(21.5, -1)
20.0
```

```python
>>> ROUND(626.3,-3)
1000.0
```

```python
>>> ROUND(1.98,-1)
0.0
```

```python
>>> ROUND(-50.55,-2)
-100.0
```

```python
>>> ROUND(0)
0.0
```

</details>
<details id="rounddown"><summary >
#### ROUNDDOWN
<code>__ROUNDDOWN__(value, places=0)</code>
<a class="headerlink" href="#rounddown" title="Permanent link">#</a>
</summary>
Rounds a number to a certain number of decimal places, always rounding down towards zero.


```python
>>> ROUNDDOWN(3.2, 0)
3
```

```python
>>> ROUNDDOWN(76.9,0)
76
```

```python
>>> ROUNDDOWN(3.14159, 3)
3.141
```

```python
>>> ROUNDDOWN(-3.14159, 1)
-3.1
```

```python
>>> ROUNDDOWN(31415.92654, -2)
31400
```

</details>
<details id="roundup"><summary >
#### ROUNDUP
<code>__ROUNDUP__(value, places=0)</code>
<a class="headerlink" href="#roundup" title="Permanent link">#</a>
</summary>
Rounds a number to a certain number of decimal places, always rounding up away from zero.


```python
>>> ROUNDUP(3.2,0)
4
```

```python
>>> ROUNDUP(76.9,0)
77
```

```python
>>> ROUNDUP(3.14159, 3)
3.142
```

```python
>>> ROUNDUP(-3.14159, 1)
-3.2
```

```python
>>> ROUNDUP(31415.92654, -2)
31500
```

</details>
<details id="seriessum"><summary >
#### SERIESSUM
<code>__SERIESSUM__(x, n, m, a)</code>
<a class="headerlink" href="#seriessum" title="Permanent link">#</a>
</summary>
Given parameters x, n, m, and a, returns the power series sum a_1*x^n + a_2*x^(n+m)
+ ... + a_i*x^(n+(i-1)m), where i is the number of entries in range `a`.


```python
>>> SERIESSUM(1,0,1,1)
1
```

```python
>>> SERIESSUM(2,1,0,[1,2,3])
12
```

```python
>>> SERIESSUM(-3,1,1,[2,4,6])
-132
```

```python
>>> round(SERIESSUM(PI()/4,0,2,[1,-1./FACT(2),1./FACT(4),-1./FACT(6)]), 6)
0.707103
```

</details>
<details id="sign"><summary >
#### SIGN
<code>__SIGN__(value)</code>
<a class="headerlink" href="#sign" title="Permanent link">#</a>
</summary>
Given an input number, returns `-1` if it is negative, `1` if positive, and `0` if it is zero.


```python
>>> SIGN(10)
1
```

```python
>>> SIGN(4.0-4.0)
0
```

```python
>>> SIGN(-0.00001)
-1
```

</details>
<details id="sin"><summary >
#### SIN
<code>__SIN__(angle)</code>
<a class="headerlink" href="#sin" title="Permanent link">#</a>
</summary>
Returns the sine of an angle provided in radians.


```python
>>> round(SIN(PI()), 10)
0.0
```

```python
>>> SIN(PI()/2)
1.0
```

```python
>>> round(SIN(30*PI()/180), 10)
0.5
```

```python
>>> round(SIN(RADIANS(30)), 10)
0.5
```

</details>
<details id="sinh"><summary >
#### SINH
<code>__SINH__(value)</code>
<a class="headerlink" href="#sinh" title="Permanent link">#</a>
</summary>
Returns the hyperbolic sine of any real number.


```python
>>> round(2.868*SINH(0.0342*1.03), 7)
0.1010491
```

</details>
<details id="sqrt"><summary >
#### SQRT
<code>__SQRT__(value)</code>
<a class="headerlink" href="#sqrt" title="Permanent link">#</a>
</summary>
Returns the positive square root of a positive number.


```python
>>> SQRT(16)
4.0
```

```python
>>> SQRT(-16)
Traceback (most recent call last):
  ...
ValueError: math domain error
```

```python
>>> SQRT(ABS(-16))
4.0
```

</details>
<details id="sqrtpi"><summary >
#### SQRTPI
<code>__SQRTPI__(value)</code>
<a class="headerlink" href="#sqrtpi" title="Permanent link">#</a>
</summary>
Returns the positive square root of the product of Pi and the given positive number.


```python
>>> round(SQRTPI(1), 6)
1.772454
```

```python
>>> round(SQRTPI(2), 6)
2.506628
```

</details>
<details id="subtotal"><summary class="unimplemented">
#### SUBTOTAL
<code>__SUBTOTAL__(function_code, range1, range2)</code>
<a class="headerlink" href="#subtotal" title="Permanent link">#</a>
</summary>
Returns a subtotal for a vertical range of cells using a specified aggregation function.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="sum"><summary >
#### SUM
<code>__SUM__(value1, *more_values)</code>
<a class="headerlink" href="#sum" title="Permanent link">#</a>
</summary>
Returns the sum of a series of numbers. Each argument may be a number or an array.
Non-numeric values are ignored.


```python
>>> SUM([5,15,30])
50
```

```python
>>> SUM([5.,15,30], 2)
52.0
```

```python
>>> SUM(5,15,[30],[2])
52
```
</details>
<details id="sumif"><summary class="unimplemented">
#### SUMIF
<code>__SUMIF__(records, criterion, sum_range)</code>
<a class="headerlink" href="#sumif" title="Permanent link">#</a>
</summary>
Returns a conditional sum across a range.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="sumifs"><summary class="unimplemented">
#### SUMIFS
<code>__SUMIFS__(sum_range, criteria_range1, criterion1, *args)</code>
<a class="headerlink" href="#sumifs" title="Permanent link">#</a>
</summary>
Returns the sum of a range depending on multiple criteria.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="sumproduct"><summary >
#### SUMPRODUCT
<code>__SUMPRODUCT__(array1, *more_arrays)</code>
<a class="headerlink" href="#sumproduct" title="Permanent link">#</a>
</summary>
Multiplies corresponding components in two equally-sized arrays,
and returns the sum of those products.


```python
>>> SUMPRODUCT([3,8,1,4,6,9], [2,6,5,7,7,3])
156
```

```python
>>> SUMPRODUCT([], [], [])
0
```

```python
>>> SUMPRODUCT([-0.25], [-2], [-3])
-1.5
```

```python
>>> SUMPRODUCT([-0.25, -0.25], [-2, -2], [-3, -3])
-3.0
```

</details>
<details id="sumsq"><summary class="unimplemented">
#### SUMSQ
<code>__SUMSQ__(value1, value2)</code>
<a class="headerlink" href="#sumsq" title="Permanent link">#</a>
</summary>
Returns the sum of the squares of a series of numbers and/or cells.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="tan"><summary >
#### TAN
<code>__TAN__(angle)</code>
<a class="headerlink" href="#tan" title="Permanent link">#</a>
</summary>
Returns the tangent of an angle provided in radians.


```python
>>> round(TAN(0.785), 8)
0.99920399
```

```python
>>> round(TAN(45*PI()/180), 10)
1.0
```

```python
>>> round(TAN(RADIANS(45)), 10)
1.0
```

</details>
<details id="tanh"><summary >
#### TANH
<code>__TANH__(value)</code>
<a class="headerlink" href="#tanh" title="Permanent link">#</a>
</summary>
Returns the hyperbolic tangent of any real number.


```python
>>> round(TANH(-2), 6)
-0.964028
```

```python
>>> TANH(0)
0.0
```

```python
>>> round(TANH(0.5), 6)
0.462117
```

</details>
<details id="trunc"><summary >
#### TRUNC
<code>__TRUNC__(value, places=0)</code>
<a class="headerlink" href="#trunc" title="Permanent link">#</a>
</summary>
Truncates a number to a certain number of significant digits by omitting less significant
digits.


```python
>>> TRUNC(8.9)
8
```

```python
>>> TRUNC(-8.9)
-8
```

```python
>>> TRUNC(0.45)
0
```

</details>
<details id="uuid"><summary >
#### UUID
<code>__UUID__()</code>
<a class="headerlink" href="#uuid" title="Permanent link">#</a>
</summary>
Generate a random UUID-formatted string identifier.
Since UUID() produces a different value each time it's called, it is best to use it in
[trigger formula](formulas.md#trigger-formulas) for new records.
This would only calculate UUID() once and freeze the calculated value. By contrast, a regular formula
may get recalculated any time the document is reloaded, producing a different value for UUID() each time.
</details>
### Schedule
<details id="schedule"><summary >
#### SCHEDULE
<code>__SCHEDULE__(schedule, start=None, count=10, end=None)</code>
<a class="headerlink" href="#schedule" title="Permanent link">#</a>
</summary>
Returns the list of `datetime` objects generated according to the `schedule` string. Starts at
`start`, which defaults to NOW(). Generates at most `count` results (10 by default). If `end` is
given, stops there.

The schedule has the format "INTERVAL: SLOTS, ...". For example:

    annual: Jan-15, Apr-15, Jul-15  -- Three times a year on given dates at midnight.
    annual: 1/15, 4/15, 7/15        -- Same as above.
    monthly: /1 2pm, /15 2pm        -- The 1st and the 15th of each month, at 2pm.
    3-months: /10, +1m /20           -- Every 3 months on the 10th of month 1, 20th of month 2.
    weekly: Mo 9am, Tu 9am, Fr 2pm  -- Three times a week at specified times.
    2-weeks: Mo, +1w Tu             -- Every 2 weeks on Monday of week 1, Tuesday of week 2.
    daily: 07:30, 21:00             -- Twice a day at specified times.
    2-day: 12am, 4pm, +1d 8am       -- Three times every two days, evenly spaced.
    hourly: :15, :45                -- 15 minutes before and after each hour.
    4-hour: :00, 1:20, 2:40         -- Three times every 4 hours, evenly spaced.
    10-minute: +0s                  -- Every 10 minutes on the minute.

INTERVAL must be either of the form `N-unit` where `N` is a number and `unit` is one of `year`,
`month`, `week`, `day`, `hour`; or one of the aliases: `annual`, `monthly`, `weekly`, `daily`,
`hourly`, which mean `1-year`, `1-month`, etc.

SLOTS support the following units:

    `Jan-15` or `1/15`    -- Month and day of the month; available when INTERVAL is year-based.
    `/15`                 -- Day of the month, available when INTERVAL is month-based.
    `Mon`, `Mo`, `Friday` -- Day of the week (or abbreviation), when INTERVAL is week-based.
    10am, 1:30pm, 15:45   -- Time of day, available for day-based or longer intervals.
    :45, :00              -- Minutes of the hour, available when INTERVAL is hour-based.
    +1d, +15d             -- How many days to add to start of INTERVAL.
    +1w                   -- How many weeks to add to start of INTERVAL.
    +1m                   -- How many months to add to start of INTERVAL.

The SLOTS are always relative to the INTERVAL rather than to `start`. Week-based intervals start
on Sunday. E.g. `weekly: +1d, +4d` is the same as `weekly: Mon, Thu`, and generates times on
Mondays and Thursdays regardless of `start`.

The first generated time is determined by the *unit* of the INTERVAL without regard to the
multiple. E.g. both "2-week: Mon" and "3-week: Mon" start on the first Monday after `start`, and
then generate either every second or every third Monday after that. Similarly, `24-hour: :00`
starts with the first top-of-the-hour after `start` (not with midnight), and then repeats every
24 hours. To start with the midnight after `start`, use `daily: 0:00`.

For interval units of a day or longer, if time-of-day is not specified, it defaults to midnight.

The time zone of `start` determines the time zone of the generated times.


```python
>>> def show(dates): return [d.strftime("%Y-%m-%d %H:%M") for d in dates]

```

```python
>>> start = datetime(2018, 9, 4, 14, 0);   # 2pm on Tue, Sep 4 2018.

```


```python
>>> show(SCHEDULE('annual: Jan-15, Apr-15, Jul-15, Oct-15', start=start, count=4))
['2018-10-15 00:00', '2019-01-15 00:00', '2019-04-15 00:00', '2019-07-15 00:00']
```


```python
>>> show(SCHEDULE('annual: 1/15, 4/15, 7/15', start=start, count=4))
['2019-01-15 00:00', '2019-04-15 00:00', '2019-07-15 00:00', '2020-01-15 00:00']
```


```python
>>> show(SCHEDULE('monthly: /1 2pm, /15 5pm', start=start, count=4))
['2018-09-15 17:00', '2018-10-01 14:00', '2018-10-15 17:00', '2018-11-01 14:00']
```


```python
>>> show(SCHEDULE('3-months: /10, +1m /20', start=start, count=4))
['2018-09-10 00:00', '2018-10-20 00:00', '2018-12-10 00:00', '2019-01-20 00:00']
```


```python
>>> show(SCHEDULE('weekly: Mo 9am, Tu 9am, Fr 2pm', start=start, count=4))
['2018-09-07 14:00', '2018-09-10 09:00', '2018-09-11 09:00', '2018-09-14 14:00']
```


```python
>>> show(SCHEDULE('2-weeks: Mo, +1w Tu', start=start, count=4))
['2018-09-11 00:00', '2018-09-17 00:00', '2018-09-25 00:00', '2018-10-01 00:00']
```


```python
>>> show(SCHEDULE('daily: 07:30, 21:00', start=start, count=4))
['2018-09-04 21:00', '2018-09-05 07:30', '2018-09-05 21:00', '2018-09-06 07:30']
```


```python
>>> show(SCHEDULE('2-day: 12am, 4pm, +1d 8am', start=start, count=4))
['2018-09-04 16:00', '2018-09-05 08:00', '2018-09-06 00:00', '2018-09-06 16:00']
```


```python
>>> show(SCHEDULE('hourly: :15, :45', start=start, count=4))
['2018-09-04 14:15', '2018-09-04 14:45', '2018-09-04 15:15', '2018-09-04 15:45']
```


```python
>>> show(SCHEDULE('4-hour: :00, +1H :20, +2H :40', start=start, count=4))
['2018-09-04 14:00', '2018-09-04 15:20', '2018-09-04 16:40', '2018-09-04 18:00']
```

</details>
### Stats
<details id="avedev"><summary class="unimplemented">
#### AVEDEV
<code>__AVEDEV__(value1, value2)</code>
<a class="headerlink" href="#avedev" title="Permanent link">#</a>
</summary>
Calculates the average of the magnitudes of deviations of data from a dataset's mean.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="average"><summary >
#### AVERAGE
<code>__AVERAGE__(value, *more_values)</code>
<a class="headerlink" href="#average" title="Permanent link">#</a>
</summary>
Returns the numerical average value in a dataset, ignoring non-numerical values.

Each argument may be a value or an array. Values that are not numbers, including logical
and blank values, and text representations of numbers, are ignored.


```python
>>> AVERAGE([2, -1.0, 11])
4.0
```

```python
>>> AVERAGE([2, -1, 11, "Hello"])
4.0
```

```python
>>> AVERAGE([2, -1, "Hello", DATE(2015,1,1)], True, [False, "123", "", 11])
4.0
```

```python
>>> AVERAGE(False, True)
Traceback (most recent call last):
  ...
ZeroDivisionError: float division by zero
```

</details>
<details id="averagea"><summary >
#### AVERAGEA
<code>__AVERAGEA__(value, *more_values)</code>
<a class="headerlink" href="#averagea" title="Permanent link">#</a>
</summary>
Returns the numerical average value in a dataset, counting non-numerical values as 0.

Each argument may be a value of an array. Values that are not numbers, including dates and text
representations of numbers, are counted as 0 (zero). Logical value of True is counted as 1, and
False as 0.


```python
>>> AVERAGEA([2, -1.0, 11])
4.0
```

```python
>>> AVERAGEA([2, -1, 11, "Hello"])
3.0
```

```python
>>> AVERAGEA([2, -1, "Hello", DATE(2015,1,1)], True, [False, "123", "", 11.5])
1.5
```

```python
>>> AVERAGEA(False, True)
0.5
```

</details>
<details id="averageif"><summary class="unimplemented">
#### AVERAGEIF
<code>__AVERAGEIF__(criteria_range, criterion, average_range=None)</code>
<a class="headerlink" href="#averageif" title="Permanent link">#</a>
</summary>
Returns the average of a range depending on criteria.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="averageifs"><summary class="unimplemented">
#### AVERAGEIFS
<code>__AVERAGEIFS__(average_range, criteria_range1, criterion1, *args)</code>
<a class="headerlink" href="#averageifs" title="Permanent link">#</a>
</summary>
Returns the average of a range depending on multiple criteria.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="average_weighted"><summary >
#### AVERAGE_WEIGHTED
<code>__AVERAGE_WEIGHTED__(pairs)</code>
<a class="headerlink" href="#average_weighted" title="Permanent link">#</a>
</summary>
Given a list of (value, weight) pairs, finds the average of the values weighted by the
corresponding weights. Ignores any pairs with a non-numerical value or weight.

If you have two lists, of values and weights, use the Python built-in zip() function to create a
list of pairs.


```python
>>> AVERAGE_WEIGHTED(((95, .25), (90, .1), ("X", .5), (85, .15), (88, .2), (82, .3), (70, None)))
87.7
```

```python
>>> AVERAGE_WEIGHTED(zip([95, 90, "X", 85, 88, 82, 70], [25, 10, 50, 15, 20, 30, None]))
87.7
```

```python
>>> AVERAGE_WEIGHTED(zip([95, 90, False, 85, 88, 82, 70], [.25, .1, .5, .15, .2, .3, True]))
87.7
```

</details>
<details id="binomdist"><summary class="unimplemented">
#### BINOMDIST
<code>__BINOMDIST__(num_successes, num_trials, prob_success, cumulative)</code>
<a class="headerlink" href="#binomdist" title="Permanent link">#</a>
</summary>
Calculates the probability of drawing a certain number of successes (or a maximum number of
successes) in a certain number of tries given a population of a certain size containing a
certain number of successes, with replacement of draws.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="confidence"><summary class="unimplemented">
#### CONFIDENCE
<code>__CONFIDENCE__(alpha, standard_deviation, pop_size)</code>
<a class="headerlink" href="#confidence" title="Permanent link">#</a>
</summary>
Calculates the width of half the confidence interval for a normal distribution.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="correl"><summary class="unimplemented">
#### CORREL
<code>__CORREL__(data_y, data_x)</code>
<a class="headerlink" href="#correl" title="Permanent link">#</a>
</summary>
Calculates r, the Pearson product-moment correlation coefficient of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="count"><summary >
#### COUNT
<code>__COUNT__(value, *more_values)</code>
<a class="headerlink" href="#count" title="Permanent link">#</a>
</summary>
Returns the count of numerical and date/datetime values in a dataset,
ignoring other types of values.

Each argument may be a value or an array. Values that are not numbers or dates, including logical
and blank values, and text representations of numbers, are ignored.


```python
>>> COUNT([2, -1.0, 11])
3
```

```python
>>> COUNT([2, -1, 11, "Hello"])
3
```

```python
>>> COUNT([DATE(2000, 1, 1), DATE(2000, 1, 2), DATE(2000, 1, 3), "Hello"])
3
```

```python
>>> COUNT([2, -1, "Hello", DATE(2015,1,1)], True, [False, "123", "", 11.5])
4
```

```python
>>> COUNT(False, True)
0
```

</details>
<details id="counta"><summary >
#### COUNTA
<code>__COUNTA__(value, *more_values)</code>
<a class="headerlink" href="#counta" title="Permanent link">#</a>
</summary>
Returns the count of all values in a dataset, including non-numerical values.

Each argument may be a value or an array.


```python
>>> COUNTA([2, -1.0, 11])
3
```

```python
>>> COUNTA([2, -1, 11, "Hello"])
4
```

```python
>>> COUNTA([2, -1, "Hello", DATE(2015,1,1)], True, [False, "123", "", 11.5])
9
```

```python
>>> COUNTA(False, True)
2
```

</details>
<details id="covar"><summary class="unimplemented">
#### COVAR
<code>__COVAR__(data_y, data_x)</code>
<a class="headerlink" href="#covar" title="Permanent link">#</a>
</summary>
Calculates the covariance of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="critbinom"><summary class="unimplemented">
#### CRITBINOM
<code>__CRITBINOM__(num_trials, prob_success, target_prob)</code>
<a class="headerlink" href="#critbinom" title="Permanent link">#</a>
</summary>
Calculates the smallest value for which the cumulative binomial distribution is greater than or equal to a specified criteria.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="devsq"><summary class="unimplemented">
#### DEVSQ
<code>__DEVSQ__(value1, value2)</code>
<a class="headerlink" href="#devsq" title="Permanent link">#</a>
</summary>
Calculates the sum of squares of deviations based on a sample.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="expondist"><summary class="unimplemented">
#### EXPONDIST
<code>__EXPONDIST__(x, lambda_, cumulative)</code>
<a class="headerlink" href="#expondist" title="Permanent link">#</a>
</summary>
Returns the value of the exponential distribution function with a specified lambda at a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="fdist"><summary class="unimplemented">
#### FDIST
<code>__FDIST__(x, degrees_freedom1, degrees_freedom2)</code>
<a class="headerlink" href="#fdist" title="Permanent link">#</a>
</summary>
Calculates the right-tailed F probability distribution (degree of diversity) for two data sets
with given input x. Alternately called Fisher-Snedecor distribution or Snedecor's F
distribution.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="fisher"><summary class="unimplemented">
#### FISHER
<code>__FISHER__(value)</code>
<a class="headerlink" href="#fisher" title="Permanent link">#</a>
</summary>
Returns the Fisher transformation of a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="fisherinv"><summary class="unimplemented">
#### FISHERINV
<code>__FISHERINV__(value)</code>
<a class="headerlink" href="#fisherinv" title="Permanent link">#</a>
</summary>
Returns the inverse Fisher transformation of a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="forecast"><summary class="unimplemented">
#### FORECAST
<code>__FORECAST__(x, data_y, data_x)</code>
<a class="headerlink" href="#forecast" title="Permanent link">#</a>
</summary>
Calculates the expected y-value for a specified x based on a linear regression of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="f_dist"><summary class="unimplemented">
#### F_DIST
<code>__F_DIST__(x, degrees_freedom1, degrees_freedom2, cumulative)</code>
<a class="headerlink" href="#f_dist" title="Permanent link">#</a>
</summary>
Calculates the left-tailed F probability distribution (degree of diversity) for two data sets
with given input x. Alternately called Fisher-Snedecor distribution or Snedecor's F
distribution.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="f_dist_rt"><summary class="unimplemented">
#### F_DIST_RT
<code>__F_DIST_RT__(x, degrees_freedom1, degrees_freedom2)</code>
<a class="headerlink" href="#f_dist_rt" title="Permanent link">#</a>
</summary>
Calculates the right-tailed F probability distribution (degree of diversity) for two data sets
with given input x. Alternately called Fisher-Snedecor distribution or Snedecor's F
distribution.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="geomean"><summary class="unimplemented">
#### GEOMEAN
<code>__GEOMEAN__(value1, value2)</code>
<a class="headerlink" href="#geomean" title="Permanent link">#</a>
</summary>
Calculates the geometric mean of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="harmean"><summary class="unimplemented">
#### HARMEAN
<code>__HARMEAN__(value1, value2)</code>
<a class="headerlink" href="#harmean" title="Permanent link">#</a>
</summary>
Calculates the harmonic mean of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="hypgeomdist"><summary class="unimplemented">
#### HYPGEOMDIST
<code>__HYPGEOMDIST__(num_successes, num_draws, successes_in_pop, pop_size)</code>
<a class="headerlink" href="#hypgeomdist" title="Permanent link">#</a>
</summary>
Calculates the probability of drawing a certain number of successes in a certain number of tries given a population of a certain size containing a certain number of successes, without replacement of draws.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="intercept"><summary class="unimplemented">
#### INTERCEPT
<code>__INTERCEPT__(data_y, data_x)</code>
<a class="headerlink" href="#intercept" title="Permanent link">#</a>
</summary>
Calculates the y-value at which the line resulting from linear regression of a dataset will intersect the y-axis (x=0).

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="kurt"><summary class="unimplemented">
#### KURT
<code>__KURT__(value1, value2)</code>
<a class="headerlink" href="#kurt" title="Permanent link">#</a>
</summary>
Calculates the kurtosis of a dataset, which describes the shape, and in particular the "peakedness" of that dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="large"><summary class="unimplemented">
#### LARGE
<code>__LARGE__(data, n)</code>
<a class="headerlink" href="#large" title="Permanent link">#</a>
</summary>
Returns the nth largest element from a data set, where n is user-defined.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="loginv"><summary class="unimplemented">
#### LOGINV
<code>__LOGINV__(x, mean, standard_deviation)</code>
<a class="headerlink" href="#loginv" title="Permanent link">#</a>
</summary>
Returns the value of the inverse log-normal cumulative distribution with given mean and standard deviation at a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="lognormdist"><summary class="unimplemented">
#### LOGNORMDIST
<code>__LOGNORMDIST__(x, mean, standard_deviation)</code>
<a class="headerlink" href="#lognormdist" title="Permanent link">#</a>
</summary>
Returns the value of the log-normal cumulative distribution with given mean and standard deviation at a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="max"><summary >
#### MAX
<code>__MAX__(value, *more_values)</code>
<a class="headerlink" href="#max" title="Permanent link">#</a>
</summary>
Returns the maximum value in a dataset, ignoring values other than numbers and dates/datetimes.

Each argument may be a value or an array. Values that are not numbers or dates, including logical
and blank values, and text representations of numbers, are ignored. Returns 0 if the arguments
contain no numbers or dates.


```python
>>> MAX([2, -1.5, 11.5])
11.5
```

```python
>>> MAX([2, -1.5, "Hello"], True, [False, "123", "", 11.5])
11.5
```

```python
>>> MAX(True, -123)
-123
```

```python
>>> MAX("123", -123)
-123
```

```python
>>> MAX("Hello", "123", True, False)
0
```

```python
>>> MAX(DATE(2015, 1, 1), DATE(2015, 1, 2))
datetime.date(2015, 1, 2)
```

```python
>>> MAX(DATE(2015, 1, 1), datetime.datetime(2015, 1, 1, 12, 34, 56))
datetime.datetime(2015, 1, 1, 12, 34, 56)
```

```python
>>> MAX(DATE(2015, 1, 2), datetime.datetime(2015, 1, 1, 12, 34, 56))
datetime.date(2015, 1, 2)
```

</details>
<details id="maxa"><summary >
#### MAXA
<code>__MAXA__(value, *more_values)</code>
<a class="headerlink" href="#maxa" title="Permanent link">#</a>
</summary>
Returns the maximum numeric value in a dataset.

Each argument may be a value of an array. Values that are not numbers, including dates and text
representations of numbers, are counted as 0 (zero). Logical value of True is counted as 1, and
False as 0. Returns 0 if the arguments contain no numbers.


```python
>>> MAXA([2, -1.5, 11.5])
11.5
```

```python
>>> MAXA([2, -1.5, "Hello", DATE(2015, 1, 1)], True, [False, "123", "", 11.5])
11.5
```

```python
>>> MAXA(True, -123)
1
```

```python
>>> MAXA("123", -123)
0
```

```python
>>> MAXA("Hello", "123", DATE(2015, 1, 1))
0
```

</details>
<details id="median"><summary >
#### MEDIAN
<code>__MEDIAN__(value, *more_values)</code>
<a class="headerlink" href="#median" title="Permanent link">#</a>
</summary>
Returns the median value in a numeric dataset, ignoring non-numerical values.

Each argument may be a value or an array. Values that are not numbers, including logical
and blank values, and text representations of numbers, are ignored.

Produces an error if the arguments contain no numbers.

The median is the middle number when all values are sorted. So half of the values in the dataset
are less than the median, and half of the values are greater. If there is an even number of
values in the dataset, returns the average of the two numbers in the middle.


```python
>>> MEDIAN(1, 2, 3, 4, 5)
3
```

```python
>>> MEDIAN(3, 5, 1, 4, 2)
3
```

```python
>>> MEDIAN(range(10))
4.5
```

```python
>>> MEDIAN("Hello", "123", DATE(2015, 1, 1), 12.3)
12.3
```

```python
>>> MEDIAN("Hello", "123", DATE(2015, 1, 1))
Traceback (most recent call last):
  ...
ValueError: MEDIAN requires at least one number
```

</details>
<details id="min"><summary >
#### MIN
<code>__MIN__(value, *more_values)</code>
<a class="headerlink" href="#min" title="Permanent link">#</a>
</summary>
Returns the minimum value in a dataset, ignoring values other than numbers and dates/datetimes.

Each argument may be a value or an array. Values that are not numbers or dates, including logical
and blank values, and text representations of numbers, are ignored. Returns 0 if the arguments
contain no numbers or dates.


```python
>>> MIN([2, -1.5, 11.5])
-1.5
```

```python
>>> MIN([2, -1.5, "Hello"], True, [False, "123", "", 11.5])
-1.5
```

```python
>>> MIN(True, 123)
123
```

```python
>>> MIN("-123", 123)
123
```

```python
>>> MIN("Hello", "123", True, False)
0
```

```python
>>> MIN(DATE(2015, 1, 1), DATE(2015, 1, 2))
datetime.date(2015, 1, 1)
```

```python
>>> MIN(DATE(2015, 1, 1), datetime.datetime(2015, 1, 1, 12, 34, 56))
datetime.date(2015, 1, 1)
```

```python
>>> MIN(DATE(2015, 1, 2), datetime.datetime(2015, 1, 1, 12, 34, 56))
datetime.datetime(2015, 1, 1, 12, 34, 56)
```

</details>
<details id="mina"><summary >
#### MINA
<code>__MINA__(value, *more_values)</code>
<a class="headerlink" href="#mina" title="Permanent link">#</a>
</summary>
Returns the minimum numeric value in a dataset.

Each argument may be a value of an array. Values that are not numbers, including dates and text
representations of numbers, are counted as 0 (zero). Logical value of True is counted as 1, and
False as 0. Returns 0 if the arguments contain no numbers.


```python
>>> MINA([2, -1.5, 11.5])
-1.5
```

```python
>>> MINA([2, -1.5, "Hello", DATE(2015, 1, 1)], True, [False, "123", "", 11.5])
-1.5
```

```python
>>> MINA(True, 123)
1
```

```python
>>> MINA("-123", 123)
0
```

```python
>>> MINA("Hello", "123", DATE(2015, 1, 1))
0
```

</details>
<details id="mode"><summary class="unimplemented">
#### MODE
<code>__MODE__(value1, value2)</code>
<a class="headerlink" href="#mode" title="Permanent link">#</a>
</summary>
Returns the most commonly occurring value in a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="negbinomdist"><summary class="unimplemented">
#### NEGBINOMDIST
<code>__NEGBINOMDIST__(num_failures, num_successes, prob_success)</code>
<a class="headerlink" href="#negbinomdist" title="Permanent link">#</a>
</summary>
Calculates the probability of drawing a certain number of failures before a certain number of successes given a probability of success in independent trials.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="normdist"><summary class="unimplemented">
#### NORMDIST
<code>__NORMDIST__(x, mean, standard_deviation, cumulative)</code>
<a class="headerlink" href="#normdist" title="Permanent link">#</a>
</summary>
Returns the value of the normal distribution function (or normal cumulative distribution
function) for a specified value, mean, and standard deviation.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="norminv"><summary class="unimplemented">
#### NORMINV
<code>__NORMINV__(x, mean, standard_deviation)</code>
<a class="headerlink" href="#norminv" title="Permanent link">#</a>
</summary>
Returns the value of the inverse normal distribution function for a specified value, mean, and standard deviation.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="normsdist"><summary class="unimplemented">
#### NORMSDIST
<code>__NORMSDIST__(x)</code>
<a class="headerlink" href="#normsdist" title="Permanent link">#</a>
</summary>
Returns the value of the standard normal cumulative distribution function for a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="normsinv"><summary class="unimplemented">
#### NORMSINV
<code>__NORMSINV__(x)</code>
<a class="headerlink" href="#normsinv" title="Permanent link">#</a>
</summary>
Returns the value of the inverse standard normal distribution function for a specified value.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="pearson"><summary class="unimplemented">
#### PEARSON
<code>__PEARSON__(data_y, data_x)</code>
<a class="headerlink" href="#pearson" title="Permanent link">#</a>
</summary>
Calculates r, the Pearson product-moment correlation coefficient of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="percentile"><summary class="unimplemented">
#### PERCENTILE
<code>__PERCENTILE__(data, percentile)</code>
<a class="headerlink" href="#percentile" title="Permanent link">#</a>
</summary>
Returns the value at a given percentile of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="percentrank"><summary class="unimplemented">
#### PERCENTRANK
<code>__PERCENTRANK__(data, value, significant_digits=None)</code>
<a class="headerlink" href="#percentrank" title="Permanent link">#</a>
</summary>
Returns the percentage rank (percentile) of a specified value in a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="percentrank_exc"><summary class="unimplemented">
#### PERCENTRANK_EXC
<code>__PERCENTRANK_EXC__(data, value, significant_digits=None)</code>
<a class="headerlink" href="#percentrank_exc" title="Permanent link">#</a>
</summary>
Returns the percentage rank (percentile) from 0 to 1 exclusive of a specified value in a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="percentrank_inc"><summary class="unimplemented">
#### PERCENTRANK_INC
<code>__PERCENTRANK_INC__(data, value, significant_digits=None)</code>
<a class="headerlink" href="#percentrank_inc" title="Permanent link">#</a>
</summary>
Returns the percentage rank (percentile) from 0 to 1 inclusive of a specified value in a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="permut"><summary class="unimplemented">
#### PERMUT
<code>__PERMUT__(n, k)</code>
<a class="headerlink" href="#permut" title="Permanent link">#</a>
</summary>
Returns the number of ways to choose some number of objects from a pool of a given size of objects, considering order.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="poisson"><summary class="unimplemented">
#### POISSON
<code>__POISSON__(x, mean, cumulative)</code>
<a class="headerlink" href="#poisson" title="Permanent link">#</a>
</summary>
Returns the value of the Poisson distribution function (or Poisson cumulative distribution
function) for a specified value and mean.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="prob"><summary class="unimplemented">
#### PROB
<code>__PROB__(data, probabilities, low_limit, high_limit=None)</code>
<a class="headerlink" href="#prob" title="Permanent link">#</a>
</summary>
Given a set of values and corresponding probabilities, calculates the probability that a value chosen at random falls between two limits.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="quartile"><summary class="unimplemented">
#### QUARTILE
<code>__QUARTILE__(data, quartile_number)</code>
<a class="headerlink" href="#quartile" title="Permanent link">#</a>
</summary>
Returns a value nearest to a specified quartile of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="rank"><summary class="unimplemented">
#### RANK
<code>__RANK__(value, data, is_ascending=None)</code>
<a class="headerlink" href="#rank" title="Permanent link">#</a>
</summary>
Returns the rank of a specified value in a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="rank_avg"><summary class="unimplemented">
#### RANK_AVG
<code>__RANK_AVG__(value, data, is_ascending=None)</code>
<a class="headerlink" href="#rank_avg" title="Permanent link">#</a>
</summary>
Returns the rank of a specified value in a dataset. If there is more than one entry of the same value in the dataset, the average rank of the entries will be returned.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="rank_eq"><summary class="unimplemented">
#### RANK_EQ
<code>__RANK_EQ__(value, data, is_ascending=None)</code>
<a class="headerlink" href="#rank_eq" title="Permanent link">#</a>
</summary>
Returns the rank of a specified value in a dataset. If there is more than one entry of the same value in the dataset, the top rank of the entries will be returned.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="rsq"><summary class="unimplemented">
#### RSQ
<code>__RSQ__(data_y, data_x)</code>
<a class="headerlink" href="#rsq" title="Permanent link">#</a>
</summary>
Calculates the square of r, the Pearson product-moment correlation coefficient of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="skew"><summary class="unimplemented">
#### SKEW
<code>__SKEW__(value1, value2)</code>
<a class="headerlink" href="#skew" title="Permanent link">#</a>
</summary>
Calculates the skewness of a dataset, which describes the symmetry of that dataset about the mean.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="slope"><summary class="unimplemented">
#### SLOPE
<code>__SLOPE__(data_y, data_x)</code>
<a class="headerlink" href="#slope" title="Permanent link">#</a>
</summary>
Calculates the slope of the line resulting from linear regression of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="small"><summary class="unimplemented">
#### SMALL
<code>__SMALL__(data, n)</code>
<a class="headerlink" href="#small" title="Permanent link">#</a>
</summary>
Returns the nth smallest element from a data set, where n is user-defined.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="standardize"><summary class="unimplemented">
#### STANDARDIZE
<code>__STANDARDIZE__(value, mean, standard_deviation)</code>
<a class="headerlink" href="#standardize" title="Permanent link">#</a>
</summary>
Calculates the normalized equivalent of a random variable given mean and standard deviation of the distribution.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="stdev"><summary >
#### STDEV
<code>__STDEV__(value, *more_values)</code>
<a class="headerlink" href="#stdev" title="Permanent link">#</a>
</summary>
Calculates the standard deviation based on a sample, ignoring non-numerical values.


```python
>>> STDEV([2, 5, 8, 13, 10])
4.277849927241488
```

```python
>>> STDEV([2, 5, 8, 13, 10, True, False, "Test"])
4.277849927241488
```

```python
>>> STDEV([2, 5, 8, 13, 10], 3, 12, 15)
4.810702354423639
```

```python
>>> STDEV([2, 5, 8, 13, 10], [3, 12, 15])
4.810702354423639
```

```python
>>> STDEV([5])
Traceback (most recent call last):
  ...
ZeroDivisionError: float division by zero
```

</details>
<details id="stdeva"><summary >
#### STDEVA
<code>__STDEVA__(value, *more_values)</code>
<a class="headerlink" href="#stdeva" title="Permanent link">#</a>
</summary>
Calculates the standard deviation based on a sample, setting text to the value `0`.


```python
>>> STDEVA([2, 5, 8, 13, 10])
4.277849927241488
```

```python
>>> STDEVA([2, 5, 8, 13, 10, True, False, "Test"])
4.969550137731641
```

```python
>>> STDEVA([2, 5, 8, 13, 10], 1, 0, 0)
4.969550137731641
```

```python
>>> STDEVA([2, 5, 8, 13, 10], [1, 0, 0])
4.969550137731641
```

```python
>>> STDEVA([5])
Traceback (most recent call last):
  ...
ZeroDivisionError: float division by zero
```

</details>
<details id="stdevp"><summary >
#### STDEVP
<code>__STDEVP__(value, *more_values)</code>
<a class="headerlink" href="#stdevp" title="Permanent link">#</a>
</summary>
Calculates the standard deviation based on an entire population, ignoring non-numerical values.


```python
>>> STDEVP([2, 5, 8, 13, 10])
3.8262252939417984
```

```python
>>> STDEVP([2, 5, 8, 13, 10, True, False, "Test"])
3.8262252939417984
```

```python
>>> STDEVP([2, 5, 8, 13, 10], 3, 12, 15)
4.5
```

```python
>>> STDEVP([2, 5, 8, 13, 10], [3, 12, 15])
4.5
```

```python
>>> STDEVP([5])
0.0
```

</details>
<details id="stdevpa"><summary >
#### STDEVPA
<code>__STDEVPA__(value, *more_values)</code>
<a class="headerlink" href="#stdevpa" title="Permanent link">#</a>
</summary>
Calculates the standard deviation based on an entire population, setting text to the value `0`.


```python
>>> STDEVPA([2, 5, 8, 13, 10])
3.8262252939417984
```

```python
>>> STDEVPA([2, 5, 8, 13, 10, True, False, "Test"])
4.648588495446763
```

```python
>>> STDEVPA([2, 5, 8, 13, 10], 1, 0, 0)
4.648588495446763
```

```python
>>> STDEVPA([2, 5, 8, 13, 10], [1, 0, 0])
4.648588495446763
```

```python
>>> STDEVPA([5])
0.0
```

</details>
<details id="steyx"><summary class="unimplemented">
#### STEYX
<code>__STEYX__(data_y, data_x)</code>
<a class="headerlink" href="#steyx" title="Permanent link">#</a>
</summary>
Calculates the standard error of the predicted y-value for each x in the regression of a dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="tdist"><summary class="unimplemented">
#### TDIST
<code>__TDIST__(x, degrees_freedom, tails)</code>
<a class="headerlink" href="#tdist" title="Permanent link">#</a>
</summary>
Calculates the probability for Student's t-distribution with a given input (x).

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="tinv"><summary class="unimplemented">
#### TINV
<code>__TINV__(probability, degrees_freedom)</code>
<a class="headerlink" href="#tinv" title="Permanent link">#</a>
</summary>
Calculates the inverse of the two-tailed TDIST function.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="trimmean"><summary class="unimplemented">
#### TRIMMEAN
<code>__TRIMMEAN__(data, exclude_proportion)</code>
<a class="headerlink" href="#trimmean" title="Permanent link">#</a>
</summary>
Calculates the mean of a dataset excluding some proportion of data from the high and low ends of the dataset.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="ttest"><summary class="unimplemented">
#### TTEST
<code>__TTEST__(range1, range2, tails, type)</code>
<a class="headerlink" href="#ttest" title="Permanent link">#</a>
</summary>
Returns the probability associated with t-test. Determines whether two samples are likely to have come from the same two underlying populations that have the same mean.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="t_inv"><summary class="unimplemented">
#### T_INV
<code>__T_INV__(probability, degrees_freedom)</code>
<a class="headerlink" href="#t_inv" title="Permanent link">#</a>
</summary>
Calculates the negative inverse of the one-tailed TDIST function.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="t_inv_2t"><summary class="unimplemented">
#### T_INV_2T
<code>__T_INV_2T__(probability, degrees_freedom)</code>
<a class="headerlink" href="#t_inv_2t" title="Permanent link">#</a>
</summary>
Calculates the inverse of the two-tailed TDIST function.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="var"><summary class="unimplemented">
#### VAR
<code>__VAR__(value1, value2)</code>
<a class="headerlink" href="#var" title="Permanent link">#</a>
</summary>
Calculates the variance based on a sample.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="vara"><summary class="unimplemented">
#### VARA
<code>__VARA__(value1, value2)</code>
<a class="headerlink" href="#vara" title="Permanent link">#</a>
</summary>
Calculates an estimate of variance based on a sample, setting text to the value `0`.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="varp"><summary class="unimplemented">
#### VARP
<code>__VARP__(value1, value2)</code>
<a class="headerlink" href="#varp" title="Permanent link">#</a>
</summary>
Calculates the variance based on an entire population.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="varpa"><summary class="unimplemented">
#### VARPA
<code>__VARPA__(value1, value2)</code>
<a class="headerlink" href="#varpa" title="Permanent link">#</a>
</summary>
Calculates the variance based on an entire population, setting text to the value `0`.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="weibull"><summary class="unimplemented">
#### WEIBULL
<code>__WEIBULL__(x, shape, scale, cumulative)</code>
<a class="headerlink" href="#weibull" title="Permanent link">#</a>
</summary>
Returns the value of the Weibull distribution function (or Weibull cumulative distribution
function) for a specified shape and scale.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="ztest"><summary class="unimplemented">
#### ZTEST
<code>__ZTEST__(data, value, standard_deviation)</code>
<a class="headerlink" href="#ztest" title="Permanent link">#</a>
</summary>
Returns the two-tailed P-value of a Z-test with standard distribution.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
### Text
<details id="char"><summary >
#### CHAR
<code>__CHAR__(table_number)</code>
<a class="headerlink" href="#char" title="Permanent link">#</a>
</summary>
Convert a number into a character according to the current Unicode table.
Same as `unichr(number)`.


```python
>>> CHAR(65)
u'A'
```

```python
>>> CHAR(33)
u'!'
```

</details>
<details id="clean"><summary >
#### CLEAN
<code>__CLEAN__(text)</code>
<a class="headerlink" href="#clean" title="Permanent link">#</a>
</summary>
Returns the text with the non-printable characters removed.

This removes both characters with values 0 through 31, and other Unicode characters in the
"control characters" category.


```python
>>> CLEAN(CHAR(9) + "Monthly report" + CHAR(10))
u'Monthly report'
```

</details>
<details id="code"><summary >
#### CODE
<code>__CODE__(string)</code>
<a class="headerlink" href="#code" title="Permanent link">#</a>
</summary>
Returns the numeric Unicode map value of the first character in the string provided.
Same as `ord(string[0])`.


```python
>>> CODE("A")
65
```

```python
>>> CODE("!")
33
```

```python
>>> CODE("!A")
33
```

</details>
<details id="concat"><summary >
#### CONCAT
<code>__CONCAT__(string, *more_strings)</code>
<a class="headerlink" href="#concat" title="Permanent link">#</a>
</summary>
Joins together any number of text strings into one string. Also available under the name
`CONCATENATE`. Similar to the Python expression `"".join(array_of_strings)`.


```python
>>> CONCAT("Stream population for ", "trout", " ", "species", " is ", 32, "/mile.")
u'Stream population for trout species is 32/mile.'
```

```python
>>> CONCAT("In ", 4, " days it is ", datetime.date(2016,1,1))
u'In 4 days it is 2016-01-01'
```

```python
>>> CONCAT("abc")
u'abc'
```

```python
>>> CONCAT(0, "abc")
u'0abc'
```

```python
>>> assert CONCAT(2, u" crème ", u"brûlée") == u'2 crème brûlée'

```

</details>
<details id="concatenate"><summary >
#### CONCATENATE
<code>__CONCATENATE__(string, *more_strings)</code>
<a class="headerlink" href="#concatenate" title="Permanent link">#</a>
</summary>
Joins together any number of text strings into one string. Also available under the name
`CONCAT`. Similar to the Python expression `"".join(array_of_strings)`.


```python
>>> CONCATENATE("Stream population for ", "trout", " ", "species", " is ", 32, "/mile.")
u'Stream population for trout species is 32/mile.'
```

```python
>>> CONCATENATE("In ", 4, " days it is ", datetime.date(2016,1,1))
u'In 4 days it is 2016-01-01'
```

```python
>>> CONCATENATE("abc")
u'abc'
```

```python
>>> CONCATENATE(0, "abc")
u'0abc'
```

```python
>>> assert CONCATENATE(2, u" crème ", u"brûlée") == u'2 crème brûlée'

```

```python
>>> assert CONCATENATE(2,  " crème ", u"brûlée") == u'2 crème brûlée'

```

```python
>>> assert CONCATENATE(2,  " crème ",  "brûlée") == u'2 crème brûlée'

```

</details>
<details id="dollar"><summary >
#### DOLLAR
<code>__DOLLAR__(number, decimals=2)</code>
<a class="headerlink" href="#dollar" title="Permanent link">#</a>
</summary>
Formats a number into a formatted dollar amount, with decimals rounded to the specified place (.
If decimals value is omitted, it defaults to 2.


```python
>>> DOLLAR(1234.567)
'$1,234.57'
```

```python
>>> DOLLAR(1234.567, -2)
'$1,200'
```

```python
>>> DOLLAR(-1234.567, -2)
'($1,200)'
```

```python
>>> DOLLAR(-0.123, 4)
'($0.1230)'
```

```python
>>> DOLLAR(99.888)
'$99.89'
```

```python
>>> DOLLAR(0)
'$0.00'
```

```python
>>> DOLLAR(10, 0)
'$10'
```

</details>
<details id="exact"><summary >
#### EXACT
<code>__EXACT__(string1, string2)</code>
<a class="headerlink" href="#exact" title="Permanent link">#</a>
</summary>
Tests whether two strings are identical. Same as `string2 == string2`.


```python
>>> EXACT("word", "word")
True
```

```python
>>> EXACT("Word", "word")
False
```

```python
>>> EXACT("w ord", "word")
False
```

</details>
<details id="find"><summary >
#### FIND
<code>__FIND__(find_text, within_text, start_num=1)</code>
<a class="headerlink" href="#find" title="Permanent link">#</a>
</summary>
Returns the position at which a string is first found within text.

Find is case-sensitive. The returned position is 1 if within_text starts with find_text.
Start_num specifies the character at which to start the search, defaulting to 1 (the first
character of within_text).

If find_text is not found, or start_num is invalid, raises ValueError.


```python
>>> FIND("M", "Miriam McGovern")
1
```

```python
>>> FIND("m", "Miriam McGovern")
6
```

```python
>>> FIND("M", "Miriam McGovern", 3)
8
```

```python
>>> FIND(" #", "Hello world # Test")
12
```

```python
>>> FIND("gle", "Google", 1)
4
```

```python
>>> FIND("GLE", "Google", 1)
Traceback (most recent call last):
...
ValueError: substring not found
```

```python
>>> FIND("page", "homepage")
5
```

```python
>>> FIND("page", "homepage", 6)
Traceback (most recent call last):
...
ValueError: substring not found
```

</details>
<details id="fixed"><summary >
#### FIXED
<code>__FIXED__(number, decimals=2, no_commas=False)</code>
<a class="headerlink" href="#fixed" title="Permanent link">#</a>
</summary>
Formats a number with a fixed number of decimal places (2 by default), and commas.
If no_commas is True, then omits the commas.


```python
>>> FIXED(1234.567, 1)
'1,234.6'
```

```python
>>> FIXED(1234.567, -1)
'1,230'
```

```python
>>> FIXED(-1234.567, -1, True)
'-1230'
```

```python
>>> FIXED(44.332)
'44.33'
```

```python
>>> FIXED(3521.478, 2, False)
'3,521.48'
```

```python
>>> FIXED(-3521.478, 1, True)
'-3521.5'
```

```python
>>> FIXED(3521.478, 0, True)
'3521'
```

```python
>>> FIXED(3521.478, -2, True)
'3500'
```

</details>
<details id="left"><summary >
#### LEFT
<code>__LEFT__(string, num_chars=1)</code>
<a class="headerlink" href="#left" title="Permanent link">#</a>
</summary>
Returns a substring of length num_chars from the beginning of the given string. If num_chars is
omitted, it is assumed to be 1. Same as `string[:num_chars]`.


```python
>>> LEFT("Sale Price", 4)
'Sale'
```

```python
>>> LEFT('Swededn')
'S'
```

```python
>>> LEFT('Text', -1)
Traceback (most recent call last):
...
ValueError: num_chars invalid
```

</details>
<details id="len"><summary >
#### LEN
<code>__LEN__(text)</code>
<a class="headerlink" href="#len" title="Permanent link">#</a>
</summary>
Returns the number of characters in a text string, or the number of items in a list. Same as
[`len`](https://docs.python.org/3/library/functions.html#len) in python.
See [Record Set](#recordset) for an example of using `len` on a list of records.


```python
>>> LEN("Phoenix, AZ")
11
```

```python
>>> LEN("")
0
```

```python
>>> LEN("     One   ")
11
```

</details>
<details id="lower"><summary >
#### LOWER
<code>__LOWER__(text)</code>
<a class="headerlink" href="#lower" title="Permanent link">#</a>
</summary>
Converts a specified string to lowercase. Same as `text.lower()`.


```python
>>> LOWER("E. E. Cummings")
'e. e. cummings'
```

```python
>>> LOWER("Apt. 2B")
'apt. 2b'
```

</details>
<details id="mid"><summary >
#### MID
<code>__MID__(text, start_num, num_chars)</code>
<a class="headerlink" href="#mid" title="Permanent link">#</a>
</summary>
Returns a segment of a string, starting at start_num. The first character in text has
start_num 1.


```python
>>> MID("Fluid Flow", 1, 5)
'Fluid'
```

```python
>>> MID("Fluid Flow", 7, 20)
'Flow'
```

```python
>>> MID("Fluid Flow", 20, 5)
''
```

```python
>>> MID("Fluid Flow", 0, 5)
Traceback (most recent call last):
...
ValueError: start_num invalid
```

</details>
<details id="phone_format"><summary >
#### PHONE_FORMAT
<code>__PHONE_FORMAT__(value, country=None, format=None)</code>
<a class="headerlink" href="#phone_format" title="Permanent link">#</a>
</summary>
Formats a phone number.

With no optional arguments, the number must start with "+" and the international dialing prefix,
and will be formatted as an international number, e.g. `+12345678901` becomes `+1 234-567-8901`.

The `country` argument allows specifying a 2-letter country code (e.g. "US" or "GB") for
interpreting phone numbers that don't start with "+". E.g. `PHONE_FORMAT('2025555555', 'US')`
would be seen as a US number and formatted as "(202) 555-5555". Phone numbers that start with
"+" ignore `country`. E.g. `PHONE_FORMAT('+33555555555', 'US')` is a French number because '+33'
is the international prefix for France.

The `format` argument specifies the output format, according to this table:

  - `"#"` or `"NATL"` (default) - use the national format, without the international dialing
    prefix, when possible. E.g. `(234) 567-8901` for "US", or `02 34 56 78 90` for "FR". If
    `country` is omitted, or the number does not correspond to the given country, the
    international format is used instead.
  - `"+"` or `"INTL"` - international format, e.g. `+1 234-567-8901` or
    `+33 2 34 56 78 90`.
  - `"*"` or `"E164"` - E164 format, like international but with no separators, e.g.
    `+12345678901`.
  - `"tel"` or `"RFC3966"` - format suitable to use as a [hyperlink](col-types.md#hyperlinks),
    e.g. 'tel:+1-234-567-8901'.

When specifying the `format` argument, you may omit the `country` argument. I.e.
`PHONE_FORMAT(value, "tel")` is equivalent to `PHONE_FORMAT(value, None, "tel")`.

For more details, see the [phonenumbers](https://github.com/daviddrysdale/python-phonenumbers)
Python library, which underlies this function.


```python
>>> PHONE_FORMAT("+12345678901")
u'+1 234-567-8901'
```

```python
>>> PHONE_FORMAT("2345678901", "US")
u'(234) 567-8901'
```

```python
>>> PHONE_FORMAT("2345678901", "GB")
u'023 4567 8901'
```

```python
>>> PHONE_FORMAT("2345678901", "GB", "+")
u'+44 23 4567 8901'
```

```python
>>> PHONE_FORMAT("+442345678901", "GB")
u'023 4567 8901'
```

```python
>>> PHONE_FORMAT("+12345678901", "GB")
u'+1 234-567-8901'
```

```python
>>> PHONE_FORMAT("(234) 567-8901")
Traceback (most recent call last):
...
NumberParseException: (0) Missing or invalid default region.
```

```python
>>> PHONE_FORMAT("(234)567 89-01", "US", "tel")
u'tel:+1-234-567-8901'
```

```python
>>> PHONE_FORMAT("2/3456/7890", "FR", '#')
u'02 34 56 78 90'
```

```python
>>> PHONE_FORMAT("+33234567890", '#')
u'+33 2 34 56 78 90'
```

```python
>>> PHONE_FORMAT("+33234567890", 'tel')
u'tel:+33-2-34-56-78-90'
```

```python
>>> PHONE_FORMAT("tel:+1-234-567-8901", country="US", format="*")
u'+12345678901'
```

</details>
<details id="proper"><summary >
#### PROPER
<code>__PROPER__(text)</code>
<a class="headerlink" href="#proper" title="Permanent link">#</a>
</summary>
Capitalizes each word in a specified string. It converts the first letter of each word to
uppercase, and all other letters to lowercase. Same as `text.title()`.


```python
>>> PROPER('this is a TITLE')
'This Is A Title'
```

```python
>>> PROPER('2-way street')
'2-Way Street'
```

```python
>>> PROPER('76BudGet')
'76Budget'
```

</details>
<details id="regexextract"><summary >
#### REGEXEXTRACT
<code>__REGEXEXTRACT__(text, regular_expression)</code>
<a class="headerlink" href="#regexextract" title="Permanent link">#</a>
</summary>
Extracts the first part of text that matches regular_expression.


```python
>>> REGEXEXTRACT("Google Doc 101", "[0-9]+")
'101'
```

```python
>>> REGEXEXTRACT("The price today is $826.25", "[0-9]*\.[0-9]+[0-9]+")
'826.25'
```

If there is a parenthesized expression, it is returned instead of the whole match.

```python
>>> REGEXEXTRACT("(Content) between brackets", "\(([A-Za-z]+)\)")
'Content'
```

```python
>>> REGEXEXTRACT("Foo", "Bar")
Traceback (most recent call last):
...
ValueError: REGEXEXTRACT text does not match
```

</details>
<details id="regexmatch"><summary >
#### REGEXMATCH
<code>__REGEXMATCH__(text, regular_expression)</code>
<a class="headerlink" href="#regexmatch" title="Permanent link">#</a>
</summary>
Returns whether a piece of text matches a regular expression.


```python
>>> REGEXMATCH("Google Doc 101", "[0-9]+")
True
```

```python
>>> REGEXMATCH("Google Doc", "[0-9]+")
False
```

```python
>>> REGEXMATCH("The price today is $826.25", "[0-9]*\.[0-9]+[0-9]+")
True
```

```python
>>> REGEXMATCH("(Content) between brackets", "\(([A-Za-z]+)\)")
True
```

```python
>>> REGEXMATCH("Foo", "Bar")
False
```

</details>
<details id="regexreplace"><summary >
#### REGEXREPLACE
<code>__REGEXREPLACE__(text, regular_expression, replacement)</code>
<a class="headerlink" href="#regexreplace" title="Permanent link">#</a>
</summary>
Replaces all parts of text matching the given regular expression with replacement text.


```python
>>> REGEXREPLACE("Google Doc 101", "[0-9]+", "777")
'Google Doc 777'
```

```python
>>> REGEXREPLACE("Google Doc", "[0-9]+", "777")
'Google Doc'
```

```python
>>> REGEXREPLACE("The price is $826.25", "[0-9]*\.[0-9]+[0-9]+", "315.75")
'The price is $315.75'
```

```python
>>> REGEXREPLACE("(Content) between brackets", "\(([A-Za-z]+)\)", "Word")
'Word between brackets'
```

```python
>>> REGEXREPLACE("Foo", "Bar", "Baz")
'Foo'
```

</details>
<details id="replace"><summary >
#### REPLACE
<code>__REPLACE__(text, position, length, new_text)</code>
<a class="headerlink" href="#replace" title="Permanent link">#</a>
</summary>
Replaces part of a text string with a different text string. Position is counted from 1.


```python
>>> REPLACE("abcdefghijk", 6, 5, "*")
'abcde*k'
```

```python
>>> REPLACE("2009", 3, 2, "10")
'2010'
```

```python
>>> REPLACE('123456', 1, 3, '@')
'@456'
```

```python
>>> REPLACE('foo', 1, 0, 'bar')
'barfoo'
```

```python
>>> REPLACE('foo', 0, 1, 'bar')
Traceback (most recent call last):
...
ValueError: position invalid
```

</details>
<details id="rept"><summary >
#### REPT
<code>__REPT__(text, number_times)</code>
<a class="headerlink" href="#rept" title="Permanent link">#</a>
</summary>
Returns specified text repeated a number of times. Same as `text * number_times`.

The result of the REPT function cannot be longer than 32767 characters, or it raises a
ValueError.


```python
>>> REPT("*-", 3)
'*-*-*-'
```

```python
>>> REPT('-', 10)
'----------'
```

```python
>>> REPT('-', 0)
''
```

```python
>>> len(REPT('---', 10000))
30000
```

```python
>>> REPT('---', 11000)
Traceback (most recent call last):
...
ValueError: number_times invalid
```

```python
>>> REPT('-', -1)
Traceback (most recent call last):
...
ValueError: number_times invalid
```

</details>
<details id="right"><summary >
#### RIGHT
<code>__RIGHT__(string, num_chars=1)</code>
<a class="headerlink" href="#right" title="Permanent link">#</a>
</summary>
Returns a substring of length num_chars from the end of a specified string. If num_chars is
omitted, it is assumed to be 1. Same as `string[-num_chars:]`.


```python
>>> RIGHT("Sale Price", 5)
'Price'
```

```python
>>> RIGHT('Stock Number')
'r'
```

```python
>>> RIGHT('Text', 100)
'Text'
```

```python
>>> RIGHT('Text', -1)
Traceback (most recent call last):
...
ValueError: num_chars invalid
```

</details>
<details id="search"><summary >
#### SEARCH
<code>__SEARCH__(find_text, within_text, start_num=1)</code>
<a class="headerlink" href="#search" title="Permanent link">#</a>
</summary>
Returns the position at which a string is first found within text, ignoring case.

Find is case-sensitive. The returned position is 1 if within_text starts with find_text.
Start_num specifies the character at which to start the search, defaulting to 1 (the first
character of within_text).

If find_text is not found, or start_num is invalid, raises ValueError.

```python
>>> SEARCH("e", "Statements", 6)
7
```

```python
>>> SEARCH("margin", "Profit Margin")
8
```

```python
>>> SEARCH(" ", "Profit Margin")
7
```

```python
>>> SEARCH('"', 'The "boss" is here.')
5
```

```python
>>> SEARCH("gle", "Google")
4
```

```python
>>> SEARCH("GLE", "Google")
4
```

</details>
<details id="substitute"><summary >
#### SUBSTITUTE
<code>__SUBSTITUTE__(text, old_text, new_text, instance_num=None)</code>
<a class="headerlink" href="#substitute" title="Permanent link">#</a>
</summary>
Replaces existing text with new text in a string. It is useful when you know the substring of
text to replace. Use REPLACE when you know the position of text to replace.

If instance_num is given, it specifies which occurrence of old_text to replace. If omitted, all
occurrences are replaced.

Same as `text.replace(old_text, new_text)` when instance_num is omitted.


```python
>>> SUBSTITUTE("Sales Data", "Sales", "Cost")
u'Cost Data'
```

```python
>>> SUBSTITUTE("Quarter 1, 2008", "1", "2", 1)
u'Quarter 2, 2008'
```

```python
>>> SUBSTITUTE("Quarter 1, 2011", "1", "2", 3)
u'Quarter 1, 2012'
```
</details>
<details id="t"><summary >
#### T
<code>__T__(value)</code>
<a class="headerlink" href="#t" title="Permanent link">#</a>
</summary>
Returns value if value is text, or the empty string when value is not text.


```python
>>> T('Text')
u'Text'
```

```python
>>> T(826)
u''
```

```python
>>> T('826')
u'826'
```

```python
>>> T(False)
u''
```

```python
>>> T('100 points')
u'100 points'
```

```python
>>> T(AltText('Text'))
u'Text'
```

```python
>>> T(float('nan'))
u''
```

</details>
<details id="text"><summary class="unimplemented">
#### TEXT
<code>__TEXT__(number, format_type)</code>
<a class="headerlink" href="#text" title="Permanent link">#</a>
</summary>
Converts a number into text according to a specified format. It is not yet implemented in
Grist.

<span class="grist-tip">Note</span>This function is not currently implemented in Grist.
</details>
<details id="trim"><summary >
#### TRIM
<code>__TRIM__(text)</code>
<a class="headerlink" href="#trim" title="Permanent link">#</a>
</summary>
Removes all spaces from text except for single spaces between words. Note that TRIM does not
remove other whitespace such as tab or newline characters.


```python
>>> TRIM(" First Quarter\n    Earnings     ")
'First Quarter\n Earnings'
```

```python
>>> TRIM("")
''
```

</details>
<details id="upper"><summary >
#### UPPER
<code>__UPPER__(text)</code>
<a class="headerlink" href="#upper" title="Permanent link">#</a>
</summary>
Converts a specified string to uppercase. Same as `text.lower()`.


```python
>>> UPPER("e. e. cummings")
'E. E. CUMMINGS'
```

```python
>>> UPPER("Apt. 2B")
'APT. 2B'
```

</details>
<details id="value"><summary >
#### VALUE
<code>__VALUE__(text)</code>
<a class="headerlink" href="#value" title="Permanent link">#</a>
</summary>
Converts a string in accepted date, time or number formats into a number or date.


```python
>>> VALUE("$1,000")
1000
```

```python
>>> assert VALUE("16:48:00") - VALUE("12:00:00") == datetime.timedelta(0, 17280)

```

```python
>>> VALUE("01/01/2012")
datetime.datetime(2012, 1, 1, 0, 0)
```

```python
>>> VALUE("")
0
```

```python
>>> VALUE(0)
0
```

```python
>>> VALUE("826")
826
```

```python
>>> VALUE("-826.123123123")
-826.123123123
```

```python
>>> VALUE(float('nan'))
nan
```

```python
>>> VALUE("Invalid")
Traceback (most recent call last):
...
ValueError: text cannot be parsed to a number
```

```python
>>> VALUE("13/13/13")
Traceback (most recent call last):
...
ValueError: text cannot be parsed to a number
```

</details>
<!-- END mkpydocs docs -->
