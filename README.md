#Learnings of Python(2.x)

##Facts about Python
* Python has no concept of **casting** - everything is an object (unless it's a type). You can pass any object (or type) to anywhere, and if you try to do something with it that it doesn't support, an exception will be thrown. This is one of the most basic things about python - everything has a type, but it usually doesn't matter what that is. All you deal with are references.

* In many languages, an include file directive is used by the preprocessor to take all code found in the file and ‘copy’ it into the caller’s code. It is different in Python: the included code is isolated in a module namespace, which means that you generally don’t have to worry that the included code could have unwanted effects, e.g. override an existing function with the same name.

* Any directory with an `__init__.py` file is considered a Python package

* The `yield` keyword turns a function into a generator

* Function call overhead in Python is relatively high, especially compared with the execution speed of a builtin function

* The Python interpreter performs some periodic checks. In particular, it decides whether or not to let another thread run and whether or not to run a pending call (typically a call established by a signal handler)


##Best Practices

###Variables

* Avoid global variables wherever possible. This can not only help in writing clean, performant code but can also make it very simple to write tests and debug

###Strings

* Doing String concatenation either like 
<pre><code>''.join([`num` for num in xrange(loop_count)])</code></pre>
or like
<pre><code>  str_list = []
  for num in xrange(loop_count):
    str_list.append(`num`)
  return ''.join(str_list)
</code></pre>
is a much more efficient and pythonic way of concatenation when compared to
<pre><code>  out_str = ''
  for num in xrange(loop_count):
    out_str += `num`
  return out_str
</code></pre>

* Instead of 
<pre><code>out = "Hello" + name + ", you seem to be " + age + "years old"</code></pre>
do this 
<pre><code>out = "Hello %s, you seem to be %i years old" % (name, age)</code></pre>

* Instead of looping over a list of words and converting them to upper case
<pre><code>newlist = []
for word in oldlist:
    newlist.append(word.upper())
</code></pre>
use ```map``` to push the loop from the interpreter into compiled C code
<pre><code>newlist = map(str.upper, oldlist)</code></pre>

###Functions

Using stateless functions is a mandatory requirement for writing good, clean code in Python.

###Modules

* Module names should be kept small and all in lowercase, avoiding even 	  `_` when possible.


*	<pre><code>import module</code></pre> is a better practice when compared to <pre><code>from module import *</code></pre> or even <pre><code>from module import func</code></pre>

* Structure a module in the following manner:
<pre><code>
"""module docstring"""
# imports
# constants
# exception classes
# interface functions
# classes
# internal functions & classes

    def main(...):
  	  ...

	if __name__ == '__main__':

    	   status = main()
    	   sys.exit(status)
</code></pre>

###Packages

* Leaving an `__init__.py` file empty inside a package is considered normal and even a good practice, if the package’s modules and sub-packages do not need to share any code.

###Exceptions

* Always try and catch the expected exception instead of using the default ```except``` clause. This makes it easier to understand and debug when things go wrong.

###Miscellaneous

* Use exceptions to make your code cleaner and easier to read, rather than filling your code with endless branching instructions

* Use a list comprehension when a computed list is the desired end result, and use a generator expression, when a computed list is the intermediate result

* Use coercion if an object must be of a particular type i.e:
Use `str(x)` instead of `isinstance(x, str)`

* To guard certain snippets in your code, put them under 
<pre><code>if \__name\__ == '\__main__'</code></pre> block

* Use ```range()``` and ```xrange()``` wisely.  When you call ```range```, it creates a list of objects in memory. ```xrange``` creates a generator object which gives you the values upon iteration. Thus ```xrange``` is lightweight in memory and is thus preferred when the upper bound is large.


##Bad Practices

* Large loops with something expensive
* Nested Loops
* Lot of function calls inside loops
* Dictionary Lookup inside Loops
