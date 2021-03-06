# Python 3 : Flow Control - Loops, Conditionals, etc

**Based on Lecture Materials By: Milad Fatenejad and Katy Huff**

Pasting into iPython
====================

This part of the lesson includes a lot of text, but it will be useful to
run it yourself in iPython.

To paste text from another application (i.e. these lecture notes) into
iPython :

1.  select text from the wiki
2.  copy with **ctrl+c**
3.  in iPython, type **%paste**

The code should paste and execute in iPython.

If you also type %autocall to turn autocall OFF, you may be able to
paste with **ctrl+v** though this won't work with all ipython builds.

Conditionals
============

A conditional (if statement) is some statement that in general says :
"When some boolean is true, do the following. Elsewise, do this other
thing."

Many equivalence test statements exist in Python that are similar in
other languages:

```python
  # two assignments:
  i = 1
  j = 2
  # and some Boolean tests:
  i == j # i is equal to j : FALSE
  i < j  # i is less than j
  i <= j # i is less than or equal to j : TRUE
  i > j  # i is greater than j
  i >= j # i is greater than or equal to j : FALSE
  i != j # i is not equal to j : TRUE
```

However, python has other equivalence test statements that are fairly
unique to python. To check whether an object is contained in a list :

```python
  python="Cleese"
  beatles=["Chapman", "Cleese", "Jones", "Gilliam", "Idle", "Palin"]
  print python in pythons # is Cleese one of the Pythons? : TRUE
  print "Wilson" not in beatles # this is also TRUE. 
```

Conditionals (if statements) are also really easy to use in python. Take
a look at the following example:

```python

  i = 4
  sign = "zero"
  if i < 0:
      sign = "negative"
  elif i > 0:
      sign = "positive"
  else:
      print "Sign must be zero"
      print "Sign is still zero..."
  print "Have a nice day"
  print sign
```

The behavior of this code snippet should be pretty clear, but there is
something peculiar. How does Python know where the if-statement ends?
Other languages, like FORTRAN, MatLab, and C/C++ all have some way of
delimiting blocks of code. For example, in MatLab you begin an if
statement with the word "if" and you end it with "end if". In C/C++ you
delimit blocks with curly braces. Python uses ''indentation'' to delimit
code blocks. The **indentation** above is NOT just to make things look
pretty - it tells Python what the body of the if-statement is. This is
true when ever we create any code blocks, such as the bodies of loops,
functions or classes.

**Aside: Compact if-statement:**

Python has an easy to use if-syntax for setting the value of a variable.
Try entering this into IPython:

```python
  i = 5
  sign = "positive" if i > 0 else "negative"
```

While Loops
===========

Lets start by looking at while loops since they function like while
loops in many other languages. The example below takes a list of
integers and computes the product of each number in the list up to the
-1 element.

A while loop will repeat the instructions within itself until the
conditional that defines it is no longer true.

```python
  mult = 1
  sequence = [1, 5, 7, 9, 3, -1, 5, 3]
  while sequence[0] is not -1:
      mult = mult * sequence[0]
      del sequence[0]

  print mult
```

Some new syntax has been introduced in this example.

-   On line 3 We begin the while loop. Notice that instead of using the
    not-equals symbol, !=, we can simply enter "is not" which is easier
    to read. This while loop will execute until sequence[0]= -1 . That
    is, until deletes all of the entries of the sequence that come
    before -1.

-   On line 4, we compute the product of the elements just to make this
    more interesting.

-   On line 5, we use the \`del\` keyword to remove the first element of
    the list, shifting every element down one.

**Watch Out**

Since a while loop will continue until its conditional is no longer
true, a **poorly formed** while loop might repeat forever. For example :

```python
  i = 1
  print "Well, there's egg and bacon, egg and spam, egg bacon and"
  while i == 1:
      print "spam "
  print "or Lobster Thermidor a Crevette with a mornay sauce served in a Provencale manner with shallots..." 
```

Since the variable **i** never changes within the while loop, we can
expect that the conditional, **i==1** will remain true forever and the
while loop will just go round and round, as if this restaurant offered
nothing but spam. (If you try this at home, please note that one way to
interrupt a non-terminating process is **ctrl+c** or **ctrl+z**.

To create nested if loops, the indentation (preferably two or four
spaces) should increase for each looping level.

```python
  weapons=["surprise","fear","ruthless efficiency","an almost fanatical devotion..."]
  tries=0
  script=""
  while tries < len(weapons) :
      i=0
      while i < tries :
          script += weapons[i]
          script += " and "
          i+=1
      script += weapons[tries]
      script += ". "
      if tries == len(weapons) - 1 :
          script += " and nice red uniforms. Oh damn!"
      tries +=1
  print script
```

For Loops
=========

For loops in python operate a little differently from other languages.
Lets start with a simple example which prints all of the numbers from 0
to 9:

```python

  for i in range(10):
      print i
```

You may be wondering how this works. Start by using help(range) to see
what the range function does.

    Help on built-in function range in module __builtin__:

    range(...)
        range([start,] stop[, step]) -> list of integers

        Return a list containing an arithmetic progression of integers.
        range(i, j) returns [i, i+1, i+2, ..., j-1]; start (!) defaults to 0.
        When step is given, it specifies the increment (or decrement).
        For example, range(4) returns [0, 1, 2, 3].  The end point is omitted!
        These are exactly the valid indices for a list of 4 elements.

Range is a function that returns a list containing a sequence of
integers. So, range(10) returns the list [0,1,2,3,4,5,6,7,8,9]. The for
loop then simply iterates over that list, setting i to each value.

For Loops with Lists and Dictionaries
=====================================

With range, we learned that **for** loops in python are really used to
iterate over sequences of things (they can be used for much more, but
for now this definition will do). Try entering the following to see what
happens:

```python

  for c in ["one", 2, "three", 4, "five"]:
      print c
