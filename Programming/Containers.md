Containers are a way of forming new data types from old ones
#### Container types
list
tuple
set
dict (for dictionary)

#### Lists
A list represents a well, list of elements
	Sensitive to repetition
		Order matters
	Some limits (Note the square brackets)
		["cabbage", "broccoli", "kohlrabi"]
		[1,3,2,3,1]
		["mixed", 5.0, True, "data"]
		\[\["lists", "of", "lists"\], \["are", "allowed"\]\]

len() function on lists
a\[i\] is the element of list a at index i
\+ concatenates lists (Pushed them togehter)
Unlike Strings, individual elements of a list can be modified

```` Python
s=[0,1,2]
s[1]=100
print(s)
output: [0,100,2]
`````

s and t points to the same place in memory. When s\[1\] is modified, so is t\[1\]
```` Python
s = [0,1,2]
t=s
t[1] = 100

Then s
print(s)
output: [0,100,2]
`````

### Tuples
A tuple is an immutable list. 
	(1,2,3,2,1)
	("cabbage", "broccoli", "kohlrabi")
Like strings, individual elements of a typle cannot be modified, and elements cannot be added or deleted
Otherwise the same operations you can do to a list, you can do to a tuple as well.
```` Python
x = t[1] (Correct)
t[1] = (Incorrect)
`````
You can't modify the tuple. It is as a final Arraylist in Java

When we define a Point, it will be as a tuple of floats;
similarly, a Triangle is a tuple of Points.

### Sets
A set is mutable, like a list. However,
	Insensitive to repetition (If it accures 2 or 3 times, it is the same as it accuring 1 time)
	Order does not matter
	Some Sets
		{1,2,3,2,1}
		{"cabbage", "broccoli", "kohlrabi"}
	We cannot ask for an element in a particular index (Because there is not order), but we can query membership.
		"kale" in {"cabbage", "broccoli", "kohlrabi"}
		False
```` Python
len([1,2,3,2,1])
output: 5
len({1,2,3,2,1})
output: 3
`````

### Dictionaries
Finally, a dictionary is a mutable data structure meant to represent a mathematical function.
```` Python
code = {"Denmark":45, "France":33, "Germany":49, "Irland":353}
code["Denmark"]
45
`````
Set comprehension / list comprehension
	These allow you to define containers from boolean valued properties

Elements to the left of the colon are called keys, elements to the right are called values. Values are thus referenced by keys instead of indices, like they are for lists.

in can be used to check membership in the set of keys:
	"Norway" in code
	False

### Common methods for mutable containers
Lists, sets, and dictionaries each support the ability to add and delete values, as well as a whole host of other built-in operations.

However: the following three operatios are meaningful for any container:
```` Python
len, in, copy
`````

```` Python
brassicae = {"cabbage", "broccoli", "kohlrabi"}
s = brassicae.copy()
brassicae.remove("cabbage")
print(s)
output: {"cabbage", "broccoli", "kohlrabi"}

# Does not modify the original when it copies
`````

### How would you model these
a Circle
	((float, float), float) Using Tuples
a roster of students enrolled in a class, say
	a dict of "students" indexed by ID. But what's a student?
		{student-ID:(firstname, last name), ...}
The results of an experiment where you measure some real-valued quantity against time.
	{float:float, float:float, ...}
A 3x3 matrix of real numbers
	A tuple of length 3 of tuples of length 3
