# Trees
Trees have a root and they grow out from their root.
Typically trees grow downwards in programming.
When data is organized in some sort of nested or hierarchical fashion, chances are there's a tree under the surface, such as File folders, algebraic expressions, Python programs. Or for folders 
Home
	Document
		Doc 1
		Doc 2
	Downloads
	Photos
		2024
			pic 1
		2025
			pic 2

Home (The root) Children of the Home would be
	Document Downloads Photos
		Doc link to Doc 1 and Doc 2
		Home Links to Download
		Photos link to 2024 and 2025 then 2024 to pic 1 and 2025 to pic 2

$(x+5)(y+2)+7$
Represented as a tree
			+
		*              2
	+          +
x         5      y       2
Nested lists (The one above for folders) are normally trees in disguise
Well parenthesized expressions are also really trees in disguise
```` python
s=0
for x in L:
	if x%2==0:
		s += x
	else
		s *= x
`````
For python programs, it also follows a nested list. 
		*
	s=0      for x in L
		if x%2 == 0 else
	s += x                        s *= x

## Tree anatomy
### Root
Each tree has one root, where it grows from.
### Leaves
Without any children of their own, so the ends of the tree.
### Nodes or Vertices
Are the "points" of the three. One of them is the Root, some of them are leaves.
### Parent, Child and Siblings
Refers to a relationships between the two vertices. Siblings are notes that share a parent. Ancestor and dissented, is somewhere above or below in the tree.

## File structure as a nested list
\[Home, \[Documents,\[Doc 1], \[Doc 2]], \[Downloads], \[Photos \[2024, \[Pic 1]], \[2025, \[Pic 2]]]]
First: Nested List encoding the subtree of documents
Second: Nested List encoding the subtree Downloads
Third: Nested List encoding the subtree of Photos

### Write a tree labeled by integers
Tree
		1
	2             3
4           6    6         9

Nested list
L = \[1, \[2, \[\[4], \[6]] 3, \[\[6], \[9]]
```` Python
len(L) = 3
`````
### How to calculate size of a labeled tree represented as a nested list?
Recursion, a type of self reference
```` python
def size(t) -> int:
	if len(t) == 1: # Signle vertex trees
		return 1
	else: # The root of the tree has children
		for i in range(1, len(t) - 1) #Iterates through all intesies except the root
			s += size(t[i])
		return s+1
`````

# Recursion
```` python
Thistuple = (5, (2, (1,),(1,)),(3, (1,),(2, (1,), (1,))))  
  
# Maximum tree  
def split_tree(t) -> bool:  
    if len(t) == 1:  
        return t[0] == 1 # Change this to True to check normal tree  
    else:  
        n = t[0]  
        a = t[1][0]  
        b = t[2][0]  
  
        if (n == a+b  
                and a <= b  
                and n > 0):  
            print(t)  
            return split_tree(t[1]) and split_tree(t[2])  
  
    return False  
  
print(split_tree(Thistuple))
Output: True
`````