```

this is equivalent to:

```python

  c = ["one", 2, "three", 4, "five"]
  for i in range(len(c)):
      print c[i]
```

With a list, then, it's clear that we can use the **in** keyword to
indicate a list of things. What about a nested loops around a list of
lists?

```python
  italy_cities = ["Rome", "Pisa", "Florence", "Venice", "Trieste"]
  argentina_cities = ["Mendoza", "Buenos Aires", "Patagonia"]
  india_cities = ["Ahmedabad","Kolkata", "Chennai", "Jaipur", "Surat"]
  us_cities = ["Chicago", "Austin", "New York", "San Fran"]
  all_cities = [italy, argentina, india, us]
  nationnames = ["italy","argentina", "india", "us"]
  for cities in all_cities :
      print nationnames[all_cities.index(nation)] + ": "
      for city in cities :
          print "  " + city 
```

Of course, this information is better stored in a dictionary, isn't it?
The data makes more sense if the keys were the nation names and the
values were lists of cities. Importantly, python has given us a tool
specifically for dictionary looping.

The syntax for looping through the keys and values of a dictionary is :

    for key, value in dictionary.iteritems():

Importantly, you don't have to use the words key and value. That's just
what will fill those variables. Here, we rewrite the previous loop using
this clever syntax.

```python
  italy_cities = ["Rome", "Pisa", "Florence", "Venice", "Trieste"]
  argentina_cities = ["Mendoza", "Buenos Aires", "Patagonia"]
  india_cities = ["Ahmedabad","Kolkata", "Chennai", "Jaipur", "Surat"]
  us_cities = ["Chicago", "Austin", "New York", "San Fran"]
  nations = {"italy":italy_cities, "argentina":argentina_cities, "india":india_cities, "us":us_cities}
  for nation, cities in nations.iteritems() :
      print nation + " : "
      for city in cities :
          print "  " + city 
```

break, continue, and else
=========================

A break statement cuts off a loop from within an inner loop. It helps
avoid infinite loops by cutting off loops when they're clearly going
nowhere.

```python
  reasonable = 10
  for n in range(1,2000):
      if n == reasonable :
          break
      print n
```

Something you might want to do instead of breaking is to continue to the
next iteration of a loop, giving up on the current one..

```python
  reasonable = 10
  for n in range(1,2000):
      if n == reasonable :
        continue
      print n
```

What is the difference between the output of these two?

We can combine loops and flow control to take actions that are 
more complex, and that depend on the data. First, let us define 
a dictionary with some names and titles, and a list with a 
subset of the names we will treat differently.

```python
  knights = {"Sir Belvedere":"the Wise", 
           "Sir Lancelot":"the Brave", 
           "Sir Galahad":"the Pure", 
           "Sir Robin":"the Brave", 
           "The Black Knight":"John Cleese"} # create a dict with names and titles
  favorites = knights.keys()      # create a list of favorites with all the knights
  favorites.remove("Sir Robin") # change favorites to include all but one.
  print knights
  print favorites
```

We can loop through the dict of names and titles and do one of 
two different things for each by putting an if statement inside 
the for loop:

```python
  for name, title in knights.items(): 
      string = name + ", "
      if name in favorites:   # this returns True if any of the values in favorites match.
          string = string + title
      else:
          string = string + title + ", but not quite so brave as Sir Lancelot." 
      print string
```

Final Example
=============

We've seen a lot so far. Lets work through a slightly lengthier example
together. I'll use some of the concepts we already saw and introduce a
few new concepts. To run the example, you'll need to locate a short file
containing phone numbers. The file can be found in your PyTrieste
repository within the phonenums directory and is called phonenums.txt.
Now we have to move ipython to that directory so it can find the
phonenums.txt file. You navigate within ipython in the same way that you
navigate in the shell, by entering "cd [path]" .

This example opens a text file containing a list of phone numbers. The
phone numbers are in the format \#\#\#-\#\#\#-\#\#\#\#, one to a line.
The example code loops through each line in the file and counts the
number of times each area code appears. The answer is stored in a
dictionary, where the area code is the key and the number of times it
occurs is the value.

```python

  areacodes = {} # Create an empty dictionary
  f = open("phonenums.txt") # Open the text file
  for line in f: # iterate through the text file, one line at a time (think of the file as a list of lines)
      ac = line.split('-')[0] # Split phone number, first element is the area code
      if not ac in areacodes: # Check if it is already in the dictionary
          areacodes[ac] = 1 # If not, add it to the dictionary
      else:
          areacodes[ac] += 1 # Add one to the dictionary entry
  
  print areacodes # Print the answer
```

Example : Iteritems
-------------------

Use the iteritems dictionary method in combination with a for loop to
print the keys/values of the areacodes dictionary one to a line. In
other words, the goal is to write a loop that prints:

    203 4
    800 4
    608 8
    773 3

This example is a little tricky to figure out, but give it a shot.
