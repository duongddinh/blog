---
layout: post
title: Right triangle number sequence
date: 2018-01-1 15:47:15 +0300
description: I wrote this awhile ago where I noticed the number sequence in a right triangle. # Add post description (optional)
img: # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [pythagoras, Math, Triangle]
---

I wrote this awhile ago where I noticed the number sequence in a right triangle

## FOR a, b, c INTEGERS

###### Starting with old idea:

- (a^2+b^2=c^2) - this formula was found by Pythagoras 

Right triangle: 

![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Rtriangle.svg/220px-Rtriangle.svg.png)

- to find a, we use: a=√(c^2+b^2) 

## `CONSIDER THESE SPECIAL FORMS: `

#### For unknown a and c = b+2

```javascript
a=(c-b)√((c+b)/2) 

```
**_Prove:_** 

```
 c^2 - b^2 = 4(c-1) => c^2 - (c-2)^2 = 4c-4 => (c-c+2)(c+c-2) = 2(2c-2) => 2(2c-2) = 2(2c-2) => true
 
```
 
note: c-1 = (c+b)/2

c | b | a  | Calc
--| --|----|----
2 | 0 | 2√1 | (2-0)√((2+0)/2)
4 | 2 | 2√3 | (4-2)√(4-2+1)
5 | 3 | 2√4=4 | (5-3)√((5+3)/2)
6 | 4 | 2√5 | (6-4)√((6+4)/2)
7 | 5 | 2√6 | (7-5)√((7+5)/2)
8 | 6 | 2√7 | (8-6)√((8+6)/2)
..| ..| ... | ...
 
#### For unknown a, c = b+4 and b < c > a

```
a = (c-b) √(d)   for c/b = e/f (factored) if (e == f+2) {d = (e+f)/2} else if(e==f+1) {d = e + f} return true if c, b > 8, 4 and c is EVEN  [1]

a= (c-b-2) √(d)   for (d = c + b) return true if c is ODD   [2]

```

 
**_Prove for [1]_**
 
 ```
 c/b = e/f => c = be/f. Since c = b + 4  => be/f - b = 4  => b = 4f/e-f = 4f/2  = 2f
 
 => c = 2f + 4 => this equation (c-b)^2(e-1) = (2f+4-2f)^2(f+1) = 16(f+1) (1)
 
 Now, this equation: c^2-b^2 = (2f+4)^2 - (2f)^2 = 4(4f+4) = 16(f+1) (2)
 
 from (1) && (2) => true 
 
```

```
 b=4f => (c-b)^2(2f+1) = 16(4f) (3)
 
 c^2 - b^2 = 16(4f) (4)
 
 from (3) && (4) => true
 
 ```
 
**_Prove for [2]_** 

 Substitute c =b+4 to c and factor this, we will have: 
 
  ```
 
 4(2b+4) = (b+4)^2-b^2 ( this is c^2 - b^2) which is 8b + 16 = 8b+16 => true  
 
  ```

c | b | a   | Calc | Explain
--| --|---- |----- |-----
5 | 1 | 2√6 | (5-1-2)√(5+1)     | ODD
12 | 8 | 2√20=4√5 |(12-8)√(3+2)|12/8=3/2 & 3=3+1 & EVEN
7 | 3 | 2√14 |(7-3-2)√(7+3)     | ODD
10 | 6 | 8 |(10-6)√((5+3)/2) | 10/6=5/3 & 5=3+2 & EVEN
..|...|.....| ... |... 

#### For unknown a and c = b+3


```
a= (c-b) √(d) for c/b = e/f => (d=e + f) return true if c%3 == 0 and c >3 else if(c==3) {a=3;}

```

 Note d =e+f is e = f+1 
 
  ```
  
 (c-b)^2(f+1+f) = (c-b)^2(2f+1) which is similar to the equation (3) above
 
 (3)=(4) => true
 
  ```
 

 
**_extended version:_**

 
~~a = √(3*(c+b))  return true if (c%3)! = 0~~
  - since c = b+3 => 3 = c-b => √((c-b)(c+b)) =>pythagoras

c | b | a   | Calc       | Explain
--| --|---- |------------|----------
3 | 0 | 3√1 | 3          | law above
9 | 6 | 3√5 |(9-6)√(3+2) | 9/6=3/2
12| 9 | 3√7 |(12-9)√(4+3)| 12/9 = 4/3
..|...|....| ...  ...    |..

__________________________________________________________

## `OVERALL FORM (except special forms): `

#### For c= b  + even number

```
a=2*√(((c-b)/2)^2 +(c-(c-b))*((c-b)/2))

```

 **_c=b+ 6_**
 
 c | b | a                                     
  --|---|----          
  6 | 0 | 2√9           
7  | 1 | 2√12          
8  | 2 | 2√15                                                 
9  | 3 | 2√18                                              
10 | 4 | 2√21                                      
11 | 5 | 2√24                                   
12 | 6 | 2√27                                                 
...|...|**2√(9+(c-6)3)**    
 
**_c=b+ 8_**

 c | b | a    
 --|---|----                  
 8 | 0 | 2√16              
 9 | 1 | 2√20                 
10 | 2 | 2√24             
11 | 3 | 2√28                          
12 | 4 | 2√32
.. |...| **2√(16+(c-8)4)**      
 
 **_c=b+ 10_**    
    
 c | b | a     
 --|---|----
 10 | 0  |  2√2
 ...|....| **2√(25+(c-10)5)**
 
#### For c = b+odd number, c>=5

~~a= √(d(c+b))  return true if d = c-b~~

- Since d =c-b =>  a=√((c-b)(c+b)) => pythagoras
  

**_c=b+ 5:_**

c | b | a     
 --|---|----
 5 | 0  | 5
 6 | 1  | √35
 7 | 2  | 3√5 =√45
 ...|....| **a = √(5(c+b))**
 
# Advantages
 
 New way | Old way
------------ | -------------
Don't have to use calculator | have to use calculator
Faster | not very fast

# Disadvantages

New way | Old way
------------ | -------------
Only INTEGERS | all real numbers
Hard at first | not very hard
 Small range  |  ALL NUMBERS
 