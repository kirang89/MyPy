#Useful Python Snippets

* To get index when iterating a list
<pre><code>for index, value in enumerate(mylist):
        print index, value
</code></pre>

* Dividing a list into groups of n
<pre><code>l = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    n = 3
    list_of_three = zip(*([iter(l)] * n))
</code></pre>

* Find the longest line in a file
<pre><code>max(open('test.txt'), key=len)</code></pre>

* Unpacking function arguments(magic version)
<pre><code>def foo(a, b, c):
        print a, b, c

    d = {'a': 1, 'b': 2}
    e = [1,2,3]

    #Unpacking a dict
    print foo(*d)  #a,b,c
    print foo(**d)  #1,2,3

    #unpacking list
    print foo(*e)  #1,2,3
</code></pre>
