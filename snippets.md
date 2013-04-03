#Useful Python Snippets

* Dividing a list into groups of n
<pre><code> l = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    n = 3
    list_of_three = zip(*([iter(l)] * n))
</code></pre>