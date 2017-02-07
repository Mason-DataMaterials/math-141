Grammar in R
========================================================
autosize: true
incremental: true


The essential sentence
========================================================



A general format:


```r
function(argument1, argument2, ...)
```

Telling R what you want it to do (the *function*) and how it should do it / what
it should do it to (the *arguments*).


```r
a <- function(argument1, argument2, ...)
```

You can save the output by *assigning* it to a new object; otherwise it's printed
to the console.


Example
========================================================


```r
x <- c(4, 7, 7, 8, 9)
sum(x)
```

```
[1] 35
```

```r
a <- sum(x)
a
```

```
[1] 35
```


Will this work?
========================================================
type: prompt

example: 


```r
sum(x
```

No! Parentheses must be balanced (quotation marks too).


Will this work?
========================================================
type: prompt

example: 


```r
sum(      x    )
```

```
[1] 35
```

Yes! Spaces generally do not matter.

A sentence involving a dataframe
========================================================

Length returns the length of a vector (column or row)


```r
data(arbuthnot)
length(arbuthnot$year)
```

```
[1] 82
```

Here we pull out the `year` column from the `arbuthnot` data frame using the
`$`.


An alternative sentence involving a dataframe
========================================================

For a graphic...


```r
qplot(x = year,y =girls, data = arbuthnot, geom="line")
```

Here, the function knows which in data frame to find `year` and `girls`, so 
there is no need for the `$`.


```r
p <- qplot(x = year,y =girls, data = arbuthnot, geom="line")
p
```

![plot of chunk unnamed-chunk-9](02B-R-concepts-figure/unnamed-chunk-9-1.png)


Will this work?
========================================================
type: prompt

example:


```r
qplot(year,y =girls, data = arbuthnot, geom="line")
```

![plot of chunk unnamed-chunk-10](02B-R-concepts-figure/unnamed-chunk-10-1.png)

Yes! If you don't name your arguments, R will guess based on their order.

Even so, it's a good idea to name your arguments.


The pipe
========================================================

![pipe](pipe.png)



Data wrangling functions
========================================================

- filter()
- mutate()
- summarize()
- group_by()


```
# A tibble: 6 × 16
   year month   day dep_time dep_delay arr_time arr_delay carrier tailnum
  <int> <int> <int>    <int>     <dbl>    <int>     <dbl>   <chr>   <chr>
1  2014     1     1        1        96      235        70      AS  N508AS
2  2014     1     1        4        -6      738       -23      US  N195UW
3  2014     1     1        8        13      548        -4      UA  N37422
4  2014     1     1       28        -2      800       -23      US  N547UW
5  2014     1     1       34        44      325        43      AS  N762AS
6  2014     1     1       37        82      747        88      DL  N806DN
# ... with 7 more variables: flight <int>, origin <chr>, dest <chr>,
#   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>
```

```
Classes 'tbl_df', 'tbl' and 'data.frame':	162049 obs. of  16 variables:
 $ year     : int  2014 2014 2014 2014 2014 2014 2014 2014 2014 2014 ...
 $ month    : int  1 1 1 1 1 1 1 1 1 1 ...
 $ day      : int  1 1 1 1 1 1 1 1 1 1 ...
 $ dep_time : int  1 4 8 28 34 37 346 526 527 536 ...
 $ dep_delay: num  96 -6 13 -2 44 82 227 -4 7 1 ...
 $ arr_time : int  235 738 548 800 325 747 936 1148 917 1334 ...
 $ arr_delay: num  70 -23 -4 -23 43 88 219 15 24 -6 ...
 $ carrier  : chr  "AS" "US" "UA" "US" ...
 $ tailnum  : chr  "N508AS" "N195UW" "N37422" "N547UW" ...
 $ flight   : int  145 1830 1609 466 121 1823 1481 229 1576 478 ...
 $ origin   : chr  "PDX" "SEA" "PDX" "PDX" ...
 $ dest     : chr  "ANC" "CLT" "IAH" "CLT" ...
 $ air_time : num  194 252 201 251 201 224 202 217 136 268 ...
 $ distance : num  1542 2279 1825 2282 1448 ...
 $ hour     : num  0 0 0 0 0 0 3 5 5 5 ...
 $ minute   : num  1 4 8 28 34 37 46 26 27 36 ...
```



Exercise 8
========================================================
What is the tail number of the plane with the fastest avg_speed?




