```` Python
while (boolean-expr):
	(code)
	
# Strips the trailing zeroes
# Example 321000 
# output: 321
while n % 10 == 0
	n //= 10
`````
### Primality
A positive natural number greater than 1 is prime if it has no divisors other than 1 and itself
	Primes: 2,3,5,7,11,13
	None-prime composite numbers: 4,6,8,10
$$
\text{Observation: if n is composite, then its leats divisor must be at most } \space \sqrt{n}
$$
```` Python
def is_prime(n: int) -> bool
	i = 2
	while (i < n ) ## (Math.sqrt(n) for n instead also
		if n % i == 0
			return False
		i += 1
		
	return True
	
is_prime(91)
`````

### Lexicographic ordering
Problem: Given two lists of integers, determine which one is lexicographically prior
Read the lists in parallel from left to right, stopping at the index where they differ. The list with the smaller corresponding value is prior

[1,2,3,4] vs. [1,2,4]
First is prior
[1,2,3,4] vs. [1,2,4,3]
First is prior
[1,2,3,4] vs [1,2,2,4,3]
Second is prior
[5,2,4,6,6] vs [5,1,100,100]
Second is prior

If one list is a prefix of another, it is lexicographically prior.
[1,2] Lexicographically prior to [1,2,3,4]
Same for [], [5], [5,2], [5,2,4] are all prior to [5,2,4,6,6]

```` Python
def prior(A:list[int], B:list[int]) -> bool: # True if A is prior, false else
	i > 0
	while(i < len(A) and i < len(B)):
		if A[i] == B[i]:
			i = i+1
		elif A[i] < B[i]:
			return True
		else
			return False
	
	# With a for loop
	for a, b in zip(A,B):
		if a < b: # a is less, then it is prior
			return True
	return False
`````

## Factorization revisited
Instead of just detecting a positive integer is prime or not, we want to list all its prime factors. Finds all the primes and use addition to get the desired number.
12: 2, 2, 3
13: 13
26: 2, 13
99: 3, 3, 11
200: 2, 2, 2, 5, 5

### Example
	98 49 7 1
	2  7  7
### Nested while loops
```` Python
# n given number
# d potential divisors
d = 2
while(n > 1):
	while(n % d == 0)
		n = n//d
		print(d) # or append to list
	d += 1
`````

### problem
Given two positive natural numbers, find their greatest common divisor.
The biggest number which divides both of them
	gcd(10,12) is 2
	gcd(48,32) is 16
	gcd(48,31) is 1
	gcd(100,10) is 10
This has a runtime of O(n)
 ```` Python
 # Naive method
 def greatestPossiblrDivider(n: [int], m: [int]):
	 d = 1 # Greatest divisor I've seen thus far
	 for each d in range(1, min(m,n))
		 if n % i == 0 and m%i == 0 # i is a common divisors
			 d = i
 `````

To compute the gcd of a and b where a > b, repeatedly replace the pair (a,b) by the par (b, a%b) until the second coordinate is zero; the first coordinate is the gcd.
### example
8 with 5, then the remainder is 3. So we take the modulus 8 % 5, and 3 in remainder, and so on.
	8 5
	5 3
	3 2
	2 1
1 0 (Second coordinate is 0)
The first coordinate is 1, which is the gcd

This code takes less iterations than the for each loop. This is O(log(n))
```` Python
# inputs a, b assume a > b
def Euclidean(a: [int], b: [int])
	# Correct way
	while(b > 0):
		tmp = a # Remebers the old value a
		a = b
		b = tmp%b
	return a

	# Gives buggy code
	while(b > 0):
		a = b
		b = a%b
`````

## Tossing Dice
By invoking the module random (by writing import random), we get access to several method of random number generation.
```` Python
import random
random.random() # Random uniformly distributed (Equally likely) float from 0,0 and 1,0

random.randint(a,b) # Random uniformly distributed integer between a and b, inclusive.

# Dice Roll
random.randint(1,6) # Inclusive of 1 and 6

# My Way
def until_one() -> list[int]:
	diceRollsList = []
	while (True)
		diceRoll = random.randint(1,6)
		if diceRoll == 1
			return False
		else
			diceRollsList.append(diceRoll)
			
	return diceRollsList
	
# Siddarth way
def until_one() -> list[int]:
	diceRollsList = []
	d = random.randint(1,6)
	while (d not 1):
		d = random.randint(1,6)
		diceRollsList.append(d) # Sticks the new roll at the end of the list
	
	return diceRollsList
`````

