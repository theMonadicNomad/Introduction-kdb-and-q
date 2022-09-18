# Introduction to kdb+ and q

## 1&2. Intro & Consoles, Data Types, Lists

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

## 3. Operators & Operators precedence


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


## 4.Booleans and Temporal Types

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

q)1 2 3=1`0 20 3 40 --Compare 2 lists of not of equal length.
'length
  [0]  1 2 3=10 20 3 40 -- Error message
  
  
  --Date Values
  
  -- q counts dates from the millenium 
  
q)2018.01.01 -- A count of days since the millenium 
2018.01.01

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