+++
title = 'Anagrams Exercise'
date = 2024-11-26
draft = false
math = true
+++
Exercise from
<a href='https://greenteapress.com/thinkpython2/html/index.html'>Think Python, 2nd Edition</a>
by Allen Downey

Write a program that reads a word list from a file (see Section 9.1) and prints all the sets of words that are anagrams.
Here is an example of what the output might look like:
['deltas', 'desalt', 'lasted', 'salted', 'slated', 'staled']
['retainers', 'ternaries']
['generating', 'greatening']
['resmelts', 'smelters', 'termless']


```
words = open('words.txt').read().split('\n')

def Anagrams(list, word):
    d = dict()
    for x in range(len(list) -1):
            if tuple(sorted(tuple(list[x]))) in d: # list[x] is first made in to a tuple s.t. 'exp' becomes ('e', 'x', 'p'), it's then ordered to ('e', 'p', 'x'), it is then \
                  # made again into a tuple as sorted returns a list but the dictionary key cannot be one

                  d[tuple(sorted(tuple(list[x])))].append(list[x])  # case in which the key already exist
            else:  # case in which the key doesnt exists
                  d[tuple(sorted(tuple(list[x])))] = [] # create an empty list in the key
                  d[tuple(sorted(tuple(list[x])))].append(list[x]) # append the first value to the empty list

    return d[tuple(sorted(tuple(word)))]

print(Anagrams(words, 'deltas'))
```