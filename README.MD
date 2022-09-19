# Introduction to kdb+ and q

Here you will find a brief summary of introduction to kdb+ and q, based on the offical lectures of Jeffry Borror, Author of [Q for Mortals](https://code.kx.com/q4m3/). You can find the official tutorial [here](https://code.kx.com/q/learn/q-for-all/).

## Chapter 1&2. Intro & Consoles, Data Types, Lists

```haskell
q)52 
52 --64 bit integer

q)32i 
32i --32 bit integer

q)6*7
42

q)5-3
2

q)4%2 -- Division operator always returns floating point
2f

-- Most of numeric operations are vector operations
q)1 2 3+10 20 30 -- Adding lists (vector programming)
11 22 33


q)1 2 3
1 2 3

q)1.0 2.0 3.0
1 2 3f -- List of Floating Points

```

## Chapter 3. Operators & Operators precedence


```haskell
q)count 10 2.0 3.0
3

q)1+10 20 30 --Adding a single number (scalar) to all numbers in a list (Vector)
11 21 31 

q)10 20 30+1
11 21 31

q)0 1 2 3 4 5%2 --Divide every item in the list by 2
0 0.5 1 1.5 2 2.5

-- All operators have same precedence in Q
--Everything is done from right to left (based on mathematics and the order in which composite functions are evaluated)

q)2*3+4
14

q)til 5 --generates a list of numbers until n
0 1 2 3 4 5

q)count till 100
100

q)1+til 7 -- generates a list until 7 and 1 to each of them
1 2 3 4 5 6 7

q)1+2*til 10 -- Generates a list of first 10 odd integers.
1 3 5 7 9 11 13 15 17 19

--q is a vector language
--q wants to run or operate on individual numbers it wants to operate
```


## Chapter 4. Booleans and Temporal Types

```haskell

q)0b -- Boolean false
0b

q)1b --Boolean True
1b

q)101b --List of booleans is not separated by space
101b -- True False True

--Each boolean value is stored in a byte

q)42=6*7 -- Compare 2 values
1b

--Comparison operators are a vector operations.

q)1 2 3=10 2 30 -- When you compare 2 lists, it compares individual elements in the two lists 
010b --False True False

q)1 2 3=10 20 3 40 --Compare 2 lists of not of equal length.
'length
  [0]  1 2 3=10 20 3 40 -- Error message
  
  
  --Date Values
  
  -- q counts dates from the millenium 
  
q)2018.01.01 -- A count of days since the millenium 
2018.01.01


--In Q, as long as things have compatible underlying values you can compare them 
q)2000.01.01=0
1b

q)1999.12.31=-1
1b

--We can do arithmetic on days
q)2000.01.01+31
2000.02.01

q)2000.02.01-2000.01.01
31i

q)2000.01m --January 2000
2000.01m

q)2000.02m=1
1b

q)1999.12m=-1
1b

q)2000.01.01=2000.01m
1b

```

## Chapter 5. Casting and Date Operators


--Casting: Convert a value of one type to another type
``` haskell
q)`long$1.0 -- Cast the float 1.0 to long
1

q)`float$1 --Cast the integer to float
1f

q)`boolean$1
1b

q)`date$31
2000.02.01

q)2000.01m+til 3
2000.01 2000.02 2000.03m

```

## Chapter 6. Operations on Lists

```haskell

--Declarative Programming: What you want, not how to do it.

q)0 +/ 10 20 30 40 50 --Initialize to 0 and add across the list
150

-- / called as over Operator in Q, similar to Fold in Functional Programming.

q)(+/) 10 20 30 40 50 --No need of initialization
150

q)(*/) 1 2 3 4 5 --Multiply across the list starting from the first number
120

q)(*/) 1+til 5
120

q)4|5 -- Returns the larger of the two numbers
5

q)10&2 --Returns the smaller of the two numbers
2

q)(|/) 10 30 20 50 40 --Returns the max of the list
50

q)(&/) 10 30 20 45 50 --Returns the min of the list
10

q)sum 10 30 20 50 40
150

q)min 10 30 20 50 40
10

q)max 10 30 20 50 40
50 

q)0b|1b
1b

q)(+/) 10 20 30 40 50
150

q)(+\) 10 20 30 40 50
10 30 60 100 150 --Displays the intermediate results along with the final results


q)(&\) 40 20 30 10 50
40 20 20 10 10

q)(|\) 40 20 30 10 50
40 40 40 40 50

q)sums 10 20 30 40 50 --Running sum
10 30 60 100 150

q)mins 10 20 30 40 50 --Running minimum
10 10 10 10 10

q)maxs --Running maximum

```

