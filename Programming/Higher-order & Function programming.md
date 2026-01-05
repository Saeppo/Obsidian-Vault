Lets say I want to compute the derivative of a function f at a point x.
Answer should be a real number.

```` python
dx = .00001  
def derivative(f):  
    """Computes the derivative function of a given function"""  
  
    #x has no meaning here  
    def g(x): #g should be the derivative of f  
        # inside the function declaration of g, x has meaning        return (f(x+dx)-f(x))/dx  
    return g  
  
def f(x):  
    return x*x  
g = derivative(f)  
print(g(1))
`````

Function composition for example if
	f(x) = x^2 + 1   and
	g(x) = x - 3

What is $(f o g)(x)? = f(g(x)) = f(x-3)=(x-3)^{2 +1}= x^{2}-6x+10$
$(g o f)(x)? = g(f(x)) = g(x^{2}+1)=x^{2}-2$ 

```` python
dx = .00001  
def derivative(f):  
    """Computes the derivative function of a given function"""  
  
    #x has no meaning here  
    def g(x): #g should be the derivative of f  
        # inside the function declaration of g, x has meaning        return (f(x+dx)-f(x))/dx  
    return g  
  
def comp(f, g):  
    """Takes in two one-input functions and returns the function (f o g)  
    (g inner function, f is the outer)"""    def h(x): # h should be the function (f o g)  
        return f(g(x))  
    return h  
  
def square(x):  
    return x**2  
  
def power(f, n: int):  
    def identity(x):  
        return x  
    if n == 0:  
        return identity  
    else:  
        comp(f, power(f,n-1))
`````

Higher-order programs are hugely important, even if you're not a strict functional programmer.
```` python
def pair(x,y):
	def f(n):
		if n == 0:
			return x
		elif n == 1:
			return y
	return f
	
p = pair(9,10)
Output = p(0) = 9
Output = p(1) = 1
`````
It is like a tuple. 
is equal to
q = (1,2)
so q\[0] = 1
and q\[1] = 2

LL = pair(1, pair(2, pair(3,4)))
LL(0) = 1
LL(1)(0) = 2
LL(1)(1)(0) = 3