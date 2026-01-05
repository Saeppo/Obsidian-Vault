Recall a Point consists of two floats.
A x:float and a y:float, in the Point.

What if I have a mystery data structure, consisting of two parts
	- first one is a float
	- the next one is another instance of my mystery datatype.

Mystery datatype
	float
		Mystery datatype
			float
				Mystery datatype
					float

We can keep repeating this pattern, but at some point it has to stop, where it ends with an empty datatype, if not, we would have infinite. We are forced to admit some sort of "empty" mystery object to avoid an infinite regress.

We could represent this as a tree. With root Float. But we essentially a list of floats. With a different representation then list\[floats] this is called a $\underline{linked \space list}$
Typical picture, we have a float, another linked list, then a float, another linked list.

Array is a fixed part in memory, where a list is stored. A Linked List, points to different points in memory, depending on where the next Linked List is.
Array is faster in time, but costly in space. Linked List can be slower, but saves a little bit of space more.

Nested data structures support recursion

```` python
from __future__ import annotations # To please the gods, or else next: LL not work.
from dataclasses import dataclass
empty = {}

@dataclasses
class LL:
	"""A class of linked lists of integers
	Hast implementation; proper implementation should use a full class"""
	first: int
	next: LL
	
Input: v = LL(1, LL(2, LL(3, empty)))
Output: LL(first=1, next=LL(first=2, next=LL(first=3, next=())))
"Python will not complain, if you put in, Integer, float, String or tuples"

"Written outside det dataclass and not inside."
def length(v:LL) -> int:
	if v == empty:
		return 0
	else: # v is not empty, so it has int "first" and a linked list "next"
		return 1 + length(v.next)
		
def contains(x:int, v:LL) -> bool:
	if v == empty:
		return False
	else: # v has a first and a next
		if v.first == x:
			return True
		else:
			return contains(x, v.next)
			
def lookup(v: LL, n:int) -> int: #Samething as List[index]
	""" Returns the integer in list v at index n, assuming n is 
	less than the lenght of v. """
	if n == 0:
		return v.first
	else:
		return loopup(v.next, n - 1)
`````

```` python
from __future__ import annotations # To please the gods, or else next: LL not work.
from dataclasses import dataclass
empty = {}

@dataclasses
class LL:
	first: int
	next: LL
	
def length(v:LL) -> int:
	if v == empty:
		return 0
	else: # v is not empty, so it has int "first" and a linked list "next"
		return 1 + length(v.next)
		
def contains(x:int, v: LL) -> bool:
	if v == empty:
		return False
	else: # v has a first and a next
		if v.first == x:
			return True
		else:
			return contains(x, v.next)
			
def lookup(v: LL, n:int) -> int: #Samething as List[index]
	if n == 0:
		return v.first
	else:
		return loopup(v.next, n - 1)
		
def add(v: LL, w: LL) -> LL:
	if v == empty:
		return w # Empty list is the identity element for addition.
	else: # If v is not empty
		return LL(v.first, add(v.next), w)
		"""add((v.next), w) is the recursive call. Its ok because at least
		one of the arguments is shorten""" 
	
def equals(v: LL, w: LL) -> bool:
	if v == empty or w == empty:
		return v == empty and w == empty
	else: #Both v and w is nonempty
		return v.first == w.first and equals(v.next, w.next)
	
def zip(v:LL, w:LL) -> LL:  
    """I have two lists of the same length, and I output a new list, that  
    alternates elements, starting with the left.    zip([1,2], [3,4]) =
    [1,3,2,4]"""    
    if v == empty:  
       return w  
    if w == empty:  
       return v  
    return LL(v.first, zip(w, v.next))  
  
v = LL(1, LL(2, (empty)))  
w = LL(3, LL(4, (empty)))  
print(zip(v, w))
Output; (LL(first=1, next=LL(first=3, next=LL(first=2, next=LL(first=4, next={})))))

#def lex_prior
"""[1,2,2,100] and [1,3,4]
Compare whether one is before each other, when we see element that differs, the lsit with the smaller element is the lex_prior. If we keep seeing the same and we run out of one of the list, the list we run out of is the lex_prior, [1,2,2,100] and [1,2,2]. Is similar to equals and zip"""

#def count

#def minimum

def increasing(v: LL) -> bool:
"""check whether input list is in sorted order, i.e., each element is less than the next."""
	if v == empty:
		return True
	elif: v.next == empty: # List has length 1
		return True
	else: # List has length 2 or greater
		return v.first < v.next.first and increasing(v.next)

#def inc_squares

#def dec_squares

#def remove_all
````

### Opgave 1
```` python
from __future__ import annotations  
from dataclasses import dataclass  
  
empty = {}  
  
@dataclass  
class LL:  
    first: int  
    rest: LL  
  
def sum(v: LL | None) -> int:  
    if v == empty:  
        return 0  
    return v.first + sum(v.rest)  
  
print(sum(LL(1,LL(2,LL(3, empty)))))
`````

### Opgave 2
```` python
from __future__ import annotations  
from dataclasses import dataclass  
  
empty = {}  
  
@dataclass  
class LL:  
    first: int  
    next: LL  
  
def even_length(v: LL | None) -> int:  
    if v == empty:  
        return 0  
    if v.first % 2 == 0:  
        return 1 + even_length(v.next)  
    else:  
        return even_length(v.next)  
        
    # Kan simplificeres
    return 1- (v.first % 2) + even_length(v.rest)
  
print(even_length(LL(4,LL(2,LL(3, empty)))))
`````

### Opgave 3
```` python
from __future__ import annotations  
from dataclasses import dataclass  
  
empty = {}  
  
@dataclass  
class LL:  
    first: int  
    next: LL  
  
def increasing(v: LL | None) -> bool:  
    if v.next == empty:  
        return True  
    print(v.first, v.next.first)  
    if v.first <= v.next.first:  
        return increasing(v.next)  
    else:  
        return False  
  
print(increasing(LL(1,LL(2,LL(3, empty)))))
`````

### Opgave 4
```` python
from __future__ import annotations  
from dataclasses import dataclass  
  
empty = {}  
  
@dataclass  
class LL:  
    first: int  
    next: LL  
  
def consec(v: LL | None) -> bool:  
    if not v or v.next == empty:  
        return False  
    if v.first == v.next.first:  
        return True  
    return consec(v.next)  
  
print(consec(LL(2,LL(2,LL(3, empty)))))
`````

### Opgave 5
```` python
from __future__ import annotations  
from dataclasses import dataclass  
  
empty = {}  
  
@dataclass  
class LL:  
    first: int  
    next: LL  
  
def remove_all(x: int, v: LL | None) -> LL | None:  
    if not v:  
        return  
    if v.first != x:  
        return LL(v.first, remove_all(x, v.next))  
    return remove_all(x, v.next)  
  
v = LL(2,LL(3,LL(4, empty)))  

print(remove_all(3, v))
`````
### Opgave 6
```` python
from __future__ import annotations  
from dataclasses import dataclass  
  
empty = {}  
  
@dataclass  
class LL:  
    first: int  
    next: LL  
  
def square(n: int):  
    if n >= 1:  
        return LL(n**2, square(n - 1))  
        
print(square(3))
`````