## Chapter 7. Functions

```haskell

q){[x]x*x}5 --Squaring Function
25

q){[x]x*x}[4]
16

q){x*x}5
25
```


## Chapter 8. Newton Raphson & Fibonacci

```haskell
q){[xn] xn +(2-xn*xn)%2*xn}/[1.0]
1.414214

q){[xn] xn +(2-xn*xn)%2*xn}`\[1.0]
1 1.5 1.416667 1.414216 1.414214 

q)2#10 20 30 40 50 --Retrieve the first 'n' numbers of the list
10 20 

q)-2# 10 20 30 40 50 -- Retrieve the last 'n' numbers of the list.
40 50 

q)10 20 , 100 200 300 --Join the lists
10 20 100 200 300

q){-2#x} 1 1 -- Take the last 2 arguments of the list
1 1

q){sum -2#x} 1 1
2

q){x, sum -2#x} 1 1 --Take the last 2 elements, sum them and concatenate to the back of the list
1 1 2

q){x, sum -2#x}/[10;1 1] -- Iterate 10 times starting with 1 1 

1 1 2 3 5 8 13 21 34 55 89 144

```


## Chapter 9. Functions Examples: Variables

```haskell

q)deltas 10 20 30 40 50 -- REturns the successive differences across a numeric list
10 10 10 10 10 

q)deltas 110 120 130 140 150
110 10 10 10 10

q)deltas sums 110 120 130 140 150
110 120 130 140 150 --Invariants

q)sums deltas 110 120 130 140 150
110 120 130 140 150 --Invariants

--Assigning a variable
q)a:42 --Assignment operator
q)a
42

q)buys:2 1 4 3 5 4 

q)sums buys
2 3 7 10 15 19

```

## Chapter 10. Tables


A collection of columns(operations on lists, vector operation) is a table in Q.

```haskell
q)dates:2018.01.01+10000?31 --Generate 10000 random numbers between 0 and 31 
q) count dates
10000

q)times:10000?24:00:00.000 -- Generate 10000 random times between 00:00:00 till 24:00:00
q)qtys: 100*1+10000?100

q)ixs:10000?3 --Generate 10000 random numbers between 0-2
q)syms: `aapl `amzn `googl` ixs
q)syms
`googl `aapl `amzn `googl ..

q)172.0 1189.0 1073.0 ixs
1073 172 1189 1073 1073 1189 ..

q)pxs:(1+10000?.03)*172.0 1189.0 1073.0 ixs
q)pxs
1080.679 172.5521 1211.08 1104.971 ..

q)t:([] date:dates; time:times; sym:syms;qty:qtys;px:pxs) --Creating table from individual lists
q)t
2018.01.27 19:44:30.940 aapl 3000 176.5086
2018.01.05 15:52:20.987 amzn 1200 1213.456
..

q)t:`date`time xasc t --Sort the table based on date and time
q)2#t First 2 rows
q)date          time        sym     qty     px
--------------------------------------------------
2018.01.01 00:00:01.129     aapl    8000    174.7627
2018.01.01 00:00:03.396     amzn    8300    175.518

```

## Chapter 11. qSQL

```haskell

q)select date, time, sym, px from t

q)select date,time,qty,px from t where sym=`aapl
q)\t select date,time,qty,px from t where sym=`aapl -- Evaluate the query and return the time taken to execute

q)first 10 20 30 40 50
10

q)last 10 20 30 40 50
50

q)5#select open:first px, close:last px by date,time from t where sym=`aapl
q)5#select open:first px, close:last px, lo:min px, hi:max px by date,time from t where sym=`aapl

```

## Chapter 12: Complex Queries(*)

```haskell
q)1 3 2 1 wavg 10 20 30 40 -- Compute the weighted average of the list on the right using the weights on the left
20f

q)5 xbar 0 12 3 4 5 10 11 21 --Largest multiple of 5 that does not exceed the number on the right
0 0 0 0 0 5 10 10 20 

q)select max px - mins px from t where sym=`aapl -- Maximizing the profit 
px
-------
5.1599992

```

## Chapter 13: Introduction to IntraProcess Communication

```haskell


q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)
q)



```