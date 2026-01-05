```` Python
L = [1,2,1,3]
d = {x:L.count(x) for x in L}

print(d)
Output: {1:2, 2:1, 3:1}
`````

## Classes
A way of defining new types of data out of old ones, giving them names, and endowing them with methods.

### Dataclasses
A Python-specific construction for develoing simple classes in a lightweight way.
Sort of a wrapper. Under the hood its is a 3 pointer, but when we look at it it is a triangle. So when Python sees a triangle it sees 3 points.

By convention, Python class names are capitalized

```` Python
from dataclasses import dataclass

@dataclass
class Points: #(class-name):
	x: float
	y: float
	
p = Point(8, 9)

print(p)
Output: x=8, y=9
`````

### Methods vs. functions
A class method is a function that uses your new class, but it differs both in the syntax of its implementation and its usage.
Methods have a self argument and are implemented inside the class.

Methods should exclusively mediate how the internal values of an object are modified.
```` Python
len(S) # Is a function
S.add(5) # Is a method
`````
### examples
```` Python
from dataclasses import dataclass

@dataclass
class Points: #(class-name):
	x: float
	y: float
	
# Flips by creating new points, so new p
def flip(p: Point) -> Points:
	return Point(p.y,p.x)
	
p = Point(8,0)

print(p)
Output(x=8, y=0)

q = flip(p)

print(q)
Output(x=0, y=8)
`````

```` Python
from dataclasses import dataclass

@dataclass
class Points: #(class-name):
	x: float
	y: float
	
# Flips without making a new point, so just changing p
def flip(p: Point) -> None:
	tmp = p.x
	p.x = p.y
	p.y = tmp
	
p = Point(1,2)
flip(p)

print(p)
Output(x=2, y=1)

q = flip(p)

print(q)
Output(None)
``````

```` Python
from dataclasses import dataclass
import math

@dataclass
class Point: #(class-name):
	x: float
	y: float
	
# Defined inside the class, special input called self, inside of a dedicated input
	def flip(self) -> None:
		tmp = self.x
		self.x = self.y
		self.y = tmp
	
	# Changing the self object and not creating a new one
	def move(self.dx: float, dy: float)
		self.x += dx
		self.y += dy 
		
	# Inside defined (Class medthod)
	def distance(self, z: Point) -> float:
	
p = Point(8,4)	
p.flip()

print(p)
Output(x=4, y=8)
	
#Outside defined (Method)
def dist(p: Point, q: Point) -> float:
	dx = p.x - q.x
	dy = p.y - q.y
	distance = math.sqrt(dx**2 + dy**2)  
	
	return distance

p = Point(0,0)
q = Point(0,1)

print(dist(p, q))
Output(1.0)
`````

```` Python
@dataclass 
class Polygon:
	vertices: list[Point]
`````
If points in different order, python will not say it is equal

### Exercise 9.
```` python
i = 1
total = 0
for i in self.vertices
	if i == range(self.vertices)
		total += dist(self.vertices[0], self.vertices[i])
		break
		
	total += dist(self.vertices[i-1], self.vertices[i])
	beforeValue = i+1
return total
`````

```` python
from dataclasses import Dataclasses
from math import sqrt

@dataclasses
class Point:
	x: float
	y: float
	
def dist (p: Point, q: Point) -> float:
	return sqrt((p.x - q.x)**2 + (p.y - q.y)**2)
	
@dataclasses
class Triangle:
	A: Point
	B: Point
	C: Point
	
p = Point(1,0)
q = Point(0,0)
r = Point(0,1)
t = Triangle(p,q,r)
s = Triangle(p,r,q)

print(s == t)
Output: False
`````

Classes do not have a list of local variables
Instead they have an "Init" method.

```` python
class Triangle:
	""" A triangle class where I only care about what the side lengths are,
	not where it's located. """
	def __init__(self, p:Point, q:Point, r:Point) -> None:
		"""Present in any class, sepcifies how to construct a new object
		the self variable refers to the object being constructed"""
		self.A = p
		self.B = q
		self.C = r
		# Local varaiable are defined within __init__
	
	def __eq__(self, other) -> bool:
		""" If defined in a class, it actually overrides Python "==" 
		If I call "==" on objects for which __eq__ is defined Python will
		use this function"""
		# Check whether self.A is equal to other.A, other.B, or other.C
		# Check whether self.B is equal to ...
		# Check whether self.C is equal to ...
		# Check whether self.A is equal to self.A, self.B, or self.C
		# Check ...
		# If all of them pass, return True
		
	
p = Point(1,0)
q = Point(0,0)
r = Point(0,1)
t = Triangle(p,q,r)
s = Triangle(p,r,q)

print(t.A)
output: (1,0)
print(t.B)
output: (0,0)
print(t.C)
output: (0,1)

print(s == t)
Output: True
`````

```` python
class Triangle:
	""" A triangle class where I only care about what the side lengths are,
	not where it's located. """
	def dist (p: Point, q: Point) -> float:
		return sqrt((p.x - q.x)**2 + (p.y - q.y)**2)
	
	def __init__(self, p:Point, q:Point, r:Point) -> None:
		"""Constructs a new triangle out of Point p, q, r recoted the side
		lengths in floats A, B, C"""
		self.A = dist(p, q)
		self.B = dist(q, r)
		self.C = dist(r, p)
		# Local varaiable are defined within __init__
	
	def __eq__(self, other) -> bool:
		return (self.A, self.B, self.C) == (other.A, other.B, other.C)
		
t = Triangle(Point(0,0), Point(0,1), Point(1,0))
s = Triangle(Point(0,0), Point(0,-1), Point(1,0))

print(t == s)
Output: True

class Rational:
	""" Exact arithmetic on fractions"""
	
	def __init__(self, a: int, b: int):
		""" Creates a new rational number with numerator a and denominator
		b"""
		self.n = a
		self.d = b
	
	def __eq__(self, other) -> bool:
		""" Checks the cross product of the division"""
		return self.n * other.d == self.d * other.n
		
	def __str__(self) -> str:
		""" Returns a string which Python interpreter usses to print an
		object. Allows you to print classes in a human-readable way"""
		return str(self.n) + '/' + str(self.d)
`````
