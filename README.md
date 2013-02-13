#Learnings of Python

##Facts about Python
* Python has no concept of **casting** - everything is an object (unless it's a type). You can pass any object (or type) to anywhere, and if you try to do something with it that it doesn't support, an exception will be thrown. This is one of the most basic things about python - everything has a type, but it usually doesn't matter what that is. All you deal with are references.

* In many languages, an include file directive is used by the preprocessor to take all code found in the file and ‘copy’ it into the caller’s code. It is different in Python: the included code is isolated in a module namespace, which means that you generally don’t have to worry that the included code could have unwanted effects, e.g. override an existing function with the same name.

* Any directory with an <pre><code>__init__.py</code></pre> file is considered a Python package

##Best Practices

###Functions

Using stateless functions is a mandatory requirement for writing good, clean code in Python.

###Modules

* Module names should be kept small and all in lowercase, avoiding even 	  '_' when possible.


*	<pre><code>import module</code></pre> is a better practice when compared to <pre><code>from module import *</code></pre> or even <pre><code>from module import func</code></pre>

###Packages

Leaving an __init__.py file empty inside a package is considered normal and even a good practice, if the package’s modules and sub-packages do not need to share any code.

##Bad Practices

* Large loops with something expensive
* Nested Loops
* Lot of function calls inside loops
* Dictionary Lookup inside Loops