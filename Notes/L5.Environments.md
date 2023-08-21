# Environments

## 1.Environments for Higher-Order Functions

- Higher-order function:

  A function that takes a ***function*** as an ***argument value*** or 

  A function that returns a ***function*** as a ***return value***

  ```python
  def apply_twice(f,x):
      """takes another function as a return value"""
      return f(f(x))
  
  def square(x):
      return x*x
  ```

  ```python
  """
  <<<apply_twice(square,3)
  81
  
  """
  ```

  

  ```python
  """example:Repeat"""
  def repeat(f,x):
      while f(x)!=x:
          x=f(X)
      return x
  
  def g(y):
      return (y+5)//3
  
  ```

  ```python
  """
  >>>repeat(g,5)
  2
  """
  ```

  

- Applying a user-defined function: 
  - Create a new frame 
  - Bind formal parameters (f & x) to arguments 
  - Execute the body: return f(f(x))



## 2.Environments for Nested Definitions

- **Nested functions** will create a new frame whose parent is the previous frame,at this example, the parent frame of "adder" is "make_adder"

  ```python
  """ Example	"""
  def make_adder(n):   
  """ 
  >>>add_three = make_adder(3)
  >>>add_three(4)
  7
  """
      def adder(k):
          return k+n
      return adder
  
  ```

## 3.Function Composition

- While writing Function composition, we need to figure out what exact frame is for each nested function

  ```python
  def squre(x):
  	return x*x
  
  def triple(x):
      return 3*x
  
  def composel(f,g):
  """ 
  >>>squiple=composel(squre,triple)
  >>squiple(3)
  27
  """
      def h(x):
          return g(f(x)
      return h
  ```


## 4.Self-Reference

- Self-Reference means we could return the function ***itself*** to execute continuously,such like the `cout<<`or`cin>>`in C++

  ```python
  def print_all(x):
  """
  >>>print_all(1)(3)(5)
  1
  3
  5
  """
      print(x)
      return print_all
  ```

  ```python
  def print_sums(x):
  """
  >>>print_sums(1)(3)(5)
  1
  4
  9
  """
      print(x)
      def next_sum(y):
          return print_sums(x+y)
      return next_sum
  
  
  ```

## 5.Function Currying

- Function currying means transforming a  multi-argument function into a single-argument,higher-order function. Such like the `make_adder(2)(3)`and `add(2,3)`

  ```python
  """with def"""
  
  def curry2(f):
  """
  >>>f=curry2(add)
  >>>f(2)(3)
  5
  """
      def g(x):
          def h(y):
              return f(x,y)
          return h
      return g
  
  ```

  ```python
  """with lambda"""
  curry2=lambda f: lambda x: lambda y : f(x,y) 
  ```

  













