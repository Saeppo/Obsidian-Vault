# List comprehension
når man har \[\] 
Filtrere: Skille nogle ti
Mapper: \[1,2,3] x*2 -> \[2,4,6]
```` python
[x for x in L if x %2 == 1]
# Første del er Map Delen "x for x in L"
# Tager x og spytter x ud
# Filter del er "if x %2 == 1"
`````
# Opgave 1
```` python
[x for x in L if x % 2 == 1]
`````

# Opgave 2
```` python
L = [0,1,0,2,7,8,1]
L[i+1] - L[i]
range(0; (len(L)-1)) # len(L)-1 kommer ikke med, men op til len(L) -2
[L[+1]-L[i] for i in range(len(L)-1)]
`````

# Opgave 3
```` python
[[L+1] for i in range(len(L)-1)

# Kan også løses med
# Subliste af en liste
L[1:] # `L[1:]` returns all elements of `L` **except the first**.
L[:1] # `L[:1]` returns a **list containing only the first** element of `L`.
  

`````

# Opgave 4
```` python
v = []  
  
x = input("Write a float ")  
while x != "stop":  
    y = float(x)  
    if y > 0:  
        v.append(y)  
    x = input("Write a float ")  
  
print(sum(v) / len(v))

`````

# Opgave 5
```` python
v = []  
  
x = float(input("Write a float: "))  
while x not in v:  
    if x > 0:  
        v.append(x)  
    x = float(input("Write a float "))  
  
print(len(v))
```