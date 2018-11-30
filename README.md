Big-O
=====

Measures efficiency of an algorithim.
Looking at how speed changes over growth of input.
Interested in average - worst case scenario. At times we need to calculate both.
  *ex. Simple search vs Binary Search with array [1..10] looking for 1 vs [1..10] looking for 8*
Not interested in absolute time (because we have no way of knowing that), interested in operations.
  *ex. Run through simple looping example*


## Types of Big O

Three different types of Big O

### 1. Big O
  * Upper bound on time. *The algorithim is at least as fast as ______*. or *speed <= ______*
### 2. Big Omega
  * Lower bound on time. *The algorithim won't be any faster than ______* or *speed >= ______*
### 3. Big Theta
  * Tight bound on time. *The algorithim is ______* or *O(n) = ______*

In the tech industry, when people say Big O they generally mean Big Theta.
  * *ex. The Big O of printing all elements in an array can generally be described as O(n) but to say it is O(n^2) would be incorrect.*

## In Terms of n

Big O is expressed in terms of n, the size of a collection.
  * *For example, iterating over an array of 100 elements means we're looking for the Big O where n = 100.*

What is the relationship between number of operations to size of input. When we graph common Big O runtimes, we're looking at a graph where the x-axis is n and the y axis is the number of operations.

We represent this by this notation: O(expression).

## Common Big O Runtimes

### 1. O(1)
  Constant time. No matter what the size of the input, the same number of operations are performed.

### 2. O(n)
  Linear time. For every additional input, there is an additional operation performed.

### 3. O(n^2)
  Quadratic time. For 5 inputs, my algorithim has to do 5*5 operations.

### 4. O(log n)
  Logarithmic time. More on this later.

### Others...
  O(n log n)
  O(2^n)
  O(!n)

## More on Logarithims

log n in Big O always denotes log2 n, as in, how many times do we have to multiply 2 by itself to get n.
  * *ex. log 8 = 3 because 2*2*2*
  Let's graph log n for numbers 2,4,8,16,32.
  x axis = n
  y axis = log n

Where is this applicable in terms of algorithims?
  Binary search vs Simple search - worst case
  * *ex. [1..128] searching for number 128
  Simple search mean's we're going to iterate through each number which is O(n)

  Binary search, we're going to half the collection until n eventually becomes 1

  START: n = 128
  (rounding down on division)
  STEP 1: n = n/2 = 64
  STEP 2: n = n/2 = 32
  STEP 3: n = n/2 = 16
  STEP 4: n = n/2 = 8
  STEP 5: n = n/2 = 4
  STEP 6: n = n/2 = 2
  STEP 7: n = n/2 = 1

  How do we represent this process mathematically?

  We could reverse this and say, "How many times do I have to multiply 1 by 2 to get to 64"

  The answer to this is what log2 describes: log2(7) = 7 times*


## Rules

### Adding operations vs multiplying

for(x in arrX)
  puts x

for(y in arrY)
  puts y

  VS

for(x in arrX)
  for(y in arrY)
    puts (x + "," + y)


## Drop the Constants

Because Big O measures the rate of increase.

O(2n)
Reasons why the above isn't valid
1) The line is essentially still linear so it's the same as O(n)

Graph O(2N) for the following

n = 5
n = 10
n = 50
n = 100

How is this graph different than O(n)

2) What are you actually measuring?

for(x of arr)
  puts x
  puts x + 1

Representing the above as O(2N) shows a level of granularity that's unnecessary. And you're not being more accurate. At the assembly level, multiplicatin requries more operations than addition. So would you consider the below the same as the above:

for(x of arr)
  puts x
  puts x * 2


## Recursive Functions

f(n)
  for(i in n)
    if( n <= 1)
      return 1
    else
      f(n - 1) + f(n - 1)

f(4)

Going to be

f(4)
f(3) + f(3)
f(2) + f(2) + f(2) + f(2)
f(1) + f(1) + f(1) + f(1) + f(1) + f(1) + f(1) + f(1)

this is the same as:
2^0 + 2^1 + 2^2..2^n

O(branches^n)




## Time Complexity vs Space Complexity

Time and Space are parralel concepts. Big O Time Complexity measures the rate of increase of time while Space Complexity measures the rate of increase of space necessitated by an algorithim.

  *ex. If an algorithim required an nxn grid then your Big O Space Complexity would be O(n^2)

  *If you iterate through each element your time complexity will likely be O(n). However, your space complexity will be O(n^2)*

  What kind of space complexity will this have? Execution Stack

  function recurs(arr){
    if(arr.length > 0)
      recurs(arr.slice(0,arr.length/2)
    else
      return "DONE"
  }
