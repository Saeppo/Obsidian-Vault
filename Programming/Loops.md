```` Python
for i in (container):
	(some code)
`````

For lists and sets, this executes the block (some code) as i ranges over elements of (container).
For dicts, this executes the block (some code) as i ranges over keys of (container)
	Keys, not values, of dictionaries

```` Python
# Print the value of dict
for i in dict
	print(dict[i])
	
# Prints the keys in the dictionar
for i in dict
	print(i)
`````

## Polynomial evaluation
Problem: given a single-variable polynomial such as
$$
2x^2+3x+1
$$
And a value for x, such as 10.
"Hurner's rule" express the problem as
$$
((2*10)+3)*10+1=2*10^{2}+3*10+1
$$
This suggests a while loop
We would store this as a list of floats
```` Python
# We don't need the x's
list[float] = [2.0,3.0,1.0]
`````

```` Python
# Almost works for Polynomial, we could jsut add some if statements
eval(p : list[float],x:float)->float:
	y = 0
	for v in p:
		y += v
		y *= x
		return y
`````

## Zip()
```` Python
# Iterationg through two lists at the same time parallel
for u, v in zip(L1,L2)
`````

For example, lets say we want to calculate the dot product (prikproduktet) of two lists of floats.
for Example
```` Python
def (mul(L1: list[float], L2: list[float]) -> float)
	sum = 0
	for u, v in zip(L1,L2)
		sum += u*v
	return sum
`````

## Nested iteration
```` Python
for i in L1:
	for j in L2:
		# Goes over every possible value
		
# Check if there is a dublicant in the two list (If A has a dublicant in B)
for i in range(len(L))
	# Iterate over numbers
	for j in range(i)
		# ranges over from 0 to i-1
		if (L[i] == L[j])
			b = False
`````

## List comprehension
So far these iterative patterns have helped us read lists in the input, but what if we want to write lists to the output.
We need a way of constructing lists.

```` Python
# List of values [0,1,2,3,4]
[i for i in range(5)]

# List of values [0,2,4,6,8]
[2*i for i in range(5)]

# List of values [2,6] Looks at the odd in the range 0,1,2,3,4 and multiplies the odds.
[2*i for i in range(5) if i%2 == 1]

# List of values [14,10,10] Can also just give a lsit, not just a range
[2*i for i in [7,5,4,5] if i%2 == 1] 

# Syntax for a general lsit comprehension:
[expr for var in list if bool-expr]
`````
